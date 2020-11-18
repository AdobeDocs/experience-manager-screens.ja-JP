---
title: ティゼン・プレイヤー
description: このページでは、Tizen Playerのインストールと動作について説明します。
translation-type: tm+mt
source-git-commit: baefade9fa013bc77ed1f112d0ad2098c992dde5
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 1%

---


# Tizen Playerの実装 {#tizen-player}

## Tizen Playerのインストール {#installing-tizen-player}

次の手順に従って、AEM Screens用のTizen Playerを実装します。

1. 「 [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) 」ページに移動してTimen Playerをダウンロードします。

1. ローカルマシンからTizen Player(.zip)ファイルをインストールします。

1. ローカルマシンのIPアドレスを取得します。

   >[!NOTE]
   >マシンのターミナルで、次のコマンドを入力します。
   >**Mac** useコマンド `ifconfig`
   >**Windows**、コマンドを使用 `ipconfig`

1. ターミナルから、解凍されたインストーラーフォルダーと同じディレクトリに移動し、localhostが動作しているかどうかを確認します。

   >[!NOTE]
   >**Mac**&#x200B;の場合は、サー `http://localhost``http` バーが実行されているかどうかを入力して確認します。

1. Tizen Playerは、ローカルサーバーからインストーラーをダウンロードします。

1. 抽出した2つのファイルをにコピー `AEMScreensPlayer.wgt` し `sssp_config.xml` ま `/Library/WebServer/Documents`す。

### SamSungデバイスの構成の更新 {#config-updates}

Samsungデバイスの次の手順に従って、デバイスにAEM Screensプレイヤーをインストールします。

1. Samsung Remoteの **Home** （ホーム）ボタンをクリックします。
1. 「 **設定」から** 「 **URLランチャー**」を選択します。
1. 開発者モードから **「リモート** 」を選択します。
1. Web Appをインストールし、コンピューターのIPアドレスを入力します。
AEM Screens・プレイヤーは、Samsungデバイスに自動的にインストールする必要があります。


