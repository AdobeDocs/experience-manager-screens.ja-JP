---
title: MultiZoneからSingleZoneへの移行の使用例
description: MultiZoneからSingleZoneへの移行の使用例については、このページを参照してください。
seo-description: MultiZoneからSingleZoneへの移行の使用例を参照してください。
contentOwner: Jyotika Syal
translation-type: tm+mt
source-git-commit: 0cae7c19759fe3418a13ab2d7cc68f1b220f397d

---


# MultiZoneからSingleZoneへの移行 {#multizone-to-singlezone-use-case}


## 使用例の説明 {#use-case-description}

この節では、シングルゾーンレイアウトチャネルと切り替わるマルチゾーンレイアウトチャネルの設定方法に重点を置いた使用例について説明します。 各チャネルは、画像/ビデオアセットを順に持つ。

### 前提条件 {#preconditions}

この使用事例を開始する前に、以下の方法を理解しておく必要があります。

* **[チャネルの作成と管理](managing-channels.md)**
* **[場所の作成と管理](managing-locations.md)**
* **[スケジュールの作成と管理](managing-schedules.md)**
* **[デバイスの登録](device-registration.md)**

### 主役 {#primary-actors}

コンテンツ作成者

## Setting up the Project {#setting-up-the-project}

次の手順に従って、プロジェクトを設定します。

1. 以下に示すように、ChannelTransitionという名前のAEM Screensプロ **ジェクトを作成し**&#x200B;ます。



1. **分割画面チャネルの作成**

   1. チャネルフォ **ルダを選択し** 、アクションバーの「 **作成** 」をクリックしてウィザードを開き、チャネルを作成します。
   1. ウィザード **から「Left-L Bar Split Screen Channel** 」を選択し、「MultiZoneLayout」という名前のチャネルを作成 **します**。



   1. Select the **MultiZoneLayout** channel and click **Edit** from the action bar to open the editor. 各ゾーンにアセットをドラッグ&amp;ドロップします。 次の例は、以下に示すように、チャネル内のビデオ、画像、およびテキストバナーを示しています。


1. **4つの画像を使用した2 X 2チャネルの作成**

   1. チャネルフォ **ルダを選択し** 、アクションバーの「 **作成** 」をクリックしてウィザードを開き、チャネルを作成します。

   1. ウィザー **ドから「2X2分割画面チャネル** 」テンプレートを選択し、「TwobyTwoChannel」という名前のチャネルを作 **成します**。


   1. チャンネルを選択し、アクシ **ョンバーで** 「編集」をクリックしてエディターを開き、次に示すように4つの画像（4つの異なるゾーン）をそのチャンネルにドラッグ&amp;ドロップします。


1. **2つの画像を使用した1 X 2分割画面チャネルの作成**

   1. チャネルフォ **ルダを選択し** 、アクションバーの「 **作成** 」をクリックしてウィザードを開き、チャネルを作成します。

   1. ウィザー **ドから「** 1X2 Split Screen Channel」テンプレートを選択し、「 **OnebyTwoChannel」という名前のチャネルを作成します**。


   1. チャンネルを選択し、アクシ **ョンバーで** 「編集」をクリックしてエディターを開き、次に示すように、2つの画像（2つの異なるゾーン）をそのチャンネルにドラッグ&amp;ドロップします。


1. **1つのフルスクリーンビデオでのチャネルの作成**

   1. チャネルフォ **ルダを選択し** 、アクションバーの「 **作成** 」をクリックしてウィザードを開き、チャネルを作成します。

   1. ウィザード **で「シーケンスチャネル** 」テンプレートを選択し、「FullScreensVideo」という名前のチャネルを作 **成します**。


   1. チャンネルを選択し、アクショ **ンバーで** 「編集」をクリックしてエディターを開き、ビデオコンポーネントをそのチャンネルにドラッグ&amp;ドロップし、次に示すように目的のビデオを追加します。

