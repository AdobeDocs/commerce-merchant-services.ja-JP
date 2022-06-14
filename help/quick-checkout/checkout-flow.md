---
title: '"チェックアウトフロー"'
description: 「 [!DNL Quick Checkout] Adobe Commerceの流れだ」
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# [!DNL Quick Checkout] 流れ

この節では、 [!DNL Quick Checkout] Adobe Commerce拡張機能の場合

成功 [!DNL Quick Checkout] フローは、次の手順で構成されます。

1. ストアフロントを開き、カートに項目を追加します。
1. チェックアウトに進みます。

![チェックアウト](assets/proceed-checkout.png)

1. プロンプトが表示されたら、 [!DNL Bolt] アカウント
1. これに送信する 1 回限りのパスワード (OTP) を入力します [!DNL Bolt] アカウントの電子メールアドレスまたは電話番号。
1. ログイン後、 [!DNL Bolt] アカウント、チェックアウトの詳細は自動的に入力されます。

   - 配送先情報
   - 支払い方法

   >[!NOTE]
   >
   > チェックアウトの詳細が自動的に入力された場合でも、既存のウォレット情報（住所またはクレジットカード情報）を使用できます。

1. 発注。

この [!DNL Quick Checkout] は、標準の追加のAdobe Commerceチェックアウトオプションと互換性があります。 [ギフトカード](https://docs.magento.com/user-guide/catalog/product-gift-card.html) または [割引コード](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Quick Checkout] 使用例

この [!DNL Quick Checkout] では、チェックアウトフロー中に複数の使用例を使用できます。

- 登録済みのゲストユーザー [!DNL Bolt] アカウント
- 新しいを使用するゲストユーザー [!DNL Bolt] アカウント
- を持つ、または登録していない既存のAdobe Commerceユーザー [!DNL Bolt] アカウント

## ゲストユーザーのチェックアウト：仕組み

ゲストのチェックアウトエクスペリエンスは、ログインしたエクスペリエンスとは異なります。 買い物客がチェックアウトに電子メールアドレスを入力すると、 [!DNL Quick Checkout] を検証して既存の [!DNL Bolt] アカウント

### 登録済み [!DNL Bolt] アカウント

次の場合、 [!DNL Bolt] アカウントが見つかった場合、買い物客は次の項目を使用して続行します [!DNL Quick Checkout] シームレスなチェックアウトエクスペリエンス：

1. これに送信する 1 回限りのパスワード (OTP) を入力します [!DNL Bolt] アカウントの電子メールアドレスまたはモバイル ( [!DNL Bolt] アカウント
1. ログイン後、 [!DNL Bolt] アカウントに入力すると、チェックアウトの詳細が自動的に入力されます。

   - 配送先情報
   - 支払い方法

1. 発注。

>[!TIP]
>
> ゲストユーザーが注文をおこない、Adobe Commerceに登録できます。

### 新規 [!DNL Bolt] アカウント

指定しない場合 [!DNL Bolt] アカウントが見つかった場合、買い物客はデフォルトの標準のAdobe Commerceチェックアウトを続行し、買い物客は注文に必要なすべての詳細を提供します。

- 配送および請求情報
- 発送方法
- 支払い方法の確認
- 登録するチェックボックスが表示されます [!DNL Bolt] チェックアウトを早めてからオーダーします。 利用規約に同意して、 [!DNL Bolt] アカウント

   ![記憶する [!DNL Bolt]](assets/checked-bolt.png)

- ゲストユーザーが注文をおこない、Adobe Commerceに登録できます。

## 既存のAdobe Commerceユーザー：仕組み

ユーザーが [!DNL Quick Checkout] を参照してください。

買い物客がチェックアウトに電子メールアドレスを入力すると、 [!DNL Quick Checkout] を検証して既存の [!DNL Bolt] アカウント

### 登録済み [!DNL Bolt] Adobe Commerceユーザーのアカウント

次の場合、 [!DNL Bolt] アカウントが見つかった場合、買い物客はデフォルトの標準のAdobe Commerceチェックアウトを続行し、買い物客は必要なすべての詳細を提供してから、順序を変更します。

- 配送および請求情報
- 発送方法
- 支払い方法の確認

詳しくは、 [トラブルシューティング](../quick-checkout/troubleshooting.md) トピックを参照してください。

>[!NOTE]
>
> ユーザーが [!DNL Bolt] アカウントと電子メールは、Adobe Commerceに登録されたものとして表示されず、1 回限りのパスワード (OTP) ログインがトリガーされます。 詳しくは、 [登録済み [!DNL Bolt] アカウント](#registered-bolt-account) フロー。

### 新規 [!DNL Bolt] アカウント

指定しない場合 [!DNL Bolt] アカウントが見つかった場合、買い物客はデフォルトのAdobe Commerceチェックアウトを続行し、保存された情報から必要なすべての詳細を選択して注文をおこないます。

- 配送および請求情報
- 発送方法
- 支払い方法の確認
- 登録するチェックボックスが表示されます [!DNL Bolt] チェックアウトを早めてからオーダーします。 利用規約に同意して、 [!DNL Bolt] アカウント

   ![記憶する [!DNL Bolt]](assets/checked-bolt.png)

## お問い合わせ

連絡先 [Adobe Commerceサポート](mailto:quick-checkout-support@adobe.com) 何か助けが必要な場合は