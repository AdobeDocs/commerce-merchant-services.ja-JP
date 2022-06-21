---
title: Commerce Services コネクタ
description: 実稼働用 API キーとサンドボックス API キーを使用して、Adobe CommerceまたはMagento Open Sourceインスタンスをサービスに統合する方法について説明します。
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
source-git-commit: 42cb709f4699fcdd56df7ca02466ab416f01cab2
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

一部のAdobe CommerceおよびMagento Open Source機能は、 [!DNL Commerce Services]  SaaS（サービスとしてのソフトウェア）としてデプロイされます。 これらのサービスを使用するには、 [!DNL Commerce] 実稼働用とサンドボックス API キーを使用し、 [設定](https://docs.magento.com/user-guide/configuration/services/saas.html). 設定が必要なのは 1 回だけです。

## 利用可能なサービス {#availableservices}

以下に、 [!DNL Commerce] でアクセスできる機能 [!DNL Commerce Services Connector]:

| サービス | 使用可否 |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) Adobe Senseiを活用 | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) Adobe Senseiを活用 | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe CommerceとMagento Open Source |

## アーキテクチャ

高いレベルでは、 [!DNL Commerce Services Connector] は、次のコア要素で構成されています。

![Commerce Services コネクタのアーキテクチャ](assets/saas-config-sync-workflow.png)

次のセクションでは、これらの各要素について詳しく説明します。

## 資格情報 {#apikey}

実稼働用とサンドボックス API キーは、 [!DNL Commerce] 一意の [!DNL Commerce] ID (MageID)。 次のようなサービスの使用権限の検証に合格するには： [!DNL Product Recommendations] または [!DNL Live Search]を使用する場合、マーチャントの組織のライセンス所有者は、アカウントが正常である限り、API キーのセットを生成できます。 キーは、ライセンス所有者に代わってプロジェクトと環境を管理するシステムインテグレーターまたは開発チームと「知っておく必要がある」という理由で共有できます。 また、ソリューションインテグレーターは、 [!DNL Commerce Services]. ソリューションインテグレーターの場合、 [!DNL Commerce] パートナー契約は、API キーを生成する必要があります。

### 実稼働環境とサンドボックス API キーを生成する {#genapikey}

1. にログインします。 [!DNL Commerce] アカウント [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}。

1. 以下 **Magento** タブ、選択 **API ポータル** サイドバーに表示されます。

1. 次の _環境_ メニュー、選択 **実稼動** または **サンドボックス**.

1. 名前を _API キー_ 「 」セクションで、「 」をクリックします。 **新規追加**.

   新しいキーをダウンロードするためのダイアログが開きます。

   ![秘密鍵をダウンロード](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > これは、鍵をコピーまたはダウンロードする必要がある唯一の機会です。

1. クリック **ダウンロード** 次に、 **キャンセル**.

1. 各環境（実稼動およびサンドボックス）に対して、上記の手順を繰り返します。

   この **API キー** 「 」セクションに API キーが表示されるようになりました。 実稼動用キーとサンドボックスキーの両方が必要な場合は、 [SaaS プロジェクトを選択または作成する](#createsaasenv).

## SaaS 設定 {#saasenv}

[!DNL Commerce] インスタンスは、SaaS プロジェクトと SaaS データスペースを使用して、 [!DNL Commerce Services] では、適切な場所にデータを送信できます。 SaaS プロジェクトは、すべての SaaS データスペースをグループ化します。 SaaS データスペースは、 [!DNL Commerce Services] を有効にします。 このデータの一部は、 [!DNL Commerce] インスタンスと一部は、ストアフロントでの買い物客の行動から収集される場合があります。 その後、そのデータは保持され、クラウドストレージを保護します。

の場合 [!DNL Product Recommendations]に設定すると、SaaS データスペースには、カタログと行動データが含まれます。 次の項目を指定： [!DNL Commerce] 次の方法で SaaS データ空間にインスタンスを送信 [選択](https://docs.magento.com/user-guide/configuration/services/saas.html) 内 [!DNL Commerce] 設定。

>[!WARNING]
>
> 実稼動環境の SaaS データ領域を実稼動環境でのみ使用する [!DNL Commerce] データの衝突を回避するためのインストール。 そうしないと、実稼動サイトのデータがテストデータで汚染され、デプロイメントが遅延する可能性があります。 例えば、実稼動製品のデータがステージング URL などのステージングデータから誤って上書きされる可能性があります。

### SaaS プロジェクトを選択または作成する {#createsaasenv}

>[!NOTE]
>
> 次の項目が表示されない場合、 **[!UICONTROL Commerce Services Connector]** セクション [!DNL Commerce] 設定するには、 [!DNL Commerce] 目的の [[!DNL Commerce] サービス](#availableservices).

SaaS プロジェクトを選択または作成するには、 [!DNL Commerce] からの API キー [!DNL Commerce] お客様の店舗のライセンス所有者。

1. の _管理者_ サイドバー、移動 **システム** /サービス/ **Commerce Services コネクタ**.

1. 内 _サンドボックス API キー_ および _実稼動 API キー_ セクションで、キー値を貼り付けます。

   秘密鍵には、 `----BEGIN PRIVATE KEY---` キーの先頭と `----END PRIVATE KEY----` 秘密鍵の最後に。

1. クリック **保存**.

キーに関連付けられている SaaS プロジェクトは、 **プロジェクト** フィールド **SaaS 識別子** 」セクションに入力します。

1. SaaS プロジェクトが存在しない場合は、「 **プロジェクトを作成**. 次に、 **プロジェクト** 「 」フィールドに、SaaS プロジェクトの名前を入力します。

   SaaS プロジェクトを作成する場合、 [!DNL Commerce] によって、に応じて 1 つ以上の SaaS データスペースが生成されます [!DNL Commerce] ライセンス：
   - Adobe Commerce - 1 つの実稼動データ領域2 つのテスト用データスペース
   - Magento Open Source- 1 つの実稼動データ領域テストデータスペースなし

1. を選択します。 **データスペース** を [!DNL Commerce] ストア。

>[!WARNING]
>
> マイアカウントの API ポータルセクションで新しいキーを生成する場合は、管理者設定で API キーを直ちに更新してください。 新しいキーを生成し、Admin で更新しない場合、SaaS 拡張機能は機能しなくなり、有用なデータが失われます。

SaaS プロジェクト名またはデータスペース名を変更するには、 **名前を変更**.

## IMS 組織（オプション） {#organizationid}

( この機能は、今後のAdobe Experience Platformとの統合のためのものです )。 Adobe CommerceインスタンスをAdobe Experience Platformに接続するには、Adobe IDを使用してAdobeアカウントにログインします。 ログインすると、Adobeアカウントに関連付けられている IMS 組織がこのセクションに表示されます。

## カタログの同期

次の場合、 [!DNL Commerce] インスタンスが正常に接続しました [!DNL Commerce Services]カタログ同期プロセスで、 [!DNL Commerce] サーバーから [!DNL Commerce Services]. [詳細情報](catalog-sync.md) カタログ同期プロセスについて
