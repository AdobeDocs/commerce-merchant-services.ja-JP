---
title: SaaS 価格インデックス作成のインストール
description: SaaS 価格インデックス作成のインストール
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
role: Admin, Developer
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# SaaS 価格インデックス作成のインストール

SaaS 価格のインデックス作成を行うには、新しいモジュールをインストールし、CLI コマンドを実行する必要があります。 管理者は、このインストールを完了するには、コマンドラインアクセスが必要です。

## 前提条件

* Adobe Commerce 2.4.4 以降
* 次の SaaS サービスのうち少なくとも 1 つがインストールされている。

   * [カタログサービス](../catalog-service/overview.md)
   * [ライブ検索](../live-search/guide-overview.md)
   * [製品Recommendations](../product-recommendations/guide-overview.md)

## 必要なモジュールのインストール

設定によっては、インストールプロセスが少し異なる場合があります。
新しいフィードおよびサポートコードを追加する拡張機能があり、デフォルトの価格フィードを削除する拡張機能があります。

1. 以下のモジュールを `composer.json` ファイル：

   ```json
   "magento/module-saas-price": "102.2.0",
   "magento/module-saas-scopes": "102.2.0",
   "magento/module-product-override-price-remover": "102.2.0",
   "magento/module-bundle-product-override-data-exporter": "102.2.0",
   ```

1. アップグレードコマンドを実行します。

   ```bash
   bin/magento setup:upgrade
   ```

アップグレード後、次の 3 つの新しいフィードを使用できます。

* `prices`  — サービスへの価格データの配信を担当
* `scopesCustomerGroup`  — サービスに顧客グループを配信します
* `scopesWebsite`  — サービスに Web サイト、ストアグループ、ストア表示を配信します


1. 新しいフィードを「スケジュールに従って更新」モードに設定します。

   ```bash
   bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
   ```

1. 新しいフィードのインデックスを再作成します。

   ```bash
   bin/magento saas:resync --feed=scopesCustomerGroup
   bin/magento saas:resync --feed=scopesWebsite
   bin/magento saas:resync --feed=prices
   ```

必要に応じて、上記のインデクサーを手動で実行します。 それ以外の場合は、標準の同期プロセスでデータが更新されます。 詳しくは、 [カタログ同期](../landing/catalog-sync.md) サービス。

Luma とAdobe Commerce Core GraphQLのユーザーは、 `catalog-adapter` Luma と Core GraphQl の互換性を提供し、PHP のコア価格インデクサーを無効にするモジュール。
次の手順で `catalog-adapter` モジュール [!DNL Live Search] および [!DNL Catalog Service] まず、をインストールして設定する必要があります。 フォロー： [インストール [!DNL Live Search]](../live-search/install.md) および [カタログサービスのインストール](../catalog-service/installation.md) 手順を参照してください。

Live Search とカタログアダプタを設定するには、以下に従ってください [Commerce Services コネクタ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en) 説明。

```bash
composer require adobe-commerce/catalog-adapter
```

必要に応じて、PHP のコア価格インデクサを次のコマンドで再度有効にすることができます。

```bash
bin/magento module:disable Magento_PriceIndexerDisabler
```
