---
title: AEM Screens の FAQ
seo-title: AEM Screens FAQs
description: ここでは、AEM Screens プロジェクトに関連する FAQ への回答を掲載しています。
seo-description: Follow this page to get answers to FAQs related to an AEM Screens project.
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: 467526b82c07fd3594c704c1720477c72ecb9d38
workflow-type: tm+mt
source-wordcount: '1978'
ht-degree: 94%

---

# AEM Screens の FAQ {#aem-screens-faqs}

次の節では、AEM Screens プロジェクトに関してよく寄せられる質問に対する回答を示します。

## 空白の画面の問題 {#blank-screen}

>[!NOTE]
>リストに示した必須チェックは、問題を発生させる前に、プライマリサポートまたは顧客側サポートが試す必要があります。

### 1. 顧客が黒い画面やコンテンツが再生できない問題に直面した場合、応急処置のトラブルシューティング手順は何ですか？  {#troubleshooting-blank-screen}

* チャネルプレビューが動作しているかどうかを確認します。
* ディスプレイプレビューが動作しているかどうかを確認します。
* 同じディスプレイに、使用中のシステムのブラウザー拡張機能としてプレーヤーを登録してみて、これが動作しているかどうかを確認します。
* システム上でプレーヤーを実行しながら、`http://localhost:24502` に移動します。すべてのコンテンツが正しくダウンロードされているかどうかを確認します。
* アセットに適切なレンディションが作成され、正しいレンディションが再生されていることを確認します。
* スケジュールされたコンテンツがあるかどうか、および時間が正しいかどうかを確認します。プレーヤーで設定された時間が正しいかどうかを確認します。
* Inspect プレーヤーコンソールはログを記録し、エラーがないか確認します。右クリックし、コンソールログを確認します。Windows Player を使用している場合は、`CTRL + ALT +I` を押して開発コンソールを起動し、ログを表示します。

### 2. デフォルトのチャネルやスケジュールを作成して AEM Screens でグレーの画面の問題を解決するには、どうすればよいですか？

フィールドに空白またはグレーの画面が表示されないようにするには、デフォルトのグローバルチャネルまたはスケジュールを作成し、すべてのディスプレイに最も低い優先度 1 を割り当ててください。（ネットワーク、プレーヤー、サーバーまたはレプリケーションが原因で）コンテンツの更新で問題が発生した場合でも、このコンテンツは既にディスク上にキャッシュされているので、正常に再生され、グレーの画面は表示されません。

チャネルやスケジュールなど、他のすべてのコンテンツの優先度は 1 より大きいので、他のコンテンツが優先され、グローバルチャネルまたはスケジュールのコンテンツ（優先度 1）はフォールバックオプションとしてのみ再生されます。

## チャネルの管理 {#channel-management}

### 1. オンラインチャネルとオフラインチャネルの違いは何ですか？  {#what-is-the-difference-between-an-online-and-an-offline-channel}

***オンラインチャネル***&#x200B;では、最新のコンテンツがリアルタイム環境で表示されるのに対して、***オフラインチャネル***&#x200B;では、キャッシュされたコンテンツが表示されます。

### 2. チャネルをオンラインにするには、どうすればよいですか？  {#how-do-i-make-a-channel-online}

チャネルを選択し、アクションバーからチャネルのプロパティに移動します。「**チャネル**」タブで「**開発者モード (チャネルをオンラインに強制)**」をオンにして、チャネルをオンラインにします。

### 3. 「チャネルロール」フィールドは何に使用しますか？  {#what-is-the-use-of-the-channel-role-field}

「チャネルロール」は、作成者が汎用のエクスペリエンスに直接専念できるように、実行される実際のチャネルを抽象化したものです。チャネルをそのコンテキスト（ディスプレイまたはスケジュール）で一意に識別する一種のタグと考えることができます。

### 4. 実際のチャネル解決はどのようにおこなわれますか？  {#how-does-actual-channel-resolution-happen}

*静的参照*&#x200B;の場合、解決は指定されたパスに従うだけです。

*動的参照*&#x200B;の場合は、チャネルが（スケジュールではなく）ディスプレイに割り当てられると、解決がおこなわれます。ディスプレイのパスがチャネルのコンテキストになり、解決は次のように（優先順位の高い順に）おこなわれます。

1. ディスプレイに、参照先のチャネル名と一致する子ノードがあります
1. ディスプレイに、参照先のチャネル名と一致する兄弟ノードがあります
1. ディスプレイの親の場所に、参照先のチャネル名と一致する子ノードがあります
1. ディスプレイの祖父母の場所に、参照先のチャネル名と一致する子ノードがあります

場所フォルダーに到達するまでこのような解決を繰り返し、到達した時点で停止します（例えば、チャネルフォルダー内のチャネルを参照することはできません。参照できるのは、場所サブツリー内のチャネルだけです）。

### 5. AEM Screensチャネルでカスタム clientlib のオフライン設定をセットアップする方法

AEM Screensチャネルでカスタムのクライアント側コード `clientlib` を使用する場合、次の手順は、`clientlib` ファイルがチャネル (`manifest.json`) に正常に読み込まれ、`clientlib` のパスを含めるために必要です。

チャネルエディターから次の手順に従います。

1. チャネルを選択し、アクションバーの「**編集**」をクリックして、チャネルエディターを開きます。
1. カスタム `clientlib` を追加するコンポーネントを選択します。
1. 設定ボタン（レンチアイコン）をクリックします。
1. 「**オフライン設定**」タブに移動し、**クライアント側ライブラリ** のカスタムクライアントライブラリへのパスを追加します。

## デバイスの登録 {#device-registration}

### 1. デバイスのオンボーディングや登録のリクエストなどのエンドポイントを検出した場合、多数のデバイスをスクリプト化して、これらのデバイスを登録できます。これをブランチ Wi-Fi にロックする以外に、これらのリクエストのセキュリティを確保することは可能ですか？ {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

現在、登録はオーサーインスタンス上でのみ可能です。登録サービスは認証されていませんが、保留中のデバイスを AEM に作成するだけで、実際にデバイスを登録したりディスプレイを割り当てたりすることはありません。

デバイスを登録する（つまり、デバイスのユーザーを AEM に作成する）には、やはり AEM に対する認証が必要です。現時点では、登録ウィザードに従って手動で登録を完了する必要があります。理論的には、悪意のあるユーザーが保留中のデバイスを複数作成する可能性がありますが、AEM にログインしない限り、デバイスを登録することはできません。

### 2. 何らかの認証形式で HTTP GET リクエストを HTTP POST リクエストに変換する方法はありますか？ {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

登録リクエストは POST リクエストです。

デバイス ID は、パラメーターとして渡すのではなく、セッションから取得することをお勧めします。これにより、サーバーログ、ブラウザーキャッシュなどがクリーンアップされます。現時点では、これでセキュリティ上の問題にはなっていません。なお、意味的には、GET は、サーバー上で状態変化がない場合に使用され、状態変化がある場合は POST が使用されます。

### 3. デバイス登録リクエストを拒否する方法はありますか？  {#is-there-a-way-to-decline-a-device-registration-request}

登録リクエストを拒否することはできません。代わりに、`Adobe Experience Manager Web Console` で設定したタイムアウトの後に登録リクエストの有効期限が切れます。デフォルトでは、この値は 1 日に設定され、メモリキャッシュに保存されます。

## デバイスの監視とヘルスレポート {#device-monitoring-and-health-reports}

### 1. AEM Screens Player に空白の画面が表示される場合、トラブルシューティングをおこなうには、どうすればよいですか？  {#how-do-i-troubleshoot-if-my-aem-screens-player-shows-blank-screen}

画面が空白になる問題のトラブルシューティングをおこなうには、以下の可能性がないか確認してください。

* AEM がオフラインコンテンツをプッシュできない
* チャネルにコンテンツがない
* 現時点で表示予定のアセットがない

### 2. AEM Screens Player を登録できず、状態が失敗と表示される場合は、どうすればよいですか？  {#what-do-i-do-if-aem-screens-player-cannot-register-and-its-state-is-displayed-as-failure}

Apache Sling Referrer Filter の「Allow Empty」をオンにする必要があります。これは、AEM Screens Player と AEM Screens サーバーの間の制御プロトコルの最適な動作のために必要です。

1. **Adobe Experience Manager Web コンソールの設定**&#x200B;に移動します。
1. 「**allow.empty**」オプションをオンにします。
1. 「**保存**」をクリックします。

### 3. AEM Screens Player の登録中にデバイスに失敗と表示され、コンソールログに ENAME_NOT_FOUND エラーが表示される場合は、どのようにトラブルシューティングすればよいですか？  {#how-to-troubleshoot-if-while-registering-an-aem-screens-player-device-shows-failure-and-the-console-logs-display-ename-not-found-error}

この問題は、プレーヤーが AEM Screens サーバーの DNS を検出できない場合に発生する可能性があります。IP アドレスを使用して接続してみてください。サーバーの IP アドレスを取得するには、*arp &lt;server_dns_name>* を使用します。

### 4. AMS では、すべてのデバイスに Android ウォッチドッグを実装することを推奨していますか？ウォッチドッグ（Cordova）プラグインは APK に含まれていますか？ {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

純粋な Android API を使用するクロスプラットフォームの Android ウォッチドッグは、既に APK に含まれています。追加のソフトウェアは必要ありませんが、使用するデバイスによっては、APK に再署名して、完全な電源サイクルを実行するためのシステム権限（PowerManager API）を取得しなければならない場合があります。製造元のキーを使用して再署名しない場合は、アプリケーションが終了して再起動しますが、電源のオン／オフはおこなわれません。

Android プレーヤーの実装方法について詳しくは、[**Android プレーヤーの実装**](implementing-android-player.md)&#x200B;を参照してください。

### 5. Adobe／AMS では、各デバイスの監視にどのようなサードパーティ製リモート監視および警告ツール（ソフトウェア）を推奨していますか？  {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

必要な監視および警告機能にもよりますが、新機能である AEM Screens 通知サービスでは、デバイスがしばらくの間 ping に応答しなかった場合にユーザーに通知します。サードパーティツールは、お使いのオペレーティングシステム（OS）とその機能、およびユーザー固有のニーズによって異なります。

デバイスアクティビティの監視について詳しくは、[**AEM Screens 通知サービス**](screens-notifications-service.md)&#x200B;を参照してください。

## AEM Screens Player {#aem-screens-player}

### 1. Chrome OS プレーヤーを Chrome ブラウザープラグインとしてインストールするには、どうすればよいですか？  {#how-to-install-chromeos-player-as-chrome-browser-plugin}

Chrome OS プレーヤーは、実際の Chrome プレーヤーデバイスがなくても、開発者モードで Chrome ブラウザープラグインとしてインストールできます。インストールについては、次の手順に従います。

1. [ここ](https://download.macromedia.com/screens/)をクリックして、最新の Chrome プレーヤーをダウンロードします。
1. 解凍してディスクに保存します。
1. Chrome ブラウザーを開き、メニューから「**拡張機能**」を選択するか、***chrome://extensions*** に直接移動します。
1. 右上隅の「**デベロッパーモード**」をオンにします。
1. 左上隅の「**パッケージ化されていない拡張機能を読み込む**」をクリックし、解凍した Chrome プレーヤーを読み込みます。
1. **AEM Screens Chrome Player** プラグインが拡張機能の一覧にあれば、それをオンにします。
1. 新しいタブを開き、左上隅の「**アプリ**」アイコンをクリックするか、***chrome://apps*** に直接移動します。
1. 「**AEM Screens** プラグイン」をクリックして、Chrome プレーヤーを起動します。デフォルトでは、プレーヤーはフルスクリーンモードで起動します。**Esc** キーを押すと、フルスクリーンモードが終了します。

### 2. AEM Screens Player がカスタムエラーハンドラーでパブリッシュインスタンスを通じて認証できない場合、トラブルシューティングするには、どうすればよいですか？  {#how-to-troubleshoot-if-screens-player-is-unable-to-authenticate-through-publish-instance-with-custom-error-handler}

AEM Screens Player は、起動時に 404 エラーが発生すると、***/content/screens/svc.ping.json*** への要求をおこないます。プレーヤーが認証要求を開始して、パブリッシュインスタンスに対して認証をおこないます。パブリッシュインスタンスにカスタムエラーハンドラーがある場合、匿名ユーザーに対しては、***/content/screens/svc.ping.json*** の実行で必ず 404 のステータスコードを返すようにしてください。

### 3. Android プレーヤーでデバイスの画面が常に表示されるように設定するには、どうすればよいですか？  {#how-to-set-the-device-screen-stay-on-in-an-android-player}

次の手順に従って、任意の Android プレーヤーで「スリープモードにしない」をオンにします。

1. Android プレーヤーの設定／**端末情報**&#x200B;に移動します。
1. ビルド番号を 7 回タップして、**設定**&#x200B;の「**開発者向けオプション**」を有効にします。
1. **開発者向けオプション**&#x200B;に移動します。
1. 「**スリープモードにしない**」をオンにします。

### 4. Windows プレーヤーのウィンドウモードを有効にする方法{#enable-player}

Windows Player にはウィンドウモードはありません。常にフルスクリーンモードになります。

### 5. AEM Screens プレーヤーがログインリクエストを継続的に送信する場合のトラブルシューティング方法 {#requests-login}

次の手順に従って、AEM Screens プレーヤーが `/content/screens/svc.json` および `/libs/granite/core/content/login.validate/j_security_check` へ継続的にリクエストを送信する場合のトラブルシューティングをおこないます。

1. AEM Screens プレーヤーが起動すると、`/content/screens/svc.json` に対してリクエストをおこないます。プレーヤーが応答で 404 ステータスコードを取得すると、*パブリッシュ*&#x200B;インスタンスに対して `/libs/granite/core/content/login.validate/j_security_check` を使用し、認証要求を開始します。*パブリッシュ*&#x200B;インスタンスにカスタムエラーハンドラーがある場合、`/content/screens/svc.json` または `/content/screens/svc.ping.json` で、匿名ユーザーに対して必ず 404 のステータスコードを返すようにしてさい。

1. ディスパッチャー設定によってこれらのリクエストが許可されているかどうかを `/filters` で確認します。

   詳しくは、[Screens フィルターの設定](https://docs.adobe.com/content/help/ja-JP/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html#step-configuring-screens-filters)を参照してください。

1. ディスパッチャーの書き換えルールによって、Screens のパスが別のパスに書き換えられているかどうかを確認します。

1. *オーサー*&#x200B;または&#x200B;*パブリッシュ*&#x200B;インスタンスに `/etc/map` パスがあるかどうか、および Screens のパスが `sling:match` と一致し、内部的に別のパスにリダイレクトされているかどうかを確認します。`/system/console/jcrresolver` で正しい URL を解決すると、これらの URL が&#x200B;*パブリッシュ*&#x200B;インスタンスによって他のパスに書き換えられているかどうかを識別できます。

1. Apache Sling Resource Resolver Factory の設定によって、内部で書き換えがおこなわれているかどうかを確認します。

### 6. プレーヤー API からディスプレイとデバイスの詳細を取得する方法

ディスプレイとデバイスの詳細は、次の場所で取得できます。

* **内部 JS API**
* **ContextHub ストア**：`/libs/screens/clientlibs/contexthub` では、チャネル、デバイス、および表示情報を公開するための 3 つの ContextHub ストアが定義されています。

   次の手順に従って、ContentHub ストアの値を使用します。

   * チャネルのプロパティを編集し、パーソナライゼーションタブの ContextHub パスを値に設定します（上述）
   * チャネル JS では、次を使用できます。

      ```shell
         ContextHub.getStore('screens-device');
         ContextHub.getStore('screens-display');
         ContextHub.getStore('screens-channels');
      ```

## トラブルシューティングに関する一般的なヒント {#general-troubleshooting-tips}

### 1. Livefyre を無効にして A/P Screens エラーを回避するには、どうすればよいですか？  {#how-to-disable-livefyre-to-avoid-a-p-screens-error}

Livefyre を無効にしてログエラーを回避するには、次の手順に従います。

1. ***Livefyre バンドルを無効にする：***

   * `https://&lt;host&gt;:&lt;port&gt;/system/console/bundles` に移動します。
   * AEM Livefyre バンドル `com.adobe.cq.social.cq-social-livefyre` を検索します。
   * 「**停止**」をクリックします。

1. ***Livefyre ポーラーを無効にする***

   * CRXDE Lite で、`/etc/importers/polling/livefyre-poller/jcr:content` に移動します。
   * 新しいプロパティ *enabled*（*Boolean* 型）を追加します。
   * **enabled プロパティ**&#x200B;を **false** に設定します。

### 2. Oak インデックス情報の追加方法  {#add-oak-index-info}

AEM Screens は、製品で使用されるクエリのインデックス定義を作成します。
`error.log` に *クエリトラバーサル WARN* がある場合は、クエリのカスタムインデックスを作成します。詳しくは、「[インデックスの設定](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=ja#configuring-the-indexes)」を参照してください。

[Oak ドキュメント](https://jackrabbit.apache.org/oak/docs/query/lucene.html)の追加リソースも参照できます。
