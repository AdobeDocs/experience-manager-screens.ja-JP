---
title: 小売店向けの在庫に応じたアクティベーション
description: 3 種類のカラーのスウェットシャツの小売在庫在庫を表示する、このAEM Screensのユースケースについて説明します。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 30%

---

# 小売店向けの在庫に応じたアクティベーション {#retail-inventory-targeted-activation}

次の使用例では、Google シートの値に応じた 3 種類の画像の表示方法を示しています。

## 説明 {#description}

このユースケースでは、3 種類のカラーのスウェットシャツの小売在庫在庫を表示します。 Googleシートに記録されているストック中のスウェットシャツの枚数に応じて、最も多い画像（赤、緑、青）が表示されます。

使用可能なセーターの最大数に基づいて、赤、緑、青のセーターが表示されます。

## 前提条件 {#preconditions}

小売在庫のターゲット設定アクティブ化の実装を開始する前に、の設定方法を学びます ***データストア***, ***オーディエンスのセグメント化*** および ***チャネルのターゲティングを有効にする*** （AEM Screens プロジェクト内）。

詳しくは、[AEM Screens での ContextHub の設定](configuring-context-hub.md)を参照してください。

## 基本フロー {#basic-flow}

「小売店向けの在庫に応じたアクティベーション」の使用例を実装するには、以下の手順に従います。

1. **Google シートにデータを入力する**

   1. ContextHubDemo Google シートに移動します。
   1. 3 種類のトレーナーに対応する値を格納する 3 つの列（Red、Green、Blue）を追加します。

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **要件に従ってオーディエンスを設定する**

   1. オーディエンスのセグメントに移動します（詳しくは、**[AEM Screens での ContextHub の設定](configuring-context-hub.md)**&#x200B;ページの&#x200B;***手順 2：オーディエンスのセグメント化の設定***&#x200B;を参照してください）。

   1. 3 つの新しいセグメント **For_Red**、**For_Green**、**For_Blue** を追加します。

   1. クリック **For_Red** をクリックして、 **編集** アクションバーから。

   1. をドラッグ&amp;ドロップします **Comparison : プロパティ – プロパティ** をエディターに送信します。
   1. 「」をクリックします **設定** アイコン。
   1. クリック **googlesheets/value/1/2** のドロップダウンから **最初のプロパティ名**.
   1. 「」をクリックします **演算子**、および **より大きい** ドロップダウンメニューから。
   1. クリック **データタイプ**、および **数値**.
   1. クリック **googlesheets/value/1/1** のドロップダウンから **2 番目のプロパティ名**.
   1. ドラッグ&amp;ドロップ **もう 1 つの比較：プロパティ – プロパティ** エディターに移動し、 **設定** アイコン。
   1. クリック **googlesheets/value/1/2** のドロップダウンから **最初のプロパティ名**.
   1. 「」をクリックします **演算子**、および **より大きい** ドロップダウンメニューから。
   1. クリック **データタイプ**、および **数値**.
   1. クリック **google シート/値/1/0** のドロップダウンから **2 番目のプロパティ名**.

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同様に、比較プロパティルールを編集し、に追加します **For_Blue** 次の図に示すセグメント。

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同様に、比較プロパティルールを編集し、に追加します **For_Green** 次の図に示すセグメント。

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >セグメント用であることに注意してください **For_Green** および **For_Green**&#x200B;最初の比較のみがGoogle シートの値に従って有効になるので、エディターでデータを解決することはできません。

1. に移動して、 **DataDrivenRetail** channel （シーケンスチャネル）。
1. アクションバーの「**編集**」をクリックします。

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >を既に設定している必要があります **ContextHub** **設定** チャネルの使用 **プロパティ** > **Personalization** タブ。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   >
   >両方をクリックします **ブランド** および **領域** （ターゲティングプロセスを開始したときに、アクティビティが適切にリストされるようにするには）。

1. **デフォルト画像を追加する**

   1. チャネルにデフォルト画像を追加し、「**ターゲティング**」をクリックします。
   1. クリック **ブランド** および **Activity** ドロップダウンメニューからを選択し、 **ターゲティングを開始**.
   1. 「**ターゲティングを開始**」をクリックします。

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   >
   >ターゲティングを開始する前に、セグメント（**For_Green**, **For_Red**、および **For_Blue**）を選択します。 **+ エクスペリエンスのターゲット設定を追加** 次の図に示すように、サイドレールから。

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 次に示すように、3 つの異なるシナリオすべてに画像を追加します。

   ![retail_targeting](assets/retail_targeting.gif)

1. **プレビューを確認する**

   1. 「**プレビュー**」をクリックします。また、Google シートを開き、値を更新します。
   1. 3 つの異なる列の値をすべて変更します。 インベントリ内の最大値に従ってディスプレイの画像が更新されます。

   ![retail_result](assets/retail_result.gif)
