---
title: クレジットカードの保管
description: 買い物客は、今後の購入のためにクレジットカードの詳細をヴォールティング（保存）できます。
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
feature: Payments, Checkout
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# クレジットカードの保管

クレジットカードヴォールティングを使用して、1 回限りの顧客を常連客に変換します。 買い物客は、チェックアウト時にクレジットカードの認証情報を保存（または「コンテナ」）して、同じマーチャントアカウント内の同じ店舗または別の店舗で後から購入する際に使用できます。

![ 後で使用するためにクレジットカードをヴォールティングする ](assets/save-card-for-later.png){width="400" zoomable="yes"}

買い物客は、保存されたトークンを使用して、保存済みのクレジットカード情報を使用して今後のチェックアウトを完了します。

![ 今後の購入のために保存された資格情報を使用する ](assets/use-stored-card.png){width="400" zoomable="yes"}

また、自分のマイアカウントにある [ 保存された支払い方法 ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/payments/stored-payment-methods) から簡単にボールト化されたクレジットカードを削除できます。

![ マイアカウントに保存されているお支払い方法 ](assets/stored-payment-methods.png){width="400" zoomable="yes"}

>[!WARNING]
>
>PayPal は現在、最大 5 枚のボルト付きカードを保存できます。

## ボルトを有効にする

[!DNL Payment Services] のストア _設定 ](settings.md#card-vaulting) で、顧客_ および管理者のマーチャント）に対してクレジットカードヴォールティングを有効にするこ [ ができます。

## 管理者でボルトを使用

顧客が以前にヴォールティングされたクレジットカードを持っている場合、マーチャントは、ヴォールティングされた支払い方法を使用して、管理者でその顧客の後続の注文を作成できます。

管理者でボルト付きカードを使用できるのは、顧客が既存のアカウントと、以前に完了した支払いからシステムに保存された有効なトークンの両方を持っている場合のみです。

ボールトに保管されたクレジット・カードを使用して顧客の受注を管理で作成する手順は、次のとおりです。

1. [ 注文を作成して製品を追加する ](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html)。
1. _[!UICONTROL Payment & Shipping Information]_で、支払方法として&#x200B;**[!UICONTROL Stored Cards]**を選択します。
1. 目的のボルト付きクレジットカードの支払方法を選択します。
1. 注文に必要なその他の手順を完了したら、[ 送信 ](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order) します。

   ![ 管理者がボルト化されたクレジットカードを顧客に使用 ](assets/admin-vaultedcard.png){width="600" zoomable="yes"}

## セキュリティ

最小限のクレジットカード情報は、買い物客と共有され、保管されたクレジットカードの最後の 4 桁、有効期限、ブランドのみが表示されます。 クレジットカード情報は、[PCI](security.md#PCI-compliance) コンプライアンス基準を満たすために支払いプロバイダーに保存されます。
