---
title: Tizen プレーヤー
description: このページでは、Tizen プレーヤーのインストールと動作について説明します。
translation-type: tm+mt
source-git-commit: aaaba2ed94fc950fec9264fef441bebf761576be
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 11%

---


# Tizen プレーヤーの実装 {#tizen-player}

## Tizen プレーヤーのインストール {#installing-tizen-player}

次の手順に従って、AEM Screens 用の Tizen プレーヤーを実装します。

1. [AEM Screensプレイヤーのダウンロード数](https://download.macromedia.com/screens/)ページに移動して、Tizen Playerをダウンロードします。

1. ローカルマシンからTizenプレーヤー&#x200B;*(.zip)*&#x200B;ファイルをインストールします。

## ローカルサーバーの設定と Zip ファイルの抽出 {#setting-local-server}

>[!NOTE]
> zipファイルを展開し、Tizenプレイヤーを`http server`から入手できるようにします。 （`http server`は、ローカルまたはApacheサーバーである必要はありません）。

その場合は、次の手順に従います。

1. `AEMScreensPlayer.wgt`や`sssp_config.xml`などの抽出した2つのファイルを、ローカルのApache Webサーバーのルートディレクトリにコピーします。

   >[!NOTE]
   >`AEMScreensPlayer.wgt`は実際のTizenプレーヤーアプリケーションで、`sssp_config.xml`はこのマップに関する情報を含んでおり、Tizenデバイスにインストールするのに役立ちます。

1. ローカルHTTPサーバーのIPまたはURLを取得します（ルートフォルダーではなくサブフォルダーに抽出した場合は、手順2で抽出したファイルを含むフォルダーのパス）。

1. Tizen プレーヤーは、ローカルサーバーからインストーラーをダウンロードします。

### Samsung デバイスでの更新の構成 {#config-updates}

Samsung デバイスの次の手順に従って、デバイスに AEM Screens プレーヤーをインストールします。

1. Samsungデバイスに移動し、電源を入れます。

1. デバイスのリモートから&#x200B;**MENU**&#x200B;ボタンをクリックし、左のナビゲーションバーから&#x200B;**System**&#x200B;まで下にスクロールします。

1. 下にスクロールし、「****&#x200B;で再生」オプションを選択して、**URLランチャー**に変更します。
   ![画像](/help/user-guide/assets/tizen/rms-2.png)

1. URLランチャーを設定したら、リモートから&#x200B;**ホーム**&#x200B;ボタンを押します。

1. **URLランチャーの設定**&#x200B;に移動し、localhostサーバーのIPアドレスを入力して、「**完了**」をクリックします。
   >[!NOTE]
   >Tizenプレイヤーがhttpサーバーに接続できる必要があります。

1. これで、AEM Screens プレーヤーは Samsung デバイスに自動的にインストールして起動します。

   >[!NOTE]
   >Tizenデバイスと`http`サーバーは両方とも接続可能である必要があります。つまり、サーバーはTizenプレーヤーに到達可能である必要があります。


## SameSite Cookieに関する問題を除外するユーザーエージェント{#exempting-user-agents}

>[!IMPORTANT]
>**この節は、Adobe Experience Manager(AEM) 6.5.5からAEM 6.5.7**に適用
>AEM 6.5からAEM 6.7に発行されたログイントークンに使用される&#x200B;*SameSite=None*&#x200B;属性と互換性のないブラウザーエンジンがいくつかあります。ほとんどの場合、ブラウザーを最新バージョンにアップグレードすると問題が解決します。 スマートディスプレイの場合、トップボックスの設定、ブラウズエンジンが組み込まれた他のデバイスなど、そのようなアップグレードが不可能な場合があります。

次の手順に従って、*SameSite=None*&#x200B;を使用する場合に、これらの互換性のないクライアントを除外します。

1. Adobe Experience Manager(AEM) Service Pack 6.5.8にアップグレードします。

1. AEMを再起動した後、`/system/console/configMgr`に移動し、**AdobeGranite Token Authentication Handler**&#x200B;を探します。 **SameSite**&#x200B;値の値を&#x200B;**None**&#x200B;に設定します。

1. 新しいオプション&#x200B;*同じ属性*&#x200B;から除外するユーザーエージェントが表示されます。 *SameSite=None*&#x200B;属性と互換性のないユーザーエージェントに対応するregexを設定します。
   >[!NOTE]
   >[SameSite=Noneを参照：互換性のない既知のクライアント](https://www.chromium.org/updates/same-site/incompatible-clients)を参照してください。 ティーゼンの選手にはregexを使用します。`(.*)Tizen(.*)`.

1. AEM 6.5.5以降のインスタンスに対してTizenプレーヤーを登録します。通常は、コンテンツが登録され、表示されます。

## Tizen Playerの一括プロビジョニング{#bulk-provisioning-tizen-player}

>[!NOTE]
>多数のデバイスに対して各デバイスの管理UIにAEMサーバのアドレスを手動で入力するのは、面倒な作業になる場合があります。 大規模なソリューションの展開と管理には、Samsung Remote Management (RMS)ソリューションを使用することをお勧めします。 詳細については、[Samsung Remote Management Service (RMS)](#enroll-tizen-device-rm)へのTizenデバイスの登録を参照してください。

次の手順に従って、起動時にAEM作成者インスタンスを指すようにアプリケーションを一括プロビジョニングします。

1. [Tizen Studio](https://developer.tizen.org/development/tizen-studio/download)をダウンロードしてインストールします。
1. Tizen studioを使用して`wgt`ファイルを開きます。
1. ファイル`firmware-platform.js`を開き、`DEFAULT_PREFERENCES`を探し、サーバーURLをAEM作成者URLに変更して保存します。
1. 新しい`wgt`ファイルを構築します。

   >[!NOTE]
   >署名の証明書を作成または設定する必要がある場合があります。

1. この新しい`wgt`ファイルをRMSまたはURLランチャーを使用して展開し、プレーヤーの起動時に自動的にサーバーを指すようにします。これにより、すべてのデバイスに手動で入力する必要がなくなります。

### TizenデバイスをSamsung Remote Management Service (RMS)に登録する{#enroll-tizen-device-rms}

次の手順に従って、TizenデバイスをSamsung Remote Management Service (RMS)に登録し、URLランチャーをリモート構成します。

>[!NOTE]
>ネットワーク設定とモニタを確認します。

1. **メニュー** -> **ネットワーク** -> **サーバーネットワーク設定**&#x200B;に移動し、**Enter**&#x200B;キーを押します。

1. サーバーアドレスに移動し、MagicInfo URLアクセスを入力して、**完了**&#x200B;キーを押します。

1. 必要に応じて、TLSをセットアップします。 ポートに移動し、サーバーからポート番号を選択して、「**保存**」をクリックします。

1. 「**デバイス**」タブに移動し、設定したデバイスを確認します。 デバイスが見つかったら、チェックボックスをクリックし、**承認**&#x200B;を選択します。

   >![画像](/help/user-guide/assets/tizen/rms-3.png)

1. 必要な情報を入力し、デバイスグループを選択します。 「**OK**」をクリックして承認プロセスを完了します。

   >![画像](/help/user-guide/assets/tizen/rms-7.png)

1. 承認されたデバイスは、デバイスリストに表示されます。 次の図に示すように、デバイスのボックスにある&#x200B;*「情報*」ボタン(**i**)をクリックします。

   >![画像](/help/user-guide/assets/tizen/rms-6.png)

1. デバイス情報ダイアログボックスが表示されます。 「**デバイス情報**」タブを選択し、「**編集**」をクリックします。

   >![画像](/help/user-guide/assets/tizen/rms-5.png)

1. デバイスのオプションを編集し、「**Setup**」タブを選択します。 **「URLランチャー**」セクションに移動し、wgtをホストするURLと`SSSP config file`を入力して`SSSP`アプリケーションをインストールします。次の図を参照してください。

   ![画像](/help/user-guide/assets/tizen/rms-9.png)

1. 「**保存**」をクリックすると、変更内容が表示画面に表示されます。

