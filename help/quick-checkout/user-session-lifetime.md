---
title: ユーザーセッションの有効期間
description: 管理者は、Adobe Commerceユーザーの Cookie の有効期間を [!DNL Quick Checkout] 拡張子。
exl-id: 32cf5d70-9a50-49ca-8b40-5f04bc1e24b7
source-git-commit: 2f14cd437be6d48e24e56b3b31a1c640357b27e3
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# ユーザーセッションの有効期間

買い物客セッションの有効期間は、Adobe Commerce管理者で設定できる、いくつかの要因によって決まります。 詳しくは、 [cookie の有効期間の設定](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/configure/customer-online-options.html){target=_blank} を参照してください。

設定された有効期間の cookie は、 [!DNL Quick Checkout] 次の場合：

1. 無操作状態のため、買い物客はAdobe Commerceからログアウトします。
1. この [!DNL Bolt] セッションの有効期限が切れます。

買い物客が [!DNL Bolt] セッションの有効期限が切れると、注文は正常に配置されましたが、ユーザーは両方のネットワークからログアウトされます。

チェックアウトが成功してもユーザーがアクティブな場合、Adobe Commerceおよび [!DNL Bolt].
