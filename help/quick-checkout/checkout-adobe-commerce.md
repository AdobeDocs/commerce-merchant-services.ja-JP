---
title: "Adobe Commerceユーザーのチェックアウトフロー"
description: 「 [!DNL Quick Checkout] Adobe Commerceユーザーのフロー。」
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
source-git-commit: 66082614ffe6456e2c24a1e8d9baaa1113fb7ffb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 既存のAdobe Commerceユーザー：仕組み

既存のAdobe Commerceユーザーは、 [!DNL Quick Checkout] を参照してください。

買い物客がチェックアウト時に電子メールアドレスを入力すると、 [!DNL Quick Checkout] を検証し、既存の [!DNL Bolt] アカウント

## Adobe Commerceと [!DNL Bolt]

買い物客がAdobe Commerceと [!DNL Bolt] ネットワーク、両方のネットワークは、保存された配送および支払いの詳細が提供されます。

次の場合、 [!DNL Bolt] アカウントはチェックアウト中に見つかり、買い物客は引き続き [!DNL Quick Checkout] シームレスなチェックアウトエクスペリエンス：

1. これに送信する 1 回限りのパスワード (OTP) を入力します [!DNL Bolt] アカウントの電子メールアドレスまたはモバイル（次に応じる） [ユーザーの環境設定 [!DNL Bolt] アカウント](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![OTP ポップアップ](assets/pop-up.png)

1. ログイン後、 [!DNL Bolt] アカウントに追加された場合、詳細は自動的に追加されます。

   - 配送先情報
   - 支払い方法

1. ご注文をお願いします。

>[!NOTE]
>
> 「Bolt OTP」ポップアップは、買い物客がチェックアウトページにいる場合にのみ表示されます。 買い物客は、そのポップアップウィンドウを閉じて、Bolt へのログインをオプトアウトできます。

買い物客がチェックアウト前にAdobe Commerceにログインしている場合、 [!DNL Bolt] OTP ポップアップはチェックアウト時には表示されませんが、買い物客が Bolt Wallet にアクセスするためにログインすることを勧めるメッセージが表示されます。

既存のAdobe Commerceユーザーとして注文する際に問題が発生した場合は、 [クイックチェックアウトに関する問題のトラブルシューティング](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) 記事をAdobe Commerce Help Center で参照してください。

## 自動ログイン

自動ログインコンポーネントは、買い物客がアクティブな Bolt セッションを持っているかどうかを検出し、買い物客を自動的にログインします。 これにより、買い物客が以前のセッションでアカウント検出と 1 回限りのパスコード (OTP) の手順をスキップします。

自動ログインを [!DNL Quick Checkout] ユーザー。 設定を有効にすると、チェックアウト時にユーザーに自動的にログインできます。

1. の _管理者_ サイドバー、次に移動 **ストア** > **設定** > **チェックアウト** をクリックして、一般的な「チェックアウト管理者設定」ページにアクセスします。
1. 内 _サービス設定_ セクション [!DNL Quick Checkout]、自動ログインの設定に必要なすべての詳細を指定します。

詳しくは、 [[!DNL Quick Checkout] サービス設定の構成](../quick-checkout/onboarding.md#configure-service-settings) トピックを参照してください。

>[!NOTE]
>
> 次の場合に初めてログイン **自動ログイン** が有効になっている場合、ポップアップウィンドウを受け入れて承認するには、ユーザーの同意が必要です。

## 新規 [!DNL Bolt] アカウント

指定しない場合 [!DNL Bolt] アカウントが見つかった場合、買い物客はそのままデフォルトのAdobe Commerceチェックアウトを続行し、保存された情報から必要な詳細をすべて選択して注文します。

- 配送および請求情報
- 発送方法
- 支払い方法の確認
- 登録するオプション [!DNL Bolt] チェックアウトを早めてから注文を行う場合。 買い物客は、利用条件に同意して、顧客の [!DNL Bolt] アカウント

   ![記憶する [!DNL Bolt]](assets/checkbox-remember-bolt.png)
