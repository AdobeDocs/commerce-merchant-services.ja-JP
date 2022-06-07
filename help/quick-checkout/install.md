---
title: '" [!DNL Quick Checkout] for Adobe Commerce extension"'
description: 次の手順に従って、 [!DNL Quick Checkout] Adobe Commerceプロジェクトに」
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# のインストール [!DNL Quick Checkout]

この [!DNL Quick Checkout] Adobe Commerceは、1 回限りのゲスト買い物客を常連のアカウント所有者に変換するための、シームレスなチェックアウトエクスペリエンスを強化します。

この [!DNL Quick Checkout] Adobe Commerceおよびの拡張 [!DNL Magento Open Source] は、 [!DNL Composer keys]( [MagentoID (mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target=&quot;_blank&quot;} が登録プロセスで提供されます。 Composer は、Adobe Commerceの初期インストール時、または [!DNL Composer keys] 以前は `auth.json` ファイル。

詳しくは、 [認証キーの取得](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target=&quot;_blank&quot;} のトピックを参照してください。 [!DNL Composer keys].

この拡張機能をインストールするには、次の 2 つの方法があります。 [Adobe Commerce an cloud infrastructure](#magento-commerce-cloud) または [オンプレミス](#on-premises) インストール。 これらの方法では、CLI（コマンドラインインターフェイス）を使用する必要があります。

## 最小安定性設定を更新

拡張機能をインストールする前に、 `minimum-stability` ～に対する要求 `RC` （リリース候補）を `composer.json` ファイルを参照してください。 IDE またはお気に入りのテキストエディタ（Visual Studio Code や Sublime Text など）を使用できます。

を `composer.json` ファイル、変更 `"minimum-stability": "stable"` から `"minimum-stability": "RC"`.

## 拡張機能のインストール

次をインストールできます： [!DNL Quick Checkout] クラウドインフラストラクチャ上のAdobe Commerceとオンプレミスインスタンスの両方の拡張機能。

### Adobe Commerce an cloud infrastructure

このメソッドは、 [!DNL Quick Checkout] Commerce Cloudインスタンスの拡張。

1. ローカルワークステーションで、クラウドプロジェクトのルートディレクトリに移動します。

1. の更新 `composer.json` ファイル：

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 依存関係を更新し、拡張機能をインストールします。

   ```bash
   composer update
   ```

   この `composer update` コマンドはすべての依存関係を更新します。 すべての依存関係を同時に更新しない場合は、代わりに次のコマンドを使用します。 `composer update magento/quick-checkout`.

1. 変更をコミットしてプッシュします。

### オンプレミス

このメソッドは、 [!DNL Quick Checkout] オンプレミスインスタンスの拡張。

1. クイックチェックアウトモジュールを `require` セクション `composer.json` ファイル：

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 依存関係を更新し、拡張機能をインストールします。

   ```bash
   composer update
   ```

   この `composer update` コマンドはすべての依存関係を更新します。 すべての依存関係を同時に更新しない場合は、代わりに次のコマンドを使用します。 `composer update magento/quick-checkout`.

1. Adobe Commerceをアップグレード：

   ```bash
   bin/magento setup:upgrade
   ```

1. キャッシュをクリアします。

   ```bash
   bin/magento cache:clean
   ```

1. 変更をコミットします。
1. オンプレミスインスタンスを更新し、コミットされたコードがデプロイされていることを確認します。

## 拡張機能のアップグレード

新しいバージョンの [!DNL Quick Checkout]を使用すると、拡張機能を簡単にアップグレードできます。

1. パッケージの最新バージョンを取得するには：

   ```bash
   composer update
   ```

   この `composer update` コマンドはすべての依存関係を更新します。 すべての依存関係を同時に更新しない場合は、代わりに次のコマンドを使用します。 `composer update magento/quick-checkout`.

1. 変更をコミットしてプッシュします。

## トラブルシューティング

をインストールしようとすると、エラーが発生する場合があります [!DNL Quick Checkout] 拡張子。

詳しくは、 [トラブルシューティング](../quick-checkout/troubleshooting.md) トピックを参照してください。 [!DNL Quick Checkout].

## 前提条件

詳しくは、 [前提条件](../quick-checkout/prerequisites.md) トピックを参照してください。
