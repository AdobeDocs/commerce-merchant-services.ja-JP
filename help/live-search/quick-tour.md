---
title: "クイックツアー"
description: 「～をちょっと見てみましょう。 [!DNL Live Search] 店の前から」
exl-id: bcb19506-6617-4c8a-83df-9d961f81e9e8
source-git-commit: 9f045a049ac775ed4673e807ab5e21b8811cde2d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# クイックツアー

スピード、関連性、使いやすさに重点を置いて [!DNL Live Search] 買い物客と商人の両方にとって、大きな変革をもたらすものです。 続いて～のクイックツアーを見る [!DNL Live Search] 店の前から

## 入力に応じて検索

[!DNL Live Search] は、提案された製品と、上位の検索結果のサムネール画像を使用して、 [ポップオーバー](storefront-popover.md) 買い物客が [検索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) ボックス。 The [製品の詳細](https://experienceleague.adobe.com/docs/commerce-admin/start/storefront/storefront.html#product-page) 買い物客が提案または注目すべき製品をクリックすると、ページが表示されます。 A _すべて表示_ リンクは、ポップオーバーのフッターに、検索結果ページを表示します。

[!DNL Live Search] は、2 文字以上のクエリに対する「入力時に検索」の結果を返します。 部分一致の場合、1 単語あたりの最大文字数は 20 文字です。 クエリの文字数は設定できません。 ポップオーバーには、次のフィールドが含まれます。 `name`, `sku`、および `category_ids`.

![ストアフロントの例 — 入力時に検索](assets/storefront-search-as-you-type.png)

## すべての検索結果を表示

「入力時に検索」クエリで返されるすべての製品をリストするには、 _すべて表示_ をクリックします。

![ストアフロントの例 — 価格ファセット](assets/storefront-view-all-search-results.png)

## ファセットを使用したフィルター済み検索

フィルター検索では、複数の属性値のディメンションが使用されます。または、 [ファセット](facets.md)、を検索条件として使用します。 フィルターの選択はマーチャントが定義し、返される製品に応じて変更します。最も一般的に使用されるファセットはリストの上部に固定されています。

URL パラメーターとしてファセットを使用：`http://yourwebsite.com?color=red`およびライブ検索は、これらの属性値に基づいて結果をフィルタリングします。

## シノニム

[シノニム](synonyms.md) カタログ内の言葉とは異なる言葉を買い物客が使用する可能性があるので、リーチを拡大し、クエリの焦点をより鋭くします。 シノニム辞書を微調整して、買い物客のエンゲージを維持し、購入パス上で使用できます。

## マーチャンダイジングルール

マーチャンダイジング [ルール](rules.md) 検索にロジックとイベントを追加する if-then 文で買い物体験を形成します。 プロモーションや季節などの期間に合わせて、製品を簡単にブーストまたは埋め込むことができます。

## 検索語のサポート

[!DNL Live Search] コマースをサポート [検索語句のリダイレクト](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html). 例えば、「送料」などの語句を検索して、直接送料ページに移動できます。
