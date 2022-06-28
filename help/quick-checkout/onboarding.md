---
title: 「 [!DNL Quick Checkout] for Adobe Commerce extension"
description: 「 [!DNL Quick Checkout] は、Adobe Commerceインスタンスや、拡張機能のオンボーディングとセットアップに成功する方法に役立ちます。」
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: ac55bf6354c8f5569ad83dc0ac2671b34c98d303
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# [!DNL Quick Checkout] オンボーディング

を使い始めるには、以下を実行します。 [!DNL Quick Checkout] Adobe Commerce拡張機能の場合、インスタンスをアドビのチェックアウト機能に接続するには、いくつかのオンボーディング手順を実行する必要があります。

1. [拡張機能の取得](#get-extension).
1. [での実稼動またはサンドボックスマーチャントアカウントの作成 [!DNL Bolt]](#create-account-with-bolt). ID を検証するために必要な情報をすべて入力します。
1. [一意の [!DNL API Key] および [!DNL Publishable Key] で生成済み [!DNL Bolt]](#obtain-api-credentials).
1. [支払いプロバイダーを [!DNL Bolt] アカウント](#configure-payment-providers).
1. [「有効にする」ドロップダウンを「はい」に設定します。](#enable-extension) をクリックして、拡張機能を有効にします。
1. [サービス設定を定義](#complete-admin-configuration) を設定するには、以下を実行します。 [!DNL Quick Checkout] 拡張子。
1. [「設定を保存」ボタンをクリックします。](#enable-live-quick-checkout) 拡張を有効にする。

>[!NOTE]
>
> を設定しない場合、 [!DNL Bolt] アカウントは、サンドボックス環境または実稼動環境を設定できません。

## 前提条件

を使用するには、 [!DNL Quick Checkout]を使用するには、以下を利用できる必要があります。 [!DNL Bolt]:

- サポートされる支払いプロバイダー
- のマーチャントおよび実稼動アカウント [!DNL Bolt]
- API および [!DNL Publishable key] で生成済み [!DNL Bolt]

詳しくは、 [前提条件](../quick-checkout/prerequisites.md) トピックを参照してください。

詳しくは、 [API 資格情報](#obtain-api-credentials) を作成し、 [!DNL API keys] 例えば、

## 拡張機能の取得

詳しくは、 [インストール](../quick-checkout/install.md) トピックを参照してください。

## でアカウントを作成 [!DNL Bolt]

を設定する前に [!DNL Quick Checkout] Adobe Commerce Admin で、 [サンドボックス](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} および [実稼動](https://merchant.bolt.com/register){target=&quot;_blank&quot;} マーチャントアカウント [!DNL Bolt]. アカウントを作成するために必要なすべての詳細を指定します。 [!DNL Bolt].

詳しくは、 [テストと検証](../quick-checkout/testing.md) トピックを参照してください。

## API 資格情報の取得

次の手順で [!DNL Quick Checkout] 必要な項目 [!DNL Bolt] 一意のキー。 次の情報を取得します。 [!DNL API keys] 移動して **開発者** > **API** > **キー** 内 **Bolt Merchant Dashboard**.

- [!DNL API key]:バックエンドが操作に使用する秘密鍵 [!DNL Bolt] API
- [!DNL Publishable key]:フロントエンドがとやり取りする際に使用するキー [!DNL Bolt] API

詳しくは、 [[!DNL Bolt] 環境の詳細](https://help.bolt.com/developers/references/environment-details/#about-keys){target=&quot;_blank&quot;} ページを参照してください。 [!DNL Publishable keys] の [!DNL Quick Checkout] 拡張子。

>[!CAUTION]
>
> 次を作成する必要があります： [!DNL API keys] サンドボックス環境と実稼動環境の両方に対して使用できます。

## 支払いプロバイダーの設定

お客様の支払いサービスプロバイダーに接続するには、 [プロセッサー設定](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/){target=&quot;_blank&quot;} 開発者 [!DNL Bolt] ページ。

## 拡張機能を有効にする

1. の _管理者_ サイドバー、移動 **ストア** > _設定_ > **設定**.
1. 左側のパネルで、を展開します。 **セールス** を選択し、 **チェックアウト**.

   ![クイックチェックアウト](assets/admin-view.png)

1. 内 [!DNL Quick Checkout] 表示、設定 **有効にする** から `Yes`.
1. 使用するメソッド（サンドボックスまたは実稼動）を選択します。

   - テストおよび開発のためのサンドボックス
   - 生産：生の支払処理者との取引を処理します

1. 一意の API を指定した後で資格情報を検証し、 [!DNL Publishable keys].

>[!CAUTION]
>
> 一意の API と [!DNL Publishable keys] 拡張機能を有効にする前に、顧客が支払いフォームを表示し、注文することができなくなります。

## 管理者設定を完了

1. の _管理者_ サイドバー、次に移動 **ストア** > **設定** > **チェックアウト** をクリックして、一般的な「チェックアウト管理者設定」ページにアクセスします。
1. 内 _サービス設定_ 「 」セクションでは、拡張機能を有効にするために必要なすべての詳細を指定します。
1. 設定 _支払いアクション_ を次のいずれかのオプションに設定します。

   - `Authorize`:認証時にトランザクションを自動的にキャプチャしないでください。
   - `Authorize and Capture`:認証時にトランザクションを自動的にキャプチャします。

Adobe Commerceの標準チェックアウトオプションについて詳しくは、 [checkout](https://docs.magento.com/user-guide/configuration/sales/checkout.html) トピック。

## ライブクイックチェックアウトを有効にする

を有効にするには、以下を実行します。 [!DNL Quick Checkout] Adobe Commerce拡張機能の場合：

1. 以下を確認します。 [!UICONTROL Enable] ドロップダウンが **はい** をクリックして、拡張機能を有効にします。
1. クリック **設定を保存**.

## お問い合わせ

オンボーディングプロセスは、 [!DNL Express Checkout] 機能。 割り当てられたSlackを通じてAdobe Commerceのエンジニアリングチームに連絡します [Adobeベータプログラムチャネル](http://adobe-beta-programs.slack.com/) チャネルを参照してください。

詳しくは、 [テストと検証](../quick-checkout/testing.md) トピックを参照してください。
