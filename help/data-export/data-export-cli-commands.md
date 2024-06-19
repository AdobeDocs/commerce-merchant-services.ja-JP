---
title: SaaS データ書き出しコマンドライン インターフェイス
description: コマンドラインインターフェイスコマンドを使用して、のフィードとプロセスを管理する方法を説明します [!DNL data export extension] （Adobe Commerce SaaS サービスの場合）
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---

# SaaS データ書き出しコマンドライン インターフェイス リファレンス

開発者およびシステム管理者は、を使用して、SaaS データ書き出しの同期操作を管理できます [Adobe Commerce コマンドラインツール](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) （CLI）。 この `saas:resync` コマンドはに含まれています `magento/saas-export` パッケージ。

Adobeは、 `saas:resync` 定期的にコマンドを実行します。 コマンドを使用する一般的なシナリオは次のとおりです。

- 初期同期
- この [SaaS データ空間 ID](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) が変更されたため、新しいデータ空間にデータを同期する必要があります。
- トラブルシューティング

## 初期同期

をトリガーすると、 `saas:resync` コマンドラインでは、カタログのサイズに応じて、データの更新に数分から数時間かかる場合があります。

>[!NOTE]
>Live Search または Product Recommendationsを使用している場合は、同期を開始する必要はありません。 サービスをCommerce インスタンスに接続すると、プロセスが自動的に開始されます。

## コマンドの例

使用前に `saas:resync` コマンド、を確認する [オプションの説明](#command-options).

- エンティティフィードの完全再同期を実行します。

  ```
  bin/magento saas:resync --feed='<FEED_NAME>' 1
  ```

  既に正常に書き出されたフィードは再同期されません。

- 指定したフィードとクリーンアップのデータを完全に再同期する

  ```
  bin/magento saas:resync --feed='FEED_NAME' --cleanup-feed
  ```

  を実行した後にのみ使用します。 [!DNL Data Space ID Cleanup] 操作。

- すぐにエクスポートフィードを使用するには、フィードテーブルのインデックスデータを切り捨てずに、接続されたCommerce サービスにすべてのデータを再送信します

  ```
   bin/magento saas:resync --feed='FEED_NAME' --no-reindex
  ```

- 使用可能なコマンドおよびオプションと説明を一覧表示します。

  ```
  bin/magento saas:resync --help
  ```

## コマンドオプション

管理には次のオプションを使用できます `saas:resync` の操作。

>[!NOTE]
>
>この `saas:resync` また、コマンドは、バッチサイズを増やし、マルチスレッド処理を追加して、データの書き出しコマンドを改善する高度なオプションもサポートします。 参照： [エクスポート処理のカスタマイズ](customize-export-processing.md).

### `feed`

この必須オプションは、次のような、再同期するフィードエンティティを指定します `products`.

この `feed` オプションの値には、使用可能なエンティティフィードを含めることができます。

- `products`：製品データフィード
- `productAttributes`：製品属性データフィード
- `categories`：カテゴリデータフィード
- `variants`：設定可能な製品バリエーションデータフィード
- `prices`：製品価格データフィード
- `categoryPermissions`：カテゴリ権限データフィード
- `productOverrides`：製品権限データフィード
- `inventoryStockStatus`：在庫状況データフィード
- `scopesWebsite`：ストアおよびストアビューのデータフィードを使用する web サイト
- `scopesCustomerGroup`：顧客グループデータフィード
- `orders`：受注データフィード

対象 [Commerce サービス](../landing/saas.md) がインストールされている場合は、で使用できるフィードのセットが異なる可能性があります `saas:resync` コマンド。

### `no-reindex`

このオプションは、既存のカタログ データをに再送信します [!DNL Commerce Services] のインデックスが再作成されることはありません。 このオプションを指定しない場合、コマンドはデータを同期する前に完全な再インデックスを実行します。

このオプションの動作は、フィードがで書き出されるかどうかによって異なります [レガシーまたは即時エクスポートモード](data-synchronization.md#synchronization-modes)

- 従来のエクスポートフィードの場合、同期処理では、フィードテーブル内のインデックス付きデータは切り捨てられません。 代わりに、すべてのデータをAdobe Commerce サービスに再送信します。
- 即時エクスポートフィードの場合、このオプションは指定されている場合は無視されます。 これらのフィードの場合、再同期プロセスではインデックスが切り捨てられず、以前に失敗した更新や項目のみが再同期されます。

### `cleanup`

このオプションは、同期前にフィードインデクサーテーブルをクリーンアップします。 指定した場合、SaaS データの書き出しにより、指定したフィードの完全再同期が実行され、フィード テーブル内の既存のデータがすべてクリーンアップされます。

Adobeでは、 [!DNL Data Space ID Cleanup] 操作。

>[!WARNING]
>
>**このオプションを定期的に使用しない**. Adobe Commerce サービスでデータ同期の問題が発生する可能性があります。 例： `delete product event` 次の場合、Adobe Commerce サービスには反映されない可能性があります `cleanup` オプションが使用されます。

## トラブルシューティング

接続されたCommerce サービスに期待されるデータが表示されない場合は、データの書き出しのエラーログを確認し、を使用して、問題のトラブルシューティングを行います `saas:resync` ペイロードとプロファイラーのデータを確認するために、環境変数を指定してコマンドを実行します。 参照： [ログの確認とトラブルシューティング](troubleshooting-logging.md).
