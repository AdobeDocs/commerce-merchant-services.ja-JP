---
title: プロファイルレコード
description: プロファイルレコードが取り込むデータを説明します。
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# [!DNL Data Connection] プロファイルレコード

次に、 [!DNL Data Connection] 拡張子。 プロファイルレコード内のデータがAdobe Experience Platformに送信されます。

## プロファイルレコード

プロファイルレコードの更新は、新しいプロファイルの作成、更新、または削除時にExperience Platformで利用できます。

### プロファイルレコードから収集されたデータ

次に、プロファイルレコード用に取り込まれるデータを示します。

| フィールド | 説明 |
|---|---|
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | 顧客に関する情報が含まれます。 |
| `person.name` | 顧客の名前に関する情報が含まれます。 |
| `person.name.firstName` | 顧客の名が含まれます。 |
| `person.name.lastName` | 顧客の姓が含まれます。 |
| `person.birthDate` | 買い物客の生年月日。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します。 |
| `userAccount.startDate` | プロファイルが最初に作成された日付。 |

>[!NOTE]
>
>各プロファイルレコードには、 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) フィールドに含まれます。これには、買い物客の電子メールアドレス（利用可能な場合）と ECID が含まれます。

方法を学ぶ [プロファイルレコード固有のスキーマの作成](profile-data.md) プロファイルレコードからデータを取り込むことができます。
