---
title: ファセット
description: ライブ検索ファセットでは、属性値の複数のディメンションが検索条件として使用されます。
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# ファセット

ファセット化は、属性値の複数のディメンションを検索基準として使用する、高パフォーマンスのフィルタリングの方法です。 ファセット検索は似ていますが、標準よりも「かなり賢い」です [層状ナビゲーション](https://docs.magento.com/user-guide/catalog/navigation-layered.html). 使用可能なフィルターのリストは、 [フィルター可能な属性](https://docs.magento.com/user-guide/catalog/navigation-layered-filterable-attributes.html) 検索結果に返された製品の数。 で最大 100 個のファセットを設定できます。 [!DNL Live Search].

![フィルター済みの検索結果](assets/storefront-search-results-run.png)

## Faceting の要件

ファセット設定のカテゴリと製品属性の要件は、レイヤー化されたナビゲーションで使用されるフィルタリング可能な属性と似ています。 各属性のストアフロントプロパティは、に設定する必要があります。 `filterable (with results)`.

| 設定 | 説明 |
|--- |--- |
| [カテゴリの表示設定](https://docs.magento.com/user-guide/catalog/categories-display-settings.html) | アンカー — `Yes` |
| [属性プロパティ](https://docs.magento.com/user-guide/stores/attribute-product-create.html) | [カタログ入力タイプ](https://docs.magento.com/user-guide/stores/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price` |
| 属性ストアフロントのプロパティ | レイヤーナビゲーションで使用 — `Filterable (with results)` |

## システム以外のデフォルトの属性プロパティ

次の表に、Luma サンプルデータに固有のプロパティを含む、非システム属性のデフォルトの検索およびフィルタリング可能なプロパティを示します。 の設定 *検索で使用* 属性プロパティを `Yes` 属性を [!DNL Live Search] そしてネイティブのAdobe Commerce

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
| 重み付け | はい | いいえ |
