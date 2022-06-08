---
title: テスト用サンドボックスの設定
description: PayPal Sandbox アカウントを使用して [!DNL Payment Services] テストモードの
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
source-git-commit: e8d008d9a38cebde7772b7e3d70d2447631414fe
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# テスト用サンドボックスの設定

Sandbox のオンボーディングを開始する前に、無料の PayPal Developer アカウントにサインアップし、マーチャント（オンボーディングに使用）と買い物客アカウント（チェックアウトのテストに使用）の両方を作成する必要があります。 必要に応じて、複数の開発者アカウントを作成できます。

PayPal Sandbox アカウントを使用すると、 [!DNL Payment Services] テストモードの PayPal では、PayPal Developer Portal で生成されたビジネスサンドボックステストアカウント、電子メール、およびパスワードをサンドボックスのオンボーディングに使用する必要があります。 サンドボックスのオンボーディングプロセス中に別のアカウントを作成しないでください。

サンドボックス PayPal のオンボーディングプロセス中にアカウントを作成した場合は、メールを検証できないので、オンボーディングサンドボックスをリセットする必要があります。

Sandbox アカウントをリセットするには：

1. クリック **[!UICONTROL Reset sandbox]**. 詳しくは、 [PayPal ビジネスサンドボックスアカウントの作成](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account) ドキュメントを参照してください。
1. クリック **[!UICONTROL Sandbox onboarding]** 次の手順を完了します。

サンドボックスのオンボーディングを完了するには：

1. 次に移動： [PayPal 開発者アカウントページ](https://developer.paypal.com/developer/accounts/).
1. クリック **[!UICONTROL Log in to Home]** 既存の資格情報を使用して PayPal Developers アカウントにログインするか、 **新規登録** をクリックしてアカウントを作成します。
1. PayPal Sandbox アカウントの作成：
   1. に移動します。 _[!UICONTROL SANDBOX]_>**[!UICONTROL Accounts]**.
   1. クリック **[!UICONTROL Create account]**.
   1. 選択 **[!UICONTROL Business]** を「アカウントタイプ」として選択し、 **[!UICONTROL Create]**.
   1. 内 _[!UICONTROL Sandbox Accounts]_」セクションで、_[!UICONTROL Manage accounts]_ 作成したサンドボックスアカウントの列。
   1. クリック **[!UICONTROL View/edit account]**.

      ![PayPal - Sandbox アカウントを表示/編集](assets/onboarding-viewedit-sandbox.png)

   1. 電子メール ID とシステム生成パスワードをコピーして保存し、後で使用できるようにします。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. クリック **[!UICONTROL Sandbox onboarding]**.

   このオプションは、のサンドボックスオンボーディングをまだ完了していない場合に表示されます。 [!DNL Payment Services].

   サンドボックスマーチャント ID が自動生成され、 [設定](settings.md). この ID を変更または変更しないでください。

   PayPal アカウントを接続して支払いの受け入れを開始するための PayPal ウィンドウが表示されます。

1. ビジネスアカウントの E メールアドレスとお住まいの国または地域を入力し、 **[!UICONTROL Next]**.

   ![PayPal — 支払いに PayPal アカウントを接続](assets/paypal-connectacct.png)

1. 以前に保存した Sandbox アカウントの資格情報を使用して、PayPal フローに従います。
1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   この **[!UICONTROL Sandbox onboarding]** ボタンが表示されなくなり、「サンドボックス支払いを保留中」テキストが表示されます。

PayPal サンドボックスのオンボーディングが承認されると、支払いシステムが現在サンドボックスモードで、ライブ支払いを処理していないことを示す通知が表示されます。

>[!IMPORTANT]
>
>次の同意を取り消した場合： [!DNL Payment Services] 対象 [!DNL Adobe Commerce] および [!DNL Magento Open Source] お客様の支払い処理（お客様の PayPal アカウント設定）に関して、お客様のストア内の注文を次の手順で処理することはできません： [!DNL Payment Services]. お使いの支払いサービスホームに、取り消された同意に関するアラートが表示されます。 アラートを閉じるには、 **[!UICONTROL Do not show again]**.

## 連絡先電話番号を有効にする

連絡先電話番号を使用すると、PayPal が顧客から収集した連絡先電話番号を取得できます。 PayPal は常に PayPal アカウント所有者から連絡先の電話番号を収集し、本人確認に役立ち、顧客のアカウントに関する問題を解決したり、達成プロセスを完了したりするために連絡を取ります。 ただし、PayPal では、商人に直接連絡先の電話番号を使用することは推奨されません。これは、販売に悪影響を与える可能性があるためです。 詳しくは、 [PayPal 連絡先の電話番号を取得](https://developer.paypal.com/docs/admin/checkout-settings/#get-contact-telephone-numbers) ドキュメントを参照してください。

この機能は `off` デフォルトでは。 この機能を有効にすると、店舗管理者は、顧客がチェックアウトページの外部で「ブランド化されたチェックアウト」フローを完了したときに、電話番号を確認できます。

>[!IMPORTANT]
>
>この設定は、他のチェックアウトフローには適用されません。

## サンドボックス環境でテスト

詳しくは、 [テストと検証](test-validate.md) を参照してください。
