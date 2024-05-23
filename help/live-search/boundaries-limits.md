---
title: 『境界と限界』
description: の境界と制限について説明します [!DNL Live Search] お客様のビジネスニーズを満たしていることを確認します。
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
source-git-commit: 29983ec083a49859b99c9c906710ce0a01054a50
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# 境界と制限

サイト検索に関しては、Adobe Commerceのオプションが用意されています。 以下の境界と制限をレビューして、以下を確認します [!DNL Live Search] および [!DNL Catalog Service] ビジネスのニーズに対応 コンテンツ検索、独自アルゴリズムの作成（BYOA）、属性ベースのマーチャンダイジングなどの高度な検索機能が必要な場合は、サードパーティの検索ソリューションを検討してください。

## 一般

- この [詳細検索](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) 次の場合、モジュールは無効になります [!DNL Live Search] がインストールされ、ストアフロントのフッター内の詳細検索リンクが削除されます。
- [階層の価格](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) および [特別価格](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) ではサポートされていません [!DNL Live Search] フィールドと製品一覧ページウィジェット。
- 製品価格には付加価値税（VAT）は含まれていません。
- コンテンツの検索はサポートされていません。
- ページ分割できる製品には、10,000 個の制限があります。
- 検索アダプターは、カスタム ソース モデルで作成され、ファセットとして使用される製品属性をサポートしていません。 この機能をサポートするには、 [製品一覧ページウィジェット](plp-styling.md).

## インデックス作成

- [!DNL Live Search] [索引](indexing.md) 1 つのストア表示につき最大で合計 450 個の製品属性。 これらは次のように配布されます。
   - 並べ替え可能な 50 個の属性
   - 200 フィルタリング可能な属性
   - 検索可能な属性 200
- [!DNL Live Search] は、Adobe Commerce データベースからの商品のみにインデックスを作成します。
- CMS ページにはインデックスが作成されません。
- SKU、名前、カテゴリの属性は、デフォルトで検索でき、検索から除外することはできません。 これらのカテゴリに製品を入れない場合は、カテゴリから製品の割り当てを解除してください。

## ファセット

- インデックス作成可能な 200 のフィルタリング可能な属性から、最大 100 の属性をファセットとして設定できます。
- ファセット内では、最大 30 個のバケットを返すことができます。 30 個を超えるバケットを返す必要がある場合、 [サポートチケットを作成](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) そのため、Adobeはパフォーマンスへの影響を分析し、お使いの環境でこの制限を増やすことが可能かどうかを判断できます。
- 動的ファセットは、大きなインデックスや通常のインデックスのパフォーマンスで問題を引き起こす可能性があります。 動的ファセットを作成し、パフォーマンスの低下や、タイムアウトエラーを伴うページの読み込みがない場合は、ファセットをピン留めに変更して、パフォーマンスの問題が解決するかどうかを判断してください。
- 在庫ステータス （`quantity_and_stock_status`）はファセットとしてサポートされていません。 次を使用できます `inStock: 'true'` 在庫品を除外します。 これは、の標準サポートで、 `LiveSearchAdapter` で「在庫切れの製品を表示」が「True」に設定されている場合のモジュール [!DNL Commerce] 管理者。

## クエリ

- [!DNL Live Search] ではカテゴリツリーの完全な分類にアクセスできません。これにより、リーチを超える階層ナビゲーション検索シナリオが作成されます。
- [!DNL Live Search] 一意のを使用 [GraphQL エンドポイント](https://developer.adobe.com/commerce/services/graphql/live-search/) 動的ファセットや入力時検索などの機能をサポートするクエリ用。 に似ていますが [GRAPHQL API](https://developer.adobe.com/commerce/webapi/graphql/)、いくつかの違いがあり、一部のフィールドは完全には互換性がない可能性があります。
- 検索クエリで返される結果の最大数は 10,000 個です。

## ルール

- 検索マーチャンダイジングの最大数 [個のルール](rules.md) ストア表示あたり 50 です。
- カテゴリマーチャンダイジングには、カテゴリごとに 1 つのルールを設定できます。
- ルールごとの条件の最大数は 10 です。
- ルールごとのイベントの最大数は 25 です。

## 同義語

- [!DNL Live Search] 最大 200 まで管理可能 [同義語](synonyms.md) ストア表示ごとに。
- マルチワードの同義語はサポートされていません。

## カテゴリマーチャンダイジング

- 各ストア表示に対して、カテゴリごとに 1 つのルールを作成できます。 各ルールには以下を含めることができます。
   - 最大 10 個の条件
   - 最大 25 イベント

## B2B およびカテゴリの権限

- 製品は、デフォルトの共有カタログに追加されていない場合は表示されません。
- カタログ権限を使用して顧客グループを制限するには：
   - 製品はルートカテゴリに割り当てる必要があります。
   - 「ログインしていない」顧客グループには、「許可」閲覧権限を付与する必要があります。
   - 製品を「ログインしていない」顧客グループに制限するには、各カテゴリに移動して、各顧客グループに権限を設定します。
- Live Search forPWA Studioでの B2B のサポートは現時点ではサポートされていません。
