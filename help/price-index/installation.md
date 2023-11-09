---
title: SaaS 価格インデックス作成手動インストール
description: 古いバージョン用の SaaS 価格インデックス作成のインストール
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
role: Admin, Developer
source-git-commit: b2ebf26c9a34e5e2e08b7adbabcc780f24363e3c
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# SaaS 価格インデックス作成手動インストール

SaaS Price Indexing は、すぐに使用でき、サポート対象 [最新バージョン](index.md#Requirements) （コマースサービス）。
最新バージョンがなく、Adobe Commerceインスタンスで SaaS Price Indexing を有効にする場合は、このガイドを使用します。

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
   "magento/module-saas-price": "^102.2.0",
   "magento/module-saas-scopes": ^"102.2.0",
   "magento/module-product-override-price-remover": "^102.2.0",
   "magento/module-bundle-product-override-data-exporter": "^102.2.0",
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

Luma とAdobe Commerce Core GraphQLのユーザーは、 [`Catalog Adapter`](catalog-adapter.md) Luma と Core GraphQl の互換性を提供し、Adobe Commerce Product Price インデクサーを無効にする拡張機能です。

## 注意事項

前 `103.0.0` バージョン、SaaS 価格インデックス作成では、シンプル、グループ化、仮想、設定可能、およびバンドルの動的な製品タイプをサポートしています。
ダウンロード可能な製品、ギフトカード、バンドル固定の製品タイプのサポートは、以下から利用できます。 `magento/module-saas-price:103.0.0` バージョンをサポートし、サポートされる Commerce Services で標準で使用できます。

新しいフィードは、 `resync` [CLI コマンド](../landing/catalog-sync.md#resynccmdline). それ以外の場合は、標準の同期プロセスでデータが更新されます。 に関する詳細情報を取得する [カタログ同期](../landing/catalog-sync.md) プロセス。
