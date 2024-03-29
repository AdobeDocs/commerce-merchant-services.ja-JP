---
title: ペイアウトレポート
description: 支払額、処理済数量および財務調整の取引レベルに関する詳細なレポートに対する完全な透明性を得るには、「支払」レポートを使用します。
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
feature: Payments, Checkout
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '1310'
ht-degree: 0%

---

# ペイアウトレポート

[!DNL Payment Services] 対象： [!DNL Adobe Commerce] および [!DNL Magento Open Source] は、店舗のトランザクション、注文、支払いを明確に把握できるように、包括的なレポートを提供します。

2 つのペイアウトレポート表示を使用して、すべてのペイアウトに関する詳細情報を確認できます。

* **[ペイアウトのデータビジュアライゼーションビュー](#payouts-data-visualization-view)** — 支払サービスホームで使用可能なグラフ。支払レポートビューから 1 日あたりの集計金額を視覚的に表します。
* **[ペイアウトレポート表示](#payouts-report-view)** — すべてのトランザクションの詳細な支払情報を表示するペイアウトで使用可能なレポート

「支払」ビューには、総合的な支払情報が一目で表示され、支払金額、処理済数量、財務調整のトランザクションレベルに関する詳細なレポートに完全に透明性を持たせることができます。

以下が可能です。 [支払トランザクションのダウンロード](#download-transactions) 既存の会計または注文管理ソフトウェアで使用する.csv ファイル形式。

>[!NOTE]
>
>ペイアウトレポートには、キャプチャされた注文のみが表示されます ( 支払いアクションは [`Authorize and Capture`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method)) — または [次のように指定 `Invoiced`](https://docs.magento.com/user-guide/sales/invoice-create.html).

## ペイアウトのデータビジュアライゼーションビュー

支払データのビジュアライゼーションビューは、支払サービスホームで使用できます。 詳細な表から、1 日あたりの集計された金額を視覚的に表したものです [ペイアウトレポート表示](#payouts-report-view).

次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** を使用すると、時間の経過に伴うクレジットとデビットおよび移動平均のデータ視覚化チャートを確認できます。

![管理者でのデータの視覚化の配分](assets/payouts-report.png){width="800" zoomable="yes"}

クリック **[!UICONTROL View Report]** 詳細な表に移動するには [ペイアウトレポート表示](#payouts-report-view).

### トランザクション期間のカスタマイズ

デフォルトでは、30 日間のトランザクションが表示されます。

ペイアウトデータのビジュアライゼーション表示で、日付範囲を選択して、表示するペイアウトトランザクションの期間をカスタマイズできます。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. ペイアウトデータビジュアライゼーションビューは、「ペイアウト」セクションに表示されます。
1. 次をクリック： **[!UICONTROL Range]** セレクターフィルター。
1. 該当する日付範囲（30 日、15 日、7 日）を選択します。
1. 指定した日付のトランザクション情報を表示します。

### トランザクション情報

選択した日付範囲のトランザクション金額は、ペイアウトのデータビジュアライゼーションビューの左側に表示されます。 選択した日付範囲の日付がビューの下部に表示されます。 特定の日付に支払いがなかった場合、その日付は表示されません。

ペイアウトデータのビジュアライゼーションビューには、次の情報が含まれています。

| データ | 説明 |
| ------------ | -------------------- |
| [!UICONTROL Transaction amount] | 指定した期間のトランザクションの金額範囲。Y 軸のデータ（左） |
| 日付範囲 | 指定した期間の日付範囲。X 軸のデータ（下部） |
| クレジット | 指定した期間の支払い |
| 借方 | 指定した期間のデビット（払い戻し） |
| 移動平均 | 指定した期間の各日付の平均支払額を表します |
| 範囲のネット | 指定した期間（範囲）の純支払額 |

## ペイアウトレポート表示

ペイアウトレポートビューは、支払サービスのペイアウトビューで使用できます。 ストアのペイアウトに関する利用可能な情報がすべて含まれます。

次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**詳細な表形式のペイアウトレポートビューを表示するには、次の手順に従います。

![管理での支払トランザクション](assets/payouts-report-new.png){width="800" zoomable="yes"}

このトピックのセクションごとに、このビューを設定して、表示するデータを最適に表示できます。

このレポート内のリンクされたコマース注文とトランザクション ID、トランザクション金額、トランザクションごとの支払い方法などを確認します。

以下が可能です。 [支払トランザクションのダウンロード](#download-transactions) 既存の会計または注文管理ソフトウェアで使用する.csv ファイル形式。

>[!NOTE]
>
>この表に示すデータは降順 (`DESC`) デフォルトでは、 `TRANS DATE`. The `TRANS DATE` は、トランザクションが開始された日時です。

### データソースを選択

ペイアウトレポート表示で、データソースを選択できます。**[!UICONTROL Live]** または **[!UICONTROL Sandbox]** — レポートの結果を表示する対象です。

![データソースの選択](assets/datasource.png){width="300" zoomable="yes"}

次の場合 _[!UICONTROL Live]_が選択されたデータソースの場合は、実稼働モードでストアのレポート情報を表示できます。 次の場合_[!UICONTROL Sandbox]_ が選択されたデータソースである場合は、サンドボックスモードでレポート情報ストアを表示できます。

データソースの選択は、次のように動作します。

* ライブモードのストアがない場合、データソースの選択はデフォルトでになります。 _[!UICONTROL Sandbox]_.
* ライブモードでストア（1 つ以上）がある場合、データソースの選択はデフォルトでになります。 _[!UICONTROL Live]_.
* レポートの書き出しは、常にデータソースの選択に従います。

「受注支払ステータス」レポートのデータ・ソースを選択する手順は、次のとおりです。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. クリック **[!UICONTROL Data source]** を選択し、 **[!UICONTROL Live]** または **[!UICONTROL Sandbox]**.

   レポート結果は、選択したデータソースに基づいて再生成されます。

### トランザクションの表示

デフォルトでは、30 日間のトランザクションが表示されます。

検索で返された行数、またはデフォルトの 30 日間のトランザクションで表示される行数は、トランザクション日付カレンダーセレクターフィルターの横にあるペイアウト表示グリッドの上に表示されます。

左右にスクロールして表示します [支払トランザクションごとの情報](#column-descriptions) 日次レポート（トランザクション日、参照 ID、請求書番号、支払い方法の詳細を含む）。

#### トランザクション期間のカスタマイズ

ペイアウトレポートビューでは、特定の日付を入力するか、日付選択ツールから日付範囲を選択することで、表示するペイアウトトランザクションの期間をカスタマイズできます。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. 次をクリック： _[!UICONTROL Transaction dates]_カレンダーセレクターフィルター。
1. 適用可能な日付範囲を選択します。
1. 指定した日付のグリッドにペイアウトステータスが表示されます。

### 列の表示と非表示を切り替える

ペイアウトレポートビューには、デフォルトで利用可能な最も多くの情報列が表示されます。 ただし、レポートに表示する列をカスタマイズすることはできます。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. 次をクリック： _列設定_ アイコン (![列設定アイコン](assets/column-settings.png){width="20" zoomable="yes"}) をクリックします。
1. レポートに表示する列をカスタマイズするには、リストの列をオンまたはオフにします。

   ペイアウトレポートビューには、列設定メニューで行った変更がすぐに表示されます。 列の環境設定は保存され、レポート表示から移動しても有効なままになります。

### トランザクションをダウンロード

ペイアウト表示グリッドに表示されるすべてのトランザクションを含む.csv ファイルをダウンロードできます。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. [トランザクションの日付範囲期間のカスタマイズ](#customize-transactions-timeframe).
1. 次をクリック： _ダウンロード_ (![](assets/icon-download.png){width="20" zoomable="yes"}) アイコンをクリックします。

支払トランザクションは.csv 形式でダウンロードされます。

### 列の説明

支払レポートには次の情報が含まれます。

| 列 | 説明 |
| ------------ | -------------------- |
| [!UICONTROL Provider] | 支払いプロバイダー |
| [!UICONTROL Provider trans] | トランザクション ID |
| [!UICONTROL Trans date] | トランザクションが開始された日時 |
| [!UICONTROL Type] | トランザクションタイプ —*[!UICONTROL PAYMENT]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br>詳しくは、 [トランザクションタイプ](#transaction-types) を参照してください。 |
| [!UICONTROL Status] | トランザクションの現在のステータス —*[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | クレジット (*CR*) または借方 (*DR*) |
| [!UICONTROL Reference ID] | このイベントが関連する元のトランザクション ID |
| [!UICONTROL Invoice] | トランザクションの請求書 ID （注文ごとに 1 つ） |
| [!UICONTROL Commerce order] | コマース注文 ID <br> <br>関連する [注文情報](https://docs.magento.com/user-guide/sales/orders.html)、「 ID 」をクリックします。 |
| [!UICONTROL Commerce trans] | コマーストランザクション ID |
| [!UICONTROL Pay method] | クレジットカードのタイプ —*[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL CREDIT_CARD]* — および関連するカードプロバイダー ( *Visa* または *MasterCard*) |
| [!UICONTROL TRANS AMT] | トランザクションの金額 |
| [!UICONTROL CUR] | トランザクション金額の通貨単位 |
| [!UICONTROL PENDING] | 未払金額 |
| [!UICONTROL CUR] | 保留中の金額の通貨単位 |
| [!UICONTROL SELLER AMT] | 顧客に対して、または顧客から移動した資金の額 <br> <br>売り手のアカウントから移動した資金には、ダッシュ (-) プレフィックスが表示されます。 |
| [!UICONTROL CUR] | 販売者金額の通貨単位 |
| [!UICONTROL PARTNER FEE] | トランザクションに関連するパートナーの手数料 <br> <br>パートナー手数料アカウントから移動した資金には、ダッシュ (-) プレフィックスが表示されます。 |
| [!UICONTROL CUR] | パートナー手数料の通貨単位 |
| [!UICONTROL PROV FEES] | トランザクションに関連する手数料 <br> <br>プロバイダーの手数料アカウントから移動した資金には、ダッシュ (-) プレフィックスが表示されます。 |
| [!UICONTROL CUR] | プロバイダー手数料の通貨単位 |
| [!UICONTROL FEE %] | 手数料として請求されたトランザクション金額の割合 |
| [!UICONTROL FIXED FEE] | 固定プロバイダー手数料の金額 |
| [!UICONTROL CHBK FEE] | トランザクションに関連するチャージバック料金 <br> <br>ダッシュ (-) プレフィックスは、チャージバック料が取り消されたことを示します。 |
| [!UICONTROL CUR] | チャージバック手数料の通貨単位 |
| [!UICONTROL HOLD AMT] | 保留中または保留から解除された金額 <br> <br>ダッシュ (-) プレフィックスは、保留資金がリリースされていることを示します。 |
| [!UICONTROL CUR] | 保留金額の通貨単位 |
| [!UICONTROL RECOUP AMT] | リカウプアカウントからリカウントされた金額 <br> <br>リカウントから移動した資金には、ダッシュ (-) プレフィックスが表示されます。 |
| [!UICONTROL CUR] | 回収金額の通貨単位 |

### トランザクションタイプ

これらのトランザクションタイプは、支払トランザクションに記載される場合があります。

| レポート | 説明 |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | 注文に対して買い手と売り手の間で移動されるお金 |
| [!UICONTROL AUTH] | 承認と承認の無効化トランザクション |
| [!UICONTROL BONUS] | — |
| [!UICONTROL CHARGEBACK] | チャージバック手数料とチャージバック手数料の取り消しトランザクション |
| [!UICONTROL CORRECTION] | -- |
| [!UICONTROL CURRENCY_CONVERSION] | -- |
| [!UICONTROL DEPOSIT] | -- |
| [!UICONTROL DISBURSEMENT] | -- |
| [!UICONTROL DISPUTE] | -- |
| [!UICONTROL FEES] | パートナー手数料、支払手数料、手数料取消取引 |
| [!UICONTROL HOLD] | -- |
| [!UICONTROL HOLD_RELEASE] | -- |
| [!UICONTROL INCENTIVES] | -- |
| [!UICONTROL OTHERS] | -- |
| [!UICONTROL RECOUP] | 銀行口座または損失勘定からの回収 |
| [!UICONTROL REFUND] | -- |
| [!UICONTROL REVERSAL] | -- |
| [!UICONTROL WITHDRAWAL] | -- |
