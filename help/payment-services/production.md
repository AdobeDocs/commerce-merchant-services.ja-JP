---
title: 有効にする [!DNL Payment Services] 実稼動用
description: を有効にしてオンボーディングプロセスを完了します。 [!DNL Payment Services] 実稼動用。
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
feature: Payments, Checkout, Configuration, Install
source-git-commit: ff83c83a054e5b14814cc3076744c5517081a80f
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 0%

---

# 有効にする [!DNL Payment Services] 実稼動用

サービスを実稼動環境に移行し、 [オンボーディングプロセス](onboard.md)、このトピックの手順に従って、次の操作をおこないます。

* [インストール](install.md) Payment Services 拡張機能
* [設定と接続](connect.md) インスタンス
* [設定](sandbox.md) および [テスト](test-validate.md) サンドボックス

## 設定 [!DNL Payment Services] 支払い方法として

後で [コマースサービスの設定](connect.md#configure-commerce-services) を有効にします。 [サンドボックステスト](sandbox.md#enable-sandbox-testing) または [生前払い](#enable-live-payments)を設定する必要があります。 [!DNL Payment Services] 支払い方法として。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. クリック **[!UICONTROL Enable Payment Services]**.

   このオプションは、まだ設定していない場合は表示されます [!DNL Payment Services] を 1 つ以上の web サイトの支払い方法として使用できます。

   ホームビューの設定領域に移動し、関連するオプションが展開されます (**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_) を使用して、 [!DNL Payment Services] のオプション [支払方法](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target="_blank"}.

1. In _[!UICONTROL General Configuration]_，設定&#x200B;**[!UICONTROL Enable]**から `Yes`.
1. 設定 **[!UICONTROL Payment Action]**（両方） _[!UICONTROL Credit Card Fields]_および_[!UICONTROL PayPal Smart Buttons]_&#x200B;を次のいずれかに変更します。

   | 設定 | 説明 |
   |---|---|
   | `Authorize` | 購入を承認し、資金を保留します。 その金額は、商人によって「取り込まれる」まで引き落とされません。 |
   | `Authorize and Capture` | 購入を承認し、商人が資金を「キャプチャ」します。 |

   >[!IMPORTANT]
   >
   >[!DNL Payment Services] は部分キャプチャをサポートします。 商人は、注文の一部を部分的に取り込む（請求書）ことができます。 例えば、各項目を個別に取り込むことも、1 つの項目を今すぐ取り込み、残りを後で取り込むこともできます。

1. クリック **[!UICONTROL Save]**.
1. クリック **[!UICONTROL Go to Payment Services]** （人に）戻る [!DNL Payment Services] ホーム。
1. [キャッシュをクリア](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html).

   設定を変更するたびに、クリアを実行する必要があります。

詳しくは、 [支払いサービスの構成](settings.md) クレジットカードフィールドと PayPal スマートボタンの設定に関する詳細

## 完全なマーチャントオンボーディング

お客様の店舗が支払いサービスと共に運営されるようにする次のステップは、ライブオンボーディングを完了することです。

支払いサービスが提供する [**詳細** （完全にサポート）および **標準** （速達チェックアウト）支払いオプション](../payment-services/payments-options.md#standard-vs-advanced-payments-experience) オンボーディングフローは、操作する国と好みの支払いエクスペリエンスに応じて異なります。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. クリック **[!UICONTROL Live onboarding]**.

   このオプションは、のライブオンボーディングをまだ完了していない場合に表示されます。 [!DNL Payment Services].

1. Adobe Analytics の _国を選択_ 「モーダル」で、操作元の国を選択します。

   支払いサービスは、 [5 か国](../payment-services/overview.md#availability) 現在は 支払サービスは、国リストに表示されるその他すべての国に対して、高速チェックアウト機能（支払いオプションのサブセット）を提供します。

   リストから選択した国によって、支払いオプションとオンボーディングフローが決まります。[詳細](#advanced-onboarding) （完全にサポート）または [標準](#standard-onboarding) （速達チェックアウト） — ご利用いただけます。

>[!TIP]
>
> オンボーディングオプション（標準または詳細）を選択して続行したら、オンボーディングを再完了して、最初の選択項目からアップグレードまたはダウングレードする必要があります。

### 高度なオンボーディング

このオンボーディングフローは、 [完全に支援された国](../payment-services/overview.md#availability).

国を選択した後：

1. 表示されるモーダルで、「 」を選択します。 **詳細**.

   の **標準** オプションを選択し、次に進みます。 [標準オンボーディングフロー](#standard-onboarding).

1. クリック **続行**.
1. PayPal アカウントの資格情報（Sandbox アカウントの資格情報ではなく）を使用して、完全にサポートされている高度なオンボーディングの PayPal フローを続行します _または_ 新しい PayPal アカウントに新規登録します。

>[!IMPORTANT]
>
>**高度なオンボーディング** 商人に～を求める [支払いの権利を要求](#request-payments-entitlement-from-adobe) ：ライブオンボーディングを有効にします。

### 標準オンボーディング

この標準オンボーディングフローは、 [高速チェックアウトのみサポート](../payment-services/overview.md#availability) が指定されている。

国を選択した後：

1. Adobe Analytics の _支払いサービス契約_ 表示されるモーダルを選択し、 **支払いサービス契約** Adobe Commerce Payment Services 契約を表示するためのリンクです。
1. Adobe Analytics の _支払いサービス契約_ モーダルをクリックします。 **同意します**.
1. Express Checkout オンボーディングの場合は、PayPal アカウントの資格情報（Sandbox アカウントの資格情報ではなく）を使用して PayPal フローを続行するか、新しい PayPal アカウントに新規登録します。

>[!IMPORTANT]
>
>[Appleの支払いフィールドとクレジットカードフィールド](../payment-services/payments-options.md) は次の場合に使用できません： **標準オンボーディング**.

## 電子メールアドレスを確認

1. 管理者のサイドバーで、 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   The _[!UICONTROL Live onboarding]_ボタンが表示されなくなり、「[!UICONTROL Live payments pending]」テキストボックスに入力します。

   このテキストボックスでは、オンボーディングを完了するために PayPal でメールアドレスを確認するように求められる場合もあります。

1. メールアドレスの確認を求めるメッセージが表示されたら、PayPal から送信された確認メッセージをメールで確認し、「 」をクリックしてメールアドレスを確認します。
1. 管理者のサイドバーで、 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. ブラウザーウィンドウを更新します。

   PayPal マーチャントのオンボーディングが承認されると、支払いシステムがサンドボックスモードで、ライブ支払いを処理していないことを示す通知が表示されます。

   >[!IMPORTANT]
   >
   >次の同意を取り消した場合： [!DNL Payment Services] 対象： [!DNL Adobe Commerce] および [!DNL Magento Open Source] お客様の支払い処理（お客様の PayPal アカウント設定）に関して、お客様のストア内の注文を次の手順で処理することはできません： [!DNL Payment Services]. お使いの支払いサービスホームに、取り消された同意に関するアラートが表示されます。

## Adobeからの支払い権限の要求

ストアの運用を有効にするには、Adobe( [高度なオンボーディングのみ](#advanced-onboarding)):

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. クリック **[!UICONTROL Get Live Payments]** の [!DNL Payment Services] ホーム。

   ![権限のリクエスト](assets/request-entitlements.png){width="500" zoomable="yes"}

1. フォームに情報を入力します。
1. セールスチームのメンバーが連絡を取ります。

または、次の場所でAdobeの支払い権限を要求できます： [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**ライブオンボーディング** は、支払いの権利付与が承認されるまでアクセスできません。

## 価格層の設定

Adobe Analytics の [!DNL Payment Services] _マーチャント ID_:

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. ホームビューで、 **[!UICONTROL Settings]**. 詳しくは、 [ホーム](payments-home.md) を参照してください。
1. 必要な項目を選択 _マーチャント ID_ を送信し、正しい価格帯を設定するセールス担当者に送信します。

## ライブ支払いを有効にする

A _実稼動マーチャント ID_ が自動生成され、 [設定](configure-admin.md). この ID を変更または変更しないでください。

ライブ支払いを有効にする：

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. ホームで、 **[!UICONTROL Settings]** をクリックします。 詳しくは、 [ホーム](payments-home.md) を参照してください。
1. Adobe Analytics の _[!UICONTROL General Configuration]_セクションセット&#x200B;**[!UICONTROL Payment mode]**から `Production`.
1. クリック **[!UICONTROL Save]**.
1. [キャッシュをクリア](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   >[!IMPORTANT]
   >
   >キャッシュをクリアしない場合、顧客はチェックアウト時に PayPal の支払いオプションを表示できません。

以下に戻ると、 [!DNL Payment Services] ホーム：ライブ支払いを処理しているので、サンドボックス支払いモードメッセージは表示されなくなりました。

詳しくは、 [管理での設定](configure-admin.md) （レガシー設定オプションの場合）

>[!IMPORTANT]
>
>次の同意を取り消した場合： [!DNL Payment Services] お客様の支払い処理（お客様の PayPal アカウント設定）に関して、お客様のストア内の注文を次の手順で処理することはできません： [!DNL Payment Services]. 支払処理を再度有効にする場合は、オンボーディングを再度完了する必要があります。 お使いの支払いサービスホームに、取り消された同意に関するアラートが表示されます。

## 本番でテスト

実際のクレジットカードと銀行を使用して実稼動環境で支払いをテストしてから、買い物客にこの機能を公開することを強くお勧めします。

詳しくは、 [テストと検証](test-validate.md) を参照してください。
