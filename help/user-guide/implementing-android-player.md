---
title: Android プレーヤーの実装
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
source-git-commit: 2a3bbdd283f983cbdb5f21b606f508603385e041
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 90%

---


# Android プレーヤーの実装 {#implementing-android-player}

ここでは、Android プレーヤーの設定について説明します。使用可能な設定ファイルやオプションと、開発およびテストに使用する推奨設定について説明します。

さらに、プレーヤーをクラッシュから回復させるソリューションとして、**ウォッチドッグ**&#x200B;があります。アプリケーションは、ウォッチドッグサービスに登録し、アプリケーション自体がアライブであることを知らせるメッセージを定期的に送信する必要があります。ウォッチドッグサービスに、所定の時間内にキープアライブメッセージが届かないと、ウォッチドッグサービスは、デバイスをリブートしてクリーンリカバリを試みるか（ウォッチドッグサービスが十分な権限が持つ場合）、アプリケーションの再起動を試みます。

## Android プレーヤーのインストール {#installing-android-player}

AEM Screens 用の Android プレーヤーを実装するには、同プレーヤーをインストールしてください。

[**AEM 6.5 Player のダウンロード**](https://download.macromedia.com/screens/)ページにアクセスします。

### AEM Screens6.5.5 Service Packの環境の設定 {#fp-environment-setup}

>[!NOTE]
>AEM Screens6.5.5 Service Packを使用している場合は、Androidプレイヤー用の環境を設定する必要があります。

login-token cookieのSameSite属性をLax **から** None **に設定します。この値は、** Adobe Experience ManagerWeb ConsoleConfiguration ******** on all AEM authorおよびpublish instancesに設定します。

その場合は、次の手順に従います。

1. `http://localhost:4502/system/console/configMgr` を使用して、**Adobe Experience Manager Web コンソールの設定**&#x200B;に移動します。

1. *Adobe Granite トークン認証ハンドラー*&#x200B;を検索します。

1. **login-token cookie の SameSite 属性**&#x200B;を **Lax** から **None** に設定します。
   ![画像](/help/user-guide/assets/granite-updates.png)

1. 「**保存**」をクリックします。


### アドホック方式 {#ad-hoc-method}

アドホック方式を使用すると、最新の Android プレーヤー（**.exe）をインストールできます。[**AEM 6.5 Player のダウンロード**](https://download.macromedia.com/screens/)ページにアクセスします。

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

Android のアーキテクチャ上、デバイスをリブートするには、アプリケーションがシステム権限を持っている必要があります。そのためには、製造元の署名キーを使用して apk に署名する必要があります。この署名をおこなわないと、ウォッチドッグはデバイスをリブートするのではなく、プレーヤーアプリケーションを再起動します。

### 製造元のキーを使用した Android apk への署名    {#signage-of-android-apks-using-manufacturer-keys}

To access some of the privileged APIs of Android such as *PowerManager* or *HDMIControlServices*, you need to sign the android apk using the manufacturer&#39;s keys.

>[!CAUTION]
>
>前提条件：
>
>以下の手順を実行する前に、Android SDK をインストールしてください。

次の手順に従って、製造元のキーを使用して Android apk に署名します。

1. Google Play または [AEM Screens Player のダウンロード](https://download.macromedia.com/screens/)ページから apk をダウンロードします。
1. 製造元のプラットフォームキーを入手して、*pk8* ファイルと *pem* ファイルを取得します。

1. find ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot; を使用して、Android SDK の apksigner ツールを見つけます。
1. &lt;pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk
1. Android SDK の zip align ツールへのパスを見つけます。
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk
1. adb install を使用して、デバイスに ***aemscreensaligned.apk*** をインストールします。

## Android ウォッチドッグの実装 {#android-watchdog-implementation}

Android ウォッチドッグサービスは、*AlarmManager* を使用した cordova プラグインとして実装されます。

次の図に、ウォッチドッグサービスの実装を示します。

![chlimage_1-31](assets/chlimage_1-31.png)

**1.初期化**：cordova プラグインの初期化時、システム権限を持っているかどうか、さらに、リブート権限を持っているかどうかの確認がおこなわれます。これらの 2 つの条件を満たしている場合は、リブートのペンディングインテントが作成され、条件を満たしていない場合は、（Launch Activity に基づいて）アプリケーションを再起動するためのペンディングインテントが作成されます。

**2.キープアライブタイマー**：15 秒おきにイベントをトリガーするためにキープアライブタイマーが使用されます。このイベントの間に、（アプリケーションをリブートまたは再起動する）既存のペンディングインテントをキャンセルし、次の 60 秒の間に新しいペンディングインテントを登録する（最終的にリブートを延期する）必要があります。

>[!NOTE]
>
>Android では、*AlarmManager* は、アプリケーションがクラッシュして、そのアラーム配信が API 19（Kitkat）から正確におこなわれなくても実行可能な *pendingIntents* を登録するために使用されます。タイマーの間隔と *AlarmManager* の *pendingIntents* のアラームとの間にいくらかの時間を設けるようにしてください。

**3.アプリケーションのクラッシュ**：クラッシュした場合、AlarmManager に登録されているリブートのペンディングインテントはリセットされず、（cordova プラグインの初期化時に使用可能な権限に応じて）アプリケーションのリブートまたは再起動を実行します。
