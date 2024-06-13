---
title: "[!DNL Storefront Popover]"
description: 「その [!DNL Live Search storefront popover] は、提案された製品とサムネールを動的に返します。」
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 099a4b9ce3ab71bc3c7ae181be242863a55d0ca9
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# [!DNL Storefront Popover]

条件 [!DNL Live Search] 等しい [installed](install.md), a [!DNL popover] 買い物客がを入力すると、ストアフロントに表示されます [検索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) ボックス。 各文字を入力すると、 [!DNL popover] に、上位の検索結果の推奨製品とサムネール画像を更新しました。

[!DNL Live Search] 2 文字以上のクエリの結果を返します。 部分一致の場合、1 単語あたりの最大文字数は 20 文字です。 「入力中の検索」クエリの文字数は設定できません。

デフォルトでは [!DNL Live Search] のサポート [検索語句のリダイレクト](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover] ページサイズ

のページサイズ [!DNL popover] オートコンプリートされた製品のライン数を指定します。 以前は、ページサイズは 6 行にハードコードされていました。 ただし、 `page_size` 値は、から設定できるようになりました。 *Admin*. Live Search のインストール中、 `page_size` の値が現在のの値に変更されます。 [カタログ検索](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` の設定値。

デフォルトでは、「カタログ検索 – オートコンプリートの制限」の値は 8 行（1 行）に設定されています。 のページサイズを変更するには [!DNL popover]、次の手順を実行します。

1. 日 *Admin* サイドバー、に移動 **ストア** > 設定 > **設定**.
1. 左側のパネルで、を展開します **カタログ** を選択します **カタログ** 設定のリストから。
1. を展開します。 *カタログ検索* セクション。
1. を **オートコンプリートの制限** を許可する行の数 [!DNL popover].
1. 完了したら、 **設定を保存**.

## カタログサービス

この [Adobe Commerceのカタログサービス](../catalog-service/overview.md) 拡張機能は、製品関連のストアフロントエクスペリエンスを迅速かつ完全にレンダリングするための機能豊富なビューモデルカタログデータを提供します。 カタログサービスをライブ検索と組み合わせて使用すると、現在ネイティブの拡張機能でサポートされていない機能を提供できます。

* 拡張属性
* その他の製品情報は次の場所に取り込むことができます

マーチャントは、カタログサービスを使用してウィジェットやストアフロント要素をカスタマイズおよび拡張できますが、Adobeのサポートチームはこの操作を行えません。

## ヘッドレス実装

ヘッドレス実装を使用するユーザーの場合は、 [npm パッケージ](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).

## 制限事項

* この [!DNL Live Search] [!DNL storefront popover] は、を使用するストアでのみ使用できます *Luma* テーマ、または基づいてカスタマイズされたテーマ *Luma*. 検索結果ページのパンくずリストには表示されません *Luma* スタイル設定。
* この [!DNL popover] はをサポートしていません *空白* テーマ。 参照： [スタイル設定 [!DNL Popover] 要素](storefront-popover-styling.md) を参照してください。
* この [!DNL popover] は、クイックオーダーフォームではサポートされていません。
* ウィッシュリストと製品の比較はサポートされていません。
