---
title: 接客予約有効化
seo-title: 接客予約有効化
description: 以下の使用例は、Googleシートに入力された値に基づいて病院の予約を有効にする方法を示しています。
seo-description: 以下の使用例は、Googleシートに入力された値に基づいて病院の予約を有効にする方法を示しています。
uuid: 7692d616-2b00-4d9a-9d3f-211c089b29af
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
discoiquuid: ef3e5dce-e36a-45d3-ad5e-db01430477c6
docset: aem65
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# 接客予約有効化 {#hospitality-reservation-activation}

以下の使用例は、Googleシートに入力された値に基づいて病院の予約を有効にする方法を示しています。

## 説明 {#description}

この使用例では、Googleシートに2つのレストラン **Restarant1** と **Restarant2の予約の割合が入力されます**。 Restarant1とRestarant2の値に基づいて数式が適用され、その数式に基づいて、AdTarget列に値1または2が割り当てら **れます** 。

**Restarant1** &gt; **Restaint2の値がAdRestarant1****1** Assigned Restaurant Value setの場合はRestainted Value **Target Assigned Value** 2 ******** AssignedValueTarget 値1はステーキフ *ード* ( *Stake food* )オプションを生成し、値2はタイフフード(Thai food)オプションを表示画面に表示します。

## 前提条件 {#preconditions}

予約の有効化を実装する前に、AEM Screensプロジェクトで ***Data Store***、 ***Audience Segmentation*** 、チャネルのターゲット設定を有効にする方法 ****** を学ぶ必要があります。

詳しくは、「AEM [画面でのContextHubの設定](configuring-context-hub.md) 」を参照してください。

## 基本フロー {#basic-flow}

次の手順に従って、AEM Screensプロジェクトにホスピタリティーの予約有効化の使用例を実装します。

1. **Googleシートに入力し、数式を追加します。**

   例えば、次の図に示すように、3列目の **AdTarget**&#x200B;に数式を適用します。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **要件に従って、オーディエンスでのセグメントの設定**

   1. オーディエンス内のセグメントに移動します(手順2 ***を参照してください。(AEM ScreensページでのContextHubの設*** 定でのオーディエンスセグメントの設定 **[](configuring-context-hub.md)** を参照)。

   1. [シートA1 1 **]を選択し、[編集** ]をクリッ **クします**。

   1. 比較プロパティを選択し、設定アイコンをクリックして、プロパティを編集します。
   1. [プ **ロパティ名]のドロップダウンから** [Googlesheets/value/1/2]を選 **択します。**

   1. ドロップダウ **ンメニュー** から「 **Operator as** equal」を選択します。

   1. 値を **** 1と入 **力**

   1. 同様に、[シートA1 2 **]を選択し、[編集** ]をクリッ **クします**。

   1. 比較プロパティを選択し、設定アイコンをクリックして、プロパティを編集します。
   1. [プ **ロパティ名]のドロップダウンから** [Googlesheets/value/1/2]を選 **択します。**

   1. 演算子を **2とし** て選 **択**

1. チャネルに移動して選択し()、アクションバ **ーの** 「編集」をクリックします。 次の例では、DataDrivenRestarantとい **う順次チャネルを使用して**、機能を紹介しています。

   >[!NOTE]
   >
   >チャネルに既にデフォルトの画像が存在し、「AEM ScreensでのContextHubの設定」の説明に従ってオーディエンスが事 [前に設定されている必要があります](configuring-context-hub.md)。

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   >
   >ContextHub設定は、channel **Properties** — **Personalization** **Tabを使用して設定しま****** す。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

1. エディター **から「ターゲティング** 」を選択し、ドロップダウンメニューから「ブラ **ンド** 」と「アクティビティ」を選択して、「ターゲット設定を開始」をクリ ********&#x200B;ックします。
1. **プレビューの確認**

   1. Click **Preview.** また、Googleシートを開き、値を更新します。
   1. Restarant1列と **Restarant2列の値を更** 新します **** 。 If **1** &gt; **2,** Thai *food* food *Thai restaurant 、それ以外の場合は画面にStake* food Thai Foodの画像が表示されるので、画面にはStake foodの画像が表示されます。
   ![result5](assets/result5.gif)

