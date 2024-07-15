---
title: AEM Screens でのオーサーおよびパブリッシュインスタンスの設定
description: AEM Screens のオーサーインスタンスとパブリッシュインスタンスを設定する方法について説明します。
exl-id: 5aef5f35-d946-4bf8-a2a8-c3ed532b7eef
source-git-commit: 6b4fc934c31640168528fa3e72cf634773f4f8e6
workflow-type: tm+mt
source-wordcount: '1940'
ht-degree: 100%

---


# AEM Screens でのオーサーおよびパブリッシュインスタンスの設定 {#configuring-author-and-publish-in-aem-screens}

このページでは、以下のトピックについて重点的に説明します。

* **オーサーインスタンスとパブリッシュインスタンスの設定**
* **パブリッシュトポロジのセットアップ**
* **公開の管理：オーサーからパブリッシュ経由でデバイスにコンテンツの更新を配信**

## 前提条件 {#prerequisites}

オーサーサーバーとパブリッシュサーバーの使用を開始する前に、以下に関する事前の知識が必要です。

* **AEM トポロジ**
* **AEM Screens プロジェクトの作成と管理**
* **デバイス登録プロセス**

>[!NOTE]
>
>この AEM Screens 機能は、AEM 6.4 Screens 機能パック 2 がインストールされている場合にのみ使用できます。この機能パックにアクセスするには、アドビサポートに連絡してアクセス権をリクエストします。アクセス権が付与されると、Package Share から機能パックをダウンロードできます。

>[!IMPORTANT]
>
>複数のパブリッシュインスタンスを Dispatcher と併用する場合は、Dispatcher をアップデートします。[スティッキーセッションの有効化](dispatcher-configurations-aem-screens.md#enable-sticky-session)を参照してください。

## オーサーインスタンスとパブリッシュインスタンスの設定 {#configuring-author-and-publish-instances}

>[!NOTE]
>
>オーサーとパブリッシュのアーキテクチャの概要と、コンテンツを AEM オーサーインスタンスで作成して、複数のパブリッシュインスタンスにフォワードレプリケートする方法について詳しくは、[オーサーとパブリッシュのアーキテクチャの概要](author-publish-architecture-overview.md)を参照してください。

次の節では、オーサーおよびパブリッシュトポロジにレプリケーションエージェントを設定する方法について説明します。

次のような 1 つのオーサーインスタンスと 2 つのパブリッシュインスタンスをホストする簡単な例を設定できます。

* オーサー > localhost:4502
* パブリッシュ 1（pub1） > localhost:4503
* パブリッシュ 2（pub2） > localhost:4504

## オーサー環境へのレプリケーションエージェントのセットアップ {#setting-replication-agents}

レプリケーションエージェントを作成するには、標準のレプリケーションエージェントの作成方法を習得します。

AEM Screens には次の 3 つのレプリケーションエージェントが必要です。

1. **デフォルトレプリケーションエージェント&#x200B;***（***標準レプリケーションエージェント**&#x200B;として指定）
1. **Screens レプリケーションエージェント**
1. **リバースレプリケーションエージェント**

### 手順 1：デフォルトレプリケーションエージェントの作成 {#step-creating-a-default-replication-agent}

以下の手順に従って、デフォルトレプリケーションエージェントを作成します。

1. AEM インスタンス／ハンマーアイコン／**操作**／**設定**&#x200B;に移動します。

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. 左側のナビゲーションツリーから「**レプリケーション**」をクリックします。

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. **レプリケーション**&#x200B;フォルダーから「**作成者のエージェント**」をクリックし、「**新規作成**」をクリックして新しい標準レプリケーションエージェントを作成します。

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. レプリケーションエージェントを作成できるように、「**タイトル**」と「**名前**」を入力し、「**作成**」をクリックします。

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. レプリケーションエージェントを右クリックし、「**開く**」をクリックして設定を編集します。

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. 「**編集**」をクリックします。

1. **エージェント設定**&#x200B;ダイアログボックスで、詳細を入力します。

   >[!NOTE]
   >
   >レプリケーションエージェントを有効にするには、「**有効**」をオンにする必要があります。デフォルト、Screens、リバースレプリケーションエージェントでこのオプションをオンにします。

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. 「**トランスポート**」タブに移動し、「**URI**」、「**ユーザー**」、「**パスワード**」を入力します。

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >また、既存のデフォルトレプリケーションエージェントをコピーして名前を変更することもできます。


#### 標準レプリケーションエージェントの作成 {#creating-standard-replication-agents}

1. pub1 の標準レプリケーションエージェントを作成します（標準のデフォルトエージェントが既に設定されている必要があります）。例えば、*`https://<hostname>:4503/bin/receive?sling:authRequestLogin=1`* のように指定します。
1. pub2 の標準レプリケーションエージェントを作成します。pub1 のレプリケーションエージェントをコピーし、トランスポート設定でポートを変更することで、トランスポートを pub2 に使用するように更新できます。例えば、*`https://<hostname>:4504/bin/receive?sling:authRequestLogin=1`* のように指定します。

#### Screens レプリケーションエージェントの作成 {#creating-screens-replication-agents}

1. pub1 の AEM Screens レプリケーションエージェントを作成します。標準では、ポート 4503 を指す名前付きの Screens レプリケーションエージェントが 1 つ用意されています。それを有効にします。
1. pub2 の AEM Screens レプリケーションエージェントを作成します。pub1 の Screens レプリケーションエージェントをコピーし、pub2 の 4504 を指すようにポートを変更します。

   >[!NOTE]
   >Screens レプリケーションエージェントの設定方法については、[Screens レプリケーションエージェントの設定](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/administering/configure-screens-replication)を参照してください。

#### Screens リバースレプリケーションエージェントの作成 {#creating-screens-reverse-replication-agents}

1. pub1 のリバースレプリケーションエージェントを作成します。
1. pub2 のリバースレプリケーションエージェントを作成します。pub1 のリバースレプリケーションエージェントをコピーし、トランスポート設定のポートを変更することで、トランスポートを pub2 に使用するように更新できます。

## パブリッシュトポロジのセットアップ {#setting-up-publish-topology}

### 手順 1：Apache Sling Oak-Based Discovery の設定 {#step-configure-apache-sling-oak-based-discovery}

トポロジ内のすべてのパブリッシュインスタンスに、Apache Sling Oak-Based Discovery をセットアップします。

パブリッシュインスタンスごとに以下を行います。

1. `https://<host>:<port>/system/console/configMgr` に移動します。
1. 「**Apache Sling Oak-Based Discovery Service**」の設定をクリックします。
1. トポロジコネクタ URL の更新：参加するすべてのパブリッシュインスタンスの URL を追加します。
   * `https://publish:4503/libs/sling/topology/connector`
   * `https://publish:4504/libs/sling/topology/connector`
1. **トポロジコネクタ `Whitelist` リスト**：すべてのパブリッシュインスタンスをカバーする IP またはサブネットに適応します。ポート番号なしで、すべてのパブリッシュインスタンスの IP／ホスト名を `whitelist` します。

1. 「**Auto-Stop Local-Loops**」をオンにします。

各パブリッシュインスタンスの設定を同じにする必要があり、ローカルループの自動停止により無限ループが防止されます。

#### 手順 2：パブリッシュトポロジの確認 {#step-verify-publish-topology}

任意のパブリッシュインスタンスについて、`https://:/system/console/topology` に移動します。各パブリッシュインスタンスが、**送信トポロジコネクタ**&#x200B;の下に表示されていることがわかります。

#### 手順 3：ActiveMQ Artemis クラスターのセットアップ {#step-setup-activemq-artemis-cluster}

この手順では、ActiveMQ Artemis クラスターの暗号化パスワードを作成できます。
トポロジ内のすべてのパブリッシュインスタンスのクラスターユーザーとパスワードは、同一である必要があります。ActiveMQ Artemis 設定のパスワードは暗号化する必要があります。インスタンスごとに専用の暗号化キーがあるので、Crypto Support を使用して、暗号化されたパスワード文字列を作成する必要があります。こうして暗号化されたパスワードを、ActiveMQ の OSGi 設定で使用できるようになります。

各パブリッシュインスタンスで以下を行います。

1. OSGi コンソールで、**MAIN**／**Crypto Support**（`https://<host>:<port>/system/console/crypto`）に移動します。
1. 目的のプレーンテキストパスワード（すべてのインスタンスに共通）を「**Plain Text**」に入力します。
1. 「**Protect**」をクリックします。
1. 値「**保護されたテキスト**」をメモ帳またはテキストエディターにコピーします。この値を、ActiveMQ の OSGi 設定で使用できます。

デフォルトでは、パブリッシュインスタンスごとに一意の暗号キーが存在するので、この手順を各パブリッシュインスタンスで実行し、次回の設定用にこの一意のキーを保存します。

>[!NOTE]
>
>パスワードは波括弧（{}）で囲んでください。次に例を示します。
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### 手順 4：ActiveMQ Artemis クラスターのアクティブ化 {#step-activate-activemq-artemis-cluster}

各パブリッシュインスタンスで以下を行います。

1. OSGi 設定マネージャー（`https://<host>:<port>/system/console/configMgr`）に移動します。
1. 「**Apache ActiveMQ Artemis JMS プロバイダー**」の設定をクリックします。
1. 以下を更新します。

   * ***クラスターパスワード***：インスタンスごとに前の手順で暗号化された値を使用
   * ***トピック***：`{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### ActiveMQ Artemis クラスターの確認 {#verify-activemq-artemis-cluster}

各パブリッシュインスタンスで次の手順に従います。

1. OSGi コンソールで、Main／ActiveMQ Artemis（`https://localhost:4505/system/console/mq`）に移動します。
1. Cluster Information／Topology でノード数 2、メンバー数 2 を選択し、他のインスタンスのポートを確認します。
1. テストメッセージを送信します（画面上部の「Broker Information」の下）。
1. 各フィールドを次のように変更します。

   1. **Destination**：/com.adobe.cq.screens/devTestTopic
   1. **Text**：Hello World
   1. 各インスタンスの `error.log` を表示すると、メッセージがクラスター全体で送受信されたことがわかります。

>[!NOTE]
>
>前の手順で設定を保存した後、OSGi コンソールに移動するのに数秒かかる場合があります。詳しくは、error.log を確認することもできます。

例えば、次の画像は、ActiveMQ Artemis サーバーの設定が正常におこなわれた場合に表示されます。

次の設定が */system/console/mq* に表示されない場合は、*/system/console/mq* に移動し、「**Restart**」をクリックしてブローカーを再起動します。

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### リファラーヘッダー要件の削除 {#remove-referrer-header-requirement}

各パブリッシュインスタンスの次の手順に従います。

1. **OSGi コンソール**&#x200B;を開いて **Configuration Manager** に移動します。
1. **Apache Sling リファラーフィルター**&#x200B;をクリックします
1. 設定を更新し、「**Allow Empty**」をオンにします。

### オーサーインスタンスとパブリッシュインスタンスの設定 {#configuring-author-and-publish-instance}

公開トポロジを設定したら、実装の実際の結果を表示するようにオーサーインスタンスとパブリッシュインスタンスを設定します。

>[!NOTE]
>
>**前提条件**
>
>この例に取りかかるには、AEM Screens プロジェクトを作成した後、プロジェクト内に場所、ディスプレイ、チャネルを作成します。チャネルにコンテンツを追加し、このチャネルをディスプレイに割り当てます。

#### 手順 1：AEM Screens Player（デバイス）の起動

1. 別のブラウザーウィンドウを起動します。
1. *Web* ブラウザーを使用して Screens Player（`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html`）に移動するか、AEM Screens アプリを起動します。デバイスを開くと、デバイスの状態が未登録であることがわかります。

>[!NOTE]
>
>AEM Screens Player を開くには、ダウンロードした AEM Screens アプリか web ブラウザーを使用します。

#### 手順 2：オーサー環境へのデバイスの登録 {#step-registering-a-device-on-author}

1. `https://localhost:4502/screens.html/content/screens/we-retail` に移動するか、プロジェクトをクリックして、デバイス／デバイスマネージャーに移動します。
1. 「**デバイスを登録**」をクリックします。
1. 「**デバイスを登録**」をクリックします。
1. 登録するデバイスをクリックして、「**デバイスを登録**」をクリックします。
1. 登録コードを確認し、「**検証**」をクリックします。
1. デバイスのタイトルを入力し、「**登録**」をクリックします。

#### 手順 3：ディスプレイへのデバイスの割り当て {#step-assigning-the-device-to-display}

1. 前の手順のダイアログボックスで、「**ディスプレイを割り当て**」をクリックします。
1. **Locations** フォルダーから、チャネルのディスプレイのパスをクリックします。
1. 「**割り当て**」をクリックします。
1. 「**完了**」をクリックしてプロセスを完了すると、デバイスが割り当てられます。

プレーヤーを確認すると、チャネルに追加したコンテンツが表示されます。

#### 手順 4：パブリッシュインスタンスへのデバイス設定の公開 {#step-publishing-device-configuration-to-publish-instances}

**デバイスの確認**

次の手順に従って、デバイスユーザーをレプリケートします。

1. ユーザー管理ページに移動します。例えば、`https://localhost:4502/useradmin` のように指定します。
1. **`screens-devices-master`** グループを検索します。
1. グループを右クリックし、「**アクティベート**」をクリックします。

>[!CAUTION]
>
>author-publish-screens-service はオーサージョブで使用されるシステムユーザーなので、アクティベートしないでください。

また、デバイス管理コンソールからデバイスをアクティブ化することもできます。次の手順に従います。

1. Screens プロジェクト／**デバイス**&#x200B;に移動します。
1. アクションバーの「**デバイスマネージャー**」をクリックします。
1. 次の図に示すように、デバイスをクリックし、アクションバーの「**アクティベート**」をクリックします。

![screen_shot_2019-02-21at111036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>または、デバイスをアクティベートした後で、サーバー URL を編集または更新することもできます。アクションバーの「**サーバー URL を編集**」をクリックします（下図を参照）。変更内容が AEM Screens Player に生成されます。

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### チェックリストの公開 {#publishing-check-list}

公開チェックリストの要点は次のとおりです。

* *Screens デバイスユーザー* - この情報は、AEM ユーザーとして保存され、**ツール**／**セキュリティ**／**ユーザー**&#x200B;でアクティブ化できます。ユーザー名の先頭には、「screens」とシリアル化された長い文字列が付けられます。

* *プロジェクト* - AEM Screens プロジェクト。
* *ロケーション* - デバイスの接続先となる場所。
* *チャネル* - ロケーションに表示されている 1 つ以上のチャネル。
* *スケジュール* - スケジュールを使用する場合は、このスケジュールを必ず公開します。
* *ロケーション、スケジュール、チャネルの各フォルダー* - 対応するリソースがフォルダー内にある場合。

次の手順に従って、オーサーとパブリッシュの動作を確認します。

1. オーサーインスタンスのチャネルコンテンツの一部を更新します。
1. 「**公開を管理**」を実行して、すべてのパブリッシュインスタンスに新しい変更を公開します。
1. 「**アクティベート**」を押して、**デバイスマネージャー**&#x200B;からデバイスをアクティベートします。
1. 「**URL を編集**」を選択して、オーサーインスタンス URL からパブリッシュインスタンス URL のいずれかに変更します。
1. AEM Screens Player に更新されたチャネルコンテンツが表示されることを確認します。
1. 別のパブリッシュインスタンスを使用して、これらの手順を繰り返します。


#### 手順 5 ：パブリッシュインスタンスを指すように管理パネルでデバイスを設定 {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Screens Player から管理 UI を表示するには、タッチ操作対応の AEM Screens Player またはマウスを使用して、左上隅を長押しして管理メニューを開きます。
1. サイドパネルの「**設定**」オプションをクリックします。
1. 「**サーバー**」のオーサーインスタンスをパブリッシュインスタンスに変更します。

AEM Screens Player で変更内容を表示します。

または、次の手順に従って、デバイス管理コンソールでサーバー URL を更新または編集することもできます。

1. AEM Screens プロジェクトに移動し、**デバイス**&#x200B;フォルダーをクリックします。
1. アクションバーの「**デバイスマネージャー**」をクリックします。
1. デバイスをクリックし、アクションバーの「**サーバー URL を編集**」をクリックします（下図を参照）。変更内容が AEM Screens Player に生成されます。

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

**公開管理**&#x200B;機能を使用すると、コンテンツの更新をオーサーからパブリッシュ経由でデバイスに配信できます。AEM Screens プロジェクト全体のコンテンツを公開／非公開にすることも、チャネル、場所、デバイス、アプリケーション、スケジュールのいずれか 1 つのコンテンツを公開／非公開にすることもできます。この機能について詳しくは、[オンデマンドコンテンツの更新](on-demand-content.md)を参照してください。

## トラブルシューティングのヒント {#troubleshoot-tips}

以下の節に従って、オーサー／パブリッシュの設定に関連したよくある質問についての回答をご確認ください。

### 最初の登録と割り当ての後に https から http へのリダイレクトを追加する方法について教えてください。 {#add-redirect}

**解決策**
`Proxy/Load Balancer Connection in the Jetty configuration` の有効化を `true` に設定します。

### `/content/dam/projects/<project>` 外部のアセットでオフラインコンテンツとプレーヤーダウンロードの問題を更新する方法について教えてください。{#update-offline-content}

**解決策**
より制限を厳しくする場合は、すべての `/content/dam` または使用する特定のアセットの bulk-offline-update-screens-service ユーザーと `screens-devices-master` グループに読み取り権限を付与します。

### Screens レプリケーションエージェントのエラーを解決する方法について教えてください。 {#replication-agent}

**解決策**
エージェント設定で「リバースレプリケーションに使用」オプションがオンになっていないことを確認してください。Screens レプリケーションエージェントは、リバースレプリケーションエージェントとして使用できません。この機能のスコープは、デバイスコマンドをオーサーからパブリッシュに転送することです。