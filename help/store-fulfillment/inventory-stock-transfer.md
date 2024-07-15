---
title: Inventory management Sourceの転送
description: 「Adobe Commerce Inventory managementを使用した  [!DNL Store Fulfillment solution]  の在庫の設定 新しい在庫を設定し、在庫をデフォルトの在庫から転送して、ストアフルフィルメントソリューションで必要なストアピックアップ機能を有効にするように設定されたソースに割り当てることができます。」
role: Admin
level: Intermediate
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Inventory management Sourceの転送

[!DNL Store Fulfillment] ソリューションでは、ネイティブのAdobe Commerce Inventory managementを使用します。 デフォルトでは、[!DNL Commerce] 設定はすべての web インベントリをデフォルトの在庫に割り当てます。デフォルトの在庫には追加のソースを割り当てることはできません。 Web サイトには 1 つの在庫のみを割り当てることができるので、マーチャントは新しい在庫を設定し、オプションで、デフォルトのソースインベントリを適切な範囲に割り当てられたソースに転送する必要があります。 次に、ソースを新しい在庫に割り当てることができます。

>[!IMPORTANT]
>
>マーチャントは、グループおよびバンドル製品タイプに含まれるすべての製品のデフォルトソースを維持する必要があります。 これらの製品には、在庫品目の最小数量しきい値を満たし、在庫ステータスが [!UICONTROL In Stock] の在庫数量が必要です。

これらの設定の変更は、次の 3 つを達成するのに役立ちます。

1. [ 在庫をソースに転送 ](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html)：在庫をデフォルト在庫/ソースから新しい在庫/ソースに移動します。

1. [ ソースの一括割り当て ](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html)：すべての製品に新しいソースを追加します。

1. [ 製品属性の一括アップデートを完了 ](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) して、`Allow Store Pickup` 属性と `Allow Home Delivery` 属性を既存の製品に追加します。 ソリューションがインストールされると、属性には最適な *デフォルト* 値が設定されます。 ただし、これらの属性は、一括更新 Content プロセスを完了するまで既存の製品には適用されません。

在庫は、選択したソース（小売店の場所または e コマースウェアハウス）から差し引かれます。 e コマースウェアハウスとして使用するソースは、店舗の集荷場所と同じ在庫に割り当てられ、小売場所の前に優先順位が付けられる必要があります。 詳しくは、[ 在庫のソースの優先順位付け ](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html) を参照してください。

在庫、在庫、ソースの管理について詳しくは、Adobe Commerce ユーザードキュメントを参照してください。

- [ 棚卸資産の管理 ](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [ 在庫数量の管理 ](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [ 株式の管理 ](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [ ソースの管理 ](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [ 在庫の調達先の優先順位付け ](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [ 製品属性の一括アップデート ](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>在庫および在庫ソースの設定を変更すると、統合システムにダウンストリームの影響を与える可能性もあります。 インベントリ設定に対する変更がこれらのシステムに与える影響を理解していることを確認します。
