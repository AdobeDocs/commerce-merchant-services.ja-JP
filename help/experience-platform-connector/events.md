---
title: イベント
description: 各イベントが取り込むデータを説明します。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: ddacfc053f83be750c63ba376519169b38f7f478
workflow-type: tm+mt
source-wordcount: '4596'
ht-degree: 0%

---

# Experience Platformコネクタイベント

次に、Commerce Connector 拡張機能をインストールする際に使用できる CommerceExperience Platformを示します。 これらのイベントで収集されたデータは、Adobe Experience Platform Edge に送信されます。 また、 [カスタムイベント](custom-events.md) 標準で提供されていない追加データを収集する場合。

以下のイベントで収集されるデータに加えて、 [その他のデータ](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) Adobe Experience Platform Web SDK によって提供されます。

## ストアフロントイベント

ストアフロントイベントは、サイトを閲覧する買い物客から匿名化された行動データを収集します。 これらのイベントで収集されたデータを使用して、特定の買い物客セットをターゲットにしたプロモーションやキャンペーンを作成できます。

>[!NOTE]
>
>すべてのストアフロントイベントには、 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) フィールドに含まれます。これには、買い物客の電子メールアドレス（利用可能な場合）と ECID が含まれます。 このプロファイルデータを各イベントに含めることで、Adobe Commerceから別のユーザーアカウントをインポートする必要がなくなります。

### addToCart

| 説明 | XDM イベント名 |
|---|---|
| 製品が買い物かごに追加されたとき、または買い物かご内の製品の数量が増加したときにトリガーされます。 | `commerce.productListAdds` |

#### addToCart から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `productListAdds` | 製品が買い物かごに追加されたかどうかを示します。 値： `1` は、製品が追加されたことを示します。 |
| `productListItems` | 買い物かごに追加された製品の配列 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `priceTotal` | 製品品目の合計価格 |
| `quantity` | 買い物かごに追加された製品単位数 |
| `discountAmount` | 適用された割引額を示します |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 商品の通貨 |
| `productImageUrl` | 製品のメイン画像 URL |
| `selectedOptions` | 設定可能な製品に使用するフィールド。 `attribute` 設定可能な製品の属性を次のように指定します。 `size` または `color` および `value` 属性の値を次のように指定します。 `small` または `black`. |
| `cartID` | 顧客の買い物かごを識別する一意の ID |

### openCart

| 説明 | XDM イベント名 |
|---|---|
| 新しい買い物かごが作成されたとき（製品が空の買い物かごに追加されたとき）にトリガーされます。 | `commerce.productListOpens` |

#### openCart から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `productListOpens` | 買い物かごが作成されたかどうかを示します。 値： `1` は、買い物かごが作成されたことを示します。 |
| `productListItems` | 買い物かごに追加された製品の配列 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `priceTotal` | 製品品目の合計価格 |
| `quantity` | 買い物かごに追加された製品単位数 |
| `discountAmount` | 適用された割引額を示します |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 商品の通貨 |
| `productImageUrl` | 製品のメイン画像 URL |
| `selectedOptions` | 設定可能な製品に使用するフィールド。 `attribute` 設定可能な製品の属性を次のように指定します。 `size` または `color` および `value` 属性の値を次のように指定します。 `small` または `black`. |
| `cartID` | 顧客の買い物かごを識別する一意の ID |

### removeFromCart

| 説明 | XDM イベント名 |
|---|---|
| 製品が削除されるたびに、または買い物かご内の製品の数量が減らされるたびにトリガーされます。 | `commerce.productListRemovals` |

#### removeFromCart から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `productListRemovals` | 製品が買い物かごから削除されたかどうかを示します。 値： `1` 製品が買い物かごから削除されたことを示します。 |
| `productListItems` | 買い物かごから削除された製品の配列 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `priceTotal` | 製品品目の合計価格 |
| `quantity` | 買い物かごから削除された製品単位の数 |
| `discountAmount` | 適用された割引額を示します |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 商品の通貨 |
| `productImageUrl` | 製品のメイン画像 URL |
| `selectedOptions` | 設定可能な製品に使用するフィールド。 `attribute` 設定可能な製品の属性を次のように指定します。 `size` または `color` および `value` 属性の値を次のように指定します。 `small` または `black`. |
| `cartID` | 顧客の買い物かごを識別する一意の ID |

### shoppingCartView

| 説明 | XDM イベント名 |
|---|---|
| 買い物かごのページが読み込まれたときにトリガーされます。 | `commerce.productListViews` |

#### shoppingCartView から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `productListViews` | 製品リストが表示されたかどうかを示します |
| `productListItems` | 買い物かごに含まれる製品の配列 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `priceTotal` | 製品品目の合計価格 |
| `quantity` | 買い物かご内の製品単位数 |
| `discountAmount` | 適用された割引額を示します |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 商品の通貨 |
| `productImageUrl` | 製品のメイン画像 URL |
| `selectedOptions` | 設定可能な製品に使用するフィールド。 `attribute` 設定可能な製品の属性を次のように指定します。 `size` または `color` および `value` 属性の値を次のように指定します。 `small` または `black`. |
| `cartID` | 顧客の買い物かごを識別する一意の ID |

### pageView

| 説明 | XDM イベント名 |
|---|---|
| ページが読み込まれたときにトリガーされます。 | `web.webpagedetails.pageViews` |

#### pageView から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `pageViews` | ページが読み込まれたかどうかを示します。 A `value` / `1` ページが読み込まれたことを示します。 |

### productPageView

| 説明 | XDM イベント名 |
|---|---|
| 製品ページが読み込まれたときにトリガーされます。 | `commerce.productViews` |

#### productPageView から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `productViews` | 製品が表示されたかどうかを示します |
| `productListItems` | 買い物かごに含まれる製品の配列 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `priceTotal` | 製品品目の合計価格 |
| `discountAmount` | 適用された割引額を示します |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 商品の通貨 |
| `productImageUrl` | 製品のメイン画像 URL |
| `selectedOptions` | 設定可能な製品に使用するフィールド。 `attribute` 設定可能な製品の属性を次のように指定します。 `size` または `color` および `value` 属性の値を次のように指定します。 `small` または `black`. |

### startCheckout

| 説明 | XDM イベント名 |
|---|---|
| 買い物客がチェックアウトボタンをクリックしたときにトリガーされます。 | `commerce.checkouts` |

#### startCheckout から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `checkouts` | チェックアウトプロセス中にアクションが発生したかどうかを示します |
| `productListItems` | 買い物かごに含まれる製品の配列 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `priceTotal` | 製品品目の合計価格 |
| `quantity` | 買い物かご内の製品単位数 |
| `discountAmount` | 適用された割引額を示します |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 商品の通貨 |
| `productImageUrl` | 製品のメイン画像 URL |
| `selectedOptions` | 設定可能な製品に使用するフィールド。 `attribute` 設定可能な製品の属性を次のように指定します。 `size` または `color` および `value` 属性の値を次のように指定します。 `small` または `black`. |
| `cartID` | 顧客の買い物かごを識別する一意の ID |

### completeCheckout

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が注文したときにトリガーされます。 | `commerce.order` |

#### completeCheckout から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `purchases` | 注文が受け入れられたかどうかを示します |
| `order` | 1 つ以上の製品の注文に関する情報が含まれます |
| `purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `orderType` | 注文のタイプを示します（チェックアウト、即時購入など） |
| `payments` | この注文の支払いのリスト |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) この支払い項目に使用される通貨コード。 例： `USD` または `EUR`. |
| `paymentAmount` | 支払の値 |
| `paymentType` | この注文の支払い方法。 オプションは次のとおりです。 `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other` |
| `transactionID` | この支払い項目の一意のトランザクション識別子 |
| `shipping` | 1 つ以上の製品の出荷の詳細。 |
| `shippingMethod` | 顧客が選択した送料方法（標準配送、即時配送、店頭受け取りなど） |
| `shippingAmount` | 買い物かご内の品目の合計送料 |
| `promotionID` | プロモーションの一意の識別子（存在する場合） |
| `personalEmail` | 個人の電子メールアドレスを指定 |
| `address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているように |
| `productListItems` | 買い物かごに含まれる製品の配列 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `priceTotal` | 製品品目の合計価格 |
| `quantity` | 買い物かご内の製品単位数 |
| `discountAmount` | 適用された割引額を示します |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 注文の合計に使用する通貨コード。 |
| `productImageUrl` | 製品のメイン画像 URL |
| `selectedOptions` | 設定可能な製品に使用するフィールド。 `attribute` 設定可能な製品の属性を次のように指定します。 `size` または `color` および `value` 属性の値を次のように指定します。 `small` または `black`. |

## プロファイルイベント

プロファイルイベントには、 `signIn`, `signOut`, `createAccount`、および `editAccount`. このデータは、セグメントをより適切に定義したり、マーケティングキャンペーンを実行したりするために必要な顧客の主要な詳細情報を入力するのに役立ちます。例えば、ニューヨークに住む買い物客をターゲットに設定する場合などです。

### signIn

| 説明 | XDM イベント名 |
|---|---|
| 買い物客がログインしようとしたときにトリガーされます。 | `userAccount.login` |

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

#### signIn から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `person` | 個々のアクター、連絡先、または所有者 |
| `accountID` | ユーザーアカウント ID をキャプチャします |
| `accountType` | ユーザーアカウントタイプをキャプチャします（例： ）。 `Personal` または `Company`該当する場合は、 |
| `personalEmailID` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているように |
| `personalEmail` | 連絡先の詳細をキャプチャします — 電子メールと関連情報 |
| `address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているように |
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します |
| `login` | 訪問者がログインしようとしたかどうかを示します |

### signOut

| 説明 | XDM イベント名 |
|---|---|
| 買い物客がサインアウトを試みたときにトリガーされます。 | `userAccount.logout` |

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

#### signOut から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します |
| `logout` | 訪問者がログアウトしようとしたかどうかを示します |

### createAccount

| 説明 | XDM イベント名 |
|---|---|
| 買い物客がアカウントを作成しようとしたときにトリガーされます。 | `userAccount.createProfile` |

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

#### createAccount から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `person` | 個々のアクター、連絡先、または所有者 |
| `accountID` | ユーザーアカウント ID をキャプチャします |
| `accountType` | ユーザーアカウントタイプをキャプチャします（例： ）。 `Personal` または `Company`該当する場合は、 |
| `personalEmailID` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているように |
| `personalEmail` | 連絡先の詳細をキャプチャします — 電子メールと関連情報 |
| `address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているように |
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します |
| `createProfile` | ユーザーがアカウントプロファイルを作成したかどうかを示します |

### editAccount

| 説明 | XDM イベント名 |
|---|---|
| 買い物客がアカウントを編集しようとしたときにトリガーされます。 | `userAccount.updateProfile` |

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

#### editAccount から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `person` | 個々のアクター、連絡先、または所有者 |
| `accountID` | ユーザーアカウント ID をキャプチャします |
| `accountType` | ユーザーアカウントタイプをキャプチャします（例： ）。 `Personal` または `Company`該当する場合は、 |
| `personalEmailID` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているように |
| `personalEmail` | 連絡先の詳細をキャプチャします — 電子メールと関連情報 |
| `address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているように |
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します |
| `updateProfile` | ユーザーがアカウントプロファイルを更新したかどうかを示します |

## イベントを検索

検索イベントは、買い物客の意図に関連するデータを提供します。 買い物客の意図をインサイトすることで、買い物客が商品やクリックしたものを検索し、最終的に購入または放棄する方法を知ることができます。 このデータの使用例は、トップ商品を検索しても商品を購入しない既存の買い物客をターゲットにしたい場合です。

以下を使用： `uniqueIdentifier` 両方に見つかったフィールド `searchRequestSent` および `searchResponseReceived` イベントを使用して、対応する検索応答に検索リクエストを相互参照します。

### searchRequestSent

| 説明 | XDM イベント名 |
|---|---|
| 「入力時に検索」ポップオーバーで、次のイベントによってトリガーされます。<br><br>[Enter] を押し、をクリックします。 _すべて表示_<br><br>&#x200B;検索結果ページの次のイベントによってトリガーされます。<br><br>フィルターを選択し、並べ替え順を変更します (_並べ替え基準_)、並べ替え方向（昇順または降順）を変更、ページごとの結果数を変更 (_1 ページあたりの数を表示_)、次のページに移動、前のページに移動、別のページに移動 | `searchRequest` |

>[!NOTE]
>
>B2B モジュールがインストールされているAdobe Commerce Enterprise Edition では、検索イベントはサポートされていません。

#### searchRequestSent から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `searchRequest` | 検索リクエストが送信されたかどうかを示します |
| `id` | この特定の検索リクエストの一意の ID |
| `filter` | 検索結果を制限するためにフィルターが適用されたかどうかを示します |
| `attribute` （フィルター） | 項目を検索結果に含めるかどうかを決定するために使用される項目のファセット |
| `value` | 検索結果に含まれる項目を決定するために使用される属性値 |
| `isRange` | true の場合、値は許容可能な値の範囲の終点を示します |
| `sort` | 検索結果の並べ替え方法を示します |
| `attribute` （並べ替え） | 検索結果の項目の並べ替えに使用する属性 |
| `order` | 検索結果を返す順序 |
| `query` | 検索された用語 |

### searchResponseReceived

| 説明 | XDM イベント名 |
|---|---|
| 「入力時に検索」ポップオーバーまたは検索結果ページの結果がライブ検索で返された場合にトリガーされます。 | `searchResponse` |

>[!NOTE]
>
>B2B モジュールがインストールされているAdobe Commerce Enterprise Edition では、検索イベントはサポートされていません。

#### searchResponseReceived から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `searchResponse` | 検索応答を受信したかどうかを示します |
| `id` | この特定の検索応答の一意の ID |
| `suggestions` | カタログに存在し、検索クエリに類似する製品とカテゴリの名前を含む文字列の配列。 |
| `numberOfResults` | 返された製品の数 |
| `productListItems` | 買い物かごに含まれる製品の配列。 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `productImageUrl` | 製品のメイン画像 URL |

## B2B イベント

![Adobe Commerce用 B2B](../assets/b2b.svg) B2B 商人の場合、 [インストール](install.md#install-the-b2b-extension) の `experience-platform-connector-b2b` 拡張機能を使用して、これらのイベントを有効にします。

B2B イベントには、 [購買依頼リスト](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) 情報（購買依頼リストが作成、追加、削除された場合など）。 購買依頼リストに固有のイベントを追跡することで、顧客が頻繁に購入する製品を確認し、そのデータに基づいてキャンペーンを作成できます。

### createRequisitionList

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が新しい購買依頼リストを作成したときにトリガーされます。 | `commerce.requisitionListOpens` |

#### createReqisitionList から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `requisitionList` | 顧客が作成した購買依頼リストのプロパティ |
| `ID` | 購買依頼リストの一意の ID |
| `name` | 顧客が指定した購買依頼リストの名前 |
| `description` | 顧客が指定した購買依頼リストの説明 |

### addToRequisitionList

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が既存のリクエストリストに製品を追加した場合、または新しいリストの作成時にトリガーされます。 | `commerce.requisitionListAdds` |

>[!NOTE]
>
>`addToRequisitionList` は、カテゴリ表示ページや設定可能な製品ではサポートされていません。 製品表示ページとシンプルな製品でサポートされています。

#### addToRequisitionList から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `requisitionList` | 顧客が作成した購買依頼リストのプロパティ |
| `ID` | 購買依頼リストの一意の ID |
| `name` | 顧客が指定した購買依頼リストの名前 |
| `description` | 顧客が指定した購買依頼リストの説明 |
| `productListItems` | 購買依頼リストに追加された製品の配列 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `quantity` | 追加された製品単位数 |
| `priceTotal` | 製品品目の合計価格 |
| `discountAmount` | 適用された割引額を示します |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) この支払い項目に使用される通貨コード |
| `selectedOptions` | 設定可能な製品に使用するフィールド。 `attribute` 設定可能な製品の属性を次のように指定します。 `size` または `color` および `value` 属性の値を次のように指定します。 `small` または `black`. |

### removeFromRequisitionList

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が購買依頼リストから製品を削除した場合にトリガーされます。 | `commerce.requisitionListRemovals` |

#### removeFromRequisitionList から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `requisitionList` | 顧客が作成した購買依頼リストのプロパティ |
| `ID` | 購買依頼リストの一意の ID |
| `name` | 顧客が指定した購買依頼リストの名前 |
| `description` | 顧客が指定した購買依頼リストの説明 |
| `productListItems` | 購買依頼リストに追加された製品の配列 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `quantity` | 追加された製品単位数 |
| `priceTotal` | 製品品目の合計価格 |
| `discountAmount` | 適用された割引額を示します |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) この支払い項目に使用される通貨コード |
| `selectedOptions` | 設定可能な製品に使用するフィールド。 `attribute` 設定可能な製品の属性を次のように指定します。 `size` または `color` および `value` 属性の値を次のように指定します。 `small` または `black`. |

## バックオフィスイベント

バックオフィスイベントには、注文が発行されたか、キャンセルされたか、返金されたか、発送されたか、完了したかなど、注文の状態に関する情報が含まれます。 これらのサーバー側イベントが収集するデータは、買い物客の注文を 360 ビュー表示します。 マーチャントがマーケティングキャンペーンを開発する際に、オーダーステータス全体をより適切にターゲティングまたは分析できるようになります。 例えば、ある製品カテゴリのトレンドを、年の異なる時期に好調に推移している項目で見分けることができます。 例えば、寒い数ヶ月の間により良く売れる冬の服や、買い物客が長年興味を持つ特定の製品の色。 また、注文ステータスデータは、以前の注文に基づいてコンバージョンする買い物客の傾向を把握することで、全期間顧客価値の計算に役立ちます。

>[!NOTE]
>
>すべてのバックオフィスイベントには、 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) フィールドに格納されます。 このプロファイルデータを各イベントに含めることで、Adobe Commerceから別のユーザーアカウントをインポートする必要がなくなります。

### orderPlaced

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が注文したときにトリガーされます。 | `commerce.backofficeOrderPlaced` |

#### orderPlaced から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているように |
| `productListItems` | 注文の製品の配列 |
| `id` | この製品エントリの品目識別子。 製品自体は、 `product` フィールドに入力します。 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `quantity` | 買い物かご内の製品単位数 |
| `priceTotal` | 製品品目の合計価格 |
| `discountAmount` | 適用された割引額を示します |
| `order` | オーダーに関する情報が含まれます |
| `purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません |
| `priceTotal` | すべての割引と税金が適用された後の、この注文の合計価格 |
| `currencyCode` | 注文の合計に使用される ISO 4217 通貨コード |
| `purchaseOrderNumber` | 購入者がこの購入または契約に割り当てた一意の ID |
| `payments` | この注文の支払いのリスト |
| `paymentType` | この注文の支払い方法。 列挙型のカスタム値を使用できます。 |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) この支払い項目に使用される通貨コード |
| `paymentAmount` | 支払の値 |
| `taxAmount` | 最終支払いの一環として購入者が支払った税額 |
| `createdDate` | コマースシステムで新しい注文が作成された日時。 例： `2022-10-15T20:20:39+00:00` |
| `shipping` | 1 つ以上の製品の出荷詳細 |
| `shippingMethod` | 顧客が選択した送料方法（標準配送、即時配送、店頭受け取りなど） |
| `shippingAmount` | 顧客が送料を支払う必要があった金額。 |
| `address` | 物理的な配送先住所 |
| `street1` | プライマリの番地の情報、アパート番号、番地、および番地 |
| `street2` | 番地レベル情報の追加フィールド |
| `city` | 市区町村の名前 |
| `state` | 州の名前。 これは自由形式のフィールドです。 |
| `postalCode` | 場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、郵便番号の一部のみが含まれます。 |
| `country` | 政府が管理する領土の名前。 次以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。 |
| `billingAddress` | 請求先住所 |
| `street1` | プライマリの番地の情報、アパート番号、番地、および番地 |
| `street2` | 番地レベル情報の追加フィールド |
| `city` | 市区町村の名前 |
| `state` | 州の名前。 これは自由形式のフィールドです。 |
| `postalCode` | 場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、郵便番号の一部のみが含まれます。 |
| `country` | 政府が管理する領土の名前。 次以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。 |
| `personalEmail` | 個人の電子メールアドレス |
| `address` | RFC2822 以降の標準で一般的に定義される技術的なアドレス ( 例：「name@domain.com」) |

### orderItemsShipped

| 説明 | XDM イベント名 |
|---|---|
| 注文が発送されたときにトリガーされます。 | `commerce.backofficeOrderItemsShipped` |

#### orderItemsShipped から収集されたデータ

次の表に、このイベントで収集されるデータを示します。
|フィールド|説明| |—|—| |`address`|技術的な住所（例： ） `name@domain.com` RFC2822 以降の標準で一般的に定義される| |`productListItems`|注文した製品の配列| |`id`|この製品エントリの行項目識別子。 製品自体は、 `product` フィールドに入力します。| |`name`|製品の表示名または人が読み取り可能な名前| |`SKU`|在庫管理単位。 商品の一意の ID。| |`quantity`|買い物かご内の製品単位数| |`priceTotal`|商品品目の合計価格| |`discountAmount`|適用された割引額を示します| |`order`|注文に関する情報が含まれます| |`purchaseID`|販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません| |`priceTotal`|すべての割引と税金が適用された後の、この注文の合計価格| |`currencyCode`|注文の合計に使用する ISO 4217 通貨コード| |`purchaseOrderNumber`|購入者がこの購入または契約に割り当てた一意の ID| |`payments`|この注文の支払いのリスト| |`paymentType`|この注文の支払い方法。 列挙型のカスタム値を使用できます。| |`currencyCode`| [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) この支払い項目に使用する通貨コード| |`paymentAmount`|支払の値| |`lastUpdatedDate`|コマースシステムで特定の注文レコードが最後に更新された時刻| |`shipping`|1 つ以上の製品の出荷の詳細| |`shippingMethod`|顧客が選択した発送方法（標準配送、即時配送、店頭受け取りなど）| |`trackingNumber`|発送業者が注文項目の出荷に対して提供した追跡番号| |`trackingURL`|注文項目の配送状況を追跡する URL| |`shipDate`|注文の 1 つ以上の品目が発送された日付| |`address`|物理的な配送先住所| |`street1`|プライマリの番地の情報、アパート番号、番地、および番地| |`street2`|番地の情報の追加フィールド| |`city`|市区町村の名前| |`state`|州の名前。 これは自由形式のフィールドです。| |`postalCode`|場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、郵便番号の一部のみが含まれます。| |`country`|政府が管理する領土の名前。 次以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。| |`shippingAmount`|顧客が送料を支払う必要があった金額。| |`billingAddress`|請求先住所| |`street1`|プライマリの番地の情報、アパート番号、番地、および番地| |`street2`|番地の情報の追加フィールド| |`city`|市区町村の名前| |`state`|州の名前。 これは自由形式のフィールドです。| |`postalCode`|場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、郵便番号の一部のみが含まれます。| |`country`|政府が管理する領土の名前。 次以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。| |`personalEmail`|個人のメールアドレス| |`address`|技術的なアドレス (RFC2822 以降の標準で一般的に定義される&#39;name@domain.com&#39;など )|

### orderCancelled

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が注文をキャンセルした場合にトリガーされます。 | `commerce.backofficeOrderCancelled` |

#### orderCancelled から収集されたデータ

次の表に、このイベントで収集されるデータを示します。
|フィールド|説明| |—|—| |`address`|技術的な住所（例： ） `name@domain.com` RFC2822 以降の標準で一般的に定義される| |`productListItems`|注文した製品の配列| |`id`|この製品エントリの行項目識別子。 製品自体は、 `product` フィールドに入力します。| |`name`|製品の表示名または人が読み取り可能な名前| |`SKU`|在庫管理単位。 商品の一意の ID。| |`quantity`|買い物かご内の製品単位数| |`priceTotal`|商品品目の合計価格| |`discountAmount`|適用された割引額を示します| |`order`|注文に関する情報が含まれます| |`purchaseID`|販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません| |`purchaseOrderNumber`|購入者がこの購入または契約に割り当てた一意の ID| |`cancelDate`|買い物客が注文をキャンセルした日時| |`lastUpdatedDate`|コマースシステムで特定の注文レコードが最後に更新された時刻| |`personalEmail`|個人のメールアドレス| |`address`|技術的なアドレス (RFC2822 以降の標準で一般的に定義される&#39;name@domain.com&#39;など )|

### creditMemoIssued

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が注文内の項目を返した場合にトリガーされます。 | `commerce.backofficeCreditMemoIssued` |

#### creditMemoIssued から収集されたデータ

次の表に、このイベントで収集されるデータを示します。
|フィールド|説明| |—|—| |`address`|技術的な住所（例： ） `name@domain.com` RFC2822 以降の標準で一般的に定義される| |`productListItems`|注文した製品の配列| |`id`|この製品エントリの行項目識別子。 製品自体は、 `product` フィールドに入力します。| |`name`|製品の表示名または人が読み取り可能な名前| |`SKU`|在庫管理単位。 商品の一意の ID。| |`quantity`|買い物かご内の製品単位数| |`priceTotal`|商品品目の合計価格| |`discountAmount`|適用された割引額を示します| |`order`|注文に関する情報が含まれます| |`purchaseID`|販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません| |`purchaseOrderNumber`|購入者がこの購入または契約に割り当てた一意の ID| |`lastUpdatedDate`|コマースシステムで特定の注文レコードが最後に更新された時刻| |`personalEmail`|個人のメールアドレス| |`address`|技術的なアドレス (RFC2822 以降の標準で一般的に定義される&#39;name@domain.com&#39;など )|

### orderShipmentCompleted

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が注文内の項目を返した場合にトリガーされます。 | `commerce.backofficeOrderShipmentCompleted` |

#### orderShipmentCompleted から収集されたデータ

次の表に、このイベントで収集されるデータを示します。
|フィールド|説明| |—|—| |`address`|技術的な住所（例： ） `name@domain.com` RFC2822 以降の標準で一般的に定義される| |`productListItems`|注文した製品の配列| |`id`|この製品エントリの行項目識別子。 製品自体は、 `product` フィールドに入力します。| |`name`|製品の表示名または人が読み取り可能な名前| |`SKU`|在庫管理単位。 商品の一意の ID。| |`quantity`|買い物かご内の製品単位数| |`priceTotal`|商品品目の合計価格| |`discountAmount`|適用された割引額を示します| |`order`|注文に関する情報が含まれます| |`purchaseID`|販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません| |`priceTotal`|すべての割引と税金が適用された後の、この注文の合計価格| |`currencyCode`|注文の合計に使用する ISO 4217 通貨コード| |`purchaseOrderNumber`|購入者がこの購入または契約に割り当てた一意の ID| |`taxAmount`|最終支払いの一環として購入者が支払った税額。| |`createdDate`|コマースシステムで新しい注文が作成された日時。 例： `2022-10-15T20:20:39+00:00`| |`payments`|この注文の支払いのリスト| |`paymentType`|この注文の支払い方法。 列挙型のカスタム値を使用できます。| |`currencyCode`| [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) この支払い項目に使用する通貨コード| |`paymentAmount`|支払の値| |`shipping`|1 つ以上の製品の出荷の詳細| |`shippingMethod`|顧客が選択した発送方法（標準配送、即時配送、店頭受け取りなど）| |`address`|物理的な配送先住所| |`street1`|プライマリの番地の情報、アパート番号、番地、および番地| |`street2`|番地の情報の追加フィールド| |`city`|市区町村の名前| |`state`|州の名前。 これは自由形式のフィールドです。| |`postalCode`|場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、郵便番号の一部のみが含まれます。| |`country`|政府が管理する領土の名前。 次以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。| |`shippingAmount`|顧客が送料を支払う必要があった金額。| |`address`|技術的な住所（例： ） `name@domain.com` RFC2822 以降の標準で一般的に定義される| |`billingAddress`|請求先住所| |`street1`|プライマリの番地の情報、アパート番号、番地、および番地| |`street2`|番地の情報の追加フィールド| |`city`|市区町村の名前| |`state`|州の名前。 これは自由形式のフィールドです。| |`postalCode`|場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、このデータは郵便番号の一部のみを含みます。| |`country`|政府が管理する領土の名前。 次以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。| |`personalEmail`|個人のメールアドレス| |`address`|技術的なアドレス (RFC2822 以降の標準で一般的に定義される&#39;name@domain.com&#39;など )|
