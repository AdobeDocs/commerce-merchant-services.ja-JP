---
title: Commerce Services コネクタ
description: 実稼働用 API キーとサンドボックス API キーを使用して、Adobe CommerceまたはMagento Open Sourceインスタンスをサービスに統合する方法について説明します。
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
feature: Services, Saas
role: Admin, User
source-git-commit: 2d6b80b5133eb00ac42a5f2b64c5846ad30e56c4
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

一部のAdobe CommerceおよびMagento Open Source機能は、 [!DNL Commerce Services]  SaaS（サービスとしてのソフトウェア）としてデプロイされます。 これらのサービスを使用するには、 [!DNL Commerce] 実稼働用とサンドボックス API キーを使用し、 [設定](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html). 設定が必要なのは 1 回だけです。

## 利用可能なサービス {#availableservices}

以下に、 [!DNL Commerce] でアクセスできる機能 [!DNL Commerce Services Connector]:

| サービス | 対象 |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) Adobe Senseiを活用 | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) Adobe Senseiを活用 | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe CommerceとMagento Open Source |
| [[!DNL Channel Manager]](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/intro-to-channel-manager/overview.html) | Adobe CommerceとMagento Open Source |
| [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html) | Adobe Commerce |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [[!DNL Data Connection]](/help/data-connection/overview.md) | Adobe Commerce |

## アーキテクチャ

高いレベルでは、 [!DNL Commerce Services Connector] は、次のコア要素で構成されています。

![Commerce Services コネクタのアーキテクチャ](assets/saas-config-sync-workflow.png)

次のセクションでは、これらの各要素について詳しく説明します。

## 資格情報 {#apikey}

実稼働用 API キーとサンドボックス API キーは、 [!DNL Commerce] ライセンス所有者のアカウント。一意の [!DNL Commerce] ID (MageID)。 次のようなサービスの使用権限の検証に合格するには： [!DNL Product Recommendations] または [!DNL Live Search]を使用する場合、マーチャントの組織のライセンス所有者は、アカウントが正常である限り、API キーのセットを生成できます。 キーは、ライセンス所有者に代わってプロジェクトと環境を管理するシステムインテグレーターまたは開発チームと「知っておく必要がある」ベースで共有できます。 また、ソリューションインテグレーターは、 [!DNL Commerce Services]. ソリューションインテグレーターの場合、 [!DNL Commerce] パートナー契約は、API キーを生成する必要があります。

### 実稼働環境とサンドボックス API キーを生成する {#genapikey}

1. にログインします。 [!DNL Commerce] アカウント [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}。

1. の下 **Magento** タブ、選択 **API ポータル** サイドバーに表示されます。

1. 次から： _環境_ メニュー、選択 **実稼動** または **サンドボックス**.

1. 名前を _API キー_ 「 」セクションで、「 」をクリックします。 **新規追加**.

   新しいキーをダウンロードするためのダイアログが開きます。

   ![秘密鍵をダウンロード](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > これは、鍵をコピーまたはダウンロードする必要がある唯一の機会です。

1. クリック **ダウンロード** 次に、「 **キャンセル**.

1. 各環境（実稼動およびサンドボックス）に対して、上記の手順を繰り返します。

   The **API キー** 「 」セクションに API キーが表示されるようになりました。 実稼動用キーとサンドボックスキーの両方が必要な場合は、 [SaaS プロジェクトを選択または作成する](#createsaasenv).

## SaaS 設定 {#saasenv}

[!DNL Commerce] インスタンスは、SaaS プロジェクトと SaaS データスペースを使用して設定し、 [!DNL Commerce Services] では、適切な場所にデータを送信できます。 SaaS プロジェクトは、すべての SaaS データスペースをグループ化します。 SaaS データスペースは、 [!DNL Commerce Services] を有効にします。 このデータの一部は、 [!DNL Commerce] インスタンスと一部は、ストアフロントでの買い物客の行動から収集される場合があります。 その後、そのデータは保持され、クラウドストレージを保護します。

の場合 [!DNL Product Recommendations]に設定すると、SaaS データスペースには、カタログと行動データが含まれます。 次の項目を指定します。 [!DNL Commerce] 次の方法で SaaS データ空間にインスタンスを送信する [選択](https://docs.magento.com/user-guide/configuration/services/saas.html) （内） [!DNL Commerce] 設定。

>[!WARNING]
>
> 実稼動環境の SaaS データ領域を実稼動環境でのみ使用する [!DNL Commerce] データの衝突を回避するためのインストール。 そうしないと、実稼動サイトのデータがテストデータで汚染され、デプロイメントが遅延する可能性があります。 例えば、実稼動製品のデータがステージング URL などのステージングデータから誤って上書きされる可能性があります。

### SaaS プロジェクトを選択または作成する {#createsaasenv}

>[!NOTE]
>
> 次の項目が表示されない場合、 **[!UICONTROL Commerce Services Connector]** セクション内 [!DNL Commerce] 設定の場合は、 [!DNL Commerce] 目的のモジュール [[!DNL Commerce] サービス](#availableservices).

SaaS プロジェクトを選択または作成するには、 [!DNL Commerce] からの API キー [!DNL Commerce] お客様の店舗のライセンス所有者。

1. 次の日： _管理者_ サイドバー、移動 **システム** /サービス/ **Commerce Services コネクタ**.

1. Adobe Analytics の _サンドボックス API キー_ および _実稼動 API キー_ 「 」セクションで、キー値を貼り付けます。

   秘密鍵にはを含める必要があります `----BEGIN PRIVATE KEY---` キーの先頭と `----END PRIVATE KEY----` 秘密鍵の最後に。

1. クリック **保存**.

キーに関連付けられている SaaS プロジェクトは、 **プロジェクト** フィールド **SaaS 識別子** 」セクションに入力します。

1. SaaS プロジェクトが存在しない場合は、「 **プロジェクトを作成**. 次に、 **プロジェクト** 「 」フィールドに、SaaS プロジェクトの名前を入力します。

   SaaS プロジェクトを作成する場合、 [!DNL Commerce] によって、に応じて 1 つ以上の SaaS データスペースが生成されます [!DNL Commerce] ライセンス：
   - Adobe Commerce - 1 つの実稼動データ領域、2 つのテストデータ領域
   - Magento Open Source:1 つの実稼動データ領域。テスト用のデータ領域なし

1. を選択します。 **データスペース** を使用して、 [!DNL Commerce] ストア。

>[!WARNING]
>
> マイアカウントの API ポータルセクションで新しいキーを生成する場合は、管理者設定で API キーを直ちに更新してください。 新しいキーを生成し、Admin で更新しない場合、SaaS 拡張機能は機能しなくなり、有用なデータが失われます。

SaaS プロジェクトまたはデータスペースの名前を変更するには、 **名前を変更** どちらか一方の隣に 名前は、プロジェクトとデータスペースを識別および区別するのに役立つラベルに過ぎないので、名前を変更してもサービスには影響しません。

## IMS 組織（オプション） {#organizationid}

Adobe CommerceインスタンスをAdobe Experience Platformに接続するには、Adobe IDを使用してAdobeアカウントにログインします。 ログインすると、Adobeアカウントに関連付けられている IMS 組織がこのセクションに表示されます。

## カタログの同期

次の場合に、 [!DNL Commerce] インスタンスが正常に接続しました [!DNL Commerce Services]を使用する場合、カタログ同期プロセスは、 [!DNL Commerce] サーバーから [!DNL Commerce Services]. 現在、カタログ同期サービスを使用しているのは製品のRecommendationsのみです。 [詳細情報](catalog-sync.md) カタログ同期プロセスについて
