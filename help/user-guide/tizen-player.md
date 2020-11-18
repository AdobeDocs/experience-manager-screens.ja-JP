---
title: ティゼン・プレイヤー
description: このページでは、Tizen Playerのインストールと動作について説明します。
translation-type: tm+mt
source-git-commit: 835da341fcee8e4abb3375c43a0a130d3f79d859
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 1%

---


# Tizen Playerの実装 {#tizen-player}

## Tizen Playerのインストール {#installing-tizen-player}

次の手順に従って、AEM Screens用のTizen Playerを実装します。

1. 「 [**AEM 6.5 Player Downloads**](https://download.macromedia.com/screens/) 」ページに移動してTimen Playerをダウンロードします。

1. ローカルマシンからTizen Player(.zip)ファイルをインストールします。

## ローカルサーバーの設定とZipファイルの抽出 {#setting-local-server}

次の手順に従ってローカルサーバーを設定し、抽出したファイルをコピーします。

1. ローカルマシンのIPアドレスを取得します。

   >[!NOTE]
   >次のコマンドを使用して、マシンのターミナルからIPアドレスを取得できます。
   >* **Mac**: `ifconfig`
   >* **Windows**: `ipconfig`


1. ターミナルから、解凍されたインストーラーフォルダーと同じディレクトリに移動し、localhostが動作しているかどうかを確認します。

   >[!NOTE]
   >**Mac**&#x200B;の場合は、サー `http://localhost``http` バーが実行されているかどうかを入力して確認します。

1. Tizen Playerは、ローカルサーバーからインストーラーをダウンロードします。

1. 抽出した2つのファイルをにコピー `AEMScreensPlayer.wgt` し `sssp_config.xml` ま `/Library/WebServer/Documents`す。

### Samsungデバイスでの更新の設定 {#config-updates}

Samsungデバイスの次の手順に従って、デバイスにAEM Screensプレイヤーをインストールします。

1. Samsungデバイスに移動し、localhostサーバーを指定します。
1. 「 **設定」から「** URLランチャーの設定 **** 」を選択し、localhostサーバーのIPアドレスを入力します。
1. Web Appをインストールします。
1. **開発者モードから** 「Remote ****」を選択します。
1. これで、AEM ScreensプレイヤーがSamsungデバイスに自動的にインストールされます。


