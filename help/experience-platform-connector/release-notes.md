---
title: リリースノート
description: Adobe CommerceのAdobe Experience Platformコネクタの最新のリリース情報です。
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: 5e6cf955080338e00f23eaadeaa0192798126151
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 1%

---

# リリースノート

これらのリリースノートには、Experience Platformコネクタの更新が含まれ、以下が含まれます。

![新規](../assets/new.svg)  — 新機能
![修正点](../assets/fix.svg)  — 修正点および改善点
![バグ](../assets/bug.svg)  — 既知の問題

Experience Platformコネクタで使用される拡張機能に関する機能の変更および修正点については、 **サポートされるサービスの更新**.

詳しくは、 [今後のリリース](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) を参照してください。

開発者向けドキュメントを参照してください。 [このモジュールをサポートするコマースバージョンを確認します。](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## サポートされるサービスの更新

これらのリリースノートでは、Experience Platformコネクタで使用される拡張機能に関する機能変更および修正点について説明します。

+++サポートされるサービスの更新

_2023 年 10 月 11 日_

![新規](../assets/new.svg)  — 新しい注文ステータスイベントが追加されました。 [注文請求済み](events.md#orderinvoiced), [注文品目の返品開始](events.md#orderitemsreturninitiated)、および [注文品目の返品完了](events.md#orderitemreturncompleted).
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

![新規](../assets/new.svg)  — という新しい拡張機能が追加されました。 `data-services-b2b` を含む [購買依頼リスト・イベント](events.md#b2b-events) B2B 商人にとって
![新規](../assets/new.svg)  — が追加されました。 `uniqueIdentifier` ～に向かって [検索](events.md#search-events) イベント。 この新しいフィールドでは、マーチャントが検索リクエストと検索応答を相互参照できます。

_2022 年 10 月 13 日_

![新規](../assets/new.svg) - 2 つ追加済み [storefront イベント](events.md), `openCart` および `removeFromCart`をAdobe Commerce Storefront Events SDK and Collector に追加します。
![新規](../assets/new.svg)  — のサポートを追加しました [AEM storefront](overview.md#aem-support).

+++

## 3.0.0

_2023 年 10 月 11 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

![新規](../assets/new.svg)  — に対する一般公開 [履歴注文を送信](connect-data.md#send-historical-order-data) データとステータスをExperience Platformに
![新規](../assets/new.svg)  — 次の場合に、OAuth 2.0 のサポートが追加されました。 [設定](connect-data.md#connect-commerce-data-to-adobe-experience-platform) Experience Platformコネクタ
![新規](../assets/new.svg) - Adobe Commerce 2.4.3 のサポートを終了しました。

## 2.3.0

_2023 年 6 月 28 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)  — 次の機能を追加しました。 [storefront イベントの送信をオフにする](connect-data.md#data-collection) Experience Platformに
![修正点](../assets/fix.svg)  — コンテンツセキュリティポリシーの設定を更新しました。
![修正点](../assets/fix.svg) - Commerce 2.4.7 バージョンでのバックオフィスイベントのサポートを修正しました。
![新規](../assets/new.svg)  — 変更を「Experience Platformコネクタ」フォームに保存したときのキャッシュの無効化に関する通知メッセージを追加しました。


## 3.0.0-beta1（内部のみ）

_2023 年 6 月 14 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) - （ベータ版） [履歴注文を送信](connect-data.md#beta-send-historical-order-data) データとステータスをExperience Platformに この機能は、ベータ版ユーザーのみが使用できます。 ベータ版に参加するには、以下のアドレス宛てにメールを送信します。 `dataconnection@adobe.com`.

## 2.2.0

_2023 年 3 月 31 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)  — バンドルされた `commerce-data-export` および `saas-export` 依存関係 `experience-platform-connector` 拡張子。 以前は、これらの依存関係を個別にインストールする必要がありました。 これらの依存関係は、マーチャント設定と共に、サーバ側での [バックオフィスイベント](events.md#back-office-events).
![新規](../assets/new.svg)  — という新しいバックオフィスイベントが追加されました。 [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_2023 年 2 月 29 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) - PHP 8.2 のサポートを追加し、すべてのExperience Platformコネクタ拡張をサポート。

## 2.1.0

_2023 年 1 月 18 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)  — 更新された [Experience Platformコネクタ管理者](connect-data.md) 独自の AEP Web SDK(alloy) を指定できます。
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
