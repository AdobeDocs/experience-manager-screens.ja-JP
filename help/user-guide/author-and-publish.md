---
title: AEM Screensでのオーサーインスタンスとパブリッシュインスタンスの設定
description: AEM Screensのオーサーインスタンスとパブリッシュインスタンスを設定する方法について説明します。
exl-id: 5aef5f35-d946-4bf8-a2a8-c3ed532b7eef
source-git-commit: 4b8013873be87d4d118f627d6131ff3e2fd087de
workflow-type: tm+mt
source-wordcount: '1937'
ht-degree: 43%

---


# AEM Screensでのオーサーインスタンスとパブリッシュインスタンスの設定 {#configuring-author-and-publish-in-aem-screens}

ここでは、以下のトピックについて重点的に説明します。

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
>このAEM Screens機能は、AEM 6.4 Screens 機能パック 2 がインストールされている場合にのみ使用できます。 この機能パックにアクセスするには、Adobeサポートに連絡し、アクセス権をリクエストする必要があります。 権限を持ったら、パッケージ共有からダウンロードできます。

>[!IMPORTANT]
>
>複数のパブリッシュインスタンスを Dispatcher と共に使用する場合は、Dispatcher を更新する必要があります。 詳しくは、[スティッキーセッションの有効化](dispatcher-configurations-aem-screens.md#enable-sticky-session)を参照してください。

## オーサーインスタンスとパブリッシュインスタンスの設定 {#configuring-author-and-publish-instances}

>[!NOTE]
>
>オーサーとパブリッシュのアーキテクチャの概要と、AEMオーサーインスタンスでコンテンツをオーサリングして、複数のパブリッシュインスタンスにフォワードレプリケートする方法について詳しくは、を参照してください。 [オーサーとパブリッシュのアーキテクチャの概要](author-publish-architecture-overview.md).

次の節では、オーサーおよびパブリッシュトポロジでレプリケーションエージェントを設定する方法について説明します。

1 つのオーサーインスタンスと 2 つのパブリッシュインスタンスをホストする簡単な例を設定できます。

* オーサー > localhost:4502
* パブリッシュ 1(pub1) > localhost:4503
* パブリッシュ 2(pub2) > localhost:4504

## オーサー環境へのレプリケーションエージェントのセットアップ {#setting-replication-agents}

レプリケーションエージェントを作成するには、標準のレプリケーションエージェントの作成方法を習得する必要があります。

Screens には、次の 3 つのレプリケーションエージェントが必要です。

1. **デフォルトレプリケーションエージェント&#x200B;***（***標準レプリケーションエージェント**&#x200B;として指定）
1. **Screens レプリケーションエージェント**
1. **リバースレプリケーションエージェント**

### 手順 1：デフォルトレプリケーションエージェントの作成 {#step-creating-a-default-replication-agent}

以下の手順に従って、デフォルトレプリケーションエージェントを作成します。

1. AEMインスタンス/ハンマーアイコンに移動します > **運用** > **設定**.

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. 左側のナビゲーションツリーから「**レプリケーション**」を選択します。

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. を選択します。 **作成者のエージェント** から **レプリケーション** フォルダーと選択 **新規** をクリックして、新しい標準レプリケーションエージェントを作成します。

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. 次を入力します。 **タイトル** および **名前** レプリケーションエージェントを作成し、「 **作成**.

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. レプリケーションエージェントを右クリックし、「 」を選択します。 **開く** をクリックして設定を編集します。

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. 「**編集**」を選択します。

1. Adobe Analytics の **エージェントの設定** ダイアログボックスで、詳細を入力します。

   >[!NOTE]
   >
   >ユーザーは次の項目を確認する必要があります： **有効** レプリケーションエージェントを有効にします。 デフォルト、画面、リバースレプリケーションエージェントで、このオプションをオンにします。

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. 次に移動： **輸送** タブに **URI**, **ユーザー**、および **パスワード**.

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >また、既存のデフォルトレプリケーションエージェントをコピーして名前を変更することもできます。


#### 標準レプリケーションエージェントの作成  {#creating-standard-replication-agents}

1. pub1 の標準レプリケーションエージェントを作成します（標準のデフォルトエージェントは既に設定されている必要があります）。 例えば、*`https://<hostname>:4503/bin/receive?sling:authRequestLogin=1`* のように指定します。
1. pub2 の標準レプリケーションエージェントを作成します。pub1 のレプリケーションエージェントをコピーし、トランスポート設定でポートを変更することで、トランスポートを pub2 に使用するように更新できます。例えば、*`https://<hostname>:4504/bin/receive?sling:authRequestLogin=1`* のように指定します。

#### Screens レプリケーションエージェントの作成 {#creating-screens-replication-agents}

1. pub1 のAEM Screensレプリケーションエージェントを作成します。 標準では、ポート 4503 を指す名前付きの Screens レプリケーションエージェントが 1 つ用意されています。有効にします。
1. pub2 のAEM Screensレプリケーションエージェントを作成します。 pub1 の Screens レプリケーションエージェントをコピーし、pub2 の 4504 を指すようにポートを変更します。

   >[!NOTE]
   >Screens レプリケーションエージェントの設定方法については、[Screens レプリケーションエージェントの設定](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configure-screens-replication)を参照してください。

#### Screens リバースレプリケーションエージェントの作成 {#creating-screens-reverse-replication-agents}

1. pub1 のリバースレプリケーションエージェントを作成します。
1. pub2 のリバースレプリケーションエージェントを作成します。pub1 のリバースレプリケーションエージェントをコピーし、トランスポート設定のポートを変更することで、トランスポートを pub2 に使用するように更新できます。

## パブリッシュトポロジのセットアップ {#setting-up-publish-topology}

### 手順 1：Apache Sling Oak-Based Discovery の設定 {#step-configure-apache-sling-oak-based-discovery}

トポロジ内のすべてのパブリッシュインスタンスに、Apache Sling Oak-Based Discovery をセットアップします。

各パブリッシュインスタンスに対して、次の操作を実行します。

1. `https://<host>:<port>/system/console/configMgr` に移動します。
1. 「**Apache Sling Oak-Based Discovery Service**」の設定を選択します。
1. トポロジコネクタ URL の更新：参加するすべてのパブリッシュインスタンスの URL を追加します。URL は以下のとおりです。
   * `https://publish:4503/libs/sling/topology/connector`
   * `https://publish:4504/libs/sling/topology/connector`
1. **Topology Connector のホワイトリスト**：すべてのパブリッシュインスタンスをカバーする IP またはサブネットに合わせます。 すべてのパブリッシュインスタンスの IP/ホスト名を、ポート番号を含めずにホワイトリストに登録してください。

1. 「**ローカルループの自動停止**」をオンにします。

各パブリッシュインスタンスの設定は同じにする必要があり、ローカルループの自動停止は無限ループを防ぎます。

#### 手順 2：パブリッシュトポロジの確認 {#step-verify-publish-topology}

任意のパブリッシュインスタンスについて、に移動します。 `https://:/system/console/topology`. 各パブリッシュインスタンスは、の下のトポロジに表示されます。 **送信トポロジコネクタ**.

#### 手順 3：ActiveMQ Artemis クラスターのセットアップ {#step-setup-activemq-artemis-cluster}

この手順では、ActiveMQ Artemis クラスターの暗号化パスワードを作成できます。
トポロジ内のすべてのパブリッシュインスタンスのクラスターユーザーとパスワードは、同じである必要があります。 ActiveMQ Artemis 設定のパスワードは暗号化する必要があります。 各インスタンスには独自の暗号化キーがあるので、Crypto Support を使用して暗号化されたパスワード文字列を作成する必要があります。 その後、暗号化されたパスワードを ActiveMQ の OSGi 設定で使用できます。

各パブリッシュインスタンスで以下をおこないます。

1. OSGi コンソールで、に移動します。 **メイン** > **暗号サポート** (`https://<host>:<port>/system/console/crypto`) をクリックします。
1. 目的のプレーンテキストパスワード（すべてのインスタンスに共通）を「**Plain Text**」に入力します。
1. 選択 **Protect**.
1. 「**Protected Text**」の値をメモ帳またはテキストエディターにコピーします。この値は、ActiveMQ の OSGi 設定で使用できます。

各パブリッシュインスタンスにはデフォルトで一意の暗号キーが割り当てられているので、各パブインスタンスでこの手順を実行し、次の設定用に一意のキーを保存します。

>[!NOTE]
>
>パスワードは波括弧（{}）で囲んでください。次に例を示します。
>`{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`

#### 手順 4：ActiveMQ Artemis クラスターのアクティブ化 {#step-activate-activemq-artemis-cluster}

各パブリッシュインスタンスで、以下の手順を実行します。

1. OSGi 設定マネージャー（`https://<host>:<port>/system/console/configMgr`）に移動します。
1. 「**Apache ActiveMQ Artemis JMS Provider**」の設定を選択します。
1. 以下を更新します。

   * ***Cluster Password***：（インスタンスごとに前の手順の暗号化された値を使用）
   * ***トピック***：`{name: 'commands', address: 'com.adobe.cq.screens.commands', maxConsumers: 50}`

#### ActiveMQ Artemis クラスターの確認 {#verify-activemq-artemis-cluster}

各パブリッシュインスタンスで次の手順に従います。

1. OSGi コンソール/メイン/ ActiveMQ Artemis に移動します。 `https://localhost:4505/system/console/mq`.
1. Cluster Information／Topology でノード数 2、メンバー数 2 を選択し、他のインスタンスのポートを確認します。
1. テストメッセージを送信します（画面上部の「Broker Information」の下）。
1. 各フィールドを次のように変更します。

   1. **Destination**：/com.adobe.cq.screens/devTestTopic
   1. **Text**：Hello World
   1. 次を表示： `error.log` 各インスタンスのを使用して、メッセージがクラスター全体で送受信されたことを確認できます。

>[!NOTE]
>
>前の手順で設定を保存した後、OSGi コンソールに移動すると、数秒かかる場合があります。 詳しくは、error.log を確認することもできます。

例えば、次の画像は、ActiveMQ Artemis サーバーの設定が正常におこなわれた場合に表示されます。

次の設定が */system/console/mq*&#x200B;を選択し、 */system/console/mq* を選択し、 **再起動** をクリックして、ブローカーを再起動します。

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### リファラーヘッダー要件の削除 {#remove-referrer-header-requirement}

各パブリッシュインスタンスで次の手順に従います。

1. **OSGi コンソール**&#x200B;を開いて **Configuration Manager** に移動します。
1. 「**Apache Sling Referrer Filter**」を選択します。
1. 設定を更新し、「**Allow Empty**」をオンにします。

### オーサーインスタンスとパブリッシュインスタンスの設定 {#configuring-author-and-publish-instance}

公開トポロジを設定したら、オーサーインスタンスとパブリッシュインスタンスを設定して、実装の実際の結果を表示します。

>[!NOTE]
>
>**前提条件**
>
>この例を開始するには、AEM Screensプロジェクトを作成した後、プロジェクト内にロケーション、ディスプレイ、チャネルを作成します。 チャネルにコンテンツを追加し、このチャネルをディスプレイに割り当てます。

#### 手順 1：AEM Screens Player（デバイス）の起動 {#step-starting-an-aem-screens-player-device}

1. 別のブラウザーウィンドウを起動します。
1. *Web* ブラウザーを使用して Screens Player（`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html`）に移動するか、AEM Screens アプリを起動します。デバイスを開いた際に、デバイスの状態が未登録であることに気がつきます。

>[!NOTE]
>
>AEM Screens Player を開くには、ダウンロードした AEM Screens アプリか Web ブラウザーを使用します。

#### 手順 2：オーサー環境へのデバイスの登録 {#step-registering-a-device-on-author}

1. `https://localhost:4502/screens.html/content/screens/we-retail` に移動するか、プロジェクトを選択してデバイス／デバイスマネージャーに移動します。
1. 「**デバイスを登録**」をクリックします。
1. 選択 **デバイスの登録**.
1. 登録するデバイスを選択し、「 」を選択します。 **デバイスを登録**.
1. 登録コードを確認し、 **検証**.
1. デバイスのタイトルを入力し、「 」を選択します。 **登録**.

#### 手順 3：ディスプレイへのデバイスの割り当て {#step-assigning-the-device-to-display}

1. 選択 **ディスプレイを割り当て** 前の手順のダイアログボックスから。
1. **ロケーション**&#x200B;フォルダーから、チャネルのディスプレイのパスを選択します。
1. 選択 **割り当て**.
1. 選択 **完了** をクリックしてプロセスを完了すると、デバイスが割り当てられます。

プレーヤーを確認し、チャネルに追加したコンテンツに注目します。

#### 手順 4：パブリッシュインスタンスへのデバイス設定の公開 {#step-publishing-device-configuration-to-publish-instances}

**デバイスの確認**

次の手順に従って、デバイスユーザーをレプリケートします。

1. ユーザー管理ページに移動します。 例えば、`https://localhost:4502/useradmin` のように指定します。
1. を検索します。 **`screens-devices-master`** グループ化します。
1. グループを右クリックし、「 」を選択します。 **有効化**.

>[!CAUTION]
>
>author-publish-screens-service はオーサージョブで使用されるシステムユーザーなので、アクティベートしないでください。

また、デバイス管理コンソールからデバイスをアクティブ化することもできます。次の手順に従います。

1. Screens プロジェクトに移動します/ **デバイス**.
1. 選択 **デバイスマネージャ** をクリックします。
1. デバイスを選択し、「 」を選択します。 **有効化** 次の図に示すように、アクションバーから。

![screen_shot_2019-02-21at111036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>または、デバイスをアクティベートした後で、サーバー URL を編集または更新することもできます。 選択 **サーバー URL を編集** 次の図に示すように、アクションバーから、変更がAEM Screens player に反映されます。

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### チェックリストの公開 {#publishing-check-list}

チェックリストの公開の要約を次に示します。

* *Screens デバイスユーザー* - AEM ユーザーとして保存され、**ツール**／**セキュリティ**／**ユーザー**&#x200B;でアクティブ化できます。ユーザーの前には、「screens」という長いシリアル化された文字列が付きます。

* *プロジェクト* - AEM Screens プロジェクト。
* *ロケーション* - デバイスの接続先となるロケーション。
* *チャネル*  — ロケーションに表示されている 1 つ以上のチャネル。
* *スケジュール* - スケジュールを使用する場合は、スケジュールを必ず公開します。
* *ロケーション、スケジュール、チャネルの各フォルダー* - 対応するリソースがフォルダー内にある場合。

次の手順に従って、オーサー/パブリッシュの動作を確認します。

1. オーサーインスタンスのチャネルコンテンツを更新します。
1. 実行 **公開を管理** をクリックして、すべてのパブリッシュインスタンスに新しい変更を公開します。
1. 押す **有効化** デバイスを有効にするには **デバイスマネージャ**.
1. **URL を編集** オーサーインスタンス URL からパブリッシュインスタンス URL の 1 つに移動します。
1. AEM Screens Player に更新されたチャネルコンテンツが表示されることを確認します。
1. 別のパブリッシュインスタンスを使用して、これらの手順を繰り返します。


#### 手順 5 ：パブリッシュインスタンスを指すように管理パネルでデバイスを設定 {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. Screens Player から Admin UI を表示し、タッチ操作対応のAEM Screens Player またはマウスを使用して Admin メニューを開くために左上隅を長押しします。
1. を選択します。 **設定** 」オプションを使用します。
1. でオーサーインスタンスをパブリッシュインスタンスに変更します。 **サーバー**.

AEM Screens Player で変更結果を表示します。

または、次の手順に従って、デバイス管理コンソールでサーバー URL を更新または編集することもできます。

1. AEM Screens プロジェクトに移動し、**デバイス**&#x200B;フォルダーを選択します。
1. 選択 **デバイスマネージャ** をクリックします。
1. デバイスを選択し、「 」を選択します。 **サーバー URL を編集** 次の図に示すように、アクションバーから、変更内容がAEM Screens player に反映されます。

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)

The **公開を管理** 機能を使用すると、コンテンツの更新をオーサーからパブリッシュ経由でデバイスに配信できます。 AEM Screensプロジェクト全体のコンテンツを公開/非公開にすることも、チャネル、ロケーション、デバイス、アプリケーション、スケジュールのいずれか 1 つに対してのみ公開/非公開にすることもできます。 この機能の詳細については、[オンデマンドコンテンツの更新](on-demand-content.md)を参照してください。

## トラブルシューティングのヒント {#troubleshoot-tips}

オーサー/パブリッシュの設定に関するよくある質問に対する回答を得るには、次の節に従います。

### 最初の登録と割り当ての後に https から http へのリダイレクトを追加する方法について教えてください。 {#add-redirect}

**解決策**
`Proxy/Load Balancer Connection in the Jetty configuration` の有効化を `true` に設定します。

### `/content/dam/projects/<project>` 外部のアセットでオフラインコンテンツとプレーヤーダウンロードの問題を更新する方法について教えてください。{#update-offline-content}

**解決策**
一括オフライン更新 —screens-service ユーザーの読み取り権限を付与し、 `screens-devices-master` すべてのグループ `/content/dam` 使用する特定のアセット（より制限を厳しくしたい場合）

### Screens レプリケーションエージェントのエラーを解決する方法について教えてください。 {#replication-agent}

**解決策**
エージェント設定で「リバースレプリケーションに使用」オプションがオンになっていないことを確認してください。Screens レプリケーションエージェントをリバースレプリケーションエージェントとして使用することはできません。この機能の範囲は、デバイスのコマンドをオーサーからパブリッシュに転送することです。