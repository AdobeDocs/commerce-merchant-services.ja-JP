---
title: Adobe Journey Optimizerを使用して、放棄された買い物かごのメールを送信する
description: Adobe Journey Optimizerを使用して、放棄された買い物かごのメールを送信する方法を説明します。
role: Admin, Developer
feature: Personalization, Integration
exl-id: 5e4e7c0a-c00b-4278-bd73-6b6f2fcbe770
source-git-commit: ee84525a9146123d80c303e40acdc6baba098cdd
workflow-type: tm+mt
source-wordcount: '1412'
ht-degree: 0%

---

# Adobe Journey Optimizerを使用して、放棄された買い物かごにメールを送信

買い物かごやブラウザーセッションが放棄された場合に、パーソナライズされた再エンゲージメントメールまたは通知を配信する方法を説明します。 この記事では、多数の製品やカテゴリを閲覧した顧客、製品にエンゲージした顧客、ページで時間を費やした顧客から生成されたデータを使用します。

## どのデータの使用を検討すればよいですか？

ストアフロントおよびバックオフィスイベントのデータを使用して、放棄された買い物かごの作成、メールの参照、通知を行います。

| データタイプ | ストアフロントデータ（行動イベント） | バックオフィスデータ（サーバーサイドイベント） |
|---|---|---|
| **定義** | サイトに対する顧客のクリックまたはアクション。 | 各注文のライフサイクルと詳細（過去および現在）に関する情報。 |
| **Adobe Commerceでキャプチャされたイベント** | [pageView](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#pageview)<br>[productPageView](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events)<br>[addToCart](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#addtocart)<br>[openCart](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#opencart)<br>[startCheckout](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#startcheckout)<br>[completeCheckout](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#completecheckout) | [orderPlaced](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events-backoffice#orderplaced)<br>[注文履歴](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/fundamentals/connect-data#send-historical-order-data) |

### Adobe Commerceだけで何ができますか？

Adobeを使用 [!DNL Commerce] ルールベースでメールのリマインダーを設定できます。リマインダーは、買い物かごとして機能したり、放棄されたメールを参照したりできます。 詳細はこちらをご覧ください。

### Adobeを使用して実行できること [!DNL Commerce] Experience Cloudは？

- **Adobe [!DNL Commerce] （Adobe Journey Optimizerを使用）** - Adobeの使用 [!DNL Commerce] Adobe Journey Optimizerのを使用すると、以下を使用できます [!DNL Commerce] オムニチャネル離脱ジャーニーのトリガーとしてのデータ。 顧客属性、放棄された項目、その他のショッピング行動、過去の購入行動に基づいて、ジャーニーをパーソナライズできます。

- **Adobe Commerce、Adobe Journey Optimizer、Adobe Real-Time CDP** - Real-Time CDPを追加すると、統合された顧客プロファイルと、一元管理されたルールベースまたは AI を利用したオーディエンスに基づいて、放棄キャンペーンをさらに絞り込むことができます。 例えば、以下を作成できます。

   - 離脱率の低い「強力なコンバーター」オーディエンス
   - 特定のカテゴリを複数回再訪問した「高い考慮事項」オーディエンス
   - 費用とロイヤルティが高いものの、最近は放棄された「高い可能性」のあるオーディエンス

### 他の顧客は何を達成しましたか？

Adobe [!DNL Commerce] お客様は、Adobeを使用してパーソナライズされた放棄キャンペーンを実装することにより、大きなビジネス上の影響を達成しています [!DNL Commerce]、Adobe [!DNL Journey Optimizer]、およびAdobe [!DNL Real-Time CDP].

グローバルなマルチブランドのアパレル小売業者が達成した成果：

- 新しいキャンペーンからのクリックによる 1.9 倍のコンバージョン
- オムニチャネル離脱ジャーニーによる売上高が 57% 増加
- 再エンゲージメントキャンペーンのコンバージョン率が 41% 増加
- 1 週間に 1,000 人以上の新規買い物客がエンゲージ

世界的な飲料企業は以下を達成しました。

- 再エンゲージメントメールの開封率 36%
- クリックスルー率が 21% 向上
- コンバージョン率が 8.5% 向上
- 再関与した放棄者の 89% がコンバージョン

## それでは、始めましょう

この特定の使用例では、のデータを使用して放棄された買い物かごメールを作成することに焦点を当てています [!DNL Commerce] インスタンスとAdobeへの送信 [!DNL Journey Optimizer].

### Adobe Journey Optimizerとは

[Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) は、買い物客向けにコマースエクスペリエンスをパーソナライズするのに役立ちます。 例えば、Journey Optimizerを使用して、小売店向けの週別プロモーションなどのスケジュールされたマーケティングキャンペーンを作成して配信したり、顧客が買い物かごに商品を追加したもののチェックアウトプロセスを完了しなかった場合に、放棄された買い物かごのメールを生成したりできます。

このトピックでは、をリッスンして、放棄された買い物かごメールを作成する方法を説明します。 `checkout` から生成されたイベント [!DNL Commerce] インスタンスを作成し、Journey Optimizerでそのイベントに応答します。

>[!IMPORTANT]
>
>デモ目的で、を使用します [!DNL Commerce] サンドボックス環境を使用すると、Experience Platformに送信するストアフロントおよびバックオフィスイベントデータで、実稼動イベントデータを薄めることがなくなります。

### 前提条件

これらの手順を開始する前に、以下を確認します。

- Adobeを使用するようにプロビジョニングされています [!DNL Journey Optimizer]. 不明な場合は、システムインテグレーターまたはプロジェクトや環境を管理する開発チームにお問い合わせください。
- あなた [installed](install.md) および [設定済み](connect-data.md) この [!DNL Data Connection] 拡張子 [!DNL Commerce].
- あなた [確認済み](connect-data.md#confirm-that-event-data-is-collected) その [!DNL Commerce] イベントデータはExperience Platformエッジに到達します。

## 手順 1：でユーザーを作成する [!DNL Commerce] サンドボックス環境

サンドボックス環境でユーザーを作成して、そのユーザーアカウント情報がExperience Platformに表示されることを確認します。 指定したメールが、このセクションで後ほど放棄された買い物かごメールを送信する際に使用するメールとして有効であることを確認します。

1. ログインするか、アカウントを [!DNL Commerce] サンドボックス環境。

   ![テストアカウントにログイン](assets/sign-in-account.png){width="700" zoomable="yes"}

   （を使用） [!DNL Data Connection] 拡張機能がインストールおよび設定されると、このアカウント情報はプロファイルとしてExperience Platformに送信されます。

1. ユーザーアカウント情報がに表示されることを確認します。 **[!UICONTROL Profile]** Experience Platformのセクション。

   に移動 **[!UICONTROL Profiles]** Adobe Experience Platformで。 クリック **[!UICONTROL Detail]** プロファイルに作成したプロファイルが表示されます。

   ![プロファイルを確認](assets/check-event-profile.png){width="700" zoomable="yes"}

## 手順 2:Journey Optimizerでイベントを表示する

あなたの [!DNL Commerce] サンドボックス環境、商品ページの表示、買い物かごへの商品の追加、買い物客が実行するその他の様々なアクティビティの完了により、ストアフロントでのトリガーイベント。 次に、これらのイベントがJourney Optimizerに送信されていることを確認します。

1. ローンチ [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).
1. を選択 **[!UICONTROL Profiles]**.
1. を設定 **[!UICONTROL Identity namespace]** 対象： `Email`.
1. を **[!UICONTROL Identity value]** をメールアドレスに送信します。
1. プロファイルを選択してから、 **[!UICONTROL Events]** タブ。

   ![イベントの詳細を確認](assets/check-event-details.png){width="700" zoomable="yes"}

   を探します。 `commerce.checkouts` イベントペイロードをイベントで確認します。

   ```json
   "personID": "84281643067178465783746543501073369488", 
   "eventType": "commerce.checkouts", 
   "_id": "4b41703f-e42e-485b-8d63-7001e3580856-0", 
   "commerce": { 
       "cart": {}, 
       "checkouts": { 
           "value": 1 
       } 
   ```

   ご覧のように、完全なイベントペイロードには豊富なイベントデータが含まれています。 次の節では、をリッスンして応答するイベントをJourney Optimizerで設定します。 `commerce.checkouts` から生成されたイベント [!DNL Commerce] ストアフロント。

## 手順 3:Journey Optimizerでのイベントの設定

Journey Optimizerで 2 つのイベントを設定：1 つのイベントがをリッスンします。 `commerce.checkouts` Commerceからのイベント、もう 1 つは、特定の時間が経過するのを待ってから、放棄された買い物かごのメールがトリガーされる基本的なタイムアウトイベントです。

### リスナーイベントの作成

1. ローンチ [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).

1. クリック **[!UICONTROL Configurations]** の下 **[!UICONTROL Administration]** 左側のウィンドウのセクション。

1. が含まれる **[!UICONTROL Events]** タイル、クリック **[!UICONTROL Manage]**.

   ![Journey Optimizer イベントの設定](assets/ajo-config.png){width="700" zoomable="yes"}

1. 日 **[!UICONTROL Events]** ページ、クリック **[!UICONTROL Create Event]**.

1. 右側のナビゲーションで、イベントを次のように設定します。

   1. を **[!UICONTROL Name]** コピー先： `firstname_lastname_checkout`.
   1. を設定 **[!UICONTROL Type]** 対象： **[!UICONTROL Unitary]**.
   1. を設定 **[!UICONTROL Event id typ]e** 対象： **[!UICONTROL Rule based]**.
   1. を設定 **[!UICONTROL Schema]** 宛先： [!DNL Commerce] [スキーマ](update-xdm.md).
   1. を選択 **[!UICONTROL Fields]** を開きます **[!UICONTROL Fields]** ページ。 次に、このイベントで役立つフィールドを選択します。 例えば、の下のすべてのフィールドを選択します **[!UICONTROL Product list items]**, **[!UICONTROL Commerce]**, **[!UICONTROL eventType]**、および **[!UICONTROL Web]**.
   1. クリック **[!UICONTROL OK]** 選択したフィールドを保存します。
   1. 内でクリック **[!UICONTROL Event id condition]** フィールド。 次に、条件を作成します。 `eventType` が次と等しい `commerce.checkouts` および `personalEmail.address` は、前の節でプロファイルを作成した際に使用したメールアドレスと同じです。

      ![Journey Optimizer設定条件](assets/ajo-set-condition.png){width="700" zoomable="yes"}

   1. クリック **[!UICONTROL OK]**.
   1. クリック **[!UICONTROL Save]** イベントを保存します。

### タイムアウトイベントの作成

1. 以前と同様に、Journey Optimizerでイベントを作成します。

1. 右側のナビゲーションで、イベントを次のように設定します。

   1. を **[!UICONTROL Name]** コピー先： `firstname_lastname_timeout`.
   1. を設定 **[!UICONTROL Type]** 対象： **[!UICONTROL Unitary]**.
   1. を設定 **[!UICONTROL Event id type]** 対象： **[!UICONTROL Rule based]**.
   1. を設定 **[!UICONTROL Schema]** 宛先： [!DNL Commerce] [スキーマ](update-xdm.md).
   1. を **[!UICONTROL Schema]**, **[!UICONTROL Fields]**、および **[!UICONTROL Event id condition]** 上記と同じです。
   1. クリック **[!UICONTROL Save]** イベントを保存します。

これら 2 つのイベントを設定し、放棄された買い物かごメールを送信するジャーニーを作成します。

## 手順 4：チェックアウトジャーニーの作成

をリッスンするジャーニーの作成 `commerce.checkouts` イベントが発生し、指定した時間が経過した後に、放棄された買い物かごのメールを送信します。

1. Journey Optimizerで、を選択します。 **[!UICONTROL Journeys]** 未満 **J[!UICONTROL OURNEY MANAGEMENT]**.
1. クリック **[!UICONTROL Create Journey]**.
1. ジャーニーの名前を指定します。
1. クリック **[!UICONTROL OK]** をクリックしてジャーニーを保存します。
1. 左側のナビゲーションでの下の **[!UICONTROL EVENTS]** セクションで、以前に作成したチェックアウトイベントを検索します。 `firstname_lastname_checkout` をクリックして、キャンバスにドラッグ&amp;ドロップします。

   >[!TIP]
   >
   >イベントをダブルクリックすると、そのイベントがキャンバスに自動的に追加されます。

1. タイムアウトイベントを検索して、キャンバスに追加します。
1. タイムアウトイベントをダブルクリックします。

   1. が含まれる **[!UICONTROL Timeout]** セクションで、 **[!UICONTROL Define the event time]** チェックボックス。
   1. が含まれる **[!UICONTROL Wait for]** フィールド入力 `1` および `Minute`.
   1. 「」を選択します **[!UICONTROL Set a timeout path]** チェックボックス。

   このタイムアウト設定を使用すると、チェックアウトを実行したが、このタイムアウト分岐で 1 分トリガー以内に注文が完了しない買い物客が発生します。 実際の実稼動環境では、これを 24 時間などの長い期間に設定します。

1. の下の左側のナビゲーション **[!UICONTROL ACTIONS]**、を追加します **[!UICONTROL Email]** タイムアウト分岐に対するアクション。 ジャーニーは次のようになります。

   ![Journey Optimizer Canvas](assets/ajo-canvas.png){width="700" zoomable="yes"}

### 放棄された買い物かごのメールの作成

放棄された買い物かごが検出されたときに送信される、放棄された買い物かごメールを作成します。

1. 上記で作成したジャーニーで、 **[!UICONTROL Email]** アイコンをキャンバスに表示します。

1. に従う [手順](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/personalization/personalization-use-cases/personalization-use-case-helper-functions.html#configure-email) Journey Optimizerガイドで、放棄された買い物かごのメールを作成する。

これで、Journey Optimizerで以下をリッスンするジャーニーができました `commerce.checkouts` からのイベント [!DNL Commerce] 一定期間経過後に送信されるストアおよび放棄された買い物かごメール。 次の節では、ジャーニーのテスト方法を説明します。

## 手順 5：チェックアウトイベントのリアルタイムトリガー

この節では、リアルタイムでイベントをテストします。

1. Journey Optimizerで、「テストモード」をオンにします。

   ![テストモードを有効にする](assets/ajo-enable-test.png){width="700" zoomable="yes"}

1. このジャーニーをリアルタイムでテストするには、別のブラウザータブを開き、 [!DNL Commerce] サンドボックス環境内の web サイト。

   1. 商品を買い物かごに追加します。
   1. チェックアウトページに移動します。
   1. チェックアウトページからメインページに戻るかタブを閉じて、買い物かごを放棄します。

      これで、ジャーニーがトリガーされます。 確認するには、Journey Optimizerでジャーニーを持つタブを開きます。 ユーザーが通過したパスを示す緑の矢印が表示されます。

1. メールのインボックスを確認します。
