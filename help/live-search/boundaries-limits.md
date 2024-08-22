---
title: 『境界と限界』
description: ビジネスのニーズを確実に満たすための  [!DNL Live Search]  の境界と制限について説明します。
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
source-git-commit: ffbb41ef2bc940982b4acb33623ef689542617c1
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 0%

---

# 境界と制限

サイト検索に関しては、Adobe Commerceのオプションが用意されています。 次の境界と制限を確認して、[!DNL Live Search] と [!DNL Catalog Service] がビジネスのニーズを満たしていることを確認します。 コンテンツ検索、独自アルゴリズムの作成（BYOA）、属性ベースのマーチャンダイジングなどの高度な検索機能が必要な場合は、サードパーティの検索ソリューションを検討してください。

## 一般

- [!DNL Live Search] がインストールされている場合は [ 詳細検索 ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) モジュールが無効になり、ストアフロントフッターの詳細検索リンクが削除されます。
- [Tier Pricing](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) および [Special Pricing](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) は、[!DNL Live Search] フィールドおよび製品一覧ページウィジェットではサポートされていません。
- 製品価格には付加価値税（VAT）は含まれていません。
- コンテンツの検索はサポートされていません。
- ページ分割できる製品には、10,000 個の制限があります。
- 属性には、説明やカスタム属性を含め、1MB のハード制限があります。
- 検索アダプターは、カスタム ソース モデルで作成され、ファセットとして使用される製品属性をサポートしていません。 この機能をサポートするには、[ 製品一覧ページウィジェット ](plp-styling.md) を使用する必要があります。

## インデックス作成

- 1 つのストア表示につき最大 450 個の製品属性を [!DNL Live Search] [ インデックス ](indexing.md) します。 これらは次のように配布されます。
   - 並べ替え可能な 50 個の属性
   - 200 フィルタリング可能な属性
   - 検索可能な属性 200
- [!DNL Live Search] は、Adobe Commerce データベースからの商品のみにインデックスを作成します。
- CMSページにはインデックスが作成されません。
- SKU、名前、カテゴリの属性は、デフォルトで検索でき、検索から除外することはできません。 これらのカテゴリに製品を入れない場合は、カテゴリから製品の割り当てを解除してください。

## ファセット

- インデックス作成可能な 200 のフィルタリング可能な属性から、最大 100 の属性をファセットとして設定できます。
- ファセット内では、最大 30 個のバケットを返すことができます。 30 を超えるバケットを返す必要がある場合は、[ サポートチケットを作成 ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) します。これにより、Adobeはパフォーマンスへの影響を分析し、お使いの環境でこの制限を増やすことが可能かどうかを判断できます。
- 動的ファセットは、大きなインデックスや通常のインデックスのパフォーマンスで問題を引き起こす可能性があります。 動的ファセットを作成し、パフォーマンスの低下や、タイムアウトエラーを伴うページの読み込みがない場合は、ファセットをピン留めに変更して、パフォーマンスの問題が解決するかどうかを判断してください。
- 在庫状態（`quantity_and_stock_status`）はファセットとしてサポートされていません。 `inStock: 'true'` を使用して、在庫製品を除外できます。 [!DNL Commerce] 管理者で「在庫切れの製品を表示」が「True」に設定されている場合、これは `LiveSearchAdapter` モジュールの初期設定でサポートされています。
- 日付タイプ属性はファセットとしてサポートされていません。

## クエリ

- [!DNL Live Search] では、クエリで一意の [GraphQL エンドポイント ](https://developer.adobe.com/commerce/services/graphql/live-search/) を使用して、動的なファセットや入力に応じた検索などの機能をサポートしています。 [GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/) と似ていますが、いくつかの違いがあり、一部のフィールドは完全な互換性がない場合があります。
- 検索クエリで返される結果の最大数は 10,000 個です。
- 日付タイプの属性を使用して結果をフィルタリングすることはできません。

## ルール

- ストア表示あたりの検索マーチャンダイジング [ ルール ](rules.md) の最大数は 50 です。
- カテゴリマーチャンダイジングには、カテゴリごとに 1 つのルールを設定できます。
- ルールごとの条件の最大数は 10 です。
- ルールごとのイベントの最大数は 25 です。
- 応答がページ分割される際に予期しない結果が生じるのを防ぐため、ピン留めされた製品の数がリクエストされたページサイズを超えないようにしてください。

## 同義語

- 1 つ [!DNL Live Search] ストア表示で最大 200 個の [ 同義語 ](synonyms.md) を管理できます。
- 複数の単語の同義語は、常に期待どおりに動作するとは限りません。 これらの同義語は、関連性に悪影響を及ぼす可能性があるので、実稼動で使用する前に、ステージング環境でテストしてください。

## カテゴリマーチャンダイジング

- 各ストア表示に対して、カテゴリごとに 1 つのルールを作成できます。 各ルールには以下を含めることができます。
   - 最大 10 個の条件
   - 最大 25 イベント

## B2B およびカテゴリの権限

- 製品は、デフォルトの共有カタログに追加されていない場合は表示されません。
- [ カテゴリ権限 ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions) を使用して顧客グループを制限するには：
   - 製品はルートカテゴリに割り当てる必要があります。
   - 「ログインしていない」顧客グループには、「許可」閲覧権限を付与する必要があります。
   - 製品を「ログインしていない」顧客グループに制限するには、各カテゴリに移動して、各 [ 顧客グループ ](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage) に権限を設定します。
- PWA Studioで PLP ウィジェットを使用した B2B の標準サポートは、現時点ではサポートされていません。 ただし、この機能を実装するには [API を使用 ](install.md#pwa-support) できます。
- [!DNL Live Search] のカテゴリファセットには、特定の [ 顧客グループ ](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage) に表示できないカテゴリが表示される場合があります。
- 最大 1,000 の顧客グループをサポートで [!DNL Live Search] ます。

## [!DNL Storefront popover]

- [[!DNL popover]](storefront-popover.md) は、*Luma* テーマを使用するストア、または *Luma* に基づいてカスタマイズされたテーマでのみ使用できます。 検索結果ページのパンくずリストには *Luma* スタイルが設定されません。
- [!DNL popover] は *Blank* テーマをサポートしていません。
- [!DNL popover] は、クイックオーダーフォームではサポートされていません。
- ウィッシュリストと製品の比較はサポートされていません。
