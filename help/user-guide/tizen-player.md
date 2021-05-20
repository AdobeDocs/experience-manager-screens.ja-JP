---
title: Tizen プレーヤー
description: このページでは、Tizen プレーヤーのインストールと動作について説明します。
feature: Screens の管理、プレーヤー
role: Administrator
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 100%

---

# Tizen プレーヤーの実装 {#tizen-player}

## Tizen プレーヤーのインストール {#installing-tizen-player}

次の手順に従って、AEM Screens 用の Tizen プレーヤーを実装します。

1. [AEM Screens Player のダウンロード](https://download.macromedia.com/screens/)ページに移動して、Tizen プレーヤーをダウンロードします。

1. ローカルマシンから Tizen プレーヤー&#x200B;*（.zip）*&#x200B;ファイルをインストールします。

## ローカルサーバーの設定と Zip ファイルの展開 {#setting-local-server}

>[!NOTE]
> zip ファイルを展開し、`http server` を通じて Tizen プレーヤーを入手できるようにします（`http server` はローカルサーバーまたは Apache サーバーである必要はありません）。

次の手順に従います。

1. 展開した 2 つのファイル（`AEMScreensPlayer.wgt`、`sssp_config.xml` など）をローカル Apache Web サーバーのルートディレクトリにコピーします。

   >[!NOTE]
   >`AEMScreensPlayer.wgt` は実際の Tizen プレーヤーアプリケーションです。`sssp_config.xml` には、Tizen プレーヤーを Tizen デバイスにインストールする際に役立つ、このマップに関する情報が記載されています。

1. ローカル HTTP サーバーの IP または URL を取得します（手順 2 で、ルートフォルダーではなくサブフォルダーに展開した場合は、展開したファイルを含むフォルダーのパスも取得します）。

1. Tizen プレーヤーは、ローカルサーバーからインストーラーをダウンロードします。

### Samsung デバイスでの更新の構成 {#config-updates}

Samsung デバイスの次の手順に従って、デバイスに AEM Screens プレーヤーをインストールします。

1. Samsung デバイスに移動し、電源を入れます。

1. デバイスのリモートコントローラーで「**MENU**」ボタンをクリックし、左のナビゲーションバーで「**System**」まで下にスクロールします。

1. 下にスクロールし、「**Play via**」オプションを選択して「**URL Launcher**」に変更します。
   ![画像](/help/user-guide/assets/tizen/rms-2.png)

1. URL ランチャーを設定したら、リモートコントローラーの「**Home**」ボタンを押します。

1. 「**URL Launcher Settings**」に移動し、localhost サーバーの IP アドレスを入力して、「**Done**」をクリックします。
   >[!NOTE]
   >Tizen プレーヤーが http サーバーに接続できるようになります。

1. これで、AEM Screens プレーヤーが Samsung デバイスに自動的にインストールされて起動します。

   >[!NOTE]
   >Tizen デバイスと `http` サーバーが相互に接続できるようになり、サーバーは Tizen プレーヤーに到達できます。


## cookie の SameSite 属性に対応していないユーザーエージェントの適用除外 {#exempting-user-agents}

>[!IMPORTANT]
>**この節の内容は、Adobe Experience Manager（AEM）6.5.5 から AEM 6.5.7** までのバージョンに適用されます。
>ブラウザーエンジンの中には、AEM 6.5 から AEM 6.7 までのバージョンが発行するログイントークンで使用される *SameSite=None* 属性に対応していないものが一部あります。この問題は、ほとんどの場合、ブラウザーを入手可能な最新のバージョンにアップグレードすることで解決できます。ただし、スマートディスプレイやセットトップボックスのように、ブラウジングエンジンが組み込まれているデバイスの場合など、そのようなアップグレードが不可能な場合があります。

*SameSite=None* を使用する場合に、その属性に対応していないこれらのクライアントを適用対象外にするには、次の手順に従います。

1. Adobe Experience Manager（AEM）Service Pack 6.5.7 にアップグレードします。

1. AEM を再起動した後、`/system/console/configMgr` に移動し、**Adobe Granite Token Authentication Handler** を探します。**SameSite** の値を「**None**」に設定します。

1. 新しいオプション「*User agents to be exempted from samesite attribute*」が表示されます。*SameSite=None* 属性に対応していないユーザーエージェントを表す正規表現を、このオプションに設定します。
   >[!NOTE]
   >詳しくは、[SameSite=None: Known Incompatible Clients](https://www.chromium.org/updates/same-site/incompatible-clients)（「SameSite=None」に対応していない既知のクライアント）を参照してください。Tizen プレーヤーの場合は `(.*)Tizen(.*)` という正規表現を使用します。

1. AEM 6.5.5 以降のインスタンスに Tizen プレーヤーを登録します。これによりプレーヤーが登録され、コンテンツが正常に表示されます。

## Tizen プレーヤーの一括プロビジョニング {#bulk-provisioning-tizen-player}

>[!NOTE]
>デバイス数が多い場合は、デバイスごとに管理 UI で AEM サーバーのアドレスを手動入力するのは面倒です。このような大規模なソリューションのデプロイと管理には、Samsung Remote Management（RMS）ソリューションを使用することをお勧めします。詳しくは、[Samsung Remote Management Service（RMS）への Tizen デバイスの登録](#enroll-tizen-device-rm)を参照してください。

起動時に AEM オーサーインスタンスを指すようにアプリケーションを一括でプロビジョニングするには、次の手順に従います。

1. [Tizen Studio](https://developer.tizen.org/development/tizen-studio/download) をダウンロードしインストールします。
1. Tizen Studio を使用して `wgt` ファイルを開きます。
1. `firmware-platform.js` ファイルを開き、`DEFAULT_PREFERENCES` を探して、サーバー URL を AEM オーサー URL に変更した後、ファイルを保存します。
1. 新しい `wgt` ファイルを作成します。

   >[!NOTE]
   >署名証明書の作成や設定が必要になることもあります。

1. RMS または URL ランチャーを使用して、この新しい `wgt` ファイルをデプロイします。プレーヤーは起動時に指定のサーバーを自動的に指すようになるので、デバイスごとにサーバーのアドレスを手動で入力する必要がなくなります。

### Samsung Remote Management Service（RMS）への Tizen デバイスの登録 {#enroll-tizen-device-rms}

Tizen デバイスを Samsung Remote Management Service（RMS）に登録し URL ランチャーをリモートで設定するには、次の手順に従います。

>[!NOTE]
>ネットワーク設定とモニターを確認します。

1. **Menu**／**Network**／**Server Network Settings** に移動し、**Enter** キーを押します。

1. サーバーのアドレスに移動し、MagicInfo URL アクセスを入力して、「**Done**」をクリックします。

1. 必要に応じて、TLS をセットアップします。ポートに移動し、サーバーのポート番号を選択して、「**Save**」をクリックします。

1. 「**Device**」タブに移動し、設定したデバイスを確認します。デバイスが見つかったら、チェックボックスをオンにし、「**Approve**」をクリックします。

   >![画像](/help/user-guide/assets/tizen/rms-3.png)

1. 必要な情報を入力し、デバイスグループを選択します。「**OK**」をクリックして、承認プロセスを完了します。

   >![画像](/help/user-guide/assets/tizen/rms-7.png)

1. 承認されたデバイスがデバイスリストに表示されます。デバイスボックスにある&#x200B;*情報*&#x200B;ボタン（「**i**」、次の図を参照）をクリックします。

   >![画像](/help/user-guide/assets/tizen/rms-6.png)

1. デバイス情報ダイアログボックスが表示されます。「**Device Info**」タブを選択し、「**Edit**」をクリックします。

   >![画像](/help/user-guide/assets/tizen/rms-5.png)

1. デバイスのオプションを編集し、「**Setup**」タブを選択します。「**URL Launcher**」セクションに移動し、`SSSP` アプリケーションをインストールするための wgt および `SSSP config file` をホストしている URL を入力します（次の図を参照）。

   ![画像](/help/user-guide/assets/tizen/rms-9.png)

1. 「**Save**」をクリックすると、変更内容が画面に表示されます。
