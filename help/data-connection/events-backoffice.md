---
title: バックオフィスイベント
description: 各バックオフィスイベントがキャプチャするデータを説明します。
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: a5a4f04b-89ac-4020-95ce-984f9f2d8385
source-git-commit: 0ab1b4b23d25bee722b35fbc8b9717ad6d1c299e
workflow-type: tm+mt
source-wordcount: '3571'
ht-degree: 0%

---

# [!DNL Data Connection] バックオフィスイベント

次のリストは、 [!DNL Data Connection] 拡張子。 これらのイベントで収集されたデータは、Adobe Experience Platformに送信されます。 また、 [カスタムイベント](custom-events.md) 標準で提供されていない追加データを収集する場合。

以下のイベントで収集されるデータに加えて、 [その他のデータ](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) Adobe Experience Platform Web SDK によって提供されます。

バックオフィスのイベントには、サーバー側のデータが含まれます。 このデータは、 [注文ステータス](#order-status) 注文が行われたか、取り消されたか、返金されたか、発送されたか、完了したかなどの情報。 サーバー側のデータには、 [顧客プロファイルイベント](#customer-profile-events) アカウントが作成、更新、削除された場合などの情報。

>[!NOTE]
>
>すべてのバックオフィスイベントには、 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) フィールドに含まれます。これには、買い物客の電子メールアドレス（利用可能な場合）と ECID が含まれます。

## 注文ステータス

注文ステータスデータは、買い物客の注文の 360 ビューを表示します。 マーチャントがマーケティングキャンペーンを開発する際に、オーダーステータス全体をより適切にターゲティングまたは分析できるようになります。 例えば、ある製品カテゴリの傾向を、年の異なる時期に好調に推移している項目で見分けることができます。 例えば、寒い数ヶ月の間により良く売れる冬の服や、買い物客が長年興味を持つ特定の製品の色。 また、注文ステータスデータは、以前の注文に基づいてコンバージョンする買い物客の傾向を把握することで、全期間顧客価値の計算に役立ちます。

### orderPlaced

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が注文したときにトリガーされます。 | `commerce.backofficeOrderPlaced` |

#### orderPlaced から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.payments` | この注文の支払いのリスト。 |
| `commerce.order.payments.paymentTransactionID` | この支払トランザクションの一意の ID。 |
| `commerce.order.payments.paymentAmount` | 支払の値。 |
| `commerce.order.payments.paymentType` | この注文の支払い方法。 カウント済み、カスタム値を使用可能 |
| `commerce.order.payments.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `commerce.order.taxAmount` | 最終支払いの一環として購入者が支払った税額。 |
| `commerce.order.discountAmount` | 注文全体に適用される割引額を示します。 |
| `commerce.order.createdDate` | コマースシステムで新しい注文が作成された日時。 例： `2022-10-15T20:20:39+00:00`. |
| `commerce.order.currencyCode` | 注文の合計に使用される ISO 4217 通貨コード。 |
| `commerce.shipping` | 1 つ以上の製品の出荷の詳細。 |
| `commerce.shipping.shippingMethod` | 顧客が選択した送料方法（標準配送、即時配送、店頭受け取りなど）。 |
| `commerce.shipping.shippingAmount` | 顧客が送料を支払う必要があった金額。 |
| `commerce.shipping.currencyCode` | 送料合計に使用する ISO 4217 通貨コード。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `commerce.billing.address` | 請求先住所。 |
| `commerce.billing.address.street1` | プライマリの番地の情報、アパート番号、番地、および番地 |
| `commerce.billing.address.street2` | 番地レベル情報の追加フィールド。 |
| `commerce.billing.address.city` | 市区町村の名前。 |
| `commerce.billing.address.state` | 州の名前。 これは自由形式のフィールドです。 |
| `commerce.billing.address.postalCode` | 場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、郵便番号の一部のみが含まれます。 |
| `commerce.billing.address.country` | 政府が管理する領土の名前。 次の値以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `productListItems` | 注文内の製品の配列。 |
| `productListItems.id` | この製品エントリの品目識別子。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |
| `productListItems.categories` | 製品のカテゴリに関する情報が含まれます。 |
| `productListItems.categories.id` | カテゴリの一意の ID。 |
| `productListItems.categories.name` | カテゴリの名前。 |
| `productListItems.categories.path` | カテゴリへのパス。 |
| `productListItems.productImageUrl` | 商品のメイン画像 URL。 |

### orderInvoiled

| 説明 | XDM イベント名 |
|---|---|
| 商人が請求書を送信して支払を要求する際にトリガーされます。 | `commerce.backofficeOrderInvoiced` |

#### orderInviled から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.priceTotal` | すべての割引と税金が適用された後の、この注文の合計価格。 |
| `commerce.order.currencyCode` | 注文の合計に使用される ISO 4217 通貨コード。 |
| `commerce.order.purchaseOrderNumber` | 購入者がこの購入または契約に割り当てた一意の ID。 |
| `commerce.order.payments` | この注文の支払いのリスト。 |
| `commerce.order.payments.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `commerce.order.payments.paymentType` | この注文の支払い方法。 カウント済み、カスタム値を使用可能 |
| `commerce.order.payments.paymentAmount` | 支払の値。 |
| `commerce.shipping` | 1 つ以上の製品の出荷の詳細。 |
| `commerce.shipping.shippingMethod` | 顧客が選択した送料方法（標準配送、即時配送、店頭受け取りなど）。 |
| `commerce.shipping.shippingAmount` | 顧客が送料を支払う必要があった金額。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `productListItems` | 注文内の製品の配列。 |
| `productListItems.id` | この製品エントリの品目識別子。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.categories` | 製品のカテゴリに関する情報が含まれます。 |
| `productListItems.categories.id` | カテゴリの一意の ID。 |
| `productListItems.categories.name` | カテゴリの名前。 |
| `productListItems.categories.path` | カテゴリへのパス。 |

### orderItemsShipped

| 説明 | XDM イベント名 |
|---|---|
| 注文が発送されたときにトリガーされます。 | `commerce.backofficeOrderItemsShipped` |

#### orderItemsShipped から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.payments` | この注文の支払いのリスト。 |
| `commerce.order.payments.paymentTransactionID` | この支払トランザクションの一意の ID。 |
| `commerce.order.payments.paymentAmount` | 支払の値。 |
| `commerce.order.payments.paymentType` | この注文の支払い方法。 カウント済み、カスタム値を使用可能 |
| `commerce.order.payments.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `commerce.order.priceTotal` | すべての割引と税金が適用された後の、この注文の合計価格。 |
| `commerce.order.purchaseOrderNumber` | 購入者がこの購入または契約に割り当てた一意の ID。 |
| `commerce.order.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `commerce.order.lastUpdatedDate` | コマースシステムで特定の注文レコードが最後に更新された時刻。 |
| `commerce.shipping` | 1 つ以上の製品の出荷の詳細。 |
| `commerce.shipping.shippingMethod` | 顧客が選択した送料方法（標準配送、即時配送、店頭受け取りなど）。 |
| `commerce.shipping.shippingAmount` | 顧客が送料を支払う必要があった金額。 |
| `commerce.shipping.address` | 実際の配送先住所。 |
| `commerce.shipping.address.street1` | プライマリの番地の情報、アパート番号、番地、および番地。 |
| `commerce.shipping.address.street2` | 2 行目（オプション） |
| `commerce.shipping.address.city` | 市区町村の名前。 |
| `commerce.shipping.address.state` | 都道府県の名前。 これは自由形式のフィールドです。 |
| `commerce.shipping.address.postalCode` | 場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、郵便番号の一部のみが含まれます。 |
| `commerce.shipping.address.country` | 政府が管理する領土の名前。 次の値以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。 |
| `commerce.shipping.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `commerce.shipping.trackingNumber` | 発注品目の出荷に対して出荷業者が提供する追跡番号。 |
| `commerce.shipping.trackingURL` | 注文項目の発送ステータスを追跡する URL。 |
| `commerce.shipping.shipDate` | 1 つ以上の注文品が出荷された日付。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `commerce.billing.address` | 請求先住所。 |
| `commerce.billing.address.street1` | プライマリの番地の情報、アパート番号、番地、および番地 |
| `commerce.billing.address.street2` | 番地レベル情報の追加フィールド。 |
| `commerce.billing.address.city` | 市区町村の名前。 |
| `commerce.billing.address.state` | 州の名前。 これは自由形式のフィールドです。 |
| `commerce.billing.address.postalCode` | 場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、郵便番号の一部のみが含まれます。 |
| `commerce.billing.address.country` | 政府が管理する領土の名前。 次の値以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `productListItems` | 注文内の製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |
| `productListItems.categories` | 製品のカテゴリに関する情報が含まれます。 |
| `productListItems.categories.id` | カテゴリの一意の ID。 |
| `productListItems.categories.name` | カテゴリの名前。 |
| `productListItems.categories.path` | カテゴリへのパス。 |

### orderCancelled

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が注文をキャンセルした場合にトリガーされます。 | `commerce.backofficeOrderCancelled` |

#### orderCancelled から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.purchaseOrderNumber` | 購入者がこの購入または契約に割り当てた一意の ID。 |
| `commerce.order.cancelDate` | 買い物客が注文をキャンセルした日時。 |
| `commerce.order.lastUpdatedDate` | コマースシステムで特定の注文レコードが最後に更新された時刻。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |

### orderLineItemRefunded

| 説明 | XDM イベント名 |
|---|---|
| 返された品目に対して買い物客が払い戻された場合にトリガーされます。 | `commerce.backofficeCreditMemoIssued` |

#### orderLineItemRefunded から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.lastUpdatedDate` | コマースシステムで特定の注文レコードが最後に更新された時刻。 |
| `commerce.order.purchaseOrderNumber` | 購入者がこの購入または契約に割り当てた一意の ID。 |
| `commerce.refunds` | この注文の返金のリスト。 |
| `commerce.refunds.transactionID` | この返金の一意の ID。 |
| `commerce.refunds.refundAmount` | 払い戻しの値。 |
| `commerce.refunds.refundPaymentType` | この注文の支払い方法。 カウント済み、カスタム値を使用可能 |
| `commerce.refunds.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `productListItems` | 注文内の製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |
| `productListItems.categories` | 製品のカテゴリに関する情報が含まれます。 |
| `productListItems.categories.id` | カテゴリの一意の ID。 |
| `productListItems.categories.name` | カテゴリの名前。 |
| `productListItems.categories.path` | カテゴリへのパス。 |

### orderItemsReturnInitiated

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が品目の返却をリクエストした場合にトリガーされます。 | `commerce.backofficeOrderItemsReturnInitiated` |

#### orderItemsReturnInitiated から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.returns` | この受注の RMA(Return Murchandise Authorization) 情報。 |
| `commerce.order.returns.returnID` | この RMA の一意の ID(Return Murchandise Authorization)。 |
| `commerce.order.returns.returnStatus` | RMA のステータス (Return Murchandise Authorization)。保留、クローズなど。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `productListItems` | 注文内の製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |
| `productListItems.categories` | 製品のカテゴリに関する情報が含まれます。 |
| `productListItems.categories.id` | カテゴリの一意の ID。 |
| `productListItems.categories.name` | カテゴリの名前。 |
| `productListItems.categories.path` | カテゴリへのパス。 |
| `productListItems.returnItem` | この品目の RMA(Return Murchandise Authorization) 情報。 |
| `productListItems.returnItem.returnStatus` | 返される項目のステータス（保留中、承認済みなど）。 |
| `productListItems.returnItem.returnReason` | この項目の返品が要求された理由。 |
| `productListItems.returnItem.returnItemCondition` | 返品が要求された品目の条件。 |
| `productListItems.returnItem.returnResolution` | 返金、交換など、返品されるアイテムの要求された解決。 |
| `productListItems.returnItem.returnQuantityRequested` | 買い物客が返すように要求したこの項目の数。 |
| `productListItems.returnItem.returnQuantityAuthorized` | 返却を許可されたこの項目の数。 |
| `productListItems.returnItem.eturnQuantityReceived` | 返された項目の数。 |
| `productListItems.returnItem.returnQuantityApproved` | 完全に完了し、承認されたこの項目の数。 |

### orderItemReturnCompleted

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が返品をリクエストした品目が完了したときにトリガーされます。 | `commerce.backofficeOrderItemsReturnCompleted` |

#### orderItemReturnCompleted から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.returns` | この受注の RMA(Return Murchandise Authorization) 情報。 |
| `commerce.order.returns.returnID` | この RMA の一意の ID(Return Murchandise Authorization)。 |
| `commerce.order.returns.returnStatus` | RMA のステータス (Return Murchandise Authorization)。保留、クローズなど。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `productListItems` | 注文内の製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |
| `productListItems.categories` | 製品のカテゴリに関する情報が含まれます。 |
| `productListItems.categories.id` | カテゴリの一意の ID。 |
| `productListItems.categories.name` | カテゴリの名前。 |
| `productListItems.categories.path` | カテゴリへのパス。 |
| `productListItems.returnItem` | この品目の RMA(Return Murchandise Authorization) 情報。 |
| `productListItems.returnItem.returnStatus` | 返される項目のステータス（保留中、承認済みなど）。 |
| `productListItems.returnItem.returnReason` | この項目の返品が要求された理由。 |
| `productListItems.returnItem.returnItemCondition` | 返品が要求された品目の条件。 |
| `productListItems.returnItem.returnResolution` | 返金、交換など、返品されるアイテムの要求された解決。 |
| `productListItems.returnItem.returnQuantityRequested` | 買い物客が返すように要求したこの項目の数。 |
| `productListItems.returnItem.returnQuantityAuthorized` | 返却を許可されたこの項目の数。 |
| `productListItems.returnItem.eturnQuantityReceived` | 返された項目の数。 |
| `productListItems.returnItem.returnQuantityApproved` | 完全に完了し、承認されたこの項目の数。 |

### orderShipmentCompleted

| 説明 | XDM イベント名 |
|---|---|
| 出荷が完了したときにトリガーされます。 | `commerce.backofficeOrderShipmentCompleted` |

#### orderShipmentCompleted から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.payments` | この注文の支払いのリスト。 |
| `commerce.order.payments.paymentTransactionID` | この支払トランザクションの一意の ID。 |
| `commerce.order.payments.paymentAmount` | 支払の値。 |
| `commerce.order.payments.paymentType` | この注文の支払い方法。 カウント済み、カスタム値を使用可能 |
| `commerce.order.payments.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `commerce.order.taxAmount` | 最終支払いの一環として購入者が支払った税額。 |
| `commerce.order.createdDate` | コマースシステムで新しい注文が作成された日時。 例： `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | 1 つ以上の製品の出荷の詳細。 |
| `commerce.shipping.shippingMethod` | 顧客が選択した送料方法（標準配送、即時配送、店頭受け取りなど）。 |
| `commerce.shipping.shippingAmount` | 顧客が送料を支払う必要があった金額。 |
| `commerce.shipping.shipDate` | 1 つ以上の注文品が出荷された日付。 |
| `commerce.shipping.address` | 実際の配送先住所。 |
| `commerce.shipping.address.street1` | プライマリの番地の情報、アパート番号、番地、および番地。 |
| `commerce.shipping.address.street2` | 2 行目（オプション） |
| `commerce.shipping.address.city` | 市区町村の名前。 |
| `commerce.shipping.address.state` | 都道府県の名前。 これは自由形式のフィールドです。 |
| `commerce.shipping.address.postalCode` | 場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、郵便番号の一部のみが含まれます。 |
| `commerce.shipping.address.country` | 政府が管理する領土の名前。 次の値以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。 |
| `commerce.billing.address` | 請求先住所。 |
| `commerce.billing.address.street1` | プライマリの番地の情報、アパート番号、番地、および番地 |
| `commerce.billing.address.street2` | 番地レベル情報の追加フィールド。 |
| `commerce.billing.address.city` | 市区町村の名前。 |
| `commerce.billing.address.state` | 州の名前。 これは自由形式のフィールドです。 |
| `commerce.billing.address.postalCode` | 場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、郵便番号の一部のみが含まれます。 |
| `commerce.billing.address.country` | 政府が管理する領土の名前。 次の値以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `productListItems` | 注文内の製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |
| `productListItems.categories` | 製品のカテゴリに関する情報が含まれます。 |
| `productListItems.categories.id` | カテゴリの一意の ID。 |
| `productListItems.categories.name` | カテゴリの名前。 |
| `productListItems.categories.path` | カテゴリへのパス。 |

## 顧客プロファイルイベント

サーバー側からキャプチャされるプロファイルイベントには、次のようなアカウント情報が含まれます。 `accountCreated`, `accountUpdated`、および `accountDeleted`. このデータは、セグメントをより適切に定義したり、新規登録の割引オファーの送信や、アカウントの変更確認など、マーケティングキャンペーンを実行するために必要な顧客の主要な詳細情報を入力するのに役立ちます。 次からキャプチャされた類似のプロファイルイベントがあります： [店頭の](events.md#customer-profile-events).

### accountCreated

| 説明 | XDM イベント名 |
|---|---|
| 買い物客がアカウントを作成しようとしたときにトリガーされます。 | `userAccount.backofficeCreateProfile` |

#### accountCreated から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `person` | 顧客に関する情報が含まれます。 |
| `person.name` | 顧客の名前に関する情報が含まれます。 |
| `person.name.firstName` | 顧客の名が含まれます。 |
| `person.name.lastName` | 顧客の姓が含まれます。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |

### accountUpdated

| 説明 | XDM イベント名 |
|---|---|
| 買い物客がアカウントを編集しようとしたときにトリガーされます。 | `userAccount.backofficeUpdateProfile` |

#### accountUpdated から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `person` | 顧客に関する情報が含まれます。 |
| `person.name` | 顧客の名前に関する情報が含まれます。 |
| `person.name.firstName` | 顧客の名が含まれます。 |
| `person.name.lastName` | 顧客の姓が含まれます。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |

### accountDeleted

| 説明 | XDM イベント名 |
|---|---|
| 買い物客がアカウントを削除しようとした場合にトリガーされます。 | `userAccount.backofficeDeleteProfile` |

#### accountDeleted から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `person` | 顧客に関する情報が含まれます。 |
| `person.name` | 顧客の名前に関する情報が含まれます。 |
| `person.name.firstName` | 顧客の名が含まれます。 |
| `person.name.lastName` | 顧客の姓が含まれます。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
