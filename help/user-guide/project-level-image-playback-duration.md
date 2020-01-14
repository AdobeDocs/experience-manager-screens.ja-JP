---
title: プロジェクトレベルの画像再生時間
seo-title: プロジェクトレベルの画像再生時間
description: 'この機能を使用すると、プロジェクトレベルでの画像の再生時間を定義できます。 '
seo-description: 'この機能を使用すると、プロジェクトレベルでの画像の再生時間を定義できます。 '
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: ae1f7cab650f811ae03f0a2f3dfa49ec855997ee

---


# プロジェクトレベルの画像再生時間 {#project-level-image-playback}

## 概要 {#overview}

この機能を使用すると、プロジェクトレベルでの画像の再生時間を定義できます。 デフォルトでは、すべての画像はこの再生時間を継承します。 プロジェクトレベルで期間が定義されていない場合、デフォルトの再生は8秒間続きます。

### 前提条件 {#prerequisites}

この機能を使用する前に、この機能の実装を開始する前提条件としてプロジェクトを設定しておく必要があります。 例：

1. Create an AEM Screens project (in this example, **ProjectLevelPlayback**)

1. Create a sequence channel as **PlayBackChannel** under **Channels** folder

1. Add content to **PlayBackChannel**

   ![アセット](assets/image_playback1.png)

   例えば、次の画像はPlayBackChannelエディターに追加された画像を **示します** 。

   ![アセット](assets/image_playback2.png)

## Editing Project Level Image Playback Duration Assignment {#editing-project-level-image-playback-duration-assignment}

以下の節では、AEM Screensプロジェクトでコンテンツの再生時間を編集する方法について説明します。

### プロジェクトレベルでの画像の再生時間の更新 {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>画像レベルまたはチャンネルレベルの再生時間を更新する場合は、「チャンネルレベルの画像再 [生時間」を参照してください](channel-level-image-playback.md)。

次の手順に従って、プロジェクトレベルの画像再生時間を更新する方法を学習します。

1. Navigate to your project **ProjectLevelPlayback** and click **Properties** from the action bar.
   ![アセット](assets/image_playback3.png)

1. チャネル内のすべての画像を選択し、左上のレンチアイコンをクリックして（下図を参照）、チャネルレベルの設定ダイアログボックスを開きます。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **ページ**&#x200B;ダイアログボックスが開きます。

   >[!NOTE]
   >
   >デフォルトでは、チャネル内の画像は8秒の再生時間に設定され、ビデオはデフォルトの長さで再生されます。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   「**デュレーション (ms)**」を「8000 (ms)」から「3000 (ms)」（3 秒）へと編集します。**ページ**&#x200B;ダイアログボックスの右上にあるチェックマークをクリックして、変更を保存します。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 結果の表示 {#viewing-the-result}

チャンネルの再生時間（この例では 3 つの画像すべての再生時間）を更新すると、画像が 8 秒間（デフォルト値）ではなく 3 秒間再生されるようになります。

![channel_preview](assets/channel_preview.gif)

