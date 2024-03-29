---
title: "インストール [!DNL Quick Checkout] for Adobe Commerce extension"
description: 「次の手順に従って、 [!DNL Quick Checkout] Adobe Commerceプロジェクトに」
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
feature: Checkout, Services, Install
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# インストール [!DNL Quick Checkout]

The [!DNL Quick Checkout] Adobe Commerceおよびの拡張機能 [!DNL Magento Open Source] を使用してインストールできます。 [!DNL Composer keys]（ Commerce アカウントにリンクされています） [`mageid`](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target="_blank"} 登録プロセスで提供されます。 Composer は、Adobe Commerceの初期インストール時、または [!DNL Composer keys] は、以前は `auth.json` ファイル。

詳しくは、 [認証キーの取得](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target="_blank"} の取得に関する詳細情報のトピック [!DNL Composer keys].

この拡張機能をインストールするには、次の 2 つの方法があります。 [Adobe Commerce an cloud infrastructure](#magento-commerce-cloud) または [オンプレミス](#on-premises) インストール。 これらの方法では、CLI（コマンドラインインターフェイス）を使用する必要があります。

## 最小安定性設定を更新

拡張機能をインストールする前に、 `minimum-stability` フィールドの `composer.json` ファイルが `"stable"`:

`"minimum-stability": "stable"`

## 拡張機能のインストール

次をインストールできます： [!DNL Quick Checkout] クラウドインフラストラクチャ上のAdobe Commerceとオンプレミスインスタンスの両方の拡張機能。

### Adobe Commerce an cloud infrastructure

このメソッドは、 [!DNL Quick Checkout] Commerce Cloudインスタンスの拡張。

1. ローカルワークステーションで、クラウドプロジェクトのルートディレクトリに移動します。

1. を更新します。 `composer.json` ファイル：

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 依存関係を更新し、拡張機能をインストールします。

   ```bash
   composer update
   ```

   The `composer update` コマンドは、すべての依存関係を更新します。 すべての依存関係を同時に更新しない場合は、代わりに次のコマンドを使用します。 `composer update magento/quick-checkout`.

1. 変更をコミットしてプッシュします。

### オンプレミス

このメソッドは、 [!DNL Quick Checkout] オンプレミスインスタンスの拡張。

1. クイックチェックアウトモジュールを `require` のセクション `composer.json` ファイル：

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 依存関係を更新し、拡張機能をインストールします。

   ```bash
   composer update
   ```

   The `composer update` コマンドは、すべての依存関係を更新します。 すべての依存関係を同時に更新しない場合は、代わりに次のコマンドを使用します。 `composer update magento/quick-checkout`.

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

の新しいバージョンをリリースする際 [!DNL Quick Checkout]を使用すると、拡張機能を簡単にアップグレードできます。

1. パッケージの最新バージョンを取得するには：

   ```bash
   composer update
   ```

   The `composer update` コマンドは、すべての依存関係を更新します。 すべての依存関係を同時に更新しない場合は、代わりに次のコマンドを使用します。 `composer update magento/quick-checkout`.

1. 変更をコミットしてプッシュします。

## トラブルシューティング

をインストールしようとすると、エラーが発生する場合があります。 [!DNL Quick Checkout] 拡張子。

次の期間中に問題が発生した場合 [!DNL Quick Checkout] インストールプロセスについては、 [クイックチェックアウトに関する問題のトラブルシューティング](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) ( Adobe Commerceヘルプセンター )

## 前提条件

詳しくは、 [前提条件](../quick-checkout/prerequisites.md) トピックを参照してください。
