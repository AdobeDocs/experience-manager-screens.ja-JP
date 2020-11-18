---
title: ティゼン・プレイヤー
description: このページでは、Tizen Playerのインストールと動作について説明します。
translation-type: tm+mt
source-git-commit: b3209d1dcce6defff347f288c704a1e7ea075ecf
workflow-type: tm+mt
source-wordcount: '230'
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
   >お使いのプラットフォームでローカルサーバーを有効にする方法については、公式のドキュメントを参照してください。

1. ターミナルから、解凍されたインストーラーフォルダーと同じディレクトリに移動し、localhostが動作しているかどうかを確認します。

1. Tizen Playerは、ローカルサーバーからインストーラーをダウンロードします。

1. およびなど、抽出した2つのファイルを、ローカルサーバーのルートディレクトリ `AEMScreensPlayer.wgt``sssp_config.xml` にコピーします。

### Samsungデバイスでの更新の設定 {#config-updates}

Samsungデバイスの次の手順に従って、デバイスにAEM Screensプレイヤーをインストールします。

1. Samsungデバイスに移動します。

1. デバイスのリモートを使用して **ホーム** ボタンをクリックし、 **URLランチャーの設定を選択します**。

1. localhostサーバーのIPアドレスを入力します。

1. **開発者モードから** 「Remote ****」を選択します。

1. デバイスのリモートから **Home** ( **ホーム)ボタンをクリックし、「** URL Launcher（URLランチャー）」を選択します。

1. これで、AEM Screens・プレイヤーはSamsungデバイスに自動的にインストールして起動します。



