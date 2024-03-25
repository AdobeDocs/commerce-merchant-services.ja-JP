---
title: カタログ同期
description: から製品データを書き出す方法を説明します。 [!DNL Commerce] サーバーから [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: d95c11a35c78d72da8126affb0753d86aa695827
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 0%

---


# カタログ同期

>[!NOTE]
>
> 「カタログ同期」ダッシュボードが「データ管理」ダッシュボードになりました。 この改良されたダッシュボードは、 [[!DNL Product Recommendations]](../product-recommendations/guide-overview.md), [[!DNL Live Search]](../live-search/guide-overview.md)、および [[!DNL Catalog Service]](../catalog-service/overview.md). お客様は、データ管理ダッシュボードを取得するには、これらのサービスのいずれかを最新バージョンに更新します。 詳しくは、 [データ管理ダッシュボード](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) ドキュメント。 この現在のトピックは、まだアップグレードせず、まだカタログ同期ダッシュボードを持っているユーザーに対しても引き続き表示されます。

Adobe Commerceは、インデクサーを使用してカタログデータをテーブルにコンパイルします。 プロセスは、次を通じて自動的にトリガーされます： [イベント](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) 製品価格や在庫レベルの変更など。

カタログ同期サービスは、製品データを [!DNL Adobe Commerce] インスタンスから [!DNL Commerce Services] データを最新の状態に保つための、継続的なプラットフォーム。 例： [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) では、現在のカタログ情報が正しい名前、価格、可用性を使用してレコメンデーションを正確に返すように必要になります。 以下を使用します。 _カタログ同期_ 同期プロセスを監視および管理するためのダッシュボード [コマンドラインインターフェイス](#resynccmdline) カタログ同期をトリガーし、使用する製品データのインデックスを再作成するには、以下を実行します。 [!DNL Commerce Services].

## カタログ同期ダッシュボードへのアクセス

カタログ同期ダッシュボードにアクセスするには、「 **システム** > _データ転送_ > **カタログ同期**.

を使用 **カタログ同期** ダッシュボードでは、次の操作を実行できます。

- 同期ステータスを表示 (**処理中**, **成功**, **失敗**)
- 同期された製品の合計数を表示します
- 同期した製品を検索して現在の状態を表示
- 名前、SKU などでストアカタログを検索
- 同期された製品の詳細を JSON で表示して、同期の不一致を診断するのに役立ちます
- 同期プロセスを再開します

### 前回の同期

次の同期ステータスを報告します。

- **成功**  — 同期が成功した日時と更新された製品数を表示
- **失敗**  — 同期が試行された日時を表示
- **処理中**  — 最後に同期が成功した日時を表示します

カタログ同期プロセスは、1 時間ごとに自動的に実行されます。 ストアフロントに期待した製品が表示されない場合や、製品に最近の変更が反映されていない場合は、解決できます [カタログ同期の問題](#resolvesync).

### 同期された製品

から同期された製品の合計数が表示されます [!DNL Commerce] カタログ。 初回同期後は、変更された製品のみを同期する必要があります。

## 再同期 {#resync}

時間別にスケジュールされた同期が実行される前にカタログの再同期を開始する必要がある場合は、強制的に再同期を実行できます。

>[!NOTE]
>
> 再同期を強制すると、トリガーカタログ全体を再同期するので、ハードウェアリソースの負荷が増加する可能性があります。

1. 次から： _カタログ同期_ ダッシュボード、選択 **設定**.

   The _カタログ同期設定_ ページが表示されます。

1. Adobe Analytics の _データの再同期_ セクションで、 [!UICONTROL Resync].

   [!DNL Commerce] 次のスケジュール済み同期ウィンドウ中にカタログを同期します。 カタログのサイズによっては、この操作に時間がかかる場合があります。

## 同期済みカタログ製品

The **同期済みカタログ製品** テーブルには、次の情報が表示されます。

| フィールド | 説明 |
|---|---|
| ID | 商品の一意の ID |
| 名前 | 製品のストアフロント名 |
| タイプ | 製品の種類（簡易、設定可能、ダウンロード可能など）を識別します。 |
| 最後のエクスポート | 商品がカタログから最後に正常に書き出された日付 |
| 最終変更日 | カタログで商品が最後に変更された日付 |
| SKU | 製品の在庫管理単位を表示します |
| 価格 | 製品の価格 |
| 表示 | で定義されている製品の表示設定 [!DNL Commerce] カタログ |

## カタログ同期の問題を解決 {#resolvesync}

データの再同期をトリガーする際、データが更新されてレコメンデーション単位などの UI コンポーネントに反映されるまでに最大 1 時間かかる場合があります。 それでも、カタログとストアフロントのデータの間に不一致が生じる場合や、カタログの同期に失敗した場合は、次を参照してください。

### データの不一致

1. 該当する製品の詳細ビューを検索結果に表示します。
1. JSON 出力をコピーし、コンテンツが [!DNL Commerce] カタログ。
1. コンテンツが一致しない場合は、スペースやピリオドの追加など、カタログ内の製品に小さな変更を加えます。
1. 再同期を待つか、 [トリガーの手動再同期](#resync).

### 同期が実行されていません

同期がスケジュールに従って実行されていない場合、または何も同期されていない場合は、次を参照してください [KnowledgeBase](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) 記事。

### 同期に失敗しました

カタログ同期のステータスが **失敗**、送信 [サポートチケット](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## コマンドラインインターフェイス {#resynccmdline}

The `saas:resync` コマンドは、 `magento/saas-export` パッケージに含まれ、 [!DNL Commerce Services] 製品 ( 例： [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) または [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> データ同期を初めて実行する場合は、 `productattributes` 最初にフィードを開き、次に `productoverrides`、実行前 `products` フィード。

コマンドオプション：

```bash
bin/magento saas:resync --feed <feed name> [no-reindex|cleanup-feed]
```

次の表に、 `saas:resync` パラメーターと説明。

| パラメーター | 説明 | 必須？ |
|---| ---| ---|
| `feed` | 再同期するエンティティを指定します。例： `products` | はい |
| `no-reindex` | 既存のカタログデータをに再送信します [!DNL Commerce Services] インデックスを再作成せずに このパラメーターを指定しない場合、コマンドはデータを同期する前に完全な再インデックスを実行します。 | いいえ |
| `cleanup-feed` | 同期の前にフィードインデクサーテーブルをクリーンアップします。 | いいえ |

フィード名は、次のいずれかになります。

- `products` — カタログ内の製品
- `productattributes` — 製品属性（例： ） `activity`, `gender`, `tops`, `bottoms`など
- `variants` — 色やサイズなど、設定可能な製品の製品バリエーション。
- `prices`  — 製品価格
- `scopesCustomerGroup`  — 顧客グループ
- `scopesWebsite`  — ストア表示の Web サイト
- `categories` — カタログ内のカテゴリ
- `categoryPermissions`  — 各カテゴリの権限
- `productoverrides` — カテゴリ権限に基づく価格やカタログ表示ルールなど、お客様固有の価格やカタログ表示ルール

対象に応じて [コマースサービス](../landing/saas.md) がインストールされている場合、異なるフィードセットを使用できる可能性があります `saas:resync` コマンドを使用します。

を実行することはお勧めしません。 `saas:resync` コマンドを定期的に実行します。 次の 2 つのシナリオで、コマンドを手動で実行する必要が生じる場合があります。

- 初期同期
- The [SaaS データ容量 ID](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) 変更済み

### 初期同期

次の場合にトリガーa `saas:resync` コマンドラインから、カタログのサイズに応じて、データが更新されるまで、数分から数時間かかる場合があります。

初期同期の場合は、次の順序でコマンドを実行することをお勧めします。

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions 
```

### トラブルシューティング

に予期されたデータが表示されない場合は、 [!DNL Commerce Service]、同期中に問題が発生したかどうかを [!DNL Adobe Commerce] インスタンスから [!DNL Commerce Service] プラットフォーム。

には 2 つのログファイルがあります。 `var/log/` ディレクトリ：

- `commerce-data-export-errors.log`  — 次の期間にエラーが発生した場合 _収集_ 位相
- `saas-export-errors.log`  — 次の期間にエラーが発生した場合 _送信中_ 位相

#### フィードペイロードを確認

これは、 [!DNL Commerce Service]. これは、環境変数 `EXPORTER_EXTENDED_LOG=1`. The `no-reindex` フラグは、現在収集されているデータのみが送信されることを意味します。

```bash
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products --no-reindex
```

ペイロードは、 `var/log/saas-export.log`.

#### フィードインデックステーブルのペイロードを保持

開始元 `magento/module-data-exporter:103.0.0` 一部のフィード（製品フィード、価格フィード）では、インデックステーブルに最低限必要なデータのみを保持します。

実稼動環境では、インデックステーブルにペイロードデータを保持することは推奨されませんが、開発者インスタンスで役立つ場合があります。 これは、 `PERSIST_EXPORTED_FEED=1` 環境変数：

```bash
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

#### プロファイル

特定のフィードの再インデックス処理に不合理な時間がかかる場合は、プロファイラを実行して、サポートチームに役立つ追加データを収集します。 これをおこなうには、 `EXPORTER_PROFILER=1`環境変数：

```bash
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

プロファイラーデータは、に保存されます。 `var/log/commerce-data-export.log` を次の形式で置き換えます。

`<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>`

#### サポートリクエストを送信

設定やサードパーティの拡張機能に関連しないエラーが表示された場合は、 [サポートチケット](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) できるだけ多くの情報を持って
