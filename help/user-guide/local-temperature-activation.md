---
title: 旅行センターの温度有効化
seo-title: 旅行センターの温度有効化
description: 以下の使用例は、Googleシートに入力された値に基づく、旅行センターのローカル温度の有効化の使用方法を示しています。
seo-description: 以下の使用例は、Googleシートに入力された値に基づく、旅行センターのローカル温度の有効化の使用方法を示しています。
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 旅行センターの温度有効化 {#travel-center-temperature-activation}

以下の使用例は、Googleシートに入力された値に基づく、旅行センターのローカル温度の有効化の使用方法を示しています。

## 説明 {#description}

この使用例では、Googleシートの値が50未満の場合、ホットドリンクのある画像が表示され、値が50以上の場合はコールドドリンクのある画像が表示されます。 他の値が存在する場合や値が存在しない場合は、プレーヤーはデフォルトの画像を表示します。

## 前提条件 {#preconditions}

トラベルセンターのローカル温度の有効化の実装を開始する前に、 ***Data Store***、 ***Audience Segmentation*** 、およびAEM Screensプロジェクトでチャネルのターゲット設定を有効にする方法 ****** を学習する必要があります。

詳しくは、「AEM [画面でのContextHubの設定](configuring-context-hub.md) 」を参照してください。

## 基本フロー {#basic-flow}

以下の手順に従って、トラベルセンターのローカル温度有効化の使用例を実装します。

1. **Googleシートの入力**

   1. ContextHubDemo googleシートに移動します。
   1. 温度に対応する値を **持つ列を** Heading1に追加します。
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **要件に従って、オーディエンスでのセグメントの設定**

   1. オーディエンス内のセグメントに移動します(手順2 ***を参照してください。(AEM ScreensページでのContextHubの設*** 定でのオーディエンスセグメントの設定 **[](configuring-context-hub.md)** を参照)。

   1. [シートA1 1 **]を選択し、[編集** ]をクリッ **クします**。

   1. 比較プロパティを選択し、設定アイコンをクリックして、プロパティを編集します。
   1. [プ **ロパティ名]のドロップダウンから** [Googlesheets/value/1/0]を選 **択します。**

   1. ドロッ **プダウン** ・メニューから「演算子」を「**より大きいか等しい**」から選択します。

   1. 値を **** 50と入力 **する**

   1. 同様に、[**シートA1 2 **]を選択し、[編集]をクリック **します**。

   1. 「比較プロパ **ティ — 値」を選択し** 、設定アイコンをクリックして、プロパティを編集します。
   1. [プ **ロパティ名]のドロップダウンから** [Googlesheets/value/1/0]を選 **択します。**

   1. ドロップダ **ウンメニューから** 「演算子」を「**より小さい**」として選択します。

   1. 値を **** 50と入力 **する**

1. チャネルに移動して選択し()、アクションバ **ーの** 「編集」をクリックします。 次の例では、 **DataDrivenWeather**、順次チャネルを使用して機能を紹介しています。

   >[!NOTE]
   >
   >チャネルに既にデフォルトの画像が存在し、「AEM ScreensでのContextHubの設定」の説明に従ってオーディエンスが事 [前に設定されている必要があります](configuring-context-hub.md)。

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >ContextHub設定は、channel **Properties** — **Personalization** **Tabを使用して設定しま****** す。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. エディター **から「ターゲティング** 」を選択し、ドロップダウンメニューから「ブラ **ンド** 」と「アクティビティ」を選択して、「ターゲット設定を開始」をクリ ********&#x200B;ックします。

   ![new_activity3](assets/new_activity3.gif)

1. **プレビューの確認**

   1. Click **Preview.** また、Googleシートを開き、値を更新します。
   1. この値を50未満に変更すると、夏の飲み物の画像が表示されます。 Googleシートの値が50以上の場合は、ホットドリンクの画像を表示できます。
   ![result3](assets/result3.gif)

