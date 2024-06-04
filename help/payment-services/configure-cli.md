---
title: コマンドライン設定
description: インストール後、以下を設定できます [!DNL Payment Services] コマンドラインインターフェイス（CLI）を使用する。
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
feature: Payments, Checkout, Configuration, Integration
source-git-commit: d1379bb108f2259051641a7bf77cd8b459fd9cbf
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# コマンドライン設定

インストール後 [!DNL Payment Services]から簡単に設定できます。 [自宅内](payments-home.md) または、コマンドラインインターフェイス（CLI）を使用します。

## データの書き出しの設定

[!DNL Payment Services] から書き出された注文データを結合します [!DNL Magento Open Source] および [!DNL Adobe Commerce] 便利なレポートを作成するために、支払いプロバイダーから集計された支払いデータを使用します。 この [!DNL Payment Services] 拡張機能では、インデクサーを使用して、レポートに必要なすべてのデータを効率的に収集します。

で使用されているデータについて説明します [!DNL Payment Services] レポート、を参照 [注文支払いステータスレポート](order-payment-status.md#data-used-in-the-report).

### での cron の設定 [!DNL Magento Open Source]

を使用する場合 `BY SCHEDULE` インデックスモード オン [!DNL Magento Open Source]を設定する必要があります。 参照： [Cron の設定と実行](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### インデクサーの設定

注文データは、次の 2 つのインデックスモードのいずれかを使用して、支払いサービスにエクスポートされ、保持されます。`ON SAVE` （デフォルト）または `BY SCHEDULE` （推奨）。

次のインデックスは、 [!DNL Payment Services]:

| コード | 名前 | 説明 |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | 販売注文フィード | 注文データのインデックスを作成 |
| `sales_order_status_data_exporter` | 販売注文ステータス フィード | 販売注文の状態データのインデックスを作成します |
| `store_data_exporter` | フィードを保存 | ストアデータのインデックスを作成します |

3 つのインデクサーすべてのインデックスモードを変更するには、次を実行します。

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>コマンドでインデクサーを指定しない場合、すべてのインデクサーが同じ値に更新されます。 特定のインデクサーを変更する場合は、コマンドでそのインデクサーをリストする必要があります。

インデクサーのモードを手動で変更する方法については、を参照してください [インデクサーの設定](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers){target="_blank"} 開発者向けドキュメント 管理者で変更する方法については、を参照してください。 [インデックス管理](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target="_blank"} （コアユーザーガイド）を参照してください。

### データを手動で再インデックス化

データが自動的に実行されるのを待たずに、手動でデータをインデックス再作成できます。 参照： [再インデックス](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target="_blank"} 。対象： [インデクサーの管理](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target="_blank"} を参照してください。

条件 `BY SCHEDULE` モードを設定すると、システムは変更されたエンティティを追跡し、cron ジョブは設定されたスケジュールに基づいてエンティティのインデックスを更新します。 参照： [コマンドラインから cron を実行します](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) 。対象： [Cron の設定と実行](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)）を参照し、cron ジョブを使用してインデックスを手動でトリガーする方法を確認してください。

### インデックス再作成されたデータを支払サービスに送信

インデックスが作成されたデータは、に自動的に送信されます。 [!DNL Payment Services]. また、次のコマンドを使用して、インデックス付きデータを送信するプロセスを手動でトリガーすることもできます。

```bash
bin/magento saas:resync --feed [feedName]
```

次のコマンドオプションを使用します。

| コマンド | 説明 |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | 指定されたフィードのインデックス再作成を実行し、対応するサービスに送信します |
| `bin/magento saas:resync --no-reindex` | インデックス化をスキップし、非同期データをインデックスから送信します。 |

この `--feed` パラメーターを使用すると、送信するフィードを指定できます。

| フィード | 説明 |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | 生産モードでの注文フィード |
| `paymentServicesOrdersSandbox` | サンドボックスモードでの注文フィード |
| `paymentServicesOrderStatusesProduction` | 生産モードでの注文ステータス |
| `paymentServicesOrderStatusesSandbox` | サンドボックスモードでのステータスの並べ替え |
| `paymentServicesStoresProduction` | 実稼動モードのストア |
| `paymentServicesStoresSandbox` | サンドボックスモードのストア |

レポートに必要なすべてのデータの送信先 [!DNL Payment Services] cron が設定およびインストールされている場合は自動的に。 また、cron データをに送信するプロセスを手動でトリガーすることもできます [!DNL Payment Services].

```bash
bin/magento cron:run --group payment_services_data_export
```

インデックス再作成とインデクサーについて詳しくは、を参照してください。 [インデクサーの管理](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) トピックについては、開発者ドキュメントを参照してください。

## L2/L3 処理の設定

[!DNL Payment Services] では、カード支払取引のレベル 2 およびレベル 3 のデータを処理して、マーチャントに追加情報を提供できます。

>[!WARNING]
>
> PayPal を使用したレベル 2 およびレベル 3 の処理との統合は、米国のマーチャントのみが利用できます。 参照： [支払い処理](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank} 詳しくは、PayPal 開発者向けドキュメントを参照してください。

以下に対して L2/L3 処理データを使用する場合： [!DNL Payment Services]ご不明な点がございましたら、お問い合わせください。 [!DNL Payment Services] アカウントマネージャー。

で使用される L2 および L3 の処理について [!DNL Payment Services]を参照してください [レベル 2 およびレベル 3 の処理](levels-card-payment-transactions.md).
