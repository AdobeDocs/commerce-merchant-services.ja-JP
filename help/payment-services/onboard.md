---
title: オンボード [!DNL Payment Services]
description: インスタンスとの接続 [!DNL Payment Services] 機能を使用できるようになります。
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# オンボード [!DNL Payment Services]

を使用し始めるには、以下を実行します。 [!DNL Payment Services] 対象 [!DNL Adobe Commerce] および [!DNL Magento Open Source]の場合は、インスタンスと支払い機能を接続するためのオンボーディング手順をいくつか実行する必要があります。

## オンボーディングフロー

![オンボーディングフロー](assets/onboarding-diagram.svg)

このオンボーディングフロー図は、オンボーディングの一般的なプロセスを示しています [!DNL Payment Services].

サンドボックスまたはライブ支払のオンボーディングを完了すると、財務レポートには次の場所からアクセスできます： [!DNL Payment Services] 」と入力します。

サンドボックスとライブの支払いの両方がオンボーディングされ、有効になっている場合、これらのモードを [!DNL Payment Services] ホーム。

## 前提条件

を使用するには [!DNL Payment Services]を使用する場合は、お使いのインスタンスで以下を使用できる必要があります。

* サービスコネクタモジュール
* サービス ID モジュール
* API キー

サービスコネクタ ID モジュールとサービス ID モジュールは、 [～の設置 [!DNL Payment Services]](install.md). インストールが完了すると、設定 (**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**) を展開する際に、**[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**.

API キーの作成またはアクセス方法については、 [API 資格情報](#obtain-api-credentials).

## オンボーディング手順

1. [のインストール [!DNL Payment Services] 拡張](install.md#get-payment-services).
1. [API 資格情報の取得](connect.md#obtain-api-credentials).
1. [インスタンスに接続](connect.md#configure-commerce-services) を Commerce Services に追加します。 この接続は、コマースインスタンスごとに 1 回だけ完了する必要があります。
1. [サンドボックスサービスの設定](sandbox.md#enable-sandbox-testing) ( または、次に進みます： [ライブ支払の有効化](sandbox.md#enable-live-payments) （他の環境で機能をテストした場合）、PayPal の支払い処理アカウントを使用します。
1. [設定 [!DNL Payment Services] お客様の支払い方法](production.md#set-payment-services-as-payment-method)（サンドボックスモード）：テストの支払いの処理を開始します。
1. [支払い権限をリクエスト](production.md#request-payments-entitlement-from-adobe) ：ライブオンボーディングを有効にします。
1. [完全なマーチャントオンボーディング](production.md#complete-merchant-onboarding) ：コマース Web サイトのライブ支払いを有効にします。
1. [ダウンロード [!DNL Payment Services] マーチャント ID](production.md#configure-pricing-tier) 正しい価格帯を設定するために、セールスに渡します。
1. [有効にする [!DNL Payment Services] ライブモード](production.md#enable-live-payments) ：ライブ支払の処理を開始します。
1. テスト支払（両方） [サンドボックス](sandbox.md#test-in-sandbox-environment) および [実稼動](production.md#test-in-production) 環境。

>[!NOTE]
>
>管理（手順 3）でコマースサービスを設定しない場合、サンドボックスまたはライブ支払いを設定できません。

## トラブルシューティング

* [トラブルシューティング [!DNL Payment Services] インストール](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=en)
* [PayPal Sandbox アカウントが検証されていません](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html)
* [遅延 [!DNL Payment Services] レポートデータ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)
* [サンドボックス環境で支払いを処理する際、PayPal でクレジットカードのテストが失敗する](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=en)
