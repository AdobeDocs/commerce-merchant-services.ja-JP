---
title: インストールと設定
description: インストール、更新、アンインストールの方法を説明します [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
source-git-commit: b06d5000263b7ee09608a4a8510d76e9f4bdb809
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# インストールと設定

の導入 [!DNL Product Recommendations] をストアフロントと管理者に送信するには、モジュールをインストールし、 [Commerce Services コネクタ](../landing/saas.md). アップデートがリリースされると、インストールを最新バージョンで簡単に更新できます。

- [インストール](#install)
- [設定](#configure)
- [更新](#update)
- [アンインストール](#uninstall)

## インストール [!DNL Product Recommendations] {#install}

これは、 [!DNL Product Recommendations] モジュールはスタンドアロンのメタパッケージで、更新はAdobe Commerceよりも頻繁にリリースされます。 最新のバグ修正および機能を最新の状態に保つには、 [リリースノート](release-notes.md).

のインストール `magento/product-recommendations` Composer を使用したモジュール：

```bash
composer require magento/product-recommendations
```

### Page Builder サポートの追加 {#pbsupport}

[!DNL Product Recommendations] の場合、Page Builder はオプションのモジュールで、別途インストールされます。 使用する [!DNL Product Recommendations] ページビルダーで、次のコマンドを実行してモジュールをインストールします。

```bash
composer require magento/module-page-builder-product-recommendations
```

有効にする [!DNL Product Recommendations] ページビルダーで、既存のアクティブな [レコメンデーション単位](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html) ページ、ブロック、動的ブロックなど、ページビルダーで作成されたすべてのコンテンツに追加できます。

### 視覚的類似性レコメンデーションタイプの追加 {#vissimsupport}

この _視覚的類似性_ レコメンデーションタイプを使用すると、レコメンデーションユニットを、 [似たような](type.md#visualsim) 表示される製品に追加します。 このレコメンデーションタイプは、商品の画像や視覚的要素が買い物エクスペリエンスの重要な部分である場合に最も役に立ちます。 のインストール _視覚的類似性_ 次のコマンドを実行してレコメンデーションタイプを指定します。

```bash
composer require magento/module-visual-product-recommendations
```

## 設定 [!DNL Product Recommendations] {#configure}

インストール後、 `magento/product-recommendations` モジュールの場合、 [Commerce Services コネクタ](https://docs.magento.com/user-guide/configuration/services/saas.html) API キーを指定し、SaaS データ領域を選択する。

カタログの書き出しが正しく実行されていることを確認するには、 [cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) ジョブと [indexers](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) が実行中で、 `Product Feed` indexer は次のように設定されています： `Update by Schedule`.

API キーを使用して Commerce Services に正常にリンクし、SaaS データスペースを指定すると、カタログの同期が開始されます。 その後、 [確認](verify.md) その行動データがストアフロントに送信されます。

## の更新 [!DNL Product Recommendations] インストール {#update}

全てのAdobe Commerceと同じように [!DNL Product Recommendations] は、インストールと更新に Composer を使用します。 次の手順で `magento/product-recommendations` モジュールで、以下を実行します。

```bash
composer update magento/product-recommendations --with-dependencies
```

2.0 から 3.0 のようなメジャーバージョンに更新するには、プロジェクトのルートを編集する必要があります `composer.json` ファイル。 ( [リリースノート](release-notes.md) を参照してください。) 例えば、 `composer.json` ファイルを開き、 `magento/product-recommendations` モジュール：

```json
"require": {
    ...
    "magento/product-recommendations": "^2.0",
    ...
}
```

メジャーバージョンを次から比較しましょう： `2.0` から `3.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

保存する `composer.json` ファイルと実行：

```bash
composer update magento/product-recommendations --with-dependencies
```

## アンインストール [!DNL Product Recommendations] {#uninstall}

必要に応じて、 [uninstall](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html) 製品レコメンデーションモジュール。
