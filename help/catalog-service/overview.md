---
title: '"[!DNL Catalog Service]"'
description: '"[!DNL Catalog Service] for Adobe Commerceは、ネイティブのAdobe Commerce GraphQL クエリよりも、製品表示ページと製品リストページのコンテンツをよりすばやく取得する方法を提供します。」'
source-git-commit: eb2242ac99cfaef4ed75936a1b5cc800cc451c83
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# [!DNL Catalog Service] Adobe Commerce

{{catalog-service-beta}}

この [!DNL Catalog Service] Adobe Commerce拡張機能には、次のような豊富なビューモデル（読み取り専用）カタログデータが用意されており、製品関連のストアフロントエクスペリエンスをすばやく完全にレンダリングできます。

* 製品の詳細ページ
* 製品リストページとカテゴリページ
* 検索結果ページ
* 製品カルーセル
* 製品比較ページ
* 買い物かご、注文、ウィッシュリストのページなど、製品データをレンダリングするその他のページ

この [!DNL Catalog Service] uses [GraphQL](https://graphql.org/) 製品データをリクエストして受け取る。 GraphQL は、フロントエンドクライアントがAdobe Commerceなどのバックエンドで定義されたアプリケーションプログラミングインターフェイス (API) との通信に使用するクエリ言語です。 GraphQL は軽量で、システムインテグレーターが各応答の内容と順序を指定できるので、一般的な通信方法です。

Adobe Commerceには 2 つの GraphQL システムがあります。 コア GraphQL システムは、様々なクエリ（読み取り操作）と変異（書き込み操作）を提供し、買い物客が製品、顧客アカウント、買い物かご、チェックアウトなど、様々な種類のページを操作できるようにします。 ただし、製品情報を返すクエリは、速度に対して最適化されていません。 サービス GraphQL システムは、製品と関連情報に対してのみクエリを実行できます。 これらのクエリは、類似のコアクエリよりもパフォーマンスが高くなります。

## アーキテクチャ

次の図に、2 つの GraphQL システムを示します。

![カタログのアーキテクチャ図](assets/catalog-service-architecture.png)

コア GraphQL システムでは、PWAが Commerce アプリケーションにリクエストを送信し、各リクエストを受信して処理し、場合によっては複数のサブシステムを介してリクエストを送信した後、ストアフロントに応答を返します。 このラウンドトリップは、ページ読み込み時間が遅くなり、コンバージョン率が低下する可能性があります。

[!DNL Catalog Service] は別の GraphQL ゲートウェイにクエリを送信します。 サービスは、製品の詳細と関連情報（製品の属性、バリアント、価格、カテゴリなど）を含む別のデータベースにアクセスします。 サービスは、インデックス化を通じて、データベースをAdobe Commerceと同期させます。
このサービスはアプリケーションとの直接通信をバイパスするので、リクエストと応答サイクルの待ち時間を短縮できます。

>[!NOTE]
>
>ゲートウェイは、 [!DNL Live Search] および [!DNL Product Recommendations]. このリリースでは、 [!DNL Catalog Service] 両方の製品の有効なライセンスキーがある場合、同じエンドポイントからのライブ検索クエリ。 ただし、2 つの製品からのクエリは、現在、応答データを共有していません。

コアとサービスの GraphQL システムは、互いに直接通信しません。 各システムには異なる URL からアクセスし、呼び出しには異なるヘッダー情報が必要です。 2 つの GraphQL システムは、一緒に使用するように設計されています。 この [!DNL Catalog Service] GraphQL システムは、製品ストアフロントをより迅速に体験できるように、コアシステムを強化します。

オプションでを実装できます。 [Adobe Developer App Builder の API メッシュ](https://developer.adobe.com/graphql-mesh-gateway/) Adobe Developerを使用して、2 つのAdobe Commerce GraphQL システムを、プライベートおよびサードパーティの API や他のソフトウェアインターフェイスと統合する場合。 メッシュを設定して、各エンドポイントにルーティングされた呼び出しに、ヘッダーに正しい認証情報が含まれるようにすることができます。

## 実装

インストールプロセスでは、 [Commerce Services コネクタ](../landing/saas.md). それが完了したら、次の手順では、システムインテグレーターがストアフロントコードを更新し、 [!DNL Catalog Service] クエリ。 すべて [!DNL Catalog Service] クエリは GraphQL ゲートウェイにルーティングされます。 URL は、オンボーディングプロセス中に提供されます。

[Adobe Commerce Devdocs](https://devdocs.magento.com/catalog-service/index.html) コアと [!DNL Catalog Service] クエリ。 各クエリの参照情報も含まれます。