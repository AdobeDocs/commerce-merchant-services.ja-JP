---
title: ストアの場所とマッピングシステムの構成
description: ストアフロント UI でストアの場所のマッピングをサポートするように距離プロバイダーを設定します。 店舗フルフィルメントソリューションでは、小売店舗の検索と、エンドツーエンドのフルフィルメントワークフローのその他のマッピングおよびスケジュール機能を有効にする距離プロバイダが必要です。
role: Admin
level: Intermediate
feature: Shipping/Delivery, Integration, Tools and External Services, Configuration
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# ストアの場所とマッピングの設定

ストアの場所と、ストアのフルフィルメントのマッピング機能を有効にするには、 [距離プロバイダー](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) をクリックして、小売店舗の場所を検索します。

**要件**

設定プロセス中に、Google Maps プラットフォーム用のGoogle API キーを指定します。 お持ちでない場合は、 [Google Maps プラットフォームから生成](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

距離プロバイダを設定するには：

1. 次の **[!UICONTROL Stores > General]** 管理者の設定で、「マップ」コンテンツタイプにGoogle Maps 統合を追加します。

   - に移動します。 **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - Google API キーを **[!UICONTROL Google Maps API Key]** フィールドに入力します。

1. 次の **[!UICONTROL Stores > Inventory]** 「管理」で、「ストアフルフィルメント」の距離プロバイダを選択します。

   - に移動します。 **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - を展開します。 **[!UICONTROL Distance Provider for Distance Based SSA]** 」セクションに入力します。

   - を **プロバイダー** から **Google Map**.

1. 次の項目の設定を行います： **[!UICONTROL Google Distance Provider]**.

   - を **Google API キー**.

   - 設定 **[!UICONTROL Computation Mode]** から `Driving` および **[!UICONTROL Value]** から `Distance`
