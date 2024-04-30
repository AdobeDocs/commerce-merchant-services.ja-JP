---
title: プロファイルレコード
description: プロファイルレコードが取得するデータを説明します。
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: bd04730d-e37a-48a9-822b-0f4aa68a4651
source-git-commit: 89607d22ba8e69e0c98fce97e041022e33d01c07
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# [!DNL Data Connection] プロファイルレコード（ベータ版）

以下は、のインストール時に利用できるCommerce プロファイルレコードデータを説明しています [!DNL Data Connection] 拡張機能。 プロファイルレコードのデータはAdobe Experience Platformに送信されます。

## プロファイルレコード

プロファイルレコードの更新は、新しいプロファイルを作成、更新または削除すると、Experience Platformで利用できます。

### プロファイルレコードから収集されたデータ

次に、プロファイルレコードに対して取り込まれるデータを示します。

| フィールド | 説明 |
|---|---|
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` contain [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例：） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | 次のようなチャネルデータのソースを識別します `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | 顧客に関する情報が含まれます。 |
| `person.name` | 顧客の名前に関する情報が含まれます。 |
| `person.name.firstName` | 顧客の名が含まれます。 |
| `person.name.lastName` | 顧客の姓が含まれます。 |
| `person.birthDate` | 買い物客の生年月日。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的アドレス（例：） `name@domain.com` rfc2822 および後続の標準で一般的に定義されている通り。 |
| `billingAddress` | 請求先住所。 |
| `billingAddress.street1` | プライマリの番地レベルの情報、アパート番号、通り番号、通り名。 |
| `billingAddress.street2` | オプションの住所情報 2 行目。 |
| `billingAddress.city` | 市区町村の名前。 |
| `billingAddress.state` | 州の名前。 これは自由形式フィールドです。 |
| `billingAddress.country` | 政府が管理する領土の名前。 次の以外： `xdm:countryCode`これは、任意の言語で国名を持つことができる自由形式フィールドです。 |
| `billingAddressPhone` | 請求先住所に関連付けられた電話番号。 |
| `billingAddressPhone.number` | 電話番号。 電話番号は文字列で、意味のある文字（角括弧など）を含めることができます `()`, ハイフン `-`、または内線などのサブダイヤル識別子を示す文字 `x` 例：  `1-353(0)18391111` または `+613 9403600x1234`. |
| `shippingAddress` | 配送先住所。 |
| `shippingAddress.street1` | プライマリの番地レベルの情報、アパート番号、通り番号、通り名。 |
| `shippingAddress.street2` | オプションの住所情報 2 行目。 |
| `shippingAddress.city` | 市区町村の名前。 |
| `shippingAddress.state` | 州の名前。 これは自由形式フィールドです。 |
| `shippingAddress.country` | 政府が管理する領土の名前。 次の以外： `xdm:countryCode`これは、任意の言語で国名を持つことができる自由形式フィールドです。 |
| `shippingAddressPhone` | 配送先住所に関連付けられている電話番号。 |
| `shippingAddressPhone.number` | 電話番号。 電話番号は文字列で、意味のある文字（角括弧など）を含めることができます `()`, ハイフン `-`、または内線などのサブダイヤル識別子を示す文字 `x` 例：  `1-353(0)18391111` または `+613 9403600x1234`. |
| `userAccount` | ロイヤルティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します。 |
| `userAccount.startDate` | プロファイルが最初に作成された日付。 |

>[!NOTE]
>
>各プロファイルレコードには、 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) フィールド。プロファイルのプライマリ識別子としてシステムが生成したCommerce顧客 ID と、セカンダリ識別子として使用されるメール ID が含まれます。

方法を学ぶ [プロファイルレコード固有のスキーマの作成](profile-data.md) これにより、プロファイルレコードからデータを取り込むことができます。
