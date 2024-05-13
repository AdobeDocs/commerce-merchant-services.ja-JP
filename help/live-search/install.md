---
title: 「の概要 [!DNL Live Search]“
description: のシステム要件とインストール手順を説明します [!DNL Live Search] Adobe Commerceから」
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: c66eab4ae0dda9a447a17f357ee0bb7364dc46ba
workflow-type: tm+mt
source-wordcount: '2405'
ht-degree: 0%

---

# を使用した成功の設定 [!DNL Live Search]

Adobe Commerce [!DNL Live Search] および [[!DNL Catalog Service]](../catalog-service/guide-overview.md) 共同で作業して、パフォーマンスが高く関連性が高く直感的な検索ソリューションを提供することで、顧客が必要なものを正確かつ迅速に見つけられるようにします。 具体的には、 [!DNL Catalog Service] などの SaaS サービスのカタログデータを表示します [!DNL Live Search] を使用します。

この記事では、を実装する手順を説明します [!DNL Live Search] （を使用） [!DNL Catalog Service].

>[!IMPORTANT]
>
>サイト検索に関しては、Adobe Commerceのオプションが用意されています。 必ずお読みください。 [境界と制限](boundaries-limits.md) 実装する前に、以下を確認します [!DNL Live Search] は、お客様のビジネスニーズに合っています。

## オーディエンス

この記事は、Adobe Commerce インスタンスのインストールと設定を担当するデベロッパーまたはシステムインテグレーターを対象としています。

## 要件

- [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4 以降
- PHP 8.1 / 8.2 / 8.3
- [!DNL Composer]

## サポートされるプラットフォーム

- クラウド上のAdobe Commerce（ECE） :2.4.4 以降
- Adobe Commerce オンプレミス（EE） :2.4.4 以降

## ワークフローの概要

大まかなレベルでのオンボーディング [!DNL Live Search] では、次の操作が必要です。

![Live Search ワークフロー](assets/livesearch-workflow.png)

## 1.をインストールする [!DNL Live Search] 拡張子

[!DNL Live Search] は、から拡張機能としてインストールされます。 [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html) から [コンポーザー](https://getcomposer.org/). インストールおよび設定後 [!DNL Live Search]、Adobe [!DNL Commerce] 検索およびカタログ データの SaaS サービスとの共有を開始します。 この時点で、 *Admin* ユーザーは、検索ファセット、同義語およびマーチャンダイジングルールを設定、カスタマイズおよび管理できます。

>[!NOTE]
>
>現在 [!DNL Live Search] 3.0.2、 [!DNL Catalog Service] 拡張機能は、にバンドルされています [!DNL Live Search] インストール。

1. を確認します。 [cron ジョブ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) および [インデクサー](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 実行中です。

   >[!IMPORTANT]
   >
   >2023 年 8 月のElasticsearch 7 のサポート終了のお知らせに伴い、Adobe Commerceのお客様はすべて OpenSearch 2.x 検索エンジンに移行することをお勧めします。 製品のアップグレード中に検索エンジンを移行する方法については、を参照してください。 [OpenSearch への移行](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) が含まれる _アップグレードガイド_.

1. をダウンロード `live-search` パッケージを [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html).

1. コマンドラインから次を実行します。

   ```bash
   composer require magento/live-search
   ```

   を追加する場合 [!DNL Live Search] への拡張 **新規** Adobe Commerceのインストール。以下を実行して無効にします [!DNL OpenSearch] および関連モジュールとインストール [!DNL Live Search]. 次に、手順 4 に進みます。

   ```bash
      bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   を追加する場合 [!DNL Live Search] の拡張 **既存** Adobe Commerceのインストール。次のコマンドを実行して、一時的に [!DNL Live Search] ストアフロントの検索結果を提供するモジュール。 次に、手順 4 に進みます。

   ```bash
      bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   [!DNL Elasticsearch] は、が次の期間、ストアフロントからの検索リクエストを引き続き管理します [!DNL Live Search] サービスは、カタログデータを同期し、バックグラウンドで製品のインデックスを作成します。

1. 次を実行します。

   ```bash
   bin/magento setup:upgrade
   ```

1. 次のことを確認します [インデクサー](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) は「スケジュールに従って更新」に設定されています。

   - 製品フィード
   - 製品バリアントフィード
   - カタログ属性フィード
   - 製品価格フィード
   - Scopes Web サイトデータフィード
   - 範囲顧客グループデータフィード
   - カテゴリフィード
   - カテゴリ権限フィード

1. をインストールする場合 [!DNL Live Search] 新しいCommerce インスタンスでは、これで完了です。次にスキップできます [2. API キーの設定](#2-configure-api-keys) セクション。 Live Search を既存のCommerce インスタンスにインストールする場合は、次の手順に進んでください。

1. 次のコマンドを実行して、 [!DNL Live Search] 拡張機能、無効化 [!DNL OpenSearch]、および実行 `setup`.

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

## 2. API キーの設定

接続するには、Adobe Commerce API キーとそれに関連する秘密鍵が必要です [!DNL Live Search] からAdobe Commerceのインストールに移動します。 API キーが生成され、のアカウントで管理されます [!DNL Commerce] 開発者またはシステムインテグレーターとライセンスを共有できるライセンス所有者。 その後、開発者は、ライセンス所有者に代わって SaaS データスペースを作成および管理できます。 既に一連の API キーがある場合は、それらを再生成する必要はありません。

で API キーを設定する方法を説明します [Commerce サービスコネクタ](../landing/saas.md) 記事。

## 3. カタログデータを同期する {#synchronize-catalog-data}

[!DNL Live Search] カタログ データをAdobeの SaaS インフラストラクチャに移動します。 データにインデックスが作成され、検索結果はこのインデックスからストアフロントに直接配信されます。 サイズと複雑さに応じて、インデックス作成に 30 分から数時間かかる場合があります。

カタログ データを SaaS サービスに初期同期するには、次のコマンドをこの順序で実行します。

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

これらのコマンドを実行すると、カタログ データの SaaS サービスへの初期同期が開始されます。

>[!WARNING]
>
> データのインデックスが作成され同期されている間は、ストアフロントで検索およびカテゴリの参照操作を使用できません。 カタログのサイズによっては、このプロセスは時間から少なくとも 1 時間かかる場合があります `cron` を実行して、データを SaaS サービスに同期します。

### 同期の進行状況の監視

同期および共有されているデータは、 [データ管理ダッシュボード](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). このダッシュボードは、ストアフロントの製品データの可用性に関する貴重なインサイトを提供し、買い物客に迅速に表示できるようにします。

![データ管理ダッシュボード](assets/data-management-dashboard.png)

#### 今後の製品アップデート

初回同期後、製品の増分更新がストアフロント検索で使用できるようになるまで最大 15 分かかる場合があります。 詳しくは、 [インデックス作成 – ストリーミング製品の更新](indexing.md).

## 4. データが書き出されたことを確認します {#verify-export}

カタログデータがAdobe Commerce インスタンスから書き出され、用に同期されていることを確認するには [!DNL Live Search]には、次の 2 つのオプションがあります。

- 次の表のエントリを探します。

   - `catalog_data_exporter_products`
   - `catalog_data_exporter_product_attributes`

- の使用 [GraphQL遊び場](https://developer.adobe.com/commerce/services/graphql/live-search/) デフォルトのクエリを使用して、次の点を確認します。

   - 返される製品数は、ストア表示で期待される数に近くなります。
   - ファセットが返されます。

その他のヘルプについては、を参照してください [[!DNL Live Search] カタログが同期されていません](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) サポートナレッジベース

## 5. データを設定する

製品データを正しく設定すると、顧客に適した検索結果が得られます。 このセクションでは、製品リストウィジェットを有効にし、カテゴリと属性を割り当てます。

### 製品リストウィジェットの有効化

のインストール時 [!DNL Live Search] 4.0.0 以降、製品一覧表示ウィジェットはデフォルトで有効になっています。 ウィジェットを有効にすると、検索結果ページとカテゴリ参照の製品リストページで別の UI コンポーネントが使用されます。 この UI コンポーネントは、 [Catalog Service API](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/)これにより、応答時間が短縮されます。

次がある場合： [!DNL Live Search] バージョン 4.0.0 以降では、製品一覧ウィジェットを手動で有効にする必要があります。

1. から *Admin*&#x200B;に移動します。 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 次の下 **[!UICONTROL Live Search]**&#x200B;を選択 **[!UICONTROL Storefront Features]**.
1. を設定 **[!UICONTROL Enable Product Listing Widgets]** 対象： `Yes`.

   ![製品リストウィジェットの有効化](assets/ls-admin-enable-widget.png)

この設定を変更すると、メッセージ `Page cache is invalidated` 表示されます。 変更内容を保存するには、Magentoキャッシュをフラッシュする必要があります。

1. へのアクセス [キャッシュ管理](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) 次のいずれかの操作を行ってページを作成します。

   - 「」をクリックします **[!UICONTROL Cache Management]** ワークスペースの上にあるメッセージ内のリンク。
   - 日 _Admin_ サイドバー、に移動 **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Cache Management]**.

1. 「」を選択します **設定** [!UICONTROL Cache Type] をクリックして、 **[!UICONTROL Flush Magento Cache]**.

   ストアフロントに対する変更は、キャッシュをフラッシュした直後に行われます。

### カテゴリの割り当て

返品された商品 [!DNL Live Search] に割り当てなければなりません [category](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/categories). 例えば Luma では、製品が「男性」、「女性」、「歯車」などのカテゴリに分類されます。 サブカテゴリも「トップス」、「ボトムス」、「ウォッチポイント」に設定されます。 これにより、フィルタリング時の精度が向上します。

### 検索可能なフィールドとフィルタリング可能なフィールド

製品が割り当てられている [属性](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/product-attributes) 検索とフィルタリングに使用できます。 属性とは、「色」、「サイズ」、「マテリアル タイプ」などです。 これらの属性を使用すると、ユーザーは「緑のトップス」を探すことができます。 各製品には、で定義された多くの属性を持つことができます。 [!DNL Commerce] 管理者。

これらの各属性は、次のように定義できます [&quot;検索可能&quot;](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) admin. 「検索可能」に設定すると、これらの属性をで検索できます。 [!DNL Live Search].

[ファセット](facets.md) は、で定義される製品属性です。 [!DNL Live Search] フィルタリング可能。 フィルタリング可能な属性は、でファセットとして設定できます。 [!DNL Live Search] ただし、一度に検索できるファセットの数には制限があります。

[同義語](synonyms.md) は、ユーザーが正しい製品に導かれるよう定義できる用語です。 ズボンを探しているユーザーは「ズボン」や「スラックス」と入力する場合があります。 これらの検索用語で「パンツ」の結果にユーザーがアクセスできるように、同義語を設定できます。

## 6.接続をテストする {#test-connection}

カタログデータを SaaS にして、テストを行い、次のシナリオで製品データが返されることを確認します。

- この [!UICONTROL Search] box は正しく結果を返します
- カテゴリの参照で結果が正しく返される
- ファセットは、検索結果ページでフィルターとして使用できます

すべてが正しく動作する場合、 [!DNL Live Search] がインストールされ、接続され、使用できる状態である。

ストアフロントで問題が発生した場合は、 `var/log/system.log` api 通信エラーまたはサービス側のエラーのファイル。

許可する [!DNL Live Search] ファイアウォールを使用して、次を追加します `commerce.adobe.io` を許可リストに追加します。

## 7. ストアフロントに合わせたカスタマイズ

がインストールされました [!DNL Live Search] データの拡張、同期、検証、設定を行います。 次に、以下を確実にします [!DNL Live Search] ウィジェットは、ストアのルックアンドフィールに準拠しています。

ポップオーバーウィジェットと PLP ウィジェットのスタイルを設定するには、必要に応じてカスタム CSS ルールを定義します。 参照： [ポップオーバー要素のスタイル設定](storefront-popover-styling.md) および [製品一覧ページウィジェット](plp-styling.md).

ウィジェットの機能を拡張する場合は、各のソースコードを公開リポジトリで入手できます。
このシナリオでは、独自のニーズに合わせて JavaScript をカスタマイズし、カスタムコードを CDN にホストできます。 このカスタムスクリプトは、 [!DNL Live Search] サービスを実行し、通常と同様の結果を返すことで、ウィジェットの機能を制御できます。

- [PLP ウィジェットリポジトリ](https://github.com/adobe/storefront-product-listing-page)
- [検索バーのリポジトリ](https://github.com/adobe/storefront-search-as-you-type)

## 更新中 [!DNL Live Search] {#update}

Live Search を更新する前に、コマンドラインから次のコマンドを実行して、インストールされている Live Search のバージョンを確認します。

```bash
composer show magento/module-live-search | grep version
```

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

1. 保存 `composer.json`. コマンドラインから次のコマンドを実行します。

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## アンインストール [!DNL Live Search] {#uninstall}

アンインストールするには [!DNL Live Search]を参照してください。 [モジュールのアンインストール](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] パッケージ {#packages}

この [!DNL Live Search] 拡張機能は、次のパッケージで構成されます。

| パッケージ | 説明 |
|--- |--- |
| `module-live-search` | を使用すると、マーチャントは、ファセット、同義語、クエリルールなどの検索設定を指定したり、読み取り専用のGraphQL プレイグラウンドにアクセスしてクエリをテストしたりできます。 *Admin*. |
| `module-live-search-adapter` | ストアフロントから次の場所に検索リクエストをルーティングします： [!DNL Live Search] 結果をサービスし、ストアフロントでレンダリングします。 <br />- カテゴリの参照 – ストアフロントからリクエストをルーティングします [上部ナビゲーション](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) を検索サービスに追加します。<br />- グローバル検索 – フォルダーからのリクエストをルーティングします [クイック検索](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) ～の店舗の右上にある箱 [!DNL Live Search] サービス。 |
| `module-live-search-storefront-popover` | 「入力中に検索」ポップオーバーは、標準のクイック検索に代わるもので、上位の検索結果のデータとサムネールを返します。 |

## [!DNL Live Search] dependencies {#dependencies}

次の [!DNL Live Search] 依存関係は次によってキャプチャされます。 [!DNL Composer].

- `magento/module-saas-catalog`
- `magento/module-saas-category`
- `magento/module-saas-category-permissions`
- `magento/module-saas-product-override`
- `magento/module-saas-product-variant`
- `magento/module-saas-price`
- `magento/module-saas-scopes`
- `magento/module-bundle-product-data-exporter`
- `magento/module-catalog-inventory-data-exporter`
- `magento/module-catalog-url-rewrite-data-exporter`
- `magento/module-configurable-product-data-exporter`
- `magento/module-parent-product-data-exporter`
- `magento/module-gift-card-product-data-exporter`
- `magento/module-bundle-product-override-data-exporter`
- `data-services`
- `services-id`

## 高度な概念

以下のセクションでは、を使用する際の、より詳細なトピックを提供します [!DNL Live Search] および [!DNL Catalog Service].

### エンドポイント

[!DNL Live Search] エンドポイント （）を介した通信 `https://catalog-service.adobe.io/graphql`.

As [!DNL Live Search] 完全な製品データベースへのアクセス権がない [!DNL Live Search] GraphQLとCommerceのコアGraphQLには、完全な同等機能はありません。

SaaS API （特にカタログサービスエンドポイント）を直接呼び出すことをお勧めします。

- Commerce データベース/Graphql プロセスをバイパスすることで、パフォーマンスを向上させ、プロセッサー負荷を軽減します。
- を利用する [!DNL Catalog Service] 通話連合 [!DNL Live Search], [!DNL Catalog Service]、および [!DNL Product Recommendations] 単一のエンドポイントから。

一部のユースケースでは、を呼び出す方が良い場合もあります。 [!DNL Catalog Service] 製品の詳細および類似の事例について。 参照： [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) を参照してください。

カスタムのヘッドレス実装がある場合は、 [!DNL Live Search] リファレンス実装：

- [PLP ウィジェット](https://github.com/adobe/storefront-product-listing-page)
- [ライブ検索フィールド](https://github.com/adobe/storefront-search-as-you-type)

Luma の検索アダプターやウィジェット、AEM CIFウィジェットなどのデフォルトのコンポーネントを使用しない場合、イベント（インテリジェントマーチャンダイジングおよびパフォーマンス指標をAdobe Senseiにフィードするクリックストリームデータ）は初期設定では機能せず、ヘッドレスイベントを実装するにはカスタム開発が必要です。

の最新バージョン [!DNL Live Search] はすでに使用しています [!DNL Catalog Service].

### 言語サポート

[!DNL Live Search] ウィジェットは次の言語をサポートしています。

|  |  |  |  |
|--- |--- |--- |--- |
| 言語 | 地域 | 言語コード | Magentoーロケール |
| ブルガリア語 | ブルガリア | bg_BG | bg_BG |
| カタルニア語 | スペイン | ca_ES | ca_ES |
| チェコ語 | チェコ共和国 | cs_CZ | cs_CZ |
| デンマーク語 | デンマーク | da_DK | da_DK |
| ドイツ語 | ドイツ | de_DE | de_DE |
| ギリシャ語 | ギリシャ | el_GR | el_GR |
| 英語 | 英国 | en_GB | en_GB |
| 英語 | 米国 | en_US | en_US |
| スペイン語 | スペイン | es_ES | es_ES |
| エストニア語 | エストニア | et_EE | et_EE |
| バスク語 | スペイン | eu_ES | eu_ES |
| ペルシャ語 | イラン | fa_IR | fa_IR |
| フィンランド語 | フィンランド | fi_FI | fi_FI |
| フランス語 | フランス | fr_FR | fr_FR |
| ガリシア語 | スペイン | gl_ES | gl_ES |
| ヒンディー語 | インド | hi_IN | hi_IN |
| ハンガリー語 | ハンガリー | hu_HU | hu_HU |
| インドネシア | インドネシア | id_ID | id_ID |
| イタリア語 | イタリア | it_IT | it_IT |
| 韓国語 | 韓国 | ko_KR | ko_KR |
| リトアニア語 | リトアニア | lt_LT | lt_LT |
| ラトビアン | ラトビア | lv_LV | lv_LV |
| ノルウェー語 | ノルウェーブークマル | nb_NO | nb_NO |
| オランダ語 | オランダ | nl_NL | nl_NL |
| ポーランド語 | ポーランド | pl_PL | pl_PL |
| ポルトガル語 | ブラジル | pt_BR | pt_BR |
| ポルトガル語 | ポルトガル | pt_PT | pt_PT |
| ルーマニア語 | ルーマニア | ro_RO | ro_RO |
| ロシア | ロシア | ru_RU | ru_RU |
| スウェーデン語 | スウェーデン | 参照（_S） | 参照（_S） |
| タイ語 | タイ | th_TH | th_TH |
| トルコ語 | トルコ | tr_TR | tr_TR |
| 中国語 | 中国 | zh_CN | zh_Hans_CN |
| 中国語 | 台湾 | zh_TW | zh_Hant_TW |

Commerce Admin 言語設定（_ストア_ > 設定 > _設定_ > _一般_ /国オプションの場合）はサポートされる言語と一致し、デフォルトでその言語に設定されます。 それ以外の場合、ウィジェットのデフォルト値は英語になります。

管理者は、 [検索インデックス](settings.md#language)を使用して、より良い検索結果が得られるようにします。

### ウィジェットコードリポジトリー

製品一覧ページウィジェットとライブ検索フィールドウィジェットは、どちらも github リポジトリからダウンロードできます。

これにより、開発者は機能とスタイル設定を完全にカスタマイズできます。 これらのユーザーは、 [!DNL Live Search] サービス。

- [PLP ウィジェット](https://github.com/adobe/storefront-product-listing-page)
- [検索バー](https://github.com/adobe/storefront-search-as-you-type)

### Inventory management

[!DNL Live Search] のサポート [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) Commerceの機能（以前はマルチソースインベントリ（MSI）と呼ばれていました）。 フルサポートを有効にするには、次の操作を行う必要があります [更新](install.md#update) 依存関係モジュール `commerce-data-export` をバージョン 102.2.0 以降にアップグレードします。

[!DNL Live Search] Inventory management内で商品が使用可能かどうかを示すブール値を返しますが、どのソースに在庫があるかに関する情報は含まれません。

### 価格インデクサー

Live Search のお客様は新しいを使用できます [SaaS 価格インデクサー](../price-index/price-indexing.md)これにより、価格変更の更新と同期時間が短縮されます。

### 価格サポート

ライブ検索ウィジェットは、Adobe Commerceでサポートされているすべての価格タイプではなく、ほとんどの価格タイプをサポートしています。

現在、基本価格がサポートされています。 サポートされていない高度な価格は次のとおりです。

- コスト
- 広告の最低価格

を見る [API メッシュ](../catalog-service/mesh.md) より複雑な価格計算の場合。

価格フォーマットでは、Commerce インスタンス内の次のロケール設定がサポートされます。 *ストア* > 設定 > *設定* > 一般 > *一般* / ローカルオプション / ロケール。

### ヘッドレスストアフロントのサポート

オプションで、 `module-data-services-graphql` アプリケーションの既存のGraphQL範囲を拡張し、ストアフロントの行動データ収集に必要なフィールドを含めるモジュール。

```bash
composer require magento/module-data-services-graphql
```

このモジュールは、GraphQL クエリにコンテキストを追加します。

- `dataServicesStorefrontInstanceContext`
- `dataServicesMagentoExtensionContext`
- `dataServicesStoreConfigurationContext`

### PWAサポート

[!DNL Live Search] はPWA Studioで動作しますが、他のCommerce実装と比較すると、わずかな違いがあります。 検索や製品リストのページなどの基本的な機能は Venia で機能しますが、Graphql の一部の並べ替えが正しく機能しない場合があります。 パフォーマンスの違いもあります。

- 現在のPWAの実装 [!DNL Live Search] 検索結果を返すのに必要な処理時間は、 [!DNL Live Search] ネイティブのCommerce ストアフロントを使用します。
- [!DNL Live Search] PWA内のはサポートしていません [イベント処理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). その結果、検索レポートやインテリジェントマーチャンダイジングも機能します。
- での直接フィルタリング `description`, `name`, `short_description` と共に使用した場合、はGraphQLでサポートされません [PWA](https://developer.adobe.com/commerce/pwa-studio/)ただし、より一般的なフィルターで返されます。

使用目的 [!DNL Live Search] PWA Studioを伴う場合、インテグレーターは次の点にも留意する必要があります。

1. インストール [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. を `environmentId` が含まれる `storeDetails` オブジェクト。

   ```javascript
   const storeDetails: StoreDetailsProps = {
       environmentId: <Storefront_ID>,
       websiteCode: "base",
       storeCode: "main_website_store",
       storeViewCode: "default",
       searchUnitId: searchUnitId,
       config: {
           minQueryLength: 5,
           pageSize: 8,
           currencySymbol: "$",
           },
       };
   ```

### の Cookie

[!DNL Live Search] は、基本機能の一部としてユーザーインタラクションデータを収集し、このデータを保存するために cookie が使用されます。 ユーザー情報を収集する場合、ユーザーは Cookie の保存に同意する必要があります。 [!DNL Live Search] および [!DNL Product Recommendations] データストリームを共有するので、cookie メカニズムは同じです。 詳しくは、こちらを参照してください。 [Cookie 制限の処理](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie).
