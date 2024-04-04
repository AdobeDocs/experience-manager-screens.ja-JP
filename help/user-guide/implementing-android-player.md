---
title: Android プレーヤーの実装
seo-title: Implementation of Android Player
description: このページでは、Android ウォッチドック（Android プレーヤーをクラッシュから回復させるソリューション）の実装について説明します。
seo-description: Follow this page to learn implementation of Android Watchdog, a solution to recover the player from crashes.
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '1510'
ht-degree: 91%

---

# Android プレーヤーの実装 {#implementing-android-player}

ここでは、Android プレーヤーの設定について説明します。使用可能な設定ファイルやオプションと、開発およびテストに使用する設定のレコメンデーションについて説明します。

さらに、プレーヤーをクラッシュから回復させるソリューションとして、**ウォッチドッグ**&#x200B;があります。アプリケーションは、自身をウォッチドッグサービスに登録し、その後、そのアプリケーションが有効であることを示すメッセージを定期的にサービスに送信する必要があります。 ウォッチドッグサービスが所定の時間内にキープアライブメッセージを受け取らない場合、サービスは（十分な権限を持っている場合は）デバイスを再起動して、クリーンリカバリを試みるか、アプリケーションを再起動します。

## Android プレーヤーのインストール {#installing-android-player}

AEM Screens 用の Android プレーヤーを実装するには、同プレーヤーをインストールしてください。

[**AEM 6.5 Player のダウンロード**](https://download.macromedia.com/screens/)ページにアクセスします。

### AEM Screens 6.5.5 Service Pack の環境の設定 {#fp-environment-setup}

>[!NOTE]
>AEM Screens 6.5.5 Service Pack を使用している場合は、Android プレーヤー用の環境を設定する必要があります。

AEM オーサーインスタンスおよびパブリッシュインスタンスの **Adobe Experience Manager Web コンソール設定**&#x200B;で、**login-token cookies の SameSite 属性**&#x200B;を **Lax** から **None** に設定します。

次の手順に従います。

1. `http://localhost:4502/system/console/configMgr` を使用して、**Adobe Experience Manager Web コンソールの設定**&#x200B;に移動します。

1. *Adobe Granite トークン認証ハンドラー*&#x200B;を検索します。

1. **login-token cookie の SameSite 属性**&#x200B;を **Lax** から **None** に設定します。
   ![画像](/help/user-guide/assets/granite-updates.png)

1. 「**保存**」をクリックします。


### アドホック方式 {#ad-hoc-method}

アドホック方式を使用すると、最新の Android プレーヤー（*.exe*）をインストールできます。[**AEM 6.5 Player のダウンロード**](https://download.macromedia.com/screens/)ページにアクセスします。

アプリケーションをダウンロードしたら、以下の手順に従ってプレーヤーのアドホックインストールを完了します。

1. 左上隅を長押しして、管理パネルを開きます。
1. 左のアクションメニューから「**設定**」に移動し、接続する AEM インスタンスの場所（アドレス）を入力して、「**保存**」をクリックします。

1. 左側のアクションメニューから「**デバイス**&#x200B;の&#x200B;**登録**」リンクに移動して、デバイス登録プロセスのステータスを確認します。

>[!NOTE]
>
>「**状態**」が「**登録済み**」の場合は、「**デバイス ID**」フィールドに値が入力されます。
>
>「**状態**」が「**未登録**」の場合は、**トークン**&#x200B;を使用してデバイスを登録できます。

## Android ウォッチドッグを実装する {#implementing-android-watchdog}

Android のアーキテクチャにより、デバイスを再起動するには、アプリケーションにシステム権限が必要です。 そのためには、製造元の署名キーを使用して apk に署名する必要があります。この署名を行わないと、ウォッチドッグはデバイスをリブートするのではなく、プレーヤーアプリケーションを再起動します。

### 製造元のキーを使用した Android apk への署名 {#signage-of-android-apks-using-manufacturer-keys}

*PowerManager* や *HDMIControlServices* など、Android の特権付き API にアクセスするには、製造元のキーを使用して Android apk に署名する必要があります。

>[!CAUTION]
>
>前提条件：
>
>次の手順を実行する前に、Android SDK をインストールしておく必要があります。

次の手順に従って、製造元のキーを使用して Android apk に署名します。

1. Google Play または [AEM Screens Player のダウンロード](https://download.macromedia.com/screens/)ページから apk をダウンロードします。
1. 製造元のプラットフォームキーを入手して、*pk8* ファイルと *pem* ファイルを取得します。

1. find ～/Library/Android/sdk/build-tools -name &quot;apksigner&quot;を使用して、android sdk で apksigner ツールを探します。
1. &lt;pathto> /apksigner sign —key platform.pk8 —cert platform.x509.pem aemscreensplayer.apk
1. Android SDK の zip align ツールへのパスを見つけます。
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk
1. adb install を使用して、デバイスに ***aemscreensaligned.apk*** をインストールします。

## Android ウォッチドッグサービスについて {#android-watchdog-services}

Android ウォッチドッグサービスは、*AlarmManager* を使用した cordova プラグインとして実装されます。

次の図に、ウォッチドッグサービスの実装を示します。

![chlimage_1-31](assets/chlimage_1-31.png)

**1.初期化**：cordova プラグインの初期化時、システム権限を持っているかどうか、さらに、リブート権限を持っているかどうかの確認が行われます。これらの 2 つの条件を満たしている場合は、リブートのペンディングインテントが作成され、条件を満たしていない場合は、（Launch Activity に基づいて）アプリケーションを再起動するためのペンディングインテントが作成されます。

**2.キープアライブタイマー**：15 秒おきにイベントをトリガーするためにキープアライブタイマーが使用されます。このイベントの間に、（アプリケーションをリブートまたは再起動する）既存のペンディングインテントをキャンセルし、次の 60 秒の間に新しいペンディングインテントを登録する（最終的にリブートを延期する）必要があります。

>[!NOTE]
>
>Android では、*AlarmManager* は、アプリケーションがクラッシュして、そのアラーム配信が API 19（Kitkat）から正確に行われなくても実行可能な *pendingIntents* を登録するために使用されます。タイマーの間隔と *AlarmManager* の *pendingIntent* のアラームとの間にいくらかの時間を設けるようにしてください。

**3.アプリケーションのクラッシュ**：クラッシュした場合、AlarmManager に登録されているリブートのペンディングインテントはリセットされず、（cordova プラグインの初期化時に使用可能な権限に応じて）アプリケーションのリブートまたは再起動を実行します。

## Android プレーヤーの一括プロビジョニング {#bulk-provision-android-player}

Android プレーヤーを一括で展開する場合、管理者 UI で手動で入力しなくても、AEM インスタンスを指すようにプレーヤーをプロビジョニングし、他のプロパティを設定する必要があります。

>[!NOTE]
>この機能は Android プレーヤー 42.0.372 から利用できます。

次の手順に従って、Android プレーヤーで一括プロビジョニングを許可します。

1. `player-config.default.json` という名前で設定 JSON ファイルを作成します。
[JSON ポリシーの例](#example-json)と、様々な[ポリシー属性](#policy-attributes)の使い方を説明した表を参照してください。

1. MDM、ADB、または Android Studio のファイルエクスプローラーを使用して、このポリシー JSON ファイルを Android デバイスの *sdcard* フォルダーにドロップします。

1. ファイルをデプロイしたら、MDM を使用してプレーヤーアプリケーションをインストールします。

1. プレーヤーアプリケーションが起動すると、この設定ファイルが読み取られ、そのファイルを登録し、その後制御できる適切な AEM サーバーが参照されます。

   >[!NOTE]
   >このファイルは、アプリケーションが初めて起動されたときは&#x200B;*読み取り専用*&#x200B;で、以降の設定には使用できません。設定ファイルがドロップされる前にプレーヤーが起動した場合は、デバイスでアプリケーションをアンインストールして、再インストールします。

### ポリシー属性 {#policy-attributes}

次の表に、参照用のポリシー JSON の例と共にポリシー属性を示します。

| **ポリシー名** | **目的** |
|---|---|
| *server* | Adobe Experience Manager サーバーの URL。 |
| *resolution* | デバイスの解像度。 |
| *rebootSchedule* | 再起動するスケジュールは、すべてのプラットフォームに適用されます。 |
| *enableAdminUI* | サイト上でデバイスを設定するための Admin UI を有効にします。設定が完了して実稼働になったら、*false* に設定します。 |
| *enableOSD* | ユーザー用のチャネルスイッチャー UI を有効にし、デバイスのチャネルを切り替えます。設定が完了して実稼働になったら、*false* に設定することを検討します。 |
| *enableActivityUI* | 有効にすると、ダウンロードや同期などのアクティビティの進行状況を表示します。トラブルシューティング用に有効にしておき、設定が完了して実稼働になったら無効にします。 |
| *enableNativeVideo* | ビデオ再生でネイティブのハードウェアアクセラレーションを使用できるようにします（Android のみ）。 |

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
>すべての Android デバイスには、実際の *SD カード*&#x200B;が挿入されているかどうかにかかわらず、*sdcard* フォルダーがあります。デプロイ時、このファイルは Downloads フォルダーと同じレベルにあります。Samsung Knox などの一部の MDM では、*sdcard* フォルダーの場所を&#x200B;*内部ストレージ*&#x200B;と呼ぶ場合があります。

## エンタープライズモビリティ管理を使用した Android プレーヤーの一括プロビジョニング {#bulk-provisioning}

Android プレーヤーを一括デプロイする場合、プレーヤーを 1 つずつ手動で AEM に登録するのは非常に面倒です。VMWare Airwatch、MobileIron、Samsung Knox などの EMM（エンタープライズモビリティ管理）ソリューションを使用して、デプロイメントのプロビジョニングと管理をリモートで行うことを強くお勧めします。AEM Screens Android プレーヤーでは、業界標準の EMM AppConfig をサポートしているので、リモートプロビジョニングが可能です。

## Android プレーヤーの命名 {#name-android}

ユーザーにわかりやすいデバイス名を Android プレーヤーに割り当てて、そのデバイス名を Adobe Experience Manager（AEM）に送信することができます。この機能により、Android プレーヤーに名前を付けるだけでなく、適切なコンテンツを簡単に割り当てることもできます。

>[!NOTE]
>プレーヤー名は、登録にのみ選択できます。プレーヤーの登録後は、プレーヤー名を変更できなくなります。

Android プレーヤーに名前を設定するには、次の手順に従います。

1. に移動します。 **設定** > **デバイスについて**
1. デバイス名を編集および設定して、Android プレーヤーに名前を付けます

### エンタープライズモビリティ管理を使用した Android プレーヤーの一括プロビジョニングの実装 {#implementation}

Android プレーヤーの一括プロビジョニングを可能にするには、次の手順に従います。

1. お使いの Android デバイスが Google Play サービスをサポートしていることを確認します。
1. AppConfig をサポートしているお気に入りの EMM ソリューションに、お使いの Android プレーヤーデバイスを登録します。
1. EMM コンソールにログインし、Google Play から AEM Screens Player アプリケーションを入手します。
1. 管理された設定または関連オプションを選択します。
1. これで、設定可能なプレーヤーオプション（サーバーや一括登録コードなど）のリストが表示されます。
1. これらのパラメーターを設定して保存し、ポリシーをデバイスにデプロイします。

   >[!NOTE]
   >デバイスは、アプリケーションと設定を同時に受信し、選択した設定を持つ正しい AEM サーバーを参照します。一括登録コードを設定することを選択し、AEM に設定した値と同じにしておくと、プレーヤーは自動的に登録されるはずです。デフォルトディスプレイを設定した場合は、一部のデフォルトコンテンツをダウンロードして表示することもできます（このコンテンツは後で都合に合わせて変更できます）。

また、AppConfig のサポートについては、EMM ベンダーに確認してください。中でも、[VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、[Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm)、[SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm)、[Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm)、[IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm)、[Samsung Knox](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) などの最も一般的なものは、この業界標準をサポートしています。

### Screens リモート制御の使用 {#using-remote-control}

AEM Screens には、リモート制御機能が用意されています。この機能について詳しくは、[Screens リモート制御](implementing-remote-control.md)を参照してください
