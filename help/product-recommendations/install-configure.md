---
title: インストールと設定
description: インストール、更新、アンインストールの方法を説明します [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
role: Admin, Developer
source-git-commit: 96a5791c5716f612f473540f27bd3f99b1bfe7c8
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# インストールと設定

の導入 [!DNL Product Recommendations] をストアフロントと管理者に送信するには、モジュールをインストールし、 [Commerce Services コネクタ](../landing/saas.md). アップデートがリリースされると、インストールを最新バージョンで簡単に更新できます。

- [インストール](#install)
- [設定](#configure)
- [更新](#update)
- [アンインストール](#uninstall)

## インストール [!DNL Product Recommendations] {#install}

これは、 [!DNL Product Recommendations] モジュールはスタンドアロンのメタパッケージで、更新はAdobe Commerceよりも頻繁にリリースされます。 最新のバグ修正と機能を確認するには、 [リリースノート](release-notes.md).

をインストールします。 `magento/product-recommendations` Composer を使用したモジュール：

```bash
composer require magento/product-recommendations
```

### Page Builder サポートの追加 {#pbsupport}

[!DNL Product Recommendations] for Page Builder はオプションのモジュールで、別途インストールされます。 次を使用するには： [!DNL Product Recommendations] ページビルダーで、次のコマンドを実行してモジュールをインストールします。

```bash
composer require magento/module-page-builder-product-recommendations
```

を有効にして [!DNL Product Recommendations] ページビルダーで、既存のアクティブな [レコメンデーション単位](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) ページ、ブロック、動的ブロックなど、ページビルダーで作成されたすべてのコンテンツに追加できます。

詳しくは、 [使用 [!DNL Product Recommendations] Page Builder コンテンツを使用](page-builder.md) を参照してください。

### 視覚的類似性レコメンデーションタイプの追加 {#vissimsupport}

The _視覚的類似性_ レコメンデーションタイプを使用すると、レコメンデーションユニットを、 [似たような](type.md#visualsim) 表示される製品に追加します。 このレコメンデーションタイプは、商品の画像や視覚的要素が買い物エクスペリエンスの重要な部分である場合に最も役に立ちます。 をインストールします。 _視覚的類似性_ 次のコマンドを実行してレコメンデーションタイプを指定します。

```bash
composer require magento/module-visual-product-recommendations
```

## 設定 [!DNL Product Recommendations] {#configure}

インストール後、 `magento/product-recommendations` モジュールの場合は、 [Commerce Services コネクタ](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) API キーを指定し、SaaS データ領域を選択する。

カタログの書き出しが正しく実行されていることを確認するには、 [cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) ジョブと [インデクサー](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) が実行中で、 `Product Feed` indexer は次のように設定されています： `Update by Schedule`.

API キーを使用して Commerce Services に正常にリンクし、SaaS データスペースを指定すると、カタログの同期が開始されます。 次の操作が可能です。 [確認](verify.md) その行動データがストアフロントに送信されます。

## を更新します。 [!DNL Product Recommendations] インストール {#update}

全てのAdobe Commerceと同じように [!DNL Product Recommendations] は、インストールと更新に Composer を使用します。 次の手順で `magento/product-recommendations` モジュールで、以下を実行します。

```bash
composer update magento/product-recommendations --with-dependencies
```

3.0 から 4.0 のようなメジャーバージョンに更新するには、ルートを編集する必要があります `composer.json` ファイルを作成します。 ( [リリースノート](release-notes.md) を参照してください。) 例えば、 `composer.json` ファイルを開き、 `magento/product-recommendations` モジュール：

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

メジャーバージョンを次から比較しましょう： `3.0` から `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

を保存します。 `composer.json` ファイルと実行：

```bash
composer update magento/product-recommendations --with-dependencies
```

または、 `magento/module-visual-product-recommendations` および `magento/module-page-builder-product-recommendations` モジュール：

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> Product Recommendationsのバージョン 3.x.x では、1 つの API キーのみが必要でした。 バージョン 4.x.x 以降では、Production の公開および非公開 API キーと、Sandbox の公開および非公開 API キーを提供する必要があります。 両方の API キーのペアを指定しない場合、管理の Product Recommendations機能にアクセスできません。 ただし、データ収集はストアフロントで引き続きおこなわれ、既存のレコメンデーションは引き続き買い物客に表示されます。

## ファイアウォール

製品Recommendationsにファイアウォールを介させるには、 `commerce.adobe.io` 許可リストに

## アンインストール [!DNL Product Recommendations] {#uninstall}

必要に応じて、 [uninstall](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) 製品レコメンデーションモジュール。
