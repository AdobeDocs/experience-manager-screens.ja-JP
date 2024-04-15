---
title: Android&trade; Player の実装
description: Android&trade; Watchdog の実装について説明します。これは、Android&trade; プレーヤーをクラッシュから回復できるソリューションです。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '1462'
ht-degree: 32%

---

# Android™ プレーヤーの実装 {#implementing-android-player}

ここでは、Android™ プレーヤーの設定について説明します。 使用可能な設定ファイルやオプションと、開発およびテストに使用する設定のレコメンデーションについて説明します。

また、 **番犬** クラッシュからプレーヤーを回復するための解決策です。 アプリケーションは、自身をウォッチドッグサービスに登録し、そのサービスが有効であることを示すメッセージを定期的に送信する必要があります。 ウォッチドッグ サービスが所定の時間内にキープアライブ メッセージを受け取らなかった場合、クリーンな回復（十分な特権を持っている場合）のためにデバイスを再起動するか、またはアプリケーションを再起動しようとします。

## Android™ プレーヤーのインストール {#installing-android-player}

AEM Screens用 Android™ プレーヤーを実装するには、AEM Screens用 Android™ プレーヤーをインストールします。

[**AEM 6.5 Player のダウンロード**](https://download.macromedia.com/screens/)ページにアクセスします。

### AEM Screens 6.5.5 Service Pack の環境の設定 {#fp-environment-setup}

>[!NOTE]
>AEM Screens 6.5.5 Service Pack を使用している場合は、Android™ プレーヤーの環境を設定します。

AEM オーサーインスタンスおよびパブリッシュインスタンスの **Adobe Experience Manager Web コンソール設定**&#x200B;で、**login-token cookies の SameSite 属性**&#x200B;を **Lax** から **None** に設定します。

次の手順に従います。

1. `http://localhost:4502/system/console/configMgr` を使用して、**Adobe Experience Manager Web コンソールの設定**&#x200B;に移動します。

1. *Adobe Granite トークン認証ハンドラー*&#x200B;を検索します。

1. **login-token cookie の SameSite 属性**&#x200B;を **Lax** から **None** に設定します。
   ![画像](/help/user-guide/assets/granite-updates.png)

1. 「**保存**」をクリックします。


### アドホック方式 {#ad-hoc-method}

アドホック方式を使用すると、最新の Android™ プレーヤー（*.exe*）に設定します。 [**AEM 6.5 Player のダウンロード**](https://download.macromedia.com/screens/)ページにアクセスします。

アプリケーションをダウンロードしたら、Player の手順に従ってアドホックインストールを完了します。

1. 左上隅のを長押して、管理パネルを開きます。
1. 左のアクションメニューから「**設定**」に移動し、接続する AEM インスタンスの場所（アドレス）を入力して、「**保存**」をクリックします。

1. に移動します。 **デバイス** **登録** 左側のアクションメニューからのリンクを使用して、デバイス登録プロセスのステータスを確認できます。

>[!NOTE]
>
>次の場合 **都道府県** 等しい **登録済み**&#x200B;を参照してください。次のことがわかります **デバイス ID** フィールドに値が入力されます。
>
>「**状態**」が「**未登録**」の場合は、**トークン**&#x200B;を使用してデバイスを登録できます。

## Android™ ウォッチドッグの実装 {#implementing-android-watchdog}

Android™ のアーキテクチャ上、デバイスを再起動するには、アプリケーションにシステム権限が必要です。 これを行うには、製造元の署名キーを使用して apk に署名します。署名しない場合、ウォッチドッグはプレーヤーアプリケーションを再起動し、デバイスは再起動しません。

### Android™ のサイネージ `apks` 製造元キーの使用 {#signage-of-android-apks-using-manufacturer-keys}

次のような Android の一部の特権 API™ アクセスするには： *PowerManager* または *HDMIControlServices* Android™ に署名します `apk` 製造元のキーを使用します。

>[!CAUTION]
>
>前提条件：
>
>次の手順を実行する前に、Android™ SDK をインストールしておく必要があります。

製造元のキーを使用して Android™ apk に署名するには、次の手順に従います。

1. Google Play または [AEM Screens Player のダウンロード](https://download.macromedia.com/screens/)ページから apk をダウンロードします。
1. 製造元からプラットフォームキーを入手して、 *pk8* および *pem* ファイル

1. を見つけます。 `apksigner` 検索を使用した Android™ sdk のツール `~/Library/Android/sdk/build-tools -name "apksigner"`
1. `<pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk`
1. Android™ sdk で zip align ツールへのパスを検索します
1. `<pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk`
1. adb install を使用して、デバイスに ***aemscreensaligned.apk*** をインストールします。

## Android™ ウォッチドッグサービスについて {#android-watchdog-services}

クロス Android ウォッチドッグサービスは、を使用して Cordova プラグインとして実装されます。 *AlarmManager*.

次の図に、ウォッチドッグサービスの実装を示します。

![chlimage_1-31](assets/chlimage_1-31.png)

**1.初期化** - Cordova プラグインの初期化時、システム権限を持っているかどうか、さらに、リブート権限を持っているかどうかの確認が行われます。 これらの 2 つの条件を満たしている場合は、リブートのペンディングインテントが作成され、条件を満たしていない場合は、（Launch Activity に基づいて）アプリケーションを再起動するためのペンディングインテントが作成されます。

**2.キープアライブ タイマー** - キープアライブ タイマーは、15 秒ごとにイベントをトリガーするために使用されます。 その場合は、既存の保留中のインテントをキャンセル（アプリを再起動または再起動するため）し、同じ 60 秒後に新しい保留中のインテントを登録します（基本的に再起動を延期します）。

>[!NOTE]
>
>Android™ では、 *AlarmManager* を使用して、 *pendingIntents* これは、アプリがクラッシュして、そのアラーム配信が API 19 （Kitkat）から正確に行われなくても実行できます。 タイマーの間隔と *AlarmManager* の *pendingIntent* のアラームとの間にいくらかの時間を設けるようにしてください。

**3.アプリケーションのクラッシュ** - クラッシュが発生した場合、AlarmManager に登録された再起動の pendingIntent はリセットされなくなりました。 そのため、アプリケーションの再起動または再起動が実行されます（Cordova プラグインの初期化時に使用できる権限によって異なります）。

## Android™ プレーヤーの一括プロビジョニング {#bulk-provision-android-player}

Android™ プレーヤーを一括でロールアウトする場合は、AEM インスタンスを指すようにプレーヤーをプロビジョニングし、管理 UI でそれらを手動で入力せずに他のプロパティを設定する必要があります。

>[!NOTE]
>この機能は、Android™ プレーヤー 42.0.372 から使用できます。

Android™ プレーヤーで一括プロビジョニングを許可するには、次の手順に従います。

1. `player-config.default.json` という名前で設定 JSON ファイルを作成します。
を表示 [JSON ポリシーの例](#example-json) および各種のの使用方法を説明した表 [ポリシー属性](#policy-attributes).

1. MDM、ADB、Android™ Studio のファイルエクスプローラーを使用して、このポリシーの JSON ファイルをにドロップします *sdcard* android™ デバイスのフォルダー。

1. ファイルがデプロイされたら、MDM を使用してプレーヤーアプリケーションをインストールします。

1. Player アプリケーションが起動すると、この設定ファイルが読み取られ、該当するAEM サーバーを指します。このサーバーに登録され、制御されます。

   >[!NOTE]
   >このファイルは *読み取り専用* アプリケーションの初回起動時。以降の設定には使用できません。 設定ファイルがドロップされる前にプレーヤーが起動された場合は、デバイスにアプリケーションをアンインストールして再インストールするだけです。

### ポリシー属性 {#policy-attributes}

次の表に、参照用のポリシー JSON の例と共にポリシー属性を示します。

| **ポリシー名** | **目的** |
|---|---|
| *server* | Adobe Experience Manager サーバーの URL。 |
| *resolution* | デバイスの解像度。 |
| *rebootSchedule* | 再起動するスケジュールは、すべてのプラットフォームに適用されます。 |
| *enableAdminUI* | サイト上でデバイスを設定するための Admin UI を有効にします。設定が完了して実稼働になったら、*false* に設定します。 |
| *enableOSD* | ユーザー用のチャネルスイッチャー UI を有効にし、デバイスのチャネルを切り替えます。設定が完了して実稼働になったら、*false* に設定することを検討します。 |
| *enableActivityUI* | ダウンロードや同期など、アクティビティの進行状況を表示する場合に有効にします。 トラブルシューティング用に有効にしておき、設定が完了して実稼働になったら無効にします。 |
| *enableNativeVideo* | ビデオ再生にネイティブのハードウェアアクセラレーションを使用する場合は、を有効にします（Android™ のみ）。 |

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
>すべての Android™ デバイスには以下が含まれています `*sdcard*` フォルダーが実際であるかどうか `*sdcard*` が挿入されているかどうか。 デプロイ時、このファイルは Downloads フォルダーと同じレベルにあります。Samsung Knox などの一部の MDM には、このメッセージが表示される場合があります *sdcard* フォルダーの場所 *内部ストレージ*.

## エンタープライズモビリティ管理を使用した Android™ プレーヤーの一括プロビジョニング {#bulk-provisioning}

Android™ プレーヤーを一括でデプロイする場合は、すべてのプレーヤーをAEMに手動で登録するのが面倒になります。 次のような EMM （エンタープライズモビリティ管理）ソリューションを使用することを強くお勧めします [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、MobileIron または Samsung Knox を使用して、デプロイメントをリモートでプロビジョニングおよび管理します。 AEM Screens Android™ プレーヤーは、業界標準の EMM AppConfig をサポートしており、リモートプロビジョニングが可能です。

## Android™ プレーヤーの命名 {#name-android}

ユーザーにわかりやすいデバイス名を Android™ プレーヤーに割り当てて、割り当てられたデバイス名をAEM（Adobe Experience Manager）に送信することができます。 この機能により、Android™ プレーヤーに名前を付けるだけでなく、適切なコンテンツを簡単に割り当てることもできます。

>[!NOTE]
>プレーヤー名は、登録にのみ選択できます。プレーヤーの登録後は、プレーヤー名を変更できなくなります。

Android™ プレーヤーに名前を設定するには、次の手順に従います。

1. に移動します。 **設定** > **デバイスについて**
1. デバイス名を編集および設定して、Android™ プレーヤーに名前を付けます

### エンタープライズモビリティ管理を使用した Android™ プレーヤーの一括プロビジョニングの実装 {#implementation}

Android™ プレーヤーで一括プロビジョニングを許可するには、次の手順に従います。

1. Android™ デバイスがGoogle Play サービスをサポートしていることを確認します。
1. Android™ プレーヤーデバイスを、AppConfig をサポートするお気に入りの EMM ソリューションに登録します。
1. EMM コンソールにログインし、Google PlayからAEM Screens Player アプリケーションを取り込みます。
1. 管理された設定または関連オプションを選択します。
1. これで、設定可能なプレーヤーオプション（サーバーや一括登録コードなど）のリストが表示されます。
1. これらのパラメーターを設定して保存し、ポリシーをデバイスにデプロイします。

   >[!NOTE]
   >デバイスは、アプリケーションと設定を同時に受信し、選択した設定を持つ正しい AEM サーバーを参照します。一括登録コードを設定することを選択し、AEM に設定した値と同じにしておくと、プレーヤーは自動的に登録されるはずです。デフォルトのディスプレイを設定した場合は、一部のデフォルトコンテンツ（後で都合に応じて変更できます）をダウンロードして表示することもできます。

また、AppConfig サポートの EMM ベンダーにも確認してください。 最も人気のあるもの（例：） [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [`Mobile Iron`](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [`SOTI`](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [`BlackBerry&reg; UEM`](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [`IBM&reg; Maas360`](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm)、および [`Samsung Knox`](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) その中には、この業界標準をサポートするものもあります。

### Screens リモート制御の使用 {#using-remote-control}

AEM Screens には、リモート制御機能が用意されています。この機能について詳しくは、[Screens リモート制御](implementing-remote-control.md)を参照してください
