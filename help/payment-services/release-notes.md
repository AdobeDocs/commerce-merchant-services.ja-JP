---
title: '"[!DNL Payment Services] リリースノート"'
description: すべての [!DNL Payment Services] リリース。
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 6fc2db2ff842244af6a3c52b575b26233540931b
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 1%

---

# リリースノート

以下のリリースノートでは、 [!DNL Payment Services] およびを含めます。

![新規](../assets/new.svg) 新機能
![修正された問題](../assets/fix.svg) 修正点および改善点
![既知の問題](../assets/bug.svg) 既知の問題

詳しくは、 [今後のリリース](https://devdocs.magento.com/release/) を参照してください。

詳しくは、 [可用性](https://devdocs.magento.com/release/availability.html) 製品の互換性について詳しくは、開発者向けドキュメントを参照してください。

## v1.1.0

![新規](../assets/new.svg)<!-- Issue PAY-2127 --> GA リリース —[!DNL Payment Services] 今 [～と互換性がある [!DNL Adobe Commerce] および [!DNL Magento Open Source] バージョン 2.4.0 ～ 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![新規](../assets/new.svg)<!-- Issue PAY-2682 --> この [!DNL Payment Services] 拡張 [!DNL Adobe Commerce] および [!DNL Magento Open Source] は現在、カナダの商人が利用できます。 商人は次のいずれかで支払の構成を表示できます： [フランス語](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies) または [英語](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies).

![新規](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] サポート [カナダドル (CAD)](overview.md#accepted-credit-cards-and-currencies) クレジットカードと PayPal トランザクションの場合。

![新規](../assets/new.svg)<!-- Issue PAY-2680 --> 商人は [オンボード [!DNL Payment Services]](onboard.md) 英語またはフランス語の言語の拡張。

![新規](../assets/new.svg)<!-- Issue PAY-2678 --> マーチャントは、現在、 [注文の支払いステータス](order-payment-status.md) および [ペイアウトレポート](payouts.md)、カナダドル (CAD)。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] は現在、 [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3017 --> サンドボックスモードのアラートが改善され、複数のストアで適切なアラートを表示するようになりました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2742 --> ストア表示レベルで、Venmo などの利用可能な支払い方法を有効または無効にできるようになりました。 以前は、Web サイトごとに支払い方法を設定することができました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2277 --> 選択的に [個々の PayPal スマートボタンの有効化または無効化](settings.md#paypal-smart-buttons).

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2561 --> 以前に削除した製品は、 _注文を確認_ ページ。

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2842 --> クレジットカードトランザクションのテスト [PayPal で失敗する場合があります](https://support.magento.com/hc/en-us/articles/5201041963917) サンドボックス環境で支払いを処理する場合。

## v1.0.0

![新規](../assets/new.svg)<!-- Issue PAY-2127 --> GA リリース —[[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) は現在、 [!DNL Adobe Commerce] および [!DNL Magento Open Source] バージョン 2.4.0 から 2.4.3-p1。

![新規](../assets/new.svg)<!-- Issue PAY-124 --> この [!DNL Payment Services] 拡張 [!DNL Adobe Commerce] および [!DNL Magento Open Source] 次のどちらかに対してインストールできます。 [[!DNL Adobe Commerce] クラウドインフラストラクチャ](install.md#adobe-commerce-on-cloud-infrastructure) または [オンプレミス](install.md#on-premises) インスタンス。 これらのメソッドでは、コマンドラインインターフェイスを使用する必要があります。

![新規](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] を支持する [サンドボックスアカウント](sandbox.md) これにより、マーチャントは拡張機能をテストモードで評価できます。

![新規](../assets/new.svg)<!-- Issue PAY-666 --> 商人は [支払サービスの設定](settings.md) 基本的な支払い行動を伴う拡張（利用など） [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) サンドボックス環境または実稼動環境の切り替え

![新規](../assets/new.svg)<!-- Issue PAY-780 --> 買い物客は [!DNL Payment Services] または経由 [手動オーダー作成](create-order.md).

![新規](../assets/new.svg)<!-- Issue PAY-1856 --> 包括的なレポート（を使用） [注文の支払いステータス](order-payment-status.md) および [ペイアウトレポート](payouts.md)、で使用可能 [!DNL Payment Services] 店舗の注文と関連する支払いを明確に表示するために。

![新規](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] は、あらゆる商人に合わせた、総処理量に基づく柔軟な階層型価格設定をサポートします。

![新規](../assets/new.svg)<!-- Issue PAY-1443 --> 簡単に [外観をカスタマイズする](payments-options.md) の PayPal スマートボタンと、Payment Services 拡張機能用のクレジットカードフィールド。

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [誤ったコンポーザーキー](https://support.magento.com/hc/en-us/articles/4406603542541) 拡張機能のインストール中に、ユーザーは [認証](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正しい `MAGEID`.

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] レポート [すぐに同期できない](https://support.magento.com/hc/en-us/articles/4406114741517).

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2475 --> お使いの [PayPal サンドボックスアカウント](https://support.magento.com/hc/en-us/articles/4406954952461) 対象 [!DNL Payment Services] は、オンボーディング中にそのアカウントを作成した場合は検証できません。
