---
title: 旅行センター向けの気温に応じたアクティベーション
seo-title: Travel Center Temperature Activation
description: 以下の使用例では、Google シートに入力された値に基づく、旅行センター向けの現地気温に応じたアクティベーションを示しています。
seo-description: The following use case demonstrates the usage of travel center local temperature activation based on the values populated in Google Sheets.
uuid: b35286d2-79be-4c36-b72e-c40ffc1a0ca0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: 9d58b971-4540-4007-968d-2a1d94d1fd38
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 89%

---

# 旅行センター向けの気温に応じたアクティベーション {#travel-center-temperature-activation}

以下の使用例では、Google シートに入力された値に基づく、旅行センター向けの現地気温に応じたアクティベーションを示しています。

## 説明 {#description}

この使用例では、Google シートの値が 50 未満の場合は、暖かい飲み物の画像が表示され、値が 50 以上の場合は冷たい飲み物の画像が表示されます。それ以外の値の場合や値がない場合は、デフォルト画像がプレーヤーに表示されます。

## 前提条件 {#preconditions}

旅行センター向けの現地気温に応じたアクティベーションの実装を開始する前に、AEM Screens プロジェクトで&#x200B;***データストア***、***オーディエンスのセグメント化***、***チャネルのターゲティングの有効化***&#x200B;をセットアップする方法を理解しておく必要があります。

参照： [AEM Screensでの ContextHub の設定](configuring-context-hub.md) を参照してください。

## 基本フロー {#basic-flow}

「旅行センター向けの現地気温に応じたアクティベーション」の使用例を実装するには、以下の手順に従います。

1. **Google シートにデータを入力する**

   1. ContextHubDemo Google シートに移動します。
   1. 気温に対応する値を格納する **Heading1** という列を追加します。

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **要件に従ってオーディエンスのセグメントを設定する**

   1. オーディエンスのセグメントに移動します（を参照）。 ***手順 2：オーディエンスセグメント化の設定*** 。対象： **[AEM Screensでの ContextHub の設定](configuring-context-hub.md)** 詳しくはこちらを参照してください）。

   1. 「**Sheets A1 1**」を選択し、「**編集**」をクリックします。

   1. 比較プロパティを選択し、設定アイコンをクリックしてプロパティを編集します。
   1. 「**プロパティ名**」のドロップダウンから「**googlesheets/value/1/0**」を選択します。

   1. 「**演算子**」のドロップダウンメニューから「**次よりも大きいか等しい**」を選択します。

   1. 「**値**」に「**50**」を入力します。

   1. 同様に、「**Sheets A1 2**」を選択し、「**編集**」をクリックします。

   1. 「**比較：プロパティ - 値**」を選択し、設定アイコンをクリックしてプロパティを編集します。
   1. 「**プロパティ名**」のドロップダウンから「**googlesheets/value/1/0**」を選択します。

   1. 「**演算子**」のドロップダウンメニューから「**次よりも小さい**」を選択します

   1. 「**値**」に「**50**」を入力します。

1. チャネルに移動して選択し、アクションバーの「**編集**」をクリックします。次の例では、**DataDrivenWeather** というシーケンスチャネルを使用して機能を紹介しています。

   >[!NOTE]
   >
   >チャネルには既にデフォルトの画像が存在し、[AEM Screens プロジェクトでの ContextHub の設定](configuring-context-hub.md)で説明しているとおりにオーディエンスが事前設定されています。

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >を設定する必要があります **ContextHub** **設定** チャネルの使用 **プロパティ** > **Personalization** タブ。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. エディターから「**ターゲット設定**」を選択し、「**ブランド**」を選択してドロップダウンメニューから「**アクティビティ**」を選択します。次に、「**ターゲット設定を開始**」をクリックします。

   ![new_activity3](assets/new_activity3.gif)

1. **プレビューを確認する**

   1. 「**プレビュー**」をクリックします。また、Google シートを開き、値を更新します。
   1. 値を 50 未満に変更すると、暖かい飲み物の画像が表示されます。Google シートの値が 50 以上の場合は、冷たい飲み物の画像が表示されます。

   ![result3](assets/result3.gif)
