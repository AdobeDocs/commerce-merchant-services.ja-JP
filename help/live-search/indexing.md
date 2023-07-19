---
title: '"[!DNL Live Search] インデックス作成»'
description: «学ぶ方法 [!DNL Live Search] 製品属性プロパティのインデックスを作成します。"
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: 7eece9b341a27637d7ac00216f18b7fad7c50740
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# インデックス作成

製品属性プロパティ（メタデータ）によって、次のことが決まります。

* カタログでの属性の使用方法
* ストア内での外観と動作
* データ転送操作に含まれるデータ

属性メタデータの範囲は次のとおりです。 `website/store/store view`.

この [!DNL Live Search] API を使用すると、クライアントは [storefront プロパティ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` に設定 `Yes` ( Adobe Commerce Admin ) 有効にした場合、 `Search Weight` および `Visible in Advanced Search` を属性に設定できます。

[!DNL Live Search] 削除済みの製品または次に設定された製品のインデックスを作成しない `Not Visible Individually`.

>[!NOTE]
>
> 次を使用してコマースを行う顧客： [!DNL Live Search] は、Web サイト上で迅速な価格変更の更新と同期時間を活用できます。 [SaaS 価格インデクサー](../price-index/index.md).

## パイプラインのインデックス作成

クライアントがストアフロントから検索サービスを呼び出して、（フィルタリング可能で並べ替え可能な）インデックスメタデータを取得します。 検索可能な製品属性のみ、 *レイヤーナビゲーションで使用* プロパティを `Filterable (with results)` および *製品リストの並べ替えに使用* に設定 `Yes` は、検索サービスによって呼び出されます。
動的クエリを作成するには、検索可能な属性とその重みを検索サービスが把握しておく必要があります。 [!DNL Live Search] は、Adobe Commerceの検索重み付けに従います（1 ～ 10、10 が最も優先度が高い場所）。 カタログサービスと同期および共有されるデータのリストは、次の場所で定義されているスキーマにあります。

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] インデックス作成クライアント検索図](assets/indexing-pipeline.svg)

1. 商人の確認 [!DNL Live Search] 使用権限
1. 属性メタデータの変更を含むストアビューを取得します。
1. インデックス作成属性を格納します。
1. 検索インデックスを再インデックスします。

### 完全なインデックス

条件 [!DNL Live Search] が設定され、オンボーディング中に同期されるので、初期インデックスの作成に最大 30 分かかる場合があります。 大きなカタログは、インデックス作成に時間がかかる場合があります。 プロセスは次の後に開始します `cron` はフィードを送信し、実行を完了します。

次のイベントは、完全同期とインデックスの構築をトリガーします。

* オンボーディング [カタログデータ同期](install.md#synchronize-catalog-data)
* 属性メタデータの変更

例えば、 `Use in Search` プロパティ `color` 属性 `No` から `Yes` 属性メタデータをに変更します。 `searchable=true`、およびトリガーの完全同期と再インデックス。 次の属性メタデータトリガーは、変更時に完全同期と再インデックスを実行します。

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### 製品アップデートのストリーミング

最初のインデックスが [オンボーディング](install.md#synchronize-catalog-data)の場合、次の増分製品アップデートが継続的に同期され、インデックスが再作成されます。

* カタログに追加された新しい製品
* 製品属性値の変更

例えば、新しいスウォッチ値を `color` 属性は、ストリーミング製品のアップデートとして処理されます。
ストリーミング更新ワークフロー：

1. 更新された製品は、Adobe Commerceインスタンスからカタログサービスに同期されます。
1. インデックス作成サービスは、カタログサービスから製品の更新を継続的に探します。 カタログサービスに到着すると、更新された製品のインデックスが作成されます。
1. 製品のアップデートがで利用できるようになるまで、最大 15 分かかる場合があります。 [!DNL Live Search].

## クライアント検索

この [!DNL Live Search] API を使用すると、クライアントは、 [storefront プロパティ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html), *製品リストの並べ替えに使用します* から `Yes`. テーマに応じて、この設定により、属性が [並べ替え基準](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) カタログページのページネーションコントロール。 最大 200 個の製品属性を [!DNL Live Search]を [storefront プロパティ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 検索可能でフィルタリング可能な
インデックスメタデータは、インデックス作成パイプラインに保存され、検索サービスからアクセスできます。

![[!DNL Live Search] インデックスメタデータ API 図](assets/index-metadata-api.svg)

### 並べ替え可能な属性のワークフロー

1. クライアントが Search Service を呼び出します。
1. 検索サービスは Search Admin Service を呼び出します。
1. 検索サービスは、インデックス作成パイプラインを呼び出します。

## すべての製品に対してインデックスが作成されます

このリストでのフィールドの順序は、書き出された製品データの一般的な列の順序を反映しています。

* `environment_id`
* `website_code`
* `store_code`
* `store_view_code`
* `product_id`
* `sku`
* `name`
* `type`
* `displayable`
* `deleted`
* `url`
* `currency`
* `meta_description`
* `meta_keyword`
* `meta_title`
* `description`
* `short_description`
* `weight`
* `image`
* `small_image`
* `thumbnail_image`
* `prices`
* `in_stock`
* `low_stock`

次のフィールドは、すべての設定可能な製品のインデックスが作成されます。

* `childrenSkus`
