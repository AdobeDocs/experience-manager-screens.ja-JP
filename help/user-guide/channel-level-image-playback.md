---
title: チャネルレベルのバルク画像再生時間
seo-title: チャネルレベルのバルク画像再生時間
description: このページでは、特定の画像コンポーネントの再生時間を編集する方法について説明します。
seo-description: このページでは、特定の画像コンポーネントの再生時間を編集する方法について説明します。
uuid: 4ebb00a9-b04d-4dfe-9fee-2348a2e2c142
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: df3cf999-0c8d-4754-8b58-5c6ced2c8ca5
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# チャネルレベルのバルク画像再生時間{#channel-level-bulk-image-playback-duration}

## 概要 {#overview}

シーケンスチャネルを作成し、そのチャネルに画像を追加すると、デフォルトでは、すべての画像はチャネルレベル設定で定義された再生時間を前提とします。 個々の画像がデフォルトを上書きし、異なる再生時間を持つ場合でも、特定の画像コンポーネントの再生時間を編集することで実現できます。

### 前提条件 {#prerequisites}

この機能の実装を開始する前に、この機能の実装を開始する前提条件としてプロジェクトを設定していることを確認してください。 以下に例を挙げます。  

1. AEM Screensプロジェクトの作成(この例では、 **ChannelLevelPlayback**)

1. Channelsフォルダーの下にPlaybackChannelとしてシーケ **ンスチャンネル****を作成**

1. PlaybackChannelへのコンテンツの **追加**

## チャネルレベルの画像再生時間の割り当ての編集 {#editing-channel-level-image-playback-duration-assignment}

以下の節では、AEM Screensチャンネルでコンテンツの再生時間を編集する方法について説明します。

### チャネル内の画像の再生時間の更新 {#updating-the-playback-duration-for-images-in-a-channel}

チャネルレベルの画像再生時間の割り当てを更新する方法を学ぶには、次の手順に従います。

1. シーケンスチャネルPlaybackChannelに移動 **します**。

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. アクションバーから「**編集**」をクリックして、エディターを開きます。

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. 次の図に示すように、チャネルエディタで2つ以上の画像を追加します。

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. チャネル内のすべての画像を選択し、左上のレンチアイコンをクリックして（下の図に示すように）、チャネルレベルの設定ダイアログボックスを開きます。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **[ページ** ]ダイアログボックスが開きます。

   >[!NOTE]
   >
   >デフォルトでは、チャネル内の画像は8秒の再生時間に設定されます。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   [ **Duration** ]を8,000（ミリ秒）～ 3000（ミリ秒）（3秒）の間で編集します。 ページダイアログボックスの右上にあるチェック **マークを** 、変更を保存します。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 結果の表示 {#viewing-the-result}

チャンネルの再生時間を更新すると（この例では、3つの画像すべて）、画像が8秒（初期設定値）ではなく3秒間再生されることに気付きます。

![channel_preview](assets/channel_preview.gif)

