---
title: オンボーディングとインストール
description: インストール方法を学ぶ [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: ec8e37078cf1b5182036192a542fdbabe61e68dd
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---

# オンボーディングとインストール

詳しくは、 [!DNL Catalog Service] プロセス。

パート 1:

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

パート 2:

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

## 前提条件

のオンボーディングプロセス [!DNL Catalog Service] は、サーバーのコマンドラインへのアクセスを必要とします。 コマンドラインでの作業に慣れていない場合は、開発者またはシステムインテグレーターに問い合わせてください。

### ソフトウェア要件

- Adobe Commerce 2.4.4 以降
- PHP 8.1, 8.2
- コンポーザー：2.x

### サポートされるプラットフォーム

- Adobe Commerce on cloud infrastructure: 2.4.4 以降
- オンプレミスのAdobe Commerce: 2.4.4 以降

## エンドポイント

[!DNL Catalog Service] には、オンボーディングで使用できる 2 つのエンドポイントがあります。

- サンドボックス (https://catalog-service-sandbox.adobe.io/graphql) — 運用開始前のテストおよび検証に使用されます。
- 実稼動 (https://catalog-service.adobe.io/graphql)-コマースマーチャントや Web サイトのライブトラフィックに使用

Commerce のすべてのテストインスタンスは、サンドボックスエンドポイントを使用する必要があります。

読み込みテストは、サンドボックスエンドポイントでのみ実行する必要があります。 次の操作をお勧めします。 [サポートチケット](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) が負荷テスト時に開かれるので、サービスチームは追加のサーバートラフィックを予測できます。

## インストールと設定

を使い始めるには、以下を実行します。 [!DNL Catalog Service] Adobe Commerceの場合は、次の手順が必要です。

- データ書き出し拡張機能のインストール
- サービスとデータのエクスポートを設定する
- サービスへのアクセス

### データ書き出し拡張機能のインストール

のオンボーディングプロセス [!DNL Catalog Service] は、サーバーのコマンドラインへのアクセスを必要とします。

The [!DNL Catalog Service] 拡張機能は、Adobe Commerceクラウドインフラストラクチャとオンプレミスインスタンスの両方にインストールできます。

The [!DNL Catalog Service] は、Commerce アカウントにリンクされた Composer キーと共にインストールされます [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/) 登録プロセス中に提供されます。 Composer は、Adobe Commerceの初回インストール時、または Composer のキーが以前に外部に保存されていなかった状況で、これらのキーを使用します `auth.json` ファイル。

詳しくは、 [認証キーの取得](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) を参照してください。

#### Adobe Commerce an cloud infrastructure

この方法を使用して、 [!DNL Catalog Service] Commerce Cloudインスタンスの拡張。

1. を開きます。 `<Commerce_root>/composer.json` ファイルを編集し、次のように require セクションを更新します。

```json
"require": {
  "magento/catalog-service": "^3.0.1"
}
```

1. 新しい設定をローカルでテストし、依存関係を更新します。

```bash
composer update
```

このコマンドは、すべての依存関係を更新します。

1. 変更をコミットしてプッシュする `composer.json` および `composer.lock`.

#### オンプレミス

この方法を使用して、 [!DNL Catalog Service] オンプレミスインスタンスの拡張。

1. を開きます。 `<Commerce_root>/composer.json` ファイルを編集し、次のように require セクションを更新します。

```json
"require": {
    "magento/catalog-service": "^3.0.1"
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

インストール後 [!DNL Catalog Service]を設定する場合は、 [Commerce Services コネクタ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) API キーを指定し、SaaS データ空間を選択する。

SaaS 設定が完了したら、 [カタログ同期](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) ガイド。

カタログの書き出しが正しく実行されていることを確認するには、次の手順を実行します。

- cron ジョブが実行中であることを確認します。
- インデクサーが実行中であることを確認します。
- 次の点を確認します。 `Catalog Attributes Feed, Product Feed, Product Overrides Feed`、および `Product Variant Feed` インデクサーは「スケジュールに従って更新」に設定されます。

カタログのサイズによっては、初期同期に数分から数時間かかる場合があります。 初回同期後、カタログは、サービスを最新の状態に保つために、コマースサーバーからコマースサービスに製品データを継続的に書き出します。

### サービスへのアクセス

The [!DNL Catalog Service] API には、HTTPS 経由でのPOSTコマンドを使用してアクセスできます。

API キーを取得するには、管理の「 Commerce Service Connector 」領域に移動し、公開 API キーをコピーします。

詳しくは、 [GraphQLドキュメント](https://developer.adobe.com/commerce/webapi/graphql/) を参照して、API リクエストの生成に必要なヘッダーをクエリして送信する方法を確認してください。

許可する手順は次のとおりです。 [!DNL Catalog Service] ファイアウォールを通じて、 `commerce.adobe.io` をに追許可リストに加える加します。

## カタログサービスと API メッシュ

The [Adobe Developer App Builder の API メッシュ](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 開発者は、AdobeI/O を使用して、プライベートまたはサードパーティの API やその他のインターフェイスをAdobe製品と統合できます。

詳しくは、  [[!DNL Catalog Service] と API メッシュ](mesh.md) インストールおよび設定の詳細に関するトピック。
