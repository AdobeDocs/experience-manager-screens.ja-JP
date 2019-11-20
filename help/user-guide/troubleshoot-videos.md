---
title: ビデオ再生の設定とトラブルシューティング
seo-title: ビデオのトラブルシューティング
description: null
seo-description: このページでは、ビデオをトラブルシューティングする方法について説明します。ビデオを DAM にアップロードしてチャネルに追加するときに、ビデオが Screens Player で再生されないという問題が発生する場合があります。ここでは、チャネルで再生されるビデオをデバッグおよびトラブルシューティングする方法について説明します。
uuid: 825b2440-5626-40d5-8c93-7689c24474d4
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 65ecc6f1-ba0e-443f-85a1-ac19f9a52c2c
translation-type: tm+mt
source-git-commit: 66c741bb73bd5deb2bb5b06dd46f2e407d9c4b7e

---


# ビデオ再生の設定とトラブルシューティング {#video-playback-configuration-and-troubleshooting}

ビデオを DAM にアップロードしてチャネルに追加するときに、ビデオが Screens Player で再生されないという問題が発生する場合があります。

以下の節では、チャネルで再生されるビデオをデバッグおよびトラブルシューティングする方法について説明します。

## DAM レンディション {#dam-renditions}

ビデオをチャネルにアップロードすると、AEM によってそのビデオの一部のレンディションの作成が開始されます。ビデオは、「アセット」の下に表示できます。

ビデオを表示するには：

1. 例えば、ビデオに移動します `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`。
1. Click the video and expand the top left menu and click **Renditions**.

様々なレンディションがあります（MP4 や M4V など）。

レンディションがない場合は、AEMが実行されているOSにffmpegがインストールされていることを確認します。

>[!CAUTION]
>
>レンディションがない場合は、AEMが実行されているOSにffmpegがインストールされていることを確認します。
>
>ffmpeg をインストールするには、[ここ](https://evermeet.cx/ffmpeg/)をクリックしてください。

## ビデオアセット {#video-assets}

ビデオの下にソース属性が表示されない場合は、ビデオがトランスコードされなかった可能性があります。ビデオが正しくトランスコードされている場合は、次の図に示すようにダッシュボードに表示されます。

ffmpegがインストールされ、ビデオプロファイルを確認します。

![chlimage_1-2](assets/chlimage_1-2.png)

### ビデオプロファイルの確認 {#checking-video-profile}

1. Navigate to the **Video Profile**, that is, `http://localhost:4502/etc/dam/video.html` and click **Upload Test Video**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Upload a test video and click **Ok** to begin the transcoding.

   トランスコードが失敗した場合は、ffmpeg 出力を展開して ffmpeg のコンソール出力でエラーを確認します。

   ![chlimage_1-4](assets/chlimage_1-4.png)

   また、ビデオが正常にトランスコードされた場合は、トランスコードされたファイルをダウンロードできます。

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >ビデオのトランスコードに十分な時間をかけてから（「処理しています」ではなく「新規」というタグが表示されます）、ビデオをチャネルに追加するようにしてください。

### ビデオコンポーネントでのプロファイルの確認 {#checking-profile-with-a-video-component}

ビデオコンポーネントが正しく設定されない場合は、ページデザインからプロファイルのリストを確認します。

1. チャネルに移動し、**デザイン**&#x200B;モードを選択します。

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. ビデオを選択し、**編集**&#x200B;ダイアログを開きます。「**プロファイル**」タブを開きます。

   様々なプロファイルを選択します（少なくとも「高画質 H.264」プロファイルは必ずあります）。

   ![chlimage_1-7](assets/chlimage_1-7.png)

### Web プレーヤーでのビデオの確認 {#checking-the-video-in-the-web-player}

**Web playerを使用し** て `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` 、ブラウザー（ChromeおよびSafari）での再生を検証します。 Chrome は Android デバイスで使用され、Safari は OSX および iOS のブラウザーです。

Safari で実行されない場合、ビデオは OSX および iOS のプレーヤーで実行されません。これはエンコーディングの問題である可能性が高く、ビデオを再度エンコードする必要があります。

DAM ワークフローを使用してフル HD レンディションを作成するには、次の手順を実行します。

1. Navigate to the *workflow model admin*, that is `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. **スクリーン更新アセット**&#x200B;モデルを選択します。
1. アクションバーから「**ワークフローを開始**」をクリックして、**ワークフローを実行**&#x200B;ダイアログボックスを開きます。

1. 「**ペイロード**」でビデオアセットを選択します。
1. 「**実行**」をクリックします。

>[!NOTE]
>
>レンディションの作成には多少時間がかかりますが、数秒または数分後（ビデオサイズによります）、Safari で Web プレーヤーを再読み込みします。

#### 自動再生ポリシーフラグのトラブルシューティング {#troubleshooting-autoplay-policy-flag}

AEM Screensプレーヤーがビデオを取得したが表示されない場合は、自動再生ポリシーフラグのトラブルシューティングを行う必要があります。

Googleの自動再生ポリシーフラグの問題をトラブルシューティングするには、次の手順に従います。

1. chrome://flags/#autoplay-policyに移動し ***ます。***
1. 自動再生 **ポリシーを「デフ** ォルト **」から** 、ユ **ーザージェスチャは不要です**

1. Webブラウザーを再起動し、プレイヤーを更新します

>[!NOTE]
>
>Chromeの新しい自動再生ポリシーでユーザーにとって良好な操作を行うためのベストプラクティスについて詳しくは、自動再生ポリシーの変更に関するドキュメ *ント*(つまり `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`、「 」を参照してください。

### 複数のプレーヤーでのビデオの同期 {#syncing-video-across-multiple-players}

複数のデバイスで同期的にビデオを再生するには、ビデオが含まれるシーケンスの絶対方法を使用する必要があります。

#### 要件 {#requirements}

* 同一の2人以上のプレーヤー
* 理想的には同種のハードウェア
* 同一のネットワークトポロジ（プレーヤーは、内部システムクロックを揃えたNTPサーバに接続されている）

#### 絶対方法の設定 {#setting-up-the-absolute-strategy}

絶対的な戦略は次のとおりです。

* アンカー時間（現在の日付の 0 時）を計算します。
* シーケンスの期間（すべての項目の期間の合計）を計算します。
* 任意の時点で、シーケンス_remaining_time = (current_time - anchor_time) % sequence_durationを解決して、現在再生する必要のあるアイテムと次のアイテムを計算します。

絶対方法を設定するには、次の手順を実行します。

1. チャネルオーサーに移動し、次の図に示すようにシーケンスコンポーネントを選択します。
1. その設定ダイアログを開きます。
1. Edit the **Strategy** and add absolute.

![chlimage_1-8](assets/chlimage_1-8.png)

>[!NOTE]
>
>プレーヤーの OS のクロックが同一である必要があります。

**OS xでのクロックの整列** OSXでクロックを整列させるには、次の手順に従います。

1. Open **Date &amp; Time** preferences on each OSX box
1. チェック**日付と時刻を自動的に設定**
1. Paste value 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com in the dropdown or simply run *sudo ntpdate -u -v 0.pool.ntp.org*
1. 2 台以上のプレーヤーを起動します。

プレーヤーが新しく割り当てられたシーケンスを開始するまでに時間がかかることがあります。

