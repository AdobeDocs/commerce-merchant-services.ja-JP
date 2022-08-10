---
title: ストアフルフィルメントサービスのオンボーディングの概要
description: '''[!DNL Live Search] オンボーディングフロー、システム要件、境界、制限事項について説明します。'''
role: User, Admin
level: Intermediate
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
source-git-commit: 1fb22b4644d41ea5c60aead3fe2c455dfa3382f8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# ストアフルフィルメントのオンボーディングの概要

の基本を学ぶ [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] 次のコンポーネントを設定、設定および有効化する。

- **Store Fulfilment 拡張機能** — このサードパーティの拡張機能をAdobe Commerceインスタンスにインストールして設定します。 インストール後、管理者からサポートするストアフルフィルメントソリューションを設定および管理できます [!DNL buys online, pickup in store] (BOPIS) シナリオが Commerce ストアフロントに表示されます。

   ![[!DNL Store Fulfillment Service] 管理ビューの設定](assets/store-fulfillment-admin-home.png)

- **受渡勘定の保存** — 有効化プロセス中に、アカウントマネージャがストアフルフィルメントアカウントを作成し、アカウント情報と認証情報を提供します。 これらの資格情報は、Adobe Commerceとストアフルフィルメントソリューション間の接続を有効にするために必要です。

- **ストアアシストアプリ** — ストアをエンドツーエンドのストアフルフィルメントワークフローと関連付けて、モバイルデバイスからの BOPIS 注文を管理します。 Store Associates は Walmart の [!DNL Store Assist] (iOSおよび Android™デバイス用 ) アプリのオンボーディングプロセスは、Walmart Commerce Technologies Client Center によって別のプロセスとして管理されます。 しかし、 [一部のアプリ設定](user-setup.md) は、Adobe Commerce Admin から入力されます。

   | Store Assist App — はじめに表示 | Store Assist App — モジュールビュー |
   |-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
   | ![[!DNL Store Assist App Getting Started] モバイルデバイスで表示](assets/store-assist-get-started-small.png) | ![[!DNL Store Assist App Orders view] モバイルデバイス上](assets/store-assist-orders-small.png) |

## プロビジョニング手順

- **新規登録[!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies]** — 次のサインアップフォームに入力します： [business.adobe.com](https://business.adobe.com/resources/store-fulfillment.html)または、Adobe Commerceのアカウントマネージャーにお問い合わせください。

- **ストアフルフィルメントのプロビジョニングリクエストを開始します** — 担当のアカウントマネージャーから提供された取り込みフォームに入力し、プロビジョニングプロセスの開始に必要な情報を入力します。

- **ストアフルフィルメントアカウントの資格情報を取得** — ストアフルフィルメントアカウントを作成したら、ストアフルフィルメントソリューションをAdobe Commerceと統合するために必要な資格情報を受け取ります。

- **[ソースコードをダウンロードして、 [!DNL Store Fulfillment] 拡張](install.md)**

## オンボーディング手順

1. [Adobe Commerceの Store Fulfilment 拡張機能のインストール](install.md).

1. 管理者から、 [解決策を有効にする](enable-general.md).

1. [Adobe Commerce管理者からの Store Fulfilment 拡張機能の設定](service-config-settings-overview.md).

1. [接続 [!DNL Store Fulfillment] 指定されたストアフルフィルメント資格情報を使用したサービス](connect-set-up-service.md).

1. [Store Assist アプリのユーザーとロールの作成](user-setup.md).

1. [ウォルマートの [!DNL Store Assist] を目的のデバイスに追加します。 このアプリは、Appleアプリ (iOS) とGoogle Play(Android™) の両方で使用できます](app-setup.md) ストア。

のインストール、設定、オンボーディングの完了、およびへのアクセス権の取得が完了したら、 [!DNL Store Assist] アプリで、以下を実行できます。 [オーダーとテストの作成を開始](test-and-deploy.md).
