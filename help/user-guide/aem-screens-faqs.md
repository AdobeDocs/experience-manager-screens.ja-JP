---
title: AEM Screens FAQ
seo-title: AEM Screens FAQ
description: このページに従って、AEM Screensプロジェクトに関連するFAQに答えてください。
seo-description: このページに従って、AEM Screensプロジェクトに関連するFAQに答えてください。
uuid: 62e58f3b-0c0a-4006-b6d5-42d2090f47b5
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: f6ee043e41e46690e057758266f9adc5323001d2

---


# AEM Screens FAQ {#aem-screens-faqs}

次の節では、AEM Screensプロジェクトに関してよく寄せられる質問に対する回答を示します。

## チャネルの管理 {#channel-management}

### 1.オンラインチャネルとオフラインチャネルの違いは何ですか。 {#what-is-the-difference-between-an-online-and-an-offline-channel}

An ***Online Channel***, will show the updated content in the real time environment whereas an ***Offline Channel***, shows the cached content.

### 2.チャネルをオンラインにする方法を教えてください。 {#how-do-i-make-a-channel-online}

チャネルを選択し、アクションバーからチャネルのプロパティに移動します。 チャネル **をオンラインにするには、「チャネル」タブで開発者モード** (チャネルを強制的にオンラ **インにする** )を確認します。

### 3.[チャネルの役割]フィールドの使用法 {#what-is-the-use-of-the-channel-role-field}

チャネルの役割は、作成者が汎用のエクスペリエンスに直接焦点を当てられるように、実行される実際のチャネルの抽象化です。 このタグは、コンテキスト内でチャネルを一意に識別するタグの一種と考えることができます（表示またはスケジュール）。

### 4.実際のチャネル解像度はどのように発生しますか。 {#how-does-actual-channel-resolution-happen}

静的 *参照の場合*、解像度は指定されたパスに従うだけです。

動的 *参照の場合*、チャネルが表示に割り当てられると（スケジュールではなく）、解像度が発生します。 表示パスがチャネルのコンテキストになり、解像度は次のようになります（優先順位が高い方から低い方）。

1. 表示には、参照先のチャネル名と一致する子ノードがあります
1. 表示には、参照されたチャネル名と一致する兄弟ノードがあります
1. 表示の親の場所に、参照先のチャネル名と一致する子ノードがあります
1. 表示の親の場所には、参照先のチャネル名と一致する子ノードがあります

例えば、locationsフォルダーに到達し、その時点でそこに停止するまで（例えば、channelsフォルダー内のチャネルを参照することはできません。ロケーションサブツリー内のチャネルだけです）。

## デバイスの登録 {#device-registration}

### 1.デバイスのオンボーディングや登録の要求などのエンドポイントを検出した場合、多数のデバイスをスクリプト化して、これらのデバイスを登録できます。 これをブランチWi-Fiにロックする以外に、これらの要求をセキュリティで保護することは可能ですか。 {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

現在、登録は作成者インスタンスでのみ可能です。 登録サービスは未認証ですが、AEMに保留中のデバイスを作成するだけで、実際にデバイスを登録したり、表示を割り当てたりすることはありません。

デバイスを登録する（つまり、AEMでデバイスのユーザーを作成する）には、AEMに対する認証が必要です。現在、登録ウィザードに従って手動で登録を完了する必要があります。 理論的には、悪意のあるユーザーが複数の保留中のデバイスを作成する可能性がありますが、AEMログインがない限り、登録することはできません。

### 2.何らかの認証形式でHTTP GETリクエストをHTTP POSTに変換する方法はありますか。 {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

登録要求はPOST要求です。

デバイスIDは、パラメーターとして渡されるのではなく、セッションから取得することをお勧めします。 これにより、サーバーログ、ブラウザーキャッシュなどがクリーンアップされます。 現在、セキュリティの問題ではありません。 意味的にはGETは、サーバー上で状態の変更がない場合に使用され、状態の変更がある場合にPOSTが使用されることに注意してください。

### 3.デバイス登録要求を拒否する方法はありますか。 {#is-there-a-way-to-decline-a-device-registration-request}

登録要求を却下することはできません。 代わりに、 [Adobe Experience Manager Web Consoleで設定したタイムアウト後に登録リクエストの有効期限が切れます](https://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.registration.impl.RegistrationServiceImpl)。 デフォルトでは、この値は1日に設定され、メモリキャッシュに保存されます。

## デバイスの監視と正常性レポート {#device-monitoring-and-health-reports}

### 1.AEM Screensプレーヤーが空白の画面を表示する場合、トラブルシューティングを行うにはどうすればよいですか。 {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

空白の画面の問題のトラブルシューティングを行うには、以下の可能性を確認してください。

* AEMはオフラインコンテンツをプッシュできません
* チャネルにコンテンツがありません
* 現在の時間に表示するようにスケジュールされたアセットはありません

### 2.AEM Screensプレーヤーが登録できず、状態が失敗と表示される場合はどうしますか。 {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Apache Slingリファラーフィルター「空白を許可」を有効にする必要があります。 これは、AEM Screens Player と AEM Screens サーバーの間の制御プロトコルの最適な動作のために必要です。

1. Navigate to **Adobe Experience Manager Web Console Configuration**
1. Check the **allow.empty** option.
1. 「**保存**」をクリックします。

### 3.AEM Screensプレーヤーの登録中にデバイスにエラーが表示され、コンソールログにENAME_NOT_FOUNDエラーが表示される場合のトラブルシューティング方法を教えてください。 {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

この問題は、プレーヤーがAEM ScreensサーバーのDNSを見つけられない場合に発生する可能性があります。 IPアドレスを使用して接続を試すことができます。 サーバーのIPを取得するには、次を使用します。 *arp &lt;server_dns_name&gt;*.

### 4.AMSは、すべてのデバイスにAndroidウォッチドッグを実装することをお勧めしますか？ APKにWatchdog(Cordova)プラグインは含まれていますか。 {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

純粋なAndroid APIを使用するクロスプラットフォームのAndroidウォッチドッグは、既にapkの一部です。 追加のソフトウェアは必要ありませんが、使用するデバイスに応じて、電源を完全に入れ直すためのシステム権限(Powermanager api)を取得するためにapkを辞退する必要がある場合があります。 製造元のキーを使用して停止しない場合は、アプリケーションを終了して再起動しますが、電源のオフ/オンは行われません。

Android Playerの実装方法について詳しくは、Android Playerの実装を参照 [**してください**](implementing-android-player.md)。

### 5.Adobe/AMSは、各デバイスの監視にどのサードパーティ製リモート監視および警告ツール（ソフトウェア）を推奨しますか。  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

監視とアラートの対象から外したいものに応じて、新しい機能のAEM Screens Notificationsサービスによって、デバイスにしばらくの間PINGが実行されなかった場合に通知されます。 サードパーティのツールは、お使いのオペレーティングシステム(OS)、その機能、お客様固有のニーズに応じて異なります。

デバイスのアクティビティを監視できる場所について詳しくは、 [**AEM Screens Notifications Serviceを参照してください**](screens-notifications-service.md)。

## AEM Screens Player {#aem-screens-player}

### 1.ChromeOSプレーヤーをChromeブラウザープラグインとしてインストールする方法を教えてください。 {#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOSプレーヤーは、実際のChromeプレーヤーデバイスを必要とせずに、開発者モードでChromeブラウザープラグインとしてインストールできます。 インストールの場合は、次の手順に従います。

1. 最新のChrome player [をダウンロードするには](https://download.macromedia.com/screens/) 、ここをクリックしてください。
1. 解凍してディスクに保存します。
1. Chromeブラウザーを開き、3つのドットを含むメニューをクリックし、右上隅の **More Tools** —&gt; **Extensions** (その他のツール ***—&gt;エクステンション)を選択するか、chrome://extensionsに直接移動***&#x200B;します。
1. 右上隅から **Developerモード** をオンにします。
1. 「**Load Unpacked **」をクリックし、解凍したChrome playerを読み込みます。
1. 拡張機能のリストに「 **AEM Screens Chrome Player** Plugin」がある場合は、それを確認します。
1. 新しいタブを開き、左上隅の **Apps** （アプリ）アイコンをクリックするか、chrome://appsに直接移動 ***します***。
1. 「 **AEM Screens** Plugin」をクリックしてChrome playerを起動します。 デフォルトでは、プレーヤーはフルスクリーンモードで起動します。 フルスク **リーンモード** を終了するには、Escキーを押します。

### 2.Screens playerが、カスタムエラーハンドラーを使用して発行インスタンスを通じて認証できない場合のトラブルシューティング方法を教えてください。 {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

AEM Screensプレーヤーが起動すると、プレーヤーが404エラーを受け取 ***ったときに***、/content/screens/svc.ping.jsonにリクエストが行われます。 プレーヤーが認証要求を開始し、発行インスタンスに対して認証を行います。 発行インスタンスにカスタムエラーハンドラーがある場合は、/content/screens/svc.ping.jsonで匿名ユーザーの404ステータスコードを返すように ***してください***。

### 3.Android Playerでデバイスの画面を常に表示する方法を教えてください。 {#how-to-set-the-device-screen-stay-on-in-an-android-player}

以下の手順に従って、任意のAndroidプレーヤーで「Stay Awake in」を有効にします。

1. Android Playerの設定 —/概要に移動しま **す。**
1. ビルド番号を7回タップして、「設定」の「開発者オプシ **ョン** 」を有効に **します**
1. 「開発者オプション」 **に移動します。**
1. 起きて **いる**

## トラブルシューティングに関する一般的なヒント {#general-troubleshooting-tips}

### 1.Livefyreを無効にしてA/P画面のエラーを回避する方法 {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

ログエラーを回避するためにLivefyreを無効にするには：

1. ***Livefyreバンドルを無効にする：***

   * 次に移動 : `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles`
   * AEM Livefyreバンドルを検索します。 `com.adobe.cq.social.cq-social-livefyre`
   * 「停止」をクリ **ック**

1. ***Livefyreポーラーを無効にする：***

   * CRXDE Liteで、 `/etc/importers/polling/livefyre-poller/jcr:content`
   * 有効にした新しいプロパティの *追加* (ブール *型)*
   * enabledプロ **パティを** falseに設 **定**

