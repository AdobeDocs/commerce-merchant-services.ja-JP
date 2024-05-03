---
title: 「インデックス作成」
description: 方法 [!DNL Live Search] では、製品属性プロパティのインデックスを作成します。"
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# インデックス作成

この [!DNL Live Search] インデックス作成プロセスは、カタログを読み取って製品属性を取得し、製品をすばやく検索、フィルタリング、提示できるようにインデックスを作成します。

製品属性プロパティ（メタデータ）によって次が決まります。

* カタログでの属性の使用方法
* ストア内の外観と動作
* データ転送操作に含まれるデータ

属性メタデータの範囲はです。 `website/store/store view`.

この [!DNL Live Search] API を使用すると、クライアントは以下を持つ任意の製品属性で並べ替えることができます [storefront プロパティ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` をに設定 `Yes` Adobe Commerce Admin. 有効な場合、 `Search Weight` および `Visible in Advanced Search` 属性に設定できます。

[!DNL Live Search] は、削除された製品またはに設定された製品のインデックスを作成しません `Not Visible Individually`.

>[!NOTE]
>
> を使用するCommerceのお客様 [!DNL Live Search] を使用すると、web サイトでの価格変更の更新と同期時間を短縮できます。 [SaaS 価格インデクサー](../price-index/price-indexing.md).

## インデックス作成パイプライン

クライアントはストアフロントから検索サービスを呼び出して、（フィルタリング可能、並べ替え可能な）インデックスメタデータを取得します。 を持つ検索可能な製品属性のみ *レイヤーナビゲーションでの使用* プロパティの設定 `Filterable (with results)` および *製品リストでの並べ替えに使用* をに設定 `Yes` 検索サービスで呼び出すことができます。
動的クエリを作成するには、検索サービスが検索可能な属性とその属性を把握している必要があります [重み](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html#weighted-search). [!DNL Live Search] は、Adobe Commerce検索の重み付け（1 ～ 10、10 が最も優先度が高い）に従います。 カタログサービスで同期および共有されるデータのリストは、スキーマで見つけることができます。このスキーマは、次で定義されています。

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] インデックス作成，クライアント検索ダイアグラム](assets/indexing-pipeline.svg)

1. のマーチャントを確認 [!DNL Live Search] 使用権限。
1. 属性メタデータの変更を含むストアビューを取得します。
1. インデックス属性を保存します。
1. 検索インデックスの再作成。

### 完全インデックス

条件 [!DNL Live Search] は、オンボーディング中に設定および同期されます。初期インデックスの作成には最大 60 分かかる場合があります。 大規模なカタログのインデックス作成には時間がかかる場合があります。 プロセスは次の時間が経過した後に開始されます `cron` フィードを送信し、実行を完了します。

次のイベントは、完全同期とインデックスのビルドをトリガーにします。

* オンボーディング [カタログデータ同期](install.md#synchronize-catalog-data)
* 属性メタデータの変更

例えば、 `Use in Search` のプロパティ `color` 属性元 `No` 対象： `Yes` 属性メタデータをに変更します `searchable=true`を指定し、フル同期と再インデックスをトリガーします。 次の属性メタデータトリガーは、変更時に完全な同期と再インデックスを行います。

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### 製品アップデートのストリーミング

最初のインデックスが次の期間で作成された後 [オンボーディング](install.md#synchronize-catalog-data)では、次の製品の増分更新が継続的に同期され、インデックスが再作成されます。

* カタログに新しい製品が追加されました
* 製品属性値の変更

例えば、新しいスウォッチ値をに追加します。 `color` 属性はストリーミング製品の更新として処理されます。
ストリーミング更新ワークフロー：

1. 更新された製品は、Adobe Commerce インスタンスからカタログサービスに同期されます。
1. インデックス サービスは、カタログ サービスから製品の更新を継続的に検索します。 更新された製品には、カタログサービスに到着した時点でインデックスが付けられます。
1. 製品アップデートがで使用可能になるまで、最大 15 分かかる場合があります。 [!DNL Live Search].

## クライアント検索

この [!DNL Live Search] API を使用すると、クライアントは [storefront プロパティ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html), *製品リストでの並べ替えに使用されます* 対象： `Yes`. テーマによりますが、この設定を使用すると、属性がのオプションとして含まれます。 [並べ替え](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) カタログページのページネーション制御。 インデックスを作成できる製品属性は、最大 200 個です。 [!DNL Live Search]、を含む [storefront プロパティ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) これは検索およびフィルタリングが可能です。
インデックスメタデータはインデックスパイプラインに保存され、検索サービスからアクセスできます。

![[!DNL Live Search] インデックスメタデータ API の図](assets/index-metadata-api.svg)

### 並べ替え可能な属性ワークフロー

1. クライアントが検索サービスを呼び出します。
1. Search Service は、Search Admin Service を呼び出します。
1. 検索サービスがインデックスパイプラインを呼び出します。

## すべての商品に対してインデックスを作成

このリストのフィールドの順序は、書き出された製品データの一般的な列の順序を反映しています。

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

次のフィールドは、設定可能なすべての製品に対してインデックスが作成されています。

* `childrenSkus`
