---
title: Android&trade；プレーヤーの実装
description: Android&trade；ウォッチドッグ（Android&trade；プレーヤーをクラッシュから回復させるソリューション）の実装について説明します。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: 2b865165793b1c0f90f1351518e41096a57ea2ff
workflow-type: tm+mt
source-wordcount: '1466'
ht-degree: 36%

---

# Android™プレーヤーの実装 {#implementing-android-player}

この節では、Android™プレーヤーの設定について説明します。 使用可能な設定ファイルやオプションと、開発およびテストに使用する設定のレコメンデーションについて説明します。

また、 **ウォッチドッグ** は、プレーヤーをクラッシュから回復させるソリューションです。 アプリケーションは、自身をウォッチドッグサービスに登録し、その後、そのアプリケーションが有効であることを示すメッセージを定期的にサービスに送信する必要があります。 ウォッチドッグサービスが所定の時間内にキープアライブメッセージを受け取らない場合、サービスは（十分な権限を持っている場合は）デバイスを再起動して、クリーンリカバリを試みるか、アプリケーションを再起動します。

## Android™プレーヤーのインストール {#installing-android-player}

AEM Screens用 Android™プレーヤーを実装するには、AEM Screens用 Android™プレーヤーをインストールします。

[**AEM 6.5 Player のダウンロード**](https://download.macromedia.com/screens/)ページにアクセスします。

### AEM Screens 6.5.5 Service Pack の環境の設定 {#fp-environment-setup}

>[!NOTE]
>AEM Screens 6.5.5 Service Pack を使用している場合は、Android™プレーヤー用の環境を設定します。

AEM オーサーインスタンスおよびパブリッシュインスタンスの **Adobe Experience Manager Web コンソール設定**&#x200B;で、**login-token cookies の SameSite 属性**&#x200B;を **Lax** から **None** に設定します。

次の手順に従います。

1. `http://localhost:4502/system/console/configMgr` を使用して、**Adobe Experience Manager Web コンソールの設定**&#x200B;に移動します。

1. *Adobe Granite トークン認証ハンドラー*&#x200B;を検索します。

1. **login-token cookie の SameSite 属性**&#x200B;を **Lax** から **None** に設定します。
   ![画像](/help/user-guide/assets/granite-updates.png)

1. 「**保存**」をクリックします。


### アドホック方式 {#ad-hoc-method}

アドホック方式を使用すると、最新の Android™プレーヤー (*.exe*) をクリックします。 [**AEM 6.5 Player のダウンロード**](https://download.macromedia.com/screens/)ページにアクセスします。

アプリケーションをダウンロードしたら、以下の手順に従ってプレーヤーのアドホックインストールを完了します。

1. 左上隅を長押しして、管理パネルを開きます。
1. 左のアクションメニューから「**設定**」に移動し、接続する AEM インスタンスの場所（アドレス）を入力して、「**保存**」をクリックします。

1. 次に移動： **デバイス** **登録** リンクを使用して、デバイス登録プロセスのステータスを確認できます。

>[!NOTE]
>
>次の場合、 **都道府県** 次に該当 **登録済み**&#x200B;を見ると、 **デバイス ID** フィールドに値が入力されます。
>
>「**状態**」が「**未登録**」の場合は、**トークン**&#x200B;を使用してデバイスを登録できます。

## Android™ウォッチドッグを実装する {#implementing-android-watchdog}

Android™のアーキテクチャにより、デバイスを再起動するには、アプリケーションにシステム権限が必要です。 これをおこなうには、製造元の署名キーを使用して apk に署名します。それ以外の場合は、ウォッチドッグがプレーヤーアプリケーションを再起動し、デバイスを再起動しません。

### Android™のサイネージ `apks` 製造元キーの使用 {#signage-of-android-apks-using-manufacturer-keys}

Android™の特権付き API( 例： *PowerManager* または *HDMIControlServices*, Android™に署名します `apk` 製造元のキーを使用します。

>[!CAUTION]
>
>前提条件：
>
>次の手順を実行する前に、Android™ SDK をインストールしておく必要があります。

次の手順に従って、製造元のキーを使用して Android™ apk に署名します。

1. Google Play または [AEM Screens Player のダウンロード](https://download.macromedia.com/screens/)ページから apk をダウンロードします。
1. 製造元からプラットフォームキーを取得し、 *pk8* および *pem* ファイル

1. 次を見つけます。 `apksigner` ツール (Android™ sdk の「検索」を使用 ) `~/Library/Android/sdk/build-tools -name "apksigner"`
1. `<pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk`
1. Android™ sdk で zip align ツールへのパスを見つけます。
1. `<pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk`
1. adb install を使用して、デバイスに ***aemscreensaligned.apk*** をインストールします。

## Android™ウォッチドッグサービスについて {#android-watchdog-services}

Android ウォッチドッグサービスは、 *AlarmManager*.

次の図に、ウォッチドッグサービスの実装を示します。

![chlimage_1-31](assets/chlimage_1-31.png)

**1.初期化** - Cordova プラグインの初期化時に、システム権限を持っているかどうか、さらに、リブート権限を持っているかどうかの確認がおこなわれます。 これらの 2 つの条件を満たしている場合は、リブートのペンディングインテントが作成され、条件を満たしていない場合は、（Launch Activity に基づいて）アプリケーションを再起動するためのペンディングインテントが作成されます。

**2.キープアライブタイマー**  — キープアライブタイマーは、15 秒ごとにイベントのトリガーを設定するために使用されます。 その場合は、既存の保留中のインテントをキャンセルし（アプリを再起動または再起動する）、その後 60 秒間新しい保留中のインテントを登録します（基本的に再起動の延期）。

>[!NOTE]
>
>Android™では、 *AlarmManager* を使用して *pendingIntents* これは、アプリがクラッシュし、そのアラーム配信が API 19(Kitkat) から正確におこなわれない場合でも実行できます。 タイマーの間隔と *AlarmManager* の *pendingIntent* のアラームとの間にいくらかの時間を設けるようにしてください。

**3.アプリケーションのクラッシュ**  — クラッシュが発生した場合、AlarmManager に登録されている再起動の pendingIntents はリセットされなくなります。 そのため、（Cordova プラグインの初期化時に使用できる権限に応じて）アプリの再起動または再起動が実行されます。

## Android™プレーヤーの一括プロビジョニング {#bulk-provision-android-player}

Android™プレーヤーを一括で展開する場合、管理 UI で手動で入力することなく、AEMインスタンスを指すようにプレーヤーをプロビジョニングし、他のプロパティを設定する必要があります。

>[!NOTE]
>この機能は Android™プレーヤー 42.0.372 から利用できます。

次の手順に従って、Android™プレーヤーで一括プロビジョニングを許可します。

1. `player-config.default.json` という名前で設定 JSON ファイルを作成します。
を参照してください。 [JSON ポリシーの例](#example-json) そして様々な用法を説明する表 [ポリシー属性](#policy-attributes).

1. MDM、ADB、または Android™ Studio のファイルエクスプローラーを使用して、このポリシー JSON ファイルをにドロップします。 *sdcard* Android™デバイス上のフォルダーに保存されます。

1. ファイルをデプロイしたら、MDM を使用してプレーヤーアプリケーションをインストールします。

1. プレーヤーアプリケーションが起動すると、この設定ファイルが読み取られ、登録され、制御された適切なAEMサーバーを指します。

   >[!NOTE]
   >このファイルは *読み取り専用* アプリケーションが初めて起動されたとき。以降の設定には使用できません。 設定ファイルがドロップされる前にプレーヤーが起動した場合は、デバイスでアプリケーションをアンインストールして再インストールします。

### ポリシー属性 {#policy-attributes}

次の表に、参照用のポリシー JSON の例と共にポリシー属性を示します。

| **ポリシー名** | **目的** |
|---|---|
| *server* | Adobe Experience Manager サーバーの URL。 |
| *resolution* | デバイスの解像度。 |
| *rebootSchedule* | 再起動するスケジュールは、すべてのプラットフォームに適用されます。 |
| *enableAdminUI* | サイト上でデバイスを設定するための Admin UI を有効にします。設定が完了して実稼働になったら、*false* に設定します。 |
| *enableOSD* | ユーザー用のチャネルスイッチャー UI を有効にし、デバイスのチャネルを切り替えます。設定が完了して実稼働になったら、*false* に設定することを検討します。 |
| *enableActivityUI* | ダウンロードや同期などのアクティビティの進行状況を表示する場合は、有効にします。 トラブルシューティング用に有効にしておき、設定が完了して実稼働になったら無効にします。 |
| *enableNativeVideo* | ビデオの再生にネイティブのハードウェアアクセラレーションを使用する場合は、有効にします (Android™のみ )。 |

### JSON ポリシーの例 {#example-json}

```java
{
  "server": "https://author-screensdemo.adobecqms.net",
"device": "",
"user": "",
"password": "",
"resolution": "auto",
"rebootSchedule": "at 4:00 am",
"maxNumberOfLogFilesToKeep": 10,
"logLevel": 3,
"enableAdminUI": true,
"enableOSD": true,
"enableActivityUI": false,
"enableNativeVideo": false,
"enableAutoScreenshot": false,
"cloudMode": false,
"cloudUrl": "https://screens.adobeioruntime.net",
"cloudToken": "",
"enableDeveloperMode": true
}
```

>[!NOTE]
>すべての Android™デバイスに `*sdcard*` 実際の `*sdcard*` が挿入されたかどうか。 デプロイ時、このファイルは Downloads フォルダーと同じレベルにあります。Samsung Knox などの一部の MDM では、*sdcard* フォルダーの場所を&#x200B;*内部ストレージ*&#x200B;と呼ぶ場合があります。

## Enterprise Mobility Management を使用した Android™プレーヤーの一括プロビジョニング {#bulk-provisioning}

Android™プレーヤーを一括でデプロイする場合、すべてのプレーヤーをAEMに手動で登録するのは面倒です。 次のような EMM(Enterprise Mobility Management) ソリューションを使用することを強くお勧めします。 [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、MobileIron または Samsung Knox を使用して、デプロイメントをリモートでプロビジョニングおよび管理できます。 AEM Screens Android™ Player は、リモートプロビジョニングを可能にする業界標準の EMM AppConfig をサポートしています。

## Android™プレーヤーの名前 {#name-android}

ユーザーにわかりやすいデバイス名を Android™プレーヤーに割り当てて、割り当てられたデバイス名をAEM(Adobe Experience Manager) に送信できます。 この機能を使用すると、Android™プレーヤーに名前を付けるだけでなく、適切なコンテンツを簡単に割り当てることができます。

>[!NOTE]
>プレーヤー名は、登録にのみ選択できます。プレーヤーの登録後は、プレーヤー名を変更できなくなります。

次の手順に従って、Android™プレーヤーで名前を設定します。

1. に移動します。 **設定** > **デバイスについて**
1. Android™プレーヤーに名前を付けるようにデバイス名を編集および設定します

### エンタープライズモビリティ管理を使用した Android™プレーヤーの一括プロビジョニングの実装 {#implementation}

次の手順に従って、Android™ Player で一括プロビジョニングを許可します。

1. お使いの Android™デバイスがGoogle Playサービスをサポートしていることを確認します。
1. Android™プレーヤーデバイスを、AppConfig をサポートするお気に入りの EMM ソリューションに登録します。
1. EMM コンソールにログインし、Google PlayからAEM Screens Player アプリケーションをプルします。
1. 管理された設定または関連オプションを選択します。
1. これで、設定可能なプレーヤーオプション（サーバーや一括登録コードなど）のリストが表示されます。
1. これらのパラメーターを設定して保存し、ポリシーをデバイスにデプロイします。

   >[!NOTE]
   >デバイスは、アプリケーションと設定を同時に受信し、選択した設定を持つ正しい AEM サーバーを参照します。一括登録コードを設定することを選択し、AEM に設定した値と同じにしておくと、プレーヤーは自動的に登録されるはずです。デフォルトのディスプレイを設定した場合は、一部のデフォルトコンテンツをダウンロードして表示することもできます（デフォルトコンテンツは、都合に応じて後で変更できます）。

また、AppConfig サポートの EMM ベンダーに問い合わせる必要があります。 最も人気のあるものは次のとおりです。 [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [`Mobile Iron`](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [`SOTI`](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [`BlackBerry&reg; UEM`](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [`IBM&reg; Maas360`](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm)、および [`Samsung Knox`](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) 特に、この業界標準を支持する者もいます。

### Screens リモート制御の使用 {#using-remote-control}

AEM Screens には、リモート制御機能が用意されています。この機能について詳しくは、[Screens リモート制御](implementing-remote-control.md)を参照してください
