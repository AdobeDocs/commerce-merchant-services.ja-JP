---
title: ヘッドレス
description: の統合方法を説明します。 [!DNL Product Recommendations] ヘッドレスな店の前に
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: 521ea4fc2cce809fc12d3958e37089f3e34e1068
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# ヘッドレス

統合可能な [!DNL Product Recommendations] 次のいずれかを使ってヘッドレスな店頭で [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) または React や Vue JS などのカスタムフロントエンドテクノロジー。

カスタムおよびヘッドレスインテグレーターは、推奨される実装として、これらの Luma とPWAの手順を参照してください。 ヘッドレスソリューションに Product Recommendationsを実装するには、様々な方法があります。このドキュメントでは、すべてのシナリオについて説明するわけではありません。 インテグレーターは、実装のイベンティング、デザイン、テストについて説明する必要があります。

[!DNL Product Recommendations] 必須 [行動データとカタログデータ](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html) を操作します。 ヘッドレス実装では、カタログデータ同期プロセスは変わりませんが、行動データ収集には変更が必要です。

>[!NOTE]
>
>ヘッドレスインスタンスは、製品のRecommendationsダッシュボードを強化するために、イベンティングを実装する必要があります。

統合するには [!DNL Product Recommendations] ヘッドレスストアフロントでは、次の操作を実行する必要があります。

1. 行動データをAdobe Senseiに送信して、製品レコメンデーションの結果を分析および計算します。 また、追加データを送信して、製品のレコメンデーションを有効にすることもできます [指標レポート](workspace.md).

1. 製品のレコメンデーション結果を取得し、ページでその結果をレンダリングします。

次のワークフローで説明するように、使用可能な SDK を使用して、これらの両方のアクションを実行できます。

1. [インストール](install-configure.md) の [!DNL Product Recommendations] モジュール。

1. をインストールして使用する [Adobe Commerce Storefront Event SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) 撃つ [行動イベント](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

   返す必要のある最小イベント数 [!DNL Product Recommendations] 結果：

   | イベント | カテゴリ |
   |--- | ---|
   | `view` | 製品 |
   | `add-to-cart` | 製品 |
   | `place-order` | checkout |

   有効にするには [指標レポート](workspace.md)に設定する場合は、次の追加のイベントが必要です。

   | イベント | カテゴリ |
   |--- | ---|
   | `impression-render` | recommendation-unit |
   | `view` | recommendation-unit |
   | `rec-click` | recommendation-unit |
   | `rec-add-to-cart-click` | recommendation-unit（recommendations テンプレートに「買い物かごに追加」ボタンが存在する場合） |

1. イベントが発生したら、 [Adobe Commerce Storefront イベントコレクター](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) イベントを処理してAdobe Senseiに送信する。

1. 行動データを収集した後、 [作成](create.md) [!DNL Product Recommendations] 」と入力します。

1. 以下を使用します。 [Recommendations SDK](https://developer.adobe.com/commerce/services/product-recommendations/) ストアフロントでレコメンデーションユニットを取得します。 SDK は、ページ上でレコメンデーション単位をレンダリングするために必要な製品データを返します。
