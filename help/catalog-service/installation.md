---
title: オンボーディングとインストール
description: インストール方法を学ぶ [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 41f42054a495fb815e6dcf0f2ef371bbd2c98701
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# オンボーディングとインストール

パートナーやお客様は、 [!DNL Catalog Service] (2022 年 8 月 9 日にリリースされたAdobe Commerceベータ版 ) 参加するには、以下を読み、当社に同意する必要があります。 [Adobe Commerce Beta プログラムの用語](https://experiencecloudpanel.adobe.com/h/s/6eGskQlHvLSHztsNmKCWMy).

契約に署名したら、 [#storefront-services](https://magentocommeng.slack.com/archives/C03HVPG8RS4) 公開Slackチャネル。 アドビは、 [!DNL Catalog Service] ベータ版。

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
   "require": {
    "magento/composer-root-update-plugin": "^2.0.2",
    "magento/magento-cloud-metapackage": ">=2.4.5 <2.4.6",
    "magento/saas-export": "^101.4.0",
    "magento/commerce-data-export": "^101.3.1",
    "magento/commerce-data-export-ee": "^101.3.1",
    "magento/services-id": "^3.0.1",
    "magento/services-connector": "1.2.1"
    }
   ```

   <!-- What if the customer already has other services installed, and some of these lines are already present? Do they need to delete the duplications? What if the version numbers are different? -->

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
     "magento/magento-cloud-metapackage": ">=2.4.3 <2.4.4",
     "magento/composer-root-update-plugin": "~1.1",
     "magento/saas-export": "^101.3.1",
     "magento/commerce-data-export": "^101.2.4",    
     "magento/commerce-data-export-ee": "^101.2.4",
     "magento/services-id": "^3.0.0",
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

## [!DNL Catalog Service] デモ

詳しくは、このビデオをご覧ください。 [!DNL Catalog Service] インストールとテスト：

>[!VIDEO](https://video.tv.adobe.com/v/3409390?quality=12&learn=on)
