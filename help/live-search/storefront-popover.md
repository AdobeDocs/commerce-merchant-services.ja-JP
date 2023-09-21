---
title: "[!DNL Storefront Popover]"
description: 「 [!DNL Live Search storefront popover] は、推奨される製品とサムネールを動的に返します。」
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 441f8c6c6113ce96c5353dcbde170ca600bb0abb
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# [!DNL Storefront Popover]

条件 [!DNL Live Search] 次に該当 [インストール済み](install.md), a [!DNL popover] 買い物客が [検索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) ボックス。 文字を入力するたびに、 [!DNL popover] が更新され、上位の検索結果の推奨製品とサムネール画像が表示されます。

[!DNL Live Search] 2 文字以上のクエリの結果を返します。 部分一致の場合、1 単語あたりの最大文字数は 20 文字です。 「入力中の検索」クエリの文字数は設定できません。

## 検索可能な属性

ターゲットを絞り込んだ結果を生成するには、 [検索可能な](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`) 製品属性。 適切性を確保するために、明確で簡潔な意味を持つコンテンツが含まれている場合にのみ属性を検索可能にします。 より正確でなく長いテキストを含む属性（例： ）を使用しないでください。 `description`は、デフォルトで検索が有効になっていますが、検索結果の精度を下げることができます。 例えば、ある人が「ショート」を検索し、説明に「ショートスリーブ」という語句が含まれるシャツがある場合、シャツは検索結果に含まれます。

次の属性は常に検索可能です。

* `sku`
* `name`
* `categories`

[[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover] ページサイズ

ページのサイズ [!DNL popover] は、返すオートコンプリート済み製品のライン数を決定します。 以前は、ページサイズは 6 行にハードコードされていました。 ただし、 `page_size` の値は、現在は *管理者*. ライブ検索のインストール中に、 `page_size` 値は、現在の値の [カタログ検索](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` 設定。

デフォルトでは、「カタログ検索 — オートコンプリートの上限」の値は 8 行（または行）に設定されています。 ページのサイズを変更するには [!DNL popover]、次の操作を実行します。

1. 次の日： *管理者* サイドバー、移動 **ストア** /設定/ **設定**.
1. 左側のパネルで、を展開します。 **カタログ** を選択します。 **カタログ** を選択します。
1. を展開します。 *カタログ検索* 」セクションに入力します。
1. を設定します。 **オートコンプリート制限** を [!DNL popover].
1. 完了したら、「 **設定を保存**.

## カタログサービス

The [Adobe Commerceのカタログサービス](../catalog-service/overview.md) 拡張機能は、豊富なビューモデルカタログデータを提供し、製品関連のストアフロントエクスペリエンスをすばやく完全にレンダリングできます。 カタログサービスをライブ検索と組み合わせて使用すると、ネイティブ拡張機能で現在サポートされていない機能を提供できます。

* カラースウォッチ
* 拡張属性
* その他の製品情報を取り込むことができます

マーチャントは、カタログサービスを使用してウィジェットやストアフロント要素をカスタマイズおよび拡張できますが、Adobeのサポートチームの範囲外です。

## ヘッドレス実装

ヘッドレス実装の場合、ライブ検索ポップオーバーを [npm パッケージ](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).

## 制限事項

* The [!DNL Live Search] [!DNL storefront popover] は、 *Luma* テーマ、または *Luma*. 検索結果ページのパンくずリストには *ルメ* スタイル設定。
* The [!DNL popover] はをサポートしていません *空白* テーマ。 詳しくは、 [スタイル設定 [!DNL Popover] 要素](storefront-popover-styling.md) を参照してください。
* The [!DNL popover] は、クイック注文フォームではサポートされていません。
* ウィッシュリストと製品の比較はサポートされていません。
