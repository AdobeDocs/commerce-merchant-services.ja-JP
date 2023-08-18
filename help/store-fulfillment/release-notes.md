---
title: '[!DNL Store Fulfillment by Walmart Commerce Technologies] リリースノート'
description: 「リリースノートで [!DNL Store Fulfillment by Walmart Commerce Technologies] リリース。」
role: Admin, User, Leader
feature: Shipping/Delivery, Release Notes
exl-id: 04dcec10-fff8-483d-a2c1-4b58e063e0f0
source-git-commit: 78b09113e72382053b01d6016276bae3aa545fa3
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 2%

---

# リリースノート

以下のリリースノートでは、 [!DNL Store Fulfillment Services by Walmart Commerce Technologies] およびを含めます。

![新規](../assets/new.svg) 新機能
![修正された問題](../assets/fix.svg) 修正点および改善点
![既知の問題](../assets/bug.svg) 既知の問題

## v1.5.0

*2023 年 8 月 4 日*

[!BADGE 互換性]{type=Informative tooltip="互換性"}[Adobe Commerce 2.4.4～2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)（2.4.6-p1、2.4.5-p3 および 2.4.4-p4 セキュリティパッチリリースを含む）

このリリースには、次の更新が含まれています。

![新規](../assets/fix.svg) をサポートするように拡張機能を更新しました。 [Adobe Commerce security patch リリース](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/security-patches/overview.html) 2.4.6-p1、2.4.5-p3 および 2.4.4-p4。

![新規](../assets/new.svg)<!-- WMTP-918 --> のサポートを追加しました。 [非同期送信](sales-emails.md) セールスメールの設定オプション。 バージョン 1.5.0 にアップグレードしたマーチャントには、すぐに E メールを送信するか（デフォルト）、非同期で E メールを送信するかの選択が可能です。

![新規](../assets/new.svg)<!-- WMTP-916--> 更新された [ソース設定](merchant-store-configuration.md) 国際電話番号形式をサポートする。

![新規](../assets/new.svg) 払い戻し金額が残りの金額または請求済みの金額を超えないようにするロジックを追加しました。

![新規](../assets/new.svg)<!-- WMTP-882 --> 置換済み `google.map.LatLng` オブジェクトに JSON リテラルを含め、の古いバージョンとの互換性をサポートします。 [!DNL Google Maps].

![修正された問題](../assets/fix.svg)<!-- WMTP- --> を作成するスクリプトを更新しました。 `[!DNL Available for Store Pickup]` および `[!DNL Available for Home Delivery]` 属性カテゴリの競合を防ぐための製品属性。

![修正された問題](../assets/fix.svg)<!-- WMTP-915 --> 一部のエンティティの読み込みと保存時に無限ループが発生する、互換性の問題を修正しました。

![修正された問題](../assets/fix.svg)<!-- WMTP-921 --> を修正しました。 [!DNL Ship to Store] 製品の詳細ページ (PDP) から買い物かごに品目が追加された際に、トリガーからの見積もり検証。

![修正された問題](../assets/fix.svg)<!-- WMTP- 932 --> お客様が、家庭での配信の資格を持たない品目に対して、ホームでの配信方法を選択できる問題を修正しました。

![修正された問題](../assets/fix.svg) インストールの更新：

- <!-- WMTP-880--> Web サイトをインストールする際に、間違ったコードが返される問題を修正しました。 [!DNL Store Fulfillment] 拡張子。

- <!-- WMTP-878--> SKU 整数の場合、インストール時にデータタイプを文字列タイプにキャストする必要がある問題を修正しました。

![修正された問題](../assets/fix.svg)<!-- WMTP-915--> チェックインエラーコードが見つからないことが原因で発生するエラーを修正しました。

![修正された問題](../assets/fix.svg)<!-- WMTP-932 --> ディスペンス操作時の部分的な却下に関するバグを修正しました。

![新規](../assets/new.svg)<!-- WMTP-953 --> API エンドポイントのキャンセルを更新し、ステータスパラメーターをオプションのオブジェクトとして使用するようにしました。

![新規](../assets/new.svg)<!-- WMTP-960 --> Despinse API エンドポイントのログの詳細を改善しました。

## v1.4.0

*2023 年 4 月 14 日*

[!BADGE 互換性]{type=Informative tooltip="互換性"}

![新規](../assets/fix.svg) [!DNL Store Fulfillment] は今 [～と互換性がある [!DNL Adobe Commerce] 2.4.4～2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.3.0

*2023 年 2 月 28 日*

[!BADGE 互換性]{type=Informative tooltip="互換性"}

このリリースには、次の更新が含まれています。

![新規](../assets/fix.svg)<!-- WMTP-795 --> システム構成設定の既定の範囲を Web サイトからグローバルに変更することで、特定のサイトの Store Fulfilment ソリューションを無効にする機能を追加しました。

## v1.2.0

*2022 年 9 月 28 日*

[!BADGE 互換性]{type=Informative tooltip="互換性"}

このリリースには、次の更新が含まれています。

![新規](../assets/fix.svg) [!DNL Store Fulfillment] は今 [～と互換性がある [!DNL Adobe Commerce] 2.4.4～2.4.5](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.1.0

*2022 年 7 月 16 日*

[!BADGE 互換性]{type=Informative tooltip="互換性"}

安定性：一般可用性

![新規](../assets/fix.svg)<!-- WMTP-731 --> を簡素化し、 [チェックインエクスペリエンス設定](check-in-experience-setup.md) デフォルトの車のメーカーとモデルの選択を追加することにより、Store Assist アプリ用に。 以前のバージョンでは、商人は車の製造とモデルの選択を手動で設定する必要がありました。

## v1.0.0

*2022 年 3 月 5 日*

[!BADGE 互換性]{type=Informative tooltip="互換性"}

安定性：一般可用性

## ストアアシストアプリ

Store Assist アプリの新しいリリースについて詳しくは、 [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.
