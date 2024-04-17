---
title: '''[!DNL Product Recommendations] リリースノート'
description: の最新のリリース情報 [!DNL Product Recommendations] Adobe Commerceから
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
feature: Services, Recommendations, Release Notes
source-git-commit: c3940c399c0639fe53e23cea96b347c7827ecb42
workflow-type: tm+mt
source-wordcount: '1276'
ht-degree: 0%

---

# [!DNL Product Recommendations] リリースノート

リリースノートには、次の更新が含まれています [!DNL Product Recommendations] モジュール：

* [!DNL Product Recommendations] メタパッケージ： `magento/product-recommendations`
* でのページビルダーのサポート [!DNL Product Recommendations] （オプション）モジュール： `magento/module-page-builder-product-recommendations`
* の視覚的類似性推奨タイプのサポート [!DNL Product Recommendations] （オプション）モジュール： `magento/module-visual-product-recommendations`

現在のメジャーリリースバージョンに対するサポートが提供されます。 古いバージョンのリリースノートが参照用に提供されています。
リリースノートには次のものが含まれます。

![新規](../assets/new.svg) 新機能
![修正](../assets/fix.svg) 修正点および改善点
![バグ](../assets/bug.svg) 既知の問題

詳しくは、開発者向けドキュメントを参照してください [製品サポートについて学ぶ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

## ホステッド サービスの更新

これらのメモでは、バージョン管理されたリリースの外部で公開された更新や、ホストされるサービスの改善について説明します。

+++ホステッド サービスの更新

_2023 年 7 月 18 日（Pt）_

![新規](../assets/new.svg) [!DNL Product Recommendations] GraphQLが追加されました [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) クエリ。

_2023 年 4 月 25 日（Pt）_

![新規](../assets/new.svg) [!DNL Product Recommendations] お客様は次のメリットを享受できます [SaaS 価格インデックス作成](../price-index/price-indexing.md).

+++

## 現在のメジャーバージョン

### magento/product-recommendations の 6.0.1

_2024 年 3 月 19 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) PHP 8.3 のサポートを追加しました。

### 以前のバージョン

### magento/product-recommendations の 6.0.0

_2024 年 2 月 22 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) この [!DNL Catalog Sync Dashboard] 現在はです [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). この改善されたダッシュボードは、のデータストリームに関するインサイトを提供します [!DNL Product Recommendations], [!DNL Live Search]、および [!DNL Catalog Service].
![修正](../assets/fix.svg) のチェックアウトエラーが発生する問題を修正しました [!DNL Product Recommendations].

+++5.0.0 以前

### magento/product-recommendations の 5.0.1

_2023 年 9 月 15 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) をサポートする新しいモジュールを追加しました [Saas 価格インデクサー](../price-index/price-indexing.md).
![新規](../assets/new.svg) バンドルされた製品やギフトカードなど、より多くの製品タイプの書き出しをサポートする新しいデータエクスポートモジュールを追加しました。
![修正](../assets/fix.svg) 製品および価格フィードのテーブルサイズが大幅に縮小されました。 テーブル `catalog_data_exporter_products` および `catalog_data_exporter_product_prices` 大幅なサイズ削減が必要です。

#### 既知の制限事項

* この `websiteCode` アンダースコア（_）が含まれる値は誤って返されます。

### magento/product-recommendations の 5.0.0

_2023 年 3 月 20 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) 更新日 [!DNL Product Recommendations] Adobe Commerce 2.4.6 をサポートします。
![新規](../assets/new.svg) これはメジャーバージョンリリースです。 [編集](install-configure.md#update) ルート `composer.json` プロジェクトのファイルです。
![新規](../assets/new.svg) [!DNL Product Recommendations] 完全なサポートを追加 [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) Commerceの機能（以前はマルチソースインベントリ（MSI）と呼ばれていました）。 フルサポートを有効にするには、次の操作を行う必要があります [更新](install-configure.md#update) 依存関係モジュール `commerce-data-export` をバージョン 102.2.0 以降にアップグレードします。

### magento/product-recommendations の 4.0.1

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg) 以前は、 [!DNL Product Recommendations] は、表示通貨がデフォルト以外の通貨に切り替えられた場合にエラーを表示します。 通貨の切り替えが正しく機能するようになりました。

### magento/product-recommendations の 4.0.0

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) 追加済み [準備状況インジケーター](create.md) 各レコメンデーションタイプのトレーニング進行状況を視覚化するのに役立ちます。
![新規](../assets/new.svg) これはメジャーバージョンリリースです。 [編集](install-configure.md#update) ルート `composer.json` プロジェクトのファイルです。 このリリースでは、のインストールおよび設定時に 2 つの API キーも指定する必要があります [!DNL Product Recommendations]: [実稼動キーとサンドボックスキー](../landing/saas.md).

#### 既知の制限事項

* この `websiteCode` アンダースコア（_）が含まれる値は誤って返されます。

### magento/product-recommendations の 3.3.7

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) PHP 8.1 のサポートを追加
![新規](../assets/new.svg) 画像のサイズ変更が改善され、参照表示テンプレートでの画像のサイズ変更の一貫性が向上しました

### magento/product-recommendations の 3.3.6

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) 最適化 [!DNL Product Recommendations] 依存関係を明示的にリストすることによるメタパッケージ

### magento/product-recommendations の 3.3.5

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) 追加済み [B2B サポート](onboarding.md#b2bsupport) 。対象： [!DNL Product Recommendations]
![新規](../assets/new.svg) 新しいフィードをに追加しました [カタログデータを同期](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) コマンドラインを使用してCommerce サービスに移動する

### magento/product-recommendations の 3.3.3

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) 新規追加 [レコメンデーションタイプ](type.md)：コンバージョン（表示から買い物かごへ）、コンバージョン（表示から購入へ）、最近表示された項目。 以下の新しいレコメンデーションタイプは、 `magento/product-recommendations` モジュール 3.2.2 以降。
![修正](../assets/fix.svg) Fastly の web アプリケーションファイアウォール（WAF）が誤って cookie をブロックしていた問題を修正しました
![修正](../assets/fix.svg) デフォルト以外のストア表示に割り当てられた製品がに表示されない問題を修正しました _Recommendations製品プレビュー_ その特定のストア表示のレコメンデーションを作成する際のパネル
![修正](../assets/fix.svg) ページビルダーの特定のレコメンデーションユニット名でレコメンデーションユニットがストアフロントに表示されない問題を修正しました

### magento/product-recommendations の 3.3.2

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg) B2B サポートの欠落依存関係を修正

### magento/product-recommendations の 3.3.1

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) B2B 顧客グループ価格のサポートを追加しました。 の設定値 [価格フィルター](filters.md) レコメンデーションユニットで、ログインした B2B 顧客は、表示された製品の顧客グループ価格設定を確認します。

### magento/product-recommendations の 3.3.0

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) Adobeクライアントデータレイヤーのサポートが追加され、Adobe Commerceの機能とサービス全体で行動データの収集を標準化できるようになりました。 を参照してください。 [readme](https://github.com/adobe/commerce-events/blob/main/packages/storefront-events-collector/README.md) を参照してください。

### magento/product-recommendations の 3.2.6

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg) Javascript モーダルエラーを修正しました
![修正](../assets/fix.svg) Fastly の web アプリケーションファイアウォール（WAF）が誤って cookie をブロックしていた問題を修正しました

### magento/product-recommendations の 3.2.5

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) Magentoサービスの名前をに変更 [Commerce サービス](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) 管理での操作性の向上

### magento/product-recommendations の 3.2.4

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg) 製品属性のインデックス作成時に「設定可能な製品オプションデータを取得できません」エラーが修正されました

### magento/product-recommendations の 3.2.3

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg) カタログ同期中の「設定可能な製品オプションデータを取得できません」エラーを修正しました
![修正](../assets/fix.svg) 「URL にストアコードを追加」設定を有効にすると、ストアコードが正しく設定されない問題を修正しました
![修正](../assets/fix.svg) 管理パネルの設定変更の検出が改善され、これらの変更がカタログ同期データに反映されるようになりました

### magento/product-recommendations の 3.2.2

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) にを追加しました。 [レコメンデーション結果のプレビュー](create.md) 作成時。 モジュールを最新バージョンに更新する必要が生じる場合があります。
![新規](../assets/new.svg) にを追加しました。 [監視と管理](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) 管理者からのカタログ同期プロセス。
![新規](../assets/new.svg) 追加済み [フィルター](filters.md) を使用して、レコメンデーションに表示する製品を制御します。
![新規](../assets/new.svg) さんがを追加しました [視覚的類似性](type.md#visualsim) レコメンデーションタイプ。

### ページビルダー用 magento/module-page-builder-product-recommendations の 1.2.1

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) の 3.2.0 以降のバージョンがサポートされるようになりました。 `magento/product-recommendations` モジュール

### magento/product-recommendations の 3.1.0

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) にを追加しました。 [再同期](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) コマンドラインを使用した SaaS サービスへのカタログ。
![新規](../assets/new.svg) データベーステーブルのプレフィックスをサポートするようになりました
![修正](../assets/fix.svg) PHP 7.1 のサポートを削除

### magento/product-recommendations の 3.0.8

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg) モジュールを設定する前に、データ収集のためにイベントが送信され、無効なトラフィックが発生する問題を修正しました

### magento/product-recommendations の 3.0.6

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) **（ベータ版）** 新規ののサポートを含む [視覚的類似性](type.md#visualsim) レコメンデーションタイプ。

### magento/module-visual-product-recommendations 1.0.0

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) **（ベータ版）** [視覚的類似性](type.md#visualsim). （を使用） _視覚的類似性_ レコメンデーションタイプ：レコメンデーションユニットを製品の詳細ページにデプロイできます。このページには、表示する製品に視覚的に似た製品が表示されます。

### magento/product-recommendations の 3.0.5

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg) カタログの書き出し中に発生する可能性のある「製品オプションデータを取得できません」エラーを修正しました。
![修正](../assets/fix.svg) の通貨記号 _収益_ の列 _[!DNL Product Recommendations]_ダッシュボードに、設定された基本通貨が正しく反映されるようになりました。

### magento/product-recommendations の 3.0.4

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg) Adobe Commerce 2.4.0 がサポートされるようになりました。

### magento/product-recommendations の 3.0.3

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg) ストアフロントテンプレートでのシンボル実装の改善

### ページビルダー用 magento/module-page-builder-product-recommendations の 1.0.4

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) ページビルダーコンテンツタイプの編集時に製品レコメンデーション名を追加しました

### 3.0.2 magento/product-recommendations

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) ページビルダーでレコメンデーション単位を選択する際のグリッドにステータス列を追加しました
![修正](../assets/fix.svg) 製品および画像 URL の誤った http/https プロトコルに関する問題を修正しました

### magento/product-recommendations の 3.0.1

[!BADGE サポート]{type=Informative tooltip="サポート"}

これはメジャーバージョンリリースです。 [編集](install-configure.md#update) プロジェクトのルート composer.json ファイル。

![新規](../assets/new.svg) 取得 [!DNL Product Recommendations] 代替 SaaS データ スペースから。 以下を使用できます。 [!DNL Product Recommendations] 実稼動以外の他の環境の製品環境で計算します。 [SaaS データ スペースの切り替え](settings.md) この機能について詳しく説明します。

![修正](../assets/fix.svg) uBlock オリジンを使用する買い物客のチェックアウトが禁止される問題を修正しました
![修正](../assets/fix.svg) 不要な買い物かごへの追加イベントを送信する問題を修正しました

### ページビルダー用 magento/module-page-builder-product-recommendations の 1.0.3

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) ページビルダーのサポート。 ページビルダーの統合を使用すると、ページビルダーが作成したコンテンツの任意の場所にレコメンデーションユニットを正確かつ詳細に配置できます。 また、見出しとレコメンデーションユニット自体のスタイルを設定することもできます。 に移動 [ページビルダー](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations) を参照してください。

### magento/product-recommendations の 2.0.0

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) 一般公開リリース

+++

## マニュアル

について詳しくは、 [!DNL Product Recommendations] および [!DNL Product Recommendations] 開発：

* [ユーザーガイド](overview.md)
* [開発者向けドキュメント](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview)
