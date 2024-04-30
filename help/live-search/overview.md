---
title: について [!DNL Live Search]?
description: “[!DNL Live Search] Adobe Commerceから迅速で関連性の高い直感的な検索を提供します。」
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 8aca09aba13e32afb191169729dfc1fbd0087262
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 0%

---

# について [!DNL Live Search]?

[!DNL Live Search] は、Adobe Commerceの標準検索機能に代わる拡張機能です。 この [!DNL Live Search] 拡張機能は Composer と共にインストールされ、 [!DNL Commerce] へのインストール [!DNL Live Search] [サービス](../landing/saas.md). これを設定すると、デフォルトの検索テキストフィールドがに置き換えられます [!DNL Live Search] テキストフィールド。 [!DNL Live Search] は製品リストページ（PLP）ウィジェットもインストールします。このウィジェットは、検索結果を参照する際に堅牢なフィルタリング機能を提供します。

（を使用） [!DNL Live Search]では、以下のことが可能です。

- 有意義な検索エクスペリエンスを作成すると、買い物客や買い物客ができるだけ少ない労力で欲しいものを見つけるのに役立ちます。
- セッション内の買い物客の行動に応じて、AI を活用した動的なファセット化と検索結果の再ランキングを利用できます。
- 簡単に更新でき、ライセンスに含まれる軽量の SaaS ベースのサービスを使用して、総所有コストを削減します。
- graphQL API、ヘッドレスの柔軟性、API サンドボックス環境、超高速 SaaS を有効にして、技術的な情報を取得します。

>[!IMPORTANT]
>
>サイト検索に関しては、Adobe Commerceのオプションが用意されています。 必ずお読みください。 [境界と制限](boundaries-limits.md) 実装する前に、以下を確認します [!DNL Live Search] は、お客様のビジネスニーズに合っています。

## アーキテクチャ

アーキテクチャのAdobe Commerce側には、検索のホストが含まれます *Admin*、カタログデータの同期とクエリサービスの実行。 後 [!DNL Live Search] をインストールして設定すると、Adobe Commerceで検索とカタログデータの SaaS サービスとの共有が開始されます。 この時点で、管理者ユーザーは検索を設定、カスタマイズ、管理できます [ファセット](facets.md), [同義語](synonyms.md)、および [マーチャンダイジングルール](category-merch.md).

![ライブ検索のデータフロー](assets/ls-cs-data-flow.png)

## クイックツアー

速度、関連性、使いやすさに重点を置いて、 [!DNL Live Search] は、買い物客と商人の両方にとってゲームのチェンジャーです。 ～の簡単なツアーを行う [!DNL Live Search] 店舗の前から。

### 入力中に検索

[!DNL Live Search] は、製品の提案と、での上位の検索結果のサムネール画像を返します。 [ポップオーバー](storefront-popover.md) 買い物客がにクエリを入力する際 [検索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) ボックス。 この [製品の詳細](https://experienceleague.adobe.com/docs/commerce-admin/start/storefront/storefront.html#product-page) ページは、買い物客が推奨製品またはおすすめ製品をクリックすると表示されます。 A _すべて表示_ ポップオーバーのフッターにあるリンクをクリックすると、検索結果のページが表示されます。

[!DNL Live Search] 2 文字以上のクエリに対しては、「入力中に検索」を行った結果を返します。 部分一致の場合、1 単語あたりの最大文字数は 20 文字です。 クエリの文字数は変更できません。 ポップオーバーには、`name`, `sku`、および `category_ids` フィールド。

![ストアフロントの例 – 入力中に検索](assets/storefront-search-as-you-type.png)

### すべての検索結果を表示

「入力中の検索」クエリで返されたすべての製品をリストするには、 _すべて表示_ ポップオーバーのフッター。

![ストアフロントの例 – 価格ファセット](assets/storefront-view-all-search-results.png)

### ファセットを使用したフィルター検索

フィルタリングされた検索で、属性値の複数のディメンションを使用する [ファセット](facets.md)を検索条件として使用します。 フィルターの選択はマーチャントによって定義され、返された製品に従って変更されます。最も一般的に使用されるファセットはリストの上部にピン留めされます。

ファセットを URL パラメーターとして使用：`http://yourwebsite.com?color=red`、およびライブ検索では、これらの属性値に基づいて結果がフィルタリングされます。

### 同義語

[同義語](synonyms.md) リーチを拡大し、買い物客がカタログと異なる単語を使用する可能性がある単語を含めることで、クエリのフォーカスを絞り込みます。 同義語辞書を微調整して、買い物客がエンゲージし、購入するパスを維持することができます。

### マーチャンダイジングルール

マーチャンダイジング [個のルール](rules.md) 検索するロジックとイベントを追加する if-then ステートメントを使用して、ショッピングエクスペリエンスを形作ります。 プロモーションやシーズン、その他の期間に合わせて、商品を簡単にブーストまたは埋め込むことができます。

### 検索用語のサポート

[!DNL Live Search] はCommerceをサポートします [検索語句のリダイレクト](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html). 例えば、「配送料」などの語句を検索すると、配送料ページに直接移動できます。

## Live Search コンポーネント

- [!DNL Live Search] [ポップオーバーウィジェット](storefront-popover.md) は、検索結果を含む検索フィールドの下に開くボックスです。
- [製品一覧ページウィジェット](plp-styling.md) は、ファセットとシノニムをサポートする、検索可能な製品リストページを提供します。
- [[!DNL Live Search] Admin](workspace.md) は、ルール、ファセットおよびシノニムが設定される場所です。

## [!DNL Live Search] workspace

この [!DNL Live Search] [workspace](workspace.md) は、管理者で設定する領域です [!DNL Live Search] 同義語、ファセット、カテゴリマーチャンダイジングなどの機能。

## イベント

[!DNL Live Search] 使用 [イベント](events.md) 計算する [インテリジェントマーチャンダイジング](category-merch.md) および [給付](performance.md) ダッシュボード。 イベントはデフォルトの実装で提供されています。 ヘッドレスストアフロントのイベントは、手動で有効にする必要があります。

## [!DNL Live Search] デモ

詳しくは、このビデオをご覧ください。 [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

Live Search の使用方法と設定方法について詳しくは、 [の完全なデモ [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration.html) トピック。
