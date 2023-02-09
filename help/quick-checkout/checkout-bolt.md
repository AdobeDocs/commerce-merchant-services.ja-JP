---
title: "Adobe Commerceでの Bolt ユーザーのチェックアウトフロー"
description: の概要 [!DNL Quick Checkout] Adobe Commerceの Bolt ユーザーのフロー。
exl-id: 12f58b7e-1f86-4891-b225-9f4be82c2d5d
source-git-commit: 66082614ffe6456e2c24a1e8d9baaa1113fb7ffb
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# ゲストユーザー

ゲストのチェックアウトエクスペリエンスは、Adobeのユーザーエクスペリエンスとは異なります。 買い物客がチェックアウトに電子メールアドレスを入力すると、 [!DNL Quick Checkout] を検証し、既存の [!DNL Bolt] アカウント

>[!WARNING]
>
> この [!DNL In-Store Pickup] (ISPU) 機能は、 [!DNL Quick Checkout] が有効になっている。

## 登録済み [!DNL Bolt] アカウント

次の場合、 [!DNL Bolt] アカウントが見つかった場合、買い物客は次の項目を使用して続行します [!DNL Quick Checkout] シームレスなチェックアウトエクスペリエンス：

1. これに送信する 1 回限りのパスワード (OTP) を入力します [!DNL Bolt] アカウントの電子メールアドレスまたはモバイル（次に応じる） [ユーザーの環境設定 [!DNL Bolt] アカウント](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![OTP ポップアップ](assets/pop-up.png)

1. ログイン後、 [!DNL Bolt] アカウントに追加された場合、詳細は自動的に追加されます。

   - 配送先情報
   - 支払い方法

1. ご注文をお願いします。

>[!TIP]
>
> ゲストユーザーが注文をおこない、オプションでAdobe Commerceに登録できます。

## 新規 [!DNL Bolt] アカウント

指定しない場合 [!DNL Bolt] アカウントが見つかった場合、買い物客はデフォルトの標準のAdobe Commerceチェックアウトを続行し、買い物客は注文に必要なすべての詳細を提供します。

- 配送および請求情報
- 発送方法
- 支払い方法の確認
- 登録するチェックボックスが表示されます [!DNL Bolt] チェックアウトを早めてからオーダーします。 買い物客は、利用条件に同意して、顧客の [!DNL Bolt] アカウント

   ![記憶する [!DNL Bolt]](assets/checkbox-remember-bolt.png)

- ゲストユーザーが注文をおこない、オプションでAdobe Commerceに登録できます。
