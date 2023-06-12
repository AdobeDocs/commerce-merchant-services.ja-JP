---
title: リリースノート
description: Adobe CommerceのAdobe Experience Platformコネクタの最新のリリース情報です。
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: b48f9eadda233f4996f1e1d806ecc973cfd241c2
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 1%

---

# リリースノート

これらのリリースノートには、Experience Platformコネクタの更新が含まれ、以下が含まれます。

* ![新規](../assets/new.svg)  — 新機能
* ![修正点](../assets/fix.svg)  — 修正点および改善点
* ![バグ](../assets/bug.svg)  — 既知の問題

Experience Platformコネクタで使用される拡張機能に関する機能の変更および修正点については、 **サポートされるサービスの更新**.

詳しくは、 [今後のリリース](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) を参照してください。

開発者向けドキュメントを参照してください。 [製品の互換性の詳細](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## サポートされるサービスの更新

これらのリリースノートでは、Experience Platformコネクタで使用される拡張機能に関する機能変更および修正点について説明します。

+++サポートされるサービスの更新

_2023 年 6 月 11 日_

* ![修正点](../assets/fix.svg) - `orderId` コマース注文識別子のプレフィックスが原因で、がコンテキストを渡していませんでした。
* ![修正点](../assets/fix.svg)  — コンテンツセキュリティポリシーの設定を更新しました。

_2023 年 3 月 31 日_

* ![新規](../assets/new.svg)  — という新しい拡張機能が追加されました。 `data-services-b2b` を含む [購買依頼リスト・イベント](events.md#b2b-events) B2B 商人向け
* ![新規](../assets/new.svg)  — が追加されました `uniqueIdentifier` ～に向かって [検索](events.md#search-events) イベント。 この新しいフィールドを使用すると、マーチャントは、どの検索リクエストをどの検索応答に対応させるかを相互に参照できます。

_2022 年 10 月 13 日_

* ![新規](../assets/new.svg) - 2 つ追加 [storefront イベント](events.md): `openCart` および `removeFromCart` をAdobe Commerce Storefront Events SDK およびコレクターに追加しました。
* ![新規](../assets/new.svg)  — のサポートを追加しました [AEM storefront](overview.md#aem-support)

+++

## 2.2.0

_2023 年 3 月 31 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

* ![新規](../assets/new.svg)  — バンドルされた `commerce-data-export` および `saas-export` 依存関係 `experience-platform-connector` 拡張子。 以前は、これらの依存関係を個別にインストールする必要がありました。 これらの依存関係は、マーチャント設定と共に、サーバ側での [バックオフィスイベント](events.md#back-office-events).
* ![新規](../assets/new.svg)  — という新しいバックオフィスイベントが追加されました [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_2023 年 2 月 29 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

* ![新規](../assets/new.svg)  — すべてのExperience Platformコネクタモジュールに対する PHP 8.2 のサポートを追加

## 2.1.0

_2023 年 1 月 18 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

* ![新規](../assets/new.svg)  — 更新された [Experience Platformコネクタ管理](connect-data.md) 独自の AEP Web SDK(alloy) を指定できます。
* ![修正点](../assets/fix.svg) 次を使用してに変更 `identityMap` の代わりに `personID` エッジにプッシュされたデータのプライマリ id を設定する際に使用します。

## 2.0.1

_2022 年 11 月 11 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

* ![修正された問題](../assets/fix.svg) - Adobe Experience Platformコンテキストは、Storefront イベントコレクターと Storefront イベント SDK が正常に読み込まれた後にのみ設定されるようになりました。

## 2.0.0

_2022 年 10 月 13 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

* ![新規](../assets/new.svg)  — 次の場合に独自の AEP Web SDK を指定する機能が追加されました。 [接続](connect-data.md) Adobe CommerceインスタンスからExperience Platform
* ![修正点](../assets/fix.svg)  — データストリーム ID をストレビューではなく Web サイトにスコープする必要があるように、データストリームスコープの要件を更新しました

## 1.0.0

_2022 年 8 月 10 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

* ![新規](../assets/new.svg)  — 一般リリース (GA)
