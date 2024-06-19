---
title: "[!DNL SaaS Data Export Guide]"
description: の使用について説明します [!DNL data export] Adobe Commerceと接続されたAdobe Commerce サービス間でデータを同期するCommerce SaaS サービスの拡張機能。」
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# [!DNL SaaS Data Export] ガイド

[!DNL SaaS data export] Adobe Commerce インスタンスと接続されたCommerce サービスの間のデータ同期を最適化することで、フロントエンドのパフォーマンスを向上させます。 Adobe Commerceのインストールに Live Search、Product Recommendationsまたは Catalog Service を追加すると、 [!DNL Data export] 拡張機能は自動的にインストールされます。

SaaS データ書き出しでは、さまざまなタイプのデータを収集して書き出します。このデータは、次のように参照されます _フィード_。特定のタイプの情報を集計します。 インストールされているCommerce サービスに応じて、SaaS データ書き出しフィードには次のものが含まれます。

- **カタログエンティティフィード** 製品データを集計します。 データには、製品、製品属性、製品価格、製品バリエーション、カテゴリ、カテゴリ権限、製品権限が含まれます。
- この **範囲フィード** 顧客グループ、web サイト、ストアおよびストアビューのデータを集計します。
- この **販売注文フィード** 注文データを集計します。請求書、出荷、クレジット メモなどの関連エンティティが含まれます。
- この **マルチソース在庫フィード** 在庫ステータス項目に関するデータの集計。

データの書き出し拡張機能では、データ同期プロセスを開始および管理するためのいくつかの方法をサポートしています。

- **管理者またはコマンドラインからの手動同期**

   - この [データ管理ダッシュボード](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) Commerce Admin には、同期ステータスがグラフィック表示されます。 ダッシュボードを使用して、完全な再同期（_完全同期_）を選択します。 ただし、Adobeでは、Adobe CommerceをCommerce サービスに初めて接続する際にのみ、完全同期を実行することをお勧めします。 参照： [同期プロセス](data-synchronization.md).

   - この [Adobe Commerce コマンドラインツール](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) （CLI）には、特定のフィードを同期するコマンドと、フィード処理をカスタマイズする追加オプションが用意されています。

- **Cron ジョブとの自動同期**

   - [部分的なデータ同期](data-synchronization.md#partial-synchronization-with-cron-jobs)- Commerce管理者ユーザーがエンティティを更新すると、Cron ジョブは部分的なデータ同期をトリガーにします。 データの書き出しプロセスでは、接続されたCommerce サービスに対してこれらの更新のみが送信されます。 部分同期プロセスはビューメカニズムに基づいており、管理者ユーザーまたはシステムインテグレーターの操作は必要ありません。

   - [同期エラーの自動再試行](data-synchronization.md#failed-items-sync-for-error-recovery)- データ同期プロセス中にエラーが発生した場合の、Cron ジョブトリガーによる同期プロセスの自動再試行。

- **スケジュールとパフォーマンスのエクスポート**

   - 開発者とシステムインテグレーターは、SaaS データの書き出しに要する時間を推定して、Adobe Commerceと接続されたサービスの間でデータを同期させることができます。 この概算は、サイトの中断を防ぐためにデータのエクスポート処理をスケジュールするのに役立ちます。 参照： [データ量と送信時間の推定](estimate-data-volume-sync-time.md).

   - 同期をより迅速に行う必要がある場合は、SaaS データのエクスポートを使用すると、エクスポート処理のパフォーマンスを向上させるためのカスタマイズオプションを利用できます。 参照： [データ書き出しのパフォーマンスの向上](customize-export-processing.md).

- **データ書き出しアクティビティの追跡とトラブルシューティング**- data-export ログと saas-export ログを使用して、同期とインデックス作成プロセス中に同期ステータスとフィードペイロードを確認します。 参照： [ログとトラブルシューティング](troubleshooting-logging.md).



