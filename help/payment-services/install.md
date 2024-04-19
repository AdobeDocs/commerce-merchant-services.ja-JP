---
title: インストール [!DNL Payment Services]
description: 支払いサービス拡張機能をインストールします。
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
role: Admin
feature: Payments, Checkout, Install, Upgrade
source-git-commit: 5c4fe370507e4154d4495d4c09e2ff8705e53191
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# インストール [!DNL Payment Services]

の支払いサービスの使用を開始するには [!DNL Adobe Commerce] および [!DNL Magento Open Source]では、いくつかのオンボーディング手順を完了する必要があります。

>[!INFO]
>
> のを表示 [設定 [!DNL Payment Services] Adobe Commerceの場合](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-payment-services) ビデオを参照してください。

のダウンロードとインストール [!DNL Payment Services] の拡張機能 [!DNL Adobe Commerce] および [!DNL Magento Open Source] を使用するための前提条件となる手順です [!DNL Payment Services].

![[!DNL Payment Services] 拡張機能の管理者ビュー](assets/admin-view.png){width="300" zoomable="yes"}

## 拡張機能のダウンロード

最初に、から拡張機能をダウンロードする必要があります。 [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) インストールする前に。

1. に移動します。 [Commerce Marketplaceの支払いサービス拡張機能](https://commercemarketplace.adobe.com/magento-payment-services.html).
1. エディションとバージョンを選択するには、を切り替えます **[!UICONTROL Edition]** および **[!UICONTROL Your store version]** 任意の選択に変更できます。
1. クリック **[!UICONTROL Add to Cart]**.
1. チェックアウトを完了し、 **[!UICONTROL Place Order]**.
1. 注文の確認と詳細については、Marketplace のダウンロードに関連するメールを確認してください。

## 拡張機能のインストール

をインストールできます [!DNL Payment Services] 両方の拡張機能 [!DNL Adobe Commerce] Commerce アカウントにリンクされたクラウドインフラストラクチャー上およびオンプレミスインスタンス [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) 登録プロセスで提供されます。
[!DNL Magento Open Source] お客様は、オンプレミスの手順を使用します。

Composer は、の初期インストール時にこれらのキーを使用します。 [!DNL Adobe Commerce]、または Composer キーが以前にに保存されていなかった状況で `auth.json` ファイル。

参照： [認証キーの取得](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) composer キーの取得の詳細については、を参照してください。

参照： [拡張機能のインストール](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) 拡張機能のダウンロードとインストールの前に考慮すべき事項の詳細については、を参照してください。

### [!DNL Adobe Commerce] クラウドインフラストラクチャー上

このメソッドは、 [!DNL Payment Services] Commerce Cloudインスタンス用の拡張機能。

1. を更新 `composer.json` ファイル：

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 依存関係を更新し、拡張機能をインストールします。

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   の使用 `composer update` すべてのルート依存関係を更新するコマンド。

1. 変更をコミットし、プッシュします。

### オンプレミスおよびその他の設定

このメソッドは、 [!DNL Payment Services] オンプレミスインスタンスの拡張機能および [!DNL Magento Open Source] 顧客。

1. 拡張機能を取得するには、次のコマンドを実行します。

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 依存関係を更新し、拡張機能をインストールします。

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   の使用 `composer update` すべてのルート依存関係を更新するコマンド。

1. インスタンスをアップグレード：

   ```bash
   bin/magento setup:upgrade
   ```

1. キャッシュをクリアする：

   ```bash
   bin/magento cache:clean
   ```

1. 変更をコミットします。
1. コミットされたコードが確実にデプロイされるように、インスタンスを更新します。

## 拡張機能のアップグレード

新しいバージョンの [!DNL Payment Services] はリリースされました。拡張機能を簡単にアップグレードできます。

1. パッケージの最新バージョンを取得するには：

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   の使用 `composer update` すべてのルート依存関係を更新するコマンド。

1. 変更をコミットし、プッシュします。

## トラブルシューティング

をインストールしようとすると、エラーが発生することがあります [!DNL Payment Services] 拡張機能。 次のトラブルシューティング方法を使用して、エラーを解決します。

### コンポーザーのキーが正しくありません

Composer キーが正しくないことを示す次のエラーが表示される場合：

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Composer キーが有効で、他のMagento パッケージにアクセスできることを確認します。

設定されている Composer キーを確認するには：

1. の場所を検索 `auth.json` ファイル：

   ```bash
   composer config --global home
   ```

1. を表示する `auth.json` ファイル：

   ```bash
   cat /path/to/auth.json
   ```

1. 参照： [Commerce アカウントに関連付けられているキー `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### PHP に必要なメモリが不足しています

PHP 用のメモリが足りないことを示す次のエラーが表示された場合：

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[メモリの上限を増やす](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) 使用している環境での PHP の場合： `php.ini`.

または、次のコマンドを使用してメモリ制限を指定することもできます。 `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

例：

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
