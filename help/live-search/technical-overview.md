---
title: 「技術概要」
description: “[!DNL Live Search] オンボーディングフロー、システム要件、境界、制限」
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: 18a0e8abd5478963425c4d0030a9a0f1df9d599e
workflow-type: tm+mt
source-wordcount: '1024'
ht-degree: 0%

---

# 技術概要

このトピックでは、インストールと最適化のための技術要件とヒントを確認します [!DNL Live Search] （Adobe Commerceの場合）

## 要件 {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4 以降
* PHP 8.1 / 8.2 / 8.3
* [!DNL Composer]

### サポートされるプラットフォーム

* Adobe Commerce オンプレミス（EE） :2.4.4 以降
* クラウド上のAdobe Commerce（ECE） :2.4.4 以降

## エンドポイント

[!DNL Live Search] エンドポイント （）を介した通信 `https://catalog-service.adobe.io/graphql`.

As [!DNL Live Search] 完全な製品データベースへのアクセス権がない [!DNL Live Search] GraphQLとCommerceのコアGraphQLには、完全な同等機能はありません。

SaaS API （特にカタログサービスエンドポイント）を直接呼び出すことをお勧めします。

* Commerce データベース/Graphql プロセスをバイパスすることで、パフォーマンスを向上させ、プロセッサー負荷を軽減します。
* を利用する [!DNL Catalog Service] 通話連合 [!DNL Live Search], [!DNL Catalog Service]、および [!DNL Product Recommendations] 単一のエンドポイントから。

一部のユースケースでは、を呼び出す方が良い場合もあります。 [!DNL Catalog Service] 製品の詳細および類似の事例について。 参照： [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) を参照してください。

カスタムのヘッドレス実装がある場合は、 [!DNL Live Search] リファレンス実装：

* [PLP ウィジェット](https://github.com/adobe/storefront-product-listing-page)
* [ライブ検索フィールド](https://github.com/adobe/storefront-search-as-you-type)

Luma の検索アダプターやウィジェット、AEM CIFウィジェットなどのデフォルトのコンポーネントを使用しない場合、イベント（インテリジェントマーチャンダイジングおよびパフォーマンス指標をAdobe Senseiにフィードするクリックストリームデータ）は初期設定では機能せず、ヘッドレスイベントを実装するにはカスタム開発が必要です。
の最新バージョン [!DNL Live Search] はすでに使用しています [!DNL Catalog Service].

## 境界としきい値

現在、 [!DNL Live Search] search/category API には、次のサポートされる制限と静的境界があります。

### インデックス作成

* [インデックス](indexing.md) 1 つのストア表示につき最大 300 個の製品属性。
* Adobe Commerce データベースからの商品のみにインデックスを作成します。
* CMS ページにはインデックスが作成されません。

### クエリ

* [!DNL Live Search] ではカテゴリツリーの完全な分類にアクセスできません。これにより、リーチを超える階層ナビゲーション検索シナリオが作成されます。
* [!DNL Live Search] では、クエリに一意のGraphQL エンドポイントを使用して、動的なファセットや入力時の検索などの機能をサポートしています。 に似ていますが [GRAPHQL API](https://developer.adobe.com/commerce/webapi/graphql/)、いくつかの違いがあり、一部のフィールドは完全には互換性がない可能性があります。

カタログ権限を使用して顧客グループを制限するには：

* 製品はルートカテゴリに割り当てる必要があります。
* 「ログインしていない」顧客グループには、「許可」閲覧権限を付与する必要があります。
* 製品をログインしていない顧客グループに制限するには、各カテゴリに移動して、各顧客グループに権限を設定します。

### ルール

* 検索マーチャンダイジングの最大数 [個のルール](rules.md) ストア表示あたり 50 です。
* カテゴリマーチャンダイジングには、カテゴリごとに 1 つのルールを設定できます。
* ルールごとの条件の最大数は 10 です。
* ルールあたりのイベントの最大数は 25 です。

### 同義語

* [!DNL Live Search] 最大 200 まで管理可能 [同義語](synonyms.md) ストア表示ごとに。

## 言語サポート

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

## カテゴリマーチャンダイジング

[カテゴリマーチャンダイジング](category-merch.md) を設定できます [!DNL Live Search] 製品カテゴリレベルで作業する

このビデオは、カテゴリマーチャンダイジングの概要です。

>[!VIDEO](https://video.tv.adobe.com/v/3424617)

## ウィジェットコードリポジトリー

製品一覧ページウィジェットとライブ検索フィールドウィジェットは、どちらも github リポジトリからダウンロードできます。

これにより、開発者は機能とスタイル設定を完全にカスタマイズできます。 これらのユーザーは、 [!DNL Live Search] サービス。

* [PLP ウィジェット](https://github.com/adobe/storefront-product-listing-page)
* [検索バー](https://github.com/adobe/storefront-search-as-you-type)

## Inventory management

[!DNL Live Search] のサポート [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) Commerceの機能（以前はマルチソースインベントリ（MSI）と呼ばれていました）。 フルサポートを有効にするには、次の操作を行う必要があります [更新](install.md#update) 依存関係モジュール `commerce-data-export` をバージョン 102.2.0 以降にアップグレードします。

[!DNL Live Search] Inventory management内で商品が使用可能かどうかを示すブール値を返しますが、どのソースに在庫があるかに関する情報は含まれません。

## 価格インデクサー

Live Search のお客様は新しいを使用できます [SaaS 価格インデクサー](../price-index/price-indexing.md)これにより、価格変更の更新と同期時間が短縮されます。

## 価格サポート

ライブ検索ウィジェットは、Adobe Commerceでサポートされているすべての価格タイプではなく、ほとんどの価格タイプをサポートしています。

現在、基本価格がサポートされています。 サポートされていない高度な価格は次のとおりです。

* コスト
* 広告の最低価格

を見る [API メッシュ](../catalog-service/mesh.md) より複雑な価格計算の場合。

価格フォーマットでは、Commerce インスタンス内の次のロケール設定がサポートされます。 *ストア* > 設定 > *設定* > 一般 > *一般* / ローカルオプション / ロケール。

## PWAサポート

[!DNL Live Search] はPWA Studioで動作しますが、他のCommerceの実装と比較すると、わずかな違いがあります。 検索や製品リストのページなどの基本機能は Venia で機能しますが、Graphql の一部の並べ替えが正しく機能しない場合があります。 パフォーマンスの違いもあります。

* 現在のPWAの実装 [!DNL Live Search] 検索結果を返すのに必要な処理時間は、 [!DNL Live Search] ネイティブのCommerce ストアフロントを使用します。
* [!DNL Live Search] PWA内のはサポートしていません [イベント処理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). その結果、検索レポートやインテリジェントマーチャンダイジングも機能します。
* での直接フィルタリング `description`, `name`, `short_description` と共に使用した場合、はGraphQLでサポートされません [PWA](https://developer.adobe.com/commerce/pwa-studio/)ただし、より一般的なフィルターで返されます。

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

## 現在サポートされていません

* この [詳細検索](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) 次の場合、モジュールは無効になります [!DNL Live Search] がインストールされ、ストアフロントのフッター内の詳細検索リンクが削除されます。
* [階層の価格](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) および [特別価格](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) ではサポートされていません [!DNL Live Search] フィールドと製品一覧ページウィジェット。

## の Cookie

[!DNL Live Search] は、基本機能の一部としてユーザーインタラクションデータを収集し、このデータを保存するために cookie が使用されます。 ユーザー情報を収集する場合、ユーザーは Cookie の保存に同意する必要があります。 [!DNL Live Search] および [!DNL Product Recommendations] データストリームを共有するので、cookie メカニズムは同じです。 詳しくは、こちらを参照してください。 [Cookie 制限の処理](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie).
