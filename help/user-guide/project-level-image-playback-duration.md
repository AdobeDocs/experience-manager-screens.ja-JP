---
title: プロジェクトレベルの画像再生時間
description: プロジェクトレベルで画像再生時間を定義する方法を説明します。
contentOwner: jsyal
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 36%

---


# プロジェクトレベルの画像再生時間 {#project-level-image-playback}

## 概要 {#overview}

この機能を使用すると、プロジェクトレベルで画像の再生時間を定義できます。 デフォルトでは、すべての画像はこの再生時間を継承します。プロジェクトレベルで期間が定義されていない場合、8 秒のデフォルトの再生が続行されます。

### 前提条件 {#prerequisites}

この機能を使用する前に、この機能の実装を開始するための前提条件としてプロジェクトを設定します。 例：

1. AEM Screens プロジェクト（この例では、 **ProjectLevelPlay**）に設定します。
1. シーケンスチャネルの作成： **PlayBackChannel** 未満 **チャネル** フォルダー。
1. コンテンツの追加先 **PlayBackChannel**.

   ![アセット](assets/image_playback1.png)

   例えば、次の画像は **PlayBackChannel** エディターに追加された画像を示します。

   ![アセット](assets/image_playback2.png)

## プロジェクトレベル画像再生時間の割り当ての編集 {#editing-project-level-image-playback-duration-assignment}

以下の節では、AEM Screens プロジェクトのコンテンツの再生時間を編集する方法について説明します。

### プロジェクトレベルでの画像の再生時間の更新 {#updating-the-playback-duration-for-images-in-a-project}


>[!NOTE]
>
>画像またはチャネルレベルの再生時間を更新する場合は、を参照してください [チャネルレベルの画像再生時間](channel-level-image-playback.md).

プロジェクトレベルの画像再生時間の割り当てを更新するには、以下の手順に従います。

1. プロジェクト **ProjectLevelPlayback** に移動し、アクションバーの「**プロパティ**」をクリックします。
   ![アセット](assets/image_playback3.png)

1. チャネル内のすべての画像を選択し、左上のレンチアイコン（下図を参照）をクリックして、チャネルレベルの設定ダイアログボックスを開きます。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. この **ページ** ダイアログボックスが開きます。

   >[!NOTE]
   >
   >デフォルトでは、チャネル内の画像の再生時間は 8 秒に設定され、ビデオは 8 秒間再生されます。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   を編集する **期間** 8000 （ミリ秒）～3000 （ミリ秒）、つまり 3 秒です。 右上のチェックマークをクリックします **ページ** ダイアログボックスが開き、変更内容が保存されます。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 結果の表示 {#viewing-the-result}

チャネル再生時間（この例では 3 つの画像すべて）を更新したら、画像が 8 秒（デフォルト値）ではなく 3 秒間再生されることに注意してください。

![channel_preview](assets/channel_preview.gif)

