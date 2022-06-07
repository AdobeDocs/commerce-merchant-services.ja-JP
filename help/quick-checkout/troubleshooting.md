---
title: 「 [!DNL Quick Checkout]"
description: 「エラーのトラブルシューティング、 [!DNL Quick Checkout] Adobe Commerce拡張機能の場合」
exl-id: a379ff81-360d-4cb9-a123-47e8cbc0cdbd
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# トラブルシューティング [!DNL Quick Checkout] Adobe Commerce

これらの固有の問題を解決するには、次のトラブルシューティング方法を使用します。

## 誤った [!DNL Composer keys]

次のエラーが表示される場合は、 [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

を確認します。 [!DNL Composer keys] は、クイックMagentoの登録で使用されるチェックアウト ID にリンクされます。

どれを見るか [!DNL Composer keys] 設定済み：

1. 次の場所を検索： `auth.json` ファイル：

   ```bash
   composer config --global home
   ```

1. 次を表示： `auth.json` ファイル：

   ```bash
   cat /path/to/auth.json
   ```

1. 詳しくは、 [MagentoID に関連付けられているキー](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

## 安定性の最小値 `composer.json` は安定に設定されています

次のエラーが表示される場合は、 [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

最小安定性をに設定 `RC` 内 `composer.json` ファイル。

## PHP のメモリが不足しています

PHP のメモリが不足していることを示す次のエラーが表示される場合：

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[メモリ制限を引き上げる](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) ( `php.ini`.

または、次のコマンドを使用してメモリ制限を指定できます。 `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

例：

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## 送付先住所が無効です

には既知の問題があります [!DNL Quick Checkout].

デフォルトの配送先住所が無効な場合、顧客は配送先住所ステップにリダイレクトされます。 ストアフロントには、有効な配送先住所のみが表示されます。

>[!WARNING]
>
> 有効な配送先住所がない場合、お客様には使用可能な配送先住所が表示されません。

詳しくは、 [出荷の詳細](../quick-checkout/shipping-details.md) トピックを参照してください。

## 新しい配送先住所を含む住所行を追加

には既知の問題があります [!DNL Quick Checkout].

次の場合： [にログインする [!DNL Bolt] アカウント](https://help.bolt.com/shoppers/guides/checkout/log-in/) 新しい配送先住所を追加できます。住所ごとに 4 行の制限があります。

Adobe Commerceは通常、最大 20 番地の住所行をサポートするように設定できます。

## チェックボックス `enable terms and conditions` 適切に表示されない

には既知の問題があります [!DNL Quick Checkout].

次を有効にした場合、 `Enable terms and conditions` 」チェックボックスをオンにし、 [!DNL Bolt] アカウント、 `Enable terms and conditions` チェックアウト時にチェックボックスが表示されない。 詳しくは、 [ログイン](https://help.bolt.com/shoppers/account/login-dashboard/) [!DNL Bolt] トピックを参照してください。

詳しくは、 [利用条件](https://docs.magento.com/user-guide/sales/terms-and-conditions.html) トピックを参照してください。

## 次の場合の予期しない動作 `Display Billing Address On` が `payment page`

には既知の問題があります [!DNL Quick Checkout].

次に `Display Billing Address On` パラメータ `payment page` および [ログイン [!DNL Bolt] アカウント](https://help.bolt.com/shoppers/guides/checkout/log-in/) 次の項目を確認する場合 `My billing and shipping address are the same` チェックボックスラジオボタンが表示される `use existing card`.

![同じアドレス](assets/checked-address.png)

詳しくは、 [チェックアウト](https://docs.magento.com/user-guide/configuration/sales/checkout.html) トピックを参照してください `Display Billing Address On` パラメーター。

## の翻訳 [!DNL Quick Checkout] 拡張

Adobe Commerceを使用すると、複数の地域や市場に対してストアをローカライズすることができます。 管理者ビューでは、エラーメッセージをローカライズすることもできます。

詳しくは、 [翻訳とローカライズ](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html) トピックを参照してください。

## キャッシュをフラッシュ

1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** をクリックし、 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

## お問い合わせ

連絡先 [Adobe Commerceサポート](mailto:quick-checkout-support@adobe.com) 助けを求めて
