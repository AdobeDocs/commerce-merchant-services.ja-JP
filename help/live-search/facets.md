---
title: "ファセット"
description: "[!DNL Live Search] ファセットでは、複数の属性値のディメンションを検索条件として使用します。"
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: 460065ecf6478e4313bd31ea848e04c7e8e192a3
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# ファセット

ファセット化は、属性値の複数のディメンションを検索基準として使用する、高パフォーマンスのフィルタリングの方法です。 ファセット検索は似ていますが、標準よりも「かなり賢い」です [層状ナビゲーション](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html). 使用可能なフィルターのリストは、 [フィルター可能な属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html#filterable-attributes) 検索結果に返された製品の数。

[!DNL Live Search] は `productSearch` 次に固有のファセットやその他のデータを返すクエリ [!DNL Live Search]. 参照： [`productSearch` クエリ](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) （開発者向けドキュメント）を参照してください。

![フィルター済みの検索結果](assets/storefront-search-results-run.png)

定義されたファセットを URL パラメーターとして使用でき、結果は次のパラメーター値に基づいてフィルタリングされます。 `http://yourstore.com?brand=acme&color=red`.

## Faceting の要件

ファセット設定のカテゴリと製品属性の要件は、レイヤー化されたナビゲーションで使用されるフィルタリング可能な属性と似ています。 属性の各ストアフロントプロパティには、「検索結果のレイヤーナビゲーションで使用」の値が「はい」に設定されている必要があります。

[!DNL Live Search] は、以下をサポートします。

* ファセットとして設定された 100 個の属性
* 50 個の並べ替え可能な属性
* 200 個のフィルター可能な属性
* 200 個の検索可能な属性

>[!NOTE]
>
> 200 個を超えるフィルタリング可能な属性が定義されている場合、200 個の実際にインデックスが作成される決定論的な属性ではありません。

コンテンツを取り込む属性が多数ある場合は、属性を 1 つの「meta-attribute」に組み合わせることを検討してください。 例えば、靴のサイズは通常数値で、シャツのサイズは通常「S/M/L/XL」です。 この 2 種類のサイズを 1 つの検索可能な属性に組み合わせることができます。

| 設定 | 説明 |
|--- |--- |
| [カテゴリの表示設定](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/create/categories-display-settings.html) | アンカー — `Yes` |
| [属性プロパティ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) | [カタログ入力タイプ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price`, `Visual swatch` （ウィジェットのみ）、 `Text swatch` （ウィジェットのみ） |
| 属性ストアフロントのプロパティ | 検索結果のレイヤーナビゲーションで使用 — `Yes` |

## ファセットの集計

ストアフロントに 3 つのファセット（カテゴリ、色、価格）があり、買い物客が 3 つすべてのファセット ( 色=青、価格が$10.00 ～ 50.00、カテゴリ= `promotions`) をクリックします。

* `categories` 集計 — 集計 `categories`を設定し、 `color` および `price` フィルター（ただし、ではない） `categories` フィルター。
* `color` 集計 — 集計 `color`を設定し、`price` および `categories` フィルター（ただし、ではない） `color` フィルター。
* `price` 集計 — 集計 `price`を設定し、 `color` および `categories` フィルター（ただし、ではない） `price` フィルター。

## デフォルトの属性値

次の製品属性には、 [storefront プロパティ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) は、 [!DNL Live Search] デフォルトで有効になっています。

| プロパティ | Storefront プロパティ | 属性 |
|---|---|---|
| 並べ替え可能 | 製品リストの並べ替えに使用 | `price` |
| 検索可能 | 検索で使用 | `price` <br />`sku`<br />`name` |
| FilterableInSearch | レイヤーナビゲーションで使用 — フィルタリング可能（結果付き） | `price`<br />`visibility`<br />`category_name` |

## システム以外のデフォルトの属性プロパティ

次の表に、Luma サンプルデータに固有のプロパティを含む、非システム属性のデフォルトの検索およびフィルタリング可能なプロパティを示します。 の設定 *検索で使用* 属性プロパティを `Yes` を指定すると、属性は [!DNL Live Search] そしてネイティブAdobe Commerce

| 属性コード | 検索可能 | レイヤーナビゲーションで使用 |
|--- |--- |--- |
| アクティビティ | はい | フィルタリング可能（結果を含む） |
| attributes_brand | はい | いいえ |
| ブランド | はい | いいえ |
| 気候 | はい | フィルタリング可能（結果を含む） |
| 襟 | はい | フィルタリング可能（結果を含む） |
| カラー | はい | フィルタリング可能（結果を含む） |
| コスト | はい | いいえ |
| eco_collection | はい | フィルタリング可能（結果を含む） |
| 性別 | はい | フィルタリング可能（結果を含む） |
| 製造元 | はい | フィルタリング可能（結果を含む） |
| 材料 | はい | フィルタリング可能（結果を含む） |
| 目的 | はい | フィルタリング可能（結果を含む） |
| strap_bags | はい | フィルタリング可能（結果を含む） |
| style_general | はい | フィルタリング可能（結果を含む） |

## デフォルトのシステム属性プロパティ

次の表に、システム属性のデフォルトの検索およびフィルタ可能なプロパティを示します。

| 属性コード | 検索可能 | レイヤーナビゲーションで使用 |
|--- |--- |--- |
| allow_open_amount | はい | フィルタリング可能（結果を含む） |
| 説明 | はい | いいえ |
| name | はい | いいえ |
| 価格 | はい | フィルタリング可能（結果を含む） |
| short_description | はい | いいえ |
| sku | はい | いいえ |
| ステータス | はい | いいえ |
| tax_class_id | はい | いいえ |
| url_key | はい | いいえ |
| 重み | はい | いいえ |
