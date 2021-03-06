---
title: '"[!DNL Live Search] 設定»'
description: 次のような価格ファセットの範囲と間隔を設定： [!DNL Live Search] ファセット」
exl-id: a0b63116-4b8f-490c-a54e-e21f1b02b634
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 設定

以下を使用： *設定* 「 」タブを使用して、ストアフロントの検索フィルターとして使用できる価格ファセットの範囲と間隔を設定します。 価格ファセット設定は、動的ではなく静的で、検索結果に基づいていません。

価格範囲グループの数と、それら間での価格値の配分方法を指定できます。 各価格帯は、前のグループと 1 つずつ重なっています。 例えば、20 の間隔を持つ 5 つのグループは、次の価格範囲を作成します。0～20、20～40、40～60、60～80、80 以上。 定義済みのすべての範囲を満たすのに十分な商品がカタログにない場合は、それに応じて使用可能なグループの表示が調整されます。 例：0～20、60～80、>80。

![設定](assets/settings.png)

## 価格ファセットのグループ化の設定

1. 管理者で、に移動します。 **マーケティング** > *SEO と検索* > **ライブ検索**.
1. の **設定** 下のタブ *価格のファセット設定*、次の操作を実行します。
   * 次を入力します。 **選択の数**&#x200B;または価格グループを使用できるようにします。 最大 50 個の価格グループを定義できます。
   * 次を入力します。 **間隔の値**&#x200B;または各グループの価格範囲。 最大値は 10,000 です。
1. クリック **保存**.

   更新された設定がストアフロントで使用できるようになるまで、約 15 分かかります。

## フィールドの説明

| フィールド | 説明 |
|--- |--- |
| 選択の数 | ストアフロントで検索フィルターとして使用できる価格範囲グループの数を指定します。 デフォルト値：8、最大値：50 |
| 間隔の値 | 各グループの価格範囲間隔を指定します。 たとえば、間隔値が 20 の 5 つを選択すると、0 ～ 20、20 ～ 40、40 ～ 60、60 ～ 80、80 を超える 5 つのグループが作成されます。 デフォルト値：5、最大値：10,000 |
