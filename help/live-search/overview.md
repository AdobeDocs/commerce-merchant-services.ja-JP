---
title: の概要 [!DNL Live Search]
description: '"[!DNL Live Search] Adobe Commerceからは、素早く、超関連性が高く、直感的な検索エクスペリエンスを提供します。」'
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: c77b2f9cb55d3eb339dcc900ce606b94c592f559
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# の概要 [!DNL Live Search]

[!DNL Live Search] は、標準の検索機能に代わるAdobe Commerceのサービスです。 The [!DNL Live Search] モジュールが Composer と共にインストールされ、 [!DNL Commerce] へのインストール [!DNL Live Search] [サービス](../landing/saas.md). 設定すると、デフォルトの検索テキストフィールドが [!DNL Live Search] テキストフィールド。 [!DNL Live Search] また、は、検索結果を参照する際に堅牢なフィルタリング機能を提供する製品リストページ (PLP) ウィジェットをインストールします。

[!DNL Live Search] 次の場所に表示される： *マーケティング* 下のメニュー *SEO と検索* （内） [!DNL Commerce] *管理者*.

アーキテクチャのAdobe Commerce側には、検索のホストが含まれます *管理者*、カタログデータの同期、およびクエリサービスの実行を行う。 後 [!DNL Live Search] がインストールおよび設定されると、Adobe Commerceは検索およびカタログデータの SaaS サービスとの共有を開始します。 この時点で、管理者ユーザーは検索の設定、カスタマイズ、管理をおこなうことができます [ファセット](facets.md), [同義語](synonyms.md)、および [マーチャンダイジングルール](category-merch.md).

![ライブ検索のアーキテクチャ図](assets/architecture-diagram.svg)

## ライブ検索コンポーネント

* [!DNL Live Search] [ポップオーバー](storefront-popover.md) は、検索結果を含む検索フィールドの下に開くボックスです。
* [製品リストページウィジェット](plp-styling.md) は、ファセットとシノニムのサポートを含む検索可能な製品リストページを提供します。
* AEM CIFコンポーネント： [ポップオーバーウィジェット](https://github.com/adobe/aem-cif-guides-venia/pull/319) そして [PLP ウィジェット](https://github.com/adobe/aem-cif-guides-venia/pull/320) AEMサイトが [!DNL Live Search].
* [[!DNL Live Search] 管理者](workspace.md) は、ルール、ファセットおよびシノニムを設定する場所です。
* 検索アダプタは、 [!DNL Live Search]. ヘッドレスおよびカスタム実装に推奨されます。

## [!DNL Live Search] デモ

詳しくは、このビデオをご覧ください。 [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

ライブ検索の使用方法と設定方法に関する詳細なビデオについては、 [に関する完全なデモ [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) トピック。
