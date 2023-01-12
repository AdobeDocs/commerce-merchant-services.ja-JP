---
title: オンボーディングとインストール
description: インストール方法を学ぶ [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# オンボーディングとインストール

## 前提条件

のオンボーディングプロセス [!DNL Catalog Service] は、サーバーのコマンドラインへのアクセスを必要とします。 コマンドラインでの作業に慣れていない場合は、開発者またはシステムインテグレーターに問い合わせてください。

### ソフトウェア要件

- Adobe Commerce 2.4.x
- PHP 8.1, 7.4, 7.3
- コンポーザー：2.x, 1.x

### サポートされるプラットフォーム

- Adobe Commerce on cloud infrastructure:2.4.x
- Adobe Commerceオンプレミス：2.4.x

## 拡張機能のインストール

次をインストールできます： [!DNL Catalog Service] クラウドインフラストラクチャ上のAdobe Commerceとオンプレミスインスタンスの両方の拡張機能。

この [!DNL Catalog Service] は、Commerce アカウントにリンクされた Composer キーと共にインストールされます [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) 登録プロセスで提供されます。 Composer は、 [!DNL Adobe Commerce]または、Composer のキーが以前に `auth.json` ファイル。

詳しくは、 [認証キーの取得](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) を参照してください。

### Adobe Commerce an cloud infrastructure

この方法を使用して、 [!DNL Catalog Service] Commerce Cloudインスタンスの拡張。

1. を開きます。 `<Commerce_root>/composer.json` ファイルを編集し、 `require` 節の内容は次のとおりです。

   ```json
   "require": {
      "magento/module-saas-catalog": "^101.4.0",
      "magento/module-saas-product-override": "^101.4.0",
      "magento/module-saas-product-variant": "^101.4.0",
      "magento/module-bundle-product-data-exporter": "^101.3.1",
      "magento/module-catalog-data-exporter": "^101.3.1",
      "magento/module-catalog-inventory-data-exporter": "^101.3.1",
      "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
      "magento/module-configurable-product-data-exporter": "^101.3.1",
      "magento/module-data-exporter": "^101.3.1",
      "magento/module-parent-product-data-exporter": "^101.3.1",
      "magento/module-product-override-data-exporter": "^101.3.1",
      "magento/data-services": "^7.0.11",
      "magento/services-id": "^3.0.1",
      "magento/services-connector": "1.2.1"
    }
   ```

1. 新しい設定をローカルでテストし、依存関係を更新します。

   ```bash
   composer update
   ```

   このコマンドは、すべての依存関係を更新します。

1. 変更をコミットしてプッシュ `composer.json` および `composer.lock`.

### オンプレミス

この方法を使用して、 [!DNL Catalog Service] オンプレミスインスタンスの拡張。

1. を開きます。 `<Commerce_root>/composer.json` ファイルを編集し、 `require` 節の内容は次のとおりです。

   ```json
   "require": {
    "magento/module-saas-catalog": "^101.4.0",
    "magento/module-saas-product-override": "^101.4.0",
    "magento/module-saas-product-variant": "^101.4.0",
    "magento/module-bundle-product-data-exporter": "^101.3.1",
    "magento/module-catalog-data-exporter": "^101.3.1",
    "magento/module-catalog-inventory-data-exporter": "^101.3.1",
    "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
    "magento/module-configurable-product-data-exporter": "^101.3.1",
    "magento/module-data-exporter": "^101.3.1",
    "magento/module-parent-product-data-exporter": "^101.3.1",
    "magento/module-product-override-data-exporter": "^101.3.1",
    "magento/data-services": "^7.0.11",
    "magento/services-id": "^3.0.1",
    "magento/services-connector": "1.2.1"
   }
   ```

1. 依存関係を更新し、拡張機能をインストールします。

   ```bash
   composer update
   ```

   このコマンドは、すべての依存関係を更新します。

1. Adobe Commerceをアップグレード：

   ```bash
   bin/magento setup:upgrade
   ```

1. キャッシュをクリアします。

   ```bash
   bin/magento cache:clean
   ```

## カタログの書き出しを設定

インストール後 [!DNL Catalog Service]を設定する場合、 [Commerce Services コネクタ](../landing/saas.md) API キーを指定し、SaaS データ領域を選択する。

カタログの書き出しが正しく実行されていることを確認するには、次の手順を実行します。

- 確認 [cron ジョブ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) が実行中です。
- を確認します。 [indexers](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) が実行中です。
- 次を確認します。 `Catalog Attributes Feed`, `Product Feed`, `Product Overrides Feed`、および `Product Variant Feed` インデクサーは次のように設定されます。 `Update by Schedule`.

## カタログサービスと API メッシュ

この [Adobe Developer App Builder の API メッシュ](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 開発者は、AdobeI/O を使用して、プライベートまたはサードパーティの API やその他のインターフェイスをAdobe製品と統合できます。

API メッシュをカタログサービスで使用する最初の手順は、API メッシュをインスタンスに接続することです。 詳しい手順については、 [メッシュを作成する](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

設定を完了するには、 [AdobeIO CLI パッケージ](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) インストール済み

AdobeI/O でメッシュを設定したら、次のコマンドを実行して、 `CommerceCatalogServiceGraph` メッシュにソースを設定します。

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

場所 `variables.json` は、AdobeI/O に一般的に使用される値を保存する個別のファイルです。
例えば、API キーはファイル内に保存できます。

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

このコマンドを実行した後、API メッシュを介してカタログサービスを実行する必要があります。 次を実行できます。 `aio api-mesh:get` コマンドを使用して、更新したメッシュの設定を表示します。

## [!DNL Catalog Service] デモ

詳しくは、このビデオをご覧ください。 [!DNL Catalog Service] インストールとテスト：

>[!VIDEO](https://video.tv.adobe.com/v/3409390?quality=12&learn=on)
