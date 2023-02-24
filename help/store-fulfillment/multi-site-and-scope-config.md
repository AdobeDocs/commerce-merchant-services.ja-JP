---
title: 複数の Web サイトおよび範囲の設定
description: 複数の Web サイトやストア範囲の在庫と配信方法を設定します。
role: User, Admin
level: Intermediate
exl-id: 8939046e-1c26-4380-83be-ff8e074e591d
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# 複数の Web サイトおよび範囲の設定

次の設定が可能です。 [範囲](https://docs.magento.com/user-guide/configuration/scope.html) 複数の web サイト、ストア、ストアの表示を収容するいくつかの要素の場合：

- [在庫の管理](https://docs.magento.com/user-guide/catalog/inventory-stock.html) 範囲ごと

- 管理 [!DNL Delivery Methods] 範囲ごと

在庫は、Web サイトまたは店舗の範囲に割り当てることができます。 次に、ストアのソースを更新して、使用可能な配信方法（ホーム配信、ストアピックアップ）を設定します。

設定が正常に更新された後、Adobe Commerceストアフロントの製品の詳細ページ (PDP) のストアのピックアップオプションは、ストアのピックアップを許可する在庫ソースから利用可能な製品に対してのみ選択できます。

## ストア内ピックアップ設定の管理

を有効または無効にする [!UICONTROL In-Store Pickup] 各 web サイトまたはストア範囲のオプション [配信方法の設定](enable-general.md#delivery-methods) 」と入力します。

1. に移動します。 **[!UICONTROL Stores > Configuration]**.

1. 設定する範囲（保存する Web サイト）を選択します。

1. 範囲を選択した状態で、に移動します。 **[!UICONTROL Sales > Delivery Methods]**.

1. を無効または有効にする **[!UICONTROL In-Store Pickup]** 配信方法。

また、このセクションでは、カーブサイドまたは店内でのピックアップをグローバルに使用できるかどうかを管理できます。

の管理 [!UICONTROL In-Store Pickup] および [!UICONTROL Delivery Method] 在庫ソースごとの設定。 実装を完全に柔軟におこなうには、他にも多数の設定が存在します。
