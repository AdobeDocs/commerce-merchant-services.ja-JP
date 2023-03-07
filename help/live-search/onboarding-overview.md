---
title: 「オンボーディングの概要」
description: '"[!DNL Live Search] オンボーディングフロー、システム要件、境界、制限事項»'
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 484319fc1df6c29c972b57c13bd0ed711e374e99
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# オンボーディングの概要

を使用し始めるには、以下を実行します。 [!DNL Live Search] Adobe Commerceの場合は、オンボーディングプロセスを完了して、拡張機能をインストールし、API キーを設定して、カタログを同期します。

## オンボーディングフロー

![[!DNL Live Search] オンボーディング図](assets/onboarding-flow.svg)

## 要件 {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.4 以上
* PHP 8.1, 8.2
* [!DNL Composer]

### サポートされるプラットフォーム

* Adobe Commerceオンプレミス (EE) :2.4.4 以上
* Adobe Commerce on Cloud (ECE) :2.4.4 以上

## 境界としきい値

この時点で、 [!DNL Live Search] 検索/カテゴリ API には、次の制限と静的境界がサポートされています。

### インデックス作成

* ストア表示あたり最大 300 個の製品属性のインデックスを作成します。
* Adobe Commerceデータベースの製品のインデックスのみを作成します。
* CMS ページはインデックス化されません。

### クエリ

* [!DNL Live Search] では、カテゴリツリーの完全な分類にアクセスできず、一部の階層的ナビゲーション検索シナリオがその範囲を超えています。
* [!DNL Live Search] は、一意のGraphQLエンドポイントをクエリに使用して、インテリジェントなファセット設定や、ユーザー入力として検索などの機能をサポートします。 ただし、 [MagentoGraphQL API](https://developer.adobe.com/commerce/webapi/graphql/)の場合は、いくつかの違いがあり、一部のフィールドは現時点で完全に互換性がない可能性があります。

### ルール

* ストアビューあたりのルールの最大数は 50 です。
* ルールあたりの条件の最大数は 10 です。
* ルールあたりのイベントの最大数は 25 です。

### シノニム

* [!DNL Live Search] は、1 つのストアビューにつき最大 200 個のシノニムを管理できます。

### PWAベータリリース

* 現在の Live Search のベータPWA実装では、ネイティブの Commerce ストアフロントを使用した Live Search よりも検索結果を返すのに、より多くの処理時間が必要です。
* のPWAのベータリリース [!DNL Live Search] はをサポートしていません [イベント処理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* 以下の製品属性は、のベータ版リリースとの関連で使用された場合、GraphQLでサポートされません。 [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### 現時点ではサポートされていません

* この [詳細検索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 次の場合、モジュールは無効になります： [!DNL Live Search] がインストールされ、ストアフロントフッターの「詳細検索」リンクは削除されます。
* [カスタム価格グループ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-group.html)
* 使用する複数の在庫場所 [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) またはその他の OMS 拡張
* 製品の価格は含まれません [付加価値税](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (VAT)。
