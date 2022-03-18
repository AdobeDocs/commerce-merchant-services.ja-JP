---
title: ストアフロントポップオーバー
description: ライブ検索ストアフロントポップオーバーは、推奨される製品とサムネールを動的に返します。
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# ストアフロントポップオーバー

条件 [!DNL Live Search] が [インストール済み](install.md)を指定した場合、買い物客が [検索](https://docs.magento.com/user-guide/catalog/search-quick.html) ボックス 入力された各文字に応じて、ポップオーバーが更新され、上位の検索結果の推奨製品とサムネール画像が表示されます。

[!DNL Live Search] 2 文字以上のクエリの結果を返します。 部分一致の場合、1 単語あたりの最大文字数は 20 文字です。 「入力中の検索」クエリの文字数は設定できません。

>[!NOTE]
>
>この [!DNL Live Search] ストアフロントポップオーバーは、 *Luma* テーマ、または *Luma*. この *Luma* テーマが [!DNL Commerce] サンプルデータ。 このポップオーバーは *空白* テーマ。 詳しくは、 [変更したテーマの使用](#working-with-modified-theme) を参照してください。

## 検索可能な属性

ターゲットを絞り込んだ結果を生成するには、 [検索可能な](https://docs.magento.com/user-guide/stores/attributes-product.html#storefront-properties) (`searchable=true`) 製品属性。 適切性を確保するために、明確で簡潔な意味を持つコンテンツが含まれている場合にのみ属性を検索可能にします。 より正確でなく長いテキストを含む属性（例： ）を使用しないでください。 `description`は、デフォルトで検索が有効になっていますが、検索結果の精度を下げることができます。 例えば、ある人が「ショート」を検索し、説明に「ショートスリーブ」という語句が含まれるシャツがある場合、シャツは検索結果に含まれます。

次の属性は常に検索可能です。

* `sku`
* `name`
* `categories`

![ライブ検索ポップオーバー](assets/storefront-search-as-you-type.png)
