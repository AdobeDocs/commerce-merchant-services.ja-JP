---
title: Cookie 制限の処理
description: 製品レコメンデーションでの cookie 制限の処理方法について説明します。
source-git-commit: 81ab2e22b0ec81e97d27ee135c88b50731a3986d
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# Cookie 制限の処理

Adobe CommerceとMagento Open Sourceは、両方とも、データをブラウザーの Cookie に保存する前に同意を求めます。 詳しくは、 [Cookie 制限モード](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html).

をデプロイする際に、 `magento/product-recommendations` モジュールから実稼動環境へと移行すると、ストアフロントで買い物客のインタラクションイベントの収集が開始されます。 これらのイベントのデータはブラウザーの Cookie またはローカルストレージに保存できるので、この機能は、買い物客が Cookie の同意を得るまでイベントを収集しないことで、Cookie 制限モードをサポートします。

これは、サードパーティ Cookie の同意ソリューションとは連携しない場合があります。 法で必要とされる場合が多いので、cookie の同意が得られる前にデータ収集がおこなわれないようにするのは、商人ごとの責任です。 カスタムコードを使用して Cookie の同意を管理する場合、 `mg_dnt` をクリックして、データ収集を制限します。

- cookie の名前：

   ```text
   `const DNT_COOKIE = "mg_dnt";`
   ```

- データ収集を無効にするには、do-not-track cookie を次のように設定します。

   ```text
   `$.mage.cookies.set(DNT_COOKIE, true);`
   ```

- ユーザーが Cookie を許可したときに Cookie をクリアするには：

   ```text
   `$.mage.cookies.clear(DNT_COOKIE);`
   ```
