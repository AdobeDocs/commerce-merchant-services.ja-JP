---
title: SaaS 価格インデックス作成
description: SaaS 価格インデックス作成を使用したパフォーマンスの向上
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: 19c4d3263c22914672b38c5dc5ec9908889bb9b6
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 0%

---

# SaaS 価格インデックス作成

SaaS 価格のインデックス作成は、価格の変更が送信後に SaaS 顧客の Web サイトに反映されるまでに要する時間を短縮します。 このオプションモジュールを使用すると、大規模で複雑なカタログを持つマーチャントや、複数の Web サイトや顧客グループを持つマーチャントが、価格の変化をより迅速かつ継続的に処理できます。

パイプラインの最大のボトルネック：インデクス作成や価格計算などの計算量の多いプロセスは、PHP のコアからAdobeのクラウドインフラストラクチャに移行されました。 これにより、マーチャントはリソースを迅速に拡張して、価格のインデクス化に要する時間を短縮し、その変更を Web サイトに迅速に反映できます。

SaaS サービスに対するコアインデックス作成データフローは次のようになります。

![デフォルトのデータフロー](assets/old_way.png)

SaaS 価格のインデックス作成では、フローは次のようになります。

![SaaS 価格インデックス作成データフロー](assets/new_way.png)

要件を満たすすべての商人は、これらの改善の恩恵を受けることができますが、最大の利益を得られるのは、次の機能を持つ顧客です。

* 定常的な価格変化：頻繁なプロモーション、季節ごとの割引、在庫のマークダウンなどの戦略目標を満たすために、価格の繰り返しの変更を必要とする商人。
* 複数の Web サイトや顧客グループ：複数の Web サイト（ドメイン/ブランド）や顧客グループにまたがって製品カタログを共有するマーチャント。
* Web サイトまたは顧客グループ間で多数のユニーク価格：Web サイトや顧客グループ間で一意の価格を含む大規模な共有商品カタログを持つマーチャント。事前に交渉された価格を持つ B2B 商人、異なる価格戦略を持つブランド。

PHP のコア価格インデクサーに依存するサードパーティのアプリケーションがある場合は、変更を加える前に、ドキュメントを読み、拡張機能プロバイダーにお問い合わせください。

SaaS 価格インデックス作成は、Adobe Commerceサービスをご利用のお客様には無料で提供されます。

このミニガイドでは、SaaS 価格のインデックス作成の仕組みと有効化方法を説明します。

## 必要システム構成

SaaS 価格のインデックス作成を使用するには、次が必要です。

* Adobe Commerce 2.4.4 以降
* 次の SaaS サービスのうち少なくとも 1 つがインストールされている。

   * [カタログサービス](../catalog-service/overview.md)
   * [ライブ検索](../live-search/guide-overview.md)
   * [製品Recommendations](../product-recommendations/guide-overview.md)

## モジュール

SaaS 価格インデックス作成では、機能を提供するために一連のモジュールを使用します。 必要なモジュールのリストは、ストアの設定に応じて少し異なる場合があります。

これらのモジュールは、管理者に新しいフィードを追加します。 これらのフィードは、価格計算に必要なデータを SaaS インデクサーに転送し、PHP のコア価格インデクサーを無視します。

```
magento/module-saas-price
magento/module-saas-scopes
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

Luma とAdobe Commerce Core GraphQLを使用しているお客様は、Luma と Core GraphQLの互換性を提供し、PHP のコア価格インデクサーを無効にするモジュールをインストールできます。

```
adobe-commerce/catalog-adapter
```

The `catalog-adapter` は 2.4.5 とのみ互換性があります。2.4.4 および 2.4.6 のサポートは、近い将来リリースされる予定です。
PHP のコア価格インデクサーは、必要に応じて、サードパーティの拡張機能やその他の理由で再度有効にすることができます。

## 注意事項

製品の種類、価格の複雑さ、カタログのサイズなどの要因に応じて、SaaS 価格のインデックス作成がストアに最適なソリューションとなる場合があります。 次の制限事項を読み、サイトに適したソリューションかどうかを判断します。

現在、SaaS の価格インデックス作成は、シンプル、グループ化、仮想、構成可能、および [Bundle Dynamic](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-bundle.html) 製品タイプ。
ダウンロード可能な製品、ギフトカード、バンドル固定製品のサポートは、近日中に提供されます。

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

### サポートされていない製品タイプを使用する Luma/Core GraphQL/ヘッドレス

* Luma/ヘッドレスマーチャント
* ギフトカード、ダウンロード可能な製品、または固定製品のバンドルの販売

現在サポートされていない製品タイプの場合は、製品タイプのサポートを完全にお待ちください。
