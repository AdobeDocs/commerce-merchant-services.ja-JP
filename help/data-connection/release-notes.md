---
title: リリースノート
description: の最新のリリース情報 [!DNL Data Connection] Adobe Commerceからの拡張。
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: c95b1fc9393c507dd757c74c30473590760d47a6
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 0%

---

# リリースノート

>[!IMPORTANT]
>
>Experience Platformコネクタの名前は「 [!DNL Data Connection].

これらのリリースノートには、 [!DNL Data Connection] 拡張機能と含まれるもの：

![新規](../assets/new.svg)  — 新機能
![修正点](../assets/fix.svg)  — 修正点および改善点
![バグ](../assets/bug.svg)  — 既知の問題

の拡張機能に関する機能の変更および修正については、 [!DNL Data Connection] 拡張機能については、 **サポートされるサービスの更新**.

詳しくは、 [今後のリリース](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) を参照してください。

開発者向けドキュメントを参照してください。 [このモジュールをサポートするコマースバージョンを確認します。](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## サポートされるサービスの更新

これらのリリースノートでは、 [!DNL Data Connection] 拡張子。

+++サポートされるサービスの更新

_2024 年 1 月 25 日_

![新規](../assets/new.svg)  — 更新された `data-services-b2b` 次の名前の新しい購買依頼イベントを含める拡張： [deleteRequisitionList](events.md#deleterequisitionlist) B2B 商人にとって

_2023 年 11 月 17 日_

![修正点](../assets/fix.svg)  — 複数の送付先住所を持つ注文をすると、エラーメッセージが正しく表示されない問題を修正しました。
![修正点](../assets/fix.svg) - [productPageView](events.md#productpageview) イベント `productListItems.priceTotal` ストア表示で通貨を切り替えた後、イベントフィールドで価格が変換されなかった問題を修正しました。
![修正点](../assets/fix.svg) - `productListItems` 商人がストア表示を切り替えた際に通貨コードが更新されなかったイベントフィールド。

_2023 年 10 月 11 日_

![新規](../assets/new.svg)  — 新しい注文ステータスイベントが追加されました。 [注文請求済み](events-backoffice.md#orderinvoiced), [注文品目の返品開始](events-backoffice.md#orderitemsreturninitiated)、および [注文品目の返品完了](events-backoffice.md#orderitemreturncompleted).
![修正点](../assets/fix.svg)  — キャッシュを更新した後、通貨設定の変更がイベントに反映されない問題を修正しました。
![修正点](../assets/fix.svg)  — 非同期の注文配置が有効な場合に注文確認メッセージが表示されない場合のエラーを修正しました。
![新規](../assets/new.svg)  — にデータを追加しました [addToRequisitionList](events.md#addtorequisitionlist) イベントを追加できます。
![修正点](../assets/fix.svg) - `selectedOptions` データを [addToRequisitionList](events.md#addtorequisitionlist) イベントに追加されます。
![新規](../assets/new.svg)  — 製品データをに追加しました [addToRequisitionList](events.md#addtorequisitionlist) イベントを追加します。
![新規](../assets/new.svg)  — 追加済み [addToRequisitionList](events.md#addtorequisitionlist) イベントを追加します。
![新規](../assets/new.svg)  — 追加済み [addToRequisitionList](events.md#addtorequisitionlist) および [removeFromRequisitionList](events.md#removefromrequisitionlist) イベント（製品数量が購買依頼リストから増加または減少した場合）

_2023 年 6 月 11 日_

![修正点](../assets/fix.svg)  — 次の場合に発生する問題を修正しました。 `orderId` コマース注文識別子のプレフィックスが原因で、コンテキストを渡しませんでした。
![修正点](../assets/fix.svg)  — コンテンツセキュリティポリシーの設定を更新しました。

_2023 年 3 月 31 日_

![新規](../assets/new.svg)  — という拡張機能が追加されました。 `data-services-b2b` を含む [購買依頼リスト・イベント](events.md#b2b-events) B2B 商人にとって
![新規](../assets/new.svg)  — が追加されました。 `uniqueIdentifier` ～に向かって [検索](events.md#search-events) イベント。 この新しいフィールドでは、マーチャントが検索リクエストと検索応答を相互参照できます。

_2022 年 10 月 13 日_

![新規](../assets/new.svg) - 2 つ追加済み [storefront イベント](events.md), `openCart` および `removeFromCart`をAdobe Commerce Storefront Events SDK and Collector に追加します。
![新規](../assets/new.svg)  — のサポートを追加しました [AEM storefront](overview.md#aem-support).

+++

## 3.2.0-beta2

_2024 年 3 月 5 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

![新規](../assets/new.svg)  — ベータ版に参加している場合は、 `composer.json` ファイルのルートレベルは次のようになります。 ` "minimum-stability": "beta"`.
![新規](../assets/new.svg)  — 次の機能を追加しました。 [カスタム属性を追加](update-xdm.md#update-schema-with-time-series-behavioral-and-back-office-event-data).
![新規](../assets/new.svg)  — 次の機能を追加しました。 [プロファイルレコードの収集と送信](connect-data.md#send-customer-profile-data) およびデータをExperience Platformに

## 3.1.0

_2023 年 11 月 17 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

![新規](../assets/new.svg) -Experience Platformコネクタの名前が [!DNL Data Connection].
![修正点](../assets/new.svg)  — エラーがアクセストークンを生成できない場合にAdobe IMSの応答を記録する機能を追加しました。
![修正点](../assets/new.svg)  — 過去の注文件数を同期しようとしたが、アカウントの資格情報が指定されていない場合に通知メッセージが追加されました。

## 3.0.0

_2023 年 10 月 11 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

これはメジャーバージョンのリリースです。 [編集](install.md#update-the-data-connection) プロジェクトのルート composer.json ファイル。

![新規](../assets/new.svg)  — に対する一般公開 [履歴注文を送信](connect-data.md#send-historical-order-data) データとステータスをExperience Platformに
![新規](../assets/new.svg)  — 次の場合に、OAuth 2.0 のサポートが追加されました。 [設定](connect-data.md#connect-commerce-data-to-adobe-experience-platform) の [!DNL Data Connection] 拡張子。
![新規](../assets/new.svg) - Adobe Commerce 2.4.3 のサポートを終了しました。

## 2.3.0

_2023 年 6 月 28 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)  — 次の機能を追加しました。 [storefront イベントの送信をオフにする](connect-data.md#data-collection) Experience Platformに
![修正点](../assets/fix.svg)  — コンテンツセキュリティポリシーの設定を更新しました。
![修正点](../assets/fix.svg) - Commerce 2.4.7 バージョンでのバックオフィスイベントのサポートを修正しました。
![新規](../assets/new.svg)  — 変更を [!DNL Data Connection] 拡張フォーム。


## 3.0.0-beta1（内部のみ）

_2023 年 6 月 14 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) - （ベータ版） [履歴注文を送信](connect-data.md#beta-send-historical-order-data) データとステータスをExperience Platformに

## 2.2.0

_2023 年 3 月 31 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)  — バンドルされた `commerce-data-export` および `saas-export` 依存関係 `experience-platform-connector` 拡張子。 以前は、これらの依存関係を個別にインストールする必要がありました。 これらの依存関係は、マーチャント設定と共に、サーバ側での [バックオフィスイベント](events-backoffice.md).
![新規](../assets/new.svg)  — という新しいバックオフィスイベントが追加されました。 [`orderShipmentCompleted`](events-backoffice.md#ordershipmentcompleted).

## 2.1.1

_2023 年 2 月 29 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) - PHP 8.2 のサポートを追加しました。 [!DNL Data Connection] 拡張機能。

## 2.1.0

_2023 年 1 月 18 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)  — 更新された [[!DNL Data Connection] 拡張機能管理者](connect-data.md) 独自の AEP Web SDK(alloy) を指定できます。
![修正点](../assets/fix.svg) 次を使用してに変更 `identityMap` の代わりに `personID` エッジにプッシュされたデータのプライマリ id を設定する際に使用します。

## 2.0.1

_2022 年 11 月 11 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正点](../assets/fix.svg) - Adobe Experience Platformコンテキストは、Storefront イベントコレクターと Storefront イベント SDK が正常に読み込まれた後にのみ設定されるようになりました。

## 2.0.0

_2022 年 10 月 13 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)  — 次の場合に独自の AEP Web SDK を指定する機能が追加されました。 [接続](connect-data.md) Adobe CommerceインスタンスをExperience Platformに
![修正点](../assets/fix.svg)  — データストリーム ID をストアレビューではなく Web サイトにスコープする必要があるように、データストリームスコープの要件を更新しました。

## 1.0.0

_2022 年 8 月 10 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) - GA リリース。
