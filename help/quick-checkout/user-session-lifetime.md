---
title: ユーザーセッションの有効期間
description: 管理者は、Adobe Commerceユーザーの Cookie の有効期間を [!DNL Quick Checkout] 拡張子。
exl-id: 32cf5d70-9a50-49ca-8b40-5f04bc1e24b7
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# ユーザーセッションの有効期間

買い物客セッションの有効期間は、Adobe Commerce管理者で設定できる、いくつかの要因によって決まります。 詳しくは、 [cookie の有効期間の設定](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/configure/customer-online-options.html){target=_blank} を参照してください。

設定された有効期間の cookie は、 [!DNL Quick Checkout] 次の場合：

1. 無操作状態のため、買い物客はAdobe Commerceからログアウトします。
1. The [!DNL Bolt] セッションの有効期限が切れます。

買い物客が [!DNL Bolt] セッションの有効期限が切れると、注文は正常に配置されましたが、ユーザーは両方のネットワークからログアウトされます。

チェックアウトが成功してもユーザーがアクティブな場合、Adobe Commerceおよび [!DNL Bolt].
