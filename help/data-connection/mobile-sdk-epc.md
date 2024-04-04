---
title: Adobe Experience Platform Mobile SDK の Commerce との統合
description: ヘッドレスまたはカスタムの Commerce ストアフロントでAdobe Experience Platform Mobile SDK を使用する方法について説明します。
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: d1340b15-e7de-42b5-ad64-d4c31f0db029
source-git-commit: 593e92ebf890bd7d9bfef1cd13be727ca6be172b
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Adobe Experience Platform Mobile SDK の Commerce との統合

>[!IMPORTANT]
>
>Adobe Experience Platform Mobile SDK for iOSは、iOS 11 以降をサポートします。

統合 [Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/) Commerce モバイルアプリを使用すると、マーチャントはコマースを送信できます。  [イベントデータ](events.md) をExperience Platformの端に

コマースイベントデータがエッジで使用可能な場合、他のAdobe Experience Cloudアプリケーションからアクセスできます。 例えば、データを使用してReal-Time CDPでオーディエンスを構築し、 [これらのオーディエンスを使用](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) をクリックして、Commerce モバイルアプリをパーソナライズします。

## 設定

Adobe Experience Platform Mobile SDK をコマースで使用し始めるには、Experience Platformで SDK をインストールして設定します。 次に、Commerce で設定を最終化します。

### Experience Platform

1. モバイルアプリの機能については、 [モバイルアプリでのAdobe Experience Cloudのチュートリアル](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html).

1. [インストールと設定](https://developer.adobe.com/client-sdks/documentation/getting-started/) SDK のExperience Platform。

   >[!NOTE]
   >
   >Experience Platformで作成および設定したスキーマは、Commerce モバイルアプリのアプリケーションコードで使用するスキーマと同じです。

### コマース

Experience Platform の SDK 設定を完了したら、SDK 設定を Commerce に追加します。

1. SDK を使用してコマースイベントデータをExperience Platformに送信するには、アプリケーションコードで XDM スキーマを指定する必要があります。 このスキーマは、スキーマと一致する必要があります [設定済み](https://developer.adobe.com/client-sdks/home/getting-started/set-up-schemas-and-datasets/) SDK のExperience Platform。

   次の例は、 `web.webpagedetails.pageViews` イベントを設定し、 `identityMap` e メールフィールドを使用します。

   ```swift
   let stateName = "luma: content: ios: us: en: home"
   var xdmData: [String: Any] = [
       "eventType": "web.webpagedetails.pageViews",
       "web": [
           "webPageDetails": [
               "pageViews": [
                   "value": 1
               ],
               "name": "Home page"
           ]
       ]
   ]
   
   let experienceEvent = ExperienceEvent(xdm: xdmData)
   Edge.sendEvent(experienceEvent: experienceEvent)
   
   // Adobe Experience Platform - Update Identity
   
   let emailLabel = "mobileuser@example.com"
   
   let identityMap: IdentityMap = IdentityMap()
   identityMap.add(item: IdentityItem(id: emailLabel), withNamespace: "Email")
   Identity.updateIdentities(with: identityMap)
   ```

1. Commerce Cloud環境に接続。

   プロジェクトのビルド設定で、URL を Commerce GraphQLエンドポイントに追加します。 例：

   - デバッグ： http://_デバッグ_.commercesite.cloud/graphql/
   - リリース： http://_リリース_.commercesite.cloud/graphql/

1. Commerce GraphQLエンドポイントからデータを取得するには、まず、 [Apollo Code Generator](https://www.apollographql.com/docs/ios/).

   1. プロジェクトディレクトリから、 [install](https://www.apollographql.com/docs/ios/get-started#1-install-the-apollo-frameworks) アポロ・iOS。

   1. [初期設定](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#initialize) アポロ・コードジェン CLI

      これにより、 `apollo-codegen-configuration.json` ファイル。

   1. の内容を置き換えて、必要なGraphQLファイルとディレクトリをプロジェクト内で生成します。 `apollo-codegen-configuration.json` ファイルには以下の情報が含まれます。

      ```json
      {
      "schemaName" : "MagentoAPI",
      "input" : {
          "operationSearchPaths" : [
          "**/*.graphql"
          ],
          "schemaSearchPaths" : [
          "**/*.graphqls"
          ]
      },
      "output" : {
          "testMocks" : {
          "none" : {
          }
          },
          "schemaTypes" : {
          "path" : "../MagentoAPI",
          "moduleType" : {
              "swiftPackageManager" : {
              }
          }
          },
          "operations" : {
          "inSchemaModule" : {
          }
          }
      },
      "schemaDownloadConfiguration": {
          "downloadMethod": {
              "introspection": {
                  "endpointURL": "http://magento24.com/graphql/",
                  "httpMethod": {
                      "POST": {}
                  },
                  "includeDeprecatedInputValues": false,
                  "outputFormat": "SDL"
              }
          },
          "downloadTimeout": 60,
          "headers": [],
          "outputPath": "magento.graphqls"
      }
      }
      ```

   1. [取得](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#fetch-schema) コマースGraphQLスキーマ。

      パスが `./apollo-codegen-config.json` ファイル。Commerce GraphQLスキーマへの参照を含みます。

   1. [生成](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#generate) ソースコード。

      パスが `./apollo-codegen-config.json` ファイル：必要なファイルとディレクトリを生成するための設定情報を含みます。

   1. 新しく作成された内 **GraphQLGenerated** GraphQLタイプのフォルダー、追加、編集を行います。 例えば、 `DynamicBlocks.graphql` 次の内容でタイプします。

      ```graphql
      query dynamicBlocks($input: DynamicBlocksFilterInput){
          dynamicBlocks(input: $input)
          {
              items {
                  content {
                      html
                  }
              }
          }
      }
      ```

   Adobe Experience Platform Mobile SDK を Commerce モバイルアプリと統合しました。 アプリからイベントエッジに渡されるExperience Platformデータ。

## モバイルアプリケーションから生成されたコマースイベントを区別する方法

すべて [イベント](events.md) ～と呼ばれる分野を含む `channel`. The `channel` フィールドに含む `channel._id` および `channel._type` Luma ストアフロントの場合、名前空間の値は `"https://ns.adobe.com/xdm/channels/web"` および `"https://ns.adobe.com/xdm/channel-types/web"` それぞれ。 ただし、モバイルストアフロントの場合、名前空間の値は `"https://ns.adobe.com/xdm/channels/mobile-app"` および `"https://ns.adobe.com/xdm/channel-types/mobile"` それぞれ。

## 次の手順

モバイルコマースアプリからReal-Time CDPオーディエンスを取得して、買い物かごの価格ルール、動的ブロック、関連する製品ルールに通知する方法については、 [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html#retrieve-audiences-using-the-adobe-experience-platform-mobile-sdk).
