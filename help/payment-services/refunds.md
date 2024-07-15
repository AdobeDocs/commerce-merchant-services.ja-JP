---
title: 払戻
description: クレジット  [!DNL Payment Services]  モ処理の一部として、管理で受注の払戻を作成します。
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# 払戻

[!DNL Payment Services] 注文の払戻は、クレジット・メモ処理の一部として管理者で作成されます。 クレジットメモは、全額払い戻しまたは一部払い戻しのために顧客に支払われる金額を示す文書で、購入に対して適用したり、顧客に直接払い戻したりできます。 クレジット メモは、[ 請求済 ](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"} 注文に対してのみ発行できます。

詳しくは、コアユーザーガイドの [ クレジットメモ ](https://docs.magento.com/user-guide/sales/credit-memos.html){target="_blank"} を参照してください。また、クレジットメモの発行方法と印刷方法についても説明しています。

PayPal またはクレジットカードで処理される注文の場合は、次のことができます。

* 注文の全金額を返金
* 注文の一部（または複数）の金額の一部を返金
* 特定の注文項目の値に満たない金額の返金

詳しくは、コアユーザーガイドの [ クレジットメモの発行 ](https://docs.magento.com/user-guide/sales/credit-memo-create.html){target="_blank"} を参照してください。

>[!NOTE]
>
>PayPal またはクレジットカードで処理された注文で、残りの注文金額（元の金額から既存の払い戻しの合計を差し引いた金額）を超える注文に対して部分的に払い戻しを行おうとした場合、または注文額全体を超える金額に対して払い戻しを行った場合にエラーが発生します。

[!UICONTROL Payment Settings] 設定の [!UICONTROL Payment Action] 設定（`Authorize` または `Authorize and Capture`）によって、注文の [ 基本返金ワークフロー ](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target="_blank"} が決まります。

詳しくは、[ クレジット・メモの発行 ](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target="_blank"} の _支払処理設定_ の項を参照してください。
