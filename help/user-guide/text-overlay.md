---
title: テキストオーバーレイ
seo-title: テキストオーバーレイ
description: テキストオーバーレイは AEM Screens で利用できる機能で、画像の上にタイトルや説明を重ねて表示することにより、シーケンスチャネルに魅力的なエクスペリエンスを作成できます。このページでは、この機能について詳しく見ていきます。
seo-description: テキストオーバーレイは AEM Screens で利用できる機能で、画像の上にタイトルや説明を重ねて表示することにより、シーケンスチャネルに魅力的なエクスペリエンスを作成できます。このページでは、この機能について詳しく見ていきます。
uuid: 944477e8-0025-4cc7-aa61-6b72f4a245fd
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: b6fdb5a0-5601-4443-a3f4-85cc90c49914
noindex: true
translation-type: tm+mt
source-git-commit: 651627223e1b9bd0f650b010d2b92f004b9e2ea2

---


# テキストオーバーレイ {#text-overlay}

ここでは、以下のトピックについて説明します。

* **概要**
* **テキストオーバーレイの使用**
* **「テキストオーバーレイ」タブのプロパティについて**
* **テキストオーバーレイでのContextHub値の使用**

>[!CAUTION]
>
>**テキストオーバーレイ**&#x200B;機能は、AEM 6.3 機能パック 5 または AEM 6.4 機能パック 3 がインストールされている場合にのみ使用できます。

## 概要 {#overview}

テキストオーバーレイは AEM Screens で利用できる機能で、画像の上にタイトルや説明を重ねて表示することにより、シーケンスチャネルに魅力的なエクスペリエンスを作成できます。

独自のカスタムコンポーネントの作成方法については、**AEM Screens コンポーネントの拡張**&#x200B;を参照してください。

この節では、ポスターコンポーネントを AEM Screens プロジェクトのシーケンスチャネルの 1 つでテキストオーバーレイとして使用する方法のみ紹介します。

## テキストオーバーレイの使用 {#using-text-overlay}

この節では、AEM Screens プロジェクトでのテキストオーバーレイの使用について説明します。

**前提条件**

テキストオーバーレイ機能の実装を開始する前に、前提条件として、プロジェクトをセットアップしておく必要があります。例：

* AEM Screens プロジェクト（この例では **TextOverlayDemo**）を作成する

* Create a sequence channel titled as **TextSample** under **Channels** folder

* **TextSample** チャネルにコンテンツを追加する

次の画像は、**チャネル**&#x200B;フォルダーに **TextSample** チャネルがある **TextOverlayDemo** プロジェクトを示しています。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

次の手順に従って、AEM Screensチャネルでテキストオーバーレイを使用します。

1. **TextOverlayDemo**／**Channels**／**TextSample** に移動し、アクションバーの「**編集**」をクリックして、エディターを開きます。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 画像を選択し、**設定**（レンチ）アイコンをクリックして、プロパティダイアログボックスを開きます。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. ダイアログボックスのナビゲーションバーから「**テキストオーバーレイ**」オプションを選択します（下図を参照）。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### 「テキストオーバーレイ」タブのプロパティについて {#understanding-text-overlay-properties}

「テキストオーバーレイ」タブのプロパティを使用すると、Screens プロジェクトの任意のコンポーネントにテキストを追加できます。この節では、「テキストオーバーレイ」タブで使用できるプロパティの概要を説明します。

![text](assets/text.gif)

テキストボックスにテキストを追加し、太字、斜体、下線などの強調書式を追加できます。

**カラーバリアント**：このオプションを選択すると、テキストは「暗い色」（黒のテキスト）または「明るい色」（白のテキスト）になります。

**サイズと位置の設定**：テキストを水平または垂直方向に揃えることができます。さらに、詳細設定ツールを使用してテキストの位置揃えをおこなうこともできます。

>[!NOTE]
>
>詳細設定ツールを適切に使用するには、「px」をサフィックスとして使用して、正しい位置をピクセル単位で指定する必要があります。たとえば、「200px」とすると、開始点から 200 ピクセル離れた位置が指定されます。

## テキストオーバーレイでのContextHub値の使用 {#using-text-overlay-context-hub}

次の節では、データストアの値の使用方法について説明します。例えば、テキストオーバーレイコンポーネントのgoogleシートなどです。

**前提条件**

AEM ScreensプロジェクトのContextHub設定を設定する必要があります。

データストアを使用してデータ駆動型アセットの変更を設定および管理する方法については、「AEM ScreensでのContextHubの設 [定」を参照してください](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/developing/configuring-context-hub.html)。

プロジェクトに必要な設定を行ったら、次の手順に従ってGoogleシートの値を使用します。

1. TextOverlayDemo **—>チャネル** —> **TextSample** —> **TextSample** , **Properties from** the action barに移動し、「Properties」をクリックします。

1. 「**パーソナライゼーション**」タブを選択して、ContextHub 設定をセットアップします。

   1. 「**ContextHub のパス**」として **libs**/**settings**/**cloudsettings**/**default**/**ContextHub Configurations** を選択し、「**選択**」をクリックします。

   1. **Segments Path** as **conf >** screens > settings > settings > **cm** segments > **thersetings** thered segments **therclickseled segments, click********** selected

   1. 「**保存して閉じる**」をクリックします。

      >[!NOTE]
      >
      >ContextHub 設定とセグメントをそれぞれ最初に保存した、Context Hub とセグメントのパスを使用します。

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. **TextOverlayDemo**／**Channels**／**TextSample** に移動し、アクションバーの「**編集**」をクリックして、エディターを開きます。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. こ追加のページの「テキストオーバーレイの使用」の節で説明している、画像とテキストオーバーレイ [](/help/user-guide/text-overlay.md#using-text-overlay) ・コンポーネント。

1. 「 **Configure** （レンチアイコン）」をクリックして、「 **Image** 」ダイアログ・ボックスを開きます。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. 「画像」( **Image** )ダイアログボックスの「ContextHub **」タブに移** 動します。 「**追加**」をクリックします。

   >[!NOTE]
   >ContextHub設定を設定していない場合、このオプションはプロジェクトで無効になります。

1. 「 **Placeholder** ( **Placeholder** )」フィールドにValueと入力し、 **GoogleHub Variable（この場合、値はGoogleシートの行2列1から取得されます）で、Googleから値を取得する行を選択し、図の下のシートのデフォルト値********** 0と入力します。 完了したら、チェックマークをクリックします。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >参照用に、次の図はGoogleシートから取得される値を示しています。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 次の図に示すように、 **Imageダイアログ** ボックスから「 *Text Overlay*」タブに戻り、「Current Temperature」 {Value}というテキストを追加します。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. 「 **プレビュー** 」をクリックし、出力を表示します。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)















