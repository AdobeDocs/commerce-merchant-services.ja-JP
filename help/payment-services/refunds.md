---
title: 払い戻し
description: 返金の作成対象 [!DNL Payment Services] クレジット・メモ・プロセスの一部として管理者でのオーダー。
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# 払い戻し

払い戻し [!DNL Payment Services] オーダーは、クレジット・メモ・プロセスの一環として管理で作成されます。 クレジットメモとは、購入に対して適用したり、顧客に直接返金したりできる、全額または一部払い戻しに対する顧客の支払い額を示す文書です。 クレジットメモは、 [請求済み](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"}.

詳しくは、 [クレジットメモ](https://docs.magento.com/user-guide/sales/credit-memos.html){target="_blank"} （コアユーザーガイド）を参照してください。

PayPal またはクレジットカードで処理される注文の場合は、次の操作を実行できます。

* 注文の全額を払い戻す
* 注文の一部金額（または複数の一部金額）を返金する
* 特定の注文項目の値より小さい金額を返金する

詳しくは、 [クレジット・メモの発行](https://docs.magento.com/user-guide/sales/credit-memo-create.html){target="_blank"} （コアユーザーガイド）を参照してください。

>[!NOTE]
>
>残りの注文額（元の金額から既存の返金額の合計を引いた額）を超える注文の一部を返金しようとすると、または全額を超える金額の返金を発行すると、PayPal またはクレジットカード処理の注文にエラーが発生します。

The [!UICONTROL Payment Action] の設定 [!UICONTROL Payment Settings] configuration — 次のいずれか `Authorize` または `Authorize and Capture` — を指定します。 [基本払い戻しワークフロー](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target="_blank"} 注文の場合。

詳しくは、 [支払アクション設定セクション](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target="_blank"} / _クレジット・メモの発行_ を参照してください。
