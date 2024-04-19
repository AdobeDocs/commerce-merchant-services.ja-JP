---
title: インスタンスの接続
description: API キーと秘密鍵を使用してCommerce インスタンスを接続し、設定内のデータスペースを指定します。
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
feature: Payments, Checkout, Configuration, Saas
source-git-commit: 5c4fe370507e4154d4495d4c09e2ff8705e53191
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---

# インスタンスの接続

[!DNL Payment Services] はCommerce サービスを活用し、SaaS （software as a service）としてデプロイされます。 API キーと秘密鍵を使用してCommerce インスタンスに接続し、 [Commerce サービスコネクタ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **この接続は 1 回だけ設定します。**

>[!INFO]
>
> のを表示 [[!DNL Adobe Commerce] サービスコネクタ](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=en) ビデオを参照してください。

* 以下がある場合： *すでにインスタンスに接続しています*&#x200B;に進むには、API 資格情報を取得して使用し、Commerce サービスを設定します。 [テストサンドボックスの設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* もしそれでも *インスタンスを接続する必要があります*&#x200B;詳しくは、このトピックのを参照してください [api 資格情報の取得](#obtain-api-credentials) および [Commerce サービスの設定](#configure-commerce-services).
* 次の場合： *インスタンスが接続されているかどうかわからない*&#x200B;に移動します。 **システム** / サービス / **Commerce サービスコネクタ** で公開 API キーと秘密 API キーの値を確認できます。 [!UICONTROL Sandbox Keys] および [!UICONTROL Production Keys] セクションと *プロジェクト* および *データスペース* のフィールド [!UICONTROL SaaS Identifier] セクション。 これらの値が存在する場合、インスタンスが接続されています。

>[!NOTE]
>
>支払いサービスの資格を持つすべてのマーチャントは、1 つの実稼動データスペースと 2 つのテストデータスペースを使用できます。

## API 資格情報の取得

Commerce SaaS サービスを使用するには、サンドボックスと実稼働環境の両方でインスタンスの API キー（Commerce公開 API キーと秘密鍵）を使用する必要があります。この両方は、で作成および管理されます [マイアカウントダッシュボード](https://account.magento.com/customer/account/login). [キーペア](https://docs.magento.com/user-guide/configuration/services/saas.html) はCommerce アカウント用に作成できます（サンドボックス用に 1 つ、実稼動用に 1 つ）。ただし、一度にアクティブに使用できるのは 1 つのペアのみです。

>[!NOTE]
>
>へのアクセスに関するヘルプ [!UICONTROL My Account] ダッシュボード？ 参照： [Commerce アカウントの作成](https://docs.magento.com/user-guide/magento/magento-account-create.html).

公開 API キーを作成すると、常にマイアカウントダッシュボードで使用できるようになります。 必要に応じて、コピーまたは削除できます。 秘密 API キーは、サンドボックスまたは実稼動用の公開 API キーを作成する際に表示されます。結果として表示されるダイアログボックスからのコピーまたは保存にのみ使用でき、後でアクセスすることはできません。

指定された API キーペアは、環境内のすべてのCommerce Services で有効です。そのため、お使いのインスタンスに既にCommerce Services が設定されている場合、API キーペアは既にCommerce Services コネクタに存在します。

API キーが失われた場合、新しい API キーのペアは [生成日時](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) および [適用日時](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) を管理者でCommerce サービスコネクタ設定に追加します。 間違ったキーが設定されている場合、または設定に何も存在しない場合、アカウントが検証されなかったことを通知するアカウント検証エラーダイアログが支払いサービスに表示されます。

を表示 [api を使用する使用可能なCommerce サービスのリスト](https://docs.magento.com/user-guide/system/saas.html#available-services).

サンドボックス環境または実稼動環境の API キーを生成する方法については、を参照してください。 [資格情報](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>
>API キーペアを再生成しないことをお勧めします *および* アクティブな実稼動インスタンス上の SaaS 識別子やデータスペースを変更します。 インスタンスが変更されると、そのインスタンスのデータは失われます。

## Commerce サービスの設定

同じ API キーを複数のインスタンスで使用できますが、各インスタンスには独自のキーが必要です [SaaS データ容量](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

>[!NOTE]
>
>マーチャントは、支払い権限に MageID 用に生成されたのと同じキーを使用する必要があります。

認証情報を取得したので、SaaS プロジェクトと Saas データ領域を設定できます。

1. 日 _Admin_ サイドバー、に移動 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. クリック **[!UICONTROL Configure Commerce Services]**.

   このオプションは、アカウントにCommerce サービスをまだ設定していない場合に表示されます。

   管理者の設定領域に移動します。 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**:Commerce サービスコネクタの設定

1. Commerce サービスを設定するには、で説明されている手順に従います [SaaS 設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).

   >[!INFO]
   >
   > のを表示 [[!DNL Adobe Commerce] サービスコネクタ](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=en#configuration-faqs) ビデオを参照してください。
