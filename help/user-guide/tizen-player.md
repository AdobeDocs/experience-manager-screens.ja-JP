---
title: Tizen プレーヤー
description: このページでは、Tizen プレーヤーのインストールと動作について説明します。
translation-type: tm+mt
source-git-commit: 1ec3e3541755550f719dbe53e83326d9796de14f
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 28%

---


# Tizen プレーヤーの実装 {#tizen-player}

## Tizen プレーヤーのインストール {#installing-tizen-player}

次の手順に従って、AEM Screens 用の Tizen プレーヤーを実装します。

1. [AEM 6.5 プレーヤーダウンロード](https://download.macromedia.com/screens/)ページに移動して、Tizen プレーヤーをダウンロードします。

1. ローカルマシンからTizenプレーヤー&#x200B;*(.zip)*&#x200B;ファイルをインストールします。

## ローカルサーバーの設定と Zip ファイルの抽出 {#setting-local-server}

次の手順に従ってローカルサーバーを設定し、抽出したファイルをコピーします。

1. ローカルマシンの IP アドレスを取得します。
   >[!NOTE]
   >お使いのプラットフォームでローカルサーバーを有効にする方法については、公式のドキュメントを参照してください。

1. ターミナルから、解凍されたインストーラーフォルダーと同じディレクトリに移動し、localhost が動作しているかどうかを確認します。

1. Tizen プレーヤーは、ローカルサーバーからインストーラーをダウンロードします。

1. `AEMScreensPlayer.wgt`や`sssp_config.xml`などの抽出した2つのファイルを、ローカルのApache Webサーバーのルートディレクトリにコピーします。

   >[!NOTE]
   >`AEMScreensPlayer.wgt`は実際のTizenプレーヤーアプリケーションで、`sssp_config.xml`はこのマップに関する情報を含んでおり、Tizenデバイスにインストールするのに役立ちます。

### Samsung デバイスでの更新の構成 {#config-updates}

Samsung デバイスの次の手順に従って、デバイスに AEM Screens プレーヤーをインストールします。

1. Samsungデバイスに移動し、電源を入れます。

1. デバイスのリモートから&#x200B;**MENU**&#x200B;ボタンをクリックし、左のナビゲーションバーから&#x200B;**System**&#x200B;まで下にスクロールします。

1. 下にスクロールし、「**URLランチャーで再生**」オプションを選択します。
   ![画像](/help/user-guide/assets/tizen/url-launcher.png)

1. リモートから&#x200B;**ホーム**&#x200B;ボタンを押します。

1. Localhost サーバーの IP アドレスを入力します。

1. **デベロッパーモード**&#x200B;から「**リモート**」を選択します。

1. デバイスのリモートから「**ホーム**」ボタンをクリックし、「**URL ランチャー**」を選択します。

1. これで、AEM Screens プレーヤーは Samsung デバイスに自動的にインストールして起動します。

## Tizen Playerの一括プロビジョニング{#bulk-provisioning-tizen-player}

>[!NOTE]
>多数のデバイスに対して各デバイスの管理UIにAEMサーバのアドレスを手動で入力するのは、面倒な作業になる場合があります。 ソリューションの展開と管理には、Samsung Remote Management (RMS)ソリューションを使用することをお勧めします。 詳細については、[Samsung Remote Management Service (RMS)](#enroll-tizen-device-rm)へのTizenデバイスの登録を参照してください。

次の手順に従って、起動時にAEM作成者インスタンスを指すようにアプリケーションを一括プロビジョニングします。

1. [Tizen Studio](https://developer.tizen.org/development/tizen-studio/download)をダウンロードしてインストールします。
1. Tizen studioを使用して`wgt`ファイルを開きます。
1. ファイル`firmware-platform.js`を開き、`DEFAULT_PREFERENCES`を探し、サーバーURLをAEM作成者URLに変更して保存します。
1. 新しい`wgt`ファイルを構築します。

   >[!NOTE]
   >署名の証明書を作成または設定する必要がある場合があります。

1. この新しい`wgt`ファイルRMSを展開し、プレーヤーの起動時に自動的にサーバーを指すようにします。これにより、すべてのデバイスに手動で入力する必要がなくなります。

### TizenデバイスをSamsung Remote Management Service(RMS)に登録する{#enroll-tizen-device-rms}

次の手順に従って、TizenデバイスをSamsung Remote Management Service (RMS)に登録し、URLランチャーをリモート構成します。

>[!NOTE]
>ネットワーク設定とモニタを確認します。

1. リモートのMenuキーを押し、Systemキーを押して、Play ViaでEnterキーを押します。

   >[!NOTE]
   >画面が「URLランチャーを使用して再生」に設定されていることを確認します。
1. **メニュー** -> **ネットワーク** -> **サーバーネットワーク設定**&#x200B;に移動し、**Enter**&#x200B;キーを押します。

1. 「Server Address」に移動し、MagicInfo URLアクセスを入力して「Done」を押します。

1. MISにログインした後、「デバイス」タブに移動します。
1. 先ほど設定したデバイスのIPアドレスやMacアドレスを確認して探します。
1. デバイスが見つかったら、チェックボックスをクリックし、「Approve」を選択します
1. 画面がURLランチャーを使用して再生するように設定されていることを確認してください
1. リモートのMenuキーを押し、Systemキーを押して、Play ViaでEnterキーを押します
1. メニュー/ネットワーク/サーバーネットワーク設定に移動し、Enterキーを押します。
1. 「サーバーアドレス」に移動し、MagicInfo URLアクセスを入力して「完了」を押します。
1. TLSを使用するか、使用しないかの状況に応じて設定
1. 「port」に移動し、サーバーからポート番号を選択します。
1. オプションの準備が整ったら、「保存」をクリックします。



