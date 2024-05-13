---
title: 旅行センター向けの気温に応じたアクティベーション
description: AEM Screensを使用して、このユースケースが、Google シートに入力された値に基づいて、トラベルセンターのローカル温度アクティベーションの使用方法を示す方法を説明します。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 2ec2891f-0fbe-4812-b3c4-ff160ead36b8
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 43%

---

# 旅行センター向けの気温に応じたアクティベーション {#travel-center-temperature-activation}

以下の使用例では、Google シートに入力された値に基づく、旅行センター向けの現地気温に応じたアクティベーションを示しています。

## 説明 {#description}

このユースケースでは、Google シートの値が 50 未満の場合、ホットドリンクを含む画像が表示されます。 値が 50 以上の場合は、コールドドリンクを含む画像が表示されます。 他の値がある場合や、値がない場合、プレーヤーはデフォルトの画像を表示します。

## 前提条件 {#preconditions}

トラベルセンターの地域温度アクティベーションの実装を開始する前に、の設定方法について説明します ***データストア***, ***オーディエンスのセグメント化*** および ***チャネルのターゲティングを有効にする*** （AEM Screens プロジェクト内）。

詳しくは、[AEM Screens での ContextHub の設定](configuring-context-hub.md)を参照してください。

## 基本フロー {#basic-flow}

「旅行センター向けの現地気温に応じたアクティベーション」の使用例を実装するには、以下の手順に従います。

1. **Google シートにデータを入力する**

   1. ContextHubDemo Google シートに移動します。
   1. を使用して列を追加 **`Heading1`** 温度に対応する値を持ちます。

   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **要件に従ってオーディエンスのセグメントを設定する**

   1. オーディエンスのセグメントに移動します（詳しくは、**[AEM Screens での ContextHub の設定](configuring-context-hub.md)**&#x200B;ページの&#x200B;***手順 2：オーディエンスのセグメント化のセットアップ***&#x200B;を参照してください）。

   1. 「」をクリックします **シート A1 1** をクリックして、 **編集**.

   1. 比較プロパティをクリックし、設定アイコンをクリックします。
   1. クリック **google シート/値/1/0** のドロップダウンから **プロパティ名**

   1. 「」をクリックします **演算子** as **次よりも大きいか等しい** ドロップダウンメニューから

   1. 「**値**」に「**50**」を入力します。

   1. 同様に、 **シート A1 2** をクリックして、 **編集**.

   1. 「」をクリックします **Comparison プロパティ – 値** 「設定」アイコンを選択します。
   1. クリック **google シート/値/1/0** のドロップダウンから **プロパティ名**

   1. 「」をクリックします **演算子** as **より小さい** ドロップダウンメニューから

   1. 「**値**」に「**50**」を入力します。

1. チャネルに移動して選択し、アクションバーの「**編集**」をクリックします。次の例では、**DataDrivenWeather** というシーケンスチャネルを使用して機能を紹介しています。

   >[!NOTE]
   >
   >チャネルには既にデフォルトの画像が存在し、[AEM Screens プロジェクトでの ContextHub の設定](configuring-context-hub.md)で説明しているとおりにオーディエンスが事前設定されています。

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   >
   >チャネルの&#x200B;**プロパティ**／**パーソナライズ機能**&#x200B;タブを使用して&#x200B;**ContextHub** **設定**&#x200B;をセットアップしておいてください。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. クリック **ターゲティング** エディターで、をクリックします **ブランド** および **Activity** ドロップダウンメニューからを選択し、 **ターゲティングを開始**.

   ![new_activity3](assets/new_activity3.gif)

1. **プレビューを確認する**

   1. 「**プレビュー**」をクリックします。また、Google シートを開き、値を更新します。
   1. 値を 50 未満に変更します。 冷たい飲み物の画像を見ることができるはずです。 Google シートの値が 50 以上の場合は、ホットドリンクの画像が表示されます。

   ![result3](assets/result3.gif)
