---
title: トランザクションレポート
description: 取引レポートを使用して、取引承認レートと取引トレンドを表示します。
role: User
level: Intermediate
exl-id: dd1d80f9-5983-4181-91aa-971522eb56fa
source-git-commit: 9f0381546a98a8a5d72394adbd3ddd49daf539cb
workflow-type: tm+mt
source-wordcount: '1264'
ht-degree: 0%

---

# トランザクションレポート

[!DNL Payment Services] （用） [!DNL Adobe Commerce] および [!DNL Magento Open Source] では、店舗の取引、注文、支払いを明確に把握できる包括的なレポートを提供します。

![トランザクションレポート](assets/transactions-report.png){width="700" zoomable="yes"}

トランザクションレポートでは、トランザクションの承認レートとマイナスのトランザクショントレンドを可視化できるため、店舗の状態を効果的に監視し、トランザクションの問題を事前に特定して対処できます。

ストアフロントで注文された注文とその支払い方法、結果、支払い応答コードなどの個々のトランザクションを参照してください。

トランザクションレポートに表示される情報は、マーチャントでの使用のみを目的としています。 この情報を顧客やその他の潜在的な詐欺師と共有しないでください。 トランザクション情報は、セキュリティチェックを回避したり、チャージバックにつながる注文を行うために使用できます。

取引レポートは.csv ファイル形式でダウンロードでき、既存の会計ソフトウェアや受注管理ソフトウェアで使用できます。

>[!NOTE]
>
>財務報告書を表示する必要はありません [オンボードおよびアクティブ化されたライブモード](production.md#enable-live-payments) （用） [!DNL Payment Services].

## トランザクションレポートの表示

取引レポート・ビューは、Payment Services の「取引」ビューで使用できます。 ストアのトランザクションに関して使用可能なすべての情報が含まれます。

日 _Admin_ サイドバー、に移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**表形式の詳細な「取引」レポート表示を表示します。

![トランザクションレポートの表示](assets/transactions-report-view.png){width="600" zoomable="yes"}

このトピックのセクションに従って、表示するデータを最も適切に表示するように、このビューを設定できます。

このレポート内のリンクされたCommerceの注文とプロバイダーの取引 ID、取引額、1 取引あたりの支払い方法などを参照してください。

すべての支払い方法が同じ精度の情報を提供するわけではありません。 例えば、クレジットカードの取引では、応答、AVS および CCV コードが提供され、取引レポートではカードの最後の 4 桁が提供されますが、PayPal の支払いボタンは提供されません。

次のことができます [トランザクションをダウンロード](#download-transactions) 既存の会計ソフトウェアまたは受注管理ソフトウェアで使用する.csv ファイル形式。

>[!WARNING]
>
> トランザクション レポートには、外部で作成されたキャプチャは含まれません [!DNL Payment Services].

### データソースを選択

トランザクションレポートの表示で、データソースを選択できます。**[!UICONTROL Live]** または **[!UICONTROL Sandbox]**- レポート結果を表示します。

![データソースの選択](assets/datasource.png){width="300" zoomable="yes"}

次の場合 _[!UICONTROL Live]_は選択したデータソースです。を使用しているストアのレポート情報を表示できます [!DNL Payment Services] 実稼動モードの場合。 次の場合_[!UICONTROL Sandbox]_ は選択したデータソースです。サンドボックスモードのレポート情報を表示できます。

データソースを選択すると、次のように機能します。

* を使用するストアがない場合 [!DNL Payment Services] 実稼動モードでは、データソースはデフォルトでに選択されます。 _[!UICONTROL Sandbox]_.
* を使用するストア（1 つまたは複数）がある場合 [!DNL Payment Services] 実稼動モードでは、データソースはデフォルトでに選択されます。 _[!UICONTROL Live]_.
* レポートの書き出しでは、常にデータソースの選択に従います。

のデータソースを選択するには [!UICONTROL Transactions] レポート :

1. 日 _Admin_ サイドバー、に移動 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. クリック **[!UICONTROL Data source]** を選択して、 **[!UICONTROL Live]** または **[!UICONTROL Sandbox]**.

   レポート結果は、選択したデータソースに基づいて再生成されます。

### 日付の期間のカスタマイズ

取引レポート表示から、特定の日付を選択して、表示する取引の期間をカスタマイズできます。 デフォルトでは、30 日間のトランザクションがグリッドに表示されます。

1. 日 _Admin_ サイドバー、に移動 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. 「」をクリックします **[!UICONTROL Transaction dates]** カレンダーセレクターフィルター。
1. 該当する日付範囲を選択します。
1. 指定した日付のトランザクションをグリッドに表示します。

### レポート情報をフィルター

取引レポート・ビューで、フィルタ条件を選択して、表示するステータス結果をフィルタできます。

1. 日 _Admin_ サイドバー、に移動 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. 「」をクリックします **[!UICONTROL Filter]** セレクター。
1. を切り替え _[!UICONTROL Transaction Result]_選択した注文取引のレポート結果のみを表示するオプション。
1. 「」を選択します _[!UICONTROL Card Type]_選択したカードタイプのレポート結果を確認します。 支払プロセッサがカード タイプを識別できない場合は、詳細情報を含むツールヒントが表示されます。
1. 「」を選択します _[!UICONTROL Card Brand]_選択したカードブランドのレポート結果を確認します。 支払い処理者がカードブランドを識別できない場合は、詳細情報を含むツールヒントが表示されます。
1. を切り替え _[!UICONTROL Payment Method]_選択した支払方法のみのレポート結果を表示するオプション。
1. を入力 _最小注文金額_ または _最大注文金額_ その受注金額範囲内のレポート結果を表示します。
1. を入力 _[!UICONTROL Order ID]_特定のトランザクションを検索します。
1. を入力 _[!UICONTROL Card Last Four Digits]_特定のクレジットカードまたはデビットカードを検索します。
1. クリック **[!UICONTROL Hide filters]** をクリックしてフィルターを非表示にします。

### 列の表示/非表示

取引レポートには、デフォルトで使用可能なすべての情報列が表示されます。 ただし、レポートに表示する列をカスタマイズすることはできます。

1. 日 _Admin_ サイドバー、に移動 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. 「」をクリックします **[!UICONTROL Column settings]** アイコン ![列設定アイコン](assets/column-settings.png){width="20" zoomable="yes"}.
1. レポートに表示される列をカスタマイズするには、リストの列をチェックまたはチェック解除します。

   取引報告書には、列設定メニューで行った変更が直ちに表示されます。 レポートビューから移動すると、列の環境設定は保存され、有効なままになります。

### レポートデータを更新

トランザクションレポートのビューには、 _[!UICONTROL Last updated]_レポート情報が最後に更新された時刻を示すタイムスタンプ。 デフォルトでは、トランザクションレポートデータは 3 時間ごとに自動更新されます。

また、レポートデータを手動で強制的に更新して、最新のレポート情報を表示することもできます。

1. 日 _Admin_ サイドバー、に移動 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. 「」をクリックします _更新_ アイコン （![更新アイコン](assets/refresh-button-med.png){width="20" zoomable="yes"}）に設定します。

   トランザクションレポートデータが更新され、 *[!UICONTROL Update complete]* 確認メッセージが表示され、最新の情報がグリッドに表示されます。

### トランザクションをダウンロード

デフォルトの 30 日間のトランザクションを表示している場合でも、カスタマイズされた期間を表示している場合でも、すべてのトランザクションがトランザクションビューグリッドに表示されている.csv ファイルをダウンロードできます。

1. 日 _Admin_ サイドバー、に移動 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Transactions]**.
1. 過去 30 日以外の期間のトランザクションを表示する場合は、 [ステータスの日付範囲の期間のカスタマイズ](#customize-dates-timeframe).
1. 「」をクリックします _Download_ ![ダウンロードアイコン](assets/icon-download.png){width="20" zoomable="yes"} アイコン。

トランザクションは.csv 形式でダウンロードされます。

### 列の説明

取引レポートには次の情報が含まれます。

| 列 | 説明 |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | Commerce注文 ID （成功した取引の値のみを含み、却下された取引の値は空です）<br> <br>関連情報を確認する [オーダー情報](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}「ID」をクリックします。 |
| [!UICONTROL Provider Transaction ID] | 支払いプロバイダーから提供されたトランザクション ID。成功したトランザクションの値のみを含み、却下されたトランザクションのダッシュを含みます。 |
| [!UICONTROL Customer ID] | 注文のCommerce顧客 ID<br> <br>参照： [顧客情報](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customer-accounts/account-create){target="_blank"} を参照してください。 |
| [!UICONTROL Transaction Date] | トランザクション日タイムスタンプ |
| [!UICONTROL Payment Method] | ブランドとカードタイプに関する詳細情報を使用したトランザクションの支払い方法。 参照： [カードタイプ](https://developer.paypal.com/docs/api/orders/v2/#definition-card_type) 詳細情報。支払いサービス バージョン 1.6.0 以降で使用可能です。 |
| [!UICONTROL Card Last Four Digits] | 取引に使用するクレジット カードまたはデビット カードの最後の 4 桁 |
| [!UICONTROL Result] | トランザクションの結果 – *[!UICONTROL OK]* （取引の成立）、 *[!UICONTROL Rejected by Payment Provider]* （PayPal により却下）、 *[!UICONTROL Rejected by Bank]* （カードを発行した銀行により拒否） |
| [!UICONTROL Response Code] | 支払プロバイダまたは銀行から拒否の理由を提供するエラーコード。次の可能性のある応答コードと説明の一覧を参照してください： [`Rejected by Bank` ステータス](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) および [`Rejected by Payment Provider` ステータス](https://developer.paypal.com/api/rest/reference/orders/v2/errors/). |
| [!UICONTROL AVS Code] | 住所確認サービスコード。支払いリクエストに対するプロセッサー応答情報です。 参照： [使用可能なコードと説明のリスト](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) を参照してください。 |
| [!UICONTROL CVV Code] | クレジット・カードとデビット・カードのカード検証値コード。次を参照してください [使用可能なコードと説明のリスト](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) を参照してください。 |
| [!UICONTROL Amount] | トランザクションの注文金額 |
| [!UICONTROL Currency] | トランザクションでの注文に使用する通貨 |
| [!UICONTROL Type] | [支払いアクション](../payment-services/production.md#set-payment-services-as-payment-method) トランザクションの場合 – `Authorize` または `Authorize and Capture` |

### エラー応答コード

この _応答コード_ 列には、トランザクションに関連する特定のエラーまたは成功コードが表示されます。 表示される一般的なエラーコードを次に示します。

* `PAYMENT_DENIED` – 不正の疑いがあり、PayPal から拒否されました。
* `INTERNAL_SERVER_ERROR` – トランザクションが PayPal によって却下され、PayPal サーバーエラーが発生しました。 トランザクションは再試行できます。
* `INSTRUMENT_DECLINED` – お客様は、選択されたお支払い方法ごとに PayPal によって拒否されました。 トランザクションは、別の支払い方法で再試行できます。
* `9500` – 不正の疑いで、関係銀行から取引を断られたこともあったんですね。
* `5120` – お客様の支払い資金が足りず、関係銀行から引き落とされました。
* `5650` – 強い顧客認証を求める銀行に対して、関係銀行がトランザクションを拒否しました（[3DS](security.md#3ds)）に設定します。

失敗したトランザクションの詳細なエラー応答コードは、2023 年 6 月 1 日（PT）以降のトランザクションで使用できます。 2023 年 6 月 1 日（PT）より前に発生した取引については、部分的なレポートデータが表示されます。
