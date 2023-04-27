---
title: Adobe CommerceからのAdobe Experience Platform Connector のインストールと設定
description: Adobe CommerceからAdobe Experience Platform Connector をインストール、設定、更新およびアンインストールする方法について説明します。
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: 898d49cbeb4711862a47693a0d608b74730dc845
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Experience Platformコネクタのインストールと設定

拡張機能をインストールする前に、 [前提条件を確認する](overview.md#prereqs).

## 拡張機能のインストール

Experience Platformコネクタ拡張機能は、 [Adobe市場](https://marketplace.magento.com/magento-experience-platform-connector.html). サーバーのコマンドラインからこの拡張機能をインストールすると、AEM Analytics の AEM as a Adobe Commerceインストールに接続されます。 [サービス](../landing/saas.md). プロセスが完了したら、 **Experience Platformコネクタ** および **Commerce Services コネクタ** 次の場所に表示される： **システム** 下のメニュー **サービス** （コマース内） _管理者_.

>[!NOTE]
>
>![Adobe Commerce用 B2B](../assets/b2b.svg) B2B マーチャントの場合は、別の拡張機能をインストールする必要があります。 この拡張機能は、B2B 固有のイベントのサポートを追加します。 [詳細情報](#install-the-b2b-extension).


1. 次の手順で `experience-platform-connector` package で、コマンドラインから次のコマンドを実行します。

   ```bash
   composer require magento/experience-platform-connector
   ```

   このメタパッケージには、次のモジュールと拡張機能が含まれています。

   * `module-experience-connector-admin` - Admin UI を更新し、特定のAdobe Commerceインスタンスのデータストリーム ID を選択できるようにしました
   * `module-experience-connector` - `Organization ID` および `datastreamId` （Storefront Events SDK の）
   * `data-services`  — ストアフロントイベントの属性コンテキストを提供します。 例えば、チェックアウトイベントが発生した場合、買い物かごに入った品目数に関する情報と、それらの品目の製品属性データが含まれます。
   * `services-id` - Adobe Commerceインスタンスをに接続します [Adobe Commerce SaaS](../landing/saas.md) サンドボックスおよび実稼動 API キーとAdobe Experience Platformへの IMS 組織 ID の取得を使用する

1. （オプション）を含めるには [!DNL Live Search] データ（検索イベントを含む）は、 [[!DNL Live Search]](../live-search/install.md) 拡張子。

### B2B 拡張機能のインストール

B2B マーチャントの場合は、次の拡張機能をインストールして、 [購買依頼リスト](events.md#b2b-events) イベントデータ。

をダウンロードします。 `magento/experience-platform-connector-b2b` コマンドラインから次のコマンドを実行して、拡張機能を設定します。

```bash
composer require magento/experience-platform-connector-b2b
```

## Experience Platformコネクタの更新 {#update}

Experience Platformコネクタを更新するには、コマンドラインで次の操作を実行します。

```bash
composer update magento/experience-platform-connector --with-dependencies
```

B2B 商人の場合は次のようになります。

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

1.0.0 から 2.0.0 のようなメジャーバージョンに更新するには、プロジェクトのルートを編集します。 [!DNL Composer] `.json` ファイルの内容は次のとおりです。

1. ルートを開く `composer.json` ファイルと検索 `magento/platform-connector`.

1. 内 `require` 「 」セクションで、次のようにバージョン番号を更新します。

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^2.0",
      ...
    }
   ```

1. **保存** `composer.json`. 次に、コマンドラインから次の操作を実行します。

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

   B2B 商人の場合は次のようになります。

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Experience Platformコネクタのアンインストール {#uninstall}

Experience Platformコネクタをアンインストールするには、 [モジュールのアンインストール](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
