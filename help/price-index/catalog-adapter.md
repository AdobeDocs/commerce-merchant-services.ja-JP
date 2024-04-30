---
title: カタログ アダプタ拡張
description: カタログアダプターを使用したCommerce Services からの価格のレンダリング
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
exl-id: 2c9120eb-aa51-48e9-b6a4-fffe25fc31f2
source-git-commit: 7d62f8d5539cd744e98d8d6c072d77a2a7c5a256
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# カタログアダプタ

この `Catalog Adapter` 拡張機能では、デフォルトのAdobe Commerce Product Price Indexer を無効にし、代わりに [カタログサービス](../catalog-service/overview.md).
Adobe Commerce Product Price Indexer は無効になっており、これらの拡張機能モジュールをインストールした状態ではオンにできません。 この拡張機能を削除または無効にした場合にのみ、デフォルトの製品価格インデクサーを再度有効にすることができます。

## 要件

* Adobe Commerce 2.4.4 以降
* 次の両方のCommerce サービスがインストールされていること。

   * [カタログサービス](../catalog-service/overview.md)
   * [Live Search](../live-search/overview.md)

## インストール

を使用するには `catalog-adapter` モジュール、 [!DNL Live Search] および [!DNL Catalog Service] 最初にインストールおよび設定を行う必要があります。 に従う [インストール [!DNL Live Search]](../live-search/install.md) および [Catalog Service のインストール](../catalog-service/installation.md) 続行する前の手順。

これらのサービスをインストールしたら、次のコマンドを実行します。

```bash
composer require adobe-commerce/catalog-adapter
```

## Adobe Commerce製品価格インデクサーを再度有効にします。

デフォルトのAdobe Commerce Product Price Indexer に依存するサードパーティアプリケーションがある場合は、次のコマンドで再度有効にすることができます。

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# re-index Product Price indexer 
bin/magento index:reindex catalog_product_price
```

## ヘッドレスストアフロントシナリオに対する製品価格インデクサーの無効化

ヘッドレス Commerce インスタンスがある場合は、Adobe Commerce Product Price Indexer を無効にして、Adobe Commerce インスタンスの負荷を軽減する必要がある場合があります。
これを行うには、 `magento/module-price-indexer-disabler` モジュール：

```bash
composer require magento/module-price-indexer-disabler
```

## 使用シナリオ

一般的なコマンドの一部を次に示します `Catalog Adapter` シナリオ。

### Adobe Commerce Product Price Indexer に依存しない

* 必要なサービス（Live Search、Product Recommendations、Catalog Service）がインストールされている、Luma またはAdobe Commerce Core GraphQL マーチャントです
* Adobe Commerce Product Price Indexer に依存するサードパーティの拡張機能はありません

1. カタログアダプタをインストールします。

### Adobe Commerce Product Price Indexer に依存する

* サポートされているサービス（Live Search、Product Recommendations、Catalog Service）がインストールされている、Luma またはAdobe Commerce Core GraphQL マーチャントです
* Adobe Commerce Product Price Indexer に基づくサードパーティの拡張機能を使用します。

1. カタログアダプタをインストールします。
1. デフォルトのAdobe Commerce Product Price Indexer を再度有効にします。

### ヘッドレス Commerce インスタンス

* 必要なサービスがインストールされたヘッドレス Commerce インスタンス（Live Search、Product Recommendations、Catalog Service）を持つマーチャント
* デフォルトのAdobe Commerce Product Price Indexer に依存しない

1. のインストール `magento/module-price-indexer-disabler` カタログアダプターパッケージからのモジュール。
