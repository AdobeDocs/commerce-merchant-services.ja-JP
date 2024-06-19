---
title: ログの確認とトラブルシューティング
description: 「トラブルシューティング方法を学ぶ [!DNL data export] データの書き出しログと saas-export ログを使用したエラー。」
feature: Services
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---


# ログの確認とトラブルシューティング

この [!DNL data export] 拡張機能は、データ収集および同期プロセスを追跡するログを提供します。

## ログ

ログは、次で利用できます `var/log` Commerce アプリケーションサーバー上のディレクトリ。

| ログ名 | ファイル名 | 説明 |
|-----------------| ----------| -------------|
| SaaS データ エクスポート ログ | `commerce-data-export.log` | エンティティトリガーや完全な再同期イベントなど、データの書き出しアクティビティに関する情報を提供します。  各ログレコードは特定の構造を持ち、フィード、操作、ステータス、経過時間、プロセス ID、呼び出し元に関する情報を提供します。 |
| SaaS データ エクスポート エラーログ | `data-export-errors.log` | データ同期処理中に発生したエラーのエラーメッセージとスタックトレースを提供します。 |
| SaaS エクスポート ログ | `saas-export.log` | Commerce SaaS サービスに送信されるデータに関する情報を提供します。 |
| SaaS エクスポート エラーログ | `saas-export-errors.log` | Commerce SaaS サービスにデータを送信する際に発生するエラーについて説明します。 |

Adobe Commerce サービスで予期されたデータが表示されない場合は、データエクスポート拡張機能のエラーログを使用して問題の発生場所を特定してください。

トラッキングとトラブルシューティングのために、追加データでログを拡張できます。 参照： [拡張ログ](#extended-logging).

### ログ形式

各ログレコードの構造は次のとおりです。

```
[<log record datetime>] report.<log level>:
{
   "feed": "<feed name>",
   "operation": "<executed operation>",
   "status": "<status of operation>",
   "elapsed": "<time elaspsed from script run>",
   "pid": "<proccess id who executed `operation`>",
   "caller": "<who called this `operation`>"
} [] []
```

>[!NOTE]
>
>JSON ベースの文字列は、読みやすいように美化されています。

次の表に、ログに記録できる操作タイプを示します。

| 操作 | 説明 | 呼び出し元の例 |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| 完全同期 | フル同期では、特定のフィードに対して、すべてのデータを収集し、SaaS に送信します。 | `bin/magento saas:resync --feed=products` |
| 部分再インデックス | 部分同期では、特定のフィード内で更新されたエンティティについてのみ、データを収集して SaaS に送信します。 このログは、更新されたエンティティが存在する場合にのみ表示されます。 | `bin/magento cron:run --group=index` |
| 失敗した項目を再試行 | Commerce アプリケーションまたはサーバーエラーが原因で前回の同期処理に失敗した場合に、SaaS への特定のフィードの項目を再送信します。 このログは、失敗した項目が存在する場合にのみ存在します。 | `bin/magento cron:run --group=saas_data_exporter`  （任意の「*_data_exporter」 cron グループ） |
| 完全同期（レガシー） | レガシーエクスポートモードでの特定フィードの完全同期。 | `bin/magento saas:resync --feed=categories` |
| 部分再インデックス（レガシー） | レガシー書き出しモードの特定のフィードに対して、更新されたエンティティを SaaS に送信します。 このログは、更新されたエンティティが存在する場合にのみ表示されます。 | `bin/magento cron:run --group=index` |
| 部分同期（レガシー） | レガシー書き出しモードの特定のフィードに対して、更新されたエンティティを SaaS に送信します。 このログは、更新されたエンティティが存在する場合にのみ表示されます。 | `bin/magento cron:run --group=saas_data_exporter` （任意の「*_data_exporter」 cron グループ） |


### ログの例

完全な再同期では、進行状況はデフォルトで 30 秒ごとに追跡され、記録されます。 ログエントリの例を次に示します。

```json
{
   "feed": "prices",
   "operation": "full sync",
   "status": "Progress: 2/5, processed: 200, synced: 100",
   "elapsed": "00:00:00 190 ms",
   "pid": "12824",
   "caller": "bin/magento saas:resync --feed=products"
}
```

この例では、 `status` 値は、同期操作に関する情報を提供します。

- **`"Progress 2/5"`** 5 回のイテレーションのうち 2 回が完了したことを示します。 イテレーションの数は、エクスポートされたエンティティの数によって異なります。
- **`"processed: 200"`** 200 個の項目が処理されたことを示します。
- **`"synced: 100"`** 100 項目が SaaS に送信されたことを示します。 予想される `"synced"` 次と等しくない `"processed"`. 次に例を示します。
   - **`"synced" < "processed"`** は、以前に同期されたバージョンと比較して、フィードテーブルで項目の変更が検出されなかったことを意味します。 このような項目は、同期操作中は無視されます。
   - **`"synced" > "processed"`** 同じエンティティ id （例：） `Product ID`）には、異なる範囲に複数の値を含めることができます。 例えば、1 つの製品を 5 つの web サイトに割り当てることができます。 この場合、「1 件の処理済み」項目と「5 件の同期済み」項目が存在する可能性があります。

+++ 例：価格フィードの完全再同期ログ

```
Price feed full resync:

[2024-03-05T21:00:51.754687+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Initialize","elapsed":"383 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.803178+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Creating batch table `catalog_data_exporter_product_prices_index_batches`. Start position: 30515","elapsed":"434 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.851878+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Batch table `catalog_data_exporter_product_prices_index_batches` created. Total Items: 500, batches: ~1","elapsed":"482 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:51.852548+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"start processing `500` items in `1` threads with `500` batch size","elapsed":"483 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:52.288369+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Progress 1\/1, processed 500, synced 0","elapsed":"919 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:53.994249+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Progress 1\/1, processed 500, synced 100","elapsed":"00:00:02 625 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
[2024-03-05T21:00:53.995168+00:00] report.INFO: {"feed":"prices","operation":"full sync","status":"Complete","elapsed":"00:00:02 626 ms","pid":"14469","caller":"bin\/magento saas:resync --feed=prices"} [] []
```

+++

## New Relicでのログの表示とトラブルシューティング

Adobe Commerce ログをNew Relicに保存する場合は、解析ルールを追加して、読みやすさとクエリエクスペリエンスを向上させることができます。

1. New Relicにログインします。

1. に移動 `Logs => Parsing`.

1. クリック `Create parsing rule`.

1. 次の値を追加して、解析ルールを設定します。

   - **NRQL に基づいたログのフィルタリング**

     `filePath LIKE '%commerce-data-export%.log'`

   - **解析ルール**

     `\[%{DATA:timestamp}\] report.%{DATA:logLevel} %{GREEDYDATA:feed:json}`

この例では、特定のフィードのタイプや処理などでNew Relic ログをクエリできるルールを追加します。

**クエリ文字列の例**—`feed.feed:"products" and feed.status:"Complete"`

## 拡張ログ

環境変数を使用して、トラッキングやトラブルシューティングのために追加データでログを拡張できます。

### フィードペイロードを確認

を追加して、フィードペイロードを SaaS 書き出しログに含めます。 `EXPORTER_EXTENDED_LOG=1` フィードを再同期する際の環境変数。

```shell script
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products
```

操作が完了すると、フィードペイロードを SaaS 書き出しログ（`var/.log/saas-export.log`）に設定します。

### フィードインデックステーブルにペイロードを保持

Commerce SaaS データエクスポート拡張機能の場合（`magento/module-data-exporter`） 103.3.0 以降、即時エクスポートフィードでは、インデックステーブルに必要な最小限のデータのみが保持されます。 フィードには、すべてのカタログと在庫のステータスフィードが含まれます。

実稼動環境ではペイロードデータをインデックステーブルに保持することは推奨されませんが、開発者環境では便利です。 を追加して、フィードペイロードをインデックスに含めます。 `PERSIST_EXPORTED_FEED=1` フィードを再同期する際の環境変数。

```shell script
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

### プロファイラーを実行してパフォーマンスが低下する場合のトラブルシューティング

特定のフィードの再インデックスプロセスに不相応な時間がかかる場合は、プロファイラーを実行して、サポートチームに役立つ追加データを収集します。

を追加してプロファイラーを実行します。 `EXPORTER_PROFILER=1` reindex コマンド実行時の環境変数。

```
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

プロファイラーデータはデータ書き出しログ（`var/log/commerce-data-export.log`）に設定する必要があります。

```
<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>
```




