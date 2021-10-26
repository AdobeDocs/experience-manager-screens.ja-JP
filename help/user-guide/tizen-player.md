---
title: Tizen プレーヤー
description: このページでは、Tizen プレーヤーのインストールと動作について説明します。
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: 0f99b96e90f0aac6bf923343ecefa1708d5cfd17
workflow-type: ht
source-wordcount: '1222'
ht-degree: 100%

---

# Tizen プレーヤーの実装 {#tizen-player}

## Tizen プレーヤーのインストール {#installing-tizen-player}

次の手順に従って、AEM Screens 用の Tizen プレーヤーを実装します。

1. [AEM Screens Player のダウンロード](https://download.macromedia.com/screens/)ページに移動して、Tizen プレーヤーをダウンロードします。

1. ローカルマシンから Tizen プレーヤー&#x200B;*（.zip）*&#x200B;ファイルをインストールします。

## HTTP サーバーのセットアップ {#setting-local-server}

>[!NOTE]
> zip ファイルを展開し、`http server` を通じて Tizen プレーヤーを入手できるようにします（`http server` はローカルサーバーまたは Apache サーバーである必要はありません）。

次の手順に従います。

1. 展開した 2 つのファイル（`AEMScreensPlayer.wgt`、`sssp_config.xml` など）をローカル Apache Web サーバーのルートディレクトリにコピーします。

   >[!NOTE]
   >`AEMScreensPlayer.wgt` は実際の Tizen プレーヤーアプリケーションです。`sssp_config.xml` には、Tizen プレーヤーを Tizen デバイスにインストールする際に役立つ、このマップに関する情報が記載されています。

1. ローカル HTTP サーバーの IP または URL を取得します（手順 2 で、ルートフォルダーではなくサブフォルダーに展開した場合は、展開したファイルを含むフォルダーのパスも取得します）。

1. Tizen プレーヤーは、ローカルサーバーからインストーラーをダウンロードします。

### Tizen プレーヤーの命名 {#name-tizen}

ユーザーにわかり-やすいデバイス名を Tizen プレーヤーに割り当てて、そのデバイス名を Adobe Experience Manager（AEM）に送信することができます。この機能により、Tizen プレーヤーに名前を付けるだけでなく、適切なコンテンツを簡単に割り当てることもできます。

>[!NOTE]
>プレーヤー名は、登録にのみ選択できます。プレーヤーの登録後は、プレーヤー名を変更できなくなります。

Tizen プレーヤーに名前を設定するには、次の手順に従います。

1. リモコンのメニューボタンを押します。
1. **Network**／**Device Name** に移動して、プレーヤーに名前を割り当てます。

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
>ブラウザーエンジンの中には、AEM 6.5 から AEM 6.7 までのバージョンが発行するログイントークンで使用される *SameSite=None* 属性に対応していないものが一部あります。この問題は、通常、ブラウザーを入手可能な最新のバージョンにアップグレードすることで解決できます。ただし、スマートディスプレイやセットトップボックスのように、ブラウジングエンジンが組み込まれているデバイスの場合など、そのようなアップグレードが不可能な場合があります。

*SameSite=None* を使用する場合に、その属性に対応していないこれらのクライアントを適用対象外にするには、次の手順に従います。

1. Adobe Experience Manager（AEM）Service Pack 6.5.7 にアップグレードします。

1. AEM を再起動した後、`/system/console/configMgr` に移動し、**Adobe Granite Token Authentication Handler** を探します。**SameSite** の値を「**None**」に設定します。

1. 新しいオプション「*User agents to be exempted from samesite attribute*」が表示されます。*SameSite=None* 属性に対応していないユーザーエージェントを表す正規表現を、このオプションに設定します。
   >[!NOTE]
   >詳しくは、[SameSite=None: Known Incompatible Clients](https://www.chromium.org/updates/same-site/incompatible-clients)（「SameSite=None」に対応していない既知のクライアント）を参照してください。Tizen プレーヤーの場合は `(.*)Tizen(.*)` という正規表現を使用します。

1. AEM 6.5.5 以降のインスタンスに Tizen プレーヤーを登録します。これによりプレーヤーが登録され、コンテンツが正常に表示されます。

## Tizen プレーヤーのリモートプロビジョニング {#remote-provisioning}

Tizen プレーヤーをリモートでプロビジョニングすると、数百台から数千台の Samsung Tizen ディスプレイを、大きな手間をかけずにデプロイできます。これにより、サーバー URL や一括登録コードなどのパラメーター（Screens as a Cloud Service の場合はクラウドモードとクラウドトークン）を各プレーヤーに手動で設定する手間を省けます。

この機能を利用すると、Tizen プレーヤーをリモートで設定し、必要に応じてそれらの設定を一元的に更新できます。必要なのは、Tizen アプリケーション `(wgt and xml file)` をホストするための `HTTP` サーバーと、適切なパラメーターを記述した `config.json` を保存するためのテキストエディターだけです。

Tizen デバイスに URL ランチャーアドレスを設定してあることを確認します（リモコンの「Home」ボタンを押して「URL Launcher Settings」に移動）。
Tizen アプリケーションをホストする `HTTP` サーバー上で、`config.json` ファイルを `wgt` ファイルと同じ場所に置きます。ファイル名は `config.json` にする必要があります。
Tizen プレーヤーがインストールされ、プレーヤーの起動時（および再起動時）に `config.json` ファイル内の設定がチェックされ適用されます。

### JSON ポリシーの例 {#example-json}

```java
{
  "server":  "http://your-aem-instance.com:4502",
  "registrationKey": "AdobeRocks!!",
  "enableAdminUI": true,
  "enableOSD": true,
  "enableActivityUI": true
}
```

### ポリシーの属性と目的 {#policy-attributes}

次の表に、ポリシーとその機能の概要を示します。

>[!NOTE]
>ポリシー設定は厳格に適用されます。プレーヤーの Admin UI で、手動で上書きされることはありません。特定のポリシーに対して手動のプレーヤー設定を許可する場合は、ポリシー設定にポリシーを指定しないでください。例えば、再起動スケジュールの手動設定を許可する場合は、ポリシー設定にキー `rebootSchedule` を指定しないでください。ポリシー設定は、プレーヤーが再読み込みされるたびに読み取られます。

| **ポリシー名** | **目的** |
|---|---|
| server | Adobe Experience Manager（AEM） サーバーの URL。 |
| registrationKey | 事前共有キーを使用したデバイスの一括登録に使用されます。 |
| resolution | デバイスの解像度。 |
| rebootSchedule | プレーヤーを再起動するスケジュール。 |
| enableAdminUI | サイト上でデバイスを設定するための Admin UI を有効にします。設定が完了して実稼働になったら、false に設定します。 |
| enableOSD | ユーザー用のチャネルスイッチャー UI を有効にし、デバイスのチャネルを切り替えます。設定が完了して実稼働になったら、false に設定することを検討します。 |
| enableActivityUI | 有効にすると、ダウンロードや同期などのアクティビティの進行状況を表示します。トラブルシューティング用に有効にしておき、設定が完了して実稼働になったら無効にします。 |
| cloudMode | Tizen プレーヤーから Screens as a Cloud Service に接続する場合は、true に設定します。AMS またはオンプレミス AEM に接続する場合は、false に設定します。 |
| cloudToken | Screens as a Cloud Service に登録するための登録トークン。 |


## Samsung Remote Management Service（RMS）への Tizen デバイスの登録 {#enroll-tizen-device-rms}

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
