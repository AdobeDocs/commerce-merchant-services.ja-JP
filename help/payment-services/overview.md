---
title: の概要 [!DNL Payment Services]
description: インストール方法と使用方法を学ぶ [!DNL Payment Services] お客様に最適な、堅牢で安全な自動支払い処理ソリューションです。 [!DNL Adobe Commerce] および [!DNL Magento Open Source] web サイト。
role: User
level: Intermediate
exl-id: e4d8d789-fcf6-4aaa-bc4e-42ce21c6dd6c
feature: Payments, Checkout
source-git-commit: ff83c83a054e5b14814cc3076744c5517081a80f
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# の概要 [!DNL Payment Services]

[!DNL Payment Services] （用） [!DNL Adobe Commerce] および [!DNL Magento Open Source] は、Commerce web サイトに堅牢で安全な支払い処理を提供するためのサンドボックステストやシンプルなセットアップを含む、自動セルフサービスソリューションです。

![[!DNL Payment Services] 拡張機能の管理者ビュー](assets/admin-view.png){width="300" zoomable="yes"}

この支払いソリューションは、小規模ビジネス、中堅企業、大企業を問わず、運用にかかる諸経費の削減、収益の増加、買い物客エクスペリエンス全体の改善に役立つツールの提供に役立ちます。

[!DNL Payment Services] は：

* セットアップとメンテナンスが容易
* 利益を最大化するように設計
* 安全でセキュア
* お客様のすべての支払いニーズを満たすように設計
* 管理者内での自己完結型

## 機能

>[!NOTE]
>
>ここで説明する機能の一部は、まだ GA （一般提供）リリースでは使用できない場合があります。

[!DNL Payment Services] は、オンラインチェックアウト（決済と払い戻しから支払い済みまで）のためのワンストップショップです。 購入者にとって最適なエクスペリエンスを作成するために必要なインサイトと制御を提供する強力なツールを提供します。

* [**オンボーディング**](onboard.md) – このプロセスに従って、商用のサインアップ、技術設定、使用権限、サンドボックス環境の設定、ライブ支払いの有効化を行うことができます。
* [**支払いオプション**](payments-options.md) – 支払いオプションを設定して、ストア（またはマルチストア）の顧客が使用できる方法をカスタマイズします。
* **キャッシュ フロー管理財務報告** – 同期する [支払いの詳細](order-payment-status.md) 処理量、支払い残高を完全に透明にするための注文を含む、 [支払額](payouts.md)、および詳細 [トランザクションレベルのレポート](transactions.md) 財務調整とトランザクションの可視性の最大化を実現します。
* **透明な価格設定** – 価格は明確かつ事前に設定されており、表示されるものは実際の価格です。
* **効率的なチェックアウトエクスペリエンス** – 迅速かつシンプルなチェックアウトに対する障壁を取り除き、次の機能を使用して常連客を作成します。 [カードヴォールティング](vaulting.md) および [即時購入](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) （Adobe Commerceではデフォルトで有効）機能。

## 対象

[!DNL Payment Services] は次のユーザーが利用できます [!DNL Adobe Commerce] および [!DNL Magento Open Source]. この [!DNL Payment Services] 拡張機能は、と互換性を持つようになりました [!DNL Adobe Commerce] バージョン 2.4.x

現在、 [!DNL Payment Services] 完全なサポートを提供（経由 [詳細オンボーディング](../payment-services/production.md#advanced-onboarding)）に設定する必要があります。

* 米国（米国）
* カナダ （カナダ）
* オーストラリア （AUS）
* フランス （FR）
* 英国（UK）

支払いサービスの提供 [高速チェックアウト機能](../payment-services/payments-options.md) （支払オプションのサブセット）（その他） [オンボーディング中に使用可能な国](../payment-services/production.md#complete-merchant-onboarding).

参照： [ライフサイクルポリシー](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html) および [[!DNL Payment Services] リリースノート](release-notes.md) リリースおよびバージョン固有の情報について詳しくは、ページを参照してください。

### 使用可能なクレジットカードおよび通貨

[!DNL Payment Services] 国の通貨を受け入れる [利用可能な](#availability). 参照： [通貨の設定](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) を参照してください。

PayPal がサポートする通貨を確認するには、以下を参照してください。 [サポートされる通貨に関するドキュメント](https://developer.paypal.com/docs/reports/reference/paypal-supported-currencies/).

PayPal がサポートする支払い方法を確認するには、 [支払い方法ドキュメント](https://developer.paypal.com/docs/checkout/payment-methods/).

## 基本を学ぶ

オンボーディングと設定 [!DNL Payment Services] は、次のいくつかの手順で完了します。

1. を取得 [[!DNL Payment Services] 拡張子](install.md).
1. Commerce インスタンスをCommerce サービスに接続します。
1. オンボードし、サンドボックスサービスを設定します。
1. Enable （有効） [!DNL Payment Services] お支払い方法として、テスト支払いの処理を開始します。
1. マーチャントのオンボーディングを完了して、web サイトのライブ支払いを有効にします。
1. Activate [!DNL Payment Services] ライブモードでライブ支払いの処理を開始します。

すべての手順を取得し、オンボーディングプロセスを開始するには、を参照してください。 [Onboard [!DNL Payment Services]](onboard.md).

## [!DNL Payment Services] デモ

詳しくは、このビデオをご覧ください。 [!DNL Payment Services]:

>[!VIDEO](https://video.tv.adobe.com/v/343990?quality=12)
