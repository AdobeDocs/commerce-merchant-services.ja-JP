---
title: '"インストール [!DNL Live Search]“'
description: 「インストール、更新、アンインストール方法を説明します [!DNL Live Search] Adobe Commerceから」
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: 8a98e069cd9ec3d2c4fec33485e5c8186d94518f
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 0%

---

# インストール [!DNL Live Search]

[!DNL Live Search] は、Adobeの Marketplace から拡張機能としてインストールされます。 後 [!DNL Live Search] モジュール（依存関係としてカタログモジュールを使用）がインストールおよび設定されている。 [!DNL Commerce] 検索およびカタログ データの SaaS サービスとの共有を開始します。 この時点で、 *Admin* ユーザーは、検索ファセット、同義語およびマーチャンダイジングルールを設定、カスタマイズおよび管理できます。

このトピックでは、次の操作を行う手順を説明します。

* インストール [!DNL Live Search] （方法 1 および 2）
* [更新 [!DNL Live Search]](#update)
* [Uninstall [!DNL Live Search]](#uninstall)

## 始める前に {#before-you-begin}

次の手順を実行します。

1. を確認します。 [cron ジョブ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) および [インデクサー](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 実行中です。

1. 要件を満たすオンボーディング方法を選択し、手順に従います。

   * [方法 1](#method-1)：なしでインストールする [!DNL OpenSearch]
   * [方法 2](#method-2)：でののインストール [!DNL OpenSearch] （ダウンタイムなし）

>[!IMPORTANT]
>
>2023 年 8 月のElasticsearch 7 のサポート終了のお知らせに伴い、Adobe Commerceのお客様はすべて OpenSearch 2.x 検索エンジンに移行することをお勧めします。 製品のアップグレード中に検索エンジンを移行する方法については、を参照してください。 [OpenSearch への移行](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) が含まれる _アップグレードガイド_.

## 方法 1:OpenSearch なしでインストールする {#method-1}

インストールする場合は、このオンボーディング方法をお勧めします [!DNL Live Search] コピー先：

* 新規 [!DNL Commerce] インストール
* ステージング環境

このシナリオでは、次の期間、ストアフロントの操作が中断されます [!DNL Live Search] サービスは、カタログ内のすべての製品にインデックスを作成します。 インストール中、 [!DNL Live Search] モジュールが有効になり、 [!DNL OpenSearch] モジュールが無効になっています。

1. 以下なしでAdobe Commerce 2.4.4 以降をインストール [!DNL Live Search].

1. をダウンロードします `live-search` パッケージを作成し、コマンドラインから次のコマンドを実行します。

   ```bash
   composer require magento/live-search
   ```

1. 次のコマンドを実行して無効にします。 [!DNL OpenSearch] および関連モジュールとインストール [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > データのインデックスが作成され同期されている間は、ストアフロントで検索およびカテゴリの参照操作を使用できません。 カタログのサイズによっては、このプロセスは時間から少なくとも 1 時間かかる場合があります `cron` を実行してデータをに同期 [!DNL Live Search] サービス。

1. 次のことを確認します [インデクサー](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) は「スケジュールに従って更新」に設定されています。

   * 製品フィード
   * 製品バリアントフィード
   * カタログ属性フィード
   * 製品価格フィード
   * Scopes Web サイトデータフィード
   * 範囲顧客グループデータフィード
   * カテゴリフィード
   * カテゴリ権限フィード

1. の設定 [API キー](#configure-api-keys) カタログ データがであることを確認 [同期](#synchronize-catalog-data) （を使用） [!DNL Live Search] サービス。

1. ファセットをストアフロントでフィルターとして使用できるようにするには、 [ファセット](facets-add.md) に応じて、必要になります [ファセット要件](facets.md).

   次の後に、ファセットを追加できます `cron` 属性フィードを実行し、属性メタデータを書き出します。

1. 次のコマンドをこの順序で実行します。

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

1. [検証](#verify-export) データが書き出されたことを示します。

1. [テスト](#test-the-connection) ストアフロントからの接続。

## 方法 2:OpenSearch によるインストール {#method-2}

インストールする場合は、このオンボーディング方法をお勧めします [!DNL Live Search] コピー先：

* 既存の実稼働環境 [!DNL Commerce] インストール

このシナリオでは、 [!DNL OpenSearch] は、次の期間、ストアフロントからの検索リクエストを一時的に管理します [!DNL Live Search] サービスは、通常のストアフロント操作を中断することなく、バックグラウンドですべての製品にインデックスを作成します。 [!DNL OpenSearch] が無効 [!DNL Live Search] すべてのカタログデータのインデックス作成と同期が完了すると、有効になります。

1. をダウンロードします `live-search` パッケージを作成し、コマンドラインから次のコマンドを実行します。

   ```bash
   composer require magento/live-search
   ```

1. 次のコマンドを実行して、 [!DNL Live Search] ストアフロントの検索結果を提供するモジュール。

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] は、が次の期間、ストアフロントからの検索リクエストを引き続き管理します [!DNL Live Search] サービスは、カタログデータを同期し、バックグラウンドで製品のインデックスを作成します。

1. 次のことを確認します [インデクサー](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) は「スケジュールに従って更新」に設定されています。

   * 製品フィード
   * 製品バリアントフィード
   * カタログ属性フィード
   * 製品価格フィード
   * スコープ web サイト データ フィード
   * 範囲顧客グループデータフィード

1. の設定 [API キー](#configure-api-keys) カタログ データがであることを確認 [同期](#synchronize-catalog-data) （を使用） [!DNL Live Search] サービス。

1. ファセットをストアフロントでフィルターとして使用できるようにするには、 [ファセット](facets-add.md) に応じて、必要になります [ファセット要件](facets.md).

   次の後に、ファセットを追加できます `cron` 製品および属性フィードを実行し、属性メタデータをに書き出します。 [!DNL Live Search] サービス。

1. 次のコマンドをこの順序で実行します。

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

1. 同期が完了したら、 [GraphQL遊び場](https://developer.adobe.com/commerce/services/graphql/live-search/) デフォルトのクエリを使用して、次の点を確認します。

   * 返される製品数は、ストア表示で期待される数に近くなります。
   * ファセットが返されます。

1. 次のコマンドを実行して以下を有効にします [!DNL Live Search] モジュール，無効にする [!DNL OpenSearch]、および実行 `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover  Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

1. [テスト](#test-the-connection) ストアフロントからの接続。

## API キーの設定 {#configure-api-keys}

接続するには、Adobe Commerce API キーとそれに関連する秘密鍵が必要です [!DNL Live Search] からAdobe Commerceのインストールに移動します。 API キーが生成され、のアカウントで管理されます [!DNL Commerce] 開発者または SI と共有できるライセンス所有者。 その後、開発者は、ライセンス所有者に代わって SaaS データスペースを作成および管理できます。  既に一連の API キーがある場合は、それらを再生成する必要はありません。

### Adobe Commerceのライセンス所有者

API キーと秘密鍵を生成するには、を参照してください。 [Commerce サービスコネクタ](../landing/saas.md).

### Adobe Commerce開発者または SI

開発者または SI は、の説明に従って SaaS データ空間を設定します。 *Commerce サービス* 設定の「」セクション。 が含まれる *Admin*&#x200B;でCommerce サービスが使用できるようになります。 *設定* saaS モジュールがインストールされている場合のサイドバー。

## カタログデータの同期 {#synchronize-catalog-data}

[!DNL Live Search] 検索操作には同期された製品データが必要で、ファセットを設定するには同期された属性データが必要です。 製品カタログとカタログサービス間の初期同期は、次の場合に開始されます [!DNL Live Search] が最初に接続されました。 インストール方法とカタログのサイズによっては、データが書き出され、によってインデックスが作成されるまで、最大 30 分かかる場合があります [!DNL Live Search]. カタログサービスと同期および共有されるデータのリストは、スキーマにあります。このスキーマは、次で定義されます。

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

の使用 [データ管理ダッシュボード](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) Commerce データベースからCommerce SaaS サービスに転送される商品データの同期ステータスをモニタリングします。

### 書き出しを検証 {#verify-export}

カタログデータがAdobe Commerce インスタンスから書き出され、用に同期されていることを確認するには [!DNL Live Search]で、次のテーブルのエントリを探します。

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

その他のヘルプについては、を参照してください。 [[!DNL Live Search] カタログが同期されていません](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) サポートナレッジベース

### 今後の製品アップデート

初回同期後、製品の増分更新がストアフロント検索で使用できるようになるまで最大 15 分かかる場合があります。 詳細については、次を参照してください： [インデックス作成 – ストリーミング製品の更新](indexing.md).

## 接続のテスト {#test-connection}

ストアフロントで、次の点を確認します。

* この [!UICONTROL Search] box は正しく結果を返します
* カテゴリの参照で結果が正しく返される
* ファセットは、検索結果ページでフィルターとして使用できます

すべてが正しく機能している場合は、おめでとうございます。 [!DNL Live Search] がインストールされ、接続され、使用できる状態である。

ストアフロントで問題が発生した場合は、 `var/log/system.log` api 通信エラーまたはサービス側のエラーのファイル。

ファイアウォールを介した Live Search を許可するには、次を追加します `commerce.adobe.io` を許可リストに追加します。

## インストールされているバージョンの確認

Live Search を更新する前に、コマンドラインから次のコマンドを実行して、インストールされている Live Search のバージョンを確認します。

```bash
composer show magento/module-live-search | grep version
```

## 更新中 [!DNL Live Search] {#update}

更新対象 [!DNL Live Search]コマンドラインから次を実行します。

```bash
composer update magento/live-search --with-dependencies
```

3.1.1 から 4.0.0 などのメジャーバージョンに更新するには、プロジェクトのルートを編集します [!DNL Composer] `.json` ファイルの内容は次のとおりです。

1. 現在インストールされているかどうか `magento/live-search` バージョン : `3.1.1` またはの下で、をバージョンにアップグレードしています `4.0.0` またはそれ以降の場合は、アップグレードの前に次のコマンドを実行します。

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   現在インストールされているに関する情報 `magento/live-search` バージョンで、次のコマンドを実行します。

   ```bash
   composer show magento/live-search
   ```

1. ルートを開きます `composer.json` ファイルでの検索 `magento/live-search`.

1. が含まれる `require` セクションで、次のようにバージョン番号を更新します。

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. **保存** `composer.json`. コマンドラインから次のコマンドを実行します。

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## アンインストール [!DNL Live Search] {#uninstall}

アンインストールするには [!DNL Live Search]を参照してください。 [モジュールのアンインストール](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] パッケージ {#packages}

| パッケージ | 説明 |
|--- |--- |
| `module-live-search` | を使用すると、マーチャントは、ファセット、同義語、クエリルールなどの検索設定を指定したり、読み取り専用のGraphQL プレイグラウンドにアクセスしてクエリをテストしたりできます。 *Admin*. |
| `module-live-search-adapter` | ストアフロントから次の場所に検索リクエストをルーティングします： [!DNL Live Search] 結果をサービスし、ストアフロントでレンダリングします。 <br />- カテゴリの参照 – ストアフロントからリクエストをルーティングします [上部ナビゲーション](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) を検索サービスに追加します。<br />- グローバル検索 – フォルダーからのリクエストをルーティングします [クイック検索](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) ～の店舗の右上にある箱 [!DNL Live Search] サービス。 |
| `module-live-search-storefront-popover` | 「入力中に検索」ポップオーバーは、標準のクイック検索に代わるもので、上位の検索結果のデータとサムネールを返します。 |

## [!DNL Live Search] dependencies {#dependencies}

次の [!DNL Live Search] 依存関係は次によってキャプチャされます。 [!DNL Composer].

* `magento/module-saas-catalog`
* `magento/module-saas-category`
* `magento/module-saas-category-permissions`
* `magento/module-saas-product-override`
* `magento/module-saas-product-variant`
* `magento/module-saas-price`
* `magento/module-saas-scopes`
* `magento/module-bundle-product-data-exporter`
* `magento/module-catalog-inventory-data-exporter`
* `magento/module-catalog-url-rewrite-data-exporter`
* `magento/module-configurable-product-data-exporter`
* `magento/module-parent-product-data-exporter`
* `magento/module-gift-card-product-data-exporter`
* `magento/module-bundle-product-override-data-exporter`
* `data-services`
* `services-id`
