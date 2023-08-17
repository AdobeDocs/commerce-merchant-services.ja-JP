---
title: の概要 [!DNL Payment Services]
description: インストールと使用の方法を学ぶ [!DNL Payment Services] お客様の [!DNL Adobe Commerce] および [!DNL Magento Open Source] web サイト。
role: User
level: Intermediate
exl-id: e4d8d789-fcf6-4aaa-bc4e-42ce21c6dd6c
feature: Payments, Checkout
source-git-commit: b1984085fa5d10c8202d2a982227e183d0b169e8
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# の概要 [!DNL Payment Services]

[!DNL Payment Services] 対象： [!DNL Adobe Commerce] および [!DNL Magento Open Source] は、サンドボックステストやシンプルなセットアップを含む、自動セルフサービスソリューションで、コマース Web サイトの堅牢で安全な支払い処理を提供します。

![[!DNL Payment Services] 拡張機能の管理ビュー](assets/admin-view.png)

小規模企業、中規模企業、大規模企業を問わず、この支払いソリューションにより、運用上のオーバーヘッドの削減、売上高の増加、買い物客体験全体を改善する便利なツールの提供が可能になります。

[!DNL Payment Services] 次に該当：

* セットアップと保守が容易
* 利益を最大化するように設計
* 安全で安全な
* お客様の支払いニーズを満たすように設計されています
* 管理者内の自己完結型

## 機能

>[!NOTE]
>
>ここで説明する機能の一部は、GA(General Availability) リリースではまだ利用できない可能性があります。

[!DNL Payment Services] は、オンラインチェックアウト用のワンストップショップです（決済、返金から支払いを受けるまで）。 購入者に最適なエクスペリエンスを作成するために必要なインサイトと制御を提供する強力なツールを提供します。

* [**オンボーディング**](onboard.md) — このプロセスは、商用サインアップ、技術的な設定、権限、サンドボックス環境の設定、ライブ支払いの有効化の手順をガイドします。
* [**支払いオプション**](payments-options.md) — 支払いオプションを設定して、店舗（またはマルチストア）の顧客が利用できる方法をカスタマイズします。
* **キャッシュフロー管理財務報告** — 同期 [支払詳細](order-payment-status.md) 処理済数量、支払残高、および詳細に対する完全な透明性を得るための注文と [トランザクションレベルのレポート](payouts.md) 財務上の調整の場合。
* **透明性の高い価格設定** — 価格は明確で前もって設定されています。
* **効率的なチェックアウトエクスペリエンス** — 迅速でシンプルなチェックアウトに対する障壁を取り除き、常連客を作成し、 [カード保管](https://experienceleague-review.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) および [即時購入](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) (Adobe Commerceの場合はデフォルトで有効 ) 機能です。

## 使用可否

[!DNL Payment Services] は、次の場所で使用できます： [!DNL Adobe Commerce] および [!DNL Magento Open Source]. The [!DNL Payment Services] 拡張機能は、 [!DNL Adobe Commerce] バージョン 2.4.x.

現在、 [!DNL Payment Services] は、次の国で利用できます。

* 米国（米国）
* カナダ (CA)
* オーストラリア (AUS)
* フランス (FR)
* 英国 (UK)

詳しくは、 [ライフサイクルポリシー](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html) そして [[!DNL Payment Services] リリースノート](release-notes.md) ページを参照してください。

### 受け入れ済みクレジットカードと通貨

[!DNL Payment Services] 国の通貨を受け入れる [それが利用可能な](#availability).

PayPal がサポートする通貨を確認するには、 [サポートされる通貨のドキュメント](https://developer.paypal.com/docs/reports/reference/paypal-supported-currencies/).

PayPal がサポートする支払い方法を確認するには、 [支払い方法に関するドキュメント](https://developer.paypal.com/docs/checkout/payment-methods/).

## 基本を学ぶ

オンボーディングとセットアップ [!DNL Payment Services] は、いくつかの手順で完了します。

1. を取得します [[!DNL Payment Services] 拡張](install.md).
1. コマースインスタンスをコマースサービスに接続します。
1. サンドボックスサービスをオンボーディングし、設定します。
1. 有効にする [!DNL Payment Services] を支払い方法として使用し、テスト支払の処理を開始します。
1. Web サイトのライブ支払いを有効にするには、完全なマーチャントオンボーディングを行ってください。
1. 有効化 [!DNL Payment Services] ライブモードでライブ支払いの処理を開始します。

すべての手順を確認し、オンボーディングプロセスを開始するには、 [オンボード [!DNL Payment Services]](onboard.md).

## [!DNL Payment Services] デモ

詳しくは、このビデオをご覧ください。 [!DNL Payment Services]:

>[!VIDEO](https://video.tv.adobe.com/v/343990?quality=12)
