---
title: カタログ同期
description: から製品データを書き出す方法を説明します。 [!DNL Commerce] サーバーから [!DNL Commerce Services] サービスを最新の状態に保つための継続的なベースで。
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalogs, Data Import/Export, Catalog Service
source-git-commit: d803cd9c78ac8c5529eadf39f361d7e46045359e
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# カタログ同期

Adobe CommerceおよびMagento Open Sourceは、インデクサーを使用してカタログデータをテーブルにコンパイルします。 プロセスは、次を通じて自動的にトリガーされます： [イベント](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) 製品価格や在庫レベルの変更など。

カタログの同期プロセスは 1 時間ごとに実行され、 [!DNL Commerce] カタログデータを使用するサービス。 カタログ同期では、 [!DNL Commerce] サーバーから [!DNL Commerce] サービスを継続的に更新し、サービスを最新の状態に保ちます。 例： [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) では、現在のカタログ情報が必要で、正しい名前、価格、可用性を使用してレコメンデーションを正確に返すことができます。 以下を使用すると、 _カタログ同期_ 同期プロセスを監視および管理するためのダッシュボード [コマンドラインインターフェイス](#resynccmdline) を使用して、カタログの同期と製品データのインデックス再作成を行います。 [!DNL Commerce] サービス。

>[!NOTE]
>
> 次の手順で _カタログ同期_ ダッシュボードまたはコマンドラインインターフェイスには、 [API キーと SaaS データ領域の設定](saas.md).

## カタログ同期ダッシュボードへのアクセス

>[!NOTE]
>
> The _カタログ同期_ ダッシュボードは、 _製品Recommendations_ モジュールがインストールされ、その機能に関連するデータ投影のみを反映します。 などの他のコマースサービスのサポート _ライブ検索_ および _カタログサービス_ は将来の予定です。

カタログ同期ダッシュボードにアクセスするには、「 **システム** > _データ転送_ > **カタログ同期**.

を使用 **カタログ同期** ダッシュボードでは、次の操作を実行できます。

- 同期ステータスを表示 (**処理中**, **成功**, **失敗**)
- 同期された製品の合計数を表示します（成功した場合）
- 同期した製品を検索して現在の状態を表示
- 名前、SKU などでストアカタログを検索
- 同期された製品の詳細を JSON で表示して、同期の不一致を診断するのに役立ちます
- 同期プロセスを再開します

### 前回の同期

次の同期ステータスを報告します。

- **成功**  — 同期が成功した日時と更新された製品数を表示
- **失敗**  — 同期が試行された日時を表示
- **処理中**  — 最後に同期が成功した日時を表示します

>[!NOTE]
>
> カタログ同期プロセスは、1 時間ごとに自動的に実行されます。 ただし、ストアフロントに製品が表示されていない場合や、製品に最近の変更が反映されていない場合は、解決できます [カタログ同期の問題](#resolvesync).

### 同期された製品

から同期された製品の合計数が表示されます [!DNL Commerce] カタログ。 初回同期後は、変更された製品のみが同期されます。

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
| タイプ | 製品タイプを識別します（シンプル、設定可能、ダウンロードなど）。 |
| 最後のエクスポート | 商品がカタログから最後に正常に書き出された日付 |
| 最終変更日 | カタログで商品が最後に変更された日付 |
| SKU | 製品の在庫管理単位を表示します |
| 価格 | 製品の価格 |
| 表示 | で定義されている製品の表示設定 [!DNL Commerce] カタログ |

## カタログ同期の問題を解決 {#resolvesync}

データの再同期をトリガーする際、データが更新されて UI コンポーネント（レコメンデーション単位など）に反映されるまでに最大 1 時間かかる場合があります。 ただし、1 時間待った後でも、カタログとストアフロントに表示される内容に食い違いが生じる場合や、カタログの同期に失敗した場合は、次を参照してください。

### データの不一致

1. 該当する製品の詳細ビューを検索結果に表示します。
1. JSON 出力をコピーし、コンテンツが [!DNL Commerce] カタログ。
1. コンテンツが一致しない場合は、スペースやピリオドの追加など、カタログ内の製品に小さな変更を加えます。
1. 再同期を待つか、 [トリガーの手動再同期](#resync).

### 同期が実行されていません

同期がスケジュールに従って実行されていない場合、または何も同期されていない場合は、 [KnowledgeBase](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html).

### 同期に失敗しました

カタログ同期のステータスが **失敗**、送信 [サポートチケット](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## コマンドラインインターフェイス {#resynccmdline}

The `saas:resync` コマンドは、 `magento/saas-export` パッケージ。 このパッケージは、 [!DNL Commerce Services] 製品 ( 例： [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) または [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> データ同期を初めて実行する場合は、 `productattributes` 最初にフィードを開き、次に `productoverrides`、実行前 `products` フィード。

コマンドオプション：

```bash
bin/magento saas:resync --feed <feed name> [no-reindex]
```

次の表に、 `saas:resync` パラメーターと説明。

| パラメーター | 説明 | 必須？ |
|---| ---| ---|
| `feed` | 再同期するエンティティを指定します。例： `products` | はい |
| `no-reindex` | 既存のカタログデータをに再送信します [!DNL Commerce Services] インデックスを再作成せずに このパラメーターを指定しない場合、コマンドはデータを同期する前に完全な再インデックスを実行します。 | いいえ |

フィード名は、次のいずれかになります。

- `products` — カタログ内の製品
- `categories` — カタログ内のカテゴリ
- `variants` — 色やサイズなど、設定可能な製品の製品バリエーション。
- `productattributes` — 製品属性（例： ） `activity`, `gender`, `tops`, `bottoms`など
- `productoverrides` — カテゴリ権限に基づく価格やカタログ表示ルールなど、お客様固有の価格やカタログ表示ルール

コマンドラインからデータの再同期をトリガーする場合、データが更新されるまで最大 1 時間かかる場合があります。

を使用している場合、 [SaaS 価格のインデックス作成](../price-index/index.md) 再同期が必要な場合は、次のコマンドを実行します。

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

### 例

次の例では、 [!DNL Commerce] カタログを作成し、コマースサービスに再同期します。

```bash
bin/magento saas:resync --feed products
```

製品の完全なインデックス再作成を実行したくない場合は、代わりに、既に生成されている製品データを同期できます。

```bash
bin/magento saas:resync --feed products --no-reindex
```
