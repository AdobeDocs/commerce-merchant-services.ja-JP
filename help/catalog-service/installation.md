---
title: オンボーディングとインストール
description: インストール方法を学ぶ [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: e11b4e86efe3483717cf4484a7fcce6e23015f4c
workflow-type: tm+mt
source-wordcount: '575'
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

## 環境

カタログサービスには、オンボーディングで使用できる環境が 2 つあります。

- サンドボックス (https://catalog-service-sandbox.adobe.io/graphql) — 運用開始前のテストおよび検証に使用
- 実稼動 (https://catalog-service.adobe.io/graphql)-コマースマーチャントや Web サイトのライブトラフィックに使用

## インストールと設定

Adobe Commerceのカタログサービスの使用を開始するには、次の手順が必要です。

- データ書き出し拡張機能のインストール
- サービスとデータのエクスポートを設定する
- サービスへのアクセス

### データ書き出し拡張機能のインストール

カタログサービスのオンボーディングプロセスでは、サーバーのコマンドラインにアクセスする必要があります。

カタログサービス拡張機能は、Adobe Commerceクラウドインフラストラクチャとオンプレミスインスタンスの両方にインストールできます。

カタログサービスは、Commerce アカウントにリンクされた Composer キーと共にインストールされます [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) 登録プロセス中に提供されます。 Composer は、Adobe Commerceの初回インストール時、または Composer のキーが以前に外部に保存されていなかった状況で、これらのキーを使用します `auth.json` ファイル。

詳しくは、 [認証キーの取得](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) を参照してください。

#### Adobe Commerce an cloud infrastructure

この方法を使用して、Commerce Cloudインスタンスのカタログサービス拡張機能をインストールします。

1. を開きます。 `<Commerce_root>/composer.json` ファイルを編集し、次のように require セクションを更新します。

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
     "magento/services-connector": "1.2.1",
     "magento/module-catalog-service-installer": "1.0.1"
   }
   ```

1. 新しい設定をローカルでテストし、依存関係を更新します。

```bash
composer update
```

このコマンドは、すべての依存関係を更新します。

1. 変更をコミットしてプッシュ `composer.json` および `composer.lock`.

#### オンプレミス

オンプレミスインスタンスのカタログサービス拡張機能をインストールするには、この方法を使用します。

1. を開きます。 `<Commerce_root>/composer.json` ファイルを編集し、次のように require セクションを更新します。

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
 "magento/services-connector": "1.2.1",
 "magento/module-catalog-service-installer": "1.0.1"
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

### サービスとデータのエクスポートを設定する

カタログサービスをインストールした後、 [Commerce Services コネクタ](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/install.html?lang=en) API キーを指定し、SaaS データ空間を選択する。

SaaS 設定が完了したら、『カタログ同期ガイド』に従って、初期データ同期を実行します。

カタログの書き出しが正しく実行されていることを確認するには、次の手順を実行します。

- cron ジョブが実行中であることを確認します。
- インデクサーが実行中であることを確認します。
- 次を確認します。 `Catalog Attributes Feed, Product Feed, Product Overrides Feed`、および `Product Variant Feed` インデクサーは「スケジュールに従って更新」に設定されます。

カタログのサイズによっては、初期同期に数分から数時間かかる場合があります。 初回同期後、カタログは、サービスを最新の状態に保つために、コマースサーバーからコマースサービスに製品データを継続的に書き出します。

### サービスへのアクセス

カタログサービス API は、HTTPS 経由でのPOSTコマンドを使用してアクセスできます。

API キーを取得するには、管理の「 Commerce Service Connector 」領域に移動し、公開 API キーをコピーします。

詳しくは、 [GraphQLドキュメント](https://developer.adobe.com/commerce/webapi/graphql/) を参照して、API リクエストの生成に必要なヘッダーをクエリして送信する方法を確認してください。

## カタログサービスと API メッシュ

この [Adobe Developer App Builder の API メッシュ](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 開発者は、AdobeI/O を使用して、プライベートまたはサードパーティの API やその他のインターフェイスをAdobe製品と統合できます。

詳しくは、  [カタログサービスと API メッシュ](mesh.md) インストールおよび設定の詳細に関するトピック。
