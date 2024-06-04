---
title: Enable （有効） [!DNL Payment Services] 実稼動用
description: を有効にして、オンボーディングプロセスを完了します。 [!DNL Payment Services] （実稼動用）。
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
feature: Payments, Checkout, Configuration, Install
source-git-commit: d1379bb108f2259051641a7bf77cd8b459fd9cbf
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---

# Enable （有効） [!DNL Payment Services] 実稼動用

サービスを実稼動環境に移行して、以下を完了できます。 [オンボーディングプロセス](onboard.md)このトピックの手順に従って、以下を行った後に、

* [インストール](install.md) 支払いサービス拡張機能
* [設定と接続](connect.md) お使いのインスタンス
* [の設定](sandbox.md) および [テスト](test-validate.md) サンドボックス

## を設定 [!DNL Payment Services] 支払方法として

お先に [Commerce サービスの設定](connect.md#configure-commerce-services) およびいずれかのオプションを有効にします [サンドボックステスト](sandbox.md#enable-sandbox-testing) または [ライブ支払](#enable-live-payments)、を設定する必要があります [!DNL Payment Services] お支払方法として。

1. 日 _Admin_ サイドバー、に移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. クリック **[!UICONTROL Enable Payment Services]**.

   このオプションは、を設定していない場合に表示されます [!DNL Payment Services] 1 つ以上の web サイトの支払方法として。

   ホームビューの設定エリアに移動すると、関連するオプションが展開されます（**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_）に割り当てます。ここで、 [!DNL Payment Services] のオプション [支払い方法](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target="_blank"}.

1. 対象： _[!UICONTROL General Configuration]_、設定&#x200B;**[!UICONTROL Enable]**対象： `Yes`.
1. を設定 **[!UICONTROL Payment Action]**、両方 _[!UICONTROL Credit Card Fields]_および_[!UICONTROL PayPal payment buttons]_&#x200B;を次のいずれかに変更します。

   | 設定 | 説明 |
   |---|---|
   | `Authorize` | 購入を承認し、資金を保留します。 この金額は、マーチャントによって「キャプチャ」されるまで引き出されません。 |
   | `Authorize and Capture` | 購入を承認すると、マーチャントは資金を「キャプチャ」します。 |

   >[!IMPORTANT]
   >
   >[!DNL Payment Services] は部分キャプチャをサポートしています。 マーチャントは、注文の一部を部分的にキャプチャ（請求）できます。 例えば、各項目を個別にキャプチャしたり、1 つの項目を今すぐキャプチャして、残りの項目を後でキャプチャしたりできます。

1. クリック **[!UICONTROL Save]**.
1. クリック **[!UICONTROL Go to Payment Services]** ～に戻る [!DNL Payment Services] ホーム。
1. [キャッシュのクリア](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html).

   設定を変更するたびにクリアを行う必要があります。

参照： [支払いサービスの設定](settings.md) クレジットカードのフィールドと PayPal の支払いボタンの設定について詳しくは、こちらを参照してください。

## マーチャントのオンボーディングの完了

ストアが支払いサービスを有効にする次のステップは、ライブオンボーディングを完了することです。

支払いサービスの提供 [**詳細** （完全にサポート）と **標準** （エクスプレスチェックアウト）支払いオプション](../payment-services/payments-options.md#standard-vs-advanced-payments-experience) また、使用する国や希望する支払い体験に応じて、オンボーディングフローも異なります。

1. 日 _Admin_ サイドバー、に移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. クリック **[!UICONTROL Live onboarding]**.

   このオプションは、のライブオンボーディングをまだ完了していない場合に表示されます [!DNL Payment Services].

1. が含まれる _国を選択_ モーダルで、操作する国を選択します。

   支払いサービスは、におけるすべての支払いオプションを完全にサポートします。 [5 か国](../payment-services/overview.md#availability) 現在。 支払いサービスは、国リストに表示されるその他すべての国に対して、高速チェックアウト機能（支払いオプションのサブセット）を提供します。

   リストから選択する国によって、支払いオプションとオンボーディングフローが決まります。[詳細](#advanced-onboarding) （完全にサポート）または [標準](#standard-onboarding) （高速チェックアウト） – 利用可能。

>[!TIP]
>
> オンボーディングオプション（標準または詳細）を選択して続行したら、オンボーディングを再度完了して、最初の選択からアップグレードまたはダウングレードする必要があります。

### 詳細オンボーディング

このオンボーディングフローは、のマーチャントが使用できます [完全に支援されている国](../payment-services/overview.md#availability).

国を選択すると、次のようになります。

1. 表示されるモーダルで、を選択します **詳細**.

   の場合 **標準** オプションで、 [標準のオンボーディングフロー](#standard-onboarding).

1. クリック **続行**.
1. PayPal アカウントの資格情報（サンドボックスアカウントの資格情報ではありません）を使用して、完全にサポートされている高度なオンボーディングで PayPal フローを続行します _または_ 新しい PayPal アカウントに新規登録します。

>[!IMPORTANT]
>
>**詳細オンボーディング** 商人は以下を行う必要があります [支払い権利のリクエスト](#request-payments-entitlement-from-adobe) ライブオンボーディングを有効にします。

### 標準オンボーディング

この標準のオンボーディングフローは、次の利用可能な国のマーチャントが使用できます [エクスプレスチェックアウトのサポート](../payment-services/overview.md#availability) が指定されている。

国を選択すると、次のようになります。

1. が含まれる _支払いサービス契約_ 表示されるモーダルで、 **支払いサービス契約** Adobe Commerce支払いサービス契約を表示するためのリンク。
1. が含まれる _支払いサービス契約_ モーダル、クリック **同意します**.
1. PayPal アカウントの資格情報（サンドボックスアカウントの資格情報ではありません）を使用して、PayPal エクスプレスチェックアウトオンボーディングの PayPal フローを続行するか、新しい PayPal アカウントに新規登録します。

>[!IMPORTANT]
>
>[Appleの Pay フィールドと Credit card フィールド](../payment-services/payments-options.md) は利用できません **標準オンボーディング**.

## メールアドレスを確認

1. 管理サイドバーで、に移動します。 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   この _[!UICONTROL Live onboarding]_ボタンが表示されなくなり、「[!UICONTROL Live payments pending]」テキストボックスに入力します。

   そのテキストボックスでは、オンボーディングを完了するために PayPal でメールアドレスを確認するように求められる場合もあります。

1. メールアドレスを確認するメッセージが表示されたら、PayPal から送信された確認メッセージをメールで確認し、クリックしてメールアドレスを確認します。
1. 管理サイドバーで、に移動します。 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. ブラウザーウィンドウを更新します。

   PayPal マーチャントオンボーディングが承認されると、支払いシステムがサンドボックスモードであり、ライブ支払いを処理していないことを示す通知が表示されます。

   >[!IMPORTANT]
   >
   >次の同意を取り消した場合： [!DNL Payment Services] （用） [!DNL Adobe Commerce] および [!DNL Magento Open Source] （PayPal アカウントの設定で）支払いを処理する場合、ストア内の注文は次のユーザーが処理することはできません [!DNL Payment Services]. 支払サービスのホームに、失効した同意に関するアラートが表示されます。

## Adobeからの支払い権利のリクエスト

ストアを有効にするには、Adobeから支払い権限をリクエストします（例：） [高度なオンボーディングのみ](#advanced-onboarding)）:

1. 日 _Admin_ サイドバー、に移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. クリック **[!UICONTROL Get Live Payments]** が含まれる [!DNL Payment Services] ホーム。

   ![リクエストの使用権限](assets/request-entitlements.png){width="500" zoomable="yes"}

1. フォームに入力します。
1. 営業チームのメンバーから連絡があります。

または、次の場所でAdobeから支払い権限をリクエストできます。 [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**ライブオンボーディング** は、支払い権限が承認されるまでアクセスできません。

## 価格レベルの構成

を入手 [!DNL Payment Services] _マーチャント ID_:

1. 日 _Admin_ サイドバー、に移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. ホームビューで、 **[!UICONTROL Settings]**. 参照： [ホーム](payments-home.md) を参照してください。
1. 必要なを選択 _マーチャント ID_ そして、正しい価格レベルを設定するセールス担当者に送信します。

参照： [レベル 2 およびレベル 3 の処理](levels-card-payment-transactions.md) 支払いトランザクションの詳細については、こちらを参照してください。

## ライブ支払いを有効にする

A _生産業者 ID_ が自動生成され、に入力されます。 [設定](configure-admin.md). この ID は変更しないでください。

ライブ支払を有効にする：

1. 日 _Admin_ サイドバー、に移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. ホームで、 **[!UICONTROL Settings]** ページの右上に 参照： [ホーム](payments-home.md) を参照してください。
1. が含まれる _[!UICONTROL General Configuration]_断面セット&#x200B;**[!UICONTROL Payment mode]**対象： `Production`.
1. クリック **[!UICONTROL Save]**.
1. [キャッシュのクリア](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   >[!IMPORTANT]
   >
   >キャッシュをクリアしないと、チェックアウト時に PayPal の支払いオプションが表示されません。

に戻る場合 [!DNL Payment Services] ホームでは、ライブ支払いを処理中なので、サンドボックス支払いモードメッセージが表示されなくなります。

参照： [管理者でを設定](configure-admin.md) （レガシー設定オプション用）。

>[!IMPORTANT]
>
>次の同意を取り消した場合： [!DNL Payment Services] （PayPal アカウントの設定で）支払いを処理する場合、ストア内の注文は次のユーザーが処理することはできません [!DNL Payment Services]. 支払い処理を再度有効にする場合は、オンボーディングを再度完了する必要があります。 支払サービスのホームに、失効した同意に関するアラートが表示されます。

## 実稼動環境でテスト

この機能を買い物客に公開する前に、実際のクレジットカードや銀行を使用して、実稼動環境で支払いをテストすることを強くお勧めします。

参照： [テストと検証](test-validate.md) を参照してください。
