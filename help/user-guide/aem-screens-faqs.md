---
title: AEM Screens 関する FAQ
description: AEM Screens プロジェクトに関する FAQ への回答をお読みください。
feature: Digital Signage, Content
role: Developer
level: Intermediate
exl-id: 67204f04-5535-407c-bd4d-fabfbf850411
source-git-commit: e82cfee5ecc6b639b7b2b65553d1635943b356ea
workflow-type: tm+mt
source-wordcount: '2135'
ht-degree: 68%

---

# AEM Screens 関する FAQ {#aem-screens-faqs}

このトピックでは、AEM Screens プロジェクトに関する FAQ への回答を示します。

## 空白の画面の問題 {#blank-screen}

>[!NOTE]
>リストに示した必須チェックは、問題を発生させる前に、プライマリサポートまたは顧客側サポートが試す必要があるものです。

### 1. 顧客が黒い画面やコンテンツが再生できない問題に直面した場合、応急処置のトラブルシューティング手順は何ですか？  {#troubleshooting-blank-screen}

* チャネルプレビューが動作しているかどうかを確認します。
* ディスプレイプレビューが動作しているかどうかを確認します。
* プレーヤーをシステム上のブラウザー拡張機能として同じディスプレイに登録し、機能しているかどうかを確認してください。
* システム上でプレーヤーを実行しながら、`http://localhost:24502` に移動します。すべてのコンテンツが正しくダウンロードされているかどうかを確認します。
* アセットに適切なレンディションが作成され、正しいレンディションが再生されていることを確認します。
* スケジュールされたコンテンツがあるかどうか、および時間が正しいかどうかを確認します。プレーヤーで設定された時間が正しいかどうかを確認します。
* Inspect プレーヤーコンソールはログを記録し、エラーがないか確認します。右クリックし、コンソールログを確認します。Windows プレーヤーを使用している場合は、 `CTRL + ALT +I` ：開発コンソールを起動してログを表示します。

### 2. デフォルトのチャネルやスケジュールを作成して AEM Screens でグレーの画面の問題を解決するには、どうすればよいですか？

フィールドに空白またはグレーの画面が表示されないようにするには、デフォルトのグローバルチャネルまたはスケジュールを作成し、すべてのディスプレイに最も低い優先度 1 を割り当てます。コンテンツの更新で問題が発生した場合は、プレーヤーがこのコンテンツを既にディスクにキャッシュしているからです。 正常に再生され、グレーの画面は表示されません。

チャネルやスケジュールなど、他のすべてのコンテンツの優先度は 1 より大きいので、他のコンテンツが優先され、グローバルチャネルまたはスケジュールのコンテンツ（優先度 1）はフォールバックオプションとしてのみ再生されます。

## チャネルの管理 {#channel-management}

### 1. オンラインチャネルとオフラインチャネルの違いは何ですか？  {#what-is-the-difference-between-an-online-and-an-offline-channel}

***オンラインチャネル***&#x200B;では、最新のコンテンツがリアルタイム環境で表示されるのに対して、***オフラインチャネル***&#x200B;では、キャッシュされたコンテンツが表示されます。

### 2. チャネルをオンラインにするには、どうすればよいですか？  {#how-do-i-make-a-channel-online}

チャネルをクリックし、アクションバーからチャネルプロパティに移動します。 「**チャネル**」タブで「**開発者モード (チャネルをオンラインに強制)**」をオンにして、チャネルをオンラインにします。

### 3. 「チャネルロール」フィールドは何に使用しますか？  {#what-is-the-use-of-the-channel-role-field}

チャネルロールは、作成者が一般的なエクスペリエンスに直接専念できるように、実行される実際のチャネルを抽象化したものです。チャネルをそのコンテキスト（ディスプレイまたはスケジュール）で一意に識別する一種のタグと考えることができます。

### 4. 実際のチャネル解決はどのように行われますか？ {#how-does-actual-channel-resolution-happen}

*静的参照*&#x200B;の場合、解決は指定されたパスに従うだけです。

*動的参照*&#x200B;の場合は、チャネルが（スケジュールではなく）ディスプレイに割り当てられると、解決が行われます。ディスプレイのパスがチャネルのコンテキストになり、解決は次のように（優先順位の高い順に）行われます。

1. ディスプレイに、参照先のチャネル名と一致する子ノードがあります
1. ディスプレイに、参照先のチャネル名と一致する兄弟ノードがあります
1. ディスプレイの親の場所に、参照先のチャネル名と一致する子ノードがあります
1. ディスプレイの祖父母の場所に、参照先のチャネル名と一致する子ノードがあります

というように、あなたは場所フォルダーに到達するまで。 （そのため、チャネルフォルダー内にあるチャネルを参照することはできません。例えば、場所サブツリー内のチャネルのみを参照します）。

### 5. AEM Screens チャネルにカスタム clientlib のオフライン設定を行うにはどうすればよいですか？

ビルド済みのカスタムクライアント側コードを使用する場合 `clientlib` AEM Screens チャンネルでは、次の手順が必要です。 これらの手順により、以下を確実に実現できます。 `clientlib` ファイルはチャネル（`manifest.json`）に設定し、のパスを格納します。 `clientlib`.

チャネルエディターで次の手順に従います。

1. チャネルをクリックしてから、 **編集** アクションバーから。
1. カスタムを追加するコンポーネントをクリックします `clientlib`.
1. 設定ボタン（レンチアイコン）をクリックします。
1. 「**オフライン設定**」タブに移動し、カスタム clientlib のパスを「**クライアント側ライブラリ**」に追加します。

## デバイスの登録 {#device-registration}

### 1. デバイスのオンボーディングや登録のリクエストなどのエンドポイントを検出した場合、多数のデバイスをスクリプト化して、これらのデバイスを登録できます。ブランチ Wi-Fi にロックする以外に、これらのリクエストを保護することは可能ですか？ {#if-i-discover-endpoints-such-as-requests-for-device-onboarding-and-registration-i-can-script-a-large-number-of-devices-and-register-these-devices-besides-locking-this-to-a-branch-wi-fi-is-it-possible-to-secure-these-requests}

現在、登録はオーサーインスタンス上でのみ可能です。登録サービスは認証されていませんが、保留中のデバイスを AEM に作成するだけで、実際にデバイスを登録したりディスプレイを割り当てたりすることはありません。

デバイスを登録するには（AEMでデバイスのユーザーを作成するには）、AEMに対して認証を行い、登録ウィザードに手動で従って登録を完了します。 理論的には、悪意のあるユーザーは複数の保留中のデバイスを作成する可能性がありますが、AEM ログインを持っていない場合は登録できません。

### 2. 何らかの認証形式で HTTP GET リクエストを HTTP POST リクエストに変換する方法はありますか？ {#is-there-a-way-to-transform-http-get-requests-into-http-post-with-some-form-of-authentication}

登録リクエストは POST リクエストです。

パラメーターとして渡されるのではなく、セッションからデバイス ID を取得することをお勧めします。 これにより、サーバーログやブラウザーのキャッシュなどがクリーンアップされます。 これはセキュリティ上の問題にはなっていません。意味的に GET は、サーバー上で状態変化がない場合に使用され、状態変化がある場合は POST が使用されます。

### 3. デバイス登録リクエストを拒否する方法はありますか？  {#is-there-a-way-to-decline-a-device-registration-request}

登録リクエストを拒否することはできません。代わりに、で設定したタイムアウトの後に登録リクエストの有効期限が切れます。 `Adobe Experience Manager Web Console`. デフォルトでは、この値は 1 日に設定され、メモリキャッシュに保存されます。

## デバイスの監視とヘルスレポート {#device-monitoring-and-health-reports}

### 1. AEM Screens Player に空白の画面が表示される場合、トラブルシューティングをおこなうには、どうすればよいですか？

画面が空白になる問題のトラブルシューティングを行うには、以下の可能性がないか確認してください。

* AEM がオフラインコンテンツをプッシュできない
* チャネルにコンテンツがありません
* 現在の時間に表示するようにスケジュールされているアセットはありません

### 2. AEM Screens Player を登録できず、ステータスが「失敗」と表示される場合は、どうすればよいですか？

Apache Sling Referrer Filter の「Allow Empty」をオンにします。AEM Screens Player とAEM Screens Server の間で制御プロトコルの最適なオペレーションを行うために必要です。

1. **Adobe Experience Manager Web コンソールの設定**&#x200B;に移動します。
1. 「**allow.empty**」オプションをオンにします。
1. 「**保存**」をクリックします。

### 3. AEM Screens Player の登録中にデバイスに FAILURE が表示され、コンソールログに ENAME_NOT_FOUND エラーが表示される場合は、どのようにトラブルシューティングすればよいですか？

この問題は、プレーヤーが AEM Screens サーバーの DNS を検出できない場合に発生する可能性があります。IP アドレスを使用して接続してみてください。サーバーの IP を取得するには、次を使用します。 *arp &lt;server_dns_name>*.

### 4. AMS では、すべてのデバイスに Android™ ウォッチドッグを実装することを推奨していますか？ウォッチドッグ（Cordova）プラグインは APK に含まれていますか？ {#does-ams-recommend-implementing-an-android-watchdog-on-all-devices-is-the-watchdog-cordova-plugin-included-as-part-of-the-apk}

純粋な Android™ API を使用するクロスプラットフォームの Android™ ウォッチドッグは、既に APK に含まれています。追加のソフトウェアは必要ありません。ただし、使用するデバイスによっては、必要に応じて、apk を再署名して完全な電源サイクル（`Powermanager` api）を取得できます。製造元のキーを使用して再署名しない場合は、アプリケーションが終了して再起動しますが、電源サイクル（電源のオン／オフ）は行われません。

Android™ プレーヤーの実装方法について詳しくは、[**Android™ プレーヤーの実装**](implementing-android-player.md)&#x200B;を参照してください。

### 5. Adobe／AMS では、各デバイスの監視にどのようなサードパーティ製リモート監視および警告ツール（ソフトウェア）を推奨していますか？ {#what-third-party-remote-monitoring-and-alerting-tools-software-does-adobe-ams-recommend-for-monitoring-each-device}

必要な監視および警告機能にもよりますが、新機能である AEM Screens 通知サービスでは、デバイスがしばらくの間 ping に応答しなかった場合にユーザーに通知します。サードパーティツールは、お使いのオペレーティングシステム（OS）とその機能、およびユーザー固有のニーズによって異なります。

デバイスアクティビティの監視について詳しくは、[**AEM Screens 通知サービス**](screens-notifications-service.md)&#x200B;を参照してください。

## AEM Screens Player

### 1. ChromeOS プレーヤーを Chrome ブラウザープラグインとしてインストールする方法 {#how-to-install-chromeos-player-as-chrome-browser-plugin}

ChromeOS プレーヤーは、実際の Chrome プレーヤーデバイスを必要とせずに、開発者モードで Chrome ブラウザープラグインとしてインストールすることができます。 インストールについては、次の手順に従います。

1. [ここ](https://download.macromedia.com/screens/)をクリックして、最新の Chrome プレーヤーをダウンロードします。
1. 解凍してディスクに保存します。
1. Chrome ブラウザーを開き、 **拡張機能** メニューから、または直接に移動 ***chrome://extensions***.
1. をオンにする **開発者モード** 右上隅から
1. クリック **展開されたロード** 左上隅から解凍した Chrome プレーヤーを読み込みます。
1. 拡張機能のリストで使用可能な場合は、 **AEM Screens Chrome Player** プラグイン。
1. 新しいタブを開き、左上隅の「**アプリ**」アイコンをクリックするか、***chrome://apps*** に直接移動します。
1. 「」をクリックします **AEM Screens** プラグイン。 デフォルトでは、プレーヤーはフルスクリーンモードで起動します。**Esc** キーを押すと、フルスクリーンモードが終了します。

### 2. Screens Player がカスタムエラーハンドラーで公開インスタンスを通じて認証できない場合、トラブルシューティングするには、どうすればよいですか？

AEM Screens Player は、起動時に次の処理を行うよう要求します。 ***/content/screens/svc.ping.json***&#x200B;プレーヤーが 404 エラーを取得した場合。 プレーヤーが認証リクエストを開始して、パブリッシュインスタンスに対して認証を行います。パブリッシュインスタンスにカスタムエラーハンドラーがある場合は、匿名ユーザーの 404 ステータスコードを返します。 ***/content/screens/svc.ping.json***.

### 3. Android™ プレーヤーでデバイスの画面が常に表示されるように設定するには、どうすればよいですか？ {#how-to-set-the-device-screen-stay-on-in-an-android-player}

次の手順に従って、任意の Android™ プレーヤーで「スリープモードにしない」をオンにします。

1. Android™ プレーヤーの設定／**端末情報**&#x200B;に移動します。
1. ビルド番号を 7 回タップすると、**設定**&#x200B;の「**開発者向けオプション**」を有効にすることができます。
1. 「**開発者向けオプション**」に移動します。
1. 「**スリープモードにしない**」をオンにします。

### 4. Windows プレーヤーのウィンドウモードを有効にする方法{#enable-player}

Windows プレーヤーにはウィンドウモードはありません。 常に全画面表示モードです。

### 5. AEM Screens Player がログインリクエストを継続的に送信する場合のトラブルシューティング方法？

次の手順に従って、AEM Screens Player がリクエストを継続的に送信する場合のトラブルシューティングを行います `/content/screens/svc.json` および `/libs/granite/core/content/login.validate/j_security_check`:

1. AEM Screens Player は、起動時に次へリクエストします。 `/content/screens/svc.json`. プレーヤーが応答で 404 ステータスコードを取得すると、*パブリッシュ*&#x200B;インスタンスに対して `/libs/granite/core/content/login.validate/j_security_check` を使用して、認証リクエストを開始します。*パブリッシュ*&#x200B;インスタンスにカスタムエラーハンドラーがある場合、`/content/screens/svc.json` または `/content/screens/svc.ping.json` で、匿名ユーザーに対して必ず 404 のステータスコードを返すようにしてさい。

1. Dispatcher 設定で、これらのリクエストが `/filters` で許可されているかどうかを確認します。

   詳しくは、[Screens フィルターの設定](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#step-configure-screens-filters)を参照してください。

1. Dispatcher の書き換えルールによって、Screens のパスが別のパスに書き換えられているかどうかを確認します。

1. *オーサー*&#x200B;または&#x200B;*パブリッシュ*&#x200B;インスタンスに `/etc/map` ルールがあるかどうか、Screens のパスが `sling:match` と一致し、内部的に別のパスにリダイレクトされているかどうかを確認します。`/system/console/jcrresolver` で正しい URL を解決すると、これらの URL が&#x200B;*パブリッシュ*&#x200B;インスタンスによって他のパスに書き換えられているかどうかを識別できます。

1. Apache Sling Resource Resolver Factory の設定によって、内部で書き換えが行われているかどうかを確認します。

### 6. プレーヤー API からディスプレイとデバイスの詳細を取得する方法

ディスプレイとデバイスの詳細は、次の方法で取得できます。

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

### 1. Livefyre を無効にして A/P Screens エラーを回避するには、どうすればよいですか？ 

Livefyre を無効にしてログエラーを回避するには、次の手順を実行します。

1. ***Livefyre バンドルを無効にする：***

   * `https://<host>:<port>/system/console/bundles` に移動します。
   * AEM Livefyre バンドル `com.adobe.cq.social.cq-social-livefyre` を検索します。
   * クリック **停止**.

1. ***Livefyre ポーラーを無効にする***

   * CRXDE Lite で、`/etc/importers/polling/livefyre-poller/jcr:content` に移動します。
   * 新しいプロパティ *enabled* タイプ *Boolean* を追加します。
   * を設定 **Enabled プロパティ** ～になる **偽**.

### 2. Oak インデックス情報の追加方法  {#add-oak-index-info}

AEM Screens は、製品で使用されるクエリのインデックス定義を作成します。
`error.log` に&#x200B;*クエリトラバーサル WARN* がある場合は、クエリのカスタムインデックスを作成します。詳しくは、[インデックスの設定](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/deploying/deploying/queries-and-indexing#configuring-the-indexes)を参照してください。

[Oak ドキュメント](https://jackrabbit.apache.org/oak/docs/query/lucene.html)の追加リソースも参照できます。


### 3. v3 マニフェストを設定するための必須事項？ {#configure-v3}

v3 マニフェストを有効にするには、次の手順を実行します。

* Dispatcher を更新します。
詳しくは、[マニフェストバージョン v3 に対応した Dispatcher の設定](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens#configuring-dispatcherv3)を参照してください。

* カスタムコンポーネントを更新します。
詳しくは、[カスタムハンドラーのテンプレート](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop#custom-handlers)を参照してください。

* `/system/console/configMgr/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` でコンテンツ同期を無効にします。

* `/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.OfflineContentServiceImpl` でスマート同期を有効にします。

* `channel/experience fragment/page components` を編集します。

* 「**オフライン設定**」タブに移動します。

* `clientlibs ` およびマニフェストに追加する必要がある静的ファイルのフォルダーを入力します。

### 4. screens-cloud-ams-pkg-0.0.20 パッケージの後、screens-cloud-ams-pkg-0.0.16 と Screens コアバンドルがインストールされていて、アクティブでない場合は、どうすればよいですか？

AMS コネクタを動作させるには、最小バージョンの AEM 6.5 機能パック 8 をインストールする必要があります。参照： [対象](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202105#availability) そのため、AEM Screens機能パックの最小バージョンを取得できます。

### 5. Screens で CQ Link Externalizer サービスを設定する方法は？

このサービスは、オーサーインスタンスとパブリッシュインスタンスのパブリックホスト名を定義するために使用され、値を使用してデバイスサーバーの URL を更新したり、ContextHub のターゲティングもおこなったりします。

Screens の CQ Link Externalizer サービスは、次の方法で設定できます。

1. `http://localhost:4502/system/console/configMgr` に移動します。
1. Day CQ Link Externalizer
1. 必要に応じて `author/publish` エントリのホスト名を変更します。