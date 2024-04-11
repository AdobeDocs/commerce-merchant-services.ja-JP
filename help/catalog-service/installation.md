---
title: オンボーディングとインストール
description: 「インストール方法を学ぶ [!DNL Catalog Service]“
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 8a98e069cd9ec3d2c4fec33485e5c8186d94518f
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 0%

---

# オンボーディングとインストール

次のビデオでは、 [!DNL Catalog Service] プロセス。

**パート 1**：オンボーディングとインストール

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

**第 2 部**：の使用 [!DNL Catalog Service]

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

>[!BEGINSHADEBOX]

## 前提条件

のオンボーディングプロセス [!DNL Catalog Service] サーバーのコマンドラインにアクセスできる必要があります。 コマンドラインからの操作に詳しくない場合は、開発者またはシステムインテグレーターにお問い合わせください。

**ソフトウェア要件**

- Adobe Commerce 2.4.4 以降
- PHP 8.1, 8.2
- コンポーザー：2.x

**サポートされるプラットフォーム**

- クラウドインフラストラクチャー上のAdobe Commerce:2.4.4 以降
- Adobe Commerce オンプレミス：2.4.4 以降

>[!ENDSHADEBOX]

## エンドポイント

[!DNL Catalog Service] には、オンボーディングに使用できる 2 つのエンドポイントがあります。

- サンドボックス （`https://catalog-service-sandbox.adobe.io/graphql`）：運用開始前のテストおよび検証に使用
- 実稼動（`https://catalog-service.adobe.io/graphql`） – Commerceのマーチャントおよび web サイトのライブトラフィックに使用します。

Commerceのすべてのテストインスタンスは、サンドボックスエンドポイントを使用する必要があります。

負荷テストは、サンドボックスエンドポイントでのみ実行してください。 以下を推奨します。 [サポートチケット](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 負荷テスト時に開いて、サービスチームが追加のサーバートラフィックを予測できるようにします。

## インストールと設定

を使用するには [!DNL Catalog Service] Adobe Commerceには、次の手順が必要です。

- データ書き出し拡張機能のインストール
- サービスとデータの書き出しの設定
- サービスへのアクセス

### データ書き出し拡張機能のインストール

のオンボーディングプロセス [!DNL Catalog Service] サーバーのコマンドラインにアクセスできる必要があります。

この [!DNL Catalog Service] 拡張機能は、Adobe Commerce クラウドインフラストラクチャとオンプレミスインスタンスの両方にインストールできます。

この [!DNL Catalog Service] は、Commerce アカウントにリンクされた Composer キーと共にインストールされます [`mageid`](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/) 登録プロセス中に提供されます。 Composer は、Adobe Commerceの初期インストール時、または以前に外部に保存されていなかった状況で、これらのキーを使用します `auth.json` ファイル。

参照： [認証キーの取得](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) composer キーの取得の詳細については、を参照してください。

#### クラウドインフラストラクチャー上のAdobe Commerce

をインストールするには、次の方法を使用します [!DNL Catalog Service] Commerce Cloudインスタンス用の拡張機能。

1. ローカルワークステーションで、をプロジェクトディレクトリに変更します。
1. カタログサービスモジュールを追加します。

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. パッケージの依存関係を更新します。

   ```bash
   composer update
   ```

1. のコード変更をコミットしてプッシュします `composer.json` および `composer.lock` ファイル。

#### オンプレミス

をインストールするには、次の方法を使用します [!DNL Catalog Service] オンプレミスのインスタンスの拡張機能。

1. Composer を使用して、Catalog Service モジュールをプロジェクトに追加します。

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. 依存関係を更新し、拡張機能をインストールします。

   ```bash
   composer update
   ```

1. Adobe Commerceをアップグレード :

   ```bash
   bin/magento setup:upgrade
   ```

1. キャッシュをクリアする：

   ```bash
   bin/magento cache:clean
   ```

### サービスとデータの書き出しの設定

インストール後 [!DNL Catalog Service]を設定する必要があります [Commerce サービスコネクタ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) API キーを指定し、SaaS データ空間を選択する。

SaaS の設定が完了したら、 [データ管理ダッシュボード](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). このダッシュボードを使用して、Commerce データベースからCommerce SaaS サービスに転送される商品データの同期ステータスをモニタリングできます。

カタログの書き出しが正しく実行されていることを確認するには：

- cron ジョブが実行中であることを確認します。
- インデクサーが実行中であることを確認します。
- 必ずを `Catalog Attributes Feed, Product Feed, Product Overrides Feed`、および `Product Variant Feed` インデクサーは「スケジュールに従って更新」に設定されています。

カタログのサイズに応じて、最初の同期に数分から数時間かかる場合があります。 最初の同期の後、カタログは、商品データをCommerce サーバーからCommerce サービスに継続的に書き出し、サービスを最新の状態に保ちます。 同期のステータスを監視するには、 [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html).

### サービスへのアクセス

この [!DNL Catalog Service] API には、POSTコマンドを使用して HTTPS でアクセスできます。

api キーを取得するには、管理のCommerce サービスコネクタ領域に移動し、公開 API キーをコピーします。

を読み取る [GraphQL ドキュメント](https://developer.adobe.com/commerce/services/graphql/) api リクエストの生成に必要なヘッダーをクエリして送信する方法を理解するため

許可する [!DNL Catalog Service] ファイアウォールを使用して、次を追加します `commerce.adobe.io` を許可リストに追加します。

## カタログサービスと API メッシュ

この [Adobe Developer App Builder の API メッシュ](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) を使用すると、開発者は、プライベートまたはサードパーティの API およびその他のインターフェイスを、Adobe IO を使用するAdobe製品と統合できます。

を参照してください。  [[!DNL Catalog Service] と API メッシュ](mesh.md) インストールと設定の詳細に関するトピック。

## データ管理ダッシュボード

ユーザーは、次を参照できます [データ管理ダッシュボード](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) 詳細なデータ： [!DNL Catalog Service] データ同期。
