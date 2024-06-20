---
title: カタログ同期
description: から製品データを書き出す方法を学ぶ [!DNL Commerce] サーバー先 [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: af9de40a717d2cb55a5f42483bd0e4cbcd913f64
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---


# カタログ同期

>[!NOTE]
>
> カタログ同期ダッシュボードが、データ管理ダッシュボードになりました。 この改善されたダッシュボードは、をサポートするようになりました [[!DNL Product Recommendations]](../product-recommendations/guide-overview.md), [[!DNL Live Search]](../live-search/overview.md)、および [[!DNL Catalog Service]](../catalog-service/overview.md). お客様は、これらのサービスのいずれかの最新バージョンに更新することで、データ管理ダッシュボードを取得できます。 詳しくは、を参照してください。 [データ管理ダッシュボード](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) ドキュメント。 この現在のトピックは、まだアップグレードしておらず、カタログ同期ダッシュボードを使用しているユーザー向けです。

Adobe Commerceはインデクサーを使用して、カタログデータをテーブルにコンパイルします。 プロセスは、次のユーザーによって自動的にトリガーされます [イベント](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) 製品価格や在庫レベルの変更など。

カタログ同期サービスは、以下から製品データを移動します [!DNL Adobe Commerce] インスタンスからへ [!DNL Commerce Services] 継続的にプラットフォームを構築し、データを最新の状態に保ちます。 例： [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) 現在のカタログ情報を使用して、正確な名前、価格、在庫状況でレコメンデーションを正確に返す必要があります。 の使用 _カタログ同期_ 同期プロセスまたはコマンドラインインターフェイスを監視および管理するダッシュボード。カタログ同期をトリガーし、で使用するために製品データを再インデックス化します。 [!DNL Commerce Services]. 参照： [コマンドラインインターフェイスリファレンス](../data-export/data-export-cli-commands.md) が含まれる _SaaS データ エクスポート_ ガイド。

## カタログ同期ダッシュボードへのアクセス

カタログ同期ダッシュボードにアクセスするには、次を選択します **システム** > _データ転送_ > **カタログ同期**.

（を使用） **カタログ同期** ダッシュボードでは、次の操作を実行できます。

- 同期ステータスの表示（**処理中**, **成功**, **失敗**）
- 同期された製品の合計数を表示します
- 同期された製品を検索して現在の状態を表示
- 名前、SKU などでストアカタログを検索
- 同期の不一致を診断するのに役立つ、同期された製品の詳細を JSON で表示します
- 同期プロセスの再開

### 最終同期

次の同期ステータスを報告：

- **成功**  – 同期が成功した日時と、更新された製品の数を表示します
- **失敗**  – 同期が試行された日時を表示します
- **処理中**  – 前回成功した同期の日時を表示します

カタログ同期プロセスは、1 時間ごとに自動的に実行されます。 ストアフロントに期待した製品が表示されない場合、または製品に最近の変更が反映されていない場合は、以下を解決できます [カタログ同期の問題](#resolvesync).

### 同期済み製品

から同期された製品の合計数を表示します [!DNL Commerce] カタログ。 最初の同期の後は、変更された製品のみ同期する必要があります。

## 再同期 {#resync}

1 時間ごとのスケジュールされた同期が発生する前にカタログの再同期を開始する必要がある場合は、再同期を強制できます。

>[!NOTE]
>
> 再同期を強制すると、商品カタログ全体の再同期がトリガーされ、ハードウェアリソースの負荷が増す可能性があります。

1. から _カタログ同期_ ダッシュボード、選択 **設定**.

   この _カタログ同期設定_ ページが表示されます。

1. が含まれる _データを再同期_ セクションで、をクリック [!UICONTROL Resync].

   [!DNL Commerce] 次にスケジュールされた同期期間中にカタログを同期します。 カタログのサイズによっては、この操作に時間がかかる場合があります。

## 同期されたカタログ製品

この **同期されたカタログ製品** 表には、次の情報が表示されます。

| フィールド | 説明 |
|---|---|
| ID | 商品の一意の ID |
| 名前 | 商品のストアフロント名 |
| タイプ | 商品タイプ（シンプル、設定可能、ダウンロード可能など）を識別します |
| 前回のエクスポート | 商品が最後にカタログから正常に書き出された日付 |
| 最終変更日 | カタログで製品が最後に変更された日付 |
| SKU | 商品の在庫管理単位を表示します |
| 価格 | 商品の価格 |
| 可視性 | で定義された製品の表示設定 [!DNL Commerce] カタログ |

## カタログ同期の問題を解決 {#resolvesync}

参照： [ログとトラブルシューティング](../data-export/troubleshooting-logging.md#troubleshooting) が含まれる _SaaS データ エクスポート ガイド_.
