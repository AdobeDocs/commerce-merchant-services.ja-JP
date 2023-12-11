---
title: の概要 [!DNL Live Search]
description: '"[!DNL Live Search] Adobe Commerceからは、素早く、超関連性が高く、直感的な検索エクスペリエンスを提供します。」'
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: d5df2a098dbbb2ecfb68c36dd12843c963d46b17
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# の概要 [!DNL Live Search]

[!DNL Live Search] は、標準の検索機能に代わるAdobe Commerceのサービスです。 The [!DNL Live Search] モジュールが Composer と共にインストールされ、 [!DNL Commerce] へのインストール [!DNL Live Search] [サービス](../landing/saas.md). 設定すると、デフォルトの検索テキストフィールドが [!DNL Live Search] テキストフィールド。 [!DNL Live Search] また、は、検索結果を参照する際に堅牢なフィルタリング機能を提供する製品リストページ (PLP) ウィジェットをインストールします。

[!DNL Live Search] 次の場所に表示される： *マーケティング* 下のメニュー *SEO と検索* （内） [!DNL Commerce] *管理者*.

アーキテクチャのAdobe Commerce側には、検索のホストが含まれます *管理者*、カタログデータの同期、およびクエリサービスの実行を行う。 後 [!DNL Live Search] がインストールおよび設定されると、Adobe Commerceは検索およびカタログデータの SaaS サービスとの共有を開始します。 この時点で、管理者ユーザーは検索の設定、カスタマイズ、管理をおこなうことができます [ファセット](facets.md), [同義語](synonyms.md)、および [マーチャンダイジングルール](category-merch.md).

## ライブ検索コンポーネント

* [!DNL Live Search] [ポップオーバーウィジェット](storefront-popover.md) は、検索結果を含む検索フィールドの下に開くボックスです。
* [製品リストページウィジェット](plp-styling.md) は、ファセットとシノニムのサポートを含む検索可能な製品リストページを提供します。
* AEM CIFコンポーネント： [ポップオーバーウィジェット](https://github.com/adobe/aem-cif-guides-venia/pull/319) そして [PLP ウィジェット](https://github.com/adobe/aem-cif-guides-venia/pull/320) AEMサイトが [!DNL Live Search].
* [[!DNL Live Search] 管理者](workspace.md) は、ルール、ファセットおよびシノニムを設定する場所です。

## ワークフローの概要

[!DNL Live Search] は、カタログデータをAdobe Commerce SaaS インフラストラクチャに移動し、ユーザーの入力に応じて検索結果をすばやく配信するために使用されるインデックスを構築することで機能します。

### 1.インストール

[!DNL Live Search] 次に該当 [インストール済み](install.md) を通じてAdobe Commerceインスタンスに [コンポーザー](https://getcomposer.org/). これにより、サービスに接続する必要なモジュールがインストールされ、デフォルトの検索フィールドを上書きするように Commerce インスタンスが設定されます。 また、サービスを設定するためのコマース管理オプションもインストールします。

### 2.データを同期

[!DNL Live Search] カタログデータをAdobeの SaaS インフラストラクチャに移動します。 データのインデックスが作成され、検索結果がこのインデックスからストアフロントに直接配信されます。 サイズと複雑さに応じて、インデックス作成には 30 分から数時間かかる場合があります。

### 3.データを設定する

製品データを正しく設定すると、顧客に対して適切な検索結果が得られます。 必要な設定手順は、カテゴリの割り当てと属性の設定です。

#### カテゴリの割り当て

返された製品 [!DNL Live Search] は、割り当てられている必要があります [カテゴリ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html). 例えば、Luma では、製品は「男性」、「女性」、「ギア」などのカテゴリに分類されます。 また、「トップス」、「ボトムス」、「ウォッチ」にもサブカテゴリが設定されています。 これにより、フィルタリング時の精度を向上できます。

#### 検索可能なフィールドとフィルタリング可能なフィールド

製品が割り当てられます [属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 検索およびフィルタリングに使用できます。 属性は、「色」、「サイズ」、「マテリアルタイプ」などです。 これらの属性を使用して、「緑のトップ」を探すことができます。 各製品には、コマース管理で定義された多数の属性が含まれる場合があります。

これらの属性は、それぞれ [&quot;searchable&quot;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html) 管理者で設定します。 「searchable」と設定した場合、これらの属性を検索に使用できます。 [!DNL Live Search].

[ファセット](facets.md) は、 [!DNL Live Search] フィルタリング可能です。 フィルタリング可能な属性は、でファセットとして設定できます。 [!DNL Live Search] ただし、一度に検索できるファセットの数には制限があります。

[シノニム](synonyms.md) とは、ユーザーを適切な製品に導くのに役立てるために定義できる用語です。 ズボンを探すユーザーは、「ズボン」や「スラックス」をタイプする場合があります。 同義語を設定して、これらの検索用語で「ズボン」の結果をユーザーに表示させることができます。

## [!DNL Live Search] workspace

The [!DNL Live Search] [workspace](workspace.md) は、設定をおこなう管理者内の領域です。 [!DNL Live Search] 同義語、ファセット、カテゴリマーチャンダイジングなどの機能。

## イベント

[!DNL Live Search] uses [イベント](events.md) 計算する [インテリジェントマーチャンダイジング](category-merch.md) および [性能](performance.md) ダッシュボード。 イベンティングは、デフォルトの実装で提供されます。 ヘッドレスストアフロントのイベンティングは、手動で有効にする必要があります。

## ウィジェットのカスタマイズ

ほとんどのストア所有者は、 [!DNL Live Search] ウィジェットは、ストアの外観と操作性に合わせています。

ポップオーバーおよび PLP ウィジェットは、必要に応じてカスタム CSS ルールを定義することでスタイルを設定できます。 詳しくは、 [ポップオーバー要素のスタイル設定](storefront-popover-styling.md) および [製品リストページウィジェット](plp-styling.md).

ウィジェットの機能を拡張する場合は、各ウィジェットのソースコードをパブリックリポジトリで使用できます。
このシナリオでは、独自のニーズに合わせて JavaScript をカスタマイズし、サイト上でカスタムコードをホストします。 このカスタムスクリプトは、 [!DNL Live Search] サービスを実行して通常どおりの結果を返し、ウィジェットの機能を制御できます。

* [PLP ウィジェットリポジトリ](https://github.com/adobe/storefront-product-listing-page)
* [検索バーリポジトリ](https://github.com/adobe/storefront-search-as-you-type)

詳細を見る [!DNL Live Search] （内） [技術概要](technical-overview.md).

## [!DNL Live Search] デモ

詳しくは、このビデオをご覧ください。 [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

ライブ検索の使用方法と設定方法に関する詳細なビデオについては、 [に関する完全なデモ [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) トピック。
