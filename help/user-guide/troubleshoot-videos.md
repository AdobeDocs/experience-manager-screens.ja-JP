---
title: ビデオ再生の設定とトラブルシューティング
description: AEM Screensのチャンネルで再生されるビデオをデバッグおよびトラブルシューティングする方法について説明します。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
feature: Channels, Interactive
role: Developer
level: Intermediate
exl-id: dfdd58b6-689b-47ca-9459-9c205f1841eb
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 32%

---

# ビデオ再生の設定とトラブルシューティング {#video-playback-configuration-and-troubleshooting}

ビデオを DAM にアップロードし、チャンネルに追加すると、AEM Screens Player でビデオが再生されない問題が発生する場合があります。

次の節では、チャネルで再生されるビデオのデバッグおよびトラブルシューティング方法について説明します。

## DAM レンディション {#dam-renditions}

ビデオをチャンネルにアップロードしたら、AEMはビデオのレンディション作成を開始する必要があります。 ビデオは Assets で表示できます。

ビデオを表示するには：

1. ビデオ（例：`http://localhost:4502/assets.html/content/dam/we-retail/en/videos`）に移動します。
1. ビデオを選択し、左上のメニューを展開して、 **レンディション**.

異なるレンディション（MP4 または M4V）が必要です。

レンディションがない場合は、AEM が動作している OS に ffmpeg がインストールされていることを確認してください。

>[!CAUTION]
>
>レンディションがない場合は、AEM が動作している OS に ffmpeg がインストールされていることを確認してください。
>
>を選択 [こちら](https://www.ffmpeg.org/download.html) をクリックして ffmpeg をインストールします。

## ビデオアセット {#video-assets}

ビデオの下にソース属性が表示されない場合は、ビデオがトランスコードされなかった可能性があります。ビデオが適切にトランスコードされている場合は、次に示すように、ダッシュボードに表示されます。

ffmpeg がインストールされていること、およびビデオプロファイルを確認してください。

![chlimage_1-2](assets/chlimage_1-2.png)

### ビデオプロファイルの確認 {#checking-video-profile}

1. に移動します。 **ビデオプロファイル**、つまり、 `http://localhost:4502/etc/dam/video.html` を選択して、 **テストビデオをアップロード**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. テストビデオをアップロードして選択 **Ok** そのため、トランスコーディングを開始できます。

   トランスコードされたビデオが失敗した場合は、ffmpeg 出力を展開して、ffmpeg のコンソール出力のエラーを把握します。

   ![chlimage_1-4](assets/chlimage_1-4.png)

   また、ビデオが正常にトランスコードされた場合は、トランスコードされたファイルをダウンロードできます。

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >ビデオをチャネルに追加する前に、ビデオがトランスコードされるための十分な時間を与えてください（ビデオは処理ではなく新しいタグで表示されます）。

### ビデオコンポーネントでのプロファイルの確認 {#checking-profile-with-a-video-component}

ビデオコンポーネントが正しく設定されていない場合は、ページデザインからプロファイルのリストを確認します。

1. チャネルに移動し、 **デザイン** モード。

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. ビデオを選択して、を開きます。 **編集** ダイアログ。 を開きます **プロファイル** タブ。

   >[!NOTE]
   >別のプロファイルを選択します（少なくとも「高品質 H.264」プロファイルが必要です）。

### Web プレーヤーでのビデオの確認 {#checking-the-video-in-the-web-player}

**Web プレーヤー**（`http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0`）を使用して、ブラウザー（Chrome および Safari）で再生を検証します。Chrome は Android™ デバイスで使用されますが、Safari は OS X およびiOS ブラウザーです。

ビデオが Safari で実行されない場合、OS X とiOS Player でも実行されません。 これはエンコーディングの問題である可能性が高く、ビデオを再エンコードする必要があります。

DAM ワークフローを使用して FullHD レンディションを作成するには、次の手順を実行します。

1. に移動します。 *ワークフローモデル管理者* つまり、 `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. 「」を選択します **Screens アセットの更新** モデル。
1. を選択 **ワークフローを開始** アクションバーから。
1. から **ワークフローを実行** ダイアログボックスで、 **ペイロード**.
1. を選択 **実行**.

>[!NOTE]
>
>レンディションを作成するには少し時間がかかりますが、ビデオのサイズによって異なる数秒/分後に、Safari で web プレーヤーをリロードします。

#### 自動再生ポリシーフラグのトラブルシューティング {#troubleshooting-autoplay-policy-flag}

AEM Screens Player がビデオを取得しても表示されない場合は、「自動再生ポリシー」フラグのトラブルシューティングを行います。

Googleの自動再生ポリシーフラグの問題をトラブルシューティングするには、次の手順に従います。

1. ***chrome://flags/#autoplay-policy*** に移動します。
1. 「**Autoplay policy**」を「**Default**」から「**No user gesture is required**」に変更します。

1. Web ブラウザーを再起動し、プレーヤーを更新します。

>[!NOTE]
>
>Chrome の新しい自動再生ポリシーで優れたユーザーエクスペリエンスを実現するためのベストプラクティスについて詳しくは、のドキュメントを参照してください *ポリシー変更の自動再生* 時刻 `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### 複数のプレーヤー間でのビデオの同期 {#syncing-video-across-multiple-players}

複数のデバイスで同期的にビデオを再生するには、そのビデオが含まれているシーケンスに関して絶対方法を使用する必要があります。

#### 要件 {#requirements}

* 同一の 2 台以上のプレーヤー
* 理想的には同種のハードウェア
* 同一のネットワークトポロジ（プレーヤーは、内部システムクロックを揃える NTP サーバーに接続されます）

#### 絶対戦略の設定 {#setting-up-the-absolute-strategy}

絶対方法：

* アンカー時刻（現在の時刻の午前 0 時）を計算します。
* シーケンスの期間（すべての項目の期間の合計）を計算します。
* シーケンス _remaining_time = （current_time - anchor_time） % sequence_duration を解決することで、どの項目を現在再生し、次の項目を再生するかを計算します。

絶対戦略を設定するには、次の手順に従います。

1. チャネル作成者に移動し、シーケンス コンポーネントを選択します（下図を参照）。
1. 設定ダイアログを開きます。
1. 「**方法**」を編集し、「絶対」を追加します。

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >プレーヤーの OS のクロックが同一である必要があります。

**OS X でのクロックの調整** OS X でクロックをアラインするには、次の手順に従います。

1. 開く **日付および時刻** 各 OS X ボックスの環境設定
1. 「**日付と時刻を自動的に設定**」をオンにします。
1. ドロップダウンの値 0.pool.ntp.org、1.pool.ntp.org、2.pool.ntp.org、3.pool.ntp.org、time.apple.com を貼り付けるか、単に *sudo ntpdate -u -v 0.pool.ntp.org* を実行します。
1. 2 台以上のプレーヤーを起動します。

プレーヤーが新しく割り当てられたシーケンスを開始するまでに時間がかかることがあります。
