---
title: 使用可能なデータ
description: Financial Reporting データを使用して、レポートを非コマースシステムと紐付けします。
role: User
level: Intermediate
source-git-commit: ed471f363546f1d337e85568dc5079cae4507840
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 使用可能なデータ

一部の注文および支払いデータは、外部システム間でAdobe Commerceの財務報告を調整できるように利用できます。

## ERP システムとの紐付け

特定の注文に関連付けられた増分 ID を使用して、Adobe Commerce Financial Reporting をAdobe以外の Enterprise Resource Planning(ERP) システムと紐付けできます。

支払いサービスがコマース注文を PayPal に送信すると、増分 ID が `custom_id` _および_ 内 `invoice_id` ( また、 `increment_id`) をクリックします。

ID には、支払のマーチャントアクティビティの詳細と PayPal Webhook の両方で簡単にアクセスできます。

この `invoice_id` および `custom_id` は、支払のマーチャント活動詳細の下部に表示されます。

![`custom_id` マーチャント活動詳細](assets/merchant-activity-ids.png)

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
