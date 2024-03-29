---
title: 「技術概要」
description: '"[!DNL Live Search] オンボーディングフロー、システム要件、境界、制限事項»'
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: e8d4215b1f16f1cb34783674cabc046dec135729
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# 技術概要

このトピックでは、技術要件、およびインストールと最適化に関するヒントについて説明します [!DNL Live Search] Adobe Commerceの

## 要件 {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4 以上
* PHP 8.1 / 8.2
* [!DNL Composer]

### サポートされるプラットフォーム

* Adobe Commerceオンプレミス (EE) :2.4.4 以降
* Adobe Commerce on Cloud (ECE) :2.4.4 以降

## エンドポイント

[!DNL Live Search] は、次の場所のエンドポイントを通じて通信します： `https://catalog-service.adobe.io/graphql`.

As [!DNL Live Search] は、製品データベース全体に対するアクセス権を持っていません。 [!DNL Live Search] GraphQLと Commerce のコアGraphQLは完全な同等性を持ちません。

SaaS API を直接（特にカタログサービスエンドポイント）呼び出すことをお勧めします。

* コマースデータベース/Graphql プロセスをバイパスして、パフォーマンスを向上し、プロセッサの負荷を軽減
* を活用する [!DNL Catalog Service] 呼び出し連盟 [!DNL Live Search], [!DNL Catalog Service]、および [!DNL Product Recommendations] を 1 つのエンドポイントから削除します。

一部の使用例では、 [!DNL Catalog Service] 製品の詳細や類似した事例については、を参照してください。 詳しくは、 [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) を参照してください。

カスタムヘッドレス実装がある場合は、 [!DNL Live Search] リファレンス実装：

* [PLP ウィジェット](https://github.com/adobe/storefront-product-listing-page)
* [ライブ検索フィールド](https://github.com/adobe/storefront-search-as-you-type)

Search Adapter や Widgets などのデフォルトのコンポーネント (Luma のウィジェットやAEM CIF Widgets など ) を使用しない場合、eventing(Adobe Senseiをインテリジェントマーチャンダイジングおよびパフォーマンス指標にフィードするクリックストリームデータ ) は初期状態では機能せず、ヘッドレスイベンティングを実装するカスタム開発が必要です。
の最新バージョン [!DNL Live Search] は既にを使用しています [!DNL Catalog Service].

## 境界としきい値

現在、 [!DNL Live Search] 検索/カテゴリ API には、次の制限と静的境界がサポートされています。

### インデックス作成

* [インデックス](indexing.md) ストア表示あたり最大 300 個の製品属性。
* Adobe Commerceデータベースの製品のインデックスのみを作成します。
* CMS ページはインデックス化されません。

### クエリ

* [!DNL Live Search] では、カテゴリツリーの完全な分類にアクセスできず、一部の階層的ナビゲーション検索シナリオがその範囲を超えています。
* [!DNL Live Search] は、クエリに一意のGraphQLエンドポイントを使用して、動的なファセット設定や検索（入力に応じて）などの機能をサポートします。 ただし、 [GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/)の場合、いくつかの違いがあり、一部のフィールドには完全な互換性がない場合があります。

カタログ権限を使用して顧客グループを制限するには、次の手順に従います。

* 製品はルートカテゴリに割り当てる必要があります。
* 「ログインしていません」顧客グループには、「許可」参照権限が付与されている必要があります。
* 製品を「未ログイン」顧客グループに制限するには、各カテゴリに移動し、各顧客グループに対して権限を設定します。

### ルール

* 検索マーチャンダイジングの最大数 [ルール](rules.md) 店舗ごとの表示は 50 です。
* カテゴリのマーチャンダイジングでは、カテゴリごとに 1 つのルールを設定できます。
* ルールあたりの条件の最大数は 10 です。
* ルールあたりのイベントの最大数は 25 です。

### シノニム

* [!DNL Live Search] 最大 200 まで管理可能 [同義語](synonyms.md) ストア表示ごと。

## 言語サポート

[!DNL Live Search] ウィジェットは、次の言語をサポートしています。

|  |  |  |  |
|--- |--- |--- |--- |
| 言語 | 地域 | 言語コード | Magentoロケール |
| ブルガリア語 | ブルガリア | bg_BG | bg_BG |
| カタロニア語 | スペイン | ca_ES | ca_ES |
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
| インドネシア語 | インドネシア | id_ID | id_ID |
| イタリア語 | イタリア | it_IT | it_IT |
| 韓国語 | 韓国 | ko_KR | ko_KR |
| リトアニア語 | リトアニア | lt_LT | lt_LT |
| ラトビア語 | ラトビア | lv_LV | lv_LV |
| ノルウェー語 | ノルウェーブークモール | nb_NO | nb_NO |
| オランダ語 | オランダ | nl_NL | nl_NL |
| ポーランド語 | ポーランド | pl_PL | pl_PL |
| ポルトガル語 | ブラジル | pt_BR | pt_BR |
| ポルトガル語 | ポルトガル | pt_PT | pt_PT |
| ルーマニア語 | ルーマニア | ro_RO | ro_RO |
| ロシア語 | ロシア | ru_RU | ru_RU |
| スウェーデン語 | スウェーデン | sv_SE | sv_SE |
| タイ語 | タイ | th_TH | th_TH |
| トルコ語 | トルコ | tr_TR | tr_TR |
| 中国語 | 中国 | zh_CN | zh_Hans_CN |
| 中国語 | 台湾 | zh_TW | zh_Hant_TW |

ウィジェットがコマース管理者の言語設定 (_ストア_ /設定/ _設定_ > _一般_ > 国のオプション ) は、サポートされている言語に一致します。デフォルトでは、その言語が使用されます。 それ以外の場合、ウィジェットはデフォルトで英語に設定されます。

管理者は、 [検索インデックス](settings.md#language)を使用して、検索結果の質を高めることができます。

## カテゴリマーチャンダイジング

[カテゴリマーチャンダイジング](category-merch.md) を設定できます。 [!DNL Live Search] 製品カテゴリレベルで作業する場合。

このビデオでは、カテゴリマーチャンダイジングの紹介をしています。

>[!VIDEO](https://video.tv.adobe.com/v/3424617)

## ウィジェットコードリポジトリ

製品リストページウィジェットとライブ検索フィールドウィジェットは、どちらも GitHub リポジトリからダウンロードできます。

これにより、開発者は機能とスタイル設定を完全にカスタマイズできます。 これらのユーザーは、 [!DNL Live Search] サービス。

* [PLP ウィジェット](https://github.com/adobe/storefront-product-listing-page)
* [検索バー](https://github.com/adobe/storefront-search-as-you-type)

## Inventory management

[!DNL Live Search] サポート [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) コマースの機能 ( 以前はマルチソースインベントリ (MSI) と呼ばれていました )。 完全なサポートを有効にするには、 [更新](install.md#update) 依存モジュール `commerce-data-export` をバージョン 102.2.0 以降に変更しました。

[!DNL Live Search] 製品がInventory management内で使用可能かどうかを示すブール値を返しますが、在庫があるソースに関する情報は含まれません。

## 価格インデクサー

ライブ検索のお客様は、 [SaaS 価格インデクサー](../price-index/price-indexing.md)：価格変更の更新と同期時間を高速化します。

## 価格のサポート

ライブ検索ウィジェットは、Adobe Commerceでサポートされているほとんどの価格タイプをサポートしていますが、一部の価格タイプはサポートしていません。

現在、基本価格がサポートされています。 サポートされていない高度な価格は次のとおりです。

* コスト
* 最小広告価格

見る [API メッシュ](../catalog-service/mesh.md) より複雑な価格計算の場合。

価格形式は、コマースインスタンス内のロケール設定をサポートします。 *ストア* /設定/ *設定* /一般/ *一般* /ローカルオプション/ロケール。

## PWAのサポート

[!DNL Live Search] はPWA Studioで機能しますが、他のコマース実装とは少し異なる場合があります。 Venia では検索や製品リストのページなどの基本機能は機能しますが、Graphql の順列の一部は正しく機能しない場合があります。 パフォーマンスに違いが生じる場合もあります。

* 現在のPWAの実装 [!DNL Live Search] を超える処理時間が必要です。 [!DNL Live Search] ネイティブの Commerce ストアフロントを使用します。
* [!DNL Live Search] のPWAはをサポートしていません [イベント処理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). その結果、検索レポートやインテリジェントマーチャンダイジングが機能します。
* 直接のフィルター `description`, `name`, `short_description` で使用する場合、GraphQLではサポートされません [PWA](https://developer.adobe.com/commerce/pwa-studio/)が返されますが、より一般的なフィルターが返されます。

次を使用するには： [!DNL Live Search] PWA Studioを使用した場合、インテグレーターは次の操作も必要になります。

1. インストール [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. を設定します。 `environmentId` （内） `storeDetails` オブジェクト。

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

## 現在はサポートされていません

* The [詳細検索](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) 次の場合、モジュールは無効になります： [!DNL Live Search] がインストールされ、ストアフロントフッターの「詳細検索」リンクは削除されます。
* [価格帯](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) および [特別価格](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) は、 [!DNL Live Search] フィールドおよび製品リストページウィジェット。

## Cookie

[!DNL Live Search] は、ユーザーインタラクションデータを基本機能の一部として収集し、cookie を使用してこのデータを保存します。 ユーザー情報を収集する場合、ユーザーは Cookie の保存に同意する必要があります。 [!DNL Live Search] および [!DNL Product Recommendations] はデータストリームを共有するので、同じ cookie メカニズムを使用する必要があります。 詳しくは、 [Cookie 制限の処理](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie).
