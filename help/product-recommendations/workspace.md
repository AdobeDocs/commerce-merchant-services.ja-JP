---
title: '''[!DNL Product Recommendations] ワークスペース`'
description: 製品レコメンデーションのパフォーマンスを設定、管理および監視する方法について説明します。
exl-id: 85a06cc3-91b9-484a-96a9-fc85718e6d70
source-git-commit: 25d5321b6f29bab5d8cf329170f3644f35100438
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# [!DNL Product Recommendations] Workspace

The [!DNL Product Recommendations] workspace には、以前に設定したレコメンデーションのリストと、各レコメンデーションの成功を追跡するのに役立つ指標が表示されます。 リストは、最終日、週または月の指標を計算するように設定できます。 指標を使用して、レコメンデーションユニットの表示やクリックの頻度に基づいて実用的なインサイトを作成したり、レコメンデーションのパフォーマンスを分析したりできます。

![Recommendations workspace](assets/workspace.png)
_Recommendations Workspace_

## 範囲の設定

最初は [範囲](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) の値は、すべてのレコメンデーション設定で `Default Store View`. コマースインストールに複数のストア表示が含まれる場合は、 **範囲** から [ストア表示](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) レコメンデーションが適用される場所。

## 指標の日付範囲の設定

1. 次をクリック： **カレンダー** ![カレンダーセレクター](assets/icon-calendar.png) コントロール。

1. 次のいずれかを選択します。

   - 過去 24 時間
   - 過去 7 日間
   - 過去 30 日間

   指標列の計算値は、現在の日付範囲を反映して変化します。

## 列を表示/非表示

1. 左上隅で、 **表示/非表示** ![列セレクター](assets/icon-show-hide-columns.png) 列。

   表示される列には青いチェックマークが付きます。

1. メニューで、次のいずれかの操作を行います。

   - 非表示の列を表示するには、チェックマークの付いていない任意の列名をクリックします。
   - 表示される列を非表示にするには、チェックマークの付いた任意の列名をクリックします。

   テーブルが更新され、選択した列のみが含まれます。

   ![Recommendations workspace](assets/workspace-select-columns.png)
   _列を表示/非表示_

## 設定

この設定は、recommendation-behavioral データを提供する SaaS データ空間を決定します。

- recommendation-behavioral データの送信元を変更するには、別の SaaS データスペースを選択します。

- 新しい SaaS データ領域を設定するには、 **設定を編集**. 詳しくは、 [設定](settings.md).

![Recommendations設定](assets/settings.png)
_Recommendations Settings_

## 詳細を表示

1. 表で、確認するレコメンデーションをクリックします。

   ![Recommendations workspace](assets/recommendation-detail.png)
   _ホームページコンバージョン率の詳細_

1. レコメンデーションのステータスを変更するには、 **有効化** または **非アクティブ化**.

## レコメンデーションを編集

レコメンデーションの詳細ページで、「 **編集**. 詳しくは、 [Recommendationsを編集](edit.md).

## レコメンデーションの作成

レコメンデーションの詳細ページで、「 **作成**. 詳しくは、 [Recommendationsを作成](create.md).

## Workspace のコントロール

| 制御 | 説明 |
|---|---|
| ![カレンダーセレクター](assets/icon-calendar.png) | 指標の計算に使用する時間範囲を決定します。 オプション： 24 時間/ 7 日/ 30 日 |
| ![列セレクター](assets/icon-show-hide-columns.png) | に表示される列を決定します。 [!DNL Product Recommendations] 表。 |
| 設定 | recommendation-behavioral データを取得する SaaS データ空間を決定し、視覚的類似性レコメンデーションタイプも有効にします。 |
| レコメンデーションを作成 | を開きます。 [新しいレコメンデーションを作成](create.md) ページに貼り付けます。 |

## 列の説明

| 列 | 説明 |
|---|---|
| 名前 | レコメンデーションの名前。 |
| ページ | レコメンデーションが表示されるページ。 |
| タイプ | レコメンデーションタイプ。 |
| ステータス | レコメンデーションのステータス。 オプション：非アクティブ/アクティブ/ドラフト |
| 作成済み | レコメンデーションが作成された日付。 |
| 最終編集日 | レコメンデーションが最後に編集された日付。 |
| Impressions | レコメンデーションユニットがページに読み込まれ、レンダリングされた回数。 ブラウザーのビューポートの下にあるレコメンデーション単位は、ページ上にレンダリングされますが、買い物客は表示しません。 この場合、レンダリングされた単位はインプレッションとしてカウントされますが、ユーザが単位を表示にスクロールした場合にのみ、ビューがカウントされます。 |
| vImpressions | （表示可能なインプレッション）少なくとも 1 つのビューを登録するレコメンデーション単位の数。 |
| 件数 | 買い物客のブラウザーのビューポートに表示されるレコメンデーション単位の数。 このイベントは、1 つのページで複数回実行できます。 |
| クリック数 | 買い物客がレコメンデーション単位で品目をクリックした回数と、買い物客が **買い物かごに追加** レコメンデーションユニットのボタン |
| 売上高 | 現在の時間範囲のレコメンデーションによって引き起こされる売上高。 |
| Lt 収益 | （全期間売上高）レコメンデーションによって駆動される全期間売上高。 |
| 視認性 | ビューに登録するレコメンデーション単位の割合。 |
| Ctr | （クリックスルー率）クリックを登録するレコメンデーションの単位インプレッションの割合。 |
| vCtr | （表示可能なクリックスルー率）クリックを登録したレコメンデーションユニットに対する表示可能なインプレッションの割合。 |
