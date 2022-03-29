---
title: オンボーディングの概要
description: ライブ検索のオンボーディングフロー、必要システム構成、境界、制限
source-git-commit: 6220824c6032a33a760fe5c2bb5d2346e00a074b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# オンボーディングの概要

Adobe Commerceのライブ検索の使用を開始するには、いくつかのオンボーディング手順を実行して、拡張機能をインストールし、API キーを設定し、カタログを同期する必要があります。

## オンボーディングフロー

![ライブ検索のオンボーディング図](assets/onboarding-flow.svg)

## 要件 {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4
* [!DNL Composer]

### サポートされるプラットフォーム

* Adobe Commerceオンプレミス (EE) :2.4.x
* Adobe Commerce on Cloud (ECE) :2.4.x

## 境界としきい値

現時点では、ライブ検索/カテゴリ API には、次の制限および静的境界がサポートされています。

### インデックス作成

* ストア表示あたり最大 300 個の製品属性のインデックス
* Adobe Commerceデータベースの製品のインデックスのみを作成します
* CMS ページのインデックスを作成しない

### クエリの制限

* ライブ検索は、カテゴリツリーの完全な分類にアクセスできず、一部の階層的なナビゲーション検索シナリオがその範囲を超えて作成されます。
* ライブ検索は、クエリに一意の GraphQL エンドポイントを使用して、インテリジェントなファセット設定や、タイプごとの検索などの機能をサポートします。 ただし、 [MagentoGraphQL API](https://devdocs.magento.com/guides/v2.4/graphql)の場合は、いくつかの違いがあり、一部のフィールドは現時点で完全に互換性がない可能性があります。

### PWAベータリリース

* ライブ検索PWAのベータ版リリースはサポートしていません [イベント処理](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).
* 以下の製品属性は、のベータ版リリースと関連して使用された場合、GraphQL ではサポートされません。 [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### 現時点ではサポートされていません

* この [詳細検索](https://docs.magento.com/user-guide/catalog/search-advanced.html) モジュールは、ライブ検索がインストールされている場合は無効になり、ストアフロントフッターの詳細検索リンクは削除されます。
* [顧客グループ](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [カスタム価格グループ](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* 使用する複数の在庫場所 [MCOM](https://docs.magento.com/user-guide/mcom.html) またはその他の OMS 拡張
* [統合 B2B 機能](https://business.adobe.com/products/magento/b2b-ecommerce.html)
