---
title: Tizen プレーヤー
description: このページでは、Tizen プレーヤーのインストールと動作について説明します。
translation-type: ht
source-git-commit: b3209d1dcce6defff347f288c704a1e7ea075ecf
workflow-type: ht
source-wordcount: '230'
ht-degree: 100%

---


# Tizen プレーヤーの実装 {#tizen-player}

## Tizen プレーヤーのインストール {#installing-tizen-player}

次の手順に従って、AEM Screens 用の Tizen プレーヤーを実装します。

1. [**AEM 6.5 プレーヤーダウンロード**](https://download.macromedia.com/screens/)ページに移動して、Tizen プレーヤーをダウンロードします。

1. ローカルマシンから Tizen player（.zip）ファイルをインストールします。

## ローカルサーバーの設定と Zip ファイルの抽出 {#setting-local-server}

次の手順に従ってローカルサーバーを設定し、抽出したファイルをコピーします。

1. ローカルマシンの IP アドレスを取得します。
   >[!NOTE]
   >お使いのプラットフォームでローカルサーバーを有効にする方法については、公式のドキュメントを参照してください。

1. ターミナルから、解凍されたインストーラーフォルダーと同じディレクトリに移動し、localhost が動作しているかどうかを確認します。

1. Tizen プレーヤーは、ローカルサーバーからインストーラーをダウンロードします。

1. `AEMScreensPlayer.wgt` や `sssp_config.xml`など、抽出した 2 つのファイルを、ローカルサーバーのルートディレクトリにコピーします。

### Samsung デバイスでの更新の構成 {#config-updates}

Samsung デバイスの次の手順に従って、デバイスに AEM Screens プレーヤーをインストールします。

1. Samsung デバイスに移動します。

1. デバイスのリモートを使用して「**ホーム**」ボタンをクリックし、「**URL ランチャー設定**」を選択します。

1. Localhost サーバーの IP アドレスを入力します。

1. **デベロッパーモード**&#x200B;から「**リモート**」を選択します。

1. デバイスのリモートから「**ホーム**」ボタンをクリックし、「**URL ランチャー**」を選択します。

1. これで、AEM Screens プレーヤーは Samsung デバイスに自動的にインストールして起動します。



