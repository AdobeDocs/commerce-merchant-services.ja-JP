---
title: ファセットに関するテクニカルノート
description: ライブ検索ファセットの使用に関する技術メモです。
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: e53fb13b98684757b8081b2e19dd33d925e8ce5d
workflow-type: tm+mt
source-wordcount: '114'
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
