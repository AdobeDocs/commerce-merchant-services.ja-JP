---
title: Adobe CommerceからのAdobe Experience Platform Connector のインストールと設定
description: Adobe CommerceからAdobe Experience Platform Connector をインストール、設定、更新およびアンインストールする方法について説明します。
source-git-commit: 9b5f2da08167e22bbba504009bccc87d0ab02c48
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Experience Platformコネクタのインストールと設定

拡張機能をインストールする前に、 [前提条件を確認する](overview.md#prereqs).

## 拡張機能のインストール

1. Experience Platformコネクタのメタパッケージをインストールします。

   ```bash
   composer require magento/platform-connector
   ```

   このメタパッケージには、次のモジュールが含まれます。

   * `module-platform-connector-admin`  — 管理 UI を更新します
   * `module-platform-connector` - `ImsOrgId` および `datastreamId` (Magentoストアフロントイベント SDK)

1. Commerce Data Services 拡張機能をインストールして、プロファイルとチェックアウトイベントを含めます。

   ```bash
   composer require magento/data-services
   ```

   Commerce Data Services 拡張機能は、ストアフロントイベントの属性コンテキストを提供します。 例えば、チェックアウトイベントが発生した場合、買い物かごに入った品目数に関する情報と、それらの品目の製品属性データが含まれます。

1. コマースサービスコネクタをインストールします。

   ```bash
   composer require magento/commerce-services
   ```

   Commerce Service コネクタを使用すると、Adobe Commerceインスタンスを [Adobe Commerce SaaS](../landing/saas.md) Adobe Experience Platformに

1. （オプション）を含めるには [!DNL Live Search] データ（検索イベントを含む）は、 [[!DNL Live Search]](../live-search/install.md) 拡張子。

## Experience Platformコネクタの更新 {#update}

Experience Platformコネクタを更新するには、コマンドラインで次の操作を実行します。

```bash
composer update magento/platform-connector --with-dependencies
```

1.0.0 から 2.0.0 のようなメジャーバージョンに更新するには、プロジェクトのルートを編集します。 [!DNL Composer] `.json` ファイルの内容は次のとおりです。

1. ルートを開く `composer.json` ファイルと検索 `magento/platform-connector`.

1. 内 `require` 「 」セクションで、次のようにバージョン番号を更新します。

   ```json
   "require": {
      ...
      "magento/platform-connector": "^2.0",
      ...
    }
   ```

1. **保存** `composer.json`. 次に、コマンドラインから次の操作を実行します。

   ```bash
   composer update magento/platform-connector –-with-dependencies
   ```

## Experience Platformコネクタのアンインストール {#uninstall}

Experience Platformコネクタをアンインストールするには、 [モジュールのアンインストール](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).
