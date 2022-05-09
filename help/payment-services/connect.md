---
title: インスタンスに接続
description: API キーと秘密鍵を使用して Commerce インスタンスに接続し、設定でデータ領域を指定します。
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 0%

---

# インスタンスに接続

[!DNL Payment Services] は、Commerce Services を利用し、SaaS（サービスとしてのソフトウェア）としてデプロイされます。 API キーと秘密鍵を使用してコマースインスタンスに接続し、設定でデータ領域を指定します。 この接続は 1 回だけ設定します。

詳しくは、 [Commerce Services コネクタ](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;}（このサービスの詳細については、コアユーザーガイドを参照）。

## API 資格情報の取得

Commerce SaaS サービスを使用するには、インスタンスの API キーを使用する必要があります。この API キーは、 [マイアカウントダッシュボード](https://account.magento.com/customer/account/login){target=&quot;_blank&quot;}。 1 つの Commerce アカウントに対して、2 つの異なる API キーペアを作成できます。1 つはサンドボックス用、もう 1 つは実稼動用（ライブ支払い）ですが、一度に 1 つのペアのみがアクティブに使用できます。

>[!NOTE]
>
>へのアクセスに関するヘルプが必要 [!UICONTROL My Account] ダッシュボード？ 詳しくは、 [コマースアカウントの作成](https://docs.magento.com/user-guide/magento/magento-account-create.html){target=&quot;_blank&quot;}（コアユーザーガイド）。

特定の API キーペアは、環境内のすべてのコマースサービスで有効です。お使いのコマースインスタンス用に既にコマースサービスが設定されている場合、API キーペアは既に管理者に存在します。 プライベート API キーが失われた場合は、新しい API キーペアを生成し、管理の Commerce Services 設定に適用する必要があります。

サンドボックス環境または実稼動環境の API キーを生成する方法については、 [Commerce Services コネクタ](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;}（コアユーザーガイド）。

>[!IMPORTANT]
>
>API キーペアを再生成して SaaS 識別子を変更すると、このインスタンスで使用されるすべての Commerce Services が別のデータストアに接続され、アクセス（以前に保存されたデータを含む）が失われます。 API キーペアを再生成せず、アクティブな実稼働インスタンスで SaaS Identifier を変更することをお勧めします。

### コマース API キーと秘密鍵

一部 [!DNL Adobe Commerce] および [!DNL Magento Open Source] 機能は、SaaS（サービスとしてのソフトウェア）としてデプロイされます。これは、Commerce Services と呼ばれます。 これらのサービスを使用するには、API キーと秘密鍵を使用してコマースインスタンスをこれらのサービスに接続し、 [設定](https://docs.magento.com/user-guide/configuration/services/saas.html){target=&quot;_blank&quot;}。

画像 ID で識別されるコマースアカウントを作成する際に、コマース API キーと秘密鍵を生成できます。 次のようなコマースサービスを使用するには： [!DNL Payment Services], [!DNL Product Recommendations]または [!DNL Live Search]に設定されている場合、ライセンス所有者が使用権限の検証に合格するには、これらのキーを生成する必要があります。 これらのキーは、ライセンス所有者に代わってプロジェクトと環境を管理するシステムインテグレーターまたは開発チームに渡すことができます。 ソリューションインテグレーターの場合は、お客様自身のニーズに合わせてこれらのサービスを使用する権利も与えられます。 この場合、コマースパートナー契約の署名者がキーを生成する必要があります。

### API キーと秘密鍵の生成

1. 次の場所にあるコマースアカウントにログインします。 [https://account.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
1. 以下 **[!UICONTROL Magento]** タブ、選択 **[!UICONTROL API Portal]** サイドバーに表示されます。
1. 次の _[!UICONTROL Environment]_メニュー、選択&#x200B;**[!UICONTROL Sandbox]**を、**[!UICONTROL Production]**.

   >[!IMPORTANT]
   >
   >両方の環境に API キーが必要です。

1. 名前を _[!UICONTROL API Keys]_「 」セクションで、「 」をクリックします。**[!UICONTROL Add New]**.

   これにより、新しいキーをダウンロードするためのダイアログが開きます。

   >[!IMPORTANT]
   >
   >このダイアログは、鍵をコピーまたはダウンロードする唯一の機会です。

1. クリック **[!UICONTROL Download]** 次に、 **[!UICONTROL Cancel]**.

   この _[!UICONTROL API Keys]_「 」セクションに API キーが表示されるようになりました。

1. SaaS プロジェクトを選択または作成する際に、API キーと秘密鍵の両方をコピーします。

   詳しくは、 [SaaS](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} （コアユーザーガイド）を参照してください。

同じ API キーを複数のインスタンスで使用することもできますが、各インスタンスには独自の SaaS データ容量が必要です。

SaaS プロジェクトを作成すると、Commerce は、Commerce ライセンスに応じて、1 つ以上の SaaS データスペースを生成します。

* [!DNL Adobe Commerce] - 1 つの実稼動データ領域2 つのテスト用データスペース
* [!DNL Magento Open Source] - 1 つの実稼動データ領域テストデータスペースなし

### SaaS プロジェクトの設定

>[!NOTE]
>
>次の項目が表示されない場合、 _[!UICONTROL Commerce Services Connector]_「 」セクションで、目的のコマースサービス用のコマースモジュール（例： ）をインストールする必要があります。 [[!DNL Payment Services]](install.md).

SaaS プロジェクトを選択または作成するには、ストアの Commerce ライセンスホルダーから Commerce API キーをリクエストします。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 左側のパネルで、を展開します。 **[!UICONTROL Services]** を選択します。 **[!UICONTROL Commerce Services Connector]**.
1. 内 _[!UICONTROL API Keys]_「 」セクションに、キー値を貼り付けます。

   >[!IMPORTANT]
   >
   >両方にキー値を追加 **[!UICONTROL sandbox]** および **[!UICONTROL production]** 環境。

1. クリック **[!UICONTROL Save Config]**.

   保存すると、API キーに関連付けられた SaaS プロジェクトがある場合は、それらのプロジェクトが _[!UICONTROL SaaS Project]_フィールド_[!UICONTROL SaaS Identifier]_ 」セクションに入力します。

1. SaaS プロジェクトが存在しない場合は、「 **[!UICONTROL Create Project]**. 次に、 **[!UICONTROL Project Name]** フィールドに入力します。
1. コマースストアの現在の設定に使用するには、 **[!UICONTROL SaaS Data Space]**.

>[!IMPORTANT]
>
>マイアカウントの API ポータルセクションでキーを再生成する場合は、管理設定で API キーを直ちに更新してください。 新しいキーを生成し、管理で更新しない場合、SaaS 拡張機能は機能しなくなり、有用なデータが失われます。

名前は、 **[!UICONTROL Rename this Project]** または **[!UICONTROL Rename Data Space]** ボタンを設定します。

## コマースサービスを設定

オンボーディングの最初の手順 [!DNL Payment Services] は、管理者でコマースサービスを設定するためのものです。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. クリック **[!UICONTROL Configure Commerce Services]**.

   このオプションは、お使いのアカウント用に Commerce Services をまだ設定していない場合に表示されます。

   管理者の設定領域に移動します。 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**をクリックして、Commerce Services コネクタを設定します。

1. コマースサービスを設定するには、 [コマースサービス](https://docs.magento.com/user-guide/system/saas.html#createsaasenv){target=&quot;_blank&quot;}。
