---
title: 「オンボーディングの概要」
description: '"[!DNL Live Search] オンボーディングフロー、システム要件、境界、制限事項»'
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 86e6fdb653278f3e70640155d697897a2ea1b674
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# オンボーディングの概要

を使用し始めるには、以下を実行します。 [!DNL Live Search] Adobe Commerceの場合は、オンボーディングプロセスを完了して、拡張機能をインストールし、API キーを設定して、カタログを同期します。

## オンボーディングフロー

![[!DNL Live Search] オンボーディング図](assets/onboarding-flow.svg)

## 要件 {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4 以上
* PHP 8.1 / 8.2
* [!DNL Composer]

### サポートされるプラットフォーム

* Adobe Commerceオンプレミス (EE) :2.4.4 以上
* Adobe Commerce on Cloud (ECE) :2.4.4 以上

## 境界としきい値

現在、 [!DNL Live Search] 検索/カテゴリ API には、次の制限と静的境界がサポートされています。

### インデックス作成

* ストア表示あたり最大 300 個の製品属性のインデックスを作成します。
* Adobe Commerceデータベースの製品のインデックスのみを作成します。
* 商品は、デフォルトの共有カタログに存在する必要があります。
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

## 価格インデクサー

ライブ検索のお客様は、 [SaaS 価格インデクサー](../price-index/index.md)：価格変更の更新と同期時間を高速化します。

### PWAサポート

ライブ検索のサポートは、一部のPWAがでテストされていないので、ベータ版と見なされます。 [!DNL Live Search]. Venia では検索や製品リストのページなどの基本機能は機能しますが、Graphql の順列の一部は正しく機能しない場合があります。

* の現在のベータPWA実装 [!DNL Live Search] を超える処理時間が必要 [!DNL Live Search] ネイティブの Commerce ストアフロントを使用します。
* [!DNL Live Search] のPWAはをサポートしていません [イベント処理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* 直接のフィルター `description`, `name`, `short_description` で使用する場合、GraphQLではサポートされません [PWA](https://developer.adobe.com/commerce/pwa-studio/)が返されますが、より一般的なフィルターが返されます。

### 現在はサポートされていません

* この [詳細検索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 次の場合、モジュールは無効になります： [!DNL Live Search] がインストールされ、ストアフロントフッターの「詳細検索」リンクは削除されます。
* 使用する複数の在庫場所 [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) またはその他の OMS 拡張
* 製品の価格は含まれません [付加価値税](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (VAT)。
* [価格帯](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) は、ライブ検索ポップオーバーおよび製品リストページウィジェットではサポートされていません。

## Cookie

[!DNL Live Search] は、ユーザーインタラクションデータを基本機能の一部として収集し、cookie を使用してこのデータを保存します。 ユーザー情報を収集する場合、ユーザーは Cookie の保存に同意する必要があります。 [!DNL Live Search] および [!DNL Product Recommendations] はデータストリームを共有するので、同じ cookie メカニズムを使用する必要があります。 詳しくは、 [Cookie 制限の処理](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
