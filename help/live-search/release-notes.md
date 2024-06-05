---
title: “[!DNL Live Search] リリースノート」
description: 「の最新のリリース情報 [!DNL Live Search] Adobe Commerceから」
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
feature: Services, Search, Release Notes
source-git-commit: fe261bfaf5a64c9501bc5523d29f9b6a9fc1a6a2
workflow-type: tm+mt
source-wordcount: '1966'
ht-degree: 0%

---

# [!DNL Live Search] リリースノート

これらのリリースノートでは、の最新バージョンについて説明します [!DNL Live Search].
現在のメジャーリリースバージョンに対するサポートが提供されます。 古いバージョンのリリースノートが参照用に提供されています。
次のような更新があります。

![新規](../assets/new.svg) 新機能
![修正](../assets/fix.svg) 修正点および改善点
![バグ](../assets/bug.svg) 既知の問題

## ホステッド サービスの更新

これらのメモでは、バージョン管理されたリリースの外部で公開された更新や、ホストされるサービスの改善について説明します。

_2024 年 2 月 13 日（Pt）_

![新規](../assets/new.svg) [!DNL Live Search] では、のデフォルトルールの設定をサポートするようになりました [マーチャンダイジングを検索](rules.md).

_2023 年 10 月 12 日（Pt）_

![新規](../assets/new.svg) Commerce管理者は、のインデックスの言語を指定できるようになりました [!DNL Live Search]. 参照： [設定](settings.md).
![修正](../assets/fix.svg) 「検索ルール」タブの名前は、「マーチャンダイジングを検索」に変更されました。

_2023 年 6 月 13 日（Pt）_

![修正](../assets/fix.svg) 引用符やアポストロフィなどの一部の文字がランキングの問題の原因となっていた問題を修正しました。 インデックス再作成を行うと、これらの問題は解決します。

_2023 年 4 月 25 日（Pt）_

![新規](../assets/new.svg) [!DNL Live Search] お客様は新しい [SaaS 価格インデクサー](../price-index/price-indexing.md).

### PLP ウィジェット

_2024 年 5 月 31 日（Pt）_

![新規](../assets/new.svg) PLP ウィジェットのバージョン 2.0.0 がリリースされ、次の機能がサポートされるようになりました。

- 「買い物かごに追加」ボタン – シンプルな製品でのみ使用できます。
- 製品ごとに複数の画像 – 設定可能な製品に対して別の色を選択すると、画像が変化する場合があります。

_2023 年 10 月 27 日（Pt）_

![新規](../assets/new.svg) この [!DNL Live Search] PLP ウィジェットがカラースウォッチをサポートするようになりました。


## [!DNL Live Search] 4.2.0 {#420}

_2024 年 5 月 31 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) PLP ウィジェット バージョン 2.0.0 を使用するように Live Search 拡張機能を更新しました。

## [!DNL Live Search] 4.1.2 {#412}

_2024 年 5 月 16 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

### 更新

![修正](../assets/fix.svg) を修正 [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering-by-categories) に基づいて正しくフィルタリングするためのGraphQL クエリ `categoryPath` および `categoryList` カテゴリの場合。

## [!DNL Live Search] 4.1.1 {#411}

_2024 年 3 月 19 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

### 新機能

![新規](../assets/new.svg) ポーランド語の言語サポートを追加しました。
![新規](../assets/new.svg) [!DNL Live Search] Adobe Commerce 2.4.4 を実行するインストールで PHP 8.3 がサポートされるようになりました。

## [!DNL Live Search] 4.1.0 {#410}

_2024 年 2 月 22 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

### 新機能

![新規](../assets/new.svg) この [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) が利用可能になりました。 この改善されたダッシュボードは、のデータストリームに関するインサイトを提供します [!DNL Product Recommendations], [!DNL Live Search]、および [!DNL Catalog Service].

### 更新

![修正](../assets/fix.svg) デフォルト以外のストア表示で、ゲストユーザーが買い物かごに製品を追加した際にエラーが発生する問題を修正しました。
![修正](../assets/fix.svg) ロケール設定に関係なく、検索ポップオーバーに常に通貨記号が価格値の前に表示される問題を修正しました。
![修正](../assets/fix.svg) インストール時の互換性の問題を修正するために、無効なコアプラグインに対する不要なタイプ定義を削除しました。

## [!DNL Live Search] 4.0.0 {#400}

_2023 年 11 月 13 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

### 新機能

![新規](../assets/new.svg) [!DNL Live Search] は、PLP ウィジェットでカラースウォッチをサポートするようになりました。
![新規](../assets/new.svg) [!DNL Live Search] では、カテゴリ ID ではなくカテゴリ名が表示されるようになりました。
![新規](../assets/new.svg) [!DNL Live Search] は、PLP ウィジェットで取り消し線の価格をサポートするようになりました。
![新規](../assets/new.svg) フィルターパネルを非表示にする「フィルターを非表示」ボタンが導入されました。


### 更新

![修正](../assets/fix.svg) この [!DNL Live Search] 新しいインストールで PLP ウィジェットがデフォルトで有効になりました。
![修正](../assets/fix.svg) CSS スタイルの設定を見直し、ウィジェットクラスの分離を改善。
![修正](../assets/fix.svg) 軽微なバグ修正

バージョン 3.1.1 以降をインストールしたら、新しいインデクサーを有効にします。

- 製品価格フィード
- スコープ web サイト データ フィード
- 範囲顧客グループデータフィード

アップグレード後、変更を実稼動環境にプッシュする前に、QA またはステージング環境で、更新された設定をテストします。

## 以前のバージョン

+++3.1.1 以前

## [!DNL Live Search] 3.1.1 {#311}

_2023 年 9 月 15 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg) 新しい「カテゴリマーチャンダイジング」タブが追加されました。 ユーザーは、カテゴリごとにインテリジェントランキングと手動ランキング（ピン、ブースト、埋め込み、非表示）を追加できるようになりました
![新規](../assets/new.svg) ユーザーは、インテリジェントまたは手動のランキングを使用して、単一のカテゴリルールを追加できます
![新規](../assets/new.svg) サブカテゴリにインテリジェントなランキングルールを追加できるようになりました
![新規](../assets/new.svg) インテリジェントランキングを使用してサブカテゴリを削除する際に、詳細な情報が提供されます
![新規](../assets/new.svg) 継承されたランキング戦略のルールを削除する機能を追加しました
![新規](../assets/new.svg) 単一カテゴリのルールを削除する機能を追加しました
![新規](../assets/new.svg) ルールを追加する際に、カテゴリ名で検索できるようになりました
![新規](../assets/new.svg) カテゴリツリー表示を使用すると、ルールが適用されているカテゴリを表示できるようになりました。
![新規](../assets/new.svg) カテゴリプレビューには、選択したカテゴリのみが表示されます。
![新規](../assets/new.svg) AEM CIF [ポップオーバーウィジェット](https://github.com/adobe/aem-cif-guides-venia/pull/319) および [PLP ウィジェット](https://github.com/adobe/aem-cif-guides-venia/pull/320) コンポーネントを使用すると、AEM サイトで以下を利用できます [!DNL Live Search].

### 更新

![修正](../assets/fix.svg) 製品および価格フィードのテーブルサイズが大幅に縮小されました。 テーブル `catalog_data_exporter_products` および `catalog_data_exporter_product_prices` 大幅なサイズ削減が必要です。
![修正](../assets/fix.svg) 「ルール」タブの名前は、「ルールを検索」に変更されます
![修正](../assets/fix.svg) 「トレンド」別にランキングする場合、次の中から選択できるようになりました。- 3 日（デフォルト） – 14 日～30 日
![修正](../assets/fix.svg) 「イベント」（ブースト/ピン/ベリー/非表示）の名前は「手動ランキング」に変更されました
![修正](../assets/fix.svg) 「ランキングタイプ」の名前が「インテリジェントランキング」に変更されました
![修正](../assets/fix.svg) 軽微なバグ修正

## [!DNL Live Search] 3.1.0 {#310}

_2023 年 9 月 1 日（Pt）_

[!BADGE サポート]{type="情報" tooltip="サポート"}

### 更新

![修正](../assets/fix.svg) 製品一覧ウィジェットが更新され、 [Catalog Service API](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/).

## [!DNL Live Search] 3.0.2 {#302}

_2023 年 8 月 7 日（Pt）_

[!BADGE サポート]{type="情報" tooltip="サポート"}

### 新機能

![新規](../assets/new.svg) 次の値がに追加されました `storeDetails` オブジェクト :

- 「1 ページにすべての製品を許可」
- 通貨レート
- 「グリッド許容値の 1 ページあたりの製品数」
- 「グリッドのデフォルト値の 1 ページあたりの製品数」
- ストアの言語

### 更新

![修正](../assets/fix.svg) 高度なデータ取得をサポートするために、カタログサービスモジュールがメタパッケージに追加されました。
![修正](../assets/fix.svg) この **マイアカウント** 製品一覧ページウィジェットを使用した際に、ページナビゲーションが消えなくなりました。

マーチャントは、 [!DNL Live Search] これらの機能にアクセスするには、拡張機能のバージョン >= 3.0.2 を使用します。

実稼動環境にプッシュする前に、アップグレードとテストを行うことをお勧めします。 テスト環境の結果を確認した後、ピーク外の時間に実稼動環境をアップグレードすることを検討します。

### 制限事項

Live Search Product Listing Page Widget を使用すると、Google Tag Manager が失敗する。 Google Tag Manager が必要な場合は、デフォルトの検索アダプタを使用します。

## [!DNL Live Search] 3.0.1 {#301}

_2023 年 3 月 14 日（Pt）_

[!BADGE サポート]{type="情報" tooltip="サポート"}

### 新機能

![新規](../assets/new.svg) ルールのプレビューの製品項目カード
![新規](../assets/new.svg) [製品一覧ページウィジェット](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling)
![新規](../assets/new.svg) [カテゴリフィルターオプション](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#facets)
![新規](../assets/new.svg) ドラッグ&amp;ドロップしてピンイベントを作成する機能を追加しました
![新規](../assets/new.svg) 新しいピン留めアクション：- スポットにピン留め – ワンクリックでピン留めイベントを作成するピンボタン – 上にピン留め – 製品を最初の位置に配置 – 下にピン留め – 結果の下部に製品を配置 – ワンクリックでイベントのピン留めを解除
![新規](../assets/new.svg) [ルールのインテリジェントランキング](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add)
![新規](../assets/new.svg) [!DNL Live Search] 完全なサポートを追加 [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) Commerceの機能（以前はマルチソースインベントリ（MSI）と呼ばれていました）。 フルサポートを有効にするには、次の操作を行う必要があります [更新](install.md#update) 依存関係モジュール `commerce-data-export` をバージョン 102.2.0 以降にアップグレードします。

### 更新

![修正](../assets/fix.svg) Configure Rules で職階を自動的にソートできるようになりました。
![修正](../assets/fix.svg) 既存のイベントを削除すると、プレビューが更新されるようになりました
![修正](../assets/fix.svg) イベントのないルールは保存できません
![修正](../assets/fix.svg) 「タイプを選択」セレクターのファセットを削除
![修正](../assets/fix.svg) 未保存のルールに新しい「編集中」ステータスを追加しました

### 修正点

![修正](../assets/fix.svg) 保存中に未完了のイベントがある場合のサーバーエラーを修正しました
![修正](../assets/fix.svg) 複数のイベントがある場合の、特定のイベントの正しい削除を修正しました
![修正](../assets/fix.svg) 新しいイベントが追加された際に、既存のルールイベントが更新されない修正
![修正](../assets/fix.svg) 詳細からの 2 回目の「編集」クリックに修正されました。 [!DNL Live Search] リロードが必要なページ
![修正](../assets/fix.svg) 同義語：ユーザーが入力をクリックアウトしても、フォーカスをフィールドに戻すことができない問題を修正しました
![修正](../assets/fix.svg) その他の軽微なバグ修正とパフォーマンスの更新


![バグ](../assets/bug.svg) - 「あなたにお勧め」によるランキングは、ライブ検索ウィジェット内でのみサポートされています。 デフォルトの Luma およびPWAの検索機能ではサポートされていません。
![バグ](../assets/bug.svg) - カスタムの価格属性ファセットが Luma で正しくレンダリングされませんが、API が適切にフィルタリングします。

マーチャントは、 [!DNL Live Search] これらの機能にアクセスするには、拡張機能のバージョン >= 3.0.1 を使用します。

実稼動環境にプッシュする前に、アップグレードとテストを行うことをお勧めします。 テスト環境の結果を確認した後、ピーク外の時間に実稼動環境をアップグレードすることを検討します。

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE サポート]{type="情報" tooltip="サポート"}

![修正](../assets/fix.svg) - ネットワークの問題が原因で SDK リソースが使用できない場合、Live Search はエラーをスローします。 このバグは修正されました。

マーチャントがこれらの機能にアクセスするには、Live Search 拡張機能のバージョン >= 2.0.5 をアップグレードする必要があります。

実稼動環境にプッシュする前に、アップグレードとテストを行うことをお勧めします。 テスト環境の結果を確認した後、ピーク外の時間に実稼動環境をアップグレードすることを検討します。

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE サポート]{type="情報" tooltip="サポート"}

![新規](../assets/new.svg) ライブサーチでは、管理者の「在庫切れの製品を表示」設定によるフィルタリングをサポートするようになりました。 「在庫切れの製品を表示」が false に設定されている場合、 `inStock = true` がフィルターに追加されます。
![修正](../assets/fix.svg) パフォーマンスを向上させるために、ライブ検索のポップアップから「候補」ブロックが削除されました。 機能を置き換える場合に備えて、データはGraphQLを通じて渡されます。
![修正](../assets/fix.svg) `categories` および `categoryPath` 置き換えられた `categoryIds` （カテゴリフィルタリング用）。 詳しくは、を参照してください。 [productSearch](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) トピック。
![修正](../assets/fix.svg) 以前は、B2B 会社に関連付けられているユーザーが検索を行うと、誤った顧客グループコードが返されていました。 ライブサーチが正しい値を返すようになりました。
![修正](../assets/fix.svg) 以前は、存在しない用語を検索すると、Live Search はエラーを返していました。 そのバグが修正されました。

マーチャントは、 [!DNL Live Search] これらの機能にアクセスするには、拡張機能のバージョン >= 2.0.4 を選択します。

実稼動環境にプッシュする前に、アップグレードとテストを行うことをお勧めします。 テスト環境の結果を確認した後、ピーク外の時間に実稼動環境をアップグレードすることを検討します。

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE サポート]{type="情報" tooltip="サポート"}

![新規](../assets/new.svg) ライブサーチでは、カテゴリ権限、共有カタログおよび顧客グループ固有の価格を考慮して、B2B 機能をサポートするようになりました。

マーチャントは、 [!DNL Live Search] これらの機能にアクセスするには、拡張機能バージョン >= 2.0.3 を選択します。

実稼動環境にプッシュする前に、アップグレードとテストを行うことをお勧めします。 テスト環境の結果を確認した後、ピーク外の時間に実稼動環境をアップグレードすることを検討します。

### [!DNL Live Search] 2.0 {#20}

[!BADGE サポート]{type="情報" tooltip="サポート"}

既存 [!DNL Live Search] インストールはにアップグレードする必要があります [!DNL Live Search] 2.0.0 では、以下の新機能、修正点および改善点を活用しています。

![新規](../assets/new.svg) [!DNL Live Search] Adobe Commerce 2.4.4 を実行するインストールで PHP 8.1 がサポートされるようになりました。
![新規](../assets/new.svg) この `Magento_ElasticsearchCatalogPermissionsGraphQl` モジュールが、インストール中に無効になるモジュールのリストに追加されます。
![新規](../assets/new.svg) で使用可能なラインの数 [[!DNL storefront popover]](overview.md) は、以下から設定できます *Admin*.
![新規](../assets/new.svg) ベータ版 [PWA](https://developer.adobe.com/commerce/pwa-studio/) サポート対象： [!DNL Live Search].
![新規](../assets/new.svg) この [!DNL Live Search] インストールプロセスは、プロセスの詳細な変更によって更新されます。
![修正](../assets/fix.svg) [詳細検索](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) ストアフロントのフッターからリンクが削除されました。
![バグ](../assets/bug.svg) 次の製品属性は、ではサポートされていません。 [COMMERCE GRAPHQL API](https://developer.adobe.com/commerce/services/graphql/live-search/) PWAのベータ版リリースに関して使用する場合： `description`, `name`, `short_description`
![バグ](../assets/bug.svg) のPWAのベータ版リリース [!DNL Live Search] はサポートしていません [イベント処理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE サポート]{type="情報" tooltip="サポート"}

![修正](../assets/fix.svg) [カスタム価格属性](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/attributes-input-types) として設定した場合にエラーが返されなくなりました。 [ファセット]（{% link live-search/facets-add.md %}）。
![修正](../assets/fix.svg) エラーが発生しない場合に発生する問題を修正しました [通貨記号](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration(optional)) （`data-currency-symbol`）が使用可能です。
![修正](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) に、 [特別価格](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) （最終価格の下限）利用可能な場合。

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE サポート]{type="情報" tooltip="サポート"}

![新規](../assets/new.svg) [パフォーマンス](performance.md) レポートダッシュボードでは、買い物客が使用する検索用語に関するインサイトを提供します。
![新規](../assets/new.svg) [!DNL Live Search] [ストアフロントイベント SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) イベントの公開サービス、購読サービスおよび指標を含む共通のデータレイヤーへのアクセスを提供します。
![修正](../assets/fix.svg) この [[!DNL Storefront popover]](storefront-popover.md) には、新しいがあります `active` のクラス `.search-autocomplete` 表示を制御するコンテナ。
![修正](../assets/fix.svg) ストアフロントでは、 [検索語句](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms) フッターリンクが削除され、のキャッシュが無効になる [!DNL Live Search] インストール。
![バグ](../assets/bug.svg) 検索アダプタのパッチは、重複した製品を処理します。
![バグ](../assets/bug.svg) [!DNL Live Search] のサポート [単一ソース](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/sources/sources-manage) （物理）複数の（仮想）インベントリの場所 [在庫](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage). 複数のインベントリソースは現在サポートされていません。

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE サポート]{type="情報" tooltip="サポート"}

![新規](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) 買い物客が「検索」ボックスにクエリを入力すると、検索結果の候補とサムネール画像が表示されます。
![新規](../assets/new.svg) コマース *Admin* キーボードが無操作状態が長時間続いている間は、セッションは開いたままになります
![新規](../assets/new.svg) [!DNL Live Search] はオンボーディング後に自動的に有効になります
![修正](../assets/fix.svg) 最初のインデックス作成時間が 1 時間未満です
![修正](../assets/fix.svg) 製品の増分更新をほぼリアルタイム（インストールおよびセットアップ後）
![修正](../assets/fix.svg) シノニム・エディタのソート可能な列
![修正](../assets/fix.svg) [!DNL Live Search] 検索条件に空の並べ替え順の値が含まれる場合にエラーがスローされなくなりました
![修正](../assets/fix.svg) 属性コードに「to」または「from」の文字列が含まれている場合に、範囲フィルタリングが解除されなくなりました。

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE サポート]{type="情報" tooltip="サポート"}

![バグ](../assets/bug.svg) この [!DNL Live Search] サービスでは、以下のみをサポートしています。 [基準通貨](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration) （Adobe Commerce インストールの場合）。
![バグ](../assets/bug.svg) ファセットを追加するときに、をに設定すると製品属性フィードが正しく更新されない `Update on Save`. この問題を回避するには、に移動してください。 [インデックス管理](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) およびが製品属性フィードをに設定しました `Update by Schedule`.
![バグ](../assets/bug.svg) [!DNL Live Search] シノニムはストア表示ごとに定義されますが、現在は web サイトごとに保存され、次の組み合わせで識別されます。 `environmentId` および `storeViewCode`. その結果、Adobe Commerce インストール内のすべての web サイトとストアビューで同義語が共有されます。 ストア表示の最近作成された同義語セットが優先されます。
![バグ](../assets/bug.svg) 同義語に複数の単語が含まれる場合、各単語は個別の同義語として扱われます。 例えば、「time piece」を「watch」の同義語として定義した場合、「time」と「piece」の両方が watch の同義語として扱われます。

+++

## マニュアル

詳細情報：

- [Adobe Commerce開発者向けドキュメント](https://developer.adobe.com/commerce/docs)
- [Adobe Commerce ユーザーガイド](https://experienceleague.adobe.com/en/docs/commerce)
- [[!DNL Live Search] Marketplace で](https://commercemarketplace.adobe.com/magento-live-search.html)
