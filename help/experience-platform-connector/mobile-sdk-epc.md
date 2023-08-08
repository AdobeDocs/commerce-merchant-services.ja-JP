---
title: Adobe Experience Platform Mobile SDK の Commerce との統合
description: ヘッドレスまたはカスタムの Commerce ストアフロントでAdobe Experience Platform Mobile SDK を使用する方法について説明します。
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: f06020fd6bea6dbb73476f91f359987b3f61cd95
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Adobe Experience Platform Mobile SDK の Commerce との統合

>[!IMPORTANT]
>
>Adobe Experience Platform Mobile SDK for iOSは、iOS 11 以降をサポートします。

統合 [Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/documentation/) Commerce モバイルアプリを使用すると、マーチャントはコマースを送信できます。  [イベントデータ](events.md) をExperience Platformの端に

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

1. SDK を使用してコマースイベントデータをExperience Platformに送信するには、アプリケーションコードで XDM スキーマを指定する必要があります。 このスキーマは、スキーマと一致する必要があります [設定済み](https://developer.adobe.com/client-sdks/documentation/getting-started/set-up-schemas-and-datasets/) SDK のExperience Platform。

次の例は、 `web.webpagedetails.pageViews` イベントを設定し、 `identityMap` e メールフィールドを使用します。

    &quot;swift&quot;
    let stateName = &quot;luma: content: ios: us: en: home&quot;
    var xdmData: [String: Any] = [
    &quot;eventType&quot;: &quot;web.webpagedetails.pageViews&quot;,
    &quot;web&quot;: [
    &quot;webPageDetails&quot;: [
    &quot;pageViews&quot;: [
    &quot;value&quot;: 1
    ],
    &quot;name&quot;: &quot;Home page&quot;
    ]
    ]
    ]
    
    let experienceEvent = ExperienceEvent(xdm:xdmData)
    Edge.sendEvent(experienceEvent: experienceEvent)
    
    // Adobe Experience Platform - ID を更新
    emailLabel = &quot;mobileuser@example.com&quot;にします。
    
    let identityMap: IdentityMap = IdentityMap()
    identityMap.add(item: IdentityItem(id: emailLabel), withNamespace: &quot;Email&quot;)
    ID.updateIdentities(with: identityMap)
    &quot;&#39;

1. Commerce Cloud環境に接続。

   プロジェクトのビルド設定で、URL を Commerce GraphQLエンドポイントに追加します。 例：

   - デバッグ： http://_デバッグ_.commercesite.cloud/graphql/
   - リリース： http://_リリース_.commercesite.cloud/graphql/

1. Commerce GraphQLエンドポイントからデータを取得するには、まず、 [Apollo Code Generator](https://www.apollographql.com/docs/ios/).

   1. プロジェクトディレクトリから、 [install](https://www.apollographql.com/docs/ios/get-started#1-install-the-apollo-frameworks) アポロ・iOS。

   1. [初期設定](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#initialize) アポロ・コードジェン CLI

      これにより、 `apollo-codegen-configuration.json` ファイル。

   1. コンテンツを `apollo-codegen-configuration.json` ファイルには以下の情報が含まれます。

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

モバイルコマースアプリからReal-Time CDPオーディエンスを取得して、買い物かごの価格ルールと動的ブロックに情報を提供する方法については、 [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html).
