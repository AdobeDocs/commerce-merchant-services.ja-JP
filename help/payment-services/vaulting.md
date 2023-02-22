---
title: クレジットカード保管
description: 買い物客は、後で購入する際に、クレジットカードの詳細を確認（保存）できます。
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# クレジットカード保管

1 回限りの顧客を、クレジットカードの保管機能を備えた常連客に変換します。 買い物客は、チェックアウト時にクレジットカードの資格情報を保存 (「vault」) して、同じ商人アカウント内で後の購入で使用することができます。

![後で使用するためのクレジットカードの保管](assets/save-card-for-later.png)

買い物客は、保存されたトークンを使用して、保存されたクレジットカード情報で将来のチェックアウトを完了します。

![保存された資格情報を今後の購入に使用](assets/use-stored-card.png)

また、Vault に登録されたクレジットカードを [保管済支払い方法](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) マイアカウント内で

![マイアカウントに保管された支払い方法](assets/stored-payment-methods.png)

## ヴォールティングを有効化

お客様向けのクレジットカード保管機能を有効にできます。 _および_ 管理人の商人 [!DNL Payment Services] [設定](settings.md#card-vaulting).

## 管理での Vaulting の使用

顧客が以前に Vault に登録されたクレジットカードを持っている場合、マーチャントは、管理者でその顧客の後続の注文を、Vault に登録された支払い方法を使用して作成できます。

顧客が既存のアカウントと、以前に完了した支払いからシステムに保存された有効なトークンの両方を持っている場合にのみ、管理者で Vaulted カードを使用できます。

管理者で、保留中のクレジットカードを使用して顧客の注文を作成するには、次の手順に従います。

1. [注文の作成と製品の追加](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. In _[!UICONTROL Payment & Shipping Information]_を選択します。**[!UICONTROL Stored Cards]**を支払い方法として使用します。
1. 適切な Vaulted クレジットカードの支払い方法を選択します。
1. オーダーに必要な他の手順を完了した後 [送信](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![顧客に管理者の Vault に保管されたクレジットカードを使用](assets/admin-vaultedcard.png)

## セキュリティ

最小限のクレジットカード情報が買い物客と共有され、彼らは、最後の 4 桁、有効期限、および 2 枚のアウトされたクレジットカードのブランドのみを表示します。 クレジットカード情報は、支払いプロバイダーと共に、満たすために保存されます [PCI](security.md#PCI-compliance) 準拠基準
