---
title: XDM スキーマへのフィールドグループの追加
description: XDM スキーマにAdobe Commerce固有のフィールドグループを追加する方法を説明します。
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
source-git-commit: 06499893f6cad4d920a231f5b22417d3044b2319
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# XDM スキーマへのフィールドグループの追加

いずれかの [前提条件](overview.md#prereqs) Experience Platformコネクタを使用するには、datastream workspace にアクセスし、 [データストリームの作成](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) Adobe Commerceに固有の そのデータストリームを作成する場合は、取り込む予定のデータを表す XDM スキーマも選択する必要があります。 このトピックでは、Adobe Commerceストアフロントで提供されるデータを正しく収集するために XDM スキーマに含める必要があるフィールドグループについて説明します [イベント](events.md).

1. XDM スキーマをまだ持っていない場合は、 [作成](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#create) 1 つ。 それ以外の場合は、 [編集](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#edit) Adobe Experience Platform UI の既存の XDM スキーマ

1. [追加](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#add-field-groups) 次のコマース固有のフィールドグループ：

   - コマース
   - サイト検索
   - ウェブページにアクセス
   - ユーザーログインプロセス
   - 参照キー
   - 個人の連絡先の詳細
   - コマースの詳細
   - Adobe Analytics Experience Event Commerce(Adobe Analyticsにデータを送信する場合 )
   - 人物識別子

   >[!NOTE]
   >
   > コマース固有のフィールドグループを次のように設定しない `Primary identity`. これにより、フィールドが必須として識別され、Experience Platformはすべてのイベントでそのフィールドを想定します。 そのフィールドがない場合、データの取り込みは失敗します。

   XDM スキーマにコマース固有のフィールドグループが含まれ、コマースストアフロントから収集されたデータが生成されます [イベント](events.md) は XDM で表されます。

1. [データストリームの作成](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) をクリックし、コマース固有のフィールドグループを含む XDM スキーマを選択します。
