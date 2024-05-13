---
title: Tizen プレーヤー
description: Tizen プレーヤーのインストールと操作について説明します。
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 45147959-b0ca-4d87-b89d-293e4b9af171
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '1217'
ht-degree: 67%

---

# Tizen プレーヤーの実装 {#tizen-player}

## Tizen プレーヤーのインストール {#installing-tizen-player}

AEM Screens用の Tizen プレーヤーを実装するには、次の手順に従います。

1. に移動します。 [AEM Screens Player のダウンロード](https://download.macromedia.com/screens/) tizen プレーヤーをダウンロードできます。

1. Tizen プレーヤーのインストール *（.zip）* ローカルマシンのファイル。

## HTTP サーバーのセットアップ {#setting-local-server}

>[!NOTE]
> zip ファイルを展開し、`http server` を通じて Tizen プレーヤーを入手できるようにします（`http server` はローカルサーバーまたは Apache サーバーである必要はありません）。

次の手順に従います。

1. 展開した 2 つのファイル（`AEMScreensPlayer.wgt`、`sssp_config.xml` など）をローカル Apache Web サーバーのルートディレクトリにコピーします。

   >[!NOTE]
   >`AEMScreensPlayer.wgt` は実際の Tizen プレーヤーアプリケーションです。`sssp_config.xml` には、Tizen プレーヤーを Tizen デバイスにインストールする際に役立つ、このマップに関する情報が記載されています。

1. ローカル HTTP サーバーの IP または URL （ルートフォルダーではなくサブフォルダーに抽出された場合は、手順 2 で抽出されたファイルを含むフォルダーへのパス）を取得します。

1. Tizen プレーヤーは、ローカルサーバーからインストーラーをダウンロードします。

### Tizen プレーヤーの命名 {#name-tizen}

ユーザーにわかりやすいデバイス名を Tizen プレーヤーに割り当てて、そのデバイス名を Adobe Experience Manager（AEM）に送信することができます。この機能により、Tizen プレーヤーに名前を付けるだけでなく、適切なコンテンツを簡単に割り当てることもできます。

>[!NOTE]
>プレーヤー名は、登録にのみ選択できます。プレーヤーの登録後は、プレーヤー名を変更できなくなります。

Tizen プレーヤーに名前を設定するには、次の手順に従います。

1. リモコンのメニューボタンを押します。
1. に移動します。 **ネットワーク** > **デバイス名** そのため、プレーヤーに名前を割り当てることができます。

### Samsung デバイスでの更新の構成 {#config-updates}

Samsung デバイスで次の手順に従って、デバイスにAEM Screens Player をインストールします。

1. Samsung デバイスに移動し、電源を入れます。
1. デバイスのリモートコントローラーで「**MENU**」ボタンをクリックし、左のナビゲーションバーで「**System**」まで下にスクロールします。
1. 下にスクロールして、 **～を経由して遊ぶ** 「」オプションを選択して、「」に変更します **URL ランチャー** オプション。
   ![画像](/help/user-guide/assets/tizen/rms-2.png)
1. URL ランチャーを設定したら、 **ホーム** リモコンのボタンを押します。
1. 「**URL Launcher Settings**」に移動し、localhost サーバーの IP アドレスを入力して、「**Done**」をクリックします。

   >[!NOTE]
   >Tizen プレーヤーは、HTTP サーバーに接続できます。

1. AEM Screens プレーヤーが Samsung デバイスに自動的にインストールされて起動します。

   >[!NOTE]
   >Tizen デバイスと `http` サーバーが相互に接続できるようになり、サーバーは Tizen プレーヤーに到達できます。


## cookie の SameSite 属性に対応していないユーザーエージェントの適用除外 {#exempting-user-agents}

>[!IMPORTANT]
>**この節の内容は、Adobe Experience Manager（AEM）6.5.5 から AEM 6.5.7 までのバージョンに適用されます。**
>
>ブラウザーエンジンの中には、AEM 6.5.5 から AEM 6.5.7 までのバージョンが発行するログイントークンで使用される *`SameSite=None`* 属性に対応していないものが一部あります。この問題は、通常、ブラウザーを入手可能な最新のバージョンにアップグレードすれば解決できます。ただし、スマートディスプレイやセットトップボックスのように、ブラウジングエンジンが組み込まれているデバイスの場合など、そのようなアップグレードが不可能な場合があります。

*SameSite=None* を使用する場合に、その属性に対応していないこれらのクライアントを適用対象外にするには、次の手順に従います。

1. Adobe Experience Manager（AEM）Service Pack 6.5.7 にアップグレードします。

1. AEM を再起動した後、`/system/console/configMgr` に移動し、**Adobe Granite Token Authentication Handler** を探します。**SameSite** の値を「**None**」に設定します。

1. 新しいオプション *`User agents to be exempted from samesite attribute`* が表示されます。このオプションに、と互換性のないユーザーエージェントに対応する正規表現を入力します *SameSite=None* 属性。

   >[!NOTE]
   >
   >詳しくは、[SameSite=None: Known Incompatible Clients](https://www.chromium.org/updates/same-site/incompatible-clients)を参照してください。Tizen プレーヤーの場合は `(.*)Tizen(.*)` という正規表現を使用します。

1. AEM 6.5.5 以降のインスタンスに Tizen プレーヤーを登録します。これによりプレーヤーが登録され、コンテンツが正常に表示されます。

## Tizen プレーヤーのリモートプロビジョニング {#remote-provisioning}

Tizen プレーヤーをリモートでプロビジョニングすると、数百台から数千台の Samsung Tizen ディスプレイを、大きな手間をかけずにデプロイできます。 これにより、サーバー URL や一括登録コード、またはその他のパラメーターを各プレーヤーに手動で設定する必要がなくなります。また、AEM Screens as a Cloud Service がある場合は、クラウドモードとクラウドトークンの設定も同様です。

この機能を利用すると、Tizen プレーヤーをリモートで設定し、必要に応じてその設定を一元的に更新できます。必要なのは、Tizen アプリケーション `(wgt and xml file)` をホストするための `HTTP` サーバーと、適切なパラメーターを記述した `config.json` を保存するためのテキストエディターだけです。

Tizen デバイスに URL ランチャーアドレスが設定されていることを確認します。 「ホーム」ボタン/「URL ランチャーの設定」をクリックします。
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
>プレーヤーの管理 UI ポリシー設定は厳密に適用され、手動で上書きされることはありません。 特定のポリシーに対して手動のプレーヤー設定を許可する場合は、ポリシー設定でポリシーを指定しないでください。
>例えば、再起動スケジュールの手動設定を許可する場合は、ポリシー設定で `rebootSchedule` キーを指定しないでください。ポリシー設定は、プレーヤーが再読み込みされるたびに読み取られます。

| **ポリシー名** | **目的** |
|---|---|
| server | Adobe Experience Manager（AEM）サーバーの URL。 |
| registrationKey | 事前共有キーを使用したデバイスの一括登録に使用されます。 |
| resolution | デバイスの解像度。 |
| rebootSchedule | プレーヤーを再起動するスケジュール。 |
| enableAdminUI | サイト上でデバイスを設定するための Admin UI を有効にします。設定が完了して実稼働になったら、false に設定します。 |
| enableOSD | ユーザーがデバイスのチャネルを切り替えるためのチャネルスイッチャー UI を有効にします。 設定が完了して実稼働になったら、false に設定することを検討します。 |
| enableActivityUI | を有効にすると、ダウンロードや同期など、アクティビティの進行状況を表示できます。 トラブルシューティング用に有効にしておき、設定が完了して実稼働になったら無効にします。 |
| cloudMode | Tizen プレーヤーから Screens as a Cloud Service に接続する場合は、true に設定します。AMS またはオンプレミス AEM に接続する場合は、false に設定します。 |
| cloudToken | Screens as a Cloud Service に登録するための登録トークン。 |


## Samsung Remote Management Service（RMS）への Tizen デバイスの登録 {#enroll-tizen-device-rms}

Tizen デバイスを Samsung Remote Management Service（RMS）に登録し URL ランチャーをリモートで設定するには、次の手順に従います。

>[!NOTE]
>ネットワーク設定とモニターを確認します。

1. **Menu**／**Network**／**Server Network Settings** に移動し、**Enter** キーを押します。

1. サーバーアドレスに移動し、MagicInfo URL access と入力してキーを押します **完了**.

1. 必要に応じて、TLS をセットアップします。ポートに移動し、サーバーのポート番号をクリックして、 **保存**.

1. 「**デバイス**」タブに移動し、設定したデバイスを確認します。デバイスが見つかったら、チェックボックスをクリックし、 **承認**.

   >![画像](/help/user-guide/assets/tizen/rms-3.png)

1. 必要な情報を入力し、デバイスグループをクリックします。 「**OK**」をクリックします。

   >![画像](/help/user-guide/assets/tizen/rms-7.png)

1. デバイスが承認されると、デバイスリストに表示されます。クリック *情報* 次に示すように、デバイスボックスに入力します。

   >![画像](/help/user-guide/assets/tizen/rms-6.png)

1. デバイス情報ダイアログボックスが表示されます。「」をクリックします **デバイス情報** tab キーを押してクリック **編集**.

   >![画像](/help/user-guide/assets/tizen/rms-5.png)

1. デバイスオプションを編集し、 **設定** タブ。 「**URL ランチャー**」セクションに移動し、wgt と `SSSP config file` をホストする URL を入力すると、次の図に示すように `SSSP` アプリケーションをインストールできます。

   ![画像](/help/user-guide/assets/tizen/rms-9.png)

1. 「**保存**」をクリックします。

### Screens リモート制御の使用 {#using-remote-control}

AEM Screens には、リモート制御機能が用意されています。この機能について詳しくは、[Screens リモート制御](implementing-remote-control.md)を参照してください
