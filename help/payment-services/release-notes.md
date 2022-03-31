---
title: '"[!DNL Payment Services] リリースノート"'
description: すべての [!DNL Payment Services] リリース。
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 93a10d91a2dc92db530074d7fc2dfd4f31a9488d
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 1%

---

# リリースノート

以下のリリースノートでは、 [!DNL Payment Services] およびを含めます。

![新規](../assets/new.svg) 新機能
![修正された問題](../assets/fix.svg) 修正点および改善点
![既知の問題](../assets/bug.svg) 既知の問題

## v1.1.0

![新規](../assets/new.svg)<!-- Issue PAY-2127 --> [[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) は、Adobe CommerceおよびMagento Open Sourceのバージョン 2.4.0 ～ 2.4.4 と互換性があるようになりました。

![新規](../assets/new.svg)<!-- Issue PAY-2682 --> この [!DNL Payment Services] Adobe CommerceとMagento Open Sourceの拡張機能は、カナダの商人が利用できます。 商人は次のいずれかで支払の構成を表示できます： [フランス語](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr) または [英語](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=en).

![新規](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] サポート [カナダドル (CAD)](overview.md#accepted-credit-cards-and-currencies) クレジットカードと Paypal を使用します。 買い物客は、買い物をする店舗のロケールに応じて、好みの言語で買い物体験をすることができます。

![新規](../assets/new.svg)<!-- Issue PAY-2680 --> 商人は [オンボード [!DNL Payment Services]](onboard.md) の拡張子が優先言語で設定されています。

![新規](../assets/new.svg)<!-- Issue PAY-2678 --> 商人が表示できるようになりました [財務報告書](order-payment-status.md) カナダドル (CAD) で。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] は現在、 [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3035 --> の管理チェックアウトの改善 [!DNL Payment Services] 拡張子。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3017 --> サンドボックスモードのアラートが改善され、複数のストアで適切なアラートを表示するようになりました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2742 --> [!DNL Payment Services] を使用すると、ストレビューレベルで Venmo などの使用可能な支払い方法を有効/無効にできます。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2277 --> 管理でのマーチャントの機能を改善し、PayPal のスマートボタンを選択的に無効化/有効化できるようにしました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2561 --> 以前に削除した製品は、 _注文を確認_ ページ。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2456 --> [!DNL Payment Services] 管理での支払い方法のラベルが改善されました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2907 --> 不正ルールとチャージバック保護を最適に利用するために、トランザクション・データの収集を改善。

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [誤ったコンポーザーキー](https://support.magento.com/hc/en-us/articles/4406603542541) 拡張機能のインストール中に、ユーザーは [認証](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正しい `MAGEID`.

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [レポート](https://support.magento.com/hc/en-us/articles/4406114741517) 支払いと注文の支払いステータスの場合、すぐには同期されない場合があります。

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2475 --> [PayPal サンドボックスアカウント](https://support.magento.com/hc/en-us/articles/4406954952461) 対象 [!DNL Payment Services] は、オンボーディング中にアカウントが作成された場合は検証できません。

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2842 --> [クレジットカードのテストが失敗しました](https://support.magento.com/hc/en-us/articles/5201041963917) と PayPal の両方を使用します。

## v1.0.0

![新規](../assets/new.svg)<!-- Issue PAY-2127 --> GA リリース。 [支払いサービス](https://marketplace.magento.com/magento-payment-services.html) は、Adobe CommerceおよびMagento Open Sourceのバージョン 2.4.0 から 2.4.3-p1 に対応しました。

![新規](../assets/new.svg)<!-- Issue PAY-124 --> この [!DNL Payment Services] Adobe CommerceとMagento Open Sourceの拡張機能は、 [Adobe Commerce an cloud infrastructure](install.md#magento-commerce-cloud) または [オンプレミス](install.md#on-premises) インスタンス。 これらのメソッドでは、コマンドラインインターフェイスを使用する必要があります。

![新規](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] を支持する [サンドボックスアカウント](onboard.md#enable-sandbox-testing) これにより、マーチャントは拡張機能をテストモードで評価できます。

![新規](../assets/new.svg)<!-- Issue PAY-666 --> 商人は [支払いサービスの設定](configure-admin.md) 基本的な支払い動作を含む拡張（サンドボックスまたは実稼動環境間の切り替えなど）。

![新規](../assets/new.svg)<!-- Issue PAY-780 --> 買い物客は [!DNL Payment Services] または、注文を電話で受け取り、 [注文全体を作成する](create-order.md) 管理者に問い合わせます。

![新規](../assets/new.svg)<!-- Issue PAY-1856 --> [!DNL Payment Services] 店舗の注文と支払いを明確に把握できるよう、マーチャント向けの包括的なレポートを提供します。

![新規](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] は、任意の商人に適合した階層型価格（TPV に基づく）をサポートします。

![新規](../assets/new.svg)<!-- Issue PAY-1443 --> PayPal のボタンと CC フィールドの外観と操作性を [支払いサービス](https://devdocs.magento.com/payment-services/customize-buttons-messaging.html) 拡張子。

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [誤ったコンポーザーキー](https://support.magento.com/hc/en-us/articles/4406603542541) 拡張機能のインストール中に、ユーザーは [認証](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正しい `MAGEID`.

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [レポート](https://support.magento.com/hc/en-us/articles/4406114741517) 支払いと注文の支払いステータスの場合、すぐには同期されない場合があります。

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2475 --> [PayPal サンドボックスアカウント](https://support.magento.com/hc/en-us/articles/4406954952461) 対象 [!DNL Payment Services] を検証できません。
