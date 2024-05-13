---
title: プロジェクトレベルの画像再生時間
description: プロジェクトレベルで画像の再生時間を定義する方法を説明します。
contentOwner: jsyal
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 85%

---


# プロジェクトレベルの画像再生時間 {#project-level-image-playback}

## 概要 {#overview}

この機能を使用すると、プロジェクトレベルで画像の再生時間を定義できます。デフォルトでは、すべての画像はこの再生時間を継承します。プロジェクトレベルで時間が定義されていない場合、デフォルトの再生は 8 秒間続きます。

### 前提条件 {#prerequisites}

この機能の使用を開始する前に、この機能の実装の前提条件として、プロジェクトをセットアップします。次に例を示します。

1. AEM Screens プロジェクト（この例では **ProjectLevelPlayback**）を作成する
1. **チャネル**&#x200B;フォルダーの下に **PlayBackChannel** というシーケンスチャネルを作成する
1. **PlayBackChannel** にコンテンツを追加する

   ![アセット](assets/image_playback1.png)

   例えば、次の画像は **PlayBackChannel** エディターに追加された画像を示します。

   ![アセット](assets/image_playback2.png)

## プロジェクトレベル画像再生時間割り当ての編集 {#editing-project-level-image-playback-duration-assignment}

以下の節では、AEM Screens プロジェクトのコンテンツの再生時間を編集する方法について説明します。

### プロジェクトレベル画像再生時間の更新 {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>画像レベルまたはチャネルレベルの再生時間を更新する場合は、[チャネルレベルの画像再生時間](channel-level-image-playback.md)を参照してください。

プロジェクトレベルの画像再生時間の割り当てを更新するには、以下の手順に従います。

1. プロジェクト **ProjectLevelPlayback** に移動し、アクションバーの「**プロパティ**」をクリックします。
   ![アセット](assets/image_playback3.png)

1. チャネル内のすべての画像をクリックし、左上のレンチ アイコン（下図を参照）をクリックして、チャネルレベルを設定ダイアログボックスを開きます。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **ページ**&#x200B;ダイアログボックスが開きます。

   >[!NOTE]
   >
   >デフォルトでは、チャネル内の画像の再生時間は 8 秒に設定され、ビデオは 8 秒間再生されます。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   「**デュレーション**」を 8000 （ミリ秒）から 3000 （ミリ秒）、すなわち 3 秒へと編集します。の右上にあるチェックマークを選択 **ページ** ダイアログボックスが開き、変更内容が保存されます。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 結果の表示 {#viewing-the-result}

チャンネルの再生時間（この例では 3 つの画像のすべて）を更新後、画像が 8 秒間（デフォルト値）ではなく 3 秒間再生されるようになります。

![channel_preview](assets/channel_preview.gif)

