---
title: クレジットカードの保管
description: 買い物客は、後で購入する際に、クレジットカードの詳細を確認（保存）できます。
source-git-commit: c993a2afe5b4da478ab57cbb391bb524d83c3d1a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# クレジットカードの保管

1 回限りの顧客を、クレジットカードの保管機能を備えた常連客に変換します。 買い物客は、チェックアウト時にクレジットカードの資格情報を保存 (「vault」) して、同じ商人アカウント内で後の購入で使用することができます。

![後で使用するためのクレジットカードの保管](assets/save-card-for-later.png)

買い物客は、保存されたトークンを使用して、保存されたクレジットカード情報で将来のチェックアウトを完了します。

![保存された資格情報を今後の購入に使用](assets/use-stored-card.png)

また、Vault に登録されたクレジットカードを [保管済支払い方法](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) マイアカウント内で

![マイアカウントに保管された支払い方法](assets/stored-payment-methods.png)

## ヴォールティングを有効化

支払サービスの店舗でのクレジットカード保管を有効にできます [設定](settings.md#card-vaulting).

## セキュリティ

最小限のクレジットカード情報が買い物客と共有され、彼らは、最後の 4 桁、有効期限、および 2 枚のアウトされたクレジットカードのブランドのみを表示します。 クレジットカード情報は、支払いプロバイダーと共に、満たすために保存されます [PCI](security.md#PCI-compliance) 準拠基準
