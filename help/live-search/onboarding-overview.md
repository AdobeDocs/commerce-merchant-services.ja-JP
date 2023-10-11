---
title: 「オンボーディングの概要」
description: '"[!DNL Live Search] オンボーディングフロー、システム要件、境界、制限事項»'
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: a6d8c259f232ab27d7ed64558d5d193d59d23cad
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# オンボーディングの概要

を使用し始めるには、以下を実行します。 [!DNL Live Search] Adobe Commerceの場合は、オンボーディングプロセスを完了して、拡張機能をインストールし、API キーを設定して、カタログを同期します。

## 要件 {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4 以上
* PHP 8.1 / 8.2
* [!DNL Composer]

### サポートされるプラットフォーム

* Adobe Commerceオンプレミス (EE) :2.4.4 以降
* Adobe Commerce on Cloud (ECE) :2.4.4 以降

## エンドポイント

[!DNL Live Search] は、次の場所のエンドポイントを通じて通信します： `https://catalog-service.adobe.io/graphql`.

## 境界としきい値

現在、 [!DNL Live Search] 検索/カテゴリ API には、次の制限と静的境界がサポートされています。

### インデックス作成

* ストア表示あたり最大 300 個の製品属性のインデックスを作成します。
* Adobe Commerceデータベースの製品のインデックスのみを作成します。
* CMS ページはインデックス化されません。

### クエリ

* [!DNL Live Search] では、カテゴリツリーの完全な分類にアクセスできず、一部の階層的ナビゲーション検索シナリオがその範囲を超えています。
* [!DNL Live Search] は、クエリに一意のGraphQLエンドポイントを使用して、動的なファセット設定や検索（入力に応じて）などの機能をサポートします。 ただし、 [GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/)の場合、いくつかの違いがあり、一部のフィールドには完全な互換性がない場合があります。

カタログ権限を使用して顧客グループを制限するには、次の手順に従います。

* 製品はルートカテゴリに割り当てる必要があります。
* 「ログインしていません」顧客グループには、「許可」参照権限が付与されている必要があります。
* 製品を「未ログイン」顧客グループに制限するには、各カテゴリに移動し、各顧客グループに対して権限を設定します。

### ルール

* ストアビューあたりのルールの最大数は 50 です。
* ルールあたりの条件の最大数は 10 です。
* ルールあたりのイベントの最大数は 25 です。

### シノニム

* [!DNL Live Search] は、1 つのストアビューにつき最大 200 個のシノニムを管理できます。

## カテゴリマーチャンダイジング

カテゴリマーチャンダイジングを使用すると、 [!DNL Live Search] 製品カテゴリレベルで作業する場合。

このビデオでは、カテゴリマーチャンダイジングの紹介をしています。

>[!VIDEO](https://video.tv.adobe.com/v/3424617)

## Inventory management

[!DNL Live Search] サポート [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) コマースの機能 ( 以前はマルチソースインベントリ (MSI) と呼ばれていました )。 完全なサポートを有効にするには、 [更新](install.md#update) 依存モジュール `commerce-data-export` をバージョン 102.2.0 以降に変更しました。

[!DNL Live Search] 製品がInventory management内で使用可能かどうかを示すブール値を返しますが、在庫があるソースに関する情報は含まれません。

## 価格インデクサー

ライブ検索のお客様は、 [SaaS 価格インデクサー](../price-index/index.md)：価格変更の更新と同期時間を高速化します。

## PWAのサポート

[!DNL Live Search] はPWA Studioで機能しますが、他のコマース実装とは少し異なる場合があります。 Venia では検索や製品リストのページなどの基本機能は機能しますが、Graphql の順列の一部は正しく機能しない場合があります。 パフォーマンスに違いが生じる場合もあります。

* 現在のPWAの実装 [!DNL Live Search] を超える処理時間が必要です。 [!DNL Live Search] ネイティブの Commerce ストアフロントを使用します。
* [!DNL Live Search] のPWAはをサポートしていません [イベント処理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). その結果、インテリジェントマーチャンダイジングは機能しません。
* 直接のフィルター `description`, `name`, `short_description` で使用する場合、GraphQLではサポートされません [PWA](https://developer.adobe.com/commerce/pwa-studio/)が返されますが、より一般的なフィルターが返されます。

次を使用するには： [!DNL Live Search] PWA Studioを使用した場合、インテグレーターは次の操作も必要になります。

1. インストール [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. を設定します。 `environmentId` （内） `storeDetails` オブジェクト。

   ```javascript
   const storeDetails: StoreDetailsProps = {
       environmentId: <Storefront_ID>,
       websiteCode: "base",
       storeCode: "main_website_store",
       storeViewCode: "default",
       searchUnitId: searchUnitId,
       config: {
           minQueryLength: 5,
           pageSize: 8,
           currencySymbol: "$",
           },
       };
   ```

## 現在はサポートされていません

* The [詳細検索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 次の場合、モジュールは無効になります： [!DNL Live Search] がインストールされ、ストアフロントフッターの「詳細検索」リンクは削除されます。
* [価格帯](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) は、ライブ検索ポップオーバーおよび製品リストページウィジェットではサポートされていません。

## Cookie

[!DNL Live Search] は、ユーザーインタラクションデータを基本機能の一部として収集し、cookie を使用してこのデータを保存します。 ユーザー情報を収集する場合、ユーザーは Cookie の保存に同意する必要があります。 [!DNL Live Search] および [!DNL Product Recommendations] はデータストリームを共有するので、同じ cookie メカニズムを使用する必要があります。 詳しくは、 [Cookie 制限の処理](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
