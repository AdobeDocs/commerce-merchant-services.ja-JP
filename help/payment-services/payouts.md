---
title: ペイアウトレポート
description: 支払額、処理済数量および財務調整の取引レベルに関する詳細なレポートに対する完全な透明性を得るには、「支払」レポートを使用します。
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
source-git-commit: aff1a43fedab473b84d02068a7d3fbd33b4fe093
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 0%

---

# ペイアウトレポート

[!DNL Payment Services] Adobe CommerceとMagento Open Sourceの場合は、包括的なレポートを使用して、店舗の注文と支払いを明確に把握できます。

![財務レポートビュー](assets/reports-view.png)

ペイアウトレポートは、総合的なペイアウト情報を一目で表示し、支払金額、処理済数量、財務調整のトランザクションレベルに関する詳細なレポートを完全に透明化できます。

注文と支払いを相互に参照したり、アカウントを紐付けするために、複数のダッシュボードまたはビューを開く必要はありません。 [!DNL Payment Services] Adobe CommerceとMagento Open Sourceでは、これらのすべてのアクションを 1 か所（ペイアウトレポート）から実行し、ペイアウトを効率的に表示および管理できます。

管理のペイアウトレポート内で、リンクされたコマース注文およびトランザクション ID、トランザクション金額、トランザクションごとの支払い方法などを確認します。

既存の会計または注文管理ソフトウェアで使用するために、支払トランザクションを.csv ファイル形式でダウンロードできます。

>[!NOTE]
>
>この表に示すデータは降順 (`DESC`) デフォルトでは、 `TRANS DATE`. この `TRANS DATE` は、トランザクションが開始された日時です。

## 使用可否

の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.

![管理での支払トランザクション](assets/payouts-report.png)

## データソースを選択

ペイアウトレポート表示で、データソースを選択できます。_[!UICONTROL Live]_または [!UICONTROL Sandbox]_ — レポートの結果を表示する

![データソースの選択](assets/datasource.png)

If _[!UICONTROL Live]_が選択されたデータソースの場合は、ライブストアのレポート情報を表示できます。 If [!UICONTROL Sandbox]選択したデータソースは_です。サンドボックス環境のレポート情報を表示できます。

データソースの選択は、次のように動作します。

* ライブモードのストアがない場合、データソースの選択はデフォルトでになります。 [!UICONTROL Sandbox]_.
* ライブモードでストア（1 つ以上）がある場合、データソースの選択はデフォルトでになります。 _[!UICONTROL Live]_.
* レポートの書き出しは、常にデータソースの選択に従います。

「受注支払ステータス」レポートのデータ・ソースを選択する手順は、次のとおりです。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. クリック **[!UICONTROL Data source]** を選択し、 _[!UICONTROL Live]_または [!UICONTROL Sandbox]_.

   レポート結果は、選択したデータソースに基づいて再生成されます。

## トランザクションの表示

デフォルトでは、30 日間のトランザクションがグリッドに表示されます。

検索で返された行数、またはデフォルトの 30 日間のトランザクションで表示される行数は、トランザクション日付カレンダーセレクターフィルターの横にあるペイアウト表示グリッドの上に表示されます。

左右にスクロールして表示します [支払トランザクションごとの情報](#column-descriptions) 日次レポート（トランザクション日、参照 ID、請求書番号、支払い方法の詳細を含む）

### トランザクション期間のカスタマイズ

「支払」ビューでは、特定の日付を入力するか、日付選択ツールから日付範囲を選択することで、表示する支払トランザクションの期間をカスタマイズできます。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. 「トランザクション日」カレンダーセレクターフィルターをクリックします。
1. 適用可能な日付範囲を選択します。
1. 指定した日付のグリッドにペイアウトステータスが表示されます。

## トランザクションをダウンロード

ペイアウト表示グリッドに表示されるすべてのトランザクションを含む.csv ファイルをダウンロードできます。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. [トランザクションの日付範囲期間のカスタマイズ](#customize-transactions-timeframe).
1. 次をクリック： _ダウンロード_ (![](assets/icon-download.png)) アイコンをクリックします。

支払トランザクションは.csv 形式でダウンロードされます。

## トランザクション情報

ペイアウトビューには、グリッドに表示される各トランザクションに関する詳細な情報が表示されます。

### 列の説明

支払レポートには次の情報が含まれます。

| 列 | 説明 |
| ------------ | -------------------- |
| [!UICONTROL Provider] | 支払いプロバイダー |
| [!UICONTROL Provider trans] | トランザクション ID |
| [!UICONTROL Trans date] | トランザクションが開始された日時 |
| [!UICONTROL Type] | トランザクションタイプ —*[!UICONTROL PAYMENT]*, *[!UICONTROL AUTH]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br>詳しくは、 [トランザクションタイプ](#transaction-types) を参照してください。 |
| [!UICONTROL Status] | トランザクションの現在のステータス —*[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | クレジット (*CR*) または借方 (*DR*) |
| [!UICONTROL Reference ID] | このイベントが関連する元のトランザクション ID |
| [!UICONTROL Invoice] | トランザクションの請求書 ID （注文ごとに 1 つ） |
| [!UICONTROL Commerce order] | コマース注文 ID <br> <br>関連する [注文情報](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}、ID をクリックします。 |
| [!UICONTROL Commerce trans] | コマーストランザクション ID <br> <br>関連する [トランザクション情報](https://docs.magento.com/user-guide/sales/transactions.html){target=&quot;_blank&quot;}、ID をクリックします。 |
| [!UICONTROL Pay method] | クレジットカードのタイプ —*[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL CREDIT_CARD]* — および関連するカードプロバイダー ( *ビザ* または *MasterCard*) |
| [!UICONTROL Trans amt] | トランザクションの金額 |
| [!UICONTROL Cur] | トランザクション金額の通貨単位 |
| [!UICONTROL Pending] | 未払金額 |
| [!UICONTROL Cur] | 保留中の金額の通貨単位 |
| [!UICONTROL Seller amt] | 顧客に対して、または顧客から移動した資金の額 <br> <br>売り手のアカウントから移動した資金には、ダッシュ (-) プレフィックスが表示されます。 |
| [!UICONTROL Cur] | 販売者金額の通貨単位 |
| [!UICONTROL Partner fee] | トランザクションに関連するパートナーの手数料 <br> <br>パートナー手数料アカウントから移動した資金には、ダッシュ (-) プレフィックスが表示されます。 |
| [!UICONTROL Cur] | パートナー手数料の通貨単位 |
| [!UICONTROL Prov fees] | トランザクションに関連する手数料 <br> <br>プロバイダーの手数料アカウントから移動した資金には、ダッシュ (-) プレフィックスが表示されます。 |
| [!UICONTROL Cur] | プロバイダー手数料の通貨単位 |
| [!UICONTROL Fee %] | 手数料として請求されたトランザクション金額の割合 |
| [!UICONTROL Fixed fee] | 固定プロバイダー手数料の金額 |
| [!UICONTROL Chbk fee] | トランザクションに関連するチャージバック料金 <br> <br>ダッシュ (-) プレフィックスは、チャージバック料が取り消されたことを示します。 |
| [!UICONTROL Cur] | チャージバック手数料の通貨単位 |
| [!UICONTROL Hold amt] | 保留中または保留から解除された金額 <br> <br>ダッシュ (-) プレフィックスは、保留資金がリリースされていることを示します。 |
| [!UICONTROL Cur] | 保留金額の通貨単位 |
| [!UICONTROL Recoup amt] | リカウプアカウントからリカウントされた金額 <br> <br>リカウントから移動した資金には、ダッシュ (-) プレフィックスが表示されます。 |
| [!UICONTROL Cur] | 回収金額の通貨単位 |

### トランザクションタイプ

これらのトランザクションタイプは、支払トランザクションに記載される場合があります。

| レポート | 説明 |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | 注文に対して買い手と売り手の間で移動されるお金 |
| [!UICONTROL AUTH] | 承認および承認無効トランザクション |
| [!UICONTROL BONUS] | — |
| [!UICONTROL CHARGEBACK] | チャージバック手数料とチャージバック手数料の取り消しトランザクション |
| [!UICONTROL CORRECTION] | — |
| [!UICONTROL CURRENCY_CONVERSION] | — |
| [!UICONTROL DEPOSIT] | — |
| [!UICONTROL DISBURSEMENT] | — |
| [!UICONTROL DISPUTE] | — |
| [!UICONTROL FEES] | パートナー手数料、支払手数料、手数料取消取引 |
| [!UICONTROL HOLD] | — |
| [!UICONTROL HOLD_RELEASE] | — |
| [!UICONTROL INCENTIVES] | — |
| [!UICONTROL OTHERS] | — |
| [!UICONTROL RECOUP] | 銀行口座または損失勘定からの回収 |
| [!UICONTROL REFUND] | — |
| [!UICONTROL REVERSAL] | — |
| [!UICONTROL WITHDRAWAL] | — |
