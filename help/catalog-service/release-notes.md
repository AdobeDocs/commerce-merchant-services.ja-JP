---
title: '''[!DNL Catalog Service] リリースノート'
description: の最新のリリース情報 [!DNL Catalog Service] （Adobe Commerceの場合）
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
feature: Services, Catalog Service, Release Notes
source-git-commit: 6ca91feefbfc2fbc4d5851040b9f1ca3de6a6560
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---

# [!DNL Catalog Service] リリースノート

これらのリリースノートでは、の最新バージョンについて説明します [!DNL Catalog Service].
現在のメジャーリリースバージョンに対するサポートが提供されます。 古いバージョンのリリースノートが参照用に提供されています。
次のような更新があります。

![新規](../assets/new.svg) 新機能
![修正](../assets/fix.svg) 修正点および改善点
![バグ](../assets/bug.svg) 既知の問題

## 現在のメジャーバージョン

### V1.19 リリース

_2024 年 5 月 23 日（Pt）_

![修正](../assets/fix.svg) <!--DATA-5033-->この `InStock` オプション値のフラグで、スコープが考慮されるようになりました `enabled` 製品バリアントのステータス。

![修正](../assets/fix.svg) <!--DATA-5888-->大きな数字（最大 16 桁）とより大きな小数点精度（最大 4 桁）を必要とする製品価格のサポートを追加します。 既存のカタログに価格構成の更新を適用するには、 [データ管理ダッシュボード](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard)または、を使用します [Adobe Commerce コマンドラインインターフェイス](../landing/catalog-sync.md#command-line-interface).

#### 既知の制限事項

次の機能は、まだサポートされていません。

* 動的属性ペイロードの最大サイズは 9 MB です。
* グループ商品価格はシンプルな商品価格で算出できます。
* 画像配列では、最初の画像にのみ役割が含まれます。

API メッシュとコア GraphQL API を使用して、次の制限を解決します。

* 広告の最低価格
* 階層の価格
* 固定価格で製品をバンドル

詳細と例については、を参照してください。 [カタログサービスと API メッシュ](mesh.md)

## 以前のバージョン

+++ 以前のバージョン

### V1.18 リリース

_2024 年 4 月 11 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) PHP 8.3 のサポートを追加。

![新規](../assets/new.svg) この [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) および [`refineProduct`](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) クエリは、シンプルな製品と複雑な製品の両方で、カスタマイズ可能なオプションデータを返すようになりました。<!--DATA-5538-->

### V1.17 リリース

_2024 年 2 月 22 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) この [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) が利用可能になりました。 この改善されたダッシュボードは、のデータストリームに関するインサイトを提供します [!DNL Product Recommendations], [!DNL Live Search]、および [!DNL Catalog Service]. この機能のサポートは、バージョン 3.1.0 で導入されました `catalog-service` メタパッケージ。

### V1.16 リリース

_2024 年 2 月 13 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) 製品ビデオが Catalog Service API でサポートされるようになりました。
![修正](../assets/fix.svg) 在庫切れのオプションが PDP ウィジェットに表示されるようになりました。

#### 既知の制限事項

これらの機能は、まだサポートされていません。

* 動的属性ペイロードの最大サイズは 9 MB です。
* グループ製品価格。 この値は、単純な製品価格で計算できます。
* 画像配列では、最初の画像にのみ役割が含まれます。

API メッシュとコア GraphQL API を使用すると、次の制限を解決できます。

* 広告の最低価格
* [階層の価格](mesh.md)

### V1.13 リリース

_2023 年 10 月 12 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) カタログサービスは、 `inStock` 製品バリアントのフラグ。
![新規](../assets/new.svg) この `urlKey` および `externalId` GraphQL スキーマにフィールドが追加されました。
![新規](../assets/new.svg) ダウンロード可能な製品とギフトカードがサポートされるようになりました。

### V1.12 リリース

_2023 年 9 月 19 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) Catalog Service now uses [SaaS 価格インデックス作成](../price-index/price-indexing.md).
![修正](../assets/fix.svg) このリリースには、サービス側のバグ修正と改善が含まれています。

### V1.11 リリース

_2023 年 7 月 18 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) カタログサービスで、がサポートされるようになりました [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) 製品RecommendationsのGraphQL クエリ。

### V1.10 リリース

_2023 年 6 月 27 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) Catalog Service API がサポートするようになりました `related products`.

### V1.7 リリース

_2023 年 4 月 12 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) 削除された製品のバリエーションをカタログサービスでクリーンアップできるようになりました。
![修正](../assets/fix.svg) インフラストラクチャの拡張性とパフォーマンスの向上。

### V1.6 リリース

_2023 年 3 月 28 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) にスウォッチを追加しました [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) クエリ。
![新規](../assets/new.svg) 取得する機能を追加しました `entityId` 使用 [API メッシュ](mesh.md).

### V1.5 リリース

_2023 年 3 月 6 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) 追加済み [`categories`](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/) GraphQL機能。
![修正](../assets/fix.svg) パフォーマンスと API のスケーラビリティの向上。

### V1.4 リリース

_2023 年 2 月 7 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) インストール手順を簡素化するためのカタログサービスメタパッケージが公開されました。
![修正](../assets/fix.svg) API のスケーラビリティとパフォーマンスの向上。

### V1.3 リリース

_2023 年 1 月 17 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) オンボーディングエクスペリエンスを簡素化し、改善しました。
![新規](../assets/new.svg) 新しい顧客サンドボックスエンドポイントは、実稼動前のテストで使用できます。
![新規](../assets/new.svg) 仮想製品のサポートが追加されました。
![修正](../assets/fix.svg) API のスケーラビリティとパフォーマンスの向上。

### V1.1 リリース

_2022 年 11 月 18 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) カタログサービスでAdobeがサポートされるようになりました [API メッシュ](https://developer.adobe.com/graphql-mesh-gateway/).
![修正](../assets/fix.svg) API のスケーラビリティと全体的なパフォーマンスの向上。

### V1.0 リリース

_2022 年 10 月 4 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) バンドルされた製品とグループ化された製品をサポートするようになりました。
![新規](../assets/new.svg) B2B 表示の上書きを追加しました。 製品が検索できるようになり、特定の顧客グループのために買い物かごに追加できるようになりました。
![修正](../assets/fix.svg) サービスの安定性とパフォーマンスが向上しました。

### 0.3 リリース - Beta+

_2022 年 9 月 12 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) バリアント型の画像のサポート：選択したオプションに基づいて製品画像が返されます
![新規](../assets/new.svg) 価格サポートの役割：特定の顧客グループのメンバーのみが製品の価格を表示できるようにします
![修正](../assets/fix.svg) サービスの安定性とパフォーマンスの向上
![新規](../assets/new.svg) 製品がカタログから削除されると、更新が受信されます

### Beta リリース

_2022 年 8 月 9 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) この `products` および `refineProduct` クエリは、次のデータを返します。

* 事前定義済み（システム）製品属性。
* 製品の動的属性および役割別のフィルター（製品の表示ページ/製品のリストページ）。
* 製品オプション。
* 製品画像を役割（PDP/PLP）別にフィルタリングする方法を説明します。
* シンプルな製品の特定の価格と設定可能な製品の価格範囲。
* 顧客グループの価格と価格範囲。 顧客グループを持たない買い物客に対しては、フォールバックのデフォルト価格が返されます。
* B2B 顧客固有の価格を使用する製品タイプ。
