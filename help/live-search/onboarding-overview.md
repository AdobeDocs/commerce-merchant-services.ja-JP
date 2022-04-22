---
title: オンボーディングの概要
description: ライブ検索のオンボーディングフロー、必要システム構成、境界、制限
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: f2934746c327528d5d52f2ae356afe303ff9b81b
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# オンボーディングの概要

を使用し始めるには、以下を実行します。 [!DNL Live Search] Adobe Commerceの場合は、オンボーディングプロセスを完了して、拡張機能をインストールし、API キーを設定して、カタログを同期します。

## オンボーディングフロー

![[!DNL Live Search] オンボーディング図](assets/onboarding-flow.svg)

## 要件 {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4 / 8.1
* [!DNL Composer]

### サポートされるプラットフォーム

* Adobe Commerceオンプレミス (EE) :2.4.x
* Adobe Commerce on Cloud (ECE) :2.4.x

## 境界としきい値

この時点で、 [!DNL Live Search] 検索/カテゴリ API には、次の制限と静的境界がサポートされています。

### インデックス作成

* ストア表示あたり最大 300 個の製品属性のインデックス
* Adobe Commerceデータベースの製品のインデックスのみを作成します
* CMS ページのインデックスを作成しない

### クエリの制限

* [!DNL Live Search] では、カテゴリツリーの完全な分類にアクセスできず、一部の階層的ナビゲーション検索シナリオがその範囲を超えています。
* [!DNL Live Search] は、クエリに一意の GraphQL エンドポイントを使用して、インテリジェントなファセット設定や、ユーザータイプでの検索などの機能をサポートします。 ただし、 [MagentoGraphQL API](https://devdocs.magento.com/guides/v2.4/graphql)の場合は、いくつかの違いがあり、一部のフィールドは現時点で完全に互換性がない可能性があります。

### PWAベータリリース

* 現在の Live Search のベータPWA実装では、ネイティブの Commerce ストアフロントを使用した Live Search よりも検索結果を返すのに、より多くの処理時間が必要です。
* のPWAのベータリリース [!DNL Live Search] はをサポートしていません [イベント処理](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).
* 以下の製品属性は、のベータ版リリースと関連して使用された場合、GraphQL ではサポートされません。 [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### 現時点ではサポートされていません

* この [詳細検索](https://docs.magento.com/user-guide/catalog/search-advanced.html) 次の場合、モジュールは無効になります： [!DNL Live Search] がインストールされ、ストアフロントフッターの「詳細検索」リンクは削除されます。
* [顧客グループ](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [カスタム価格グループ](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* 使用する複数の在庫場所 [MCOM](https://docs.magento.com/user-guide/mcom.html) またはその他の OMS 拡張
* [統合 B2B 機能](https://business.adobe.com/products/magento/b2b-ecommerce.html)
* 製品の価格は含まれません [付加価値税](https://docs.magento.com/user-guide/tax/vat.html) (VAT)。
* 在庫切れの製品は、 [在庫オプション](https://docs.magento.com/user-guide/catalog/inventory-options-global.html) 設定。
