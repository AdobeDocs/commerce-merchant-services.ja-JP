---
title: のインストール [!DNL Express Checkout] Adobe Commerce拡張機能
description: 次の手順に従って、 [!DNL Upgrade Compatibility Tool] Adobe Commerceプロジェクト用
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: 163dd5260908b4ea3a8bfbcfdb834531d1603734
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# のインストール [!DNL Express Checkout]

>[!IMPORTANT]
>
> この機能は、Early Adopter Program(EAP) ユーザー専用で、すべてのお客様がまだアクセスできるわけではありません。 現在、米国のお客様に限定されています。 サポートおよび質問については、Adobe Commerceサポートにお問い合わせください。

この [!DNL Express Checkout] Adobe Commerceは、1 回限りのゲスト買い物客を常連のアカウント所有者に変換するための、シームレスなチェックアウトエクスペリエンスを強化します。

この [!DNL Express Checkout] Adobe CommerceおよびMagento Open Source用の拡張機能は、Composer のキーと共にインストールできます。このキーは、 [MagentoID (mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target=&quot;_blank&quot;} が登録プロセスで提供されます。 Composer は、Adobe Commerceの初回インストール時、または Composer のキーが以前に `auth.json` ファイル。

詳しくは、 [認証キーの取得](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target=&quot;_blank&quot;} を参照してください。

この拡張機能をインストールするには、次の 2 つの方法があります。 [Adobe Commerce an cloud infrastructure](#magento-commerce-cloud) または [オンプレミス](#on-premises) インストール。 これらの方法では、CLI（コマンドラインインターフェイス）を使用する必要があります。

## 最小安定性設定を更新

拡張機能をインストールする前に、 `minimum-stability` ～に対する要求 `RC` （リリース候補）を `composer.json` ファイルを参照してください。 IDE またはお気に入りのテキストエディタ（Visual Studio Code や Sublime Text など）を使用できます。

を `composer.json` ファイル、変更 `"minimum-stability": "stable"` から `"minimum-stability": "RC"`.

## 拡張機能のインストール

次をインストールできます： [!DNL Express Checkout] クラウドインフラストラクチャ上のAdobe Commerceとオンプレミスインスタンスの両方の拡張機能。

### Adobe Commerce an cloud infrastructure

このメソッドは、 [!DNL Express Checkout] Commerce Cloudインスタンスの拡張。

1. ローカルワークステーションで、クラウドプロジェクトのルートディレクトリに移動します。

1. の更新 `composer.json` ファイル：

   ```bash
   composer require magento/express-checkout --no-update
   ```

1. 依存関係を更新し、拡張機能をインストールします。

   ```bash
   composer update
   ```

   この `composer update` コマンドはすべての依存関係を更新します。 すべての依存関係を同時に更新しない場合は、代わりに次のコマンドを使用します。 `composer update magento/express-checkout`.

1. 変更をコミットしてプッシュします。

### オンプレミス

このメソッドは、 [!DNL Express Checkout] オンプレミスインスタンスの拡張。

1. 高速チェックアウトモジュールを `require` セクション `composer.json` ファイル：

   ```bash
   composer require magento/express-checkout --no-update
   ```

1. 依存関係を更新し、拡張機能をインストールします。

   ```bash
   composer update
   ```

   この `composer update` コマンドはすべての依存関係を更新します。 すべての依存関係を同時に更新しない場合は、代わりに次のコマンドを使用します。 `composer update magento/express-checkout`.

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

新しいバージョンの [!DNL Express Checkout]を使用すると、拡張機能を簡単にアップグレードできます。

1. パッケージの最新バージョンを取得するには：

   ```bash
   composer update
   ```

   この `composer update` コマンドはすべての依存関係を更新します。 すべての依存関係を同時に更新しない場合は、代わりに次のコマンドを使用します。 `composer update magento/express-checkout`.

1. 変更をコミットしてプッシュします。

## トラブルシューティング

をインストールしようとすると、エラーが発生する場合があります [!DNL Express Checkout] 拡張子。

詳しくは、 [トラブルシューティング](../express-checkout/troubleshooting.md) トピックを参照してください。 [!DNL Express Checkout].

## 前提条件

詳しくは、 [前提条件](../express-checkout/prerequisites.md) トピックを参照してください。
