---
title: バックグラウンドプロセス設定
description: 次のスケジュールを設定： [!DNL Store Fulfillment] データをフルフィルメントサービスと同期する際に使用するバックグラウンドプロセス」
role: Admin, Developer
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# バックグラウンドプロセス設定

ストアフルフィルメント統合では、最適なパフォーマンスとスケールを実現するために、バックグラウンドプロセスとメッセージキューを使用します。 を使用して、Adobe Commerceストア用の環境を構築します。 [デプロイメント変数](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) 自動的に開始する [メッセージキューランナー](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html).

バックグラウンドプロセスは、標準のAdobe Commerce [予定タスク](https://docs.magento.com/user-guide/system/cron.html) 機能。 これらのプロセスは、注文とマーチャントストアの設定データをストアフルフィルメント Web サービスと同期する役割を果たします。

## ストアの達成の予定タスクを管理

管理者から、に移動します。 **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**.

ストアフルフィルメントサービスのデフォルト設定を確認します。 これらの設定は、注文処理の量とリソースの可用性に応じてカスタマイズできます。
