---
title: カスタム注文属性の追加
description: バックオフィスデータにカスタム注文属性を追加し、それらの属性をExperience Platformに送信する方法を説明します。
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 14d190726324e2f42d66c2270f2e27be5a74132f
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 2%

---

# カスタム注文属性の追加

この記事では、バックオフィスイベントにカスタム属性を追加する方法について説明します。 カスタム属性を使用すると、豊富なデータインサイトを取得して分析を強化し、買い物客向けにパーソナライズされたエクスペリエンスをさらに作成できます。

カスタム属性は、次の 2 つのレベルでサポートされます。

- 注文レベル
- 注文品目レベル

>[!NOTE]
>
>Adobe [!DNL Commerce] は、文字列、ブール値、日付のデータタイプを持つカスタム属性をサポートしています。

バックオフィスイベントにカスタム属性を追加するには、次の操作が必要です。

1. [!DNL Commerce] インストールにプロジェクトを作成します。
1. 新しいカスタム属性をExperience Platformに適切に取り込めるように、スキーマを更新します。
1. 管理者で、カスタム属性が取り込まれてExperience Platformに送信されていることを確認します。

>[!IMPORTANT]
>
>以下のディレクトリ構造とコードサンプルは、カスタム属性を実装する方法を示しています。 実際に必要なディレクトリ構造とコードは、ストアの設定と環境によって異なります。

## 手順 1：ディレクトリ構造の作成

1. [!DNL Commerce] インストールの `app/code` ディレクトリに移動し、モジュールディレクトリを作成します。 例：`Magento/AepCustomAttributes`。 このディレクトリには、カスタム アトリビュートに必要なファイルが含まれています。
1. モジュールディレクトリに、`etc` というサブディレクトリを作成します。 `etc` ディレクトリには、`module.xml`、`query.xml`、`di.xml` および `et_schema.xml` ファイルが含まれます。

## 手順 2：依存関係とセットアップバージョンを定義する

依存関係とセットアップバージョンを定義する `module.xml` ファイルを作成します。 例：

```xml
<?xml version="1.0"?>
<!--
/**
* Copyright (c) [year], [name]. All rights reserved.
*/
-->
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="Magento_SalesRuleStaging" setup_version="2.0.0">
        <sequence>
            <module name="Magento_Staging"/>
            <module name="Magento_SalesRule"/>
        </sequence>
    </module>
</config>
```

## 手順 3：受注データの取得

受注データを取得する `query.xml` ファイルを作成します。 例：

```xml
<query>
    <source name="sales_order" type="sales">
        <attribute name="increment_id" operator="eq" alias="order_increment_id"/>
        <link source="inventory_source_item" condition_type="by_sku"/>
    </source>
</query>
```

## 手順 4：依存関係の挿入を設定する

依存関係の挿入を設定する `di.xml` ファイルを作成します。 例：

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="com.example.instrumentedtest"
          android:versionCode="1"
          android:versionName="1.0">
    <uses-sdk android:minSdkVersion="8" android:targetSdkVersion="15"/>
    
    <instrumentation
        android:name=".MyInstrumentationTestRunner"
        android:targetPackage="com.example.instrumentedtest"/>
    
    <!-- More instrumentation elements might be here -->
</manifest>
```

## 手順 5：依存関係の挿入に使用するサービスを定義する

依存関係の挿入に使用するサービスを定義する `et_schema.xml` ファイルを作成します。 例：

```xml
<services>
    <service id="App\Controller\MainController" class="App\Controller\MainController">
        <argument type="service" id="doctrine.orm.default_entity_manager"/>
        <argument type="service" id="form.factory"/>
        <argument type="service" id="security.authorization_checker"/>
    </service>

    <!-- ... -->

    <service id="App\Controller\SecurityController" class="App\Controller\SecurityController">
        <argument type="service" id="security.authentication_utils"/>
        <tag name="controller.service_arguments"/>
    </service>

    <!-- ... -->
</services>
```

## 手順 6:PHP ファイル用のディレクトリの作成

`etc` ディレクトリと同じレベルに、`Module/Provider` という名前のディレクトリを作成します。 このディレクトリには、`OrderCustomAttributes` および `OrderItemCustomAttributes` の PHP ファイルが含まれています。

## 手順 7:OrderCustomAttributes の定義

順序のカスタム属性を定義する `OrderCustomAttributes.php` ファイルを作成します。 例：

```php
namespace App\Transformers;

use League\Fractal\TransformerAbstract;
use Illuminate\Support\Collection;

class CustomAttributeTransformer extends TransformerAbstract
{
    protected $availableIncludes = [];
    protected $defaultIncludes = [];

    public function __construct($signsField, $jsonSignsField = null)
    {
        $this->signsField = $signsField;
        $this->jsonSignsField = $jsonSignsField;
    }

    public function transform(Collection $collection)
    {
        // Initialize array for additional information.
        $additionalInformation = [];

        // Source - this comes from values sent to this transformer.
        foreach ($collection->{$this->signsField} ?: [] as $value) {
            if (is_array($value)) {
                // If value is an array, serialize it.
                foreach ($value as &$item) {
                    if (isset($item['custom_attr'])) {
                        // Serialize custom attribute data.
                        ...
                    }
                }
            } else {
                // Add non-array values directly.
                ...
            }
        }

        ...

        return [
            'current' => ...,
            'additional_information' => ...,
            'source' => ...,
        ];
    }

    private function flatten(array $values)
    {
      return Arr::flatten($values);
  }
}
```

## 手順 8: OrderItemCustomAttributes の定義

注文項目のカスタム属性を定義する `OrderItemCustomAttributes.php` ファイルを作成します。 例：

```php
namespace Magento\AepCustomAttributes\Model\Provider;

use Magento\Framework\Serialize\Serializer\Json;

class OrderItemCustomAttribute
{
    private Json $jsonSerializer;
    private string $usingField;

    public function __construct(Json $jsonSerializer, string $usingField)
    {
        $this->jsonSerializer = $jsonSerializer;
        $this->usingField = $usingField;
    }

    public function get(array $values): array
    {
        $output = [];
        $values = $this->flatten($values);

        foreach ($values as $row) {
            $info = \is_string($row['additionalInformation']) ? $row['additionalInformation'] : '{}';
            $unserializedData = $this->jsonSerializer->unserialize($info) ?? [];

            $attrLabel = implode(',', ['label1', 'label2']);
            $unserializedData['custom_attr1'] = $attrLabel;

            $additionalInformation = [];
            foreach ($unserializedData as $name => $value) {
                $additionalInformation[] = [
                    'name' => $name,
                    'value' => \is_string($value) ? $value : $this->jsonSerializer->serialize($value),
                ];
            }

            foreach ($additionalInformation as $information) {
                $output[] = [
                    'additionalInformation' => $information,
                    $this->usingField => $row[$this->usingField],
                ];
            }
        }

        return $output;
    }

    private function flatten(array $values): array
    {
        return array_merge([], ...array_values($values));
    }
}
```

## 手順 9:productContext ファイルのディレクトリの作成

`etc` ディレクトリと同じレベルに、`Plugin/Module` という名前のディレクトリを作成します。 このディレクトリには `ProductContext.php` ファイルが含まれています。

## 手順 10:ProductContext クラスの定義

`ProductContext` クラスを定義する `ProductContext.php` というファイルを作成します。 例：

```php
namespace Magento\Catalog\Model\Product;

use Magento\Framework\App\ResourceConnection;
use Magento\Quote\Api\Data\CartInterface;

class ProductContext
{
    private $brandCache = [];
    private $resourceConnection;

    public function __construct(
        ResourceConnection $resourceConnection
    ) {
        $this->resourceConnection = $resourceConnection;
    }

    public function afterGetProductData($subject, array $result)
    {
        if (isset($result['brand_id'])) {
            if (!isset($this->brandCache[$result['brand_id']])) {
                // @todo load brand label by brand id.
                $this->brandCache[$result['brand_id']] = 'Brand Label ' . $result['brand_id'];
            }
            $result['brands'] = ['label' => $this->brandCache[$result['brand_id']]];
        }

        return $result;
    }
}
```

## 手順 11：モジュールを登録

`etc` ディレクトリと同じレベルで、モジュールを登録する `registration.php` ファイルを作成します。 例：

```php
use \Magento\Framework\Component\ComponentRegistrar;

ComponentRegistrar::register(
    ComponentRegistrar::MODULE,
    'Dfe_Stripe',
    __DIR__
);
```

## 手順 12：既存の XDM スキーマを拡張する

新しいカスタム注文属性をExperience Platformの [!DNL Commerce] スキーマで確実に取り込めるようにするには、スキーマを拡張してこれらのカスタムフィールドを含める必要があります。

既存の XDM スキーマを拡張してこれらのカスタムフィールドを含める方法については、Experience Platformドキュメントの [UI でのスキーマの作成と編集 ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas#custom-fields-for-standard-groups) の記事を参照してください。 テナント ID フィールドは動的に生成されますが、フィールド構造はExperience Platformドキュメントで提供されている例に類似している必要があります。

>[!IMPORTANT]
>
>XDM カスタム属性は、[!DNL Commerce] から送信された属性と一致する必要があります。

`commerce.order` に、注文レベルのフィールドを追加します。

![ 注文レベル ](assets/order-level.png)

`productListItems` に、注文項目レベルのフィールドを追加します。

![ 注文品目レベル ](assets/order-item-level.png)

## 手順 12：データがキャプチャされていることを確認する

管理者の「[ データのカスタマイズ ](connect-data.md#data-customization)」タブを表示し、カスタム属性データがキャプチャされてExperience Platformに送信されていることを確認します。

### トラブルシューティング

「**[!UICONTROL Data Customization]**」タブにメッセージ `No custom order attributes found.` が表示された場合は、次の確認を行ってください。

1. [ データコネクタ拡張機能 ](overview.md#prerequisites) を有効にするための前提条件は完了しています。
1. [ カスタム注文属性 ](#add-custom-order-attributes) を設定しました。
1. 1 つ以上の注文イベントが生成されています。
