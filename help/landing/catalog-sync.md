---
title: カタログ同期
description: から製品データを書き出す方法を学ぶ [!DNL Commerce] サーバー先 [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: 7d62f8d5539cd744e98d8d6c072d77a2a7c5a256
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 0%

---


# カタログ同期

>[!NOTE]
>
> カタログ同期ダッシュボードが、データ管理ダッシュボードになりました。 この改善されたダッシュボードは、をサポートするようになりました [[!DNL Product Recommendations]](../product-recommendations/guide-overview.md), [[!DNL Live Search]](../live-search/overview.md)、および [[!DNL Catalog Service]](../catalog-service/overview.md). お客様は、これらのサービスのいずれかの最新バージョンに更新することで、データ管理ダッシュボードを取得できます。 詳しくは、を参照してください。 [データ管理ダッシュボード](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) ドキュメント。 この現在のトピックは、まだアップグレードしておらず、カタログ同期ダッシュボードを使用しているユーザー向けです。

Adobe Commerceはインデクサーを使用して、カタログデータをテーブルにコンパイルします。 プロセスは、次のユーザーによって自動的にトリガーされます [イベント](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) 製品価格や在庫レベルの変更など。

カタログ同期サービスは、以下から製品データを移動します [!DNL Adobe Commerce] インスタンスからへ [!DNL Commerce Services] 継続的にプラットフォームを構築し、データを最新の状態に保ちます。 例： [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) 現在のカタログ情報を使用して、正確な名前、価格、在庫状況でレコメンデーションを正確に返す必要があります。 の使用 _カタログ同期_ 同期プロセスを監視および管理するダッシュボード [コマンドラインインターフェイス](#resynccmdline) カタログ同期をトリガーし、次の方法で使用するために商品データを再インデックス化する [!DNL Commerce Services].

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

データの再同期をトリガーする場合、データが更新され、レコメンデーションユニットなどの UI コンポーネントに反映されるまで、最大 1 時間かかる場合があります。 カタログとストアフロントのデータの間にまだ不一致が表示される場合、またはカタログの同期に失敗した場合は、次を参照してください。

### データの不一致

1. 検索結果に、該当する製品の詳細ビューを表示します。
1. JSON 出力をコピーし、コンテンツが内にあるものと一致することを確認します。 [!DNL Commerce] カタログ。
1. コンテンツが一致しない場合は、スペースやピリオドの追加など、カタログの製品に小さな変更を加えます。
1. 再同期を待つか、 [手動再同期のトリガー](#resync).

### 同期が実行されていません

同期がスケジュールに従って実行されていないか、何も同期されていない場合は、こちらを参照してください [KnowledgeBase](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) 記事。

### 同期できませんでした

カタログ同期のステータスがの場合 **失敗**、送信 [サポートチケット](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## コマンドラインインターフェイス {#resynccmdline}

この `saas:resync` コマンドは、 `magento/saas-export` パッケージは、次のいずれかの方法で追加設定なしで利用できます [!DNL Commerce Services] 製品（例：） [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) または [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> データ同期を初めて実行する場合は、 `productattributes` 最初にフィードし、次にフィード `productoverrides`を実行する前に、 `products` フィード。

コマンドオプション：

```bash
bin/magento saas:resync --feed <feed name> [no-reindex|cleanup-feed]
```

以下の表で、 `saas:resync` パラメーターと説明。

| パラメーター | 説明 | 必須？ |
|---| ---| ---|
| `feed` | 次のように、再同期するエンティティを指定します `products` | はい |
| `no-reindex` | 既存のカタログ データをに再送信します [!DNL Commerce Services] のインデックスが再作成されることはありません。 このパラメーターを指定しない場合、コマンドは、データを同期する前に完全な再インデックスを実行します。 | 不可 |
| `cleanup-feed` | 同期前にフィードインデクサーテーブルをクリーンアップします。 | 不可 |

フィード名は次のいずれかになります。

- `products`— カタログ内の製品
- `productattributes` – 次のような製品属性 `activity`, `gender`, `tops`, `bottoms`など
- `variants` – 色やサイズなど、設定可能な製品の製品バリエーション
- `prices` ・製品価格について
- `scopesCustomerGroup`  – 顧客グループ
- `scopesWebsite` — ストアビューがある Web サイト
- `categories`— カタログ内のカテゴリ
- `categoryPermissions`  – 各カテゴリの権限
- `productoverrides` – カテゴリ権限に基づくものなど、顧客固有の価格およびカタログ表示ルール

対象 [Commerce サービス](../landing/saas.md) がインストールされている場合、で使用できるフィードのセットは異なる可能性があります `saas:resync` コマンド。

を実行しないことをお勧めします `saas:resync` 定期的にコマンドを実行します。 次の 2 つのシナリオでは、コマンドを手動で実行する必要がある場合があります。

- 初期同期
- この [SaaS データ空間 ID](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) が変更されました

### 初期同期

をトリガーすると、 `saas:resync` コマンドラインでは、カタログのサイズに応じて、データの更新に数分から数時間かかる場合があります。

初期同期では、次の順序でコマンドを実行することをお勧めします。

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

に期待されたデータが表示されない場合 [!DNL Commerce Service]で、同期中に問題が発生したかどうかを [!DNL Adobe Commerce] インスタンスからへ [!DNL Commerce Service] プラットフォーム。

には 2 つのログファイルがあります。 `var/log/` ディレクトリ：

- `commerce-data-export-errors.log`  – 次の期間にエラーが発生した場合： _収集_ フェーズ
- `saas-export-errors.log`  – 次の期間にエラーが発生した場合： _送信中_ フェーズ

#### フィードペイロードを確認

に送信されたフィードペイロードを確認すると役立つ場合があります。 [!DNL Commerce Service]. これは、環境変数を渡すことで実行できます `EXPORTER_EXTENDED_LOG=1`. この `no-reindex` フラグは、現在収集されているデータのみが送信されることを意味します。

```bash
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products --no-reindex
```

ペイロードはで入手できます。 `var/log/saas-export.log`.

#### フィードインデックステーブルにペイロードを保持

From の説明 `magento/module-data-exporter:103.0.0` 一部のフィード：製品フィード、価格フィードでは、インデックステーブルに必要な最小限のデータのみを保持します。

実稼動環境では、ペイロードデータをインデックステーブルに保持することは推奨されませんが、開発者インスタンスでは便利な場合があります。 これは、を渡すことによって行われます。 `PERSIST_EXPORTED_FEED=1` 環境変数：

```bash
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

#### プロファイル

特定のフィードの再インデックスプロセスに不相応な時間がかかる場合は、プロファイラーを実行して、サポートチームに役立つ追加データを収集します。 これを行うには、 `EXPORTER_PROFILER=1`環境変数：

```bash
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

プロファイラーデータはに保存されます。 `var/log/commerce-data-export.log` 次の形式を使用します。

`<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>`

#### サポートリクエストを送信

設定やサードパーティの拡張機能に関連しないエラーが表示された場合は、 [サポートチケット](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) できるだけ多くの情報を使用します。
