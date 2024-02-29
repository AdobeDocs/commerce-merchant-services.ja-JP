---
title: コマースデータ取り込み用の時系列イベントスキーマの更新
description: コマースデータ取り込み用の時系列イベントデータを収集して送信するスキーマ、データセット、データストリームを作成する方法について説明します。
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 0%

---

# コマースデータ取り込み用の時系列イベントスキーマの更新

いずれかの [オンボーディング手順](overview.md#onboarding-steps) を使用する場合 [!DNL Data Connection] 拡張機能は、datastream workspace にアクセスし、 [データストリームの作成](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) これはAdobe Commerceに固有です。 そのデータストリームを作成する場合は、取り込む予定のデータを記述したスキーマも選択する必要があります。 このスキーマには、コマース固有のフィールドグループを含める必要があります。

この記事では、Adobe Commerceイベントによって提供される次の時系列データを正しく収集するために、スキーマに含める必要があるフィールドグループについて説明します。

- [行動](events.md)  — ストアフロント、プロファイル、検索、B2B イベントが含まれます。
- [バックオフィス](events-backoffice.md)  — 注文ステータスとプロファイルイベントが含まれます。

詳細情報： [時系列データ](data-ingestion.md).

詳しくは、 [スキーマ構成の基本](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html).

## 時系列の行動とバックオフィスのイベントデータでスキーマを更新

この節では、既存のスキーマを更新する方法、または行動とバックオフィスのイベントデータを含むスキーマを作成する方法について説明します。

>[!NOTE]
>
>詳しくは、 [時系列プロファイルイベントデータ](#time-series-profile-event-data) を参照してください。

1. スキーマをまだ持っていない場合は、 [作成](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 1 つは、クラスが **エクスペリエンスイベント**.

1. [追加](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 次のコマース固有のフィールドグループを使用します（または既存のスキーマを編集し、これらのフィールドグループを追加します）。

   - サイト検索
   - ウェブページにアクセス
   - ユーザーログインプロセス
   - 参照キー
   - 個人の連絡先の詳細
   - チャネルの詳細
   - コマースの詳細
   - Adobe Analytics ExperienceEvent Commerce(Adobe Analyticsにデータを送信する場合 )

   >[!NOTE]
   >
   > コマース固有のフィールドグループを次のように設定しない `Primary identity`. これにより、フィールドが必須として識別され、Experience Platformはすべてのイベントでそのフィールドを想定します。 そのフィールドがない場合、データの取り込みは失敗します。

   これで、スキーマにコマース固有のフィールドグループが含まれ、コマースから時系列データが収集されます [行動](events.md) および [バックオフィス](events-backoffice.md) イベントは、スキーマで表されます。

1. [有効にする](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) プロファイルのスキーマ。

   プロファイルに対してスキーマを有効にすると、このスキーマから作成されたすべてのデータセットがReal-Time CDPに参加し、異なるソースのデータを結合して、各顧客の完全なビューを構築します。

1. [データセットの作成](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 作成または更新したスキーマに基づいて

   データセットは、データの集まり ( 通常、スキーマ（列）とフィールド（行）を含むテーブル ) のストレージと管理の構成体です。 データセットには、保存するデータの様々な側面を記述したメタデータも含まれます。

1. [データストリームの作成](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) をクリックし、コマース固有のフィールドグループと、対応するデータセットを含むスキーマを選択します。

   データストリームは、収集したデータをデータセットに転送します。 データは、選択したスキーマに基づいて、データセット内に表されます。

1. **ベータ版** （オプション）カスタムのバックオフィスイベントデータをコマースインスタンスからExperience Platformに渡す場合は、カスタム属性を使用できます。 この機能はベータ版です。 ベータ版プログラムに参加したい場合は、にリクエストを送信してください。 [dataconnection@adobe.com](mailto:dataconnection@adobe.com). リクエストに次を含めます。

   - お使いの [Adobe組織 ID](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255). 例： `organization_id@AdobeOrg`.
   - 注文レベルのカスタム属性のリスト。
   - 注文項目レベルの属性のリスト。

   Adobe Commerceチームから、詳細および次の手順についての連絡が届きます。

行動データとバックオフィスデータ用に設定されたスキーマ、データセット、データストリームを使用すると、次のことが可能になります。 [設定](connect-data.md#data-collection) コマースインスタンスを使用してデータを収集し、Experience Platformに送信します。

買い物客のプロファイル情報を含めるには、次の節を参照してください。

## 時系列プロファイルイベントデータ

時系列プロファイルイベントデータは、次のイベントから生成されます。

- [&#39;accountCreated&#39;](events-backoffice.md#accountcreated)
- [&#39;accountUpdated&#39;](events-backoffice.md#accountupdated)
- [&#39;accountDeleted&#39;](events-backoffice.md#accountdeleted)

顧客のプロファイルイベントデータをExperience Platformに取り込む場合は、既存のコマーススキーマを更新し、設定済みと同じデータストリームを使用するか、プロファイル固有のデータストリームとスキーマを作成します。 この決定は、お客様の会社のデータガバナンスに基づいておこなわれます。 次の 2 つのセクションでは、どちらの場合も説明します。

### 既存のデータストリームを使用して、時系列プロファイルイベントデータをExperience Platformに送信します。

時系列を追加する場合 [サーバーサイドプロファイルイベントデータ](events-backoffice.md#customer-profile-events-server-side) 既存のコマースデータストリームに、 `Demographic Details` フィールドグループをスキーマに追加します。 スキーマに、次のコマース固有のフィールドグループが含まれます。

- サイト検索
- ウェブページにアクセス
- ユーザーログインプロセス
- 参照キー
- 個人の連絡先の詳細
- チャネルの詳細
- コマースの詳細
- Adobe Analytics ExperienceEvent Commerce(Adobe Analyticsにデータを送信する場合 )
- 新規： **人口統計の詳細**

を `Demographic Details` 既存のコマーススキーマのフィールドグループでは、コマーススキーマに既に関連付けられているデータセットとデータストリームが、この時系列プロファイルデータに使用されます。

### 時系列プロファイルイベントデータを別のデータストリームのExperience Platformに送信する

を追加する場合、 [サーバーサイドプロファイルイベントデータ](events-backoffice.md#customer-profile-events-server-side) 新しいプロファイル固有のデータストリームとスキーマに対して、次の手順を実行します。

1. [作成](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) スキーマを作成し、クラスを **エクスペリエンスイベント**.

1. [追加](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 次のプロファイル固有のフィールドグループ：

   - 人口統計の詳細
   - 個人の連絡先の詳細
   - チャネルの詳細
   - コマースの詳細

1. [有効にする](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) プロファイルのスキーマ。

   プロファイルに対してスキーマを有効にすると、このスキーマから作成されたすべてのデータセットがReal-Time CDPに参加し、異なるソースのデータを結合して、各顧客の完全なビューを構築します。

1. [データセットの作成](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 作成したスキーマに基づいて

   データセットは、データの集まり ( 通常、スキーマ（列）とフィールド（行）を含むテーブル ) のストレージと管理の構成体です。 データセットには、保存するデータの様々な側面を記述したメタデータも含まれます。

1. [データストリームの作成](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) をクリックし、コマース固有のフィールドグループと対応するデータセットを含む XDM スキーマを選択します。

   データストリームは、収集したデータをデータセットに転送します。 データは、選択したスキーマに基づいて、データセット内に表されます。

顧客プロファイルデータ用に設定されたスキーマ、データセット、データストリームを使用すると、次のことが可能になります。 [設定](connect-data.md#data-collection) コマースインスタンスを使用して、そのデータを収集し、Experience Platformに送信します。

プロファイルレコードデータのスキーマ、データセット、データストリームを作成するには、 [プロファイルレコードデータをExperience Platformに送信](profile-data.md).
