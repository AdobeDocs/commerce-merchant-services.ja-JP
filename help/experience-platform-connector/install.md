---
title: Adobe CommerceからのAdobe Experience Platform Connector のインストールと設定
description: Adobe CommerceからAdobe Experience Platform Connector をインストール、設定、更新およびアンインストールする方法について説明します。
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: 334ee967ec2379a87acfc5fb427d7ada6fa25ee7
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Experience Platformコネクタのインストールと設定

拡張機能をインストールする前に、 [前提条件を確認する](overview.md#prereqs).

## 拡張機能のインストール

1. Experience Platformコネクタのメタパッケージをインストールします。

   ```bash
   composer require magento/experience-platform-connector
   ```

   このメタパッケージには、次のモジュールと拡張機能が含まれています。

   * `module-platform-connector-admin` - Admin UI を更新し、特定のAdobe Commerceインスタンスのデータストリーム ID を選択できるようにしました
   * `module-platform-connector` - `ImsOrgId` および `datastreamId` ( Adobe Commerce Storefront Event SDK の )
   * `data-services`  — ストアフロントイベントの属性コンテキストを提供します。 例えば、チェックアウトイベントが発生した場合、買い物かごに入った品目数に関する情報と、それらの品目の製品属性データが含まれます。
   * `services-id` - Adobe Commerceインスタンスをに接続します [Adobe Commerce SaaS](../landing/saas.md) サンドボックスおよび実稼動 API キーとAdobe Experience Platformへの IMS 組織 ID の取得を使用する

1. （オプション）を含めるには [!DNL Live Search] データ（検索イベントを含む）は、 [[!DNL Live Search]](../live-search/install.md) 拡張子。

## Experience Platformコネクタの更新 {#update}

Experience Platformコネクタを更新するには、コマンドラインで次の操作を実行します。

```bash
composer update magento/experience-platform-connector --with-dependencies
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

## Experience Platformコネクタのアンインストール {#uninstall}

Experience Platformコネクタをアンインストールするには、 [モジュールのアンインストール](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).
