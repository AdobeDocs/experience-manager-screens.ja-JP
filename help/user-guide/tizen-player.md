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
ht-degree: 42%

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

ユーザーにわかりやすいデバイス名を Tizen プレーヤーに割り当てて、割り当てられたデバイス名をAdobe Experience Manager（AEM）に送信することができます。 この機能により、Tizen プレーヤーに名前を付けるだけでなく、適切なコンテンツを簡単に割り当てることもできます。

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

1. AEM Screens Player が自動的にインストールされ、Samsung デバイスで起動します。

   >[!NOTE]
   >Tizen デバイスと `http` サーバーが相互に接続できるようになり、サーバーは Tizen プレーヤーに到達できます。


## cookie の SameSite 属性に対応していないユーザーエージェントの適用除外 {#exempting-user-agents}

>[!IMPORTANT]
>**この節の内容は、Adobe Experience Manager（AEM） 6.5.5 からAEM 6.5.7 までのバージョンに適用されます。**
>
>ブラウザーのエンジンの中には、 *`SameSite=None`* AEM 6.5.5 からAEM 6.5.7 までのバージョンで発行されるログイントークンで使用される属性。通常、この問題はブラウザーを入手可能な最新バージョンにアップグレードすることで解決できます。 スマートディスプレイ、セットトップボックス、またはブラウジングエンジンが組み込まれたその他のデバイスでは、アップグレードができない場合があります。

*SameSite=None* を使用する場合に、その属性に対応していないこれらのクライアントを適用対象外にするには、次の手順に従います。

1. Adobe Experience Manager（AEM）Service Pack 6.5.7 にアップグレードします。

1. AEMの再起動後、に移動します。 `/system/console/configMgr` を検索します **Adobe Granite トークン認証ハンドラー**. **SameSite** の値を「**None**」に設定します。

1. 新しいオプションが表示されます *`User agents to be exempted from samesite attribute`*. このオプションに、と互換性のないユーザーエージェントに対応する正規表現を入力します *SameSite=None* 属性。

   >[!NOTE]
   >
   >詳しくは、[SameSite=None: Known Incompatible Clients](https://www.chromium.org/updates/same-site/incompatible-clients)（「SameSite=None」に対応していない既知のクライアント）を参照してください。Tizen プレーヤーの場合は、正規表現を使用します。 `(.*)Tizen(.*)`.

1. AEM 6.5.5 以降のインスタンスに Tizen プレーヤーを登録します。これによりプレーヤーが登録され、コンテンツが正常に表示されます。

## Tizen プレーヤーのリモートプロビジョニング {#remote-provisioning}

Tizen プレーヤーをリモートでプロビジョニングすると、数百台から数千台の Samsung Tizen ディスプレイを、大きな手間をかけずにデプロイできます。 これにより、サーバー URL や一括登録コードなどのパラメーターを各プレーヤーに手動で設定する必要がなくなります。 また、AEM Screensがas a Cloud Serviceされている場合は、クラウドモードとクラウドトークンを設定します。

この機能を使用すると、Tizen プレーヤーをリモートで設定し、必要に応じてそれらの設定を一元的に更新できます。 必要なのは、Tizen アプリケーション `(wgt and xml file)` をホストするための `HTTP` サーバーと、適切なパラメーターを記述した `config.json` を保存するためのテキストエディターだけです。

Tizen デバイスに URL ランチャーアドレスが設定されていることを確認します。 「ホーム」ボタン/「URL ランチャーの設定」をクリックします。
Tizen アプリケーションをホストする `HTTP` サーバー上で、`config.json` ファイルを `wgt` ファイルと同じ場所に置きます。ファイル名は `config.json` にする必要があります。
Tizen プレーヤーがインストールされ、プレーヤーの起動時（および再起動時）に `config.json` ファイル。

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
>例えば、再起動スケジュールの手動設定を許可する場合は、キーを指定しないでください `rebootSchedule` をポリシー設定で使用できます。 ポリシー設定は、プレーヤーが再読み込みされるたびに読み取られます。

| **ポリシー名** | **目的** |
|---|---|
| server | Adobe Experience Manager（AEM）サーバーの URL。 |
| registrationKey | 事前共有キーを使用したデバイスの一括登録に使用されます。 |
| resolution | デバイスの解像度。 |
| rebootSchedule | プレーヤーを再起動するスケジュール。 |
| enableAdminUI | サイト上でデバイスを設定するための Admin UI を有効にします。設定が完了して実稼働になったら、false に設定します。 |
| enableOSD | ユーザーがデバイスのチャネルを切り替えるためのチャネルスイッチャー UI を有効にします。 設定が完了して実稼働になったら、false に設定することを検討します。 |
| enableActivityUI | を有効にすると、ダウンロードや同期など、アクティビティの進行状況を表示できます。 トラブルシューティング用に有効にしておき、設定が完了して実稼働になったら無効にします。 |
| cloudMode | Tizen プレーヤーから Screens as a Cloud Service に接続する場合は、true に設定します。AMS またはオンプレミス AEMに接続する場合は、false に設定します。 |
| cloudToken | Screens as a Cloud Service に登録するための登録トークン。 |


## Samsung Remote Management Service（RMS）への Tizen デバイスの登録 {#enroll-tizen-device-rms}

Tizen デバイスを Samsung Remote Management Service（RMS）に登録し URL ランチャーをリモートで設定するには、次の手順に従います。

>[!NOTE]
>ネットワーク設定とモニターを確認します。

1. **Menu**／**Network**／**Server Network Settings** に移動し、**Enter** キーを押します。

1. サーバーアドレスに移動し、MagicInfo URL access と入力してキーを押します **完了**.

1. 必要に応じて、TLS を設定します。 ポートに移動し、サーバーのポート番号をクリックして、 **保存**.

1. に移動します。 **デバイス** タブをクリックして、設定したデバイスを確認します。 デバイスが見つかったら、チェックボックスをクリックし、 **承認**.

   >![画像](/help/user-guide/assets/tizen/rms-3.png)

1. 必要な情報を入力し、デバイスグループをクリックします。 「**OK**」をクリックします。

   >![画像](/help/user-guide/assets/tizen/rms-7.png)

1. デバイスが承認されると、デバイスリストに表示されます。 クリック *情報* 次に示すように、デバイスボックスに入力します。

   >![画像](/help/user-guide/assets/tizen/rms-6.png)

1. デバイス情報ダイアログボックスが表示されます。「」をクリックします **デバイス情報** tab キーを押してクリック **編集**.

   >![画像](/help/user-guide/assets/tizen/rms-5.png)

1. デバイスオプションを編集し、 **設定** タブ。 に移動します。 **URL ランチャー** セクションに移動し、ウィジェットをホストする URL を入力して、 `SSSP config file` 以下に、 `SSSP` アプリケーション（下図を参照）。

   ![画像](/help/user-guide/assets/tizen/rms-9.png)

1. 「**保存**」をクリックします。

### Screens リモート制御の使用 {#using-remote-control}

AEM Screens には、リモート制御機能が用意されています。この機能について詳しくは、[Screens リモート制御](implementing-remote-control.md)を参照してください
