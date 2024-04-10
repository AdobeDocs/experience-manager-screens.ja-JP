---
title: テキストオーバーレイ
description: 画像の上にオーバーレイしたタイトルや説明を提供することで、シーケンスチャネルで魅力的なエクスペリエンスを作成できる、AEM Screensのテキストオーバーレイについて説明します。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 58%

---

# テキストオーバーレイ {#text-overlay}

ここでは、以下のトピックについて説明します。

* **概要**
* **テキストオーバーレイの使用**
* **テキストオーバーレイのプロパティについて**
* **テキストオーバーレイでの ContextHub 値の使用**

>[!CAUTION]
>
>この **テキストオーバーレイ** 機能は、AEM 6.3 機能パック 5 またはAEM 6.4 機能パック 3 がインストールされている場合にのみ使用できます。

## 概要 {#overview}

テキストオーバーレイは、AEM Screensで使用できる機能で、画像の上にオーバーレイされたタイトルや説明を提供することで、シーケンスチャネルで魅力的なエクスペリエンスを作成できます。

独自のカスタムコンポーネントの作成方法については、を参照してください。 **AEM Screens コンポーネントの拡張**.

この節では、ポスターコンポーネントを AEM Screens プロジェクトで使用および適用して、シーケンスチャネルの 1 つにテキストオーバーレイとして使用する方法のみ紹介します。

## テキストオーバーレイの使用 {#using-text-overlay}

この節では、AEM Screens プロジェクトでのテキストオーバーレイの使用について説明します。

**前提条件**

この機能を実装する前に、テキストオーバーレイの実装を開始するための前提条件として、プロジェクトが設定されていることを確認してください。 例：

* AEM Screens プロジェクト（この例では **TextOverlayDemo**）を作成する

* **チャネル**&#x200B;フォルダーの下に **TextSample** というシーケンスチャネルを作成します

* **TextSample** チャネルにコンテンツを追加する

次の画像は、**チャネル**&#x200B;フォルダーに **TextSample** チャネルがある **TextOverlayDemo** プロジェクトを示しています。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

次の手順に従って、AEM Screens チャネルでテキストオーバーレイを使用します。

1. に移動します。 **TextOverlayDemo** > **チャネル** > **TextSample** をクリックして、 **編集** アクションバーから。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 画像を選択し、**設定**（レンチ）アイコンをクリックして、プロパティダイアログボックスを開きます。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. ダイアログボックスのナビゲーションバーから「**テキストオーバーレイ**」オプションを選択します（下図を参照）。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### テキストオーバーレイのプロパティについて {#understanding-text-overlay-properties}

テキストオーバーレイのプロパティを使用すると、Screens プロジェクトの任意のコンポーネントにテキストを追加できます。この節では、「テキストオーバーレイ」タブで使用できるプロパティの概要を説明します。

![text](assets/text.gif)

テキストボックスにテキストを追加し、太字、斜体、下線など、書式に強調を追加できます。

**カラーバリアント**：このオプションを選択すると、テキストは「暗い色」（黒のテキスト）または「明るい色」（白のテキスト）になります。

**サイズと位置の設定**&#x200B;このオプションで、テキストを水平または垂直方向に揃えることができます。または、テキストの位置揃えには詳細設定ツールを使用します。

>[!NOTE]
>
>詳細設定ツールを適切に使用するには、「px」をサフィックスとして使用して、正しい位置をピクセル単位で指定する必要があります。例えば、「200px」とすると、この式の結果は、スタートポイントから 200 ピクセルになります。

## テキストオーバーレイでの ContextHub 値の使用 {#using-text-overlay-context-hub}

次の節では、データストアの値の使用方法について説明します。例えば、テキストオーバーレイコンポーネントの Google シートなどです。

**前提条件**

AEM Screens プロジェクトの ContextHub 設定を設定します。

データストアを使用してデータ駆動型アセットの変更を設定および管理する方法については、を参照してください。 [AEM Screensでの ContextHub の設定](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/developing/configuring-context-hub).

プロジェクトに必要な設定を行った後、次の手順に従ってGoogle Sheets の値を使用します。

1. に移動します。 **TextOverlayDemo** > **チャネル** > **TextSample** を選択して、 **プロパティ** アクションバーから。

1. 「」を選択します **Personalization** タブをクリックして、ContextHub 設定をセットアップします。

   1. 「」を選択します **ContextHub パス** as **libs** > **設定** > **cloudsettings** > **default** > **ContextHub 設定** を選択して、 **を選択**.

   1. 「」を選択します **セグメントのパス** as **conf** > **スクリーン** > **設定** > **wcm** > **セグメント** を選択して、 **を選択**.

   1. 「**保存して閉じる**」を選択します。

      >[!NOTE]
      >
      >ContextHub 設定とセグメントをそれぞれ最初に保存した、Context Hub とセグメントのパスを使用します。

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. に移動します。 **TextOverlayDemo** > **チャネル** > **TextSample** をクリックして、 **編集** アクションバーから。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. 「[テキストオーバーレイの使用](/help/user-guide/text-overlay.md#using-text-overlay)」の節で説明されているように、画像とテキストオーバーレイコンポーネントを画像に追加します。

1. Select on **設定** （レンチアイコン）をクリックして、 **画像** ダイアログが表示されます。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. **画像**&#x200B;ダイアログボックスから「**ContextHub**」タブに移動します。「**追加**」を選択します。

   >[!NOTE]
   >ContextHub 設定を行っていない場合、このオプションはプロジェクトで無効になります。

1. Enter **値** が含まれる **プレースホルダー** フィールド。 Google シートの値を取得する行を **ContextHub 変数**. この場合、値はGoogle シートの行 2 と列 1 から取得されます。 次の図に示すように、**デフォルト値**&#x200B;を **20** と入力します。完了したら、チェックマークをクリックします。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >参考までに、次の画像はGoogle Sheets から取得された値を示しています。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 次の図に示すように、画像ダイアログボックスから&#x200B;**テキストオーバーレイ**&#x200B;タブに戻り、「*Current Temperature {Value}*」というテキストを追加します。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. **プレビュー**&#x200B;を選択します。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
