---
title: コマースデータをAdobe Experience Platformに接続
description: コマースデータをAdobe Experience Platformに接続する方法を説明します。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: dead0b8dae69476c196652abd43c4966a38c4141
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# コマースデータをAdobe Experience Platformに接続

Experience Platformコネクタをインストールすると、 **システム** 下のメニュー **サービス** （コマース内） _管理者_.

- Commerce Services コネクタ
- Experience Platformコネクタ

Adobe Commerceインスタンスを Adobe Experience Platform に接続するには、Commerce Services コネクタから開始し、Experience Platformコネクタで終了するように、両方のコネクタを設定する必要があります。

## Commerce Services コネクタの更新

既にAdobe Commerceサービスをインストールしている場合は、既に Commerce Services コネクタが設定されている可能性があります。 そうでない場合は、 [Commerce Services コネクタ](../landing/saas.md) ページ：

1. Commerce アカウントにログインして、 [実稼動環境とサンドボックス API キーの取得](../landing/saas.md#credentials).
1. を選択します。 [SaaS データ容量](../landing/saas.md#saas-configuration).
1. にAdobeアカウントにログイン [組織 ID の取得](../landing/saas.md#ims-organization-optional).

コマースサービスコネクタを設定した後、Experience Platformコネクタを設定します。

## Experience Platformコネクタの更新

このセクションでは、組織 ID を使用してAdobe CommerceインスタンスをAdobe Experience Platformに接続します。 次に、ストアフロントまたはバックオフィスのデータタイプを指定して、Experience PlatformEdge に送信できます。

![Experience Platformコネクタの設定](assets/epc-config-dc.png)

## 一般

1. でAdobeアカウントにサインイン [Commerce Services コネクタ](../landing/saas.md#organizationid) 組織 ID を選択します。

   >[!NOTE]
   >
   >以前に Commerce Services コネクタを設定している場合は、組織 ID が既に選択されているので、この手順をスキップできます。

1. 管理者で、に移動します。 **システム** /サービス/ **Experience Platformコネクタ**.

1. 内 **範囲** ドロップダウンで、コンテキストを **Web サイト**.

1. 内 **組織 ID** フィールドで、Adobe Experience Platformアカウントに関連付けられている ID を確認します。これは、 [Commerce Services コネクタ](../landing/saas.md#organizationid). 組織 ID はグローバルです。 1 つのAdobe Commerceインスタンスに関連付けることができる組織 ID は 1 つだけです。

1. （オプション）既に [AEP Web SDK（合金）](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) サイトにデプロイし、チェックボックスを有効にして、AEP Web SDK の名前を追加します。 それ以外の場合は、これらのフィールドを空白のままにすると、Experience Platformコネクタによって自動的にデプロイされます。

   >[!NOTE]
   >
   >独自の AEP Web SDK を指定した場合、Experience Platformコネクタは、このページで指定されたデータストリーム ID（存在する場合）ではなく、その SDK に関連付けられたデータストリーム ID を使用します。

## データ収集

内 **データ収集** 「 」セクションで、ストアフロントやバックオフィスのデータを選択して、Experience PlatformEdge に送信します。 Adobe Commerceインスタンスでデータ収集を開始できることを確認するには、 [前提条件](overview.md#prerequisites).

詳しくは、イベントのトピックを参照してください [店頭](events.md#storefront-events) および [バックオフィス](events.md#back-office-events) イベント。

>[!NOTE]
>
>すべてのフィールド ( **データ収集** セクションの適用対象 **Web サイト** 範囲以上。

1. 選択 **ストアフロントイベント** storefront 行動データを送信する場合。

   >[!NOTE]
   >
   >この **ストアフロントイベント** AEP Web SDK および組織 ID が有効な場合、チェックボックスは自動的に有効になります。

1. 選択 **バックオフィスイベント** 注文が発行されたか、取り消されたか、返金されたか、出荷されたかなど、注文ステータス情報を送信する場合。

   >[!NOTE]
   >
   >次を選択した場合、 **バックオフィスイベント**&#x200B;に設定されていない場合、すべてのバックオフィスデータがExperience PlatformEdge に送信されます。 買い物客がデータ収集をオプトアウトする場合は、Experience Platformで買い物客のプライバシー設定を明示的に設定する必要があります。 これは、コレクターが買い物客の環境設定に基づいて既に同意を処理しているストアフロントイベントとは異なります。 [詳細情報](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) Experience Platformでの買い物客のプライバシー設定に関する情報。

1. バックオフィスのイベントデータを、 [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) ジョブの場合、 `Sales Orders Feed` インデックス `Update by Schedule`.

   1. の _管理者_ サイドバー、移動 **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. のチェックボックスをオンにします。 `Sales Orders Feed` インデクサー。

   1. 設定 **[!UICONTROL Actions]** から `Update by Schedule`.

   1. バックオフィスのデータを初めて有効にする場合は、次のコマンドを実行して再インデックスを作成し、再同期をトリガーします。 以降の再同期は、 [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) ジョブが正しく設定されている。

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

1. （独自の AEP Web SDK を使用している場合は、この手順をスキップします）。 [作成](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) Adobe Experience Platformのデータストリーム、または収集に使用する既存のデータストリームを選択します。

1. （独自の AEP Web SDK を使用している場合は、この手順をスキップします）。 内 **データストリーム ID** 「 」フィールドに、新規または既存のデータストリームの ID を貼り付けます。

## フィールドの説明

| フィールド | 説明 |
|--- |--- |
| 範囲 | 設定を適用する特定の Web サイト。 |
| 組織 ID （グローバル） | AdobeDX 製品を購入した組織に属する ID。 この ID は、Adobe CommerceインスタンスをAdobe Experience Platformにリンクします。 |
| AEP Web SDK が既にサイトにデプロイされているか。 | 独自の AEP Web SDK をサイトにデプロイした場合は、このチェックボックスを選択します。 |
| AEP Web SDK 名（グローバル） | 既にサイトにExperience PlatformWeb SDK がデプロイされている場合は、このフィールドにその SDK の名前を指定します。 これにより、Storefront Event Collector および Storefront Event SDK は、Experience PlatformコネクタによってデプロイされたExperience Platformではなく、Web SDK を使用できます。 サイトにExperience PlatformWeb SDK がデプロイされていない場合、このフィールドを空白のままにすると、Experience Platformコネクタがデプロイします。 |
| ストアフロントイベント | 組織 ID とデータストリーム ID が有効である限り、デフォルトでオンになります。 Storefront イベントは、サイトを閲覧する買い物客から匿名化された行動データを収集します。 |
| バックオフィスイベント | オンにすると、イベントペイロードには、注文が発行されたか、キャンセルされたか、返金されたか、発送されたかなど、匿名化された注文ステータス情報が含まれます。 |
| Datastream ID (Website) | Adobe Experience Platformから他のAdobeDX 製品にデータを送信できるようにする ID。 この ID は、特定のAdobe Commerceインスタンス内の特定の Web サイトに関連付ける必要があります。 独自のExperience PlatformWeb SDK を指定する場合は、このフィールドにデータストリーム ID を指定しないでください。 Experience Platformコネクタは、その SDK に関連付けられたデータストリーム ID を使用し、このフィールドで指定されたデータストリーム ID を無視します（存在する場合）。 |

## データがExperience Platformに送信されていることを確認

オンボーディング後、ストアフロントデータがExperience Platformエッジに送られ始めます。 バックオフィスのデータは、オンボーディング後、データがエッジに表示されるまでに約 5 分かかります。 その後の更新は、Cron スケジュールに基づいてエッジで表示されます。

コマースデータがExperience Platformエッジに送信されると、次のようなレポートを作成できます。

![Adobe Experience Platformのコマースデータ](assets/aem-data-1.png)
_Adobe Experience Platformのコマースデータ_
