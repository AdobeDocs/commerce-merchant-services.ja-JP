---
title: カタログ アダプタ拡張
description: カタログアダプターを使用したCommerce Services からの価格のレンダリング
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
exl-id: 2c9120eb-aa51-48e9-b6a4-fffe25fc31f2
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# カタログアダプタ

この `[!DNL Catalog Adapter]` 拡張機能は、Commerce アプリケーションに含まれているデフォルトの製品価格インデクサーを無効にし、によって提供される価格を使用します。 [カタログサービス](../catalog-service/overview.md) その代わり。

このアダプタは、 [SaaS データのエクスポート](../data-export/overview.md) とAdobe Commerce サービスも同様です。 SaaS データのエクスポートは、価格の送信を担当し、 [!DNL Catalog Adapter] Adobe Commerce サービスからすべての価格を取得します。

を有効にする場合 [!DNL Catalog Adapter]、価格のインデックス作成と操作は、次のような影響を受けます。

- Adobe Commerce アプリケーションに含まれる価格インデクサーが無効になっています。
- 価格の管理には、SaaS データのエクスポートと [SaaS 価格インデクサー](price-indexing.md).
- お客様が商品や商品の価格を表示するページを開くと、その価格はAdobe Commerce サービスから取得されます。
- 価格は、からのデータを同期してAdobe Commerce サービスに送信されます。 [SaaS データのエクスポート](../data-export/overview.md).
- チェックアウトでは価格が動的に再計算されます。

カタログアダプタ拡張機能を削除または無効にすることで、Commerce アプリケーションで価格インデックスを再度有効にすることができます。

## 要件

- Adobe Commerce 2.4.4 以降
- 次のいずれかのCommerce サービスがインストールされていること。

   - [Live Search](../live-search/install.md)
   - [製品のRecommendations](../product-recommendations/install-configure.md)
   - [カタログサービス](../catalog-service/installation.md)

## インストール

カタログ アダプタ拡張機能は、次のモジュールをインストールする Composer メタパッケージです。

- **Price Indexer Disabler** – このモジュールは、Commerce アプリケーションで価格インデックスを無効にして、SaaS 価格インデックスを使用して価格が配信されるようにします。 SaaS 価格インデックス作成拡張機能がインストールされている場合、Commerce アプリケーションの製品価格インデックス作成を有効にすることはできません。
- **価格プロバイダー**・Adobe Commerceサービスの商品の価格を提示します。 検索クエリを作成し、フロントエンドの製品の価格を取得します。
- **カタログ サービス検索アダプター** – 商品検索リクエストに応じて、Adobe CommerceアプリからAdobe Commerceサービスに価格を転送します。

## インストール手順

>[!BEGINTABS]

>[!TAB クラウドインフラストラクチャ]

このメソッドを使用して、 [!DNL Catalog Adapter] Commerce Cloudインスタンスの場合。

1. ローカルワークステーションで、Adobe Commerce on cloud infrastructure プロジェクトのプロジェクトディレクトリに移動します。

   >[!NOTE]
   >
   >Commerce プロジェクト環境のローカル管理については、を参照してください。 [CLI によるブランチの管理](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) が含まれる _Adobe Commerce on Cloud Infrastructure ユーザーガイド_.

1. Adobe Commerce Cloud CLI を使用して更新する環境ブランチを確認します。

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. カタログアダプタモジュールを追加します。

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. パッケージの依存関係を更新します。

   ```bash
   composer update "magento/catalog-adapter"
   ```

1. のコード変更をコミットしてプッシュします `composer.json` および `composer.lock` ファイル。

1. のコード変更の追加、コミット、プッシュ `composer.json` および `composer.lock` ファイルをクラウド環境に送信します。

   ```shell
   git add -A
   git commit -m "Add catalog adapter module"
   git push origin <branch-name>
   ```

   更新をクラウド環境にプッシュすると、が開始されます [Commerce cloud のデプロイメントプロセス](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) 変更を適用します。 からデプロイメントステータスを確認します。 [ログをデプロイ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB オンプレミス]

このメソッドを使用して、 [!DNL Catalog Adapter] オンプレミスのインスタンスの場合。

1. Composer を使用して、プロジェクトにカタログアダプタを追加します。

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. 依存関係を更新し、拡張機能をインストールします。

   ```bash
   composer update  "magento/catalog-adapter"
   ```

1. Adobe Commerceをアップグレード :

   ```bash
   bin/magento setup:upgrade
   ```

1. キャッシュをクリアする：

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >場合によっては（特に実稼動環境にデプロイする場合）、コンパイル済みのコードは時間がかかるので、クリアしないようにしたい場合があります。 変更を加える前に、システムを必ずバックアップしてください。

>[!ENDTABS]


## Adobe Commerce製品価格インデクサーを再度有効にします。

デフォルトのAdobe Commerce product price indexer に依存するサードパーティアプリケーションがある場合は、次のコマンドを使用して再度有効にすることができます。

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# re-index Product Price indexer
bin/magento index:reindex catalog_product_price
```

## ヘッドレスストアフロントシナリオに対する製品価格インデクサーの無効化

ヘッドレス Commerce インスタンスがある場合は、Adobe Commerce product price indexer を無効にして、Adobe Commerce インスタンスの負荷を軽減する必要がある場合があります。 このタスクを完了するには、をインストールします `magento/module-price-indexer-disabler` モジュール：

```bash
composer require magento/module-price-indexer-disabler
```

## 使用シナリオ

一般的なコマンドの一部を次に示します `[!DNL Catalog Adapter]` シナリオ。

### Adobe Commerce product price indexer に依存しない

- 必要なサービス（Live Search、Product Recommendations、Catalog Service）がインストールされている、Luma またはAdobe Commerce Core GraphQL マーチャントです
- Adobe Commerce product price indexer に依存するサードパーティの拡張機能との統合はありません。

1. のインストール [!DNL Catalog Adapter].

### Adobe Commerce product price indexer に依存する

- サポートされているサービス（Live Search、Product Recommendations、Catalog Service）がインストールされている、Luma またはAdobe Commerce Core GraphQL マーチャントです
- Adobe Commerce product price indexer に基づくサードパーティの拡張機能を使用します。

1. のインストール [!DNL Catalog Adapter].
1. デフォルトのAdobe Commerce製品価格インデクサーを再度有効にします。

### ヘッドレス Commerce インスタンス

- 必要なサービスがインストールされたヘッドレス Commerce インスタンス（Live Search、Product Recommendations、Catalog Service）を持つマーチャント
- デフォルトのAdobe Commerce製品価格インデクサーに依存しない

1. のインストール `magento/module-price-indexer-disabler` からのモジュール [!DNL Catalog Adapter] パッケージ。

