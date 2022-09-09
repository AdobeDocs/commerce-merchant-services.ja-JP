---
title: 使用可能なデータ
description: Financial Reporting データを使用して、レポートを非コマースシステムと紐付けします。
role: User
level: Intermediate
source-git-commit: 1186b4e52f1d613332a7862c58f482c2591e29a8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# 使用可能なデータ

一部の注文および支払いデータは、外部システム間でAdobe Commerceの財務報告を調整できるように利用できます。

## ERP システムとの紐付け

特定の注文に関連付けられた増分 ID を使用して、Adobe Commerce Financial Reporting をAdobe以外の Enterprise Resource Planning(ERP) システムと紐付けできます。

支払いサービスがコマース注文を PayPal に送信すると、増分 ID が `custom_id`. この `custom_id` は、支払のマーチャントアクティビティの詳細と PayPal Webhook に表示されます。

`custom_id` 支払のマーチャント活動詳細の下部に、次の手順を実行します。

![`custom_id` マーチャント活動詳細](assets/merchant-activity.png)

`custom_id` PayPal のウェブフックの詳細は次の通りです。

```json
   ...
   },
   "seller_protection": {
   "status": "NOT_ELIGIBLE"
   },
   "create_time": "2022-08-28T21:06:53Z",
   "custom_id": "000000829",
   "supplementary_data": {
   "related_ids":

   { "authorization_id": "6WW957787A749904A", "order_id": "3SV13726F9525791J" }
   },
   ...
```

詳しくは、 PayPal の REST API に関するドキュメントを参照してください。

* [`purchase_unit` この `custom_id` 常駐](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit, — 折りたたみ)
* [注文の詳細を表示](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
