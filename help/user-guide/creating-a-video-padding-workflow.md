---
title: ビデオパディングワークフローの作成
description: アセットのワークフローにおけるビデオパディングの作成について詳しく説明します。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 16180f96-2855-4250-9d55-24ed77a908b7
TQID: https://experienceleague.adobe.com/NNWMddEX0RPig8ye2p8UfgG6BQHpCapqb9KNc5RS9Ys
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 594
ht-degree: 85%

---

# ビデオパディングワークフローの作成 {#creating-a-video-padding-workflow}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

ここでは、以下のトピックについて説明します。

* **概要**
* **前提条件**
* **ビデオパディングワークフローの作成**
   * **ワークフローの作成**
   * **AEM Screens プロジェクトでのワークフローの使用**

* **ワークフローの出力の検証**

## 概要 {#overview}

次の使用例では、チャネルへのビデオ（例：1280 x 720）の配置が必要になります。このチャネルのディスプレイは 1920 x 1080 で、0x0（左上）にビデオが配置されます。 ビデオは、引き伸ばしや変更を一切おこなわないでください。また、ビデオコンポーネントで「**カバー**」は使用しません。

ビデオは横がピクセル 1～1280、縦がピクセル 1～720 のオブジェクトとして表示されます。 チャンネルの残りの部分はデフォルトのカラーです。

## 前提条件 {#prerequisites}

ビデオのワークフローを作成する前に、次の前提条件を満たしてください。

1. AEM インスタンスの **Assets** フォルダーにビデオをアップロードする
1. AEM Screens プロジェクト（例：**TestVideoRendition**）と、**VideoRendering** という名前のチャネルを作成します（下図を参照）。

![screen_shot_2018-10-17at85307pm](assets/screen_shot_2018-10-17at85307pm.png)

## ビデオパディングワークフローの作成 {#creating-a-video-padding-workflow-1}

ビデオパディングワークフローを作成するには、ビデオのワークフローを作成したあと、同じワークフローを AEM Screens プロジェクトのチャネルでも使用します。

以下の手順に従って、ワークフローを作成して使用します。

1. ワークフローの作成
1. AEM Screens プロジェクトでのワークフローの使用

### ワークフローの作成 {#creating-a-workflow}

以下の手順に従って、ビデオのワークフローを作成します。

1. AEM インスタンスに移動します。
1. サイドパネルからツールをクリックします。
1. **ワークフロー**／**モデル**&#x200B;をクリックすると、モデルを作成できます。

   ![screen_shot_2018-10-17at90025pm](assets/screen_shot_2018-10-17at90025pm.png)

1. **モデル**／**作成**／**モデルを作成**&#x200B;をクリックします。 **ワークフローモデルを追加**&#x200B;で、「**タイトル**」（**VideoRendition** など）と「**名前**」を入力します。 「**完了**」をクリックして、ワークフローモデルを追加します。

   ![screen_shot_2018-10-17at90747pm](assets/screen_shot_2018-10-17at90747pm.png)

1. ワークフローモデルを作成したら、モデル（**VideoRendition**）をクリックし、アクションバーの「**編集**」をクリックします。

   ![screen_shot_2018-10-17at91256pm](assets/screen_shot_2018-10-17at91256pm.png)

1. **`Command Line`**&#x200B;コンポーネントをワークフローにドラッグ＆ドロップします。

   ![screen_shot_2018-10-22at14846pm](assets/screen_shot_2018-10-22at14846pm.png)

1. **`Command Line`**&#x200B;コンポーネントをクリックし、プロパティダイアログボックスを開きます。

   ![screen_shot_2018-10-17at95752pm](assets/screen_shot_2018-10-17at95752pm.png)

1. 「**引数**」タブをクリックします。
1. 「**コマンドライン – ステップのプロパティ**」ダイアログボックスで、**Mime Types** （***video/mp4***）という形式で入力し、コマンド（{***`/usr/local/Cellar/ffmpeg -i ${filename} -vf "pad=1920:height=1080:x=0:y=0:color=black" cq5dam.video.fullhd-hp.mp4`***）を入力します。 このコマンドは、「**コマンド**」フィールド内のワークフローを開始します。

   「**MIME タイプ**」と「**コマンド**」について詳しくは、以下の注記を参照してください。

   ![screen_shot_2018-10-18at105300am](assets/screen_shot_2018-10-18at105300am.png)

1. ワークフロー（**VideoRenditions**）をクリックします。
1. アクションバーの「**ワークフローを開始**」をクリックします。

   ![screen_shot_2018-10-18at105335am](assets/screen_shot_2018-10-18at105335am.png)

1. **ワークフローを実行**&#x200B;ダイアログボックスで、「**ペイロード**」内のアセットのパス（***/content/dam/huseinpeyda-crossroads01_512kb 2.mp4***）をクリックし、「**タイトル**」を ***RunVideo*** と入力して、「**実行**」をクリックします。

   ![screen_shot_2018-10-18at112043am](assets/screen_shot_2018-10-18at112043am.png)

### AEM Screens プロジェクトでのワークフローの使用 {#using-the-workflow-in-an-aem-screens-project}

以下の手順に従って、AEM Screens プロジェクトでワークフローを使用します。

1. AEM Screens プロジェクト（**TestVideoRendition**／**チャネル**／**VideoRendition**）に移動します。

   ![screen_shot_2018-10-17at100715pm](assets/screen_shot_2018-10-17at100715pm.png)

1. アクションバーの「**編集**」をクリックします。 最初に&#x200B;**アセット**&#x200B;フォルダーにアップロードしたビデオをドラッグ＆ドロップします。

   ![screen_shot_2018-10-17at102806pm](assets/screen_shot_2018-10-17at102806pm.png)

1. ビデオをアップロードしたら、「**プレビュー**」をクリックして出力を表示します。

   ![screen_shot_2018-10-22at15151pm](assets/screen_shot_2018-10-22at15151pm.png)

## ワークフローの出力の検証 {#validating-the-output-for-the-workflow}

出力は、次のいずれかの方法で検証できます。

* チャネル内のビデオのプレビューを確認する
* 次の図に示すように、CRXDE Liteの&#x200B;***/content/dam/testvideo.mp4/jcr:content/renditions/cq5dam.video.fullhd-hp.mp4***&#x200B;に移動します。

![screen_shot_2018-10-22at14326pm](assets/screen_shot_2018-10-22at14326pm.png)

