---
title: Android™ プレーヤーの実装
description: Android™ プレーヤーをクラッシュから回復できるソリューションである Android™ ウォッチドッグの実装について説明します。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens, Android Player
role: Admin
level: Intermediate
exl-id: d1331cb8-8bf6-4742-9525-acf18707b4d8
source-git-commit: 06082edf3dadbaea1cea142ff624e83bc6045dfd
workflow-type: tm+mt
source-wordcount: '1471'
ht-degree: 99%

---

# Android™ プレーヤーの実装 {#implementing-android-player}

この節では、Android™ プレーヤーの設定について説明します。開発およびテストで使用する設定に関して、使用可能および推奨される設定ファイルおよびオプションの情報を提供します。

さらに、プレーヤーをクラッシュから回復させる解決策として、**ウォッチドッグ**&#x200B;があります。アプリケーションは、ウォッチドッグサービスに登録し、アプリケーション自体がアライブであることを知らせるメッセージを定期的に送信する必要があります。ウォッチドッグサービスが所定の時間内にキープアライブメッセージを受信しない場合、サービスはデバイスの再起動を試みます。（十分な権限を持っている場合は）デバイスを再起動してクリーンリカバリを行うか、アプリケーションを再起動します。

## Android™ プレーヤーのインストール {#installing-android-player}

AEM Screens 用の Android™ プレーヤーを実装するには、同プレーヤーをインストールしてください。

[**AEM 6.5 Player のダウンロード**](https://download.macromedia.com/screens/)ページにアクセスします。

### AEM Screens 6.5.5 サービスパック環境の設定 {#fp-environment-setup}

>[!NOTE]
>AEM Screens 6.5.5 サービスパックを使用している場合は、Android™ プレーヤー用の環境を設定します。

AEM オーサーインスタンスおよびパブリッシュインスタンスの **Adobe Experience Manager Web コンソール設定**&#x200B;で、**login-token cookies の SameSite 属性**&#x200B;を **Lax** から **None** に設定します。

次の手順に従います。

1. `http://localhost:4502/system/console/configMgr` を使用して、**Adobe Experience Manager Web コンソールの設定**&#x200B;に移動します。

1. *Adobe Granite トークン認証ハンドラー*&#x200B;を検索します。

1. **login-token cookie の SameSite 属性**&#x200B;を **Lax** から **None** に設定します。
   ![画像](/help/user-guide/assets/granite-updates.png)

1. 「**保存**」をクリックします。


### アドホック方式 {#ad-hoc-method}

アドホック方式を使用すると、最新の Android™ プレーヤー（*.exe*）をインストールできます。[**AEM 6.5 Player のダウンロード**](https://download.macromedia.com/screens/)ページにアクセスします。

アプリケーションをダウンロードしたら、プレーヤー上で以下の手順に従ってアドホックインストールを完了します。

1. 左上隅を長押しして、管理パネルを開きます。
1. 左のアクションメニューから「**設定**」に移動し、接続する AEM インスタンスの場所（アドレス）を入力して、「**保存**」をクリックします。

1. 左側のアクションメニューから「**デバイス**&#x200B;の&#x200B;**登録**」リンクに移動して、デバイス登録プロセスのステータスを確認できます。

>[!NOTE]
>
>「**状態**」が「**登録済み**」の場合は、「**デバイス ID**」フィールドに値が入力されます。
>
>「**状態**」が「**未登録**」の場合は、**トークン**&#x200B;を使用してデバイスを登録できます。

## Android™ ウォッチドッグを実装する {#implementing-android-watchdog}

Android™ のアーキテクチャ上、デバイスをリブートするには、アプリケーションがシステム権限を持っている必要があります。製造元の署名キーを使用して apk に署名します。この署名を行わないと、ウォッチドッグはプレーヤーアプリケーションを再起動できても、デバイスは再起動できません。

### 製造元のキーを使用した Android™ `apks` への署名  {#signage-of-android-apks-using-manufacturer-keys}

*PowerManager* や *HDMIControlServices* など、Android™ の特権付き API にアクセスするには、製造元のキーを使用して Android™ `apk` に署名します。

>[!CAUTION]
>
>前提条件：
>
>次の手順を実行する前に、Android™ SDK をインストールしておく必要があります。

次の手順に従って、製造元のキーを使用して Android™ apk に署名します。

1. Google Play または [AEM Screens Player のダウンロード](https://download.macromedia.com/screens/)ページから apk をダウンロードします。
1. 製造元のプラットフォームキーを入手して、*pk8* ファイルと *pem* ファイルを取得できます。

1. find `~/Library/Android/sdk/build-tools -name "apksigner"` を使用してAndroid™ SDK で `apksigner` ツールを見つける
1. `<pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk`
1. Android™ SDK の zip align ツールへのパスを見つける
1. `<pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk`
1. adb install を使用して、デバイスに ***aemscreensaligned.apk*** をインストールします。

## Android™ ウォッチドッグサービスについて {#android-watchdog-services}

クロスAndroid™ ウォッチドッグサービスは、を使用して Cordova プラグインとして実装されます。 *AlarmManager*.

次の図に、ウォッチドッグサービスの実装を示します。

![chlimage_1-31](assets/chlimage_1-31.png)

**1.初期化** – Cordova プラグインの初期化時、システム権限を持っているかどうか、さらに、リブート権限を持っているかどうかの確認が行われます。これらの 2 つの条件を満たしている場合は、リブートのペンディングインテントが作成され、条件を満たしていない場合は、（Launch Activity に基づいて）アプリケーションを再起動するためのペンディングインテントが作成されます。

**2.キープアライブタイマー** – 15 秒おきにイベントをトリガーするためにキープアライブタイマーが使用されます。このイベントの間に、（アプリケーションをリブートまたは再起動する）既存のペンディングインテントをキャンセルし、次の 60 秒の間に新しいペンディングインテントを登録（基本的にリブートを延期）します。

>[!NOTE]
>
>Android™ では、*AlarmManager* は、アプリケーションがクラッシュして、そのアラーム配信が API 19（Kitkat）から正確に行われなくても実行可能な *pendingIntents* を登録するために使用されます。タイマーの間隔と *AlarmManager* の *pendingIntent* のアラームとの間にいくらかの時間を設けるようにしてください。

**3.アプリケーションのクラッシュ** – クラッシュが発生した場合、AlarmManager に登録されたリブートの pendingIntent はリセットされなくなりました。そのため、アプリケーションのリブートまたは再起動が実行されます（Cordova プラグインの初期化時に使用できる権限によって異なります）。

## Android™ プレーヤーの一括プロビジョニング {#bulk-provision-android-player}

Android™ プレーヤーを一括で展開する場合、管理者 UI で手動で入力せずに、AEM インスタンスを指すようにプレーヤーをプロビジョニングし、他のプロパティを設定する必要があります。

>[!NOTE]
>この機能は Android™ プレーヤー 42.0.372 から利用できます。

次の手順に従って、Android™ プレーヤーで一括プロビジョニングを許可します。

1. `player-config.default.json` という名前で設定 JSON ファイルを作成します。
[JSON ポリシーの例](#example-json)と、様々な[ポリシー属性](#policy-attributes)の使い方を説明した表を参照してください。

1. MDM、ADB、または Android™ Studio のファイルエクスプローラーを使用して、このポリシー JSON ファイルを Android™ デバイスの *sdcard* フォルダーにドロップします。

1. ファイルをデプロイしたら、MDM を使用してプレーヤーアプリケーションをインストールします。

1. プレーヤーアプリケーションが起動すると、この設定ファイルが読み取られ、該当する AEM サーバーを指し、そこで登録および制御されます。

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
| *enableOSD* | ユーザー用のチャネルスイッチャー UI を有効にし、デバイスのチャネルを切り替えます。設定が完了して運用が開始したら、*false* に設定することを検討します。 |
| *enableActivityUI* | ダウンロードや同期などのアクティビティの進行状況を表示する場合に有効にします。トラブルシューティング用に有効にしておき、設定が完了して実稼働になったら無効にします。 |
| *enableNativeVideo* | ビデオ再生でネイティブのハードウェアアクセラレーションを使用する場合に有効にします（Android™ のみ）。 |

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
>すべての Android™ デバイスには、実際の `*sdcard*` が挿入されているかどうかにかかわらず、`*sdcard*` フォルダーがあります。デプロイ時、このファイルは Downloads フォルダーと同じレベルにあります。Samsung Knox などの一部の MDM では、*sdcard* フォルダーの場所を&#x200B;*内部ストレージ*&#x200B;と見なす場合があります。

## エンタープライズモビリティ管理を使用した Android™ プレーヤーの一括プロビジョニング {#bulk-provisioning}

Android™ プレーヤーを一括デプロイする場合、すべてのプレーヤーを手動で AEM に登録するのは非常に手間がかかります。デプロイメントのプロビジョニングと管理をリモートで行うには、[`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、MobileIron、Samsung Knox などの EMM（エンタープライズモビリティ管理）ソリューションを使用します。AEM Screens Android™ プレーヤーでは、業界標準の EMM AppConfig をサポートしているので、リモートプロビジョニングが可能です。

## Android™ プレーヤーの命名 {#name-android}

ユーザーにわかりやすいデバイス名を Android™ プレーヤーに割り当てて、そのデバイス名を AEM（Adobe Experience Manager）に送信することができます。この機能により、Android™ プレーヤーに名前を付けるだけでなく、適切なコンテンツを簡単に割り当てることもできます。

>[!NOTE]
>プレーヤー名は、登録前にのみ選択できます。プレーヤーの登録後は、プレーヤー名を変更できなくなります。

Android™ プレーヤーに名前を設定するには、次の手順に従います。

1. **設定**／**デバイス情報**&#x200B;に移動します。
1. デバイス名を編集および設定して、Android™ プレーヤーに名前を付けます

### エンタープライズモビリティ管理を使用した Android™ プレーヤーの一括プロビジョニングの実装 {#implementation}

Android™ プレーヤーの一括プロビジョニングを可能にするには、次の手順に従います。

1. お使いの Android™ デバイスが Google Play サービスをサポートしていることを確認します。
1. AppConfig をサポートしているお気に入りの EMM ソリューションに、お使いの Android™ プレーヤーデバイスを登録します。
1. EMM コンソールにログインし、Google Play から AEM Screens Player アプリケーションを入手します。
1. 管理された設定または関連オプションをクリックします。
1. これで、設定可能なプレーヤーオプション（サーバーや一括登録コードなど）のリストが表示されます。
1. これらのパラメーターを設定して保存し、ポリシーをデバイスにデプロイします。

   >[!NOTE]
   >デバイスは、設定と共にアプリケーションを受信する必要があります。選択した設定の正しい AEM サーバーを指す必要があります。一括登録コードを設定することを選択し、AEM での設定と同じにしておくと、プレーヤーは自動的に登録できます。デフォルトディスプレイを設定した場合は、一部のデフォルトコンテンツをダウンロードして表示することもできます（このコンテンツは後で都合に合わせて変更できます）。

また、AppConfig のサポートについては、EMM ベンダーに確認してください。[`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、[`Mobile Iron`](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm)、[`SOTI`](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm)、[`BlackBerry&reg; UEM`](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm)、[`IBM&reg; Maas360`](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm)、および [`Samsung Knox`](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) など、最も人気のあるデバイスが、この業界標準をサポートしています。

### Screens リモート制御の使用 {#using-remote-control}

AEM Screens には、リモート制御機能が用意されています。この機能について詳しくは、[Screens リモート制御](implementing-remote-control.md)を参照してください
