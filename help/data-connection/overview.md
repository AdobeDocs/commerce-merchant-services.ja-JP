---
title: ガイドの概要
description: を使用してAdobe CommerceデータをAdobe Experience Platformに統合する方法を説明します。 [!DNL Data Connection] 拡張子。
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: af54529ad037dc99dbc07cf1a6ac270d17f16870
workflow-type: tm+mt
source-wordcount: '1732'
ht-degree: 0%

---

# [!DNL Data Connection] はじめに

>[!IMPORTANT]
>
>Experience Platformコネクタの名前は「 [!DNL Data Connection].

The [!DNL Data Connection] 拡張機能は、Adobe Commerce Web インスタンスをAdobe Experience Platformおよび Edge ネットワークに接続します。 方法を学ぶ [統合する](./mobile-sdk-epc.md) コマースを使用するAdobe Experience Platform Mobile SDK

コマースストアには豊富なデータが含まれています。 買い物客がサイトで商品を閲覧、表示、最終的に購入する方法に関する情報が、よりパーソナライズされた買い物体験を作成する機会を明らかにします。 このデータは、買い物かごの価格ルールや動的ブロックなどのネイティブのコマース機能に通知できますが、データはコマースインスタンス内に配置されたままになります。

Adobe Experience Platformは、コマースストアのデータにハイドレートされた場合に、Edge ネットワークを通じてそのデータを他のAdobeDX 製品に配布し、買い物客の購入行動に対するインサイトを解き放つことができるテクノロジーのスイートを提供します。 これらの深いインサイトを使用して、すべてのチャネルにわたって、よりパーソナライズされたショッピングエクスペリエンスを作成できます。

次の図は、Commerce データがストアから他のAdobeDX 製品にどのように送られるかを示しています。

![データがExperience Platformエッジに送られる仕組み](assets/commerce-edge.png)

上の画像では、行動、バックオフィス、顧客プロファイルのデータが、SDK、API、ソースコネクタを使用してExperience Platformエッジに送信されます。 拡張機能でデータ共有の複雑さが処理されるので、これらの要素の動作を完全に理解する必要はありません。 イベントデータが最前線にある場合は、そのデータを他のイベントアプリケーションに取り込むことができますExperience Platform。 例：

| アプリ | 目的 | 使用例 |
|---|---|---|
| [Adobe [!DNL Real-Time CDP]](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html) | プロファイル管理とセグメント化サービス | **購入履歴のセグメント化**：商人は、特定の期間（月別、四半期別、年別など）に基づいて品目を購入した顧客を識別できます。 次に、マーチャントは顧客に対してセグメントを作成し、プロモーション、キャンペーン、 _漏斗の上部_ サブスクリプションサービスのリードのデータ。<br> **カテゴリベースのセグメント化**：マーチャントは、購入された製品のカテゴリを確認できます。<br> **オファーベースのセグメント化**：商人は、一貫して商品を返す顧客を特定できます。 オファーや割引がよりインテリジェントになりました。 例えば、常に商品を返品する顧客の場合は、送料無料を削除できます。<br> **類似のターゲティング**: A _類似オーディエンス_ は、既存の顧客と同様の特性を共有するので、ビジネスに興味を持つ可能性が高い新規顧客にリーチするためのプロモーションに関して、マーチャントがおこなう手法です。 類似セグメントは、行動データとトランザクションデータに基づいて作成できます。<br> **顧客傾向**：顧客の行動の変化は、トランザクションデータから作成できる顧客プロファイルの深さの結果として識別できます。 製品の返却数や製品の設定など、計算により多くのデータが流れ込むので、傾向スコアの信頼性は高くなります。<br> **クロス販売**：マーチャントは、コマースで取得された詳細な情報から、強力なクロス販売およびアップ販売の機会を識別できます。 |
| [顧客 [!DNL Journey Analytics]](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html) | 完全なコマースジャーニーのディープ分析 | **季節的な傾向**：商人は季節の傾向を特定でき、特定の製品に対する需要の定期的な変化に備えるのに役立ちます。 また、商人は、何年にもわたる製品の全体的な人気の変化を特定できます。<br> **コンバージョン分析**：商品がいつ購入されたかを把握し、ストアフロントのインプレッションイベントにアクセスすることで、マーチャントは顧客の豊富なプロファイルを生成して、コンバージョン分析を実行できます。 |
| [Adobe [!DNL Analytics]](https://experienceleague.adobe.com/docs/analytics/analyze/admin-overview/analytics-overview.html) | 顧客の行動とキャンペーンのパフォーマンスに関する深い分析 | **注文の返品**：マーチャントは、再商品のパターンを持つ顧客や大規模な顧客セグメントを識別できます。 これにより、商人は顧客ベースの行動がどのように表示されるかを把握しながら、商取引戦略を改善できます。<br> **注文の住所**：商人は、配送先住所に基づいて、注文が顧客自身によっておこなわれているか、別の個人またはエンティティの注文であるかを把握できます。<br> **シーズナリティの傾向**：商人は季節の傾向を特定でき、特定の製品に対する需要の定期的な変化に備えるのに役立ちます。 また、商人は、何年にもわたる製品の全体的な人気の変化を特定できます。<br> **コンバージョン分析**：商品がいつ購入されたかを把握し、ストアフロントのインプレッションイベントにアクセスすることで、マーチャントは顧客の豊富なプロファイルを生成して、コンバージョン分析を実行できます。 **注意** Adobe Analyticsは、行動 (storefront) イベントデータのみをサポートします。 Adobe Analyticsは、トランザクション (backoffice) イベントデータをサポートしていません。 |
| [Adobe [!DNL Journey Optimizer]](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) | チャネル間のキャンペーンオーケストレーション | **行動ベースのジャーニー**：マーチャントは、2 年前に携帯電話を購入した顧客をターゲットにして、新しいモデルの購入を提案できます。 マーチャントは、顧客に合わせてパーソナライズされたキャンペーンやプロモーションを作成し、E メールや SMS 機能を使用して連絡を取ることができます。 また、マーチャントは、履歴的な順序と行動データを使用して、トレンドを識別できます。 例えば、過去に特定の設定を持つ品目を購入し、現在同じ製品を再度購入しようとしているお客様は、同じ製品設定を表示し、アクセスできるようにすることで、購入ジャーニーを強化できます。<br> **パーソナライズ**：顧客プロファイル情報へのアクセス権を持つ [!DNL Journey Optimizer] では、パーソナライズされたジャーニーを解放し、マーチャントが複数の異なるチャネルで顧客にリーチできるようにします。<br> **新しいプロファイルが作成されました**：ようこそメールやプロモーション活動が、新しい顧客をショッピングジャーニーに促し、影響を与える可能性があります。<br> **削除されたプロファイル**：商人は、アカウントを閉じた顧客に対するプロモーション E メールの送信を停止できます。 また、損失した顧客を取り戻すために、マーチャントがキャンペーンを構築することもできます。 |

## Experience Platformデータを Commerce に取り込む

を使用してコマースデータをExperience Platformに送信する [!DNL Data Connection] 拡張機能は、コマースのデータ共有機能の 1 つです。 もう一方の側（オプションの拡張）は、と呼ばれます。 [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html). この拡張機能を使用すると、Real-Time CDPでオーディエンスを構築し、それらのオーディエンスをコマースストアにデプロイして、買い物かごの価格ルール、関連する製品ルール（ベータ版）、動的ブロックに通知できます。

コマースストアからExperience Platformに、またAudience Activation拡張機能を通じて戻るデータのフローは、大まかに見ると、次のようになります。

![[!DNL Data Connection] 流れ](assets/data-connection.png)

コマースからExperience Platformへの接続と、Experience Platformからコマースへの接続を設定した後も、データは流れ続けます。 アップグレードで必要な場合を除き、再接続する必要はありません。

## 概念

これら 2 つのシステム間でデータを共有するには、いくつかの概念を理解しておく必要があります。

* **データ** -Experience Platformと共有されるデータは、ストアフロントのブラウザーイベント、サーバーのバックオフィスイベント、プロファイルレコードデータから収集されるデータです。 ストアフロントイベントは、サイトでの買い物客のインタラクションからキャプチャされ、次のようなイベントが含まれます。 [`addToCart`](events.md#addtocart), [`pageView`](events.md#pageview), [`createAccount`](events.md#createaccount), [`editAccount`](events.md#editaccount), [`startCheckout`](events.md#startcheckout), [`completeCheckout`](events.md#completecheckout), [`signIn`](events.md#signin), [`signOut`](events.md#signout)など。 詳しくは、 [storefront イベント](events.md#storefront-events) ストアフロントイベントの完全なリストを参照してください。 サーバー側またはバックオフィスのイベントには、以下が含まれます。 [注文ステータス](events-backoffice.md#order-status) 情報： [`orderPlaced`](events-backoffice.md#orderplaced), [`orderReturned`](events-backoffice.md#orderitemreturncompleted), [`orderShipped`](events-backoffice.md#ordershipmentcompleted), [`orderCancelled`](events-backoffice.md#ordercancelled)など。 詳しくは、 [バックオフィスイベント](events-backoffice.md) バックオフィスイベントの完全なリストを参照してください。 プロファイルレコードデータには、新しいプロファイルが作成、更新または削除されたときの情報が含まれます。 詳しくは、 [プロファイルレコードデータ](events-profilerecord.md) を参照してください。

* **Experience Platformと Edge ネットワーク**  — ほとんどのAdobeDX 製品の Data Warehouse。 その後、Experience Platformに送信されたデータは、Edge Network を通じてAdobeDX 製品にExperience Platformされます。 例えば、Journey Optimizerを起動し、特定のコマースイベントデータをエッジから取得して、Journey Optimizerで放棄された買い物かごの電子メールを作成できます。 Journey Optimizerは、コマースストアに放棄された買い物かごがある場合に、その電子メールを送信できます。 詳しくは、 [Experience Platformと Edge ネットワーク](https://experienceleague.adobe.com/docs/platform-learn/data-collection/web-sdk/overview.html).

* **スキーマ**  — スキーマは、送信されるデータの構造を表します。 Experience Platformがコマースデータを取り込む前に、データの構造を記述するスキーマを作成し、各フィールドに含めることができるデータの種類に制約を与える必要があります。 スキーマは、基本クラスと 0 個以上のスキーマフィールドグループで構成されます。 スキーマは XDM 構造を使用します。この構造は、すべてのAdobeDX 製品が読み取ることができます。 したがって、データをExperience Platformに送信する際には、すべての DX 製品でデータが確実に認識されるようにすることができます。 詳細情報： [スキーマ](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html).

* **データセット**  — データのコレクションのストレージと管理の構成。通常、スキーマ（列）とフィールド（行）を含むテーブルです。 データセットには、保存するデータの様々な側面を記述したメタデータも含まれます。 Adobe Experience Platformに正常に取り込まれたすべてのデータは、データセット内に含まれています。 詳細情報： [データセット](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html).

* **Datastream** - Adobe Experience Platformから他のAdobeDX 製品にデータを送信できる ID。 この ID は、特定のAdobe Commerceインスタンス内の特定の Web サイトに関連付ける必要があります。 このデータストリームを作成する場合は、上で作成した XDM スキーマを指定します。 詳細情報： [datastreams](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html).

## サポートされるアーキテクチャ

The [!DNL Data Connection] 拡張機能は、次のアーキテクチャで使用できます。

* PHP/Luma
* [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/)
* [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html)

## 前提条件

次の手順で [!DNL Data Connection] 拡張機能には、以下が必要です。

* Adobe Commerce 2.4.4 以降
* Adobe IDと組織 ID
* [Adobeクライアントデータレイヤー (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html)：ストアフロントイベントデータの収集に必要です。
* 他のAdobeDX 製品の使用権限

## オンボーディング手順

高いレベルでは、 [!DNL Data Connection] 拡張機能には、次の手順が含まれます。

1. [インストール](install.md) の [!DNL Data Connection] 拡張子。
1. [ログイン](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) をAdobeアカウントに追加し、 [確認するビュー](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) 組織 ID。 組織 ID は、プロビジョニングされた組織の会社に関連付けられたExperience CloudID です。 この ID は 24 文字の英数字から成る文字列で、その後にが続きます（必須） `@AdobeOrg`.
1. 次の条件を満たしていることを確認します。 [Experience Platformでのデータ収集の権限](https://experienceleague.adobe.com/docs/experience-platform/collection/permissions.html).
1. 以下を確認します。 [データのタイプ](data-ingestion.md) 収集して送信できます。
1. を作成または更新します。 [時系列イベントスキーマ](update-xdm.md) または [プロファイルレコードデータスキーマ](profile-data.md) コマース固有のフィールドグループを持つ。
1. [データセットの作成](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 作成または更新したスキーマに基づいて このデータセットには、Experience PlatformEdge に送信された Commerce データが含まれています。
1. [データストリームの作成](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) をクリックし、コマース固有のフィールドグループを含む XDM スキーマを選択します。
1. [Commerce Services に接続](../landing/saas.md).
1. [Adobe Experience Platformに接続](connect-data.md).

このガイドの残りの部分では、これらのすべての手順を詳しく説明し、コマースストアでAdobeDX 製品を利用する際に最適な方法を習得して利用を開始できるようにします。

>[!NOTE]
>
>モバイル開発者の場合は、以下をおこなう方法を学習します。 [統合する](./mobile-sdk-epc.md) コマースを使用するAdobe Experience Platform Mobile SDK

## 対象ユーザ

このガイドは、顧客がショッピングエクスペリエンスを強化するために、コマースストアをエンリッチメントし、パーソナライズするAdobe Commerceの商人を対象にしています。

## サポート

このガイドに記載されていない情報や質問がある場合は、次のリソースを使用してください。

* [ヘルプセンター](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
* [サポートチケット](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"} — 追加のヘルプを受け取るには、チケットを送信します。
