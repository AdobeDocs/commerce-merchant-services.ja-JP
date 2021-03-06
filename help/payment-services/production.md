---
title: 有効にする [!DNL Payment Services] 本番用
description: を有効にしてオンボーディングプロセスを完了します。 [!DNL Payment Services] 実稼動用。
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
source-git-commit: 51722d7045ccb6ccfdc7ab5bd93d5ca46b52cf03
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---

# 有効にする [!DNL Payment Services] 本番用

Payments Services 拡張機能が [インストール済み](install.md)、インスタンスが [構成済みおよび接続済み](connect.md)、および [サンドボックスの設定](sandbox.md) テストが完了したら、サービスを本番環境に移行し、 [オンボーディングプロセス](onboard.md).

## 設定 [!DNL Payment Services] 支払い方法

後 [コマースサービスの設定](connect.md#configure-commerce-services) また、 [サンドボックステスト](sandbox.md#enable-sandbox-testing) または [生前払い](#enable-live-payments)の場合、 [!DNL Payment Services] 支払い方法として。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. クリック **[!UICONTROL Enable Payment Services]**.

   このオプションは、まだ設定していない場合は表示されます [!DNL Payment Services] を使用して、1 つ以上のMagentoweb サイトの支払い方法。

   ホームビューの設定領域に移動し、関連するオプションが展開されます (**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_) を使用し、 [!DNL Payment Services] オプション [支払方法](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target=&quot;_blank&quot;}。

1. In _[!UICONTROL General Configuration]_，設定&#x200B;**[!UICONTROL Enable]**から `Yes`.
1. 設定 **[!UICONTROL Payment Action]**、両方 _[!UICONTROL Credit Card Fields]_および_[!UICONTROL PayPal Smart Buttons]_&#x200B;を次のいずれかに変更します。

   | 設定 | 説明 |
   |---|---|
   | `Authorize` | 購入を承認し、資金を保留します。 その金額は、商人によって「取り込まれる」まで引き落とされません。 |
   | `Authorize and Capture` | 購入を承認し、商人が資金を「キャプチャ」します。 |

1. クリック **[!UICONTROL Save]**.
1. クリック **[!UICONTROL Go to Payment Services]** 戻る [!DNL Payment Services] ホーム。
1. [キャッシュをクリア](https://docs.magento.com/user-guide/system/cache-management.html){target=&quot;_blank&quot;}。

   設定を変更するたびに、クリアを実行する必要があります。

詳しくは、 [支払いサービスの構成](settings.md) クレジットカードフィールドと PayPal スマートボタンの設定に関する詳細

## 完全なマーチャントオンボーディング

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. クリック **[!UICONTROL Live onboarding]**.

   このオプションは、のライブオンボーディングをまだ完了していない場合に表示されます。 [!DNL Payment Services].

   PayPal ウィンドウが表示されます。

1. PayPal フローを続行するには、PayPal アカウントの資格情報（Sandbox アカウントの資格情報ではなく）を使用するか、新しい PayPal アカウントに新規登録します。
1. 管理者のサイドバーで、 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   この _[!UICONTROL Live onboarding]_ボタンが表示されなくなり、「[!UICONTROL Live payments pending]」テキストボックスに入力します。

   このテキストボックスでは、オンボーディングを完了するために PayPal でメールアドレスを確認するように求められる場合もあります。

1. メールアドレスの確認を求めるメッセージが表示されたら、PayPal から送信された確認メッセージをメールで確認し、「 」をクリックしてメールアドレスを確認します。
1. 管理者のサイドバーで、 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. ブラウザーウィンドウを更新します。

   PayPal マーチャントのオンボーディングが承認されると、支払いシステムがサンドボックスモードで、ライブ支払いを処理していないことを示す通知が表示されます。

   >[!IMPORTANT]
   >
   >次の同意を取り消した場合： [!DNL Payment Services] 対象 [!DNL Adobe Commerce] および [!DNL Magento Open Source] お客様の支払い処理（お客様の PayPal アカウント設定）に関して、お客様のストア内の注文を次の手順で処理することはできません： [!DNL Payment Services]. お使いの支払いサービスホームに、取り消された同意に関するアラートが表示されます。

## Adobeからの支払い権限の要求

ライブオンボーディングを有効にするには、次のAdobeに支払い権限を要求する必要があります。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. クリック **[!UICONTROL Get Live Payments]** の [!DNL Payment Services] ホーム。

   ![権限のリクエスト](assets/request-entitlements.png)

1. フォームに情報を入力します。
1. セールスチームのメンバーから連絡が来ます。

または、次の場所でAdobeの支払い権限を要求できます： [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**ライブオンボーディング** は、支払いの権利付与が承認されるまでアクセスできません。

## 価格層の設定

次の手順で [!DNL Payment Services] _マーチャント ID_:


1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. ホームビューで、 **[!UICONTROL Settings]**. 詳しくは、 [ホーム](payments-home.md) を参照してください。
1. 必要な _マーチャント ID_ を送信し、正しい価格帯を設定するセールス担当者に送信します。

## ライブ支払いを有効にする

A _実稼動商人 ID_ が自動生成され、 [設定](configure-admin.md). この ID を変更または変更しないでください。

ライブ支払を有効にする手順は、次のとおりです。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. ホームで、 **[!UICONTROL Settings]** をクリックします。 詳しくは、 [ホーム](payments-home.md) を参照してください。
1. 内 _[!UICONTROL General Configuration]_セクションセット&#x200B;**[!UICONTROL Payment mode]**から `Production`.
1. クリック **[!UICONTROL Save]**.
1. [キャッシュをクリア](https://docs.magento.com/user-guide/system/cache-management.html){target=&quot;_blank&quot;}。

   >[!IMPORTANT]
   >
   >キャッシュをクリアしない場合、顧客はチェックアウト時に PayPal の支払いオプションを表示できません。

以下に戻る [!DNL Payment Services] ホーム：ライブ支払いを処理しているので、サンドボックス支払いモードメッセージは表示されなくなりました。

詳しくは、 [管理での設定](configure-admin.md) （レガシー設定オプション）。

>[!IMPORTANT]
>
>次の同意を取り消した場合： [!DNL Payment Services] お客様の支払い処理（お客様の PayPal アカウント設定）に関して、お客様のストア内の注文を次の手順で処理することはできません： [!DNL Payment Services]. 支払処理を再度有効にする場合は、オンボーディングを再度完了する必要があります。 お使いの支払いサービスホームに、取り消された同意に関するアラートが表示されます。

## 本番でテスト

実際のクレジットカードと銀行を使用して実稼動環境で支払いをテストしてから、買い物客にこの機能を公開することを強くお勧めします。

詳しくは、 [テストと検証](test-validate.md) を参照してください。
