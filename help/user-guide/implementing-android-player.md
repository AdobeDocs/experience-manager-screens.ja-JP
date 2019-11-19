---
title: Android playerの実装
seo-title: Android プレーヤーの実装
description: このページでは、Android ウォッチドック（Android プレーヤーをクラッシュから回復させるソリューション）を実装する方法について見ていきます。
seo-description: このページでは、Android ウォッチドック（Android プレーヤーをクラッシュから回復させるソリューション）を実装する方法について見ていきます。
uuid: 17edd093-f1b1-479e-9f25-28c64f1a7223
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 77fe9d4e-e1bb-42f7-b563-dc03e3af8a60
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Android playerの実装 {#implementing-android-player}

ここでは、Androidプレーヤーの設定について説明します。 開発およびテストで使用する設定に関して、使用可能および推奨される設定ファイルおよびオプションの情報を提供します。

Additionally,**Watchdog** is a solution to recover the player from crashes. アプリケーションは、ウォッチドッグサービスに登録し、アプリケーション自体がアライブであることを知らせるメッセージを定期的に送信する必要があります。ウォッチドッグサービスに、所定の時間内にキープアライブメッセージが届かないと、ウォッチドッグサービスは、デバイスをリブートしてクリーンリカバリを試みるか（ウォッチドッグサービスが十分な権限が持つ場合）、アプリケーションの再起動を試みます。

## Android Playerのインストール {#installing-android-player}

AEM Screens用のAndroid playerを実装するには、AEM Screens用のAndroid Playerをインストールしてください。

「 [**AEM 6.4 Player Downloads**](https://download.macromedia.com/screens/) 」ページにアクセスします。

### アドホックメソッド {#ad-hoc-method}

アドホック方式を使用すると、最新のAndroid Player(*.exe*)をインストールできます。 AEM 6.4 [**プレイヤーのダウンロードページにアクセス**](https://download.macromedia.com/screens/) 。

アプリケーションをダウンロードしたら、プレーヤーの次の手順に従ってアドホックインストールを完了します。

1. 左上隅を長押しして、管理パネルを開きます。
1. 左側のアク **ション** メニューから「Configuration」に移動し、接続するAEMインスタンスの場所（アドレス）を入力し、「 **Save」をクリックします**。

1. 左側のアクションメニ **ューから** 「Device **** Registration」リンクに移動して、デバイス登録プロセスのステータスを確認します。

>[!NOTE]
>
>「 **State** 」が「 **REGISTERED**」の場合は **、「** Device id」フィールドに値が入力されます。
>
>状態が **UNREGISTEREDの場合** 、ト **ークンを**&#x200B;使用して **** デバイスを登録できます。

## Android ウォッチドッグを実装する {#implementing-android-watchdog}

Android のアーキテクチャ上、デバイスをリブートするには、アプリケーションがシステム権限を持っている必要があります。そのためには、製造元の署名キーを使用して apk に署名する必要があります。この署名をおこなわないと、ウォッチドッグはデバイスをリブートするのではなく、プレーヤーアプリケーションを再起動します。

### 製造元のキーを使用した Android apk への署名 {#signage-of-android-apks-using-manufacturer-keys}

To access some of the privileged APIs of Android such as *PowerManager* or *HDMIControlServices*, you need to signtheandroid apk using the manufacturer's keys.

>[!CAUTION]
>
>前提条件:
>
>以下の手順を実行する前に、Android SDK をインストールしてください。

次の手順に従って、製造元のキーを使用して Android apk に署名します。

1. Download the apk from Google Play or from [AEM Screens Player Downloads](https://download.macromedia.com/screens/) page
1. Obtain the platform keys from the manufacturer to get a *pk8* and a *pem* file

1. find ~/Library/Android/sdk/build-tools -name "apksigner" を使用して、Android SDK の apksigner ツールを見つけます。
1. &lt;pathto&gt; /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk
1. Android SDKでzip alignツールへのパスを探します。
1. &lt;pathto&gt; /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk
1. *****adb install を使用して、デバイスに aemscreensaligned.apk をインストールします。*

## Android ウォッチドッグの実装 {#android-watchdog-implementation}

The cross-Android watchdog service is implemented as a cordova plugin using *AlarmManager*.

次の図に、ウォッチドッグサービスの実装を示します。

![chlimage_1-31](assets/chlimage_1-31.png)

**1.Initialization** At the time of initialization of the cordova plugin, permissions are checked to see if we have system privileges and thus the Reboot permission. これらの 2 つの条件を満たしている場合は、リブートのペンディングインテントが作成され、条件を満たしていない場合は、（Launch Activity に基づいて）アプリケーションを再起動するためのペンディングインテントが作成されます。

**2.Keep Alive Timer** A keep alive timer is used to trigger an event every 15 seconds. このイベントの間に、（アプリケーションをリブートまたは再起動する）既存のペンディングインテントをキャンセルし、次の 60 秒の間に新しいペンディングインテントを登録する（最終的にリブートを延期する）必要があります。

>[!NOTE]
>
>Android では、AlarmManager は、アプリケーションがクラッシュして、そのアラーム配信が API 19（Kitkat）から正確におこなわれなくても実行可能なペンディングインテントを登録するために使用されます。****&#x200B;タイマーの間隔と AlarmManager のペンディングインテントのアラームとの間にいくらかの時間を設けるようにしてください。****

**3.Application Crash** In case of a crash, the pendingIntent for Reboot registered with AlarmManager is no longer reset and thus it executes a reboot or restart of app (depending on permissions available at the time of initialization of the cordova plugin).
