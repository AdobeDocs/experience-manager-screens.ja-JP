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
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 33%

---

# 接客業向けの予約状況に応じたアクティベーション {#hospitality-reservation-activation}

以下の使用例では、Google シートに入力された値に基づく、接客業向けの予約状況に応じたアクティベーションを示しています。

## 説明 {#description}

この使用例では、Google シートに、2 つのレストランの予約率が表示されます **`Restaurant1`** および **`Restaurant2`**. 数式は、次の値に基づいて適用されます `Restaurant1` および `Restaurant2` さらに、数式に基づいて、値 1 または値 2 がに割り当てられます **AdTarget** 列。

の値 **`Restaurant1`** > **`Restaurant2`**、次に **広告** 割り当てられた値 **1** それ以外の場合 **AdTarget** 割り当てられた値 **2**. 値 1 の場合、 *ステーキ食品* オプションと値 2 の結果、 *タイ料理* ディスプレイ画面のオプション。

## 前提条件 {#preconditions}

予約アクティベーションの実装を開始する前に、の設定方法を学びます ***データストア***, ***オーディエンスのセグメント化*** および ***チャネルのターゲティングを有効にする*** （AEM Screens プロジェクト内）。

詳しくは、[AEM Screens での ContextHub の設定](configuring-context-hub.md)を参照してください。

## 基本フロー {#basic-flow}

次のユースケース手順に従って、AEM Screens プロジェクトのホスピタリティ予約のアクティベーションを実装します。

1. **Googleシートへの入力と式の追加**.

   例えば、3 列目の **AdTarget** に数式を適用します（下図を参照）。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **要件に従ってオーディエンスのセグメントを設定する**

   1. オーディエンスのセグメントに移動します（詳しくは、**[AEM Screens での ContextHub の設定](configuring-context-hub.md)**&#x200B;ページの&#x200B;***手順 2：オーディエンスのセグメント化のセットアップ***&#x200B;を参照してください）。
   1. 「」をクリックします **シート A1 1** をクリックして、 **編集**.
   1. 「比較」プロパティをクリックし、 **設定** アイコン。
   1. クリック **googlesheets/value/1/2** のドロップダウンから **プロパティ名**.
   1. 「」をクリックします **演算子** as **等しい** ドロップダウンメニューから。
   1. 「**値**」に「**1**」を入力します。
   1. 同様に、 **シート A1 2** をクリックして、 **編集**.
   1. 「比較」プロパティをクリックし、 **設定** アイコン。
   1. クリック **googlesheets/value/1/2** のドロップダウンから **プロパティ名**.
   1. 「」をクリックします **演算子** as **2**.

1. チャネル（）に移動してクリックし、 **編集** アクションバーから。 次の例では、**DataDrivenRestaurant** というシーケンスチャネルを使用して機能を紹介しています。

   >[!NOTE]
   >
   >チャネルには既にデフォルトの画像が存在し、[AEM Screens プロジェクトでの ContextHub の設定](configuring-context-hub.md)で説明しているとおりにオーディエンスが事前設定されています。

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >あなたの **ContextHub** **設定** チャネルの使用 **プロパティ** > **Personalization** この時点では、タブは既に設定されているはずです。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. クリック **ターゲティング** エディターで、をクリックします **ブランド** および **Activity** ドロップダウンメニューからを選択し、 **ターゲティングを開始**.
1. **プレビューを確認する**

   1. 「**プレビュー**」をクリックします。また、Google シートを開き、値を更新します。
   1. の値を更新します **`Restaurant1`** および **`Restaurant2`** 列。 次の場合 **`Restaurant1`** > **`Restaurant2`,** 次の画像を表示できます *ステーキ* 食べ物は別として。 *タイ語* 画面に食べ物の画像が表示されます。

   ![result5](assets/result5.gif)
