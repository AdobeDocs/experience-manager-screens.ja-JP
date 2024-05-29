---
title: ビデオ再生の設定とトラブルシューティング
description: AEM Screens のチャネルで再生されるビデオをデバッグおよびトラブルシューティングする方法について説明します。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
feature: Channels, Interactive
role: Developer
level: Intermediate
exl-id: dfdd58b6-689b-47ca-9459-9c205f1841eb
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 80%

---

# ビデオ再生の設定とトラブルシューティング {#video-playback-configuration-and-troubleshooting}

ビデオを DAM にアップロードしてチャンネルに追加すると、AEM Screens Player でビデオが再生されない問題が発生する場合があります。

以下の節では、チャネルで再生されるビデオをデバッグおよびトラブルシューティングする方法について説明します。

## DAM レンディション {#dam-renditions}

ビデオをチャネルにアップロードすると、AEM によってそのビデオのレンディションの作成が開始されます。ビデオは Assets で表示できます。

ビデオを表示するには：

1. ビデオ（例：`http://localhost:4502/assets.html/content/dam/we-retail/en/videos`）に移動します。
1. ビデオをクリックし、左上のメニューを展開して「**レンディション**」をクリックします。

様々なレンディションがあります（MP4 や M4V など）。

レンディションがない場合は、AEMが動作している OS に FFMPEG がインストールされていることを確認します。

>[!CAUTION]
>
>レンディションがない場合は、AEMが動作している OS に FFMPEG がインストールされていることを確認します。
>
>クリック [こちら](https://www.ffmpeg.org/download.html) FFMPEG をインストールします。

## ビデオアセット {#video-assets}

ビデオの下にソース属性が表示されない場合は、ビデオがトランスコードされなかった可能性があります。ビデオが正しくトランスコードされている場合は、以下に示すようにダッシュボードに表示されます。

FFMPEG がインストールされ、ビデオプロファイルが指定されていることを確認します。

![chlimage_1-2](assets/chlimage_1-2.png)

### ビデオプロファイルの確認 {#checking-video-profile}

1. **ビデオプロファイル**（`http://localhost:4502/etc/dam/video.html`）に移動し、「**テストビデオをアップロード**」をクリックします。

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. テストビデオをアップロードし、「**OK**」をクリックしてトランスコードを開始します。

   トランスコードされたビデオが失敗した場合は、FFMPEG 出力を展開して、FFMPEG のコンソール出力にエラーがあるかどうかを確認します。

   ![chlimage_1-4](assets/chlimage_1-4.png)

   また、ビデオが正常にトランスコードされた場合は、トランスコードされたファイルをダウンロードできます。

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >ビデオのトランスコードに十分な時間をかけてから（「処理しています」ではなく新しいタグが表示されます）、ビデオをチャネルに追加するようにしてください。

### ビデオコンポーネントでのプロファイルの確認 {#checking-profile-with-a-video-component}

ビデオコンポーネントが正しく設定されない場合は、ページデザインからプロファイルのリストを確認します。

1. チャネルに移動し、「**デザイン**」モードをクリックします。

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. ビデオをクリックし、**編集**&#x200B;ダイアログを開きます。「**プロファイル**」タブを開きます。

   >[!NOTE]
   >別のプロファイルをクリックします（少なくとも「高品質 H.264」プロファイルがあるはずです）。

### Web プレーヤーでのビデオの確認 {#checking-the-video-in-the-web-player}

**Web プレーヤー**（`http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0`）を使用して、ブラウザー（Chrome および Safari）で再生を検証します。Chrome は Android™ デバイスで使用されますが、Safari は OS X および iOS ブラウザーです。

ビデオが Safari で実行されない場合、OS X と iOS Player でも実行されません。この問題はエンコーディングの問題である可能性が高く、ビデオを再エンコードする必要があります。

DAM ワークフローを使用して FullHD レンディションを作成するには、次の手順を実行します。

1. *ワークフローモデル管理*（`http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`）に移動します。
1. 「**スクリーン更新アセット**」モデルをクリックします。
1. アクションバーの「**ワークフローを開始**」をクリックします。
1. **ワークフローを実行**&#x200B;ダイアログボックスで、**ペイロード**&#x200B;のビデオアセットをクリックします。
1. 「**実行**」をクリックします。

>[!NOTE]
>
>レンディションの作成には多少時間がかかりますが、数秒または数分後（ビデオサイズによります）、Safari で eb プレーヤーを再読み込みします。

#### 自動再生ポリシーフラグのトラブルシューティング {#troubleshooting-autoplay-policy-flag}

AEM Screens プレーヤーでビデオを取得してもビデオが表示されない場合は、自動再生ポリシーフラグのトラブルシューティングを行います。

Google の自動再生ポリシーフラグに関する問題をトラブルシューティングするには、以下の手順に従います。

1. ***chrome://flags/#autoplay-policy*** に移動します。
1. 「**Autoplay policy**」を「**Default**」から「**No user gesture is required**」に変更します。

1. Web ブラウザーを再起動し、プレーヤーを更新します

>[!NOTE]
>
>Chrome の新しい自動再生ポリシーで、優れたユーザーエクスペリエンスを実現するベストプラクティスについて詳しく説明します。 参照： *ポリシー変更の自動再生* 時刻 `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### 複数のプレーヤーでのビデオの同期 {#syncing-video-across-multiple-players}

複数のデバイスで同期的にビデオを再生するには、そのビデオが含まれているシーケンスに関して絶対方法を使用する必要があります。

#### 要件 {#requirements}

* 同一の 2 台以上のプレーヤー
* 理想的には同種のハードウェア
* 同一のネットワークトポロジ（プレーヤーは、内部システムクロックを揃える NTP サーバーに接続されます）

#### 絶対方法の設定 {#setting-up-the-absolute-strategy}

絶対方法：

* アンカー時間（現在の日付の 0 時）を計算します。
* シーケンスの期間（すべての項目の期間の合計）を計算します。
* 任意の時点で、シーケンスの _remaining_time = (current_time - anchor_time) % sequence_duration を求めることによって、現在再生されている項目および次の項目を計算します。

絶対方法を設定するには、次の手順を実行します。

1. チャネルオーサーに移動し、次の図に示すようにシーケンスコンポーネントをクリックします。
1. その設定ダイアログを開きます。
1. 「**方法**」を編集し、「絶対」を追加します。

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >プレーヤーの OS のクロックが同一である必要があります。

**OS X でクロックを揃える**：OS X でクロックを揃えるには、以下の手順に従います。

1. 各 OSX ボックスで、**日付と時刻**&#x200B;環境設定を開きます。
1. 「**日付と時刻を自動的に設定**」をオンにします。
1. ドロップダウンの値 0.pool.ntp.org、1.pool.ntp.org、2.pool.ntp.org、3.pool.ntp.org、time.apple.com を貼り付けるか、単に *sudo ntpdate -u -v 0.pool.ntp.org* を実行します。
1. 2 台以上のプレーヤーを起動します。

プレーヤーが新しく割り当てられたシーケンスを開始するまでに時間がかかることがあります。
