---
title: を使用した、Real-Time CDPでのオーディエンスの作成 [!DNL Commerce] イベントデータ
description: の使用方法を学ぶ [!DNL Commerce] Real-Time CDPでオーディエンスを作成するためのイベントデータ
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: fc2a7ba6891cf8affdec13b0400d75350284faa2
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 0%

---

# を使用したReal-Time CDPでのオーディエンスの作成 [!DNL Commerce] イベントデータ

から取得したイベントデータを使用 [!DNL Commerce] Real-Time CDPでオーディエンスを作成するために保存します。 取得されるデータは、閲覧行動、過去の購入、プロファイル属性、コンバージョンまたはチャーンへの傾向、ロイヤルティステータス、高および低の顧客価値などに基づいています。

## どのデータの使用を検討すればよいですか？

ストアフロント、バックオフィス、プロファイルイベントからのデータを使用して、Real-Time CDPでオーディエンスを作成します。

| データタイプ | ストアフロントデータ（行動イベント） | バックオフィスデータ（サーバーサイドイベント） | 顧客プロファイルとセグメントデータ |
|---|---|---|---|
| **定義** | サイトに対する顧客のクリックまたはアクション。 | 各注文のライフサイクルと詳細（過去および現在）に関する情報。 | 買い物客は誰で、どのようなセグメントに該当するか。 |
| **Adobe Commerceでキャプチャされたイベント** | [productPageView](events.md#productpageview)<br>[addToCart](events.md#addtocart) | [placeOrder](events.md#completecheckout)<br>[orderplaced](events-backoffice.md#orderplaced)<br>[orderLineItemRefunded](events-backoffice.md#orderlineitemrefunded)<br>[キャンセル済みの注文](events-backoffice.md#ordercancelled)<br>[注文履歴](connect-data.md#send-historical-order-data) | [createAccount](events.md#createaccount)<br>[editAccount](events.md#editaccount)<br>[プロファイルレコード](events-profilerecord.md) |

## 他の顧客は何を達成しましたか？

Adobe [!DNL Commerce] お客様は、Real-Time CDPで作成されたオーディエンスをアクティブ化し、それらをお客様にデプロイすることで、大きなビジネス上の影響を受けています [!DNL Commerce] インスタンス。

グローバルなマルチブランドのアパレル小売業者が達成した成果：

- 1,000 万件に及ぶ統合された顧客プロファイルを持つ 1 つの情報源
- 様々なチャネルにわたってエンゲージメントを高めるために、「ハイインテント顧客」の 40 以上の一意のオーディエンスを作成しました

あるグローバル飲料企業は以下の情報を収集した。

- 100 か国以上から 9,800 万件の顧客プロファイル

## それでは、始めましょう

この記事では、以下の方法を学びます。

- に基づいて、Real-Time CDPでオーディエンスを作成します [!DNL Commerce] イベントが収集するデータ
- のオーディエンスをアクティベート [!DNL Commerce] store
- オーディエンスの使用： [!DNL Commerce] 買い物かごの価格ルールを通知するには

>[!IMPORTANT]
>
>を使用して、この記事で説明しているタスクを実行します。 [!DNL Commerce] サンドボックス環境。 これにより、Experience Platformに送信するストアフロントおよびバックオフィスのイベントデータが、実稼動イベントデータを薄めることがなくなります。

### 前提条件

開始する前に、次を確認します。

- Real-Time CDPを使用するようにプロビジョニングされています。 不明な場合は、システムインテグレーターまたはプロジェクトや環境を管理する開発チームにお問い合わせください。
- あなた [installed](install.md) および [設定済み](connect-data.md) この [!DNL Data Connection] 拡張子 [!DNL Commerce].
- あなた [確認済み](connect-data.md#confirm-that-event-data-is-collected) その [!DNL Commerce] イベントデータはExperience Platformエッジに到達します。

### 1. オーディエンスの作成

オーディエンスは、類似した行動や特性を共有する顧客のセットです。 この演習では、ストア内の特定の製品に関心を持つユーザーを選定するオーディエンスを作成します。

この演習を簡略化するには、のイベントデータを使用します [productPageView](events.md#productpageview) イベント。 このイベントでは、製品名、SKU、価格など、表示された製品に関する詳細をキャプチャします。

このイベントデータを使用して、SKU （製品識別子）がサイト上の特定の製品と等しく、イベントが最終日に発生する「製品表示数」イベントを少なくとも 1 つ持つ個人がオーディエンスに含まれることを指定します。&#x200B;

1. Experience Platformを開いて選択 **[!UICONTROL Audiences]** 左側のナビゲーションメニューから。

   ![オーディエンスダッシュボード](assets/audience-left-rail.png)

1. クリック **[!UICONTROL Create Audience]**.

   ![オーディエンスを作成](assets/browse-create-audience.png)

   この **セグメントビルダー** ワークスペースが表示されます。

1. が含まれる **セグメントビルダー** ワークスペースで、 **ルールを作成** 作成方法。

   ![ルールを作成](assets/build-rule.png)

   この **セグメントビルダー** ワークスペースでは、オーディエンスのルールと条件を定義&#x200B;ます。 これらのルールと条件は、Commerce ストアのイベントおよびプロファイルデータに基づいており、ユーザーがオーディエンスに該当するかどうかを判断する条件を定義します。 例えば、特定の製品を表示したユーザーや、特定の期間内に購入を行ったユーザーを含むルールを作成できます。 の詳細情報 [セグメントビルダー](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) およびルールと条件。

1. 「」を選択します [イベント](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder#events) タブ。

   ![「イベント」タブ](assets/audience-events-tab.png)

1. 「製品表示回数」イベントタイプを検索します。 次に、にドラッグ&amp;ドロップします **セグメントビルダー** ワークスペース。

1. に戻る **イベント** タブで「SKU」を検索します（の下のデータフィールド） `productListItems` フィールド。 ドラッグ&amp;ドロップ **セグメントビルダー** 上部のワークスペース **製品表示** イベント。

   この **イベントルール** 「」セクションが表示され、オーディエンスを作成する特定の製品を指定できます。

   ![SKU を選択](assets/audience-addsku.png)

1. 「」をクリックして、時間間隔を 1 日に設定します **いつでも** および選択 *過去* 値： *1*.

   オーディエンスを作成する際に、最近のアクティビティを取り込むための時間間隔を指定できます。 時間間隔を設定すると、特定の期間内の最近のインタラクションまたは行動に基づいてユーザーをターゲットに設定できます。

1. が含まれる **オーディエンスプロパティ** ワークスペースの右側の「」セクションで、オーディエンスの名前、説明、評価方法を指定して、オーディエンスプロパティを設定します。

1. オーディエンスを保存するには、をクリックします。 **[!UICONTROL Save and Close]**.

   オーディエンスの詳細はに表示されます **対象読者** ダッシュボード。

### 2.へのオーディエンスをアクティブ化する [!DNL Commerce] 宛先

オーディエンスをで使用できるようになります。 [!DNL Commerce] に対してアクティブ化する [!DNL Commerce] の宛先。

>[!IMPORTANT]
>
>まだ設定していない場合 [!DNL Commerce] データを受信するための使用可能な宛先として、を参照してください [Adobe [!DNL Commerce] 接続](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-commerce) トピック。

1. が含まれる **詳細** オーディエンスのタブで、 **宛先に対してアクティブ化**.

1. を選択 [!DNL Commerce] の宛先。 次に、 **次**.

1. 「」をクリックしてアクティベーションプロセスを完了します **[!UICONTROL Finish]**.

## 3. オーディエンスダッシュボードでオーディエンスを表示する

対象： [!DNL Commerce]、すべて表示できます [アクティブ](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations) ユーザー向けにパーソナライズできるオーディエンス [!DNL Commerce] を使用したインスタンス **Real-Time CDP オーディエンス** ダッシュボード。

にアクセスするには **Real-Time CDP オーディエンス** ダッシュボードで、 _Admin_ サイドバーの後、に移動します。 **[!UICONTROL Customers]** > **[!UICONTROL Real-time CDP Audience]**.

ダッシュボードで、作成したオーディエンスを探します。 買い物かごの価格ルールまたは動的ブロックでは使用されていないことに注意してください。 次の節では、オーディエンスを買い物かごの価格ルールにリンクします。

![Real-Time CDP Audiences ダッシュボード](assets/real-time-cdp-dashboard.png)

### 4. オーディエンスに基づく買い物かご価格ルールの作成

この節では、新しいオーディエンスに基づいて買い物かごの価格ルールを作成する方法について説明します。

1. 新しいオーディエンスがに表示されていることを確認します。 **Real-Time CDP オーディエンス** ダッシュボード。
1. [買い物かご価格ルールの作成](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create).
1. [条件を設定](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#use-real-time-cdp-audiences-to-set-a-condition) 新しいオーディエンスを使用した買い物かご価格ルールの。
1. [アクションの設定](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#step-3-define-the-actions) 商品が買い物かごに追加された際に実行する。
1. 引き続き買い物かご価格ルールを設定します。
1. サンドボックスインスタンスの顧客ビューに移動します。
1. オーディエンスに基づいて作成した製品を買い物かごに追加します。 買い物かごの価格ルールが有効になっていることに注意してください。

## まとめ

この演習では、Real-Time CDPでオーディエンスを作成し、に対してアクティブ化しました [!DNL Commerce] の宛先。 次に、 [!DNL Commerce] 管理者は、そのオーディエンスに基づいて買い物かご価格ルールを作成し、サンドボックス環境でルールを有効にしました。
