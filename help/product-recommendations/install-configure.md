---
title: インストールと設定
description: ' [!DNL Product Recommendations] をインストール、更新、アンインストールする方法を説明します。'
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
role: Admin, Developer
source-git-commit: 96a5791c5716f612f473540f27bd3f99b1bfe7c8
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# インストールと設定

[!DNL Product Recommendations] をストアフロントおよび管理者にデプロイするには、モジュールをインストールして ](../landing/saas.md)1}Commerce サービスコネクタ } を設定する必要があります。 [更新がリリースされると、インストールを最新バージョンに簡単に更新できます。

- [インストール](#install)
- [設定](#configure)
- [更新](#update)
- [Uninstall](#uninstall)

## [!DNL Product Recommendations] のインストール {#install}

[!DNL Product Recommendations] モジュールはスタンドアロンメタパッケージなので、アップデートはAdobe Commerceよりも頻繁にリリースされます。 最新のバグ修正と機能を確認するには、[ リリースノート ](release-notes.md) を参照してください。

Composer を使用して `magento/product-recommendations` モジュールをインストールします。

```bash
composer require magento/product-recommendations
```

### ページビルダーのサポートの追加 {#pbsupport}

ページビルダーの [!DNL Product Recommendations] はオプションのモジュールで、個別にインストールされます。 ページビルダーで [!DNL Product Recommendations] を使用するには、次のコマンドを実行してモジュールをインストールします。

```bash
composer require magento/module-page-builder-product-recommendations
```

ページビルダーで [!DNL Product Recommendations] を有効にすると、ページ、ブロック、動的ブロックなど、ページビルダーで作成した任意のコンテンツに既存のアクティブな [ レコメンデーションユニット ](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) を追加できます。

詳しくは [ ページビルダーコンテンツの使用  [!DNL Product Recommendations]  を参照 ](page-builder.md) てください。

### 視覚的類似性レコメンデーションタイプを追加 {#vissimsupport}

_視覚的類似性_ レコメンデーションタイプを使用すると、表示している製品に [ 視覚的に類似 ](type.md#visualsim) している製品を表示するレコメンデーションユニットを製品の詳細ページにデプロイできます。 このレコメンデーションタイプは、商品の画像や視覚的側面がショッピング体験の重要な部分である場合に最も役立ちます。 次のコマンドを実行して、「_ビジュアルな類似性_」レコメンデーションタイプをインストールします。

```bash
composer require magento/module-visual-product-recommendations
```

## [!DNL Product Recommendations] の設定 {#configure}

`magento/product-recommendations` モジュールをインストールした後、API キーを指定して SaaS Data Space を選択することにより ](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html)1}Commerce サービスコネクタを設定する必要があります。[

カタログの書き出しが正しく実行されていることを確認するには、[cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) ジョブと [ インデクサー ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) が実行され、`Product Feed` インデクサーが `Update by Schedule` に設定されていることを確認します。

API キーを使用してCommerce サービスに正常にリンクし、SaaS Data Space を指定すると、カタログの同期が開始されます。 その後、行動データがストアフロントに送信されていることを [ 確認 ](verify.md) できます。

## [!DNL Product Recommendations] インストールの更新 {#update}

他のすべてのAdobe Commerceと同様に、[!DNL Product Recommendations] はインストールとアップデートに Composer を使用します。 `magento/product-recommendations` モジュールを更新するには、次の手順を実行します。

```bash
composer update magento/product-recommendations --with-dependencies
```

3.0 から 4.0 などのメジャーバージョンにアップデートするには、プロジェクトのルート `composer.json` ファイルを編集する必要があります。 （最新のバージョンについて詳しくは、[ リリースノート ](release-notes.md) を参照してください）。 例えば、メインの `composer.json` ファイルを開いて、`magento/product-recommendations` モジュールを検索します。

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

メジャーバージョンを `3.0` から `4.0` に変更しましょう。

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

`composer.json` ファイルを保存し、次を実行します。

```bash
composer update magento/product-recommendations --with-dependencies
```

または、`magento/module-visual-product-recommendations` モジュールと `magento/module-page-builder-product-recommendations` モジュールがインストールされている場合は、次の手順を実行します。

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> Product Recommendationsのバージョン 3.x.x では、1 つの API キーのみが必要でした。 バージョン 4.x.x 以降では、実稼動用の公開 API および秘密 API キーと、サンドボックスの公開 API および秘密 API キーを指定する必要があります。 API キーの両方のペアを指定しない場合は、管理者の Product Recommendations機能にアクセスできません。 ただし、データ収集はストアフロントで続行され、既存のお勧めは引き続き買い物客に表示されます。

## ファイアウォール

Product Recommendationsがファイアウォールを通過できるようにするには、許可リストに `commerce.adobe.io` を追加します。

## [!DNL Product Recommendations] のアンインストール {#uninstall}

必要に応じて、製品レコメンデーションモジュールを [ アンインストール ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) できます。
