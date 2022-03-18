---
title: ファセットに関するテクニカルノート
description: ライブ検索ファセットの使用に関する技術メモです。
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# ファセットに関するテクニカルノート

ファセット設定は、検索可能な静的および動的属性値の複数のディメンションを検索基準として使用する、パフォーマンスの高いフィルタリング方法です。

[!DNL Live Search] は `productSearch` 次に固有のファセットやその他のデータを返すクエリ [!DNL Live Search]. 参照： [`productSearch` クエリ](https://devdocs.magento.com/live-search/product-search.html) コード例を参照してください。

## ファセットの集計

ストアフロントに 3 つのファセット（カテゴリ、色、価格）があり、買い物客が 3 つすべてのファセット ( 色=青、価格が$10.00～50.00、カテゴリ= `promotions`) をクリックします。

* `categories` 集計 — 集計 `categories`適用 `color` および `price` フィルター（ただし、除外） `categories` フィルター。
* `color` 集計 — 集計 `color`適用 `price` および `categories` フィルター（ただし、除外） `color` フィルター。
* `price` 集計 — 集計 `price`適用 `color` および `categories` フィルター（ただし、除外） `price` フィルター。

## デフォルトの属性値

次の製品属性には、 [storefront プロパティ](https://docs.magento.com/user-guide/stores/attributes-product.html) これはデフォルトで有効になっています。

| プロパティ | Storefront プロパティ | 属性 |
|---|---|---|
| 並べ替え可能 | 製品リストの並べ替えに使用 | `price` |
| 検索可能 | 検索で使用 | `price` <br />`sku`<br />`name` |
| FilterableInSearch | レイヤーナビゲーションで使用 — フィルタリング可能（結果付き） | `price`<br />`visibility`<br />`category_name` |
