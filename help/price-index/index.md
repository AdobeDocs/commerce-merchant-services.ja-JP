---
title: SaaS 価格インデックス作成
description: SaaS 価格インデックス作成を使用したパフォーマンスの向上
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: b7989b416f852d2c7164d21e8f0598373662b760
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# SaaS 価格インデックス作成

SaaS 価格のインデックス作成により、価格の変更が反映されるまでの時間が短縮されます。 [コマースサービス](../landing/saas.md) 送信後 これにより、大規模で複雑なカタログを持つマーチャントや、複数の Web サイトや顧客グループを持つマーチャントが、価格の変更を継続的に処理できます。
ヘッドレスストアフロントがある場合、または [catalog-adapter](./catalog-adapter.md) 拡張機能を使用すると、Adobe Commerceのコア価格インデクサーを無効にできます。

インデクス作成や価格計算などの計算量の多いプロセスが、コマースコアからAdobeのクラウドインフラストラクチャに移行されました。 これにより、マーチャントは迅速にリソースを拡張して、価格のインデクション時間を短縮し、その変更を迅速に反映できます。

SaaS サービスに対するコアインデックス作成データフローは次のようになります。

![デフォルトのデータフロー](assets/old_way.png)

SaaS 価格のインデックス作成では、フローは次のようになります。

![SaaS 価格インデックス作成データフロー](assets/new_way.png)

すべての商人がこれらの改善の恩恵を受けることができますが、最大の利益を得られるのは次の機能を持つ顧客です。

* 定常的な価格変化：頻繁なプロモーション、季節ごとの割引、在庫のマークダウンなどの戦略目標を満たすために、価格の繰り返しの変更を必要とする商人。
* 複数の Web サイトや顧客グループ：複数の Web サイト（ドメイン/ブランド）や顧客グループにまたがって製品カタログを共有するマーチャント。
* Web サイトまたは顧客グループ間で多数のユニーク価格：Web サイトまたは顧客グループ間で一意の価格を含む大規模な共有商品カタログを持つマーチャント（事前に交渉された価格を持つ B2B 商人、異なる価格戦略を持つブランドなど）。

SaaS 価格インデックス作成は、Adobe Commerceサービスをご利用のお客様は無料で利用でき、組み込みのAdobe Commerce製品タイプすべてで価格計算をサポートします。

このミニガイドでは、SaaS 価格のインデックス作成の仕組みと有効化方法を説明します。

## 要件

* Adobe Commerce 2.4.4 以降
* Adobe Commerce拡張機能の最新バージョンを持つ、次のコマースサービスの少なくとも 1 つ：

   * [カタログサービス](../catalog-service/overview.md)
   * [ライブ検索](../live-search/guide-overview.md)
   * [製品Recommendations](../product-recommendations/guide-overview.md)

Luma とAdobe Commerce Core GraphQLのユーザーは、 [`catalog-adapter`](catalog-adapter.md) Luma と Core GraphQl の互換性を提供し、Adobe Commerce Product Price インデクサーを無効にする拡張機能です。

## 使用状況

Adobe Commerceインスタンスを SaaS 価格インデックス作成サポートでアップグレードした後、新しいフィードを同期します。

```
magento/module-saas-price
magento/module-saas-scopes
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
magento/module-bundle-product-override-data-exporter
magento/module-gift-card-product-data-exporter
```

## カスタム製品タイプの価格

価格の計算は、基本価格、特別価格、グループ価格、カタログルール価格などのカスタム製品タイプでサポートされます。

特定の数式を使用して最終価格を計算するカスタムの製品タイプがある場合、製品価格フィードの動作を拡張できます。

## 使用状況

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
    </type>
</config>
```

新しいフィードは、 `resync` [CLI コマンド](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). それ以外の場合は、標準の同期プロセスでデータが更新されます。 に関する詳細情報を取得する [カタログ同期](../landing/catalog-sync.md) プロセス。

## 使用シナリオ

### 拡張機能の依存関係がない Luma

* 必要なサービス ( ライブ検索、製品Recommendations、カタログサービス ) がインストールされている Luma またはAdobe Commerce Core GraphQLマーチャント
* PHP のコア価格インデクサーに依存するサードパーティの拡張機能はありません
* シンプルで構成可能な、グループ化された、仮想製品、およびバンドル化された動的製品の販売

1. 新しいフィードを有効にします。
1. カタログアダプタをインストールします。

### Luma とAdobe Commerce Core GraphQl と PHP コア価格インデクサーの依存関係

* サポート対象のサービス ( ライブ検索、製品Recommendations、カタログサービス ) がインストールされている Luma またはAdobe Commerce Core GraphQLマーチャント
* PHP のコア価格インデクサーに依存するサードパーティの拡張機能を使用
* シンプルで構成可能な、グループ化された、仮想製品、およびバンドル化された動的製品の販売

1. 新しいフィードを有効にする
1. カタログアダプタをインストールします。
1. PHP のコア価格インデクサを再度有効にします。
1. で新しいフィードと Luma の互換性コードを使用 `catalog-adapter` モジュール。

### ヘッドレスマーチャント

* サポート対象のサービス ( ライブ検索、製品Recommendations、カタログサービス ) がインストールされているヘッドレスマーチャント
* PHP のコア価格インデクサに依存しない
* シンプルで構成可能な、グループ化された、仮想製品、およびバンドル化された動的製品の販売

1. 新しいフィードを有効にする
1. PHP のコア価格インデクサを無効にするカタログアダプタをインストールします。

## カスタム価格

SaaS 価格インデクサーは、特別価格、グループ価格、カタログルール価格など、Adobe Commerceで使用可能なカスタムの製品タイプ価格機能をサポートしています。

例：カスタムの製品タイプがあります  `custom_type` および製品 (SKU 「Custom Type Product」)

デフォルトでは、コマースデータの書き出し拡張機能は、次の価格フィードを価格インデクサーに送信します。

```json
{
    "sku": "Custom Type Product",
    "type": "SIMPLE", // must be "SIMPLE" regardless of the real product type
    "customerGroupCode": "0",
    "websiteCode": "base",
    "regular": 123, // the regular base price found in catalog_product_entity_decimal table
    "discounts":    // list of discounts: special_price, group, catalog_rule
    [
        {
            "code": "catalog_rule",
            "price": 102.09
        }
    ],
    "deleted": false,
    "updatedAt": "2023-07-31T13:07:54+00:00"
}
```

「カスタム製品タイプ」で一意の数式を使用して製品価格を計算する場合、システムインテグレーターは、コマースデータの書き出し拡張機能を拡張することで、価格フィールドと割引フィールドを上書きできます。

1. でのプラグインの作成 `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` クラス。

`di.xml` ファイル：

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" disabled="false" />
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
        // Get all custom products, prices and discounts per website and customer groups
        // Override the output $result with your data for the corresponding products
        return $result;
    }
}
```
