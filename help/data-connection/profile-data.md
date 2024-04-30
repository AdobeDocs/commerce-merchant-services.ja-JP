---
title: Commerce データ取り込み用のプロファイルレコードスキーマの更新
description: スキーマ、データセット、データストリームを作成して、Commerce プロファイルレコードデータを収集し、Experience Platformに送信する方法を説明します。
role: Admin, Developer
feature: Personalization, Integration
exl-id: 86a3ba12-7f26-4f7e-98a0-9af0d1d8d881
source-git-commit: 813be62b366b1c76a2b909079cfba31ef8000617
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Commerce データ取り込み（ベータ版）用のプロファイルレコードスキーマの更新

買い物客がCommerce サイトでプロファイルを作成すると、プロファイルレコードが作成され、データが取り込まれます。 そのプロファイルデータをExperience Platformにストリーミングするには、そのプロファイルレコードに固有のスキーマとデータセットを作成する必要があります。

1. [作成](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) スキーマし、クラスをに設定します **個人プロファイル**.

1. [追加](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) 次のプロファイル固有のフィールドグループ：

   - identityMap
   - 人口統計の詳細
   - 個人の連絡先の詳細
   - ユーザーアカウントの詳細

1. [Enable （有効）](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) プロファイルのスキーマ。

   スキーマがプロファイルで有効になっている場合、このスキーマから作成されたデータセットは、異なるソースのデータを結合して各顧客の全体像を構築するReal-Time CDPに関与します。

1. [データセットの作成](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform) 作成または更新したスキーマに基づいています。

   データセットは、データのコレクションのためのストレージおよび管理用の構成体で、通常は、スキーマ（列）とフィールド（行）を含むテーブルです。 データセットには、保存するデータの様々な側面を記述したメタデータも含まれます。

1. を作成 [カスタム名前空間](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces#create-namespaces) 次の値とExperience Platformします。

   - **表示名**: _Commerce顧客 ID_
   - **ID シンボル**: _顧客 ID_
   - **タイプ**: _個々のクロスデバイス ID_

   ![カスタム名前空間の作成](assets/custom-namespace.png){width="700" zoomable="yes"}

   クリック **[!UICONTROL Create]**. カスタム名前空間は、プロファイルフラグメントをステッチして結合するために、統合プロファイルサービスで使用されます。

顧客プロファイルレコードデータ用に設定されたスキーマ、データセット、カスタムネームスペースを使用すると、次のことができます [設定](connect-data.md#data-collection) そのデータを収集してExperience Platformに送信するCommerce インスタンス。

行動およびバックオフィスイベントデータのスキーマ、データセット、データストリームを作成するには、を参照してください。 [Commerce データ取り込みの時系列イベントスキーマの更新](update-xdm.md).
