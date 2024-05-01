---
title: リリースノート
description: の最新のリリース情報 [!DNL Data Connection] Adobe Commerceからの拡張機能。
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: 84094f4249eeb9f98a85e582c52e2c48e0dd9316
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 0%

---

# リリースノート

>[!IMPORTANT]
>
>Experience Platformコネクタの名前をに変更しました [!DNL Data Connection].

これらのリリースノートには、 [!DNL Data Connection] 拡張機能には次の機能が含まれます。

![新規](../assets/new.svg)  – 新機能
![修正](../assets/fix.svg)  – 修正点および改善点
![バグ](../assets/bug.svg)  – 既知の問題

で使用される拡張機能に関連する機能の変更および修正 [!DNL Data Connection] 拡張機能、を参照 **サポートされるサービスのアップデート**.

参照： [今後のリリース](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) リリーススケジュールとサポートについて説明します。

詳しくは、開発者向けドキュメントを参照してください [このモジュールをサポートするCommerceのバージョンについて説明します](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## サポートされるサービスのアップデート

これらのリリースノートは、が使用する拡張機能に関連する機能の変更と修正について説明します [!DNL Data Connection] 拡張機能。

+++サポートされているサービスのアップデート

_2024 年 1 月 24 日（Pt）_

![新規](../assets/new.svg)  – が更新されました `data-services-b2b` という新しい要求イベントを含めるための拡張機能 [deleteRequisitionList](events.md#deleterequisitionlist) b2B マーチャントの場合。

_2023 年 11 月 16 日（Pt）_

![修正](../assets/fix.svg)  – 複数の配送先住所を持つ注文を行った際に、エラーメッセージが正しく表示されない問題を修正しました。
![修正](../assets/fix.svg)  – の問題を修正しました [productPageView](events.md#productpageview) イベント条件 `productListItems.priceTotal` ストアビューで通貨を切り替えた後、イベントフィールドで価格を変換できませんでした。
![修正](../assets/fix.svg)  – の問題を修正しました `productListItems` マーチャントがストアビューを切り替えた際に、通貨コードが更新されなかったイベントフィールド。

_2023 年 10 月 10 日（Pt）_

![新規](../assets/new.svg)  – 新しい注文ステータスイベントを追加しました。 [注文の請求](events-backoffice.md#orderinvoiced), [注文品目の返品を開始しました](events-backoffice.md#orderitemsreturninitiated)、および [注文品目の返品完了](events-backoffice.md#orderitemreturncompleted).
![修正](../assets/fix.svg) - キャッシュを更新した後、通貨設定の変更がイベントに反映されない問題を修正しました。
![修正](../assets/fix.svg)  – 非同期注文配置が有効になっている場合に、注文確認メッセージが表示されないエラーを修正しました。
![新規](../assets/new.svg) - データをに追加しました [addToRequisitionList](events.md#addtorequisitionlist) カテゴリ表示ページのシンプルな製品のイベント。
![修正](../assets/fix.svg)  – の問題を修正しました `selectedOptions` 内のデータ [addToRequisitionList](events.md#addtorequisitionlist) 注文確認ページから商品が追加された際のイベント。
![新規](../assets/new.svg)  – 製品データをに追加しました [addToRequisitionList](events.md#addtorequisitionlist) 「カテゴリ」表示ページから購買依頼リストに製品が追加された場合のイベント。
![新規](../assets/new.svg)  – が追加されました [addToRequisitionList](events.md#addtorequisitionlist) 設定可能な製品が「製品」表示ページから購買依頼リストに追加された場合のイベント。
![新規](../assets/new.svg)  – が追加されました [addToRequisitionList](events.md#addtorequisitionlist) および [removeFromRequisitionList](events.md#removefromrequisitionlist) 購買依頼リストから製品数量が増加または減少するイベント。

_2023 年 6 月 10 日（Pt）_

![修正](../assets/fix.svg)  – の場合の問題を修正しました `orderId` Commerceのオーダー識別子にプレフィックスがあるので、はコンテキストでを渡しませんでした。
![修正](../assets/fix.svg) - コンテンツセキュリティポリシー設定を更新しました。

_2023 年 3 月 30 日（Pt）_

![新規](../assets/new.svg)  – という拡張機能を追加しました。 `data-services-b2b` 次を含む [購買依頼リスト・イベント](events.md#b2b-events) b2B マーチャントの場合。
![新規](../assets/new.svg)  – がを追加しました `uniqueIdentifier` フィールド先 [検索](events.md#search-events) イベント。 この新しいフィールドを使用すると、マーチャントは、検索リクエストと検索応答を相互参照できます。

_2022 年 10 月 12 日（Pt）_

![新規](../assets/new.svg) - 2 つを追加 [ストアフロントイベント](events.md), `openCart` および `removeFromCart`をAdobe Commerce Storefront Events SDK およびコレクターに送信します。
![新規](../assets/new.svg)  – をサポートするようになりました [AEM ストアフロント](overview.md#aem-support).

+++

## 3.1.1

[!BADGE 互換性]{type=Informative tooltip="互換性"}

_2024 年 4 月 4 日（Pt）_

![新規](../assets/new.svg)  – すべての PHP 8.3 のサポートを追加 [!DNL Data Connection] 拡張機能。
![新規](../assets/new.svg)  – 方法に関する記事を追加しました [の統合](mobile-sdk-epc.md) Adobe Experience Platform Mobile SDK とCommerce。

## 3.2.0-beta2

_2024 年 3 月 4 日（Pt）_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

![新規](../assets/new.svg) - ベータ版に参加している場合は、必ずを入手してください `composer.json` ファイルのルートレベルは次のとおりです。 ` "minimum-stability": "beta"`. また、次も追加します `composer require "magento/customers-connector: ^1.2.0"` お客様のプロファイルをCommerce インスタンスから SaaS に送信する場合
![新規](../assets/new.svg)  – にを追加しました。 [カスタム属性の追加](update-xdm.md#update-schema-with-time-series-behavioral-and-back-office-event-data).
![新規](../assets/new.svg)  – にを追加しました。 [プロファイルレコードの収集と送信](connect-data.md#send-customer-profile-data) およびデータをExperience Platformに送信します。

## 3.1.0

_2023 年 11 月 16 日（Pt）_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

![新規](../assets/new.svg) -Experience Platformコネクタの名前がに変更されました [!DNL Data Connection].
![修正](../assets/new.svg) - Adobe IMSがアクセストークンを生成できない場合にエラー応答をログに記録できるようになりました。
![修正](../assets/new.svg)  – 注文履歴を同期しようとしたが、アカウント資格情報を指定していない場合に表示される通知メッセージを追加しました。

## 3.0.0

_2023 年 10 月 10 日（Pt）_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

これはメジャーバージョンリリースです。 [編集](install.md#update-the-data-connection) プロジェクトのルート composer.json ファイル。

![新規](../assets/new.svg)  – への一般公開 [過去の注文を送信](connect-data.md#send-historical-order-data) Experience Platformに対するデータとステータス。
![新規](../assets/new.svg)  – 次の場合に OAuth 2.0 がサポートされるようになりました [設定](connect-data.md#connect-commerce-data-to-adobe-experience-platform) この [!DNL Data Connection] 拡張機能。
![新規](../assets/new.svg) - Adobe Commerce 2.4.3 のサポートを終了。

## 2.3.0

_2023 年 6 月 27 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)  – にを追加しました。 [ストアフロント イベントの送信を無効にする](connect-data.md#data-collection) をExperience Platformに追加します。
![修正](../assets/fix.svg) - コンテンツセキュリティポリシー設定を更新しました。
![修正](../assets/fix.svg) - Commerce 2.4.7 バージョンでのバックオフィスイベントのサポートを修正しました。
![新規](../assets/new.svg)  – に変更を保存する際の、キャッシュの無効化に関する通知メッセージを追加しました [!DNL Data Connection] 拡張機能フォーム。


## 3.0.0-beta1 （内部のみ）

_2023 年 6 月 13 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) - （ベータ版）に機能を追加しました [過去の注文を送信](connect-data.md#beta-send-historical-order-data) Experience Platformに対するデータとステータス。

## 2.2.0

_2023 年 3 月 30 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) - バンドル `commerce-data-export` および `saas-export` を使用した依存関係 `experience-platform-connector` 拡張機能。 以前は、これらの依存関係を個別にインストールする必要がありました。 これらの依存関係とマーチャント設定により、のサーバーサイド処理が可能になります。 [バックオフィスイベント](events-backoffice.md).
![新規](../assets/new.svg)  – という新しいバックオフィスイベントを追加しました [`orderShipmentCompleted`](events-backoffice.md#ordershipmentcompleted).

## 2.1.1

_2023 年 2 月 28 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) - PHP 8.2 の全てのサポートを追加 [!DNL Data Connection] 拡張機能。

## 2.1.0

_2023 年 1 月 17 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)  – が更新されました [[!DNL Data Connection] 拡張機能の管理者](connect-data.md) 独自の AEP Web SDK （alloy）を指定できます。
![修正](../assets/fix.svg) を使用するに変更されました `identityMap` の代わりに `personID` エッジにプッシュされたデータのプライマリ ID を設定する場合。

## 2.0.1

_2022 年 11 月 10 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg) - Storefront Event Collector および Storefront Event SDK が正常に読み込まれた後にのみAdobe Experience Platform コンテキストが設定されるようになりました。

## 2.0.0

_2022 年 10 月 12 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)  – 独自の AEP Web SDK を指定する機能が追加されました [接続](connect-data.md) Experience PlatformへのAdobe Commerce インスタンス。
![修正](../assets/fix.svg) - データストリーム ID を storereview ではなく web サイトにスコープする必要があるように、データストリーム範囲の要件を更新しました。

## 1.0.0

_2022 年 8 月 9 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)  – 一般提供リリース。
