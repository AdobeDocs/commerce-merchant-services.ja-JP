---
title: オンボーディングとインストール
description: 「インストール方法を学ぶ [!DNL Catalog Service]“
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 0%

---

# オンボーディングとインストール

カタログサービスをインストールし、を使用してCommerce インスタンスから商品データをリクエストおよび受信する [Catalog Service GraphQL API](https://developer.adobe.com/commerce/services/graphql/catalog-service/). カタログサービスは、repo.magento.com リポジトリからコンポーザメタパッケージとして提供されます。

>[!NOTE]
>
>Commerce インスタンスで Live Search または Product Recommendationsを使用している場合は、サービスのオンボーディングまたはアップグレードの際に、Catalog Service のインストールまたは更新が自動的に行われます。 詳しくは、のインストール手順を参照してください [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install) および [製品のRecommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure).



## 必要システム構成

**ソフトウェア要件**

- Adobe Commerce 2.4.4 以降
- PHP 8.1、8.2、8.3
- コンポーザー：2.x

**サポートされるプラットフォーム**

- クラウドインフラストラクチャー上のAdobe Commerce:2.4.4 以降
- Adobe Commerce オンプレミス：2.4.4 以降

## エンドポイント

[!DNL Catalog Service] には、オンボーディングに使用できる 2 つのエンドポイントがあります。

- サンドボックス （`https://catalog-service-sandbox.adobe.io/graphql`）：運用開始前のテストおよび検証に使用
- 実稼動（`https://catalog-service.adobe.io/graphql`） – Commerceのマーチャントおよび web サイトのライブトラフィックに使用します。

すべてのCommerce テストインスタンスは、サンドボックス エンドポイントを使用します。

サンドボックスエンドポイントですべての負荷テストを実行します。 負荷テストを開始する前に、 [サポートチケット](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) そのため、サービスチームは、追加のサーバートラフィックを予測することができます。

## インストールと設定

を使用するには [!DNL Catalog Service] Adobe Commerceには、次の手順が必要です。

- カタログサービス拡張機能（`magento/catalog-service`）
- サービスとデータの書き出しの設定
- サービスへのアクセス

### カタログサービス拡張機能のインストール

>[!BEGINSHADEBOX]

**前提条件**

- アクセス [repo.magento.com](https://repo.magento.com) をクリックして拡張機能をインストールします。 キーの生成と必要な権限の取得については、を参照してください。 [認証キーの取得](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys). クラウドインストールについては、を参照してください [クラウドインフラストラクチャー上のCommerce ガイド](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/authentication-keys)

- Adobe Commerce アプリケーションサーバーのコマンドラインにアクセスします。

>[!ENDSHADEBOX]

カタログサービス拡張機能の最新バージョン（`magento/catalog-service`Adobe Commerce Adobe Commerce）を選択する必要があります。 カタログサービスは、 [repo.magento.com](https://repo.magento.com) リポジトリ。

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
   git commit -m "Add catalog service module"
   git push origin <branch-name>
   ```

   更新をクラウド環境にプッシュすると、が開始されます [Commerce cloud のデプロイメントプロセス](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) 変更を適用します。 からデプロイメントステータスを確認します。 [ログをデプロイ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB オンプレミス]

このメソッドを使用して、 [!DNL Catalog Adapter] オンプレミスのインスタンスの場合。

1. Composer を使用して、Catalog Service モジュールをプロジェクトに追加します。

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

### サービスとデータの書き出しの設定

をインストールしたら、 [!DNL Catalog Service]カタログサービスをAdobe Commerce インスタンスに統合するには、次のタスクを実行します。 この統合により、Commerce インスタンス、カタログサービスおよびその他のサポートサービス間のデータ同期と通信が可能になります。

1. の設定 [Commerce サービスコネクタ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) API キーを指定し、SaaS データ空間を選択する。

   Commerce Services Connector のセットアップは、カタログサービス、ライブ検索、製品RecommendationsなどのAdobe Commerce サービスを使用するために必要な 1 回限りのプロセスです。 別のサービス用にコネクタを既に設定している場合は、この手順をスキップします。

1. からの初期データ同期の実行 [データ管理ダッシュボード](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).

   カタログのサイズに応じて、最初の同期に数分から数時間かかる場合があります。 同期ステータスは、データ管理ダッシュボードから監視できます。 最初の同期の後、カタログは、サービスを最新の状態に保つために、継続的に製品データを書き出します。

カタログの書き出しが正しく実行されていることを確認するには：

- [Cron ジョブが実行中であることを確認](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).
- インデクサーがから実行されていることを確認 [Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) または、Commerce CLI コマンドを使用します `bin/magento indexer:info`.
- を確認します `Catalog Attributes Feed, Product Feed, Product Overrides Feed`、および `Product Variant Feed` インデクサーはに設定されています。 `Update by Schedule`.

### サービスへのアクセス

この [!DNL Catalog Service] GraphQL API には、 ` https://catalog-service.adobe.io/graphql` https 経由でPOSTコマンドを使用するエンドポイント

GraphQL クエリでは、管理者でAdobe Commerce サービスコネクタ設定に追加した公開 API キーを含む、複数の HTTP ヘッダーを指定する必要があります。 詳しくは、を参照してください [ストアフロントサービスGraphQL](https://developer.adobe.com/commerce/services/graphql/) ドキュメント。

### ファイアウォール設定

許可する [!DNL Catalog Service] ファイアウォールを使用して、次を追加します `commerce.adobe.io` を許可リストに追加します。

## カタログサービスと API メッシュ

この [Adobe Developer App Builder の API メッシュ](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) を使用すると、開発者は、プライベートまたはサードパーティの API およびその他のインターフェイスを、Adobe IO を使用するAdobe製品と統合できます。

を参照してください。 [[!DNL Catalog Service] と API メッシュ](mesh.md) インストールと設定の詳細に関するトピック。

## データ管理ダッシュボード

詳しくは、 [!DNL Catalog Service] データ同期については、を参照してください。 [データ管理ダッシュボード](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).
