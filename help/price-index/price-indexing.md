---
title: SaaS 価格インデックス作成
description: SaaS 価格インデックスを使用したパフォーマンスの向上
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 5b92d6ea-cfd6-4976-a430-1a3aeaed51fd
source-git-commit: 7d62f8d5539cd744e98d8d6c072d77a2a7c5a256
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# SaaS 価格インデックス作成

SaaS の価格インデックス作成により、価格の変更が反映されるまでの時間が短縮されます [Commerce サービス](../landing/saas.md) 送信後 これにより、大規模で複雑なカタログを持つマーチャント、または複数の Web サイトや顧客グループを持つマーチャントは、価格変更を継続的に処理できます。
ヘッドレスなストアフロントがある場合や、 [catalog-adapter](./catalog-adapter.md) の拡張機能で、お客様はAdobe Commerce core price indexer を無効にできます。

インデックス化や価格計算などの計算量の多いプロセスは、Commerce コアからAdobeのクラウドインフラストラクチャに移行されました。 これにより、マーチャントはリソースを迅速に拡大して価格のインデックス化時間を短縮し、その変更をより迅速に反映することができます。

SaaS サービスへのコアインデックス作成のデータフローは次のようになります。

![デフォルトのデータフロー](assets/old_way.png)

SaaS 価格インデックス作成のフローは次のとおりです。

![SaaS 価格インデックス作成データ フロー](assets/new_way.png)

これらの改善は、すべてのマーチャントにメリットをもたらしますが、最大限のメリットを享受できるのは次のような顧客です。

* 一定の価格変更：頻繁なプロモーション、季節的な割引、在庫のマークダウンなどの戦略的目標を達成するために、価格の繰り返しの変更を必要とするマーチャント。
* 複数の web サイトや顧客グループ：複数の web サイト（ドメイン/ブランド）や顧客グループで製品カタログを共有しているマーチャント。
* Web サイトまたは顧客グループをまたいだ一意の価格の膨大：事前に交渉された価格の B2B マーチャント、異なる価格戦略のブランドなど、web サイトまたは顧客グループをまたいだ一意の価格を含む広範な共有製品カタログを持つマーチャント。

SaaS 価格インデックスは、Adobe Commerce サービスを使用するお客様が無償で利用でき、すべての組み込みAdobe Commerce製品タイプの価格計算をサポートします。

このガイドでは、SaaS 価格インデックスの仕組みと有効化の方法について説明します。

## 要件

* Adobe Commerce 2.4.4 以降
* 最新バージョンのAdobe Commerce拡張機能を備えた、次のCommerce サービスのうち少なくとも 1 つ：

   * [カタログサービス](../catalog-service/overview.md)
   * [Live Search](../live-search/overview.md)
   * [製品のRecommendations](../product-recommendations/guide-overview.md)

Luma とAdobe Commerce Core GraphQLのユーザーは、 [`catalog-adapter`](catalog-adapter.md) luma とコア GraphQl の互換性を提供し、Adobe Commerce Product Price Indexer を無効にする拡張機能。

## 使用方法

SaaS 価格インデックス作成をサポートしてAdobe Commerce インスタンスをアップグレードしたら、新しいフィードを同期します。

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

## カスタム製品タイプの価格

価格計算は、基本価格、特別価格、グループ価格、カタログルール価格などのカスタム製品タイプに対してサポートされています。

特定の数式を使用して最終価格を計算するカスタム製品タイプがある場合、製品価格フィードの動作を拡張できます。

1. にプラグインを作成する `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` クラス。

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
       <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
           <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
       </type>
   </config>
   ```

1. カスタム式を使用してメソッドを作成します。

   ```php
   class UpdatePriceFromFeed
   {
       /**
       * @param ProductPrice $subject
       * @param array $result
       * @param array $values
       *
       * @return array
       */
       public function afterGet(ProductPrice $subject, array $result, array $values) : array
       {
           // Override the output $result with your data for the corresponding products (see original method for details) 
           return $result;
       }
   }
   ```
