---
title: XDM スキーマへのフィールドグループの追加
description: XDM スキーマにAdobe Commerce固有のフィールドグループを追加する方法を説明します。
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# XDM スキーマへのフィールドグループの追加

いずれかの [オンボーディング手順](overview.md#onboarding-steps) を使用する場合 [!DNL Data Connection] 拡張機能は、datastream workspace にアクセスし、 [データストリームの作成](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) これはAdobe Commerceに固有です。 そのデータストリームを作成する場合は、取り込む予定のデータを表す XDM スキーマも選択する必要があります。 このトピックでは、Adobe Commerceから提供されるデータを正しく収集するために XDM スキーマに含める必要があるフィールドグループについて説明します [イベント](events.md).

1. XDM スキーマをまだ持っていない場合は、 [作成](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 1 つ。 それ以外の場合は、 [編集](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) Adobe Experience Platform UI の既存の XDM スキーマ。

1. [追加](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 次のコマース固有のフィールドグループ：

   - サイト検索
   - ウェブページにアクセス
   - ユーザーログインプロセス
   - 参照キー
   - 個人の連絡先の詳細
   - コマースの詳細
   - Adobe Analytics ExperienceEvent Commerce(Adobe Analyticsにデータを送信する場合 )
   - ID マップ

   >[!NOTE]
   >
   > コマース固有のフィールドグループを次のように設定しない `Primary identity`. これにより、フィールドが必須として識別され、Experience Platformはすべてのイベントでそのフィールドを想定します。 そのフィールドがない場合、データの取り込みは失敗します。

   XDM スキーマにコマース固有のフィールドグループが含まれ、コマースから収集されたデータが生成されます。 [イベント](events.md) は XDM で表されます。

1. [データセットの作成](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 作成または更新したスキーマに基づいて

   データセットは、スキーマ（列）とフィールド（行）を含むテーブルなど、データの集まりのストレージと管理の構成体です。 データセットには、保存するデータの様々な側面を記述したメタデータも含まれます。

1. [データストリームの作成](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) をクリックし、コマース固有のフィールドグループと対応するデータセットを含む XDM スキーマを選択します。

   データストリームは、収集したデータをデータセットに転送します。 データは、選択したスキーマに基づいて、データセット内に表されます。