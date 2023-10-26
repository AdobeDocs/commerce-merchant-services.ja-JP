---
title: "[!DNL Live Search] リリースノート"
description: 次の最新のリリース情報： [!DNL Live Search] Adobe Commerceから」
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
feature: Services, Search, Release Notes
source-git-commit: 67b4f24828dfdda6bd166791d6c36922294b402f
workflow-type: tm+mt
source-wordcount: '1797'
ht-degree: 0%

---

# [!DNL Live Search] リリースノート

これらのリリースノートでは、の最新バージョンについて説明します。 [!DNL Live Search].
現在のメジャーリリースバージョンがサポートされています。 古いバージョンのリリースノートは参照用に提供されています。
更新内容は次のとおりです。

![新規](../assets/new.svg) 新機能
![修正点](../assets/fix.svg) 修正点および改善点
![バグ](../assets/bug.svg) 既知の問題

## ホストされるサービスの更新

これらのノートでは、バージョン管理されたリリース以外で公開された更新や、ホストされたサービスの改善について説明します。

+++ホストされたサービスの更新

_2023 年 10 月 13 日_

![新規](../assets/new.svg) コマース管理者は、インデックスの言語を指定できるようになりました。 [!DNL Live Search]. 詳しくは、 [設定](settings.md).
![修正点](../assets/fix.svg) 「検索ルール」タブの名前が「検索マーチャンダイジング」に変更されました。

_2023 年 6 月 14 日_

![修正点](../assets/fix.svg) 引用符やアポストロフィなどの一部の文字がランキングの問題を引き起こしていた問題を修正しました。 インデックスを再作成すると、これらの問題が解決します。

_2023 年 4 月 26 日_

![新規](../assets/new.svg) [!DNL Live Search] お客様は、 [SaaS 価格インデクサー](../price-index/index.md).

+++

## [!DNL Live Search] 3.1.1 {#311}

_2023 年 9 月 16 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

### 新機能

![新規](../assets/new.svg) 新しいカテゴリマーチャンダイジングタブが追加されました。 ユーザーは、カテゴリごとにインテリジェントランキングと手動ランキング（ピン、ブースト、ベリー、非表示）を追加できるようになりました。
![新規](../assets/new.svg) ユーザーは、インテリジェントランキングまたは手動ランキングを持つ単一のカテゴリルールを追加できます
![新規](../assets/new.svg) ユーザーは、インテリジェントランキングルールをサブカテゴリに追加できるようになりました
![新規](../assets/new.svg) インテリジェントランキングを持つサブカテゴリを削除する際に、詳細情報が表示されます
![新規](../assets/new.svg) 継承されたランキング戦略のルールを削除する機能を追加しました。
![新規](../assets/new.svg) 単一のカテゴリのルールを削除する機能を追加しました。
![新規](../assets/new.svg) ルールを追加する際に、カテゴリ名で検索できるようになりました
![新規](../assets/new.svg) カテゴリツリー表示を使用すると、ルールが適用されたカテゴリを表示できるようになりました。
![新規](../assets/new.svg) カテゴリプレビューには、選択したカテゴリのみが表示されます。
![新規](../assets/new.svg) AEM CIF [ポップオーバーウィジェット](https://github.com/adobe/aem-cif-guides-venia/pull/319) および [PLP ウィジェット](https://github.com/adobe/aem-cif-guides-venia/pull/320) コンポーネントを使用すると、AEMサイトで [!DNL Live Search].

### 更新

![修正点](../assets/fix.svg) 製品と価格のフィードのテーブルサイズが大幅に縮小されました。 テーブル `catalog_data_exporter_products` および `catalog_data_exporter_product_prices` 大幅なサイズ削減が見込まれる
![修正点](../assets/fix.svg) 「ルール」タブの名前が「検索ルール」に変更されました
![修正点](../assets/fix.svg) 「トレンド」でランク付けする場合、次の中から選択できるようになりました。* 3 日（デフォルト） * 14 日* 30 日
![修正点](../assets/fix.svg) 「イベント」（ブースト/ピン/ベリー/非表示）の名前が「手動ランキング」に変更されました。
![修正点](../assets/fix.svg) 「ランキングタイプ」は「インテリジェントランキング」に名前が変更されました
![修正点](../assets/fix.svg) マイナーなバグ修正。

マーチャントは [!DNL Live Search] 拡張機能のバージョンが 3.1.1 以降の場合は、これらの機能にアクセスできます。

バージョン 3.1.1 をインストールした後、次の新しいインデクサーを有効にする必要があります。

* 製品価格フィード
* スコープの Web サイトデータフィード
* スコープの顧客グループデータフィード

変更を実稼動環境にプッシュする前に、QA またはステージングでアップグレードおよびテストすることをお勧めします。

## 以前のバージョン

+++3.1.0 以前

## [!DNL Live Search] 3.1.0 {#310}

_2023 年 9 月 2 日_

[!BADGE サポート対象]{type="参考情報" tooltip="サポート対象"}

### 更新

![修正点](../assets/fix.svg) 製品リストウィジェットが更新され、 [カタログサービス API](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/product-search/).

## [!DNL Live Search] 3.0.2 {#302}

_2023 年 8 月 8 日_

[!BADGE サポート対象]{type="参考情報" tooltip="サポート対象"}

### 新機能

![新規](../assets/new.svg) 以下の値が `storeDetails` オブジェクト：

* &quot;1 ページにすべての製品を許可&quot;
* 通貨レート
* 「許容値のグリッドの 1 ページあたりの製品数」
* 「グリッドのデフォルト値の 1 ページあたりの製品」
* ストアの言語

### 更新

![修正点](../assets/fix.svg) 高度なデータ取得をサポートするために、カタログサービスモジュールがメタパッケージに追加されました。
![修正点](../assets/fix.svg) The **マイアカウント** 製品リストページウィジェットを使用する際に、ページナビゲーションが消えなくなりました。

マーチャントは [!DNL Live Search] これらの機能にアクセスするには、拡張機能バージョン 3.0.2 以降を参照してください。

実稼動環境にプッシュする前に、アップグレードおよびテストすることをお勧めします。 テスト環境の結果を確認した後、オフピーク時に実稼動環境のアップグレードを検討します。

### 制限事項

ライブ検索の製品リストページウィジェットを使用すると、Google Tag Manager が失敗します。 Google Tag Manager が必要な場合は、デフォルトの検索アダプターを使用します。

## [!DNL Live Search] 3.0.1 {#301}

_2023 年 3 月 15 日_

[!BADGE サポート対象]{type="参考情報" tooltip="サポート対象"}

### 新機能

![新規](../assets/new.svg) ルールプレビューの製品品目カード
![新規](../assets/new.svg) [製品リストページウィジェット](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
![新規](../assets/new.svg) [カテゴリのフィルターオプション](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#facets)
![新規](../assets/new.svg) ドラッグ&amp;ドロップでピンイベントを作成する機能が追加されました。
![新規](../assets/new.svg) 新しいピン操作： *スポットにピン留め — ピン留めボタンを使用して 1 回のクリックでピンイベントを作成*最上位にピン留め — 最初の位置に商品を配置*最下位にピン留め — 結果の下位に商品を配置*1 回のクリックでイベントのピン留めを解除
![新規](../assets/new.svg) [ルールのインテリジェントランキング](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add.html#ranking-type)
![新規](../assets/new.svg) [!DNL Live Search] フルをサポート [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) コマースの機能 ( 以前はマルチソースインベントリ (MSI) と呼ばれていました )。 完全なサポートを有効にするには、 [更新](install.md#update) 依存モジュール `commerce-data-export` をバージョン 102.2.0 以降に変更しました。

### 更新

![修正点](../assets/fix.svg) ルールの構成で位置を自動的に一意に並べ替えるようになりました
![修正点](../assets/fix.svg) 既存のイベントを削除すると、プレビューが更新されるようになりました
![修正点](../assets/fix.svg) イベントのないルールは保存できません
![修正点](../assets/fix.svg) ファセット設定の「タイプを選択」セレクターを削除
![修正点](../assets/fix.svg) 未保存のルールに新しい「編集中」ステータスを追加しました

### 修正点

![修正点](../assets/fix.svg) 保存中に未完了のイベントが発生した場合のサーバーエラーを修正しました。
![修正点](../assets/fix.svg) 複数のイベントがある場合に特定のイベントを正しく削除する問題を修正しました。
![修正点](../assets/fix.svg) 新しいイベントが追加された場合に既存のルールイベントが更新されない問題を修正しました。
![修正点](../assets/fix.svg) 2 回目の「編集」での詳細のクリックを修正。 [!DNL Live Search] 再読み込みが必要なページ
![修正点](../assets/fix.svg) シノニム：ユーザーが入力をクリックアウトした場合に、フォーカスをフィールドに戻すことができない問題を修正しました。
![修正点](../assets/fix.svg) その他のマイナーなバグ修正とパフォーマンスの更新


![バグ](../assets/bug.svg) - 「お勧め」によるランキングは、Live Search ウィジェット内でのみサポートされています。 デフォルトの Luma およびPWA検索機能ではサポートされていません。
![バグ](../assets/bug.svg)  — カスタム価格属性ファセットは Luma では正しくレンダリングされませんが、API はそれらに対して適切にフィルタリングします。

マーチャントは [!DNL Live Search] これらの機能にアクセスするには、拡張機能バージョン 3.0.1 以降を参照してください。

実稼動環境にプッシュする前に、アップグレードおよびテストすることをお勧めします。 テスト環境の結果を確認した後、オフピーク時に実稼動環境のアップグレードを検討します。

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE サポート対象]{type="参考情報" tooltip="サポート対象"}

![修正点](../assets/fix.svg)  — ネットワークの問題が原因で SDK リソースを使用できない場合、ライブ検索でエラーが発生していました。 このバグは修正されました。

これらの機能にアクセスするには、マーチャントは Live Search 拡張機能バージョン 2.0.5 以降をアップグレードする必要があります。

実稼動環境にプッシュする前に、アップグレードおよびテストすることをお勧めします。 テスト環境の結果を確認した後、オフピーク時に実稼動環境のアップグレードを検討します。

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE サポート対象]{type="参考情報" tooltip="サポート対象"}

![新規](../assets/new.svg) ライブ検索で、管理の「在庫切れの製品を表示」設定によるフィルタリングがサポートされるようになりました。 「在庫切れの製品を表示」が false に設定されている場合、 `inStock = true` がフィルターに追加されます。
![修正点](../assets/fix.svg) パフォーマンスを向上させるために、ライブ検索ポップアップから「候補」ブロックが削除されました。 この機能を置き換える場合でも、データはGraphQL経由で渡されます。
![修正点](../assets/fix.svg) `categories` および `categoryPath` 置き換えられた `categoryIds` （カテゴリのフィルタリング用） 詳しくは、 [productSearch](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) トピック。
![修正点](../assets/fix.svg) 以前は、B2B 会社に関連付けられているユーザーが検索をおこなうと、誤った顧客グループコードを受け取っていました。 ライブ検索で正しい値が返されるようになりました。
![修正点](../assets/fix.svg) 以前は、存在しない語句を検索すると、ライブ検索でエラーが返されていました。 そのバグは修正されました。

マーチャントは [!DNL Live Search] これらの機能にアクセスするには、拡張機能バージョン 2.0.4 以降を参照してください。

実稼動環境にプッシュする前に、アップグレードおよびテストすることをお勧めします。 テスト環境の結果を確認した後、オフピーク時に実稼動環境のアップグレードを検討します。

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE サポート対象]{type="参考情報" tooltip="サポート対象"}

![新規](../assets/new.svg) ライブ検索で、カテゴリ権限、共有カタログ、および顧客グループ固有の価格設定を遵守することで、B2B 機能がサポートされるようになりました。

マーチャントは [!DNL Live Search] これらの機能にアクセスするには、拡張機能バージョン 2.0.3 以降を参照してください。

実稼動環境にプッシュする前に、アップグレードおよびテストすることをお勧めします。 テスト環境の結果を確認した後、オフピーク時に実稼動環境のアップグレードを検討します。

### [!DNL Live Search] 2.0 {#20}

[!BADGE サポート対象]{type="参考情報" tooltip="サポート対象"}

既存 [!DNL Live Search] インストールは、次にアップグレードする必要があります： [!DNL Live Search] 2.0.0 では、次の新機能、修正点および改善点を活用できます。

![新規](../assets/new.svg) [!DNL Live Search] Adobe Commerce 2.4.4 を実行するインストールで、PHP 8.1 がサポートされるようになりました。
![新規](../assets/new.svg) The `Magento_ElasticsearchCatalogPermissionsGraphQl` モジュールは、インストール時に無効になるモジュールのリストに追加されます。
![新規](../assets/new.svg) 内の使用可能な行の数 [[!DNL storefront popover]](quick-tour.md) は、 *管理者*.
![新規](../assets/new.svg) ベータ版 [PWA](https://developer.adobe.com/commerce/pwa-studio/) サポート対象： [!DNL Live Search].
![新規](../assets/new.svg) The [!DNL Live Search] インストールプロセスが、高度なプロセス変更で更新されました。
![修正点](../assets/fix.svg) [詳細検索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) storefront フッターからリンクが削除されました。
![バグ](../assets/bug.svg) 次の製品属性は、ではサポートされていません。 [Commerce GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/) PWAのベータリリースに関連して使用する場合： `description`, `name`, `short_description`
![バグ](../assets/bug.svg) のPWAのベータリリース [!DNL Live Search] はをサポートしていません。 [イベント処理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE サポート対象]{type="参考情報" tooltip="サポート対象"}

![修正点](../assets/fix.svg) [カスタム価格属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) では、 [ファセット]({% link live-search/facets-add.md %})。
![修正点](../assets/fix.svg) 次の場合にエラーが発生する問題を修正しました。 [通貨記号](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`) が使用可能です。
![修正点](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) には、が表示されます [特別価格](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) （最終価格の最小値）を指定できます。

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE サポート対象]{type="参考情報" tooltip="サポート対象"}

![新規](../assets/new.svg) [パフォーマンス](performance.md) レポートダッシュボードでは、買い物客が使用する検索用語に関するインサイトを得ることができます。
![新規](../assets/new.svg) [!DNL Live Search] [Storefront Events SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) では、イベント公開および購読サービス、指標を含む、共通のデータレイヤーにアクセスできます。
![修正点](../assets/fix.svg) The [[!DNL Storefront popover]](storefront-popover.md) には、新しい `active` クラス `.search-autocomplete` 表示/非表示を制御するコンテナ。
![修正点](../assets/fix.svg) 店頭では、 [検索語句](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) フッターリンクが削除され、そのキャッシュが無効になっている [!DNL Live Search] インストール。
![バグ](../assets/bug.svg) 検索アダプタのパッチは、重複した製品を処理します。
![バグ](../assets/bug.svg) [!DNL Live Search] サポート [単一ソースの](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) （物理）複数の（仮想）在庫場所 [在庫](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). 現在、複数の在庫ソースはサポートされていません。

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE サポート対象]{type="参考情報" tooltip="サポート対象"}

![新規](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) 「検索」ボックスに買い物客タイプのクエリとして、上位の検索結果の推奨製品とサムネール画像を表示します。
![新規](../assets/new.svg) コマース *管理者* キーボードの操作が行われない時間が長く続く間、セッションは開いたままになる
![新規](../assets/new.svg) [!DNL Live Search] オンボーディング後、が自動的に有効になります
![修正点](../assets/fix.svg) 初期インデックス作成時間が 1 時間未満です
![修正点](../assets/fix.svg) ほぼリアルタイムで製品の増分アップデート（インストールおよびセットアップ後）
![修正点](../assets/fix.svg) シノニム・エディタの並べ替え可能な列
![修正点](../assets/fix.svg) [!DNL Live Search] 検索条件に空の並べ替え順の値が含まれる場合にエラーがスローされなくなりました。
![修正点](../assets/fix.svg) 属性コードに「to」または「from」の文字列が含まれる場合、範囲フィルターが壊れなくなりました。

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE サポート対象]{type="参考情報" tooltip="サポート対象"}

![バグ](../assets/bug.svg) The [!DNL Live Search] サービスは、 [基準通貨](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) Adobe Commerceのインストール
![バグ](../assets/bug.svg) ファセットを追加する場合、に設定すると、製品属性フィードが正しく更新されません。 `Update on Save`. この問題を回避するには、に移動します。 [インデックス管理](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 製品属性フィードをに設定します。 `Update by Schedule`.
![バグ](../assets/bug.svg) [!DNL Live Search] シノニムはストア表示ごとに定義されますが、現在は Web サイトごとに保存され、次の組み合わせで識別されます。 `environmentId` および `storeViewCode`. その結果、Adobe Commerceのインストール内のすべての Web サイトおよびストア表示では、同義語が共有されます。 ストア表示のシノニムの最近作成したセットが優先されます。
![バグ](../assets/bug.svg) シノニム用語に複数の単語が含まれる場合、各単語は別々のシノニムとして扱われます。 例えば、「時間」を「時間」のシノニムとして定義した場合、「時間」と「ピース」の両方は、時間の同義語として扱われます。

+++

## ドキュメント

詳しくは、以下を参照してください。

* [Adobe Commerce開発者向けドキュメント](https://developer.adobe.com/commerce/docs)
* [Adobe Commerce User Guide](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] Marketplace の](https://commercemarketplace.adobe.com/magento-live-search.html)
