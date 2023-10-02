---
title: カタログアダプタ拡張
description: カタログアダプタを使用してコマースサービスから価格をレンダリングする
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
source-git-commit: 6b578e7113c278a05a64f2db5e032bccc4a9580a
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---


# カタログアダプタ

The `Catalog Adapter` 拡張機能を使用すると、デフォルトのAdobe Commerce Product Price インデクサーが無効になり、代わりに、 [カタログサービス](../catalog-service/overview.md).
Adobe Commerce Product Price Indexer は無効になっており、これらの拡張機能モジュールがインストールされていると、有効にできません。 この拡張機能を削除または無効にすることでのみ、デフォルトの製品価格インデクサーを再度有効にできます。

## 要件

* Adobe Commerce 2.4.4 以降
* 次の Commerce Services のいずれかがインストールされています。

   * [カタログサービス](../catalog-service/overview.md)
   * [ライブ検索](../live-search/guide-overview.md)

## インストール

次の手順で `catalog-adapter` モジュール [!DNL Live Search] および [!DNL Catalog Service] まず、をインストールして設定する必要があります。 フォロー： [インストール [!DNL Live Search]](../live-search/install.md) および [カタログサービスのインストール](../catalog-service/installation.md) 手順を参照してください。

これらのサービスがインストールされたら、次のコマンドを実行します。

```bash
composer require adobe-commerce/catalog-adapter
```

## Adobe Commerce Product Price インデクサーの再有効化

デフォルトのAdobe Commerce Product Price インデクサーに依存するサードパーティアプリケーションがある場合は、次のコマンドを使用して再度有効にできます。

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# reindex Product Price indexer 
bin/magento index:reindex catalog_product_price
```

## ヘッドレスストアフロントシナリオの製品価格インデクサーを無効にする

ヘッドレスコマースインスタンスがある場合、Adobe Commerceインスタンスの負荷を軽減するために、場合によってはAdobe Commerce製品価格インデクサーを無効にする必要があります。
これは、 `magento/module-price-indexer-disabler` モジュール：

```bash
composer require magento/module-price-indexer-disabler
```

## 使用シナリオ

次に、一般的な例を示します。 `Catalog Adapter` シナリオ。

### Adobe Commerce Product Price インデクサーに依存しません

* 必要なサービス ( ライブ検索、製品Recommendations、カタログサービス ) がインストールされている Luma またはAdobe Commerce Core GraphQLのマーチャントです。
* Adobe Commerce Product Price インデクサーに依存するサードパーティの拡張機能はありません

1. カタログアダプタをインストールします。

### Adobe Commerce Product Price インデクサーに依存

* サポート対象のサービス ( ライブ検索、製品Recommendations、カタログサービス ) がインストールされている Luma またはAdobe Commerce Core GraphQLのマーチャントです。
* Adobe Commerce Product Price インデクサーに依存するサードパーティの拡張機能を使用する

1. カタログアダプタをインストールします。
1. デフォルトのAdobe Commerce Product Price インデクサーを再度有効にします。

### ヘッドレスコマースインスタンス

* 必要なサービスがインストールされたヘッドレスコマースインスタンス ( ライブ検索、製品Recommendations、カタログサービス ) を持つマーチャント
* デフォルトのAdobe Commerce製品価格のインデクサーに依存しない

1. カタログアダプタパッケージから「価格無効」をインストールします。
