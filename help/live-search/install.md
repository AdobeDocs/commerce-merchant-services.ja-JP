---
title: "インストール [!DNL Live Search]"
description: インストール、更新、アンインストールの方法を学ぶ [!DNL Live Search] Adobe Commerceから」
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: e8d4215b1f16f1cb34783674cabc046dec135729
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 0%

---

# インストール [!DNL Live Search]

[!DNL Live Search] は、Marketplace の拡張機能としてAdobeされます。 次の期間の後に [!DNL Live Search] モジュール（カタログモジュールを依存関係として使用）がインストールされ、設定されます。 [!DNL Commerce] は、SaaS サービスとの検索およびカタログデータの共有を開始します。 この時点で *管理者* ユーザーは、検索ファセット、シノニムおよびマーチャンダイジングルールを設定、カスタマイズおよび管理できます。

このトピックでは、次の操作の手順を説明します。

* インストール [!DNL Live Search] （方法 1 及び 2）
* [更新 [!DNL Live Search]](#update)
* [アンインストール [!DNL Live Search]](#uninstall)

## 始める前に {#before-you-begin}

次の操作を実行します。

1. 確認 [cron ジョブ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) および [インデクサー](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) が実行中です。

1. 要件を満たすオンボーディング方法を選択し、指示に従います。

   * [方法 1](#method-1)：を使用せずにインストール [!DNL OpenSearch]
   * [方法 2](#method-2)：を使用してインストール [!DNL OpenSearch] （ダウンタイムなし）

>[!IMPORTANT]
>
>2023 年 8 月のElasticsearch7 のサポート終了のお知らせにより、すべてのAdobe Commerceのお客様は OpenSearch 2.x 検索エンジンに移行することをお勧めします。 製品のアップグレード中に検索エンジンを移行する方法については、 [OpenSearch への移行](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) （内） _アップグレードガイド_.

## 方法 1:OpenSearch を使用せずにインストールする {#method-1}

このオンボーディング方法は、 [!DNL Live Search] からに変更します。

* 新規 [!DNL Commerce] インストール
* ステージング環境

このシナリオでは、ストアフロント操作は、 [!DNL Live Search] サービスは、カタログ内のすべての製品のインデックスを作成します。 インストール時に、 [!DNL Live Search] モジュールが有効になり、 [!DNL OpenSearch] モジュールが無効になっています。

1. 次を使用せずにAdobe Commerce 2.4.4 以降をインストールする [!DNL Live Search].

1. 次の手順で `live-search` package で、コマンドラインから次のコマンドを実行します。

   ```bash
   composer require magento/live-search
   ```

1. 次のコマンドを実行して無効にします。 [!DNL OpenSearch] および関連するモジュール、およびインストール [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > データのインデックスが作成され、同期されている間は、検索およびカテゴリの参照操作はストアフロントで使用できません。 カタログのサイズによっては、プロセスに少なくとも 1 時間かかる場合があります。 `cron` データの同期先として実行 [!DNL Live Search] サービス。

1. 次の点を確認します。 [インデクサー](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) が「スケジュールに従って更新」に設定されている場合：

   * 製品フィード
   * 製品バリアントフィード
   * カタログ属性フィード
   * 製品価格フィード
   * スコープの Web サイトデータフィード
   * スコープの顧客グループデータフィード
   * カテゴリフィード
   * カテゴリ権限フィード

1. を設定します。 [API キー](#configure-api-keys) カタログデータが [同期済み](#synchronize-catalog-data) 次を使用 [!DNL Live Search] サービス。

1. ストアフロントでファセットをフィルターとして使用できるようにするには、 [ファセット](facets-add.md) 以下の通り必要です。 [ファセット要件](facets.md).

   の後にファセットを追加できます。 `cron` 属性フィードを実行し、属性メタデータを書き出します。

1. 次のコマンドを次の順序で実行します。

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

1. [検証](#verify-export) データがエクスポートされた。

1. [テスト](#test-the-connection) ストアフロントからの接続。

## 方法 2:OpenSearch を使用してインストールする {#method-2}

このオンボーディング方法は、 [!DNL Live Search] 移動先：

* 既存の実稼動 [!DNL Commerce] インストール

このシナリオでは、 [!DNL OpenSearch] ストアフロントからの検索リクエストを一時的に管理し、 [!DNL Live Search] サービスは、通常のストアフロント操作を中断することなく、バックグラウンドですべての製品のインデックスを作成します。 [!DNL OpenSearch] が無効で、 [!DNL Live Search] すべてのカタログデータのインデックスが作成され、同期された後に有効になります。

1. 次の手順で `live-search` package で、コマンドラインから次のコマンドを実行します。

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

   [!DNL Elasticsearch] はストアフロントから検索リクエストを引き続き管理し、 [!DNL Live Search] サービスは、カタログデータを同期し、製品のインデックスをバックグラウンドで作成します。

1. 次の点を確認します。 [インデクサー](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) が「スケジュールに従って更新」に設定されている場合：

   * 製品フィード
   * 製品バリアントフィード
   * カタログ属性フィード
   * 製品価格フィード
   * スコープの Web サイトデータフィード
   * スコープの顧客グループデータフィード

1. を設定します。 [API キー](#configure-api-keys) カタログデータが [同期済み](#synchronize-catalog-data) 次を使用 [!DNL Live Search] サービス。

1. ストアフロントでファセットをフィルターとして使用できるようにするには、 [ファセット](facets-add.md) 以下の通り必要です。 [ファセット要件](facets.md).

   の後にファセットを追加できます。 `cron` 製品および属性フィードを実行し、属性メタデータをに書き出します。 [!DNL Live Search] サービス。

1. 次のコマンドを次の順序で実行します。

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

1. 同期が完了したら、 [GraphQLプレイグラウンド](https://developer.adobe.com/commerce/services/graphql/live-search/) をデフォルトのクエリに置き換えて、以下を検証します。

   * 返される製品数は、ストア表示で期待される数に近い数です。
   * ファセットが返されます。

1. 次のコマンドを実行してを有効にします。 [!DNL Live Search] モジュール、無効 [!DNL OpenSearch]、およびを実行します。 `setup`.

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

接続するには、Adobe Commerce API キーと、それに関連する秘密鍵が必要です [!DNL Live Search] をAdobe Commerceのインストールに追加します。 API キーは、 [!DNL Commerce] 開発者または SI と共有できるライセンス所有者。 開発者は、ライセンス所有者に代わって SaaS データスペースを作成および管理できます。  既に API キーのセットがある場合は、それらを再生成する必要はありません。

### Adobe Commerceライセンス保持者

API キーと秘密鍵の生成については、 [Commerce Services コネクタ](../landing/saas.md).

### Adobe Commerce開発者または SI

開発者または SI は、 *コマースサービス* 」セクションに含まれています。 Adobe Analytics の *管理者*&#x200B;に設定されている場合、Commerce Services は *設定* SaaS モジュールがインストールされている場合にサイドバーが表示されます。

## カタログデータを同期 {#synchronize-catalog-data}

[!DNL Live Search] では、検索操作用に同期された製品データが必要です。ファセットを設定するには、同期された属性データが必要です。 製品カタログとカタログサービス間の初期同期は、次の時点で開始されます。 [!DNL Live Search] は最初に接続されます。 カタログのインストール方法とサイズに応じて、データの書き出しとインデックス作成に最大 30 分かかる場合があります。 [!DNL Live Search]. カタログサービスと同期および共有されるデータのリストは、次の場所で定義されているスキーマ内にあります。

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### 書き出しを検証 {#verify-export}

カタログデータがAdobe Commerceインスタンスから書き出され、次の項目と同期されていることを確認するには： [!DNL Live Search]次の表のエントリを探します。

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

その他のヘルプについては、 [[!DNL Live Search] カタログが同期されていません](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) 」を参照してください。

### 今後の製品アップデート

最初の同期の後、製品の増分更新がストアフロント検索で使用できるようになるまで、最大 15 分かかる場合があります。 詳しくは、 [インデックス作成 — 製品アップデートのストリーミング](indexing.md).

## 接続をテストする {#test-connection}

ストアフロントで、以下を確認します。

* The [!UICONTROL Search] ボックスが正しく結果を返す
* カテゴリの参照によって結果が正しく返される
* ファセットは、検索結果ページのフィルターとして使用できます

すべてが正しく動作する場合は、おめでとうございます。 [!DNL Live Search] がインストールされ、接続され、使用できる状態になっている。

ストアフロントで問題が発生した場合は、 `var/log/system.log` ファイルに保存され、API 通信の失敗やサービス側でのエラーに関する情報が含まれます。

ファイアウォールを介したライブ検索を許可するには、 `commerce.adobe.io` 許可リストに

## インストールされているバージョンの確認

ライブ検索を更新する前に、コマンドラインから次のコマンドを実行して、インストールされているライブ検索のバージョンを確認します。

```bash
composer show magento/module-live-search | grep version
```

## 更新中 [!DNL Live Search] {#update}

更新するには [!DNL Live Search]のコマンドラインで、次のコマンドを実行します。

```bash
composer update magento/live-search --with-dependencies
```

3.1.1 から 4.0.0 のようなメジャーバージョンに更新するには、プロジェクトのルートを編集します。 [!DNL Composer] `.json` ファイルの内容は次のとおりです。

1. 現在 `magento/live-search` のバージョンが `3.1.1` または以下のバージョンにアップグレードしている `4.0.0` 以降の場合は、アップグレードの前に次のコマンドを実行します。

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   現在インストールされている `magento/live-search` バージョンの場合は、次のコマンドを実行します。

   ```bash
   composer show magento/live-search
   ```

1. ルートを開く `composer.json` ファイルと検索 `magento/live-search`.

1. Adobe Analytics の `require` 「 」セクションで、次のようにバージョン番号を更新します。

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. **保存** `composer.json`. 次に、コマンドラインから次の操作を実行します。

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## アンインストール [!DNL Live Search] {#uninstall}

アンインストールするには [!DNL Live Search]（を参照）。 [モジュールのアンインストール](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] パッケージ {#packages}

| パッケージ | 説明 |
|--- |--- |
| `module-live-search` | マーチャントがファセット設定、シノニム、クエリルールなどの検索設定を行えるようにし、読み取り専用のGraphQLプレイグラウンドにアクセスして、 *管理者*. |
| `module-live-search-adapter` | ストアフロントからにリクエストをルーティングします [!DNL Live Search] 結果がストアフロントに表示されます。 <br /> — カテゴリ参照 — ストアフロントからリクエストをルーティングします。 [上部ナビゲーション](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) を検索サービスに追加します。<br /> — グローバル検索 — リクエストを [クイック検索](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) 店頭の右上にある箱 [!DNL Live Search] サービス。 |
| `module-live-search-storefront-popover` | 「入力に応じて検索」ポップオーバーは、標準のクイック検索に代わり、上位の検索結果のデータとサムネールを返します。 |

## [!DNL Live Search] 依存関係 {#dependencies}

次の [!DNL Live Search] 依存関係は次の方法でキャプチャされます。 [!DNL Composer].

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
