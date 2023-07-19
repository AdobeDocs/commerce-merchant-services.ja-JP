---
title: XDM スキーマへのフィールドグループの追加
description: XDM スキーマにAdobe Commerce固有のフィールドグループを追加する方法を説明します。
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 1d8609a607e0bcb74fdef47fb8e4e582085836e2
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# XDM スキーマへのフィールドグループの追加

いずれかの [オンボーディング手順](overview.md#onboarding-steps) Experience Platformコネクタを使用するには、datastream workspace にアクセスし、 [データストリームの作成](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) Adobe Commerceに固有の そのデータストリームを作成する場合は、取り込む予定のデータを表す XDM スキーマも選択する必要があります。 このトピックでは、Adobe Commerceストアフロントで提供されるデータを正しく収集するために XDM スキーマに含める必要があるフィールドグループについて説明します [イベント](events.md).

1. XDM スキーマをまだ持っていない場合は、 [作成](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 1 つ。 それ以外の場合は、 [編集](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) Adobe Experience Platform UI の既存の XDM スキーマ

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

   XDM スキーマにコマース固有のフィールドグループが含まれ、コマースストアフロントから収集されたデータが生成されます [イベント](events.md) は XDM で表されます。

1. [データセットの作成](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 作成または更新したスキーマに基づいて

   データセットは、スキーマ（列）とフィールド（行）を含むテーブルなど、データの集まりのストレージと管理の構成体です。 データセットには、保存するデータの様々な側面を記述したメタデータも含まれます。

1. [データストリームの作成](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) をクリックし、コマース固有のフィールドグループと対応するデータセットを含む XDM スキーマを選択します。

   データストリームは、収集したデータをデータセットに転送します。 データは、選択したスキーマに基づいて、データセット内に表されます。
