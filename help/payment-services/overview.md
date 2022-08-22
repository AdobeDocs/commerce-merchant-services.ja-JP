---
title: の概要 [!DNL Payment Services]
description: インストールと使用の方法を学ぶ [!DNL Payment Services] お客様の [!DNL Adobe Commerce] および [!DNL Magento Open Source] web サイト。
role: User
level: Intermediate
exl-id: e4d8d789-fcf6-4aaa-bc4e-42ce21c6dd6c
source-git-commit: 3f753f6a91c9f2c29def90d323c004a689056e71
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# の概要 [!DNL Payment Services]

[!DNL Payment Services] 対象 [!DNL Adobe Commerce] および [!DNL Magento Open Source] は、サンドボックステストやシンプルなセットアップを含む、自動セルフサービスソリューションで、コマース Web サイトの堅牢で安全な支払い処理を提供します。

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
* **透明性の高い価格設定** — 価格は明確で前もって設定されています。何が見えるかは、得るものです。

## 使用可否

[!DNL Payment Services] は、次の場所で使用できます： [!DNL Adobe Commerce] および [!DNL Magento Open Source]. この [!DNL Payment Services] 拡張機能は、 [!DNL Adobe Commerce] バージョン 2.4.x.

詳しくは、 [ライフサイクルポリシー](https://devdocs.magento.com/release/lifecycle-policy.html){target=&quot;_blank&quot;} および [[!DNL Payment Services] リリースノート](release-notes.md) 詳細なリリースおよびバージョン固有の情報に関するページ

## 受け入れ済みクレジットカードと通貨

現在、 [!DNL Payment Services] は、次の場所でのみ使用できます。

* 米国（米国）と米ドル (USD) 通貨を受け入れます。
* カナダ (CA) およびカナダドル (CAD) の通貨を受け入れます。

詳しくは、 [PayPal の通貨の可用性](https://developer.paypal.com/docs/platforms/checkout/reference/country-availability-advanced-cards/) ドキュメントを参照してください。

## はじめに

オンボーディングとセットアップ [!DNL Payment Services] は、いくつかの手順で完了します。

1. を取得 [[!DNL Payment Services] 拡張](install.md).
1. コマースインスタンスをコマースサービスに接続します。
1. サンドボックスサービスをオンボーディングし、設定します。
1. 有効にする [!DNL Payment Services] を支払い方法として使用し、テスト支払の処理を開始します。
1. Web サイトのライブ支払いを有効にするには、完全なマーチャントオンボーディングを行ってください。
1. 有効化 [!DNL Payment Services] ライブモードでライブ支払いの処理を開始します。

すべての手順を確認し、オンボーディングプロセスを開始するには、 [オンボード [!DNL Payment Services]](onboard.md).

## [!DNL Payment Services] デモ

詳しくは、このビデオをご覧ください。 [!DNL Payment Services]:

>[!VIDEO](https://video.tv.adobe.com/v/343990?quality=12)