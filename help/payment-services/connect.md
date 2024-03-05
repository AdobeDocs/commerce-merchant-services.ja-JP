---
title: インスタンスに接続
description: API キーと秘密鍵を使用して Commerce インスタンスに接続し、設定でデータ領域を指定します。
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
feature: Payments, Checkout, Configuration, Saas
source-git-commit: 57b140463d457404b57dd23d33c72e48b4c3ac89
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 0%

---

# インスタンスに接続

[!DNL Payment Services] は、Commerce Services を利用し、SaaS（サービスとしてのソフトウェア）としてデプロイされます。 API キーと秘密鍵を使用してコマースインスタンスに接続し、 [Commerce Services コネクタ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **この接続は 1 回だけ設定します。**

* 次の条件を満たしている場合： *インスタンスは既に接続されています* API 資格情報を取得して使用し、Commerce Services を設定すると、次に進むことができます。 [テストサンドボックスの設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* もしまだ *インスタンスに接続する必要があります*&#x200B;については、このトピックの情報を参照してください。 [API 資格情報の取得](#obtain-api-credentials) および [Commerce Services の設定](#configure-commerce-services).
* 次の場合、 *インスタンスが接続されているかどうかが不明です*&#x200B;に移動します。 **システム** /サービス/ **Commerce Services コネクタ** と、 [!UICONTROL Sandbox Keys] および [!UICONTROL Production Keys] セクション、および *プロジェクト* および *データスペース* フィールド [!UICONTROL SaaS Identifier] 」セクションに入力します。 これらの値が存在する場合、インスタンスは接続されます。

>[!NOTE]
>
>支払いサービスを利用できるすべてのマーチャントは、1 つの実稼動データスペースと 2 つのテストデータスペースを使用できます。

## API 資格情報の取得

Commerce SaaS サービスを使用するには、サンドボックスと実稼働の両方でインスタンスの API キー（Commerce 公開 API キーと秘密鍵）を使用する必要があります。この API キーは、 [マイアカウントダッシュボード](https://account.magento.com/customer/account/login). [キーペア](https://docs.magento.com/user-guide/configuration/services/saas.html) コマースアカウント（sandbox 用と実稼動用）用に作成できますが、一度に 1 つのペアのみをアクティブに使用できます。

>[!NOTE]
>
>へのアクセスに関するヘルプが必要 [!UICONTROL My Account] ダッシュボード？ 詳しくは、 [コマースアカウントの作成](https://docs.magento.com/user-guide/magento/magento-account-create.html).

公開 API キーは作成後、常にマイアカウントダッシュボードで使用できます。 必要に応じてコピーまたは削除できます。 秘密鍵 API キーは、サンドボックスまたは実稼動用の公開 API キーを作成すると表示されます。このキーは、その後のダイアログボックスからのコピーまたは保存にのみ使用でき、後でアクセスすることはできません。

特定の API キーペアは、環境内のすべての Commerce Services で有効です。そのため、お使いのインスタンスに対して既に Commerce Services が設定されている場合、API キーペアは Commerce Services Connector に既に存在します。

API キーが失われた場合、新しい API キーペアを [生成済み](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) および [適用済み](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) を追加します。 間違ったキーが設定されているか、設定に存在しない場合は、アカウントが検証されなかったことを通知するアカウント検証エラーダイアログが Payment Services に表示されます。

参照先 [API を使用する使用可能な Commerce Services のリスト](https://docs.magento.com/user-guide/system/saas.html#available-services).

サンドボックス環境または実稼動環境の API キーを生成する方法については、 [資格情報](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>
>API キーペアを再生成しないことをお勧めします *および* アクティブな実稼動インスタンス上の SaaS 識別子やデータ領域を変更します。 変更されると、インスタンスのデータが失われます。

## コマースサービスを設定

同じ API キーをインスタンス全体で使用できますが、各インスタンスには独自の API キーが必要です [SaaS データ容量](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

>[!NOTE]
>
>マーチャントは、支払い権限に MageID 用に生成された同じキーを使用する必要があります。

資格情報を取得したら、SaaS プロジェクトと Saas Data Space を設定できます。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. クリック **[!UICONTROL Configure Commerce Services]**.

   このオプションは、お使いのアカウント用に Commerce Services をまだ設定していない場合に表示されます。

   管理者の設定領域に移動します。 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**をクリックして、Commerce Services コネクタを設定します。

1. コマースサービスを設定するには、 [SaaS 設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).
