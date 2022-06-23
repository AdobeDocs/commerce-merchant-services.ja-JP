---
title: アプリ設定
description: 設定 [!DNL Store Assist] エンドツーエンドの店舗フルフィルメントワークフローとプロセスを管理するアプリは、オンラインで購入し、店舗注文で受け取ります。
role: User, Admin
level: Intermediate
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 421c90f4c8bd687216cd48c72f30301a32115522
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---

# アプリ設定

Store Assist は、Walmart Commerce Technologies を活用したフルフィルメント・ア・サービス (FaaS) プラットフォーム・アプリです。 デスクトップアプリケーションは、ストア内フルフィルメント機能を提供し、 [!DNL buy online], [!DNL pick up in store] (BOPIS) 注文。  店舗アシストを使用すると、店舗関連者は、顧客が注文した品目を確認し、正しい品目を迅速に選択し、顧客に対する店舗内またはキューブサイドのピックアップ配信の履行注文を設定できます。

Store Assist アプリは、注文の詳細から時間まで、すべての注文および顧客情報を受け取り、モバイルデバイスを通じて、関連付けをオンラインで保存するためのデータを使用できるようにします。 アプリにはが含まれます [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff]、および [!UICONTROL Orders] Store Associates が次のような達成活動に役立つモジュールです。

- 注文の配信日時を割り当てます。
- 受注の受け取り用に顧客が到着したら、顧客から通知を受け取ります。
- 顧客への引き渡しのステージ注文。
- 割り当てられた店舗の場所にあるすべての注文のステータスを追跡します。

>[!NOTE]
>
>詳しくは、 [Store Assist フルフィルメントワークフロー](store-assist-modules.md) を参照して、Store Assist アプリの詳細を確認してください。

## Store Assist アプリの設定

Store Assist アプリには、次の 2 種類の設定が必要です。

- Adobe Commerce管理者の設定 [Adobe Commerce管理システム設定から、ユーザーアカウント、ユーザーの役割、およびリソース権限を管理します。](user-setup.md).

- Store Assist アプリインターフェイスおよび以下のようなその他の設定をカスタマイズするためのフロントエンド設定

   - **ストアアシストアプリのブランディング** — 会社のロゴと色を使用して、アプリのユーザーインターフェイスをカスタマイズします。

   - **デフォルトの手順を更新** — ピック、ステージ、ハンドオフ、注文モジュールの Store Assist インターフェイスの指示をカスタマイズして、会社のポリシーと手順に準拠し、Store Associates にフルフィルメントワークフローの各ステップを案内します。

   - **ローカリゼーション** — アプリで使用できる言語を選択します。 日付と時刻の形式を選択し、デフォルトの測定単位とデフォルトの通貨を選択します。

   - **無操作時間** — アプリケーションが非アクティブである必要がある時間を指定します。この時間を過ぎるとログアウトされます。

   - **ストアからのキャンセル** — オーダーをストアからキャンセルできるかどうか、およびキャンセル権限を持つロールを指定します

   - **注文のクリーンアップウィンドウ** — 選択した受注が再在庫されるまでにステージングに残る予定ピックアップ時間（3 日間など）を指定します。

   - アプリ内の指示（選択、ステージング、ハンドオフ）をすべてカスタマイズします。

   - **通知の選択** — 顧客が注文した後にピッキングプロセスを開始するためにプッシュ通知を送信するかどうかを指定します。

   - **チェックイン通知** — 注文のチェックインプロセス中に、チェックイン後に、顧客の待機時間が指定した期間を超えた後にプッシュ通知を送信するかどうかを指定します。 または、通知を無効にします。

   - **手渡しプロセス**- Store Associate が顧客に注文を行う場合（例えば、顧客の署名が必要な場合や、顧客 ID の確認を要求するメッセージを表示する場合）は、オプションのプロセスを有効にします。

   - **ハンドオフ時に項目却下を有効にする** — 注文の受け渡し中に、顧客が注文項目を返却またはキャンセルできるようにします。
   Walmart Commerce Technologies Client Services チームと協力して、Store Assist App のフロントエンド設定を完了します。

## アプリのダウンロードとインストール

Store Assist アプリの設定が完了すると、Store Associates は、モバイルデバイスから Store Assist アプリをダウンロード、インストールし、ログインできます。

- モバイルデバイスが [ハードウェアとソフトウェアの要件](solution-requirements.md#store-assist-app-requirements) を参照してください。

- Store Assist アプリをからダウンロードします。 [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id16092815390){target=&quot;_blank&quot;} または [Google Playストア](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target=&quot;_blank&quot;}。

- Store Associates のログインには次の情報が必要です。

   - Store Assist アカウントに関連付けられた会社名

   - Store Assist アカウント資格情報（アカウントのユーザー名とパスワードの資格情報）。
   Adobe Commerce管理者は、ユーザーアカウントを作成し、ストアの場所を持つ Store Assist App ユーザーアカウントに対する権限を設定できます [店内ピックアップ](merchant-store-configuration.md#pickup-location-configuration) が管理ストア設定で有効になっている。
