---
title: '[!DNL SaaS Data Export Extension] リリースノート'
description: Adobe Commerceの最新  [!DNL Data Export Extension]  リリース情報です。
feature: Services, Release Notes
recommendations: noCatalog
exl-id: 0c7aeeda-e8a6-4740-b466-0661a6d2df07
source-git-commit: 42a9ea0f62f35db451cd3e780adf530d0699a638
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# [!DNL SaaS Data Export] Extension リリースノート

これらのリリースノートでは、[!DNL SaaS data export] 拡張機能の最新バージョンについて説明します。 現在のメジャーリリースバージョンに対するサポートが提供されます。 古いバージョンのリリースノートが参照用に提供されています。

次のような更新があります。

![ 新機能 ](../assets/new.svg) 新機能
![ 修正 ](../assets/fix.svg) 修正点および改善点
![ バグ ](../assets/bug.svg) 既知の問題


>[!NOTE]
>
>SaaS データ書き出し拡張機能は、Live Search、Product Recommendations、カタログサービスと共に自動的にインストールされるモジュールのコレクションです。 コンポーザーを使用して、システムにインストールされているバージョンを確認できます。 場合によっては、Commerce サービスのバージョンを更新せずに修正点または新機能を取得するように、システムのデータエクスポート拡張機能をアップグレードする必要があります。

## 現在のメジャーバージョン

## 103.3.5 リリース

![ 修正 ](../assets/fix.svg)SaaS 共通モジュールの最新の互換性のあるデータ書き出しバージョンの依存関係を設定します。

![ 修正 ](../assets/fix.svg) 別のサービス設定 `ScopeConfig` サポートするために、インスタンスを `ServiceConfigInterface` に置き換えました。

## 103.3.4 リリース

![ 修正 ](../assets/fix.svg) インデックス再作成プロセスの詳細を追加して、Commerce SaaS データ書き出しログを改善します。

## 103.3.3 リリース

![ 新規 ](../assets/new.svg)SaaS データ エクスポートで、属性メタデータ クエリの Entity-Attribute-Value （EAV）属性がキャッシュされるようになりました。

![ 修正 ](../assets/fix.svg) 製品が削除された場合に、再試行時に `InventoryStockStatus` フィードが保存されない問題を修正しました。

## 103.3.2 リリース

![ 修正 ](../assets/fix.svg) 削除されたエンティティフィードに `modifiedAt` フィールドが表示されない問題を修正しました。

## 103.3.1 リリース

![ 修正 ](../assets/fix.svg) ページビルダーのインストール時に、製品フィードのインデックス再作成中に `Invalid Template File` メッセージが表示される問題を修正しました。

## 103.3.0 リリース

![ 新規 ](../assets/new.svg) 統合構造に即時エクスポートフィードテーブルを移行しました。
`id`, `source_entity_id`, `feed_id`, `modified_at`, `is_deleted`, `status`, `feed_data`, `feed_hash`, `errors`

![ 新規 ](../assets/new.svg) 移行されたカタログおよび在庫は、即時エクスポートソリューションにフィードされます。

![ 新規 ](../assets/new.svg) 即時エクスポートフィード cron-jobs の名前を `*_feed_resend_failed_items` に変更しました。

![ 新規 ](../assets/new.svg) 即時エクスポートフィードおよび変更ログテーブルの名前を変更しました。

![ 修正 ](../assets/fix.svg) フィードデータのフィールド `modified_at`、必要なフィードに対してのみ設定します。

![ 修正 ](../assets/fix.svg) 製品属性のみを取得するように `productAttributes` クエリを変更します。

## 103.2.6 リリース

![ 修正 ](../assets/fix.svg) テーブルにプレフィックスが付いている場合にフィードのインデックスを再作成できない問題を修正しました。

## 103.2.5 リリース

![ 修正 ](../assets/fix.svg) 価格クエリを最適化しました。

## 103.2.4 リリース

![ 修正 ](../assets/fix.svg)Commerce Inventory managementが有効な場合に、商品に対して表示される間違った在庫ステータスを修正しました。

## 103.2.3 リリース

![ 修正 ](../assets/fix.svg) 固定 Web サイトレベルの特別価格。
![ 修正 ](../assets/fix.svg) 処理されるすべてのフィードに mutex が追加されました。


## 103.2.2 リリース

![ 修正 ](../assets/fix.svg) 大規模なカタログのフィードのバッチ化戦略を改善しました。 メモリの使用量を減らすために、バッチ表に入力される ID の数が制限されるようになりました。

![ 修正 ](../assets/fix.svg) MSI モジュールへの CommerceInventoryDataExporter のハード依存関係を解消しました。

![ 修正 ](../assets/fix.svg) より多くの情報を収集し、様々な書き出しステージで整理するように、`commerce-data-exporter` ログが改善されました。

## 103.2.1 リリース

- リリースされている更新バージョン。

## 103.2.0 リリース

- 製品と価格のマルチスレッドデータ同期を追加しました。
