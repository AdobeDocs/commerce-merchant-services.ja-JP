---
title: インストール
description: " [!DNL Store Fulfillment solution] PHP 用の Composer を使用するAdobe Commerceストアフロントの場合。"
role: User, Admin
level: Intermediate
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---


# インストール

最初のインストールを完了する [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] 実稼動環境以外の環境の拡張で、キューマネージャーが実行され、例外の処理を許可するようにキャッシュが設定されています。 Adobe Commerceインスタンスの動作と保守に関するベストプラクティスを確実に実施するための開発ツールが、開発環境に含まれていることを確認します。

## 前提条件

以下を確認します。 [要件](solution-requirements.md) をインストールする前に、Store Fulfilment ソリューションに関する情報を収集し、必要な情報を収集します。 [!DNL Store Fulfillment] Adobe Commerceの拡張機能。

Store Fulfilment for Adobe Commerce拡張機能のプレリリース版またはベータ版をインストールしている場合は、次のコマンドを使用して削除してから、現在のバージョンをインストールしてください。

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## インストール要件

- **Walmart Commerce Technologies ソフトウェアアーカイブ（.zip ファイル）による Store Fulfilment へのアクセス** — オンボーディングとイネーブルメントのプロセス中に、アカウントマネージャーと協力して、Store Fulfilment 拡張機能のインストールファイルにアクセスします。

- **Adobe Commerceアカウント情報**- [!DNL Store Fulfillment] ソリューションには [[!DNL Commerce] アカウント](https://docs.magento.com/user-guide/magento/magento-account.html){target="_blank"}. に対する所有者または管理者アクセス権を持つアカウント ID と資格情報が必要です [!DNL Adobe Commerce] プロジェクト。

- の場合 [!DNL Adobe Commerce] クラウドインフラストラクチャプロジェクトでは、ソフトウェアインストーラーが Cloud プロジェクトに管理者アクセス権を持っている必要があります。 詳しくは、 [ユーザーアクセスを管理](https://devdocs.magento.com/cloud/project/user-admin.html).

- **Composer と[!DNL Commerce CLI]** — 参照 [一般的な CLI のインストール](https://devdocs.magento.com/extensions/install/){target="_blank"} を参照してください。 [!DNL Adobe Commerce] プラットフォーム。

- **Adobe Commerceでサードパーティの拡張機能をインストールした経験** — 参照については、 Adobe Commerceのドキュメントを参照してください。

   - [クラウドインフラストラクチャインスタンス上のAdobe Commerceの拡張機能のインストール](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension).

   - [Adobe Commerceオンプレミスインスタンスの拡張機能のインストール](https://devdocs.magento.com/extensions/install/).

### 手順 1:拡張機能バンドルのダウンロード

アカウント担当者から提供される手順に従って、Store Fulfilment Services 拡張機能をインストールするための Composer パッケージを含むアーカイブファイルをダウンロードします。

### 手順 2:アプリケーションへの拡張機能アーティファクトの抽出

統合バンドルを含むアーカイブファイルを抽出し、Store Fulfilment Services 拡張機能をインストールします。

1. 抽出したファイルのターゲットディレクトリを作成します。

   - コマンドラインから、Web サーバーの doc root ディレクトリに移動します。

   - の作成 `artifacts` ディレクトリ。

1. アーカイブファイルを新しいディレクトリに抽出します。

1. ファイルの一覧を確認して、抽出したファイルを確認します。

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### 手順 3:Composer を使用したアプリの設定

Composer を使用して、インストールのソースディレクトリを設定し、Store Fulfilment Services 拡張機能をインストールします。

1. Composer のインストール用にソースリポジトリを設定します。

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. Store Fulfilment Services 拡張機能の追加先 `composer.json`.

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>オンプレミスのAdobe Commerceインスタンスでのパフォーマンスを向上させるには、 [自動読み込み設定を更新](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader): `composer dump-autoload --optimize`

### 手順 4:データベーススキーマとデータのアップグレード

次を使用してインストールを完了します： `bin/magento setup:upgrade` をクリックして、データベースのスキーマとデータを、ストアフルフィルメントソリューションをサポートする変更で更新します。

>[!NOTE]
>
>Adobe Commerce on cloud infrastructure プロジェクトの場合、拡張機能を登録する必要はありません。 代わりに、前の手順で行ったコードの変更をコミットし、環境ブランチにプッシュします。 データベーススキーマとデータを更新するコマンドは、クラウドのビルドおよびデプロイメントプロセス中に自動的に実行されます。

### 手順 5:インストールの完了

1. を使用して、拡張機能をAdobe Commerceに登録します。 `setup:upgrade` MagentoCLI コマンド

   ```terminal
   bin/magento setup:upgrade
   ```

1. プロンプトが表示されたら、 [!DNL Commerce] プロジェクト。

   ```bash
   bin/magento setup:di:compile
   ```

1. キャッシュをクリーンアップします。

   ```bash
   bin/magento cache:clean
   ```

1. メンテナンスモードを無効にします。

   ```bash
   bin/magento maintenance:disable
   ```

### 手順 6:インストールの確認

Adobe Commerceサーバーから、Store Fulfilment Services 拡張機能のモジュールがインストールされ、有効になっていることを確認します。

1. サーバーにログインします。

   クラウドインフラストラクチャ上のAdobe Commerceでのインストールの場合、 [SSH を使用してリモート環境にログイン](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh).

1. ストアフルフィルメントサービスモジュールが有効になっていることを確認します。

   ```bash
   bin/magento module:status  --enabled | grep Walmart
   ```

   出力には、次のモジュールが含まれます。

   ```
   Walmart_BopisBase
   Walmart_BopisAlternatePickupContact
   Walmart_BopisAlternatePickupContactFrontend
   Walmart_BopisApiConnector
   Walmart_BopisAlternatePickupContactAdminUi
   Walmart_BopisCheckoutPickInStoreApi
   Walmart_BopisInventorySourceAdminUi
   Walmart_BopisCheckoutPickInStore
   Walmart_BopisInventoryCatalogApi
   Walmart_BopisPreferredLocationApi
   Walmart_BopisHomeDeliveryApi
   Walmart_BopisHomeDelivery
   Walmart_BopisPreferredLocation
   Walmart_BopisInventoryCatalog
   Walmart_BopisPreferredLocationFrontend
   Walmart_BopisCheckoutPickInStoreAdminUi
   Walmart_BopisInventorySourceApi
   Walmart_BopisInventorySourceFaasSync
   Walmart_BopisInventorySourceReservation
   Walmart_BopisLocationCheckInApi
   Walmart_BopisLogging
   Walmart_BopisStoreAssociateApi
   Walmart_BopisLocationCheckInFrontend
   Walmart_BopisStoreAssociate
   Walmart_BopisOperationQueue
   Walmart_BopisOperationQueueAdminUi
   Walmart_BopisOperationQueueApi
   Walmart_BopisOrderFaasSync
   Walmart_BopisOrderUpdateApi
   Walmart_BopisLocationCheckIn
   Walmart_BopisInventoryCatalogAdminUi
   Walmart_BopisPreferredLocationAdminUi
   Walmart_BopisDeliverySelection
   Walmart_BopisCheckoutPickInStoreFrontend
   Walmart_BopisLocationCheckInAdminUi
   Walmart_BopisStoreAssociateAdminUi
   Walmart_BopisOrderUpdate
   Walmart_BopisStoreAssociateTfa
   Walmart_BopisStoreAssociateTfaApi
   ```

### その他の手順

必要に応じて、 [設定:static-content:デプロイ](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html){target="_blank"} 静的ビューファイルを実稼動環境にデプロイする CLI コマンド。

```terminal
php bin/magento setup:static-content:deploy -f
```

この `-f` オプションは、空のテーマを使用する場合に必要です。

>[!NOTE]
>
>詳しくは、 [Adobe Commerceでの静的コンテンツデプロイのベストプラクティス](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment.html) ( Adobe Commerceヘルプセンター )
