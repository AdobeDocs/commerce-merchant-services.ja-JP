---
title: コマースデータのタイプ
description: 収集してExperience Platformに送信できるデータのタイプについて説明します。
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: d5824e11b4961b518e35fcf56ff2c7ee00480617
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# コマースデータのタイプ

The [データ接続拡張機能](overview.md) は、コマースデータをExperience Platformに接続します。 Experience Platformでの使用を意図したデータは、2 つの動作タイプ（時系列データ、に属する）にグループ化されます **エクスペリエンスイベント** クラスおよびレコードデータ ( **個々のプロファイル** クラス。

詳細情報： [データ動作](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#data-behaviors) および [クラス](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#class) Experience Platform。

## 時系列データ

時系列データは、レコードの主体によって直接または間接的にアクションが実行された時点のシステムのスナップショットを提供します。 例えば、買い物客がサイト上の製品を閲覧し、買い物かごに製品を追加したり、注文したりする場合などです。 時系列データは、クラスがに設定されたExperience Platformを使用してスキーマに取り込まれます。 **エクスペリエンスイベント**.

### 取り込まれた時系列データ

詳しくは、 [行動イベント](events.md) および [バックオフィスイベント](events-backoffice.md) 時系列イベントが生成されたときに取り込まれるデータを確認する。

### 時系列イベントデータの取り込みに必要なスキーマ

方法を学ぶ [スキーマの作成](update-xdm.md) 行動とバックオフィスの時系列のイベントデータを取り込むことができます。

## レコードデータ

>[!NOTE]
>
>この機能はベータ版です。 ベータ版プログラムに参加したい場合は、にリクエストを送信してください。 [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

レコードデータは、主体の属性に関する情報を提供します。 主体は、組織または個人にすることができます。 例えば、サイトの買い物客がアカウントを作成し、そのアカウントがレコードデータを生成したとします。 このデータは、クラスがに設定されたExperience Platformを使用してスキーマに取り込まれます。 **個々のプロファイル**. そのレコードデータは、Adobeのプロファイル管理およびセグメント化サービスに送信できます。 [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html).

### キャプチャされたプロファイルレコードデータ

詳しくは、 [顧客プロファイルレコードデータ](events-profilerecord.md) を使用すると、プロファイルレコードの生成時に取り込まれるデータを確認できます。

### プロファイルレコードデータの取り込みに必要なスキーマ

方法を学ぶ [スキーマの作成](profile-data.md) プロファイルレコードデータを取り込むことができます。
