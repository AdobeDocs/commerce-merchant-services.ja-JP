---
title: コマースデータ取り込み用にプロファイルレコードスキーマを更新
description: コマースプロファイルレコードデータを収集してExperience Platformに送信するスキーマ、データセット、データストリームを作成する方法を説明します。
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# コマースデータ取り込み用にプロファイルレコードスキーマを更新

買い物客がコマースサイトでプロファイルを作成すると、プロファイルレコードが作成され、データが取り込まれます。 プロファイルデータをExperience Platformにストリーミングする前に、そのプロファイルレコードに固有のスキーマとデータセットを作成する必要があります。

1. [作成](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) スキーマを作成し、クラスを **個々のプロファイル**.

1. [追加](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 次のプロファイル固有のフィールドグループ：

   - identityMap
   - 人口統計の詳細
   - 個人の連絡先の詳細
   - ユーザーアカウントの詳細

1. [有効にする](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) プロファイルのスキーマ。

   プロファイルに対してスキーマを有効にすると、このスキーマから作成されたすべてのデータセットがReal-Time CDPに参加し、異なるソースのデータを結合して、各顧客の完全なビューを構築します。

1. [データセットの作成](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 作成または更新したスキーマに基づいて

   データセットは、データの集まり ( 通常、スキーマ（列）とフィールド（行）を含むテーブル ) のストレージと管理の構成体です。 データセットには、保存するデータの様々な側面を記述したメタデータも含まれます。

顧客プロファイルレコードデータ用に設定されたスキーマとデータセットを使用すると、次のことができます。 [設定](connect-data.md#data-collection) コマースインスタンスを使用して、そのデータを収集し、Experience Platformに送信します。

行動イベントデータとバックオフィスイベントデータのスキーマ、データセット、データストリームを作成するには、 [コマースデータ取り込み用の時系列イベントスキーマを更新](update-xdm.md).
