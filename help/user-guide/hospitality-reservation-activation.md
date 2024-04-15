---
title: 接客業向けの予約状況に応じたアクティベーション
description: このユースケースが、Google シートに入力された値に基づいたホスピタリティ予約アクティベーションの使用を示す方法を説明します。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: ae032042-fa2b-49cd-91fe-ce50f3ce9867
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 31%

---

# 接客業向けの予約状況に応じたアクティベーション {#hospitality-reservation-activation}

以下の使用例では、Google シートに入力された値に基づく、接客業向けの予約状況に応じたアクティベーションを示しています。

## 説明 {#description}

このユースケースでは、Google シートには、2 つのレストランの予約率が入力されています **`Restaurant1`** および **`Restaurant2`**. 数式は、次の値に基づいて適用されます `Restaurant1` および `Restaurant2` さらに、数式に基づいて、値 1 または値 2 がに割り当てられます **AdTarget** 列。

の値 **`Restaurant1`** > **`Restaurant2`**、次に **広告** 割り当てられた値 **1** それ以外の場合 **AdTarget** 割り当てられた値 **2**. 値 1 の生成 *ステーキ食品* オプションと値 2 の結果、 *タイ料理* ディスプレイ画面のオプション。

## 前提条件 {#preconditions}

予約アクティベーションの実装を開始する前に、の設定方法を学びます ***データストア***, ***オーディエンスのセグメント化*** および ***チャネルのターゲティングを有効にする*** （AEM Screens プロジェクト内）。

参照： [AEM Screensでの ContextHub の設定](configuring-context-hub.md) を参照してください。

## 基本フロー {#basic-flow}

次のユースケース手順に従って、AEM Screens プロジェクトのホスピタリティ予約のアクティベーションを実装します。

1. **Googleシートへの入力と式の追加**.

   例えば、3 列目の **AdTarget** に数式を適用します（下図を参照）。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **要件に従ってオーディエンスのセグメントを設定する**

   1. オーディエンスのセグメントに移動します（を参照）。 ***手順 2：オーディエンスセグメント化の設定*** 。対象： **[AEM Screensでの ContextHub の設定](configuring-context-hub.md)** 詳しくはこちらを参照してください）。
   1. 「」を選択します **シート A1 1** を選択して、 **編集**.
   1. 比較プロパティを選択し、 **設定** アイコン。
   1. 「**プロパティ名**」のドロップダウンから「**googlesheets/value/1/2**」を選択します。
   1. 「」を選択します **演算子** as **等しい** ドロップダウンメニューから。
   1. 「**値**」に「**1**」を入力します。
   1. 同様に、 **シート A1 2** を選択して、 **編集**.
   1. 比較プロパティを選択し、 **設定** アイコン。
   1. 「**プロパティ名**」のドロップダウンから「**googlesheets/value/1/2**」を選択します。
   1. 「」を選択します **演算子** as **2**.

1. チャネル（）に移動して選択し、次を選択します **編集** アクションバーから。 次の例では、**DataDrivenRestaurant** というシーケンスチャネルを使用して機能を紹介しています。

   >[!NOTE]
   >
   >チャネルには既にデフォルトの画像が存在し、[AEM Screens プロジェクトでの ContextHub の設定](configuring-context-hub.md)で説明しているとおりにオーディエンスが事前設定されています。

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >を設定する必要があります **ContextHub** **設定** チャネルの使用 **プロパティ** > **Personalization** タブ。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. を選択 **ターゲティング** エディターでを選択します。 **ブランド** および **Activity** ドロップダウンメニューからを選択します。 **ターゲティングを開始**.
1. **プレビューを確認する**

   1. を選択 **プレビュー。**」をクリックします。また、Google シートを開き、値を更新します。
   1. の値を更新します **`Restaurant1`** および **`Restaurant2`** 列。 次の場合 **`Restaurant1`** > **`Restaurant2`,** 次の画像を表示できます *ステーキ* 食べ物は別として。 *タイ語* 画面に食べ物の画像が表示されます。

   ![result5](assets/result5.gif)
