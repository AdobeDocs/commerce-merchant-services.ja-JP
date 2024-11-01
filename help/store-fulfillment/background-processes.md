---
title: バックグラウンドプロセス設定
description: 「データをフルフィルメントサービス  [!DNL Store Fulfillment]  同期する際に使用されるバックグラウンドプロセスのスケジュールを設定します。」
role: Admin, Developer
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 37380063242b6d904910be731b8e58471625e9cb
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# バックグラウンドプロセス設定

ストアフルフィルメント統合では、最適なパフォーマンスと拡張性を実現するために、バックグラウンドプロセスとメッセージキューを使用します。 自動的に開始する [ デプロイメント変数 ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#cron_consumers_runner) を使用して、Adobe Commerce ストアの環境を作成します [ メッセージキューランナー ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework)。

バックグラウンドプロセスは、標準のAdobe Commerce[ スケジュールされたタスク ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cron) 機能を使用して管理されます。 これらのプロセスは、注文とマーチャントストアの設定データをストアフルフィルメント web サービスと同期する役割を果たします。

## Store Fulfillment のスケジュールされたタスクの管理

管理者から、**[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]** に移動します。

Store Fulfillment サービスのデフォルト設定を確認します。 これらの設定は、注文処理量とリソースの可用性に基づいてカスタマイズできます。
