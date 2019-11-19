---
title: 小売在庫ターゲットの有効化
seo-title: 小売在庫ターゲットの有効化
description: この使用例は、3種類の色付きシャツの小売在庫を示します。 Googleシートに記録されている在庫にあるスウェットシャツの数に応じて、最も多い数の画像（赤、緑、青のスウェットシャツ）が画面に表示されます。
seo-description: この使用例は、3種類の色付きシャツの小売在庫を示します。 Googleシートに記録されている在庫にあるスウェットシャツの数に応じて、最も多い数の画像（赤、緑、青のスウェットシャツ）が画面に表示されます。
uuid: 8e7faa65-b004-42b3-8865-4f71eb5dc1b1
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 70147920-5bdb-401c-884e-51d268d40585
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 小売在庫ターゲットの有効化 {#retail-inventory-targeted-activation}

次の使用例は、Googleシートの値に基づいて3つの異なる画像を示しています。

## 説明 {#description}

この使用例は、3種類の色付きシャツの小売在庫を示します。 Googleシートに記録されている在庫にあるスウェットシャツの数に応じて、最も多い数の画像（赤、緑、青のスウェットシャツ）が画面に表示されます。

この使用事例では、利用可能なセーターの数が最も多いことに基づいて、赤、緑、青のセーターが画面に表示されます。

## 前提条件 {#preconditions}

小売在庫ターゲットの有効化の実装を開始する前に、AEM Screensプロジェクトで ***Data Store***、 ***Audience Segmentation*** 、チャネルのターゲット設定を有効にする方法 ****** を学ぶ必要があります。

詳しくは、「AEM [画面でのContextHubの設定](configuring-context-hub.md) 」を参照してください。

## 基本フロー {#basic-flow}

小売在庫の有効化の使用例を実装するには、次の手順に従います。

1. **Googleシートの入力**

   1. ContextHubDemo googleシートに移動します。
   1. 3種類のスウェートシャツに対応する値を持つ3つの列（赤、緑、青）を追加します。
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **要件に従ったオーディエンスの設定**

   1. オーディエンス内のセグメントに移動します(手順2 ***を参照してください。(AEM ScreensページでのContextHubの設*** 定でのオーディエンスセグメントの設定 **[](configuring-context-hub.md)** を参照)。

   1. 3つの新しいセグ **メントFor_Red**、 **For_Green**、 **For_Blueを追加します**。

   1. 「 **For_Red」を選択し、アク** ションバー **で「編集** 」をクリックします。

   1. 比較をドラッグ&amp;ドロ **ップします。「プロパティ** 」 — プロパティをエディタに追加し、設定アイコンをクリックしてプロパティを編集します。
   1. 「 **First Property name」のドロップダウンから** 「googlesheets/value/1/2」を **選択します。**

   1. ドロップダウ **ンメニューから** 「**より大きい**」を選択します。

   1. 「 **Data Type** 」を「 **number」として選択**

   1. 「 **Second Property name」のドロップダウンから** 「googlesheets/value/1/1」を **選択します。**

   1. **別の比較をドラッグ&amp;ドロップ：プロパティ — プロパティ**をエディタに追加し、設定アイコンをクリックして、プロパティを編集します。
   1. 「 **First Property name」のドロップダウンから** 「googlesheets/value/1/2」を **選択します。**

   1. ドロップダウ **ンメニューから** 「**より大きい**」を選択します。

   1. 「 **Data Type** 」を「 **number」として選択**

   1. 「 **Second Property name」のドロップダウンから** 「googlesheets/value/1/0」を **選択します。**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同様に、次の図に示すように、比較プロパティ **ルールを編集し** 、For_Blueセグメントに追加します。

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同様に、以下の図に示すように、比較プロパティルールを編集して、** For_Green **segmentに追加します。

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >セグメント **For_Green** と **For_Green**&#x200B;は、Googleシートの値に基づいて、現時点では最初の比較のみが有効なので、データをエディターで解決できません。

1. DataDrivenRetailチャネル(シーケ **ルチャネル** )に移動して選択し、アクションバーの **「編集** 」をクリックします。

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >ContextHub設定は、channel **Properties** — **Personalization** **Tabを使用して設定しま****** す。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   ターゲット設定プロセスを開始する **ときに、ア** クティビティを正しく表示するには **** 、ブランドとエリアの両方を選択する必要があります。

1. **デフォルト画像の追加**

   1. チャネルにデフォルトの画像を追加し、「ターゲット設定」をクリ **ックしま**&#x200B;す。
   1. ドロップ **ダウンメニューから「ブ** ランド **」と「アクティビティ** 」を選択し、「ターゲット設定を開始」を **クリックします**。

   1. 「**ターゲット設定を開始**」をクリックします。
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   ターゲット設定を開始する前に、図に示すように、「****+ Experience Targeting **Add Side rail from the side rail」をクリックして、セグメント(** For_Green **、For_Red**、および **For_Blue** )を追加する必要があります。

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 以下に示すように、画像を3つの異なるスクリーンすべてに追加します。

   ![retail_targeting](assets/retail_targeting.gif)

1. **プレビューの確認**

   1. Click **Preview.** また、Googleシートを開き、値を更新します。
   1. 3つの異なる列の値をすべて変更すると、在庫の最も高い値に応じて表示画像が更新されます。
   ![retail_result](assets/retail_result.gif)

