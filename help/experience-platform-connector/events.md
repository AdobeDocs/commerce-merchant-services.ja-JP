---
title: イベント
description: 各イベントが取り込むデータを説明します。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: aaaab3d11c15a69856711a41e889a5d0208aedd2
workflow-type: tm+mt
source-wordcount: '1977'
ht-degree: 0%

---

# Experience Platformコネクタイベント

次に、Commerce Connector 拡張機能をインストールする際に使用できる CommerceExperience Platformを示します。 これらのイベントで収集されたデータは、Adobe Experience Platform Edge に送信されます。 また、 [カスタムイベント](custom-events.md) 標準で提供されていない追加データを収集する場合。

以下のイベントで収集されるデータに加えて、 [その他のデータ](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) Adobe Experience Platform Web SDK によって提供されます。

>[!NOTE]
>
>すべてのストアフロントイベントには、 `personID` フィールド。人物の一意の ID です。

## addToCart

製品が買い物かごに追加されたとき、または買い物かご内の製品の数量が増加したときにトリガーされます。

### XDM イベント名

`commerce.productListAdds`

### タイプ

ストアフロント

### 収集されたデータ

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

## openCart

新しい買い物かごが作成されたとき（製品が空の買い物かごに追加されたとき）にトリガーされます。

### XDM イベント名

`commerce.productListOpens`

### タイプ

ストアフロント

### 収集されたデータ

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

## removeFromCart

製品が削除されるたびに、または買い物かご内の製品の数量が減らされるたびにトリガーされます。

### XDM イベント名

`commerce.productListRemovals`

### タイプ

ストアフロント

### 収集されたデータ

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

## shoppingCartView

買い物かごのページが読み込まれたときにトリガーされます。

### XDM イベント名

`commerce.productListViews`

### タイプ

ストアフロント

### 収集されたデータ

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

## pageView

ページが読み込まれたときにトリガーされます。

### XDM イベント名

`web.webpagedetails.pageViews`

### タイプ

ストアフロント

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `pageViews` | ページが読み込まれたかどうかを示します。 A `value` / `1` ページが読み込まれたことを示します。 |

## productPageView

製品ページが読み込まれたときにトリガーされます。

### XDM イベント名

`commerce.productViews`

### タイプ

ストアフロント

### 収集されたデータ

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

## startCheckout

買い物客がチェックアウトボタンをクリックしたときにトリガーされます。

### XDM イベント名

`commerce.checkouts`

### タイプ

ストアフロント

### 収集されたデータ

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

## completeCheckout

買い物客が注文したときにトリガーされます。

### XDM イベント名

`commerce.order`

### タイプ

ストアフロント

### 収集されたデータ

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
| `productListItems` | 買い物かごに含まれる製品の配列 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `priceTotal` | 製品品目の合計価格 |
| `quantity` | 買い物かご内の製品単位数 |
| `discountAmount` | 適用された割引額を示します |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 注文の合計に使用する通貨コード。 |
| `productImageUrl` | 製品のメイン画像 URL |
| `selectedOptions` | 設定可能な製品に使用するフィールド。 `attribute` 設定可能な製品の属性を次のように指定します。 `size` または `color` および `value` 属性の値を次のように指定します。 `small` または `black`. |

## signIn

買い物客がログインしようとしたときにトリガーされます。

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

### XDM イベント名

`userAccount.login`

### タイプ

プロファイル

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `eventType` | この時系列レコードの主なイベントタイプ。次に例を示します。 `userAccount.login` |
| `person` | 個々のアクター、連絡先、または所有者 |
| `accountID` | ユーザーアカウント ID をキャプチャします |
| `personalEmailID` | 個人用電子メールの一意の識別子を指定します |
| `address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているように |
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します |
| `login` | 訪問者がログインしようとしたかどうかを示します |

## signOut

買い物客がサインアウトを試みたときにトリガーされます。

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

### XDM イベント名

`userAccount.logout`

### タイプ

プロファイル

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `eventType` | この時系列レコードの主なイベントタイプ。次に例を示します。 `userAccount.logout` |
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します |
| `logout` | 訪問者がログアウトしようとしたかどうかを示します |

## createAccount

買い物客がアカウントを作成しようとしたときにトリガーされます。

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

### XDM イベント名

`userAccount.createProfile`

### タイプ

プロファイル

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `eventType` | この時系列レコードの主なイベントタイプ。次に例を示します。 `account.createProfile` |
| `person` | 個々のアクター、連絡先、または所有者 |
| `accountID` | ユーザーアカウント ID をキャプチャします |
| `accountType` | ユーザーアカウントタイプをキャプチャします（例： ）。 `Personal` または `Company`該当する場合は、 |
| `personalEmailID` | 個人用電子メールの一意の識別子を指定します |
| `address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているように |
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します |
| `createProfile` | ユーザーがアカウントプロファイルを作成したかどうかを示します |

## editAccount

買い物客がアカウントを編集しようとしたときにトリガーされます。

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

### XDM イベント名

`userAccount.updateProfile`

### タイプ

プロファイル

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `eventType` | この時系列レコードの主なイベントタイプ。次に例を示します。 `account.updateProfile` |
| `person` | 個々のアクター、連絡先、または所有者 |
| `accountID` | ユーザーアカウント ID をキャプチャします |
| `accountType` | ユーザーアカウントタイプをキャプチャします（例： ）。 `Personal` または `Company`該当する場合は、 |
| `personalEmailID` | 個人用電子メールの一意の識別子を指定します |
| `personalEmail` | 個人の電子メールアドレスを指定 |
| `address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているように |
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します |
| `updateProfile` | ユーザーがアカウントプロファイルを更新したかどうかを示します |

## searchRequestSent

「入力時に検索」ポップオーバーで、次のイベントによってトリガーされます。

- Enter キーを押します。
- クリック _すべて表示_

検索結果ページの次のイベントによってトリガーされます。

- フィルターを選択
- 並べ替え順を変更する (_並べ替え基準_)
- 並べ替え方向を変更（昇順または降順）
- 1 ページの結果数を変更します (_1 ページあたりの数を表示_)
- 次のページに移動します。
- 前のページに移動します。
- 別のページに移動

>[!NOTE]
>
>B2B モジュールがインストールされているAdobe Commerce Enterprise Edition では、検索イベントはサポートされていません。

### XDM イベント名

`searchRequest`

### タイプ

検索

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `searchRequest` | 検索リクエストが送信されたかどうかを示します |
| `filter` | 検索結果を制限するためにフィルターが適用されたかどうかを示します |
| `attribute` （フィルター） | 項目を検索結果に含めるかどうかを決定するために使用される項目のファセット |
| `value` | 検索結果に含まれる項目を決定するために使用される属性値 |
| `isRange` | true の場合、値は許容可能な値の範囲の終点を示します |
| `sort` | 検索結果の並べ替え方法を示します |
| `attribute` （並べ替え） | 検索結果の項目の並べ替えに使用する属性 |
| `order` | 検索結果を返す順序 |
| `query` | 検索された用語 |

## searchResponseReceived

「入力時に検索」ポップオーバーまたは検索結果ページの結果がライブ検索で返された場合にトリガーされます。

>[!NOTE]
>
>B2B モジュールがインストールされているAdobe Commerce Enterprise Edition では、検索イベントはサポートされていません。

### XDM イベント名

`searchResponse`

### タイプ

検索

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `searchResponse` | 検索応答を受信したかどうかを示します |
| `suggestions` | カタログに存在し、検索クエリに類似する製品とカテゴリの名前を含む文字列の配列。 |
| `numberOfResults` | 返された製品の数 |
| `productListItems` | 買い物かごに含まれる製品の配列。 次を含む `SKU`（在庫管理単位）及び `name` 製品の名前（表示名または人間が読み取り可能な名前）。 |
