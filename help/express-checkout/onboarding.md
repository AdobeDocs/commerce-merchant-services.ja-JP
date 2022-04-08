---
title: のオンボーディング [!DNL Express Checkout] Adobe Commerce拡張機能
description: 詳しくは、 [!DNL Express Checkout] は、Adobe Commerceインスタンスと、拡張機能のオンボーディングとセットアップに成功する方法に役立ちます。
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: 1a7df2c5581ea6d590aa1a2f701b4428371d2299
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# [!DNL Express Checkout] オンボーディング

>[!IMPORTANT]
>
> この機能は、Early Adopter Program(EAP) ユーザー専用で、すべてのお客様がまだアクセスできるわけではありません。 現在、米国のお客様に限定されています。 サポートおよび質問については、Adobe Commerceサポートにお問い合わせください。

を使い始めるには、以下を実行します。 [!DNL Express Checkout] Adobe Commerce拡張機能の場合、インスタンスをアドビのチェックアウト機能に接続するには、いくつかのオンボーディング手順を実行する必要があります。

1. [拡張機能の取得](#get-extension).
1. [での実稼動またはサンドボックスマーチャントアカウントの作成 [!DNL Bolt]](#create-account-with-bolt). ID を検証するために必要な情報をすべて入力します。
1. [で生成された一意の API キーと公開可能なキーを指定します。 [!DNL Bolt]](#obtain-api-credentials).
1. [支払いプロバイダーを [!DNL Bolt] アカウント](#configure-payment-providers).
1. [「有効にする」ドロップダウンを「はい」に設定します。](#enable-extension) をクリックして、拡張機能を有効にします。
1. [サービス設定を定義](#complete-admin-configuration) を設定するには、以下を実行します。 [!DNL Express Checkout] 拡張子。
1. [「設定を保存」ボタンをクリックします。](#enable-live-express-checkout) 拡張を有効にする。

>[!NOTE]
>
> を設定しない場合、 [!DNL Bolt] アカウント（上記の手順 2）サンドボックスまたは実稼動環境を設定することはできません。

## 前提条件

を使用するには、 [!DNL Express Checkout]を使用するには、以下を利用できる必要があります。 [!DNL Bolt]:

- サポートされる支払いプロバイダー
- のマーチャントおよび実稼動アカウント [!DNL Bolt]
- で生成された API と公開可能なキー [!DNL Bolt]

詳しくは、 [前提条件](../express-checkout/prerequisites.md) トピックを参照してください。

詳しくは、 [API 資格情報](#obtain-api-credentials) を参照して、インスタンスの API キーを作成またはアクセスする方法を確認してください。

## 拡張機能の取得

詳しくは、 [インストール](../express-checkout/install.md) トピックを参照してください。

## Bolt でアカウントを作成

を設定する前に [!DNL Express Checkout] Adobe Commerce Admin で、 [サンドボックス](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} および [実稼動](https://merchant.bolt.com/register){target=&quot;_blank&quot;} マーチャントアカウント [!DNL Bolt]. アカウントを作成するために必要なすべての詳細を指定します。 [!DNL Bolt].

詳しくは、 [テストと検証](../express-checkout/testing.md) トピックを参照してください。

## API 資格情報の取得

次の手順で [!DNL Express Checkout] 必要な項目 [!DNL Bolt] 一意のキー。 に移動して、次の API キーを取得します。 **開発者** > **API** > **キー** 内 **Bolt Merchant Dashboard**.

- API キー：バックエンドが操作に使用する秘密鍵 [!DNL Bolt] API
- 公開可能なキー：フロントエンドがとやり取りする際に使用するキー [!DNL Bolt] API

詳しくは、 [[!DNL Bolt] 環境の詳細](https://help.bolt.com/developers/references/environment-details/#about-keys){target=&quot;_blank&quot;} ページ： [!DNL Express Checkout] 拡張子。

>[!CAUTION]
>
> サンドボックス環境と実稼動環境の両方に API キーを作成する必要があります。

## 支払いプロバイダーの設定

お客様の支払いサービスプロバイダーに接続するには、 [プロセッサー設定](https://help.bolt.com/integrations/adobe-express-checkout/set-up/){target=&quot;_blank&quot;} 開発者 [!DNL Bolt] ページ。

## 拡張機能を有効にする

1. の _管理者_ サイドバー、次に移動 **ストア** > **設定** > **チェックアウト** をクリックして、「チェックアウト管理者設定」ページにアクセスします。

   ![高速チェックアウト](assets/admin-view.png)

1. 内 [!DNL Express Checkout] 表示、設定 **有効にする** から `Yes`.
1. 使用するメソッド（サンドボックスまたは実稼動）を選択します。

   - テストおよび開発のためのサンドボックス
   - 生産：生の支払処理者との取引を処理します

1. 一意の API と公開可能なキーを指定した後で資格情報を検証します。

>[!CAUTION]
>
> 拡張機能を有効にする前に、一意の API と発行可能なキーを指定する必要があります。指定しないと、顧客は支払いフォームを表示し、注文できなくなります。

## 管理設定の完了

1. の _管理者_ サイドバー、次に移動 **ストア** > **設定** > **チェックアウト** をクリックして、一般的な「チェックアウト管理者設定」ページにアクセスします。
1. 内 _サービス設定_ 「 」セクションでは、拡張機能を有効にするために必要なすべての詳細を指定します。
1. 設定 _支払いアクション_ 形式：

   - 許可：認証時にトランザクションを自動的にキャプチャしないでください。
   - 認証およびキャプチャ：認証時にトランザクションを自動的にキャプチャします。

Adobe Commerceの標準チェックアウトオプションについて詳しくは、 [checkout](https://docs.magento.com/user-guide/configuration/sales/checkout.html) トピック。

## Live Express チェックアウトを有効にする

を有効にするには、以下を実行します。 [!DNL Express Checkout] Adobe Commerce拡張機能の場合：

1. クリック **設定を保存**.

## お問い合わせ

オンボーディングプロセスは、すべての [!DNL Express Checkout] 機能。 サポートが必要な場合は、Adobe Commerceサポートにお問い合わせください。

詳しくは、 [テストと検証](../express-checkout/testing.md) トピックを参照してください。
