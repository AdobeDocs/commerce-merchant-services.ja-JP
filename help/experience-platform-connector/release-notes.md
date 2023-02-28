---
title: リリースノート
description: Adobe CommerceのAdobe Experience Platformコネクタの最新のリリース情報です。
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: 57d0d0604e871a0d8a76bfd2c006250b55f0eeb1
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 1%

---

# リリースノート

これらのリリースノートには、Experience Platformコネクタの更新が含まれ、以下が含まれます。

* ![新規](../assets/new.svg)  — 新機能
* ![修正点](../assets/fix.svg)  — 修正点および改善点
* ![バグ](../assets/bug.svg)  — 既知の問題

Experience Platformコネクタで使用される拡張機能に関する機能の変更および修正点については、 **サポートされるサービスの更新**.

詳しくは、 [今後のリリース](https://experienceleague.adobe.com/docs/commerce-operations/release/schedule.html) を参照してください。

詳しくは、 [使用可否](https://experienceleague.adobe.com/docs/commerce-operations/release/availability.html) 製品の互換性については、を参照してください。

## サポートされるサービスの更新

これらのリリースノートでは、Experience Platformコネクタで使用される拡張機能に関する機能変更および修正点について説明します。

+++サポートされるサービスの更新

_2022 年 10 月 13 日_

* ![新規](../assets/new.svg) - 2 つ追加 [storefront イベント](events.md): `openCart` および `removeFromCart` をAdobe Commerce Storefront Events SDK およびコレクターに追加しました。
* ![新規](../assets/new.svg)  — のサポートを追加しました [AEM storefront](overview.md#aem-support)

+++

## 2.1.1

_2023 年 2 月 29 日_

* ![新規](../assets/new.svg)  — すべてのExperience Platformコネクタモジュールに対する PHP 8.2 のサポートを追加

## 2.1.0

_2023 年 1 月 18 日_

* ![新規](../assets/new.svg)  — 更新された [Experience Platformコネクタ管理](connect-data.md) 独自の AEP Web SDK(alloy) を指定できます。 また、バックオフィスのベータ版プログラムに登録した商人が [バックオフィスのイベントデータ](connect-data.md#data-collection) をエッジに追加します。 これらのイベントには、 [注文ステータス情報](events.md#beta-order-status-events) 注文について（注文が行われたか、キャンセルされたか、返金されたか、または発送されたかなど）。 バックオフィスベータプログラムに参加したい場合は、 [drios@adobe.com](mailto:drios@adobe.com).
* ![修正点](../assets/fix.svg) 次を使用してに変更 `identityMap` の代わりに `personID` エッジにプッシュされたデータのプライマリ id を設定する際に使用します。

## 2.0.1

_2022 年 11 月 11 日_

* ![修正された問題](../assets/fix.svg) - Adobe Experience Platformコンテキストは、Storefront イベントコレクターと Storefront イベント SDK が正常に読み込まれた後にのみ設定されるようになりました。

## 2.0.0

_2022 年 10 月 13 日_

* ![新規](../assets/new.svg)  — 次の場合に独自の AEP Web SDK を指定する機能が追加されました。 [接続](connect-data.md) Adobe CommerceインスタンスからExperience Platform
* ![修正点](../assets/fix.svg)  — データストリーム ID をストレビューではなく Web サイトにスコープする必要があるように、データストリームスコープの要件を更新しました

## 1.0.0

_2022 年 8 月 10 日_

* ![新規](../assets/new.svg)  — 一般リリース (GA)

## ドキュメント

詳しくは、以下を参照してください。

* [Adobe Commerce開発者向けドキュメント](https://devdocs.magento.com/)
* [Adobe Commerce User Guide](https://docs.magento.com/user-guide/)
