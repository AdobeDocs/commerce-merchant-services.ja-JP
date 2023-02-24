---
title: ストアフルフィルメントソリューションの接続
description: Adobe Commerce統合を作成し承認し、ストアフルフィルメントアカウント資格情報をAdobe Commerceサービス設定に追加することで、Adobe Commerceとストアフルフィルメントソリューション間の接続を確立します。
role: User, Admin
level: Intermediate
exl-id: 74c71c43-305a-4ea7-84f8-95f3ce0a9482
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ストアフルフィルメントソリューションの接続

必要な認証資格情報と接続データをAdobe Commerce管理者に追加して、Store Fulfilment Services をAdobe Commerceに接続します。

- **[設定 [!DNL Commerce integration settings]](#create-the-commerce-integration)** — ストアフルフィルメントサービス用のAdobe Commerce統合を作成し、ストアフルフィルメントサーバーからの受信リクエストを認証するアクセストークンを生成します。

- **[ストアフルフィルメントサービスのアカウント資格情報を構成](#configure-store-fulfillment-account-credentials)**- Adobe Commerceをストアフルフィルメントアカウントに接続するための資格情報を追加します。

>[!NOTE]
>
>テストを開始する前に、接続設定を完了し、接続を正常に検証してください。

## Adobe Commerce統合の作成

Adobe Commerceをストアフルフィルメントサービスと統合するには、コマース統合を作成し、ストアフルフィルメントサーバーからの要求を認証するために使用できるアクセストークンを生成します。

1. 管理者から、ストアの達成の統合を作成します。

   - 拡張機能に名前を付ける
   - メールアドレスを入力
   - 管理者アカウントのパスワードを入力してください

1. 設定 [!UICONTROL API Resource Access permissions] 統合の場合、 `[!UICONTROL All]`

1. 統合を保存してアクティブ化することで、認証用のアクセストークンを生成します。

1. 安全で暗号化された場所にアクセストークンをコピーして保存します。

1. アカウントマネージャーと協力して、ストアの達成側の設定を完了し、統合を承認します。


>[!NOTE]
>
>詳しい手順については、 [統合](https://docs.magento.com/user-guide/system/integrations.html) 内 _Adobe Commerce User Guide_.

## ストアフルフィルメントアカウント資格情報の設定

取り込みフォームを完了すると、Walmart Store Fulfilment アカウントが作成されます。 次の資格情報が使用可能になると、受け取ります。

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] （通常、上記の設定と同じ）

これらの資格情報は、ストアフルフィルメントを構成して使用するために必要です。

>[!NOTE]
>
>アカウントの作成プロセスが完了するまでに時間がかかる場合があります。 資格情報を待つ間、 [ストアフルフィルメントソリューションの他の設定の確認と構成](service-config-settings-overview.md).

### ストアフルフィルメントに接続するための資格情報を追加

1. 設定 [アカウント資格情報](enable-general.md) 実稼動環境とサンドボックス環境用に作成されたものです。

1. 管理者から、に移動します。 **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. に指定したアカウント資格情報を入力 **[!UICONTROL Production environment]**. すべてのフィールドが必須です。

1. 選択 **[!UICONTROL Save Config]**.

1. 「 」を選択して接続をテストします。 **[!UICONTROL Validate Credentials]**.

>[!NOTE]
>
>資格情報が無効な場合は、各環境に対して正しい値を入力したことを確認し、再検証します。 接続で問題が解決しない場合は、アカウント担当者にお問い合わせください。
