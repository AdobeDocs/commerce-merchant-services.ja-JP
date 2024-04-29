---
title: Commerce サービスコネクタ
description: 実稼動およびサンドボックス API キーを使用して、Adobe CommerceまたはMagento Open Sourceインスタンスをサービスに統合する方法について説明します。
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
feature: Services, Saas
role: Admin, User
source-git-commit: b86464ac65aeb260930fa2f6fed0a4aedbd7eddf
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Adobe CommerceとMagento Open Sourceの一部の機能は、 [!DNL Commerce Services]  また、SaaS （software as a service）として導入されます。 これらのサービスを使用するには、を接続する必要があります [!DNL Commerce] 実稼動およびサンドボックスの API キーを使用したインスタンス、および [設定](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html). これは 1 回だけ設定する必要があります。

## 利用可能なサービス {#availableservices}

以下に、 [!DNL Commerce] からアクセスできる機能 [!DNL Commerce Services Connector]:

| サービス | 対象 |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) powered by Adobe Sensei | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) powered by Adobe Sensei | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe CommerceとMagento Open Source |
| [[!DNL Channel Manager]](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/intro-to-channel-manager/overview.html) | Adobe CommerceとMagento Open Source |
| [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html) | Adobe Commerce |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [[!DNL Data Connection]](/help/data-connection/overview.md) | Adobe Commerce |

## アーキテクチャ

大まかには、 [!DNL Commerce Services Connector] は、次のコア要素で構成されています。

![Commerce Services コネクタのアーキテクチャ](assets/saas-config-sync-workflow.png)

次のセクションでは、これらの各要素について詳しく説明します。

## 資格情報 {#apikey}

実稼働およびサンドボックスの API キーは、 [!DNL Commerce] 一意で識別されるライセンス所有者のアカウント [!DNL Commerce] ID （MageID）。 などのサービスのエンタイトルメント検証に合格するには： [!DNL Product Recommendations] または [!DNL Live Search]を使用すると、アカウントが正常な状態にある限り、マーチャントの組織のライセンス所有者は API キーのセットを生成できます。 キーは、ライセンス所有者の代わりにプロジェクトや環境を管理するシステムインテグレーターまたは開発チームと、「必要に応じて」共有できます。 さらに、ソリューションインテグレーターはを使用する資格もあります。 [!DNL Commerce Services]. ソリューションインテグレーターの場合は、の署名者 [!DNL Commerce] パートナー契約は、API キーを生成する必要があります。

### 実稼動およびサンドボックス API キーの生成 {#genapikey}

1. にログイン [!DNL Commerce] アカウント： [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}。

1. の下 **Magento** タブ、選択 **API ポータル** サイドバーに。

1. から _0.5511122_ メニュー、選択 **実稼動** または **Sandbox**.

1. に名前を入力 _API キー_ セクションでクリック **新規を追加**.

   新しいキーをダウンロードするためのダイアログが開きます。

   ![秘密鍵をダウンロード](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > これは、キーをコピーまたはダウンロードする必要がある唯一の機会です。

1. クリック **Download** 次に、 **キャンセル**.

1. 各環境（実稼動環境とサンドボックス）で上記の手順を繰り返します。

   この **API キー** API （公開）キーがセクションに表示されるようになりました。 次の場合には、実稼動用キーとサンドボックス用キー（公開+秘密）の両方が必要です [saaS プロジェクトの選択または作成](#createsaasenv).

## SaaS 設定 {#saasenv}

[!DNL Commerce] インスタンスには、SaaS プロジェクトと SaaS データ領域を設定する必要があります。これにより、 [!DNL Commerce Services] データを適切な場所に送信できる。 SaaS プロジェクトは、すべての SaaS データ スペースをグループ化します。 SaaS データ スペースは、を可能にするデータの収集および保存に使用されます。 [!DNL Commerce Services] 仕事に。 このデータの一部は、 [!DNL Commerce] インスタンスおよび一部は、ストアフロントの買い物客の行動から収集される場合があります。 そのデータは、セキュリティで保護されたクラウドストレージに保持されます。

の場合 [!DNL Product Recommendations]の場合、SaaS データ スペースには、カタログと行動データが含まれています。 を指定できます。 [!DNL Commerce] 次の方法で SaaS データ空間にインスタンス化する [選択](https://docs.magento.com/user-guide/configuration/services/saas.html) が含まれる [!DNL Commerce] 設定。

>[!WARNING]
>
> 実稼動用の SaaS データ領域を実稼動用にのみ使用する [!DNL Commerce] データの競合を回避するためのインストール。 そうしないと、テストデータで実稼動サイトデータが汚染され、デプロイメントの遅延が発生するリスクがあります。 例えば、実稼動製品のデータが、ステージング URL などのステージングデータと誤って上書きされる可能性があります。

### SaaS プロジェクトの選択または作成 {#createsaasenv}

>[!NOTE]
>
> が表示されない場合、 **[!UICONTROL Commerce Services Connector]** セクション： [!DNL Commerce] 設定する。をインストールする必要があります [!DNL Commerce] 目的に合ったモジュール [[!DNL Commerce] サービス](#availableservices).

SaaS プロジェクトを選択または作成するには、 [!DNL Commerce] からの API キー [!DNL Commerce] ストアのライセンス所有者。

1. 日 _Admin_ サイドバー、に移動 **システム** / サービス / **Commerce サービスコネクタ**.

1. が含まれる _サンドボックス API キー_ および _実稼動 API キー_ セクションに、キー値を貼り付けます。

   秘密鍵には次を含める必要があります `----BEGIN PRIVATE KEY---` キーの先頭、および `----END PRIVATE KEY----` 秘密鍵の末尾。

1. クリック **保存**.

キーに関連付けられている SaaS プロジェクトは、に表示されます **プロジェクト** のフィールド **SaaS 識別子** セクション。

1. SaaS プロジェクトが存在しない場合、 **プロジェクトを作成**. 次に、 **プロジェクト** フィールドに、SaaS プロジェクトの名前を入力します。

   SaaS プロジェクトを作成する場合、 [!DNL Commerce] は、に応じて 1 つ以上の SaaS データスペースを生成します [!DNL Commerce] ライセンス：
   - Adobe Commerce – 実稼動データスペース 1 つ、テスト用データスペース 2 つ
   - Magento Open Source - 1 つの実稼動データスペースで、テスト用のデータスペースはない

1. 「」を選択します **データスペース** を現在の設定に使用するには [!DNL Commerce] ストア。

>[!WARNING]
>
> マイアカウントの API ポータルセクションで新しいキーを生成した場合、直ちに管理設定の API キーを更新します。 新しいキーを生成し、管理者でそれらを更新しない場合、SaaS 拡張機能は機能しなくなり、貴重なデータが失われます。

SaaS プロジェクトまたはデータ領域の名前を変更するには、 **名前を変更** どちらかの隣。 名前を変更しても、サービスには影響しません。名前は、プロジェクトとデータ スペースを識別および区別するのに役立つラベルにすぎないからです。

## IMS 組織（オプション） {#organizationid}

Adobe Commerce インスタンスをAdobe Experience Platformに接続するには、Adobe IDを使用してAdobeアカウントにログインします。 ログインすると、Adobeアカウントに関連付けられた IMS 組織がこのセクションに表示されます。

## カタログ同期

いつ [!DNL Commerce] インスタンスの接続先 [!DNL Commerce Services]の場合、カタログ同期プロセスによってユーザーから製品データを [!DNL Commerce] サーバー先 [!DNL Commerce Services]. 現在、カタログ同期サービスを使用するのは、製品Recommendationsのみです。 [詳細情報](catalog-sync.md) カタログ同期プロセスについて。
