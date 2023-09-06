---
title: 使用可能なデータ
description: Financial Reporting データを使用して、レポートを非コマースシステムと紐付けします。
role: User
level: Intermediate
exl-id: dbf41ce9-01f9-45d0-b651-e4c499e83822
feature: Payments, Checkout, Data Import/Export
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# 使用可能なデータ

一部の注文および支払いデータは、外部システム間でAdobe Commerceの財務報告を調整できるように利用できます。

## ERP システムとの紐付け

特定の注文に関連付けられた増分 ID を使用して、Adobe Commerce Financial Reporting をAdobe以外の Enterprise Resource Planning(ERP) システムと紐付けできます。

支払いサービスがコマース注文を PayPal に送信すると、増分 ID が `custom_id` _および_ （内） `invoice_id` ( また、 `increment_id`) をクリックします。

ID には、支払のマーチャントアクティビティの詳細と PayPal Webhook の両方で簡単にアクセスできます。

The `invoice_id` および `custom_id` は、支払のマーチャント活動詳細の下部に表示されます。

![`custom_id` マーチャント活動の詳細](assets/merchant-activity-ids.png){width="600" zoomable="yes"}

`custom_id` および `invoice_id` PayPal のウェブフックの詳細は次の通りです。

```json
   ...
   {
    "id": "4E855005GK253170H",
    "intent": "AUTHORIZE",
    "status": "COMPLETED",
    "payment_source": {
        ...
    },
    "purchase_units": [
        {
            ...
            "custom_id": "000001322",
            "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
            ...
            "payments": {
                "authorizations": [
                    {
                       ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ],
                "captures": [
                    {
                        ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ]
            }
        }
    ],
    "payer": {
        ...
    },
    "create_time": "2022-09-12T14:59:01Z",
    "update_time": "2022-09-12T14:59:45Z",
    "links": [
        ...
    ]
}
   ...
```

詳しくは、 PayPal の REST API に関するドキュメントを参照してください。

* [`purchase_unit`は、 `custom_id` および `invoice_id` 存在する](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit, — 折りたたみ)
* [注文の詳細を表示](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
