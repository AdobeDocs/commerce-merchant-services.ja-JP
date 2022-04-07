---
title: ダッシュボードでの設定
description: インストール後、 [!DNL Payment Services] 」と入力します。
role: Admin, User
level: Intermediate
source-git-commit: bfb2b6632fe494d6e392c214f5e3f5a11930c0b2
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# ダッシュボードでの設定

カスタマイズ可能 [!DNL Payment Services] を使用して、ダッシュボードの設定オプションを利用できます。

クリック時 [!UICONTROL Settings] ダッシュボードでは、 [!DNL Payment Services] Adobe CommerceとMagento Open Sourceの これらの設定オプションは、 [!UICONTROL Payment mode] フィールドに値を入力します。

詳しくは、 [[!UICONTROL General] 設定セクション](#general-settings) を参照してください。

>[!IMPORTANT]
>
> マルチストアまたはレガシー設定については、 [管理での設定](configure-admin.md) トピック。

## 支払いサービスの構成

次を有効にすることができます。 [!DNL Payment Services] を有効にし、 [!UICONTROL General] 設定セクションに表示されます。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![ダッシュボード表示](assets/payment-services-menu-small.png)

1. ダッシュボードで、 **[!UICONTROL Settings]** をクリックします。

   この _[!UICONTROL General]_「 」セクションには、設定に使用する設定オプションが含まれています。 [!DNL Payment Services] 支払い方法として。

1. 上部の切り替えオプション (**[!UICONTROL Enable Payment Services as payment method]**)、 `Yes` 有効にする [!DNL Payment Services] を設定します。

1. の場合 **支払いモード**&#x200B;に設定し、 `Sandbox` まだテスト中の場合 [!DNL Payment Services] お客様のストアまたは `Production` ライブ支払いを有効にする準備が整っている場合。

   >[!WARNING]
   >
   >お使いの [!UICONTROL Sandbox Merchant ID] および [!UICONTROL Production Merchant ID] は自動生成され、サンドボックスや実稼動のオンボーディングが完了すると、該当するフィールドに存在します。 これらの ID を削除または変更しないでください。

1. 支払い関数とストアフロント表示のデフォルト設定を変更するには、必要に応じて追加のオプションを設定します。

   - [クレジットカードのフィールド](#credit-card-fields)
   - [PayPal のスマートボタン](#paypal-smart-buttons)
   - [ボタンのスタイル](#button-style)

1. 変更を保存するには、 **[!UICONTROL Save]** をクリックします。

1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** をクリックし、 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

### クレジットカードのフィールド

この [!UICONTROL Credit Card Fields] 支払いオプションは、クレジットカードまたはデビットカードの支払い方法のためのシンプルでセキュアなチェックアウトを提供します。

詳しくは、 [支払いオプション](payments-options.md#paypal-smart-buttons) を参照してください。

1. の場合 **[!UICONTROL Checkout title]**、（必要に応じて）テキストを入力して、チェックアウト時に表示される支払い方法の名前を変更します。
1. 宛先 [支払い処理を設定](production.md#set-payment-services-as-payment-method)，設定 **[!UICONTROL Payment action]** から `Authorize` または `Authorize and Capture`.
1. の場合 **[!UICONTROL Debug Mode]**&#x200B;で、セレクターを切り替えてデバッグモードを有効にします。
1. 変更を保存するには、 **[!UICONTROL Save]** をクリックします。
1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** をクリックし、 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

### PayPal のスマートボタン

この [!DNL PayPal Smart Buttons] 支払いオプションは、お客様に対して、シンプルで迅速かつ安全なチェックアウトプロセスを提供します。 詳しくは、 [支払いオプション](payments-options.md#paypal-smart-buttons) を参照してください。

ダッシュボード内で PayPal スマートボタンの支払いオプションを有効にできます。

1. チェックアウト時に表示される支払い方法の名前を変更するには、 **[!UICONTROL Checkout Title]** フィールドに入力します。
1. 宛先 [支払い処理を設定](production.md#set-payment-services-as-payment-method)，設定 **[!UICONTROL Payment action]** から `Authorize` または `Authorize and Capture`.
1. 切り替えセレクターを使用して、有効または無効にします [!DNL PayPal smart button] 表示機能：
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL Show Venmo button]**.
   - **[!UICONTROL PayPal Pay Later enabled]** ：チェックアウト時にボタンを表示するオプションを有効にします。

1. 次の手順で [後で支払うメッセージ](payments-options.md#pay-later-button) （必要に応じて）、 **[!UICONTROL Display Pay Later message]** オプション。
1. デバッグモードを有効にするには、 **[!UICONTROL Debug Mode]**,
1. 変更を保存するには、 **[!UICONTROL Save]** をクリックします。
1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** をクリックし、 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

### ボタンのスタイル

また、 _[!UICONTROL Button style]_ダッシュボード内の PayPal スマートボタンのオプション：

1. 次の手順で **[!UICONTROL Layout]**&#x200B;を選択します。 `Vertical` または `Horizontal`.
1. 横置きレイアウトでタグラインを有効にするには、 **[!UICONTROL Show tagline]**.
1. 次の手順で **[!UICONTROL Color]**」で、目的のカラーオプションを選択します。
1. 次の手順で **[!UICONTROL Shape]**&#x200B;を選択します。 `Pill` または `Rect`.
1. ボタンの高さセレクターを有効にするには、 **[!UICONTROL Responsive button height]**.
1. 次の手順で **[!UICONTROL Label]**」で、目的のラベルオプションを選択します。
1. 変更を保存するには、 **[!UICONTROL Save]** をクリックします。
1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** をクリックし、 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

次の項目を設定できます。 [!DNL PayPal Smart Buttons] スタイルを管理者またはダッシュボードで設定する。 詳しくは、 [設定 [!DNL PayPal Smart Buttons style]](configure-admin.md#configure-paypal-smart-button-styling) を参照してください。
