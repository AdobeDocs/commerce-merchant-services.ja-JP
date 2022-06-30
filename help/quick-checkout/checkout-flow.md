---
title: '"チェックアウトフロー"'
description: 「 [!DNL Quick Checkout] Adobe Commerceの流れだ」
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: 01bb92d1de1f6a6da1d6326c0190eb7711274045
workflow-type: tm+mt
source-wordcount: '176'
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

- [ゲストユーザー](../quick-checkout/checkout-adobe-commerce.md) 登録された、または新しい [!DNL Bolt] アカウント
- 既存の [Adobe Commerceユーザー](../quick-checkout/checkout-adobe-commerce.md) 登録を受けている/登録を受けていない [!DNL Bolt] アカウント

## お問い合わせ

連絡先 [Adobe Commerceサポート](mailto:quick-checkout-support@adobe.com) 何か助けが必要な場合は
