---
title: "Adobe Commerceユーザーのチェックアウトフロー"
description: 「 [!DNL Quick Checkout] Adobe Commerceユーザーのフロー。」
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
source-git-commit: d28e8ccd4362b4e32b2eb8c6e1faf38d7c99a4c2
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# 既存のAdobe Commerceユーザー：仕組み

既存のAdobe Commerceユーザーは、 [!DNL Quick Checkout] を参照してください。

買い物客がチェックアウト時に電子メールアドレスを入力すると、 [!DNL Quick Checkout] を検証し、既存の [!DNL Bolt] アカウント

## Adobe Commerceと [!DNL Bolt]

買い物客がAdobe Commerceと [!DNL Bolt] ネットワーク、両方のネットワークは、保存された配送および支払いの詳細が提供されます。

次の場合、 [!DNL Bolt] アカウントはチェックアウト中に見つかり、買い物客は引き続き [!DNL Quick Checkout] シームレスなチェックアウトエクスペリエンス：

1. これに送信する 1 回限りのパスワード (OTP) を入力します [!DNL Bolt] アカウントの電子メールアドレスまたはモバイル（次に応じる） [ユーザーの環境設定 [!DNL Bolt] アカウント](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}。

![OTP ポップアップ](assets/pop-up.png)

1. ログイン後、 [!DNL Bolt] アカウントに追加された場合、詳細は自動的に追加されます。

   - 配送先情報
   - 支払い方法

1. ご注文をお願いします。

>[!NOTE]
>
> 「Bolt OTP」ポップアップは、買い物客がチェックアウトページにいる場合にのみ表示されます。 買い物客は、そのポップアップウィンドウを閉じて、Bolt へのログインをオプトアウトできます。

買い物客がチェックアウト前にAdobe Commerceにログインしている場合、 [!DNL Bolt] OTP ポップアップはチェックアウト時には表示されません。

既存のAdobe Commerceユーザーとして注文する際に問題が発生した場合は、 [クイックチェックアウトに関する問題のトラブルシューティング](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) 記事をAdobe Commerce Help Center で参照してください。

## 新規 [!DNL Bolt] アカウント

指定しない場合 [!DNL Bolt] アカウントが見つかった場合、買い物客はそのままデフォルトのAdobe Commerceチェックアウトを続行し、保存された情報から必要な詳細をすべて選択して注文します。

- 配送および請求情報
- 発送方法
- 支払い方法の確認
- 登録するオプション [!DNL Bolt] チェックアウトを早めてから注文を行う場合。 買い物客は、利用条件に同意して、顧客の [!DNL Bolt] アカウント

   ![記憶する [!DNL Bolt]](assets/checkbox-remember-bolt.png)
