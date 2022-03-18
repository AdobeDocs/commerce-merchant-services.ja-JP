---
title: '"[!DNL Payment Services] リリースノート"'
description: すべての [!DNL Payment Services] リリース。
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: eb8fdba65b4b64730d0ad4fa6e0c9b64bdadc7df
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 1%

---

# リリースノート

以下のリリースノートでは、 [!DNL Payment Services] およびを含めます。

![新規](../assets/new.svg) 新機能
![修正された問題](../assets/fix.svg) 修正点および改善点
![既知の問題](../assets/bug.svg) 既知の問題

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
