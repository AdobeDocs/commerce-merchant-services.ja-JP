---
title: 空白
description: ボイドを使用すると、購入金額の認証によってブロックまたは保留されたクレジットカードまたはデビットカードの口座の資金を解放できます。
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
source-git-commit: 7b31fe7a71c3c238e6448627b2edfe06bbfbc80e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 空白

を使用 [!DNL Payment Services]を使用すると、既存のコマース機能を使用してトランザクションを無効にできます。 ボイドを使用すると、購入金額の認証によってブロックまたは保留されたクレジットカードまたはデビットカードの口座の資金を解放できます。

>[!NOTE]
>
>支払がまだキャプチャされていない場合にのみ、取引を無効にできます。

ストアが [設定済み](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} ：販売時点での（取得できない）資金のみを承認し、店舗からの購入により、 `Processing` コマース管理でのステータス。

また、 [注文をキャンセルする](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order)請求されていない {target=&quot;_blank&quot;}。 キャンセル処理の一環として、取り込まれていない認証も無効になります。

>[!NOTE]
>
>オーダーをキャンセルしても、ボイドが生成されますが、オーダーを無効にしても、キャンセルはトリガーされません。

注文の基本的な手順について詳しくは、 [注文ワークフロー](https://docs.magento.com/user-guide/sales/order-workflow.html){target=&quot;_blank&quot;} のトピックを参照してください。

無効機能と注文取引を無効にする方法については、 [オーダーの処理](https://docs.magento.com/user-guide/sales/order-processing.html){target=&quot;_blank&quot;}（コアユーザーガイド）。
