---
title: ビデオパディングワークフローの作成
description: アセットのワークフローでのビデオパディングの作成について詳しくは、こちらを参照してください。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 16180f96-2855-4250-9d55-24ed77a908b7
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 61%

---

# ビデオパディングワークフローの作成 {#creating-a-video-padding-workflow}

ここでは、以下のトピックについて説明します。

* **概要**
* **前提条件**
* **ビデオパディングワークフローの作成**
   * **ワークフローの作成**
   * **AEM Screens プロジェクトでのワークフローの使用**

* **ワークフローの出力の検証**

## 概要 {#overview}

次の使用例では、チャネルへのビデオ（例：1280 x 720）の配置が必要になります。このチャネルのディスプレイは 1920 x 1080 で、0x0（左上）にビデオが配置されます。ビデオは、引き伸ばしや変更を一切おこなわないでください。また、ビデオコンポーネントで「**カバー**」は使用しません。

ビデオは、ピクセル 1 ～ 1280 の間でピクセル 1 からピクセル 720 の間でオブジェクトとして表示され、残りのチャネルはデフォルトのカラーになります。

## 前提条件 {#prerequisites}

ビデオのワークフローを作成する前に、次の前提条件を満たしてください。

1. AEM インスタンスの **Assets** フォルダーにビデオをアップロードする
1. AEM Screens プロジェクト（例：**TestVideoRendition**）と、**VideoRendering** という名前のチャネルを作成します（下図を参照）。

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## ビデオパディングワークフローの作成 {#creating-a-video-padding-workflow-1}

ビデオパディングワークフローを作成するには、ビデオのワークフローを作成してから、AEM Screens プロジェクトチャネルで同じワークフローを使用します。

以下の手順に従って、ワークフローを作成して使用します。

1. ワークフローの作成
1. AEM Screens プロジェクトでのワークフローの使用

### ワークフローの作成 {#creating-a-workflow}

以下の手順に従って、ビデオのワークフローを作成します。

1. AEM インスタンスに移動します。
1. サイドパネルからツールをクリックします。
1. クリック **ワークフロー** > **モデル** そのため、モデルを作成できます。

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. **モデル**／**作成**／**モデルを作成**&#x200B;をクリックします。**ワークフローモデルを追加**&#x200B;で、「**タイトル**」（**VideoRendition**）と「**名前**」を入力します。「**完了**」をクリックして、ワークフローモデルを追加します。

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. ワークフローモデルを作成したら、モデル（**VideoRendition**）を選択し、をクリックします **編集** アクションバーから。

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. をドラッグ&amp;ドロップ **`Command Line`** コンポーネントをワークフローに追加します。

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. 「」をクリックします **`Command Line`** コンポーネントを選択し、「プロパティ」ダイアログボックスを開きます。

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. 「**引数**」タブをクリックします。
1. が含まれる **コマンドライン – ステップのプロパティ** ダイアログ ボックスで、形式を **Mime タイプ** （as ***video/mp4***）、およびコマンドを（***/usr/local/Cellar/ffmpeg -i ${filename} -vf &quot;pad=1920:height=1080:x=0:y=0:color=black&quot; cq5dam.video.fullhd-hp.mp4***）。 このコマンドは、でワークフローを開始します **コマンド** フィールド。

   「**MIME タイプ**」と「**コマンド**」について詳しくは、以下の注記を参照してください。

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. ワークフロー（**VideoRenditions**）に設定します。
1. クリック **ワークフローを開始** アクションバーから。

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. が含まれる **ワークフローを実行** ダイアログボックスで、 **ペイロード** （as ***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4***）を選択し、を入力します **タイトル** as ***RunVideo*** をクリックして、 **実行**.

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### AEM Screens プロジェクトでのワークフローの使用 {#using-the-workflow-in-an-aem-screens-project}

以下の手順に従って、AEM Screens プロジェクトでワークフローを使用します。

1. AEM Screens プロジェクト（**TestVideoRendition**／**チャネル**／**VideoRendition**）に移動します。

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. アクションバーの「**編集**」をクリックします。最初に&#x200B;**アセット**&#x200B;フォルダーにアップロードしたビデオをドラッグ＆ドロップします。

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. ビデオをアップロードしたら、 **プレビュー** 出力を表示します。

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## ワークフローの出力の検証 {#validating-the-output-for-the-workflow}

出力は、次のいずれかの方法で検証できます。

* チャネル内のビデオのプレビューを確認する
* CRXDE Lite で ***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4*** に移動する（下図を参照）

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)
