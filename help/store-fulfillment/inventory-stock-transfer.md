---
title: Inventory management Source Transfer
description: 「 [!DNL Store Fulfillment solution] Adobe Commerce Inventory managementと 新しい在庫を設定し、在庫をデフォルトの在庫から移動します。これにより、店舗フルフィルメントソリューションで必要な受け取り機能を有効にするように設定されたソースに割り当てることができます。
role: User, Admin
level: Intermediate
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---


# Inventory management Source Transfer

この [!DNL Store Fulfillment] ソリューションはネイティブのAdobe Commerce Inventory managementを使用します。 デフォルトでは、 [!DNL Commerce] 設定により、すべての web インベントリがデフォルトの在庫に割り当てられ、追加のソースを割り当てることはできません。 Web サイトには 1 つの在庫しか割り当てられないので、マーチャントは新しい在庫を設定し、必要に応じて、適切な範囲に割り当てられたソースにデフォルトの在庫を転送する必要があります。 その後、新しい在庫にソースを割り当てることができます。

これらの設定の変更は、次の 3 つのことを実現するのに役立ちます。

1. [在庫をソースに転送](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) ：デフォルトの在庫/ソースから新しい在庫/ソースに在庫を移動します。

1. [ソースの一括割り当て](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) をクリックして、すべての製品の新しいソースを追加します。

1. [製品属性の一括更新の完了](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) を追加します。 `Allow Store Pickup` および `Allow Home Delivery` 既存の製品の属性。 ソリューションがインストールされると、属性は最適な *デフォルト* 値。 ただし、一括更新プロセスが完了するまで、これらの属性は既存の製品に適用されません。

在庫は、選択したソース（小売店の場所または e コマースウェアハウス）から差し引かれます。 e コマース倉庫として使用するソースは、店舗の受取場所と同じ在庫に割り当て、小売場所の前に優先順位付けする必要があります。 詳しくは、 [在庫のソースの優先順位付け](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).

在庫、在庫、ソースの管理について詳しくは、次のAdobe Commerceユーザードキュメントを参照してください。

- [在庫の管理](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [在庫数量の管理](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [在庫の管理](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [ソースの管理](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [在庫のソースの優先順位付け](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [製品属性の一括更新](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>在庫および在庫ソースの設定を変更すると、統合システムに下流の影響を与える可能性もあります。 インベントリ設定の変更がこれらのシステムに与える影響を理解しておく必要があります。
