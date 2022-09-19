---
title: インストール [!DNL Payment Services]
description: Payments Services 拡張機能をインストールします。
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: 7b31fe7a71c3c238e6448627b2edfe06bbfbc80e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# インストール [!DNL Payment Services]

のダウンロードとインストール [!DNL Payment Services] 拡張 [!DNL Adobe Commerce] および [!DNL Magento Open Source] は、 [!DNL Payment Services].

![[!DNL Payment Services] 拡張機能の管理ビュー](assets/admin-view.png)

## 拡張機能のダウンロード

まず、から拡張機能をダウンロードする必要があります。 [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) インストールする前に

1. 次に移動： [Commerce Marketplaceの Payment Services 拡張](https://marketplace.magento.com/magento-payment-services.html).
1. エディションとバージョンを選択するには、切り替えます。 **[!UICONTROL Edition]** および **[!UICONTROL Your store version]** を選択します。
1. クリック **[!UICONTROL Add to Cart]**.
1. チェックアウトを完了し、「 **[!UICONTROL Place Order]**.
1. 注文の確認と詳細については、Marketplace のダウンロードに関連する電子メールを確認してください。

## 拡張機能のインストール

次をインストールできます： [!DNL Payment Services] 両方の [!DNL Adobe Commerce] ご使用のコマースアカウントにリンクされているクラウドインフラストラクチャおよびオンプレミスインスタンス上 [mageid](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) 登録プロセスで提供されます。 [!DNL Magento Open Source] お客様はオンプレミスの手順を使用します。

Composer は、 [!DNL Adobe Commerce]または、Composer のキーが以前に `auth.json` ファイル。

詳しくは、 [認証キーの取得](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) を参照してください。

詳しくは、 [拡張機能のインストール](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) 拡張機能をダウンロードしてインストールする前に考慮すべき事項の詳細については、を参照してください。

### [!DNL Adobe Commerce] クラウドインフラストラクチャ

このメソッドは、 [!DNL Payment Services] Commerce Cloudインスタンスの拡張。

1. の更新 `composer.json` ファイル：

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 依存関係を更新し、拡張機能をインストールします。

   ```bash
   composer update
   ```

   この `composer update` コマンドはすべての依存関係を更新します。 すべての依存関係を同時に更新しない場合は、代わりに次のコマンドを使用します。 `composer require magento/payment-services`.

1. 変更をコミットしてプッシュします。

### オンプレミスおよびその他の設定

このメソッドは、 [!DNL Payment Services] オンプレミスインスタンスの拡張および [!DNL Magento Open Source] 顧客。

1. 拡張機能を取得するには、次のコマンドを実行します。

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 依存関係を更新し、拡張機能をインストールします。

   ```bash
   composer update
   ```

   この `composer update` コマンドはすべての依存関係を更新します。 すべての依存関係を同時に更新しない場合は、代わりに次のコマンドを使用します。 `composer require magento/payment-services`.

1. インスタンスをアップグレードします。

   ```bash
   bin/magento setup:upgrade
   ```

1. キャッシュをクリアします。

   ```bash
   bin/magento cache:clean
   ```

1. 変更をコミットします。
1. コミット済みのコードが確実にデプロイされるようにするには、インスタンスを更新します。

## 拡張機能のアップグレード

の新しいバージョンが [!DNL Payment Services] がリリースされたので、拡張機能を簡単にアップグレードできます。

1. パッケージの最新バージョンを取得するには：

   ```bash
   composer update
   ```

   この `composer update` コマンドはすべての依存関係を更新します。 すべての依存関係を同時に更新しない場合は、代わりに次のコマンドを使用します。 `composer update magento/payment-services`.

1. 変更をコミットしてプッシュします。

## トラブルシューティング

をインストールしようとすると、エラーが発生する場合があります [!DNL Payment Services] 拡張子。 次のトラブルシューティング方法を使用して、エラーを解決します。

### コンポーザーのキーが正しくありません

次のエラーが表示される場合は、コンポーザーのキーが正しくないことを示します。

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Composer のキーが `MageID` 次の場合に使用 [!DNL Payment Services] 登録。

どの Composer キーが設定されているかを確認するには：

1. 次の場所を検索： `auth.json` ファイル：

   ```bash
   composer config --global home
   ```

1. 次を表示： `auth.json` ファイル：

   ```bash
   cat /path/to/auth.json
   ```

1. 詳しくは、 [コマースアカウントに関連付けられているキー `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### PHP のメモリが不足しています

PHP のメモリが不足していることを示す次のエラーが表示される場合：

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[メモリ制限を引き上げる](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) ( `php.ini`.

または、次のコマンドを使用してメモリ制限を指定できます。 `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

例：

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
