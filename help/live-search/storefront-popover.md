---
title: ストアフロントポップオーバー
description: ライブ検索ストアフロントポップオーバーは、推奨される製品とサムネールを動的に返します。
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 61d50ec07e7c8ced1696f4169a90302cca4d4f96
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ストアフロントポップオーバー

条件 [!DNL Live Search] が [インストール済み](install.md)を指定した場合、買い物客が [検索](https://docs.magento.com/user-guide/catalog/search-quick.html) ボックス 入力された各文字に応じて、ポップオーバーが更新され、上位の検索結果の推奨製品とサムネール画像が表示されます。

[!DNL Live Search] 2 文字以上のクエリの結果を返します。 部分一致の場合、1 単語あたりの最大文字数は 20 文字です。 「入力中の検索」クエリの文字数は設定できません。

>[!NOTE]
>
>この [!DNL Live Search] ストアフロントポップオーバーは、 *Luma* テーマ、または *Luma*. この *Luma* テーマが [!DNL Commerce] サンプルデータ。 このポップオーバーは *空白* テーマ。 詳しくは、 [ポップオーバー要素のスタイル設定](storefront-popover-styling.md) を参照してください。

## 検索可能な属性

ターゲットを絞り込んだ結果を生成するには、 [検索可能な](https://docs.magento.com/user-guide/stores/attributes-product.html#storefront-properties) (`searchable=true`) 製品属性。 適切性を確保するために、明確で簡潔な意味を持つコンテンツが含まれている場合にのみ属性を検索可能にします。 より正確でなく長いテキストを含む属性（例： ）を使用しないでください。 `description`は、デフォルトで検索が有効になっていますが、検索結果の精度を下げることができます。 例えば、ある人が「ショート」を検索し、説明に「ショートスリーブ」という語句が含まれるシャツがある場合、シャツは検索結果に含まれます。

次の属性は常に検索可能です。

* `sku`
* `name`
* `categories`

![ライブ検索ポップオーバー](assets/storefront-search-as-you-type.png)

## ポップオーバーページサイズ

ポップオーバーのページサイズによって、返すオートコンプリート済み製品の行数が決まります。 以前は、ページサイズは 6 行にハードコードされていました。 ただし、 `page_size` の値は現在、 *管理者*. ライブ検索のインストール中に、 `page_size` 値が [カタログ検索](https://docs.magento.com/user-guide/configuration/catalog/catalog.html#catalog-search) - `Autocomplete Limit` 設定。

デフォルトでは、「カタログ検索 — オートコンプリートの上限」の値は 8 行（または行）に設定されています。 ポップオーバーのページサイズを変更するには、次の操作を行います。

1. の *管理者* サイドバー、移動 **ストア** /設定/ **設定**.
1. 左側のパネルで、を展開します。 **カタログ** を選択します。 **カタログ** を選択します。
1. を展開します。 *カタログ検索* 」セクションに入力します。
1. を **オートコンプリート制限** を、ポップオーバーに許可する行数に設定します。
1. 完了したら、「 **設定を保存**.
