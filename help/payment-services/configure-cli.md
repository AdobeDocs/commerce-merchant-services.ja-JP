---
title: コマンドライン設定
description: インストール後、 [!DNL Payment Services] コマンドラインインターフェイス (CLI) を使用する。
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# コマンドライン設定

インストール後 [!DNL Payment Services]を使用すると、 [家の中で](payments-home.md) または CLI（コマンド・ライン・インタフェース）を使用します。

## データエクスポートの設定

[!DNL Payment Services] から書き出された注文データを組み合わせます [!DNL Magento Open Source] および [!DNL Adobe Commerce] を使用して、有用なレポートを作成するための支払いプロバイダーからの集計された支払いデータ。 この [!DNL Payment Services] 拡張機能では、インデクサーを使用して、レポートに必要なすべてのデータを効率的に収集します。

で使用されるデータについて学ぶには [!DNL Payment Services] レポートについては、 [注文の支払いステータスレポート](order-payment-status.md#data-used-in-the-report).

### cron の設定 [!DNL Magento Open Source]

を使用する場合、 `BY SCHEDULE` インデックスモード [!DNL Magento Open Source]を設定する場合は、cron を設定する必要があります。 詳しくは、 [cron の設定と実行](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### インデクサーを設定

注文データは、次の 2 つのインデックスモードのいずれかを使用して、支払サービスでエクスポートおよび永続化されます。`ON SAVE` （デフォルト）または `BY SCHEDULE` （推奨）。

次のインデックスは、 [!DNL Payment Services]:

| コード | 名前 | 説明 |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | 販売注文フィード | 注文データのインデックスを作成します |
| `sales_order_status_data_exporter` | 販売注文ステータスフィード | 販売注文ステータスデータのインデックスを作成します |
| `store_data_exporter` | フィードを保存 | ストアデータのインデックスを作成します |

3 つのインデクサすべてに対してインデックス・モードを変更するには、次のコマンドを実行します。

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>コマンドにインデクサを指定しない場合、すべてのインデクサは同じ値に更新されます。 特定のインデクサを変更する場合は、コマンドでそのインデクサをリストする必要があります。

インデクサーのモードを手動で変更する方法について詳しくは、 [インデクサーの設定](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers){target=&quot;_blank&quot;}（開発者向けドキュメント）。 管理者で変更する方法については、 [インデックス管理](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target=&quot;_blank&quot;}（コアユーザーガイド）。

### 手動でデータを再インデックス

データが自動的に発生するのを待つ代わりに、手動でデータのインデックスを再作成できます。 詳しくは、 [再インデックス](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target=&quot;_blank&quot;} in [インデクサーの管理](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target=&quot;_blank&quot;} を参照してください。

条件 `BY SCHEDULE` モードが設定されている場合、システムは変更されたエンティティをトラッキングし、cron ジョブは設定されたスケジュールに基づいて、変更されたエンティティのインデックスを更新します。 詳しくは、 [コマンドラインから cron を実行します。](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) in [cron の設定と実行](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)) を参照してください。

### 支払いサービスに再インデックス化されたデータを送信

データのインデックスが作成されると、に自動的に送信されます。 [!DNL Payment Services]. また、次のコマンドを使用して、インデックス付きデータを送信するプロセスを手動でトリガーすることもできます。

```bash
bin/magento saas:resync --feed [feedName]
```

次のコマンドオプションを使用します。

| コマンド | 説明 |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | 指定されたフィードのインデックス再作成を実行し、それを対応するサービスに送信します |
| `bin/magento saas:resync --no-reindex` | インデックス作成をスキップし、同期されていないデータをインデックスから送信します |

この `--feed` パラメーターを使用すると、送信するフィードを指定できます。

| フィード | 説明 |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | 実稼動モードでのフィードのオーダー |
| `paymentServicesOrdersSandbox` | サンドボックスモードでのフィードの注文 |
| `paymentServicesOrderStatusesProduction` | 実稼働モードでのオーダーステータス |
| `paymentServicesOrderStatusesSandbox` | サンドボックスモードでの注文ステータス |
| `paymentServicesStoresProduction` | 実稼動モードでのストア |
| `paymentServicesStoresSandbox` | サンドボックスモードでのストア |

レポートに必要なすべてのデータは、 [!DNL Payment Services] cron が設定され、インストールされている場合は、自動的にを設定します。 また、に cron データを送信するプロセスを手動でトリガーすることもできます。 [!DNL Payment Services].

```bash
bin/magento cron:run --group payment_services_data_export
```

インデックスの再作成とインデクサーについて詳しくは、 [インデクサーの管理](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) トピックに関する情報が含まれています。
