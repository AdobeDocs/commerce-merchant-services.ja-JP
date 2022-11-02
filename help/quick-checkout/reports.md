---
title: '"[!DNL Quick Checkout] レポート»'
description: '"[!DNL Quick Checkout] は、包括的なレポート情報を提供します。」'
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# レポート

[!DNL Quick Checkout] Adobe CommerceとMagento Open Sourceの場合は、包括的なレポートを使用して、ストアのチェックアウトエクスペリエンスの統計に関する詳細な情報を取得できます。

![レポート表示](assets/reports-view-big-checkout.png)

>[!WARNING]
>
> 有効にする必要があります [**チェックアウトの追跡**](../quick-checkout/settings-quick-checkout.md) を使用して、Adobe Commerceがチェックアウト情報を Bolt と共有できるようにすることをお勧めします。 デフォルトでは、この設定オプションはに設定されています。 **はい**. このオプションが無効な場合 ( **いいえ**) が含まれる場合、レポートは影響を受けます。

## 概要レポート

「概要」セクションのグラフには、平均チェックアウト時間、チェックアウト中またはチェックアウト中断中に作成された新規アカウントなど、ストアのチェックアウトパフォーマンスに関する詳細情報が表示されます。

![レポートの概要](assets/overview-report-checkout.png)

| グラフ | 説明 |
|---|---|
| [!UICONTROL Checkout abandonment] | 購入を完了せずにチェックアウトプロセスを終了した訪問者の割合。 |
| [!UICONTROL Checkout abandonment breakdown] | チェックアウトの中断を訪問者のタイプで割ります。 オプション： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Average checkout time] | 訪問者がチェックアウトプロセスを完了するまでの平均時間。 |
| [!UICONTROL Average checkout time breakdown] | 平均チェックアウト時間を訪問者のタイプで割った値です。 オプション： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 注文を訪問者のタイプで割った値です。 オプション： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |

## トレンドレポート

「トレンド」セクションのグラフには、アカウントタイプ別にフィルターされたチェックアウトエクスペリエンスのトレンド、またはチェックアウト時に作成された新しいアカウントが表示されます。

![レポートのトレンド](assets/trends-report-checkout.png)

| グラフ | 説明 |
|---|---|
| [!UICONTROL Checkout abandonment by account type] | チェックアウトの中断の傾向を訪問者のタイプで割った値です。 オプション： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 注文件数のトレンドを訪問者のタイプで割った値です。 オプション： [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL New accounts on your store] | ストアトレンドの新しいアカウント。 |

## データをフィルター

日付別に表示される結果や、既存のプリセット ( **過去 30 日間**.

![フィルター表示](assets/filter-view.png)

| フィールド | 説明 |
|---|---|
| [!UICONTROL Preset] | 特定の範囲のデータを表示するために使用できるデフォルトのプリセットを表示するドロップダウン。 デフォルトでは：過去 30 日間 |
| [!UICONTROL Date range] | 選択した日付に応じて特定の範囲のデータを選択できるドロップダウン。 |

