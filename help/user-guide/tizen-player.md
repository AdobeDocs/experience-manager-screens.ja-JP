---
title: Tizen プレーヤー
description: このページでは、Tizen プレーヤーのインストールと動作について説明します。
translation-type: tm+mt
source-git-commit: 4c005ace7b1da94ed527164d6cfa09666d746273
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 21%

---


# Tizen プレーヤーの実装 {#tizen-player}

## Tizen プレーヤーのインストール {#installing-tizen-player}

次の手順に従って、AEM Screens 用の Tizen プレーヤーを実装します。

1. [AEM 6.5 プレーヤーダウンロード](https://download.macromedia.com/screens/)ページに移動して、Tizen プレーヤーをダウンロードします。

1. ローカルマシンからTizenプレーヤー&#x200B;*(.zip)*&#x200B;ファイルをインストールします。

## 同じサイトのCookieに関する問題を除外するユーザーエージェント{#exempting-user-agents}

>[!IMPORTANT]
>**この節はAEM 6.5.5からAEM 6.5.7**に適用
>AEM 6.5からAEM 6.7に発行されたログイントークンで使用される&#x200B;*SameSite=None*&#x200B;属性と互換性のないブラウザーエンジンがあります。ほとんどの場合、ブラウザーを最新バージョンにアップグレードすると問題が解決します。 スマートディスプレイの場合、トップボックスの設定、ブラウズエンジンが組み込まれた他のデバイスなど、そのようなアップグレードが不可能な場合があります。 SameSite=Noneを使用する場合に、これらの互換性のないクライアントを除外するには、次の手順を使用してください。

1. パッチ&#x200B;*jarファイル*&#x200B;を`https://artifactory.corp.adobe.com/artifactory/maven-aem-release-local/com/adobe/granite/crx-auth-token/2.6.10/`からダウンロードします。

1. AEMの`/system/console/bundles`に移動し、「`install/update`」ボタンをクリックします。

1. `crx-auth-token` jarファイルをインストールします。 このjarは認証に関連しているので、このjarをインストールした後、AEMをシャットダウンして再起動する必要がある場合があります。

1. AEMを再起動した後、`/system/console/configMgr`に移動し、**AdobeGranite Token Authentication Handler**&#x200B;を探します。 「SameSite」設定の値を「None」に設定します。

1. 新しいオプション&#x200B;*同じ属性*&#x200B;から除外するユーザーエージェントが表示されます。 *SameSite=None*&#x200B;属性と互換性のないユーザーエージェントに対応するregexを設定します。
   >[!NOTE]
   >[SameSite=Noneを参照：互換性のない既知のクライアント](https://www.chromium.org/updates/same-site/incompatible-clients)を参照してください。

1. ティーゼンの選手にはregexを使用します。`(.*)Tizen (4|5)(.*)` AEM 6.5.5以上のインスタンスに対してTizenプレーヤーを登録します。通常は登録してコンテンツを表示します。


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
   ![画像](/help/user-guide/assets/tizen/rms-2.png)

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

1. **メニュー** -> **ネットワーク** -> **サーバーネットワーク設定**&#x200B;に移動し、**Enter**&#x200B;キーを押します。

   >[!NOTE]
   >画面が「URLランチャーを使用して再生」に設定されていることを確認します。
   >![画像](/help/user-guide/assets/tizen/rms-2.png)

1. 「Server Address」に移動し、MagicInfo URLアクセスを入力して「Done」を押します。

1. 必要に応じて、TLSをセットアップします。 ポートに移動し、サーバーからポート番号を選択します。 「**保存**」をクリックします。

1. 「デバイス」タブに移動し、設定したデバイスを探します。

1. デバイスが見つかったら、チェックボックスをクリックし、**承認**&#x200B;を選択します。

1. 必要な情報を入力し、デバイスグループを選択します。 「**OK**」をクリックして承認プロセスを完了します。

   >![画像](/help/user-guide/assets/tizen/rms-7.png)

1. 承認されたデバイスは、デバイスリストに表示されます。 デバイスのボックス&#x200B;**i**&#x200B;にある[*情報*]ボタンをクリックします。

   >![画像](/help/user-guide/assets/tizen/rms-6.png)

1. デバイス情報ダイアログボックスが表示されます。 「**デバイス情報**」タブを選択し、「**編集**」をクリックします。

1. 「Edit Device」オプションを選択し、「**Setup**」タブを選択します。 **「URLランチャー**」セクションに移動し、wgtをホストするURLと`SSSP config file`を入力して`SSSP`アプリケーションをインストールします。次の図を参照してください。

   ![画像](/help/user-guide/assets/tizen/rms-9.png)

1. 「**保存**」をクリックすると、変更内容が表示画面に表示されます。




