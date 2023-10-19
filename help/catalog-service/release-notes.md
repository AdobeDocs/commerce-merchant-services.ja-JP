---
title: '[!DNL Catalog Service] リリースノート'
description: の最新のリリース情報 [!DNL Catalog Service] Adobe Commerceの
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
feature: Services, Catalog Service, Release Notes
source-git-commit: ec8e37078cf1b5182036192a542fdbabe61e68dd
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 1%

---

# [!DNL Catalog Service] リリースノート

これらのリリースノートでは、の最新バージョンについて説明します。 [!DNL Catalog Service].
現在のメジャーリリースバージョンがサポートされています。 古いバージョンのリリースノートは参照用に提供されています。
更新内容は次のとおりです。

![新規](../assets/new.svg) 新機能
![修正点](../assets/fix.svg) 修正点および改善点
![バグ](../assets/bug.svg) 既知の問題

## 現在のメジャーバージョン

### V1.13 リリース

_2023 年 10 月 13 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) カタログサービスは、 `inStock` 製品バリアントのフラグ。
![新規](../assets/new.svg) `urlKey` および `externalId` がGraphQLスキーマに追加されました。
![新規](../assets/new.svg) カタログサービスはクリーンアップ API と互換性があるようになりました。

#### 既知の制限事項

以下の機能は、まだサポートされていません。

* 定価で製品をバンドル
* 動的属性ペイロードの最大サイズは 9 MB です。
* グループの製品価格。 単純な製品価格で計算できます。
* 画像配列では、最初の画像のみに役割が含まれます。

API Mesh と Core GraphQL API を使用して、次の制限を解決できます。

* 最小広告価格
* [価格帯](mesh.md)
* ダウンロード可能な製品とギフトカード

## 以前のバージョン

+++ 以前のバージョン

### V1.12 リリース

_2023 年 9 月 20 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) カタログサービスは現在、を使用しています [SaaS 価格のインデックス作成](../price-index/index.md).
![修正点](../assets/fix.svg) このリリースには、サービス側のバグ修正と改善が含まれています。

### V1.11 リリース

_2023 年 7 月 19 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) カタログサービスは、 [`recommendations`](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) GraphQL製品Recommendationsに対するクエリ。

### V1.10 リリース

_2023 年 6 月 28 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) カタログサービス API で「関連製品」がサポートされるようになりました。

### V1.7 リリース

_2023 年 4 月 13 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) カタログサービスで、削除された製品のバリアントをクリーンアップするようになりました。
![修正点](../assets/fix.svg) インフラストラクチャの拡張性とパフォーマンスの向上。

### V1.6 リリース

_2023 年 3 月 29 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) スウォッチを [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) クエリ。
![新規](../assets/new.svg) を取得する機能を追加しました。 `entityId` using [API メッシュ](mesh.md).

### V1.5 リリース

_2023 年 3 月 7 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) 追加済み [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) GraphQL機能。
![修正点](../assets/fix.svg) パフォーマンスと API の拡張性が向上しました。

### V1.4 リリース

_2023 年 2 月 8 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) インストール手順を簡単にするカタログサービスのメタパッケージを公開しました。
![修正点](../assets/fix.svg) API の拡張性とパフォーマンスの向上。

### V1.3 リリース

_2023 年 1 月 18 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) オンボーディングエクスペリエンスをシンプル化し、改善しました。
![新規](../assets/new.svg) 実稼動前のテストで、新しい顧客サンドボックスエンドポイントを使用できます。
![新規](../assets/new.svg) 仮想製品のサポートが追加されました。
![修正点](../assets/fix.svg) API の拡張性とパフォーマンスの向上。

### V1.1 リリース

_2022 年 11 月 19 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) カタログサービスでAdobeの [API メッシュ](https://developer.adobe.com/graphql-mesh-gateway/).
![修正点](../assets/fix.svg) API の拡張性と全体的なパフォーマンスが向上しました。

### V1.0 リリース

_2022 年 10 月 5 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) バンドルされた製品とグループ化された製品をサポートするようになりました。
![新規](../assets/new.svg) B2B 表示の上書きを追加しました。 製品が検索可能になり、特定の顧客グループ用に買い物かごに追加できるようになりました。
![修正点](../assets/fix.svg) サービスの安定性が向上し、パフォーマンスが向上しました。

### 0.3 リリース — ベータ+

_2022 年 9 月 13 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) バリエーションをサポートする画像：製品の画像は、選択したオプションに基づいて返されます。
![新規](../assets/new.svg) 価格サポートの役割：特定の顧客グループのメンバーのみが製品の価格を表示できます
![修正点](../assets/fix.svg) サービスの安定性とパフォーマンスの向上
![新規](../assets/new.svg) 製品がカタログから削除されると、アップデートを受け取ります

### ベータリリース

_2022 年 8 月 10 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) The `products` および `refineProduct` クエリは次のデータを返します。

* 定義済み（システム）の製品属性。
* 動的な製品属性を選択し、役割でフィルターします（製品の表示ページ/製品リストページ）。
* 製品オプション。
* 製品画像を使用し、役割 (PDP/PLP) でフィルタリングします。
* シンプルな製品の特定の価格と、設定可能な製品の価格帯。
* 顧客グループの価格と価格帯。 顧客グループを持たない買い物客に対して、フォールバックのデフォルト価格が返されます。
* B2B 顧客固有の価格を使用する製品タイプ。

+++
