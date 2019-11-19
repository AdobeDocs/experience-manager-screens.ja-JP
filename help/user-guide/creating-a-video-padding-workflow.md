---
title: ビデオパディングワークフローの作成
seo-title: ビデオパディングワークフローの作成
description: このページでは、アセットのワークフローでのビデオパディングの作成について説明します。
seo-description: このページでは、アセットのワークフローでのビデオパディングの作成について説明します。
uuid: c0f004ca-c934-47f8-bcdc-da58ea62118e
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: a90e3950-c95a-4aff-8cb3-9229c660a815
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# ビデオパディングワークフローの作成 {#creating-a-video-padding-workflow}

この節では、以下のトピックについて説明します。

* **概要**
* **前提条件**
* **ビデオパディングワークフローの作成**
   * **ワークフローの作成**
   * **AEM Screensプロジェクトでのワークフローの使用**

* **ワークフローの出力の検証**

## 概要 {#overview}

次の使用例は、ビデオの配置を含みます(例：1280 x 720)(ディスプレイが1920 x 1080で、ビデオが0x0（左上）に配置されるチャンネル)。 ビデオは、ストレッチまたは変更を一切行わないでください。また、ビデオコンポーネ **ントの** 「カバー」は使用しません。

ビデオはピクセル1からピクセル1280の間、およびピクセル1からピクセル720の間でオブジェクトとして表示され、残りのチャンネルは初期設定の色になります。

## 前提条件 {#prerequisites}

ビデオのワークフローを作成する前に、次の前提条件を満たしてください。

1. AEMインスタンスの **Assets** フォルダーにビデオをアップロード
1. 次の図に示すように、AEM Screensプロジェクト( **TestVideoRendition**&#x200B;など)と(**VideoRendering**)という名前のチャネルを作成します。

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## ビデオパディングワークフローの作成 {#creating-a-video-padding-workflow-1}

ビデオパディングワークフローを作成するには、ビデオのワークフローを作成し、AEM Screensプロジェクトチャネルでも同じワークフローを使用する必要があります。

次の手順に従って、ワークフローを作成し、使用します。

1. ワークフローの作成
1. AEM Screensプロジェクトでのワークフローの使用

### Creating a Workflow {#creating-a-workflow}

次の手順に従って、ビデオのワークフローを作成します。

1. AEMインスタンスに移動し、サイドレールからツールをクリックします。 「ワー **クフロー** 」(Workflow **** ) &gt; 「モデル」(Models)の順に選択して、新しいモデルを作成します。

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. [モデ **ル** ] —&gt; [作成 **] —&gt; [モデル** を作成 **]をクリックします**。 「ワークフロ **ーモデ** ルの **追加」に「タイトル」(VideoRenditionと**********&#x200B;して)と「名前」を入力します。 「完了」を **クリックし** 、ワークフローモデルを追加します。

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. ワークフローモデルを作成したら、モデル(**VideoRendition**)を選択し、アクションバーから「 **Edit** 」をクリックします。

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. **コマンドライン**コンポーネントをワークフローにドラッグ&amp;ドロップします。

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. コマンドライン **コンポーネントを選択し** 、プロパティダイアログボックスを開きます。

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. 「引数」タブ **を選択し** 、「コマンドライン — ステップのプ **ロパティ」ダイアログにフィールドを入力します** 。

   「 **MIME Types** ( ***video/mp4***)」に形式を入力し、コマンドを「（***/usr/local/Cellar/ffmpeg -i ${filename} -vf "pad=1920:height=1080:x=0:y=0:color=black" cq5dam.video.hd-hp.mp4」と入力します。**）をクリックして、「コマンド」フィールドでワークフ **ローを開始します** 。

   以下の注記の「 **Mime Types** 」と「 **Commands** 」の詳細を参照してください。

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. ワークフロー(「ビデオレンディシ&#x200B;**ョン」**)を選択し、アクシ **ョンバーの「ワークフローを開始」をクリックして、ワークフロー****** を実行ダイアログボックスを開きます。

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. ペイロードでアセットのパスを **(/content/dam/huseinpeyda-crossroads01_512kb 2.mp4** )選択し、**Title **( ***RunIdeo***)を入力し、「 ***Run***」をクリックして「 **** Run」をクリックします。

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### AEM Screensプロジェクトでのワークフローの使用 {#using-the-workflow-in-an-aem-screens-project}

次の手順に従って、AEM Screensプロジェクトでワークフローを使用します。

1. AEM Screensプロジェクト(**TestVideoRendition** —&gt; **Channels** —&gt;**VideoRendition**)に移動します。

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. Click **Edit** from the action bar. 最初にアセットにアップロードしたビデオをドラッグ&amp;ドロ **ップしま**&#x200B;す。

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. ビデオをアップロードしたら、「プレビュー」を **クリック** して出力を表示します。

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## ワークフローの出力の検証 {#validating-the-output-for-the-workflow}

出力は、次の方法で検証できます。

* チャネル内のビデオのプレビューを確認する
* CRXDE Lite ***の/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** （下図を参照）に移動します。

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

