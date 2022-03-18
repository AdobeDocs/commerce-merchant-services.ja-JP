---
title: 注文の支払いステータスレポート
description: 注文の支払ステータスレポートを使用して、注文の支払ステータスを確認し、潜在的な問題を特定します。
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
source-git-commit: cd1c735e9b3be0d75019e0987c84899f9aa66951
workflow-type: tm+mt
source-wordcount: '1184'
ht-degree: 0%

---

# 注文の支払いステータスレポート

[!DNL Payment Services] Adobe CommerceとMagento Open Sourceの場合は、包括的なレポートを使用して、店舗の注文と支払いを明確に把握できます。

![財務レポートビュー](assets/reports-view.png)

注文の支払ステータスレポートは、特定の注文がキャッシュ・プロセス・フローの注文内のどこにあるかを容易に把握するのに役立ちます。 このレポートでは、注文の支払い状況をすばやく確認し、潜在的な問題を特定できます。

複数のビューを開いて、注文と支払いを手動で相互参照する必要はありません。 [!DNL Payment Services] Adobe CommerceとMagento Open Sourceの場合は、注文と支払いの状況を簡単に確認できます。すべて注文の支払い状況レポート内で確認できます。

このレポート内の支払ステータス、請求済みステータスと出荷済みステータス、返金ステータス、係争ステータスなどをすべて管理者で確認します。

既存の会計または注文管理ソフトウェアで使用するために、注文の支払いステータストランザクションを.csv ファイル形式でダウンロードできます。

>[!NOTE]
>
>財務レポートを表示できないのは、 [オンボード済みでアクティブ化されたライブモード](production.md#enable-live-payments) 対象 [!DNL Payment Services].

## レポートで使用されるデータ

この [!DNL Payment Services] モジュールは、注文データを使用し、他のソース（PayPal を含む）からの集計された支払いデータと組み合わせて、意味のある非常に有用なレポートを提供します。

注文データは、支払いサービスでエクスポートおよび保持されます。 次の場合： [注文のステータスを変更または追加する](https://docs.magento.com/user-guide/sales/order-status-custom.html){target=&quot;_blank&quot;} または [ストア表示の編集](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html){target=&quot;_blank&quot;}, [ストア](https://docs.magento.com/user-guide/stores/store-information.html){target=&quot;_blank&quot;} または Web サイト名では、このデータと支払いデータが組み合わされ、注文の支払い状況レポートに組み合わされた情報が入力されます。

このプロセスには、次の 2 つの手順があります。

1. インデックスは、データを変更します `ON SAVE` （注文情報またはストア情報が変更されるたびに）または `BY SCHEDULE` （事前設定された Cron スケジュールに基づく）、 [インデックス管理](https://docs.magento.com/user-guide/system/index-management.html){target=&quot;_blank&quot;}（管理）。

   デフォルトでは、データのインデックス作成がおこなわれます `ON SAVE`：つまり、注文、注文ステータス、ストア表示、ストアまたは Web サイトで何かが変更された場合には、そのたびに再インデックス化処理がおこなわれます。

1. インデックス付きのデータが支払いサービスに送信され、注文の支払いステータスレポートに入力されます。

レポート目的でエクスポートおよび照合されるデータは、注文の支払いステータスレポートで使用されるデータのみです。

>[!NOTE]
>
>この表に示すデータは降順 (`DESC`) デフォルトでは、 `ORDER DATE`. この `ORDER DATE` は、注文が作成された日付のタイムスタンプです。

### データエクスポートの設定

ただし、デフォルトでは、インデックスの再作成は `ON SAVE` モードの場合は、 `BY SCHEDULE` モード。 この `BY SCHEDULE` インデックスは cron スケジュールで 1 分間実行され、変更されたデータはデータの変更から 2 分以内に注文ステータスレポートに表示されます。 このスケジュールされたインデックス再作成により、（各注文がおこなわれるのではなく）スケジュールに基づいて発生するので、特に大量の受信注文がある場合に、ストアの負担を軽減できます。

インデックスモードを変更できます。`ON SAVE` または `BY SCHEDULE`—[管理者](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target=&quot;_blank&quot;}。

データエクスポートを設定する方法については、 [コマンドライン設定](configure-cli.md#configure-data-export).

## 使用可否

の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Order payment status]** をクリックして、注文の支払いステータスを確認します。

![管理者での注文の支払いステータス](assets/order-payment-status-report.png)

## データソースを選択

注文の支払いステータスレポートビューで、データソースを選択できます。_[!UICONTROL Live]_または_[!UICONTROL Sandbox]_ — レポートの結果を表示する対象です。

![データソースの選択](assets/datasource.png)

If _[!UICONTROL Live]_が選択されたデータソースの場合は、 [!DNL Payment Services] in_[!UICONTROL Live]_ モード。 If [!UICONTROL Sandbox]選択したデータソースは_です。サンドボックス環境のレポート情報を表示できます。

データソースの選択は、次のように動作します。

* を使用するストアがない場合は、 [!DNL Payment Services] ライブモードでは、データソースの選択はデフォルトでに設定されます。 [!UICONTROL Sandbox]_.
* を使用するストア（1 つ以上）がある場合 [!DNL Payment Services] ライブモードでは、データソースの選択はデフォルトでに設定されます。 _[!UICONTROL Live]_.
* レポートの書き出しは、常にデータソースの選択に従います。

のデータソースを選択するには、以下を実行します。 [!UICONTROL Order Payment Status] レポート：

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. クリック **[!UICONTROL Data source]** を選択し、 _[!UICONTROL Live]_または [!UICONTROL Sandbox]_.

   レポート結果は、選択したデータソースに基づいて再生成されます。

## 日付の期間をカスタマイズ

注文の支払い状況レポートビューで、特定の日付を選択することで、表示するステータスの期間をカスタマイズできます。 デフォルトでは、30 日間の注文支払いステータスがグリッドに表示されます。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. 次をクリック： **[!UICONTROL Order dates]** カレンダーセレクターフィルター。
1. 適用可能な日付範囲を選択します。
1. グリッドで指定した日付の注文支払ステータスを表示します。

## ステータスの表示

デフォルトでは、30 日間の注文支払いステータスがグリッドに表示されます。

左右にスクロールして表示します [注文の支払い状況情報](#column-descriptions)（受注日、承認日、請求済み、発送済み、支払いステータスなど）。

検索で返された行数、またはデフォルトの 30 日間の注文支払いステータスに表示される行数は、注文日カレンダーセレクターフィルターの横にある注文の支払いステータス表示グリッドの上に表示されます。

## レポートデータを更新

注文の支払いステータスレポートビューには、 _[!UICONTROL Last updated]_レポート情報が最後に更新された時刻を示すタイムスタンプ。 デフォルトでは、注文の支払いステータスレポートデータは、3 時間ごとに自動で更新されます。

注文の支払いステータスレポートデータを手動で更新し、最新のレポート情報を表示することもできます。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. 次をクリック： _更新_ アイコン (![更新アイコン](assets/refresh-button-med.png)) をクリックします。

   注文の支払いステータスレポートデータが更新され、 *[!UICONTROL Update complete]* 確認が表示され、最新の情報がグリッドに表示されます。

## 注文の支払いステータスをダウンロード

デフォルトの 30 日間のステータスを表示しているか、カスタマイズされた期間を表示しているかに関わらず、すべてのステータスを含む.csv ファイルを注文の支払いステータス表示グリッドに表示してダウンロードできます。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. 過去 30 日以外の期間のステータスを表示するには、 [ステータスの日付範囲期間のカスタマイズ](#customize-dates-timeframe).
1. 次をクリック： _ダウンロード_ (![ダウンロードアイコン](assets/icon-download.png)) アイコンをクリックします。

注文の支払いステータスは、.csv 形式でダウンロードされます。

<!-- ## Default order payment status timeframes

These order payment status timeframes are currently available in [!DNL Payment Services].

| Report       | Description          |
| ------------ | -------------------- |
| Yesterday | Available from the Order payment status dates selector, this shows information for the prior date. |
| | Today | Available from the Order payment status dates selector, this shows information for the current day. |
| Last 7 days | Available from the Order payment status dates selector, this shows information for the last seven days. |
| Last 30 days | Available from the Order payment status dates selector and by default in the Order payment statuses view, this shows information for the last 30 days. |
| Last 90 days | Available from the Order payment status dates selector, this shows information for the last 90 days. |
| Year to date | Available from the Order payment status dates selector, this shows information for the the entire year to date. |
| Custom range | Available from the Order payment status dates selector, this can be filtered to show a custom date range. |
-->

## 注文の支払いステータス情報

注文の支払いステータスビューには、グリッドに表示される各ステータスに関する詳細な情報が表示されます。

### 列の説明

注文の支払いステータスレポートには、次の情報が含まれます。

| 列 | 説明 |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | コマース注文 ID<br> <br>関連する [注文情報](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}、ID をクリックします。 |
| [!UICONTROL Order Date] | 注文日のタイムスタンプ |
| [!UICONTROL Authorized Date] | 支払承認の日付タイムスタンプ |
| [!UICONTROL Order Status] | 現在のコマース [注文ステータス](https://docs.magento.com/user-guide/sales/order-status.html){target=&quot;_blank&quot;} |
| [!UICONTROL Invoiced] | 注文の請求書ステータス —*[!UICONTROL No]*, *[!UICONTROL Partial]*&#x200B;または *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | 注文の発送ステータス —*[!UICONTROL No]*, *[!UICONTROL Partial]*&#x200B;または *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | 注文の総計金額 |
| [!UICONTROL Cur] | 注文の通貨タイプ |
| [!UICONTROL Pay Status] | 特定の注文の支払いステータス |
| [!UICONTROL Paid Amt] | 注文で支払われた金額 |
| [!UICONTROL Cur] | 注文で支払われた金額の通貨タイプ |
| [!UICONTROL Refund Status] | 注文の返金のステータス（返品、RMA、クレジット・メモからの情報など）:   *[!UICONTROL Requires refund]*, *[!UICONTROL Refund requested]*, *[!UICONTROL Refunded]*, *[!UICONTROL Refund failed]*&#x200B;または *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | 注文の払い戻し済み金額の合計 |
| [!UICONTROL Cur] | 注文に対して払い戻された金額の通貨タイプ |
| [!UICONTROL Dispute Status] | オーダーに関する紛争のステータス（紛争やチャージバックからの情報）*[!UICONTROL New]*, *[!UICONTROL Representment]*, *[!UICONTROL Accepted]*, *[!UICONTROL Pre-arbitration received]*, *[!UICONTROL Arbitration]*&#x200B;または *[!UICONTROL Arbitration received]* |
| [!UICONTROL Payment Method] | 注文のコマーストランザクションで使用される支払い方法 |
| [!UICONTROL Website] | 注文元の Web サイト |
| [!UICONTROL Store] | 注文が行われた店舗 |
| [!UICONTROL Store View] | 注文がおこなわれたストア表示 |
