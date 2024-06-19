---
title: “[!DNL SaaS Data Export Extension] リリースノート」
description: の最新のリリース情報 [!DNL Data Export Extension] （Adobe Commerceの場合）
feature: Services, Release Notes
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# [!DNL SaaS Data Export] 拡張機能のリリースノート

これらのリリースノートでは、の最新バージョンについて説明します [!DNL SaaS data export] 拡張機能。 現在のメジャーリリースバージョンに対するサポートが提供されます。 古いバージョンのリリースノートが参照用に提供されています。

次のような更新があります。

![新規](../assets/new.svg) 新機能
![修正](../assets/fix.svg) 修正点および改善点
![バグ](../assets/bug.svg) 既知の問題


>[!NOTE]
>
>SaaS データ書き出し拡張機能は、Live Search、Product Recommendations、カタログサービスと共に自動的にインストールされるモジュールのコレクションです。 コンポーザーを使用して、システムにインストールされているバージョンを確認できます。 場合によっては、Commerce サービスのバージョンを更新せずに修正点または新機能を取得するように、システムのデータエクスポート拡張機能をアップグレードする必要があります。

## 現在のメジャーバージョン

## 103.3.5 リリース

![修正](../assets/fix.svg) SaaS 共通モジュールの最新の互換性のあるデータ書き出しバージョンの依存関係を設定します。

![修正](../assets/fix.svg) 置き換え `ScopeConfig` 次を使用してインスタンス `ServiceConfigInterface` 異なるサービス設定をサポートします。

## 103.3.4 リリース

![修正](../assets/fix.svg) インデックス再作成プロセスの詳細を追加して、Commerce SaaS データ書き出しログを改善しました。

## 103.3.3 リリース

![新規](../assets/new.svg) SaaS データ エクスポートで、属性メタデータ クエリの Entity-Attribute-Value （EAV）属性がキャッシュされるようになりました。

![修正](../assets/fix.svg) がの問題を修正しました `InventoryStockStatus` 製品が削除された場合、再試行時にフィードが保存されませんでした。

## 103.3.2 リリース

![修正](../assets/fix.svg) がの問題を修正しました `modifiedAt` 削除されたエンティティフィードにフィールドがありませんでした。

## 103.3.1 リリース

![修正](../assets/fix.svg) を実行する原因となった問題を修正しました `Invalid Template File` ページビルダーのインストール時に、製品フィードのインデックス再作成中に表示されるメッセージ。

## 103.3.0 リリース

![新規](../assets/new.svg) 即時のエクスポートフィードテーブルを統合構造に移行しました。
`id`, `source_entity_id`, `feed_id`, `modified_at`, `is_deleted`, `status`, `feed_data`, `feed_hash`, `errors`

![新規](../assets/new.svg) 移行されたカタログおよび在庫は、即時エクスポートソリューションにフィードされます。

![新規](../assets/new.svg) 即時エクスポートフィード cron-jobs の名前をに変更 `*_feed_resend_failed_items`.

![新規](../assets/new.svg) 即時エクスポートフィードおよび変更ログテーブルの名前を変更しました。

![修正](../assets/fix.svg) を設定 `modified_at` フィードデータのフィールドは、必要なフィードに対してのみ使用できます。

![修正](../assets/fix.svg) を変更する `productAttributes` 製品属性のみを取得するクエリ。

## 103.2.6 リリース

![修正](../assets/fix.svg) テーブルにプレフィックスがある場合にフィードのインデックスを再作成できない問題を修正しました。

## 103.2.5 リリース

![修正](../assets/fix.svg) 価格クエリを最適化しました。

## 103.2.4 リリース

![修正](../assets/fix.svg) Commerce Inventory managementが有効になっている場合に、商品に表示される誤った在庫ステータスを修正しました。

## 103.2.3 リリース

![修正](../assets/fix.svg) Web サイトレベルの固定価格。
![修正](../assets/fix.svg) 処理されるすべてのフィードに mutex が追加されました。


## 103.2.2 リリース

![修正](../assets/fix.svg) 大規模なカタログのフィードのバッチ化戦略を改善しました。 メモリの使用量を減らすために、バッチ表に入力される ID の数が制限されるようになりました。

![修正](../assets/fix.svg) CommerceInventoryDataExporter の MSI モジュールへのハード依存をなくしました。

![修正](../assets/fix.svg) 改善 `commerce-data-exporter` ログを使用して、より多くの情報を収集し、様々なエクスポートステージ別に整理します。

## 103.2.1 リリース

- リリースされている更新バージョン。

## 103.2.0 リリース

- 製品と価格のマルチスレッドデータ同期を追加しました。

