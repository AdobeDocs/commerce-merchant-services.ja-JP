---
title: '"[!DNL Quick Checkout] Adobe Commerce開発者向け情報»'
description: '"[!DNL Quick Checkout] 開発者情報」'
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
feature: Checkout, Services
role: Developer
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# [!DNL Quick Checkout] 開発者情報

このトピックには、Adobe Commerceおよび [!DNL Magento Open Source] コードを作成し、 [!DNL Quick Checkout] 拡張子。

## 拡張ポイント

拡張ポイントを使用した [!DNL Quick Checkout].

拡張機能ポイントを使用すると、アプリケーションコード内のコアコンポーネントを実際に変更することなく、カスタマイズを行うことができます。

## 発送先の詳細ステップ

拡張ポイントを使用して、でログインした後の自動ステップナビゲーションをカスタマイズできます。 [!DNL Bolt].

買い物客が [!DNL Bolt]の場合、すべての有効な情報が事前入力され、注文をおこなうための支払いの詳細ステップにリダイレクトされます。 詳しくは、 [チェックアウトフロー](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-flow.html) トピックを参照してください。

この拡張ポイントは、支払い手順への移動を防ぎ、買い物客が出荷手順に対して追加のアクションを実行する必要がある拡張機能がある場合に役立ちます。 拡張機能ポイントと Mixin の使用方法について、以下の例を参照してください。

1. での新しい Mixin の登録 `require-config.js` 次の場所にあるファイル： `app/code/Vendor/ModuleName/view/frontend/`.

   ```js
   var config = {
       config: {
           mixins: {
               "Magento_ExpressCheckout/js/model/can-navigate-to-payment": {
                   "Vendor/ModuleName/js/model/can-navigate-to-payment-mixin": true
               }
           }
       }
   };
   ```

1. でモデルを拡張する `can-navigate-to-payment.js` 次の場所にあるファイル： `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

   ```js
   define([
       'Magento_Checkout/js/model/quote',
       'mage/utils/wrapper',
   ], function (quote, wrapper) {
       'use strict';
       return function (canNavigateToPayment) {
           return wrapper.wrap(canNavigateToPayment, function (originalAction) {
               /* Include custom checks or conditions to stay on the shipping step,i.e: your shopper is from Germany */
               return originalAction() && quote.shippingAddress().countryId !== 'DE');
           });
       };
   });
   ```

>[!WARNING]
>
> これは、ドイツ (DE) の買い物客が配送の詳細ステップに滞在したい場合の例です。

チェック [[!DNL Bolt] 開発者向けヘルプ](https://help.bolt.com/developers/) 詳しくは、 [!DNL Bolt] 開発者向け。
