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
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '1471'
ht-degree: 71%

---

# Android™ プレーヤーの実装 {#implementing-android-player}

ここでは、Android™ プレーヤーの設定について説明します。 開発およびテストで使用する設定に関して、使用可能および推奨される設定ファイルおよびオプションの情報を提供します。

さらに、プレーヤーをクラッシュから回復させる解決策として、**ウォッチドッグ**&#x200B;があります。アプリケーションは、ウォッチドッグサービスに登録し、アプリケーション自体がアライブであることを知らせるメッセージを定期的に送信する必要があります。ウォッチドッグ サービスは、指定された時間内にキープアライブ メッセージを受信しない場合、デバイスの再起動を試みます。 （十分な権限を持っている場合は）クリーンな回復のために、またはアプリケーションを再起動するために行われます。

## Android™ プレーヤーのインストール {#installing-android-player}

AEM Screens 用の Android™ プレーヤーを実装するには、同プレーヤーをインストールしてください。

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

アドホック方式を使用すると、最新の Android™ プレーヤー（*.exe*）をインストールできます。[**AEM 6.5 Player のダウンロード**](https://download.macromedia.com/screens/)ページにアクセスします。

アプリケーションをダウンロードしたら、Player の手順に従ってアドホックインストールを完了します。

1. 左上隅を長押しして、管理パネルを開きます。
1. に移動します。 **設定** 左側のアクションメニューから接続先のAEM インスタンスの場所（アドレス）を入力し、をクリックします **保存**.

1. 左側のアクションメニューから「**デバイス**&#x200B;の&#x200B;**登録**」リンクに移動して、デバイス登録プロセスのステータスを確認できます。

>[!NOTE]
>
>「**状態**」が「**登録済み**」の場合は、「**デバイス ID**」フィールドに値が入力されます。
>
>「**状態**」が「**未登録**」の場合は、**トークン**&#x200B;を使用してデバイスを登録できます。

## Android™ ウォッチドッグを実装する {#implementing-android-watchdog}

Android™ のアーキテクチャ上、デバイスをリブートするには、アプリケーションがシステム権限を持っている必要があります。製造元の署名キーを使用して apk に署名します。署名しない場合、ウォッチドッグはデバイスを再起動するのではなく、プレーヤーアプリケーションを再起動できます。

### 製造元のキーを使用した Android™ `apks` への署名  {#signage-of-android-apks-using-manufacturer-keys}

*PowerManager* や *HDMIControlServices* など、Android™ の特権付き API にアクセスするには、製造元のキーを使用して Android™ `apk` に署名します。

>[!CAUTION]
>
>前提条件：
>
>次の手順を実行する前に、Android™ SDK をインストールしておく必要があります。

次の手順に従って、製造元のキーを使用して Android™ apk に署名します。

1. Google Playまたは [AEM Screens Player のダウンロード](https://download.macromedia.com/screens/) ページ
1. 製造元のプラットフォームキーを入手して、*pk8* ファイルと *pem* ファイルを取得できます。

1. を見つけます。 `apksigner` 検索を使用した Android™ SDK のツール `~/Library/Android/sdk/build-tools -name "apksigner"`
1. `<pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk`
1. Android™ SDK で zip align ツールへのパスを見つけます
1. `<pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk`
1. adb install を使用して、デバイスに ***aemscreensaligned.apk*** をインストールします。

## Android™ ウォッチドッグサービスについて {#android-watchdog-services}

Android ウォッチドッグサービスは、*AlarmManager* を使用した Cordova プラグインとして実装されます。

次の図は、ウォッチドッグサービスの実装を示しています。

![chlimage_1-31](assets/chlimage_1-31.png)

**1.初期化** – Cordova プラグインの初期化時、システム権限を持っているかどうか、さらに、リブート権限を持っているかどうかの確認が行われます。これらの 2 つの条件を満たしている場合は、リブートのペンディングインテントが作成され、条件を満たしていない場合は、（Launch Activity に基づいて）アプリケーションを再起動するためのペンディングインテントが作成されます。

**2.キープアライブタイマー** – 15 秒おきにイベントをトリガーするためにキープアライブタイマーが使用されます。その場合は、既存の保留中のインテントをキャンセル（アプリの再起動または再起動を目的）し、同じ 60 秒後に新しい保留中のインテントを登録します（基本的に再起動を延期します）。

>[!NOTE]
>
>Android™ では、*AlarmManager* は、アプリケーションがクラッシュして、そのアラーム配信が API 19（Kitkat）から正確に行われなくても実行可能な *pendingIntents* を登録するために使用されます。タイマーの間隔と *AlarmManager* の *pendingIntent* のアラームとの間にいくらかの時間を設けるようにしてください。

**3.アプリケーションのクラッシュ** – クラッシュが発生した場合、AlarmManager に登録されたリブートの pendingIntent はリセットされなくなりました。そのため、アプリケーションのリブートまたは再起動が実行されます（Cordova プラグインの初期化時に使用できる権限によって異なります）。

## Android™ プレーヤーの一括プロビジョニング {#bulk-provision-android-player}

Android™ プレーヤーを一括でロールアウトする場合は、AEM インスタンスを指すようにプレーヤーをプロビジョニングし、管理 UI で手動で入力せずにその他のプロパティを設定する必要があります。

>[!NOTE]
>この機能は Android™ プレーヤー 42.0.372 から利用できます。

次の手順に従って、Android™ プレーヤーで一括プロビジョニングを許可します。

1. `player-config.default.json` という名前で設定 JSON ファイルを作成します。
[JSON ポリシーの例](#example-json)と、様々な[ポリシー属性](#policy-attributes)の使い方を説明した表を参照してください。

1. MDM、ADB、または Android™ Studio のファイルエクスプローラーを使用して、このポリシー JSON ファイルを Android™ デバイスの *sdcard* フォルダーにドロップします。

1. ファイルがデプロイされたら、MDM を使用してプレーヤーアプリケーションをインストールします。

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
| *enableOSD* | ユーザーがデバイスのチャネルを切り替えるためのチャネルスイッチャー UI を有効にします。 をに設定することを検討してください *偽* 設定が完了して実稼働になったら、 |
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

Android™ プレーヤーを一括でデプロイする場合、すべてのプレーヤーをAEMに手動で登録するのは面倒になります。 次のような EMM （エンタープライズ・モビリティ管理）ソリューションを使用します [`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、MobileIron または Samsung Knox を使用すると、デプロイメントをリモートでプロビジョニングおよび管理できます。 AEM Screens Android™ プレーヤーでは、業界標準の EMM AppConfig をサポートしているので、リモートプロビジョニングが可能です。

## Android™ プレーヤーの命名 {#name-android}

ユーザーにわかりやすいデバイス名を Android™ プレーヤーに割り当てて、そのデバイス名を AEM（Adobe Experience Manager）に送信することができます。この機能により、Android™ プレーヤーに名前を付けるだけでなく、適切なコンテンツを簡単に割り当てることもできます。

>[!NOTE]
>プレーヤー名は、登録にのみ選択できます。プレーヤーの登録後は、プレーヤー名を変更できなくなります。

Android™ プレーヤーに名前を設定するには、次の手順に従います。

1. **設定**／**デバイス情報**&#x200B;に移動します。
1. デバイス名を編集および設定して、Android™ プレーヤーに名前を付けます

### エンタープライズモビリティ管理を使用した Android™ プレーヤーの一括プロビジョニングの実装 {#implementation}

Android™ プレーヤーの一括プロビジョニングを可能にするには、次の手順に従います。

1. お使いの Android™ デバイスが Google Play サービスをサポートしていることを確認します。
1. AppConfig をサポートしているお気に入りの EMM ソリューションに、お使いの Android™ プレーヤーデバイスを登録します。
1. EMM コンソールにログインし、Google Play から AEM Screens Player アプリケーションを入手します。
1. 「管理設定」または関連オプションをクリックします。
1. これで、設定可能なプレーヤーオプション（サーバーや一括登録コードなど）のリストが表示されます。
1. これらのパラメーターを設定して保存し、ポリシーをデバイスにデプロイします。

   >[!NOTE]
   >デバイスは、設定と共にアプリケーションを受け取る必要があります。 選択した設定を持つ正しいAEM サーバーを指している必要があります。 一括登録コードを設定し、AEMで設定したのと同じ設定にした場合は、Player は自動的に登録されます。 デフォルトディスプレイを設定した場合は、一部のデフォルトコンテンツをダウンロードして表示することもできます（このコンテンツは後で都合に合わせて変更できます）。

また、AppConfig のサポートについては、EMM ベンダーに確認してください。[`VMWare Airwatch`](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、[`Mobile Iron`](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm)、[`SOTI`](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm)、[`BlackBerry&reg; UEM`](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm)、[`IBM&reg; Maas360`](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm)、および [`Samsung Knox`](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) など、最も人気のあるデバイスが、この業界標準をサポートしています。

### Screens リモート制御の使用 {#using-remote-control}

AEM Screens には、リモート制御機能が用意されています。この機能について詳しくは、[Screens リモート制御](implementing-remote-control.md)を参照してください
