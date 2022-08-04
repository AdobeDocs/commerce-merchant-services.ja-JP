---
title: 買い物客プロファイルのAdobe Experience Platformへのアップロード
description: 買い物客プロファイルをAdobe Experience Platformにアップロードする方法を説明します。
source-git-commit: 93133019f8004437ef85db32ff336bfd0e8c6fc2
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# 買い物客プロファイルをAdobe Experience Platformにアップロード

Adobe Commerceの商人が顧客プロファイルデータを [リアルタイム顧客プロファイル](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)(Adobe Experience Platformの一部 ) プロファイルを使用すると、顧客データを統合ビューに統合し、顧客とのやり取りごとに実用的なタイムスタンプ付きの説明を提供できます。

>[!NOTE]
>
> プロファイルデータには電子メールアドレスを含める必要があります。これは、買い物客とストアフロント行動データの間のリンクの作成方法です。

買い物客のプロファイルをアップロードすると、サイトでの買い物客のインタラクションに関連付けられたイベントデータがExperience Platformコネクタを通じてプロファイルに送信され、その買い物客のプロファイルにリンクされます。

>[!NOTE]
>
> この `createAccount` [storefront イベント](events.md) では、プロファイルに顧客プロファイルを自動的に作成しません。 これはセキュリティ上の理由から制限され、意図的に行われます。

このトピックでは、Adobe Commerceの顧客プロファイルを、Experience Platformでリアルタイムの顧客プロファイルにアップロードする方法を説明します。

1. 顧客データを保存する場所を決定します。 一部の商人では、このデータはAdobe Commerceに保存され、 [書き出し済み](https://docs.magento.com/user-guide/system/data-export.html) を CSV ファイルとして保存します。 その他の場合は、別の顧客関係管理 (CRM) システムに存在する可能性があります。

1. 顧客データを保存する場所を決定したら、適切な [ソースコネクタ](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en) 顧客データの保存場所に基づいて。 適切なソースコネクタが表示されない場合は、 [ローカルファイルのアップロード](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html) コネクタを使用し、CSV ファイルから買い物客プロファイルを読み込みます。

   >[!NOTE]
   >
   > ローカルファイルアップロードコネクタを使用する場合、 **プロファイルデータセット** オプション [データセットの定義](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html#use-an-existing-dataset). これにより、データセットがプロファイルデータであることが識別されます。

プロファイルで買い物客プロファイルを作成すると、その買い物客に関連付けられているすべてのストアフロントデータがその買い物客のプロファイルにリンクされます。

## 頻繁にプロファイルをアップロード

買い物客のエクスペリエンスを確実に強化するには、プロファイルデータを定期的に読み込む必要があります。 一部のソースコネクタでは、プロファイルデータをスケジュールに従ってインポートできます。
