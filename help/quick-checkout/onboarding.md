---
title: 「 [!DNL Quick Checkout] for Adobe Commerce extension"
description: 「 [!DNL Quick Checkout] は、Adobe Commerceインスタンスや、拡張機能のオンボーディングとセットアップに成功する方法に役立ちます。」
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: 0624ddc369ddedaaf9ae741831e0d5c5589ea4c2
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 0%

---

# [!DNL Quick Checkout] オンボーディング

を使い始めるには、以下を実行します。 [!DNL Quick Checkout] Adobe Commerce拡張機能の場合、インスタンスをアドビのチェックアウト機能に接続するには、いくつかのオンボーディング手順を実行する必要があります。

1. [拡張機能の取得](#get-extension).
1. [での実稼動またはサンドボックスマーチャントアカウントの作成 [!DNL Bolt]](#create-account-with-bolt). ID を検証するために必要な情報をすべて入力します。
1. [一意の [!DNL API Key] および [!DNL Publishable Key]](#obtain-api-credentials) で生成済み [!DNL Bolt].
1. [支払いプロバイダーを [!DNL Bolt] アカウント](#configure-payment-providers).
1. [「有効にする」ドロップダウンを「はい」に設定します。](#enable-extension) をクリックして、拡張機能を有効にします。
1. [サービス設定を定義](#complete-admin-configuration) を設定するには、以下を実行します。 [!DNL Quick Checkout] 拡張子。
1. [「設定を保存」をクリックします。](#enable-live-quick-checkout) ボタンをクリックして拡張機能を有効にします。
1. 範囲をに切り替え **メイン Web サイト** および [「コールバック URL を設定」をクリックします。](#check-shopper-valid-account) 」ボタンをクリックします。

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

次の手順で [!DNL Quick Checkout] 必要な項目 [!DNL Bolt] 一意のキーと [!DNL signing secret]. 次の情報を取得します。 [!DNL API keys] 移動して **開発者** > **API** > **キー** 内 **Bolt Merchant Dashboard**.

- [!DNL API key]:バックエンドが操作に使用する秘密鍵 [!DNL Bolt] API
- [!DNL Publishable key]:フロントエンドがとやり取りする際に使用するキー [!DNL Bolt] API
- [!DNL Signing secret]:から受信した要求の署名検証に使用されます [!DNL Bolt].

![クイックチェックアウト](assets/account-credentials.png)

詳しくは、 [[!DNL Bolt] 環境の詳細](https://help.bolt.com/developers/references/environment-details/#about-keys){target=&quot;_blank&quot;} ページ：キーと署名の秘密鍵について [!DNL Bolt] の [!DNL Quick Checkout] 拡張子。

>[!CAUTION]
>
> 次を作成する必要があります： [!DNL API keys] サンドボックス環境と実稼動環境の両方に対して使用できます。

## 支払いプロバイダーの設定

お客様の支払いサービスプロバイダーに接続するには、 [プロセッサー設定](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/){target=&quot;_blank&quot;} 開発者 [!DNL Bolt] ページ。

## 拡張機能を有効にする

1. の _管理者_ サイドバー、移動 **ストア** > _設定_ > **設定**.
1. 左側のパネルで、を展開します。 **セールス** を選択し、 **チェックアウト**.
1. 内 [!DNL Quick Checkout] 表示、設定 **有効にする** から `Yes`.
1. 使用するメソッド（サンドボックスまたは実稼動）を選択します。

   - テストおよび開発のためのサンドボックス
   - 生産：生の支払処理者との取引を処理します

1. 一意の API を指定した後で資格情報を検証し、 [!DNL Publishable keys].

![クイックチェックアウト](assets/extension-view.png)

>[!CAUTION]
>
> 一意の API と [!DNL Publishable] キーを押してから拡張機能を有効にします。そうしないと、顧客は支払いフォームを表示し、注文できなくなります。

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

## 買い物客の有効なアカウントを確認

買い物客が [!DNL Bolt] アカウント：

1. 範囲をに切り替えます。 **メイン Web サイト**.
1. 次をクリック： **コールバック URL の設定** 」ボタンをクリックします。 これにより、 [!DNL Bolt] をクリックして、買い物客がアカウントを持っているかどうかを判断します。 存在する場合は、OTP ポップアップが表示されます。

>[!CAUTION]
>
> スコープを **メイン Web サイト** は、適切な URL が設定されていることを確認します。 各 Web サイトには複数のドメインを含めることができます。

詳しくは、 [サイト、ストア、および表示範囲](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings){target=&quot;_blank&quot;} のトピックを参照してください。Adobe Commerceのスコープの詳細については、こちらを参照してください。

## お問い合わせ

オンボーディングプロセスは、 [!DNL Express Checkout] 機能。 割り当てられたSlackを通じてAdobe Commerceのエンジニアリングチームに連絡します [Adobeベータプログラムチャネル](http://adobe-beta-programs.slack.com/) チャネルを参照してください。

詳しくは、 [テストと検証](../quick-checkout/testing.md) トピックを参照してください。
