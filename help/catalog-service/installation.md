---
title: オンボーディングとインストール
description: インストール方法を学ぶ [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: c740e75c9fe12b062683fa957d0c6623d8180e4f
workflow-type: tm+mt
source-wordcount: '432'
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

詳しくは、 [認証キーの取得](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) を参照してください。

### Adobe Commerce an cloud infrastructure

この方法を使用して、 [!DNL Catalog Service] Commerce Cloudインスタンスの拡張。

1. を開きます。 `<Commerce_root>/composer.json` ファイルを編集し、 `require` 節の内容は次のとおりです。

   ```json
   "require":{
   "magento/composer-root-update-plugin":"^2.0.2",
   "magento/magento-cloud-metapackage":">=2.4.5 <2.4.6",
   "magento/catalog-service": "^1.0.0"
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
   "magento/composer-root-update-plugin":"^2.0.2",
   "magento/catalog-service": "^1.0.0"
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


## カタログサービスと API メッシュ

この [API メッシュ](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 開発者は、AdobeI/O を使用して、プライベートまたはサードパーティの API やその他のインターフェイスをAdobe製品と統合できます。

API メッシュをカタログサービスで使用する最初の手順は、API メッシュをインスタンスに接続することです。 詳しい手順については、 [メッシュを作成する](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

設定を完了するには、 [AdobeIO CLI パッケージ](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) インストール済み

AdobeI/O でメッシュを設定したら、次のコマンドを実行して新しいメッシュを接続します。

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph"
```

このコマンドを実行した後、API メッシュを介してカタログサービスを実行する必要があります。

## カタログの書き出しを設定

インストール後 [!DNL Catalog Service]を設定する場合、 [Commerce Services コネクタ](../landing/saas.md) API キーを指定し、SaaS データ領域を選択する。

カタログの書き出しが正しく実行されていることを確認するには、次の手順を実行します。

- 確認 [cron ジョブ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) が実行中です。
- を確認します。 [indexers](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) が実行中です。
- 次を確認します。 `Catalog Attributes Feed`, `Product Feed`, `Product Overrides Feed`、および `Product Variant Feed` インデクサーは次のように設定されます。 `Update by Schedule`.

## [!DNL Catalog Service] デモ

詳しくは、このビデオをご覧ください。 [!DNL Catalog Service] インストールとテスト：

>[!VIDEO](https://video.tv.adobe.com/v/3409390?quality=12&learn=on)
