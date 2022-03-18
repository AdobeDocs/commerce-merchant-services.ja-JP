---
title: チェックアウトフロー
description: の概要 [!DNL Express Checkout] Adobe Commerceのフロー。
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: 163dd5260908b4ea3a8bfbcfdb834531d1603734
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---

# [!DNL Express Checkout] 流れ

>[!IMPORTANT]
>
> この機能は、Early Adopter Program(EAP) ユーザー専用で、すべてのお客様がまだアクセスできるわけではありません。 現在、米国のお客様に限定されています。 サポートおよび質問については、Adobe Commerceサポートにお問い合わせください。

この節では、 [!DNL Express Checkout] Adobe Commerce拡張機能の場合

成功 [!DNL Express Checkout] フローは、次の手順で構成されます。

1. ストアフロントを開き、カートに項目を追加します。
1. チェックアウトに進みます。

![チェックアウト](../assets/proceed-checkout.png)

1. プロンプトが表示されたら、Bolt アカウントに関連付けられた電子メールアドレスを入力します。
1. Bolt アカウントのメールアドレスまたは電話番号に送信されるワンタイムパスワード (OTP) を入力します。
1. Bolt アカウントでログインすると、チェックアウトの詳細が自動的に入力されます。

   - 配送先情報
   - 支払い方法

   >[!NOTE]
   >
   > チェックアウトの詳細が自動的に入力された場合でも、既存のウォレット情報（住所またはクレジットカード情報）を使用できます。

1. 発注。

この [!DNL Express Checkout] は、標準の追加のAdobe Commerceチェックアウトオプションと互換性があります。 [ギフトカード](https://docs.magento.com/user-guide/catalog/product-gift-card.html) または [割引コード](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Express Checkout] 使用例

この [!DNL Express Checkout] では、チェックアウトフロー中に複数の使用例を使用できます。

- 登録済みの Bolt アカウントを持つゲストユーザー。
- 新しい Bolt アカウントを持つゲストユーザー。
- Bolt アカウントを持つ、または登録していない既存のAdobe Commerceユーザー。

## ゲストユーザーのチェックアウト：仕組み

ゲストのチェックアウトエクスペリエンスは、ログインしたエクスペリエンスとは異なります。 買い物客がチェックアウトに電子メールアドレスを入力すると、 [!DNL Express Checkout] を検証して、既存の Bolt アカウントを検索します。

### 登録済み Bolt アカウント

Bolt アカウントが見つかった場合、買い物客は引き続き [!DNL Express Checkout] シームレスなチェックアウトエクスペリエンス：

1. Bolt アカウントでのユーザーの好みに応じて、Bolt アカウントの電子メールアドレスまたは携帯電話に送信される 1 回限りのパスワード (OTP) を入力します。
1. Bolt アカウントでログインすると、チェックアウトの詳細が自動的に入力されます。

   - 配送先情報
   - 支払い方法

1. 発注。

>[!TIP]
>
> ゲストユーザーが注文をおこない、Adobe Commerceに登録できます。

### 新しい Bolt アカウント

Bolt アカウントが見つからない場合、買い物客はデフォルトの標準のAdobe Commerceチェックアウトを続行し、買い物客は注文に必要なすべての詳細を提供します。

- 配送および請求情報
- 発送方法
- 支払い方法の確認
- 注文を行う前にチェックアウトを高速化するために、Bolt に登録するチェックボックスが表示されます。 利用規約に同意して、Bolt アカウントを作成できます。

   ![ボルトを記憶](../assets/checked-bolt.png)

- ゲストユーザーが注文をおこない、Adobe Commerceに登録できます。

## 既存のAdobe Commerceユーザー：仕組み

ユーザーが [!DNL Express Checkout] を参照してください。

買い物客がチェックアウトに電子メールアドレスを入力すると、 [!DNL Express Checkout] を検証して、既存の Bolt アカウントを検索します。

### Adobe Commerceユーザーに登録された Bolt アカウント

Bolt アカウントが見つかった場合、買い物客はデフォルトの標準のAdobe Commerceチェックアウトを続行し、買い物客は必要なすべての詳細を提供してから、次の順序で並べ替えます。

- 配送および請求情報
- 発送方法
- 支払い方法の確認

詳しくは、 [トラブルシューティング](../express-checkout/troubleshooting.md) トピックを参照してください。

>[!NOTE]
>
> ユーザーが Bolt アカウントを持っていて、電子メールがAdobe Commerceに登録されていない場合は、1 回限りのパスワード (OTP) ログインがトリガーされます。 詳しくは、 [登録済み Bolt アカウント](#registered-bolt-account) フロー。

### 新しい Bolt アカウント

Bolt アカウントが見つからない場合、買い物客はデフォルトのAdobe Commerceチェックアウトを続行し、保存された情報から必要な詳細をすべて選択して注文を行います。

- 配送および請求情報
- 発送方法
- 支払い方法の確認
- 注文を行う前にチェックアウトを高速化するために、Bolt に登録するチェックボックスが表示されます。 利用規約に同意して、Bolt アカウントを作成できます。

   ![ボルトを記憶](../assets/checked-bolt.png)

## お問い合わせ

サポートおよび質問については、Adobe Commerceサポートにお問い合わせください。
