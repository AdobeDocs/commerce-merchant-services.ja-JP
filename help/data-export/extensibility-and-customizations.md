---
title: SaaS データ書き出しフィードデータの拡張とカスタマイズ
description: フィードデータを拡張してカスタマイズする方法  [!DNL SaaS Data Export]  説明します。
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 51238f86f36a756b86d07bdf6bb0a5cf0c61cbeb
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# SaaS データ書き出しフィードデータの拡張とカスタマイズ

[!DNL Commerce Data Export] 拡張機能を使用すると、[!DNL Commerce] アプリケーションからCommerce サービス（Live Search、カタログサービス、Product Recommendationsなど）にデータを書き出すことができます。 必要に応じて、フィードデータを拡張およびカスタマイズして追加のデータを含めたり、`Magento\CatalogDataExporter` モジュールを更新して収集したデータを変更したりできます。

>[!NOTE]
>
>フィードに新しいデータを追加したり、既存のデータを変更したりすると、フィード収集のパフォーマンスに影響を与え、Adobe Commerce側の処理ロジックに問題が生じる可能性があります。 実稼動環境に結合する前に、カスタマイズされたコードをテストしてください。

## 製品フィードでの属性データの拡張

製品フィードには、製品の処理に必要な、または消費者によって一般的に使用されるデフォルトの属性が含まれています。 製品フィードに追加することで、製品フィードに追加のシステム属性を含めることができます。

このタスクを完了するには、`magento/catalog-data-exporter` モジュールを更新して、追加のシステム属性を [ 依存関係インジェクション設定ファイル ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) （`di.xml`）に追加します。 製品属性クエリ（`Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery`）に属性を追加します。

**例**

```xml
    <type name="Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery">
        <arguments>
            <argument name="systemAttributes" xsi:type="array">
                <item name="news_from_date" xsi:type="string">news_from_date</item>
                ...
                <item name="some_system_attribute_code">some_system_attribute_code</item>
            </argument>
        </arguments>
    </type>
```
