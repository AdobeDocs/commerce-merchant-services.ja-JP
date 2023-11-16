---
title: インストール [!DNL Data Connection]
description: インストール、更新、アンインストールの方法を説明します [!DNL Data Connection] Adobe Commerceからの拡張。
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 2392cb4257f6efdcb8fc3e38c007148e03e338fd
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# インストール [!DNL Data Connection]

拡張機能をインストールする前に、 [前提条件を確認する](overview.md#prereqs).

## 拡張機能のインストール

The [!DNL Data Connection] 拡張機能は、 [AdobeMarketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html). サーバーのコマンドラインからこの拡張機能をインストールすると、AEM Analytics の AEM as a Adobe Commerceインストールに接続されます。 [サービス](../landing/saas.md). プロセスが完了したら、 **[!DNL Data Connection]** および **Commerce Services コネクタ** 次の場所に表示される： **システム** 下のメニュー **サービス** （コマース内） _管理者_.

>[!IMPORTANT]
>
>拡張機能の名前が拡張機能コネクタからに変更されましたが、Experience Platformは [!DNL Data Connection]、パッケージ名は残ります。 `experience-platform-connector` 後方互換性をサポートするため。

1. 次の手順で `experience-platform-connector` package で、コマンドラインから次のコマンドを実行します。

   ```bash
   composer require magento/experience-platform-connector
   ```

   このメタパッケージには、次のモジュールと拡張機能が含まれています。

   * `module-experience-connector-admin` - Admin UI が更新され、特定のAdobe Commerceインスタンスのデータストリーム ID を選択できるようになりました。
   * `module-experience-connector` - `Organization ID` および `datastreamId` （Storefront Events SDK の）を参照してください。
   * `data-services`  — ストアフロントイベントの属性コンテキストを提供します。 例えば、チェックアウトイベントが発生した場合、買い物かごに入った品目数に関する情報と、それらの品目の製品属性データが含まれます。
   * `services-id` - Adobe Commerceインスタンスをに接続します。 [Adobe Commerce SaaS](../landing/saas.md) サンドボックスおよび実稼動 API キーとAdobe Experience Platformに対してを使用し、IMS 組織 ID を取得する。
   * `orders-connector`  — 注文ステータスサービスをAdobe Commerceインスタンスに接続します。

1. （オプション）を含めるには [!DNL Live Search] 次を含むデータ： [イベントを検索](events.md#search-events), install [[!DNL Live Search]](../live-search/install.md) 拡張子。

1. （オプション）B2B データを含める場合は、 [要求イベント](events.md#b2b-events), install [B2B 拡張機能](#install-the-b2b-extension).

### 注文コネクタの設定

インストール後、 `experience-platform-connector` 拡張機能を使用する場合は、のインストールを完了する必要があります。 `orders-connector` デプロイメントタイプに基づくモジュール：オンプレミスまたはクラウドインフラストラクチャ上のAdobe Commerce。

#### オンプレミス

オンプレミス環境では、コード生成とAdobe Commerceイベントを手動で有効にする必要があります。

```bash
bin/magento events:generate:module
bin/magento module:enable Magento_AdobeCommerceEvents
bin/magento setup:upgrade
bin/magento setup:di:compile
bin/magento config:set adobe_io_events/eventing/enabled 1
```

#### クラウドインフラストラクチャ上

クラウド上のAdobe Commerceインフラストラクチャで、 `ENABLE_EVENTING` のグローバル変数 `.magento.env.yaml`. [詳細情報](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html#enable_eventing).

```bash
stage:
   global:
      ENABLE_EVENTING: true
```

更新されたファイルをコミットし、クラウド環境にプッシュします。 デプロイメントが完了したら、次のコマンドを使用してイベントの送信を有効にします。

```bash
bin/magento config:set adobe_io_events/eventing/enabled 1
```

### B2B 拡張機能のインストール

B2B マーチャントの場合は、次の拡張機能をインストールして以下を含めます。 [購買依頼リスト](events.md#b2b-events) イベントデータ。

をダウンロードします。 `magento/experience-platform-connector-b2b` コマンドラインから次のコマンドを実行して、拡張機能を設定します。

```bash
composer require magento/experience-platform-connector-b2b
```

## を更新します。 [!DNL Data Connection] 拡張 {#update}

次の手順で [!DNL Data Connection] 拡張機能の場合は、コマンドラインから次のコマンドを実行します。

```bash
composer update magento/experience-platform-connector --with-dependencies
```

また、B2B 商人の場合は次のようになります。

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

2.0.0 から 3.0.0 のようなメジャーバージョンに更新するには、プロジェクトのルートを編集します。 [!DNL Composer] `.json` ファイルの内容は次のとおりです。

1. ルートを開く `composer.json` ファイルと検索 `magento/experience-platform-connector`.

1. Adobe Analytics の `require` 「 」セクションで、次のようにバージョン番号を更新します。

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^3.0",
      ...
    }
   ```

1. **保存** `composer.json`. 次に、コマンドラインから次の操作を実行します。

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

   また、B2B 商人の場合は次のようになります。

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## をアンインストールします。 [!DNL Data Connection] 拡張 {#uninstall}

をアンインストールするには、以下を実行します。 [!DNL Data Connection] 拡張機能：を参照してください。 [モジュールのアンインストール](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
