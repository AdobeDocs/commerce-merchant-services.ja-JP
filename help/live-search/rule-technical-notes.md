---
title: ルールのテクニカルノート
description: ライブ検索ルールの使用に関するテクニカルノート。
exl-id: 24ff6a19-f7cd-42f7-b466-fc18f9091504
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# ルールのテクニカルノート

[!DNL Live Search] ルールトリガーのアクションは、様々なクエリ条件に基づいておこなわれ、マーチャントが様々なシナリオでの検索エクスペリエンスを形成できます。

の現在のリリース [!DNL Live Search] ルールは、返された結果のセットではなく、買い物客が入力したクエリ文字列に基づいています。 クエリ文字列には英数字を含めることができ、大文字と小文字は無視されます。 ファセットやシノニムと同様に、ルールは `protobuf dynamo`. クエリ時に、検索サービスは `grpc` への呼び出し `search-admin-service`.
