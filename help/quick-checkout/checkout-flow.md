---
title: 「Adobe Commerceのチェックアウトフロー」
description: 「 [!DNL Quick Checkout] Adobe Commerceの流れだ」
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: 66082614ffe6456e2c24a1e8d9baaa1113fb7ffb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Quick Checkout] 流れ

この節では、 [!DNL Quick Checkout] Adobe Commerce拡張機能の場合

成功 [!DNL Quick Checkout] フローは、次の手順で構成されます。

1. ストアフロントを開き、カートに項目を追加します。
1. チェックアウトに進みます。

![チェックアウト](assets/proceed-checkout.png)

>[!NOTE]
>
> マーチャントに対する自動ログインを有効にすることができます。 詳しくは、 [Bolt&#39;s Enable Automatic Login トピック](https://help.bolt.com/products/embedded/direct-api/auto-login/) を参照してください。

1. プロンプトが表示されたら、 [!DNL Bolt] アカウント
1. これに送信する 1 回限りのパスワード (OTP) を入力します [!DNL Bolt] アカウントの電子メールアドレスまたは電話番号。

![OTP ポップアップ](assets/pop-up.png)

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

- [ゲストユーザー](../quick-checkout/checkout-bolt.md) 登録された、または新しい [!DNL Bolt] アカウント
- 既存の [Adobe Commerceユーザー](../quick-checkout/checkout-adobe-commerce.md) 登録を持っているか、持っていないか [!DNL Bolt] アカウント

## お問い合わせ

を通じてAdobe Commerceサポートに問い合わせる [Adobe Commerce Help Center](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html) 何か助けが必要な場合は
