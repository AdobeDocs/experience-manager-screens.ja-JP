---
title: AEM Screensでの作成者と公開の設定
seo-title: AEM Screensでの作成者と公開の設定
description: AEM Screensのアーキテクチャは、従来のAEM Sitesのアーキテクチャに似ています。 コンテンツはAEMオーサーインスタンスで作成され、複数のパブリッシュインスタンスに転送複製されます。 このページでは、AEM Screens用の作成者と公開の設定方法について説明します。
seo-description: AEM Screensのアーキテクチャは、従来のAEM Sitesのアーキテクチャに似ています。 コンテンツはAEMオーサーインスタンスで作成され、複数のパブリッシュインスタンスに転送複製されます。 このページでは、AEM Screens用の作成者と公開の設定方法について説明します。
uuid: 0a6e87e7-0018-42ef-b484-9a3da61c636a
contentOwner: jsyal
content-type: reference
topic-tags: authoring
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
discoiquuid: f2397d11-a18b-4779-b77b-5f99b797f40c
docset: aem65
translation-type: tm+mt
source-git-commit: 221243c537e708aac44145c8d5d5a181ea80a293

---


# AEM Screensでの作成者と公開の設定 {#configuring-author-and-publish-in-aem-screens}

このページでは、次のトピックについて説明します。

* **作成者インスタンスと発行インスタンスの設定**
* **パブリッシュトポロジの設定**
* **パブリケーションの管理：作成者からデバイスに公開するコンテンツの更新の配信**

## 前提条件 {#prerequisites}

作成者サーバとパブリッシュサーバを使い始める前に、次の事項に関する事前の知識が必要です。

* **AEMトポロジ**
* **AEM Screensプロジェクトの作成と管理**
* **デバイス登録プロセス**

>[!NOTE]
>
>このAEM Screens機能は、AEM 6.4 Screens機能パック2をインストールしている場合にのみ使用できます。 この機能パックにアクセスするには、アドビサポートに連絡してアクセス権をリクエストする必要があります。アクセス権が付与されると、パッケージ共有から機能パックをダウンロードできるようになります。

## 作成者インスタンスと発行インスタンスの設定 {#configuring-author-and-publish-instances}

>[!NOTE]
>
>作成者と発行のアーキテクチャの概要、およびAEM作成者インスタンスでコンテンツを作成し、複数の発行インスタンスに転送複製する方法について詳しくは、「作成者と発行のアーキテクチャの概要」を参照 [してください](author-publish-architecture-overview.md)。

次の節では、作成者トポロジとパブリッシュトポロジで複製エージェントを設定する方法について説明します。

作成者と2つのパブリッシュインスタンスをホストする簡単な例を設定できます。

* 作成者 —&gt; localhost:4502
* 発行1(pub1) —&gt; localhost:4503
* 公開(pub2) —&gt; localhost:4504

## 作成者への複製エージェントの設定 {#setting-replication-agents}

レプリケーションエージェントを作成するには、標準のレプリケーションエージェントの作成方法を学習する必要があります。

画面に必要なレプリケーションエージェントは3つあります。

1. **デフォルト・レプリケー&#x200B;***ション・エージェント&#x200B;***(標準レプリケーション・エージェント**)
1. **画面複製エージェント**
1. **リバースレプリケーションエージェント**

### 手順1:デフォルトのレプリケーションエージェントの作成 {#step-creating-a-default-replication-agent}

次の手順に従って、デフォルトの複製エージェントを作成します。

1. AEMインスタンス —&gt;ハンマーアイコン —&gt;操作 **—&gt;設定に移動し** ます ****。

   ![screen_shot_2019-02-25at24621pm](assets/screen_shot_2019-02-25at24621pm.png)

1. 左側のナビゲ **ーション** ・ツリーから[Replication]を選択します。

   ![screen_shot_2019-02-25at24715pm](assets/screen_shot_2019-02-25at24715pm.png)

1. 「 **Replication** 」フォルダから「 **Agents on author** 」を選択し、「 **New** 」をクリックして、新しい標準レプリケーションエージェントを作成します。

   ![screen_shot_2019-02-25at25400pm](assets/screen_shot_2019-02-25at25400pm.png)

1. 複製エージェ **ントを作成する** 「Title **」と「Name** 」を入力し、「 **Create**」をクリックします。

   ![screen_shot_2019-02-25at25737pm](assets/screen_shot_2019-02-25at25737pm.png)

1. 複製エージェントを右クリックし、「 **Open** 」をクリックして設定を編集します。

   ![screen_shot_2019-02-25at30018pm](assets/screen_shot_2019-02-25at30018pm.png)

1. 「 **Edit** 」をクリックして **Agent Settings** （エージェント設定）ダイアログ・ボックスを開き、詳細を入力します。

   ![screen_shot_2019-02-25at30134pm](assets/screen_shot_2019-02-25at30134pm.png)

1. 「 **Transport** 」タブに移動し、 **URI**、User **、Password** を入 ****&#x200B;力します。

   ![screen_shot_2019-03-04at34955pm](assets/screen_shot_2019-03-04at34955pm.png)

   >[!NOTE]
   >
   >また、既存のデフォルト・レプリケーション・エージェントをコピーして名前を変更することもできます。


#### 標準レプリケーションエージェントの作成 {#creating-standard-replication-agents}

1. pub1用の標準レプリケーションエージェントを作成します（デフォルトのエージェントは既に設定されている必要があります）(例： *https://&lt;hostname&gt;:4503/bin/receive?sling:authRequestLogin=1*)。
1. pub2用の標準レプリケーションエージェントを作成します。 トランスポート構成のポートを変更することで、pub1のrepエージェントをコピーし、pub2に使用するトランスポートを更新できます。 (例： *https://&lt;hostname&gt;:4504/bin/receive?sling:authRequestLogin=1*)

#### 画面複製エージェントの作成 {#creating-screens-replication-agents}

1. pub1用のAEM Screensレプリケーションエージェントを作成します。 デフォルトで、ポート4503を指す画面複製エージェントという名前のエージェントがあります。 これは有効にする必要があります。
1. pub2用のAEM Screensレプリケーションエージェントを作成します。 pub1の画面レプリケーションエージェントをコピーし、pub2のポートを4504に変更します。

#### 画面逆複製エージェントの作成 {#creating-screens-reverse-replication-agents}

1. pub1用の標準逆複製エージェントを作成します。
1. pub2用の標準逆複製エージェントを作成します。 トランスポート構成のポートを変更することで、pub1のリバースrepエージェントをコピーし、pub2に使用するトランスポートを更新できます。

## パブリッシュトポロジの設定 {#setting-up-publish-topology}

### 手順1:Apache Sling Oakベースの検出の設定 {#step-configure-apache-sling-oak-based-discovery}

トポロジ内のすべての発行インスタンスに対してApache Sling Oak-Based Discoveryを設定します

各発行インスタンスに対して、次の操作を行います。

1. 次に移動 : `https://<host>:<port>/system/console/configMgr`
1. 「 **Apache Sling Oak-Based Discovery Service** Configuration」を選択します。
1. トポロジコネクタURLの更新：すべてのパーティングする発行インスタンスのURLの追加、 `https://localhost:4502/libs/sling/topology/connector`
1. トポロジコネクタホワイトリスト：パブリッシュインスタンスを覆うIPまたはサブネットに適応
1. ローカル **ループの自動停止の有効化**

各パブリッシュインスタンスの設定は同じにする必要があり、自動停止ローカルループは無限ループを防ぎます。

#### 手順2:パブリッシュトポロジの確認 {#step-verify-publish-topology}

任意の発行インスタンスについて、に移動しま `https://<host>:<port>/system/console/topology`す。 各パブリッシュインスタンスがトポロジ内に表示されます。

#### 手順3:ActiveMQアルテミスクラスターのセットアップ {#step-setup-activemq-artemis-cluster}

この手順では、ActiveMQ Artemisクラスター用に暗号化されたパスワードを作成できます。
トポロジ内のすべてのパブリッシュインスタンスのクラスタユーザーとパスワードは、同じである必要があります。 ActiveMQ Artemis設定のパスワードを暗号化する必要があります。 各インスタンスは独自の暗号化キーを持つので、暗号化サポートを使用して暗号化されたパスワード文字列を作成する必要があります。 その後、ActiveMQ用のOSGi設定で暗号化されたパスワードが使用されます。

各発行インスタンスで：

1. OSGiコンソールで、 **MAIN** —&gt; **Crypto Support** (*https://&lt;host&gt;:&lt;port&gt;/system/console/crypto*)に移動します。
1. 目的のプレーンテキストパスワードを（すべてのインスタンスで同じ）プレーンテキストで入 **力します。**
1. 「保護」をク **リックします**。
1. 値「Protected Text」をメモ帳 **またはテキスト** ・エディタにコピーします。 この値は、ActiveMQのOSGi設定で使用されます。

デフォルトでは、各パブリッシュインスタンスには一意の暗号キーが存在するので、この手順を各パブインスタンスで実行し、次の設定用に一意のキーを保存する必要があります。

次に例を示します。**

Pub1 - `{1ec346330f1c26b5c48255084c3b7272a5e85260322edd59119828d1fa0a610e}`Pub2 - `{8d3d113c834cc4f52c2daee0da3cb0a21122a31f0138bfe4b70c9ead79415f41}`

#### 手順4:ActiveMQアルテミスクラスターのアクティブ化 {#step-activate-activemq-artemis-cluster}

各発行インスタンスで、次の操作を行います。

1. OSGi Config Manager *https://&lt;ホスト&gt;:&lt;ポート&gt;/system/console/configMgrに移動します。*
1. 「 **Apache activeMQ Artemis JMS Provider** Configuration」を選択します。
1. 次を更新します。

* ***Cluster Password***:（各インスタンスごとに前の手順の暗号化された値を使用）
* ***トピック***:{name:'commands', address:'com.adobe.cq.screens.commands', maxConsumers:50}

#### ActiveMQアルテミスクラスターの確認 {#verify-activemq-artemis-cluster}

各発行インスタンスで次の手順に従います。

1. OSGi Console -&gt; Main &gt; activeMQ Artemisに移動します `[https://localhost:4505/system/console/mq`。
1. 「Cluster Information」&gt;「Topology」&gt;「nodes=2, members=2」で、他のインスタンスのポートを確認し、確認します。
1. テストメッセージの送信（画面の上部の「Broker Information」の下）
1. フィールドに次の変更を入力します。

   1. **宛先**:/com.adobe.cq.screens/devTestTopic
   1. **テキスト**:ハローワールド
   1. 各インスタンスのerror.logを表示して、メッセージがクラスター全体で送受信されたことを確認します

>[!NOTE]
>
>OSGIコンソールに移動すると、前の手順で設定を保存した後、数秒かかる場合があります。 詳しくは、error.logを確認することもできます。

例えば、次の画像は、ActiveMQ Artemis Serverの設定が成功した場合に表示されます。

次の設定が/system/console/mqから表示されない場合は、 */system/console/mqに移動し、「* Restart ****** 」をクリックしてブローカーを再起動します。

![image-2018-06-18-18-14-55-449](assets/image-2018-06-18-18-14-55-449.png)

#### リファラーヘッダー要件の削除 {#remove-referrer-header-requirement}

各発行インスタンスの手順に従います。

1. OSGiコンソール/ **Configuration** Managerに **移動します。**
1. Select **Apache Sling Referrer Filter**
1. 設定を更新し、「空白を **許可」をチェック**

### Configuring Author and Publish Instance {#configuring-author-and-publish-instance}

発行トポロジを設定したら、実装の実際の結果を表示するために、作成者インスタンスと発行インスタンスを設定する必要があります。

>[!NOTE]
>
>**前提条件**
>
>この例を使用するには、新しいAEM Screensプロジェクトを作成し、プロジェクト内に場所、表示、チャネルを作成します。 チャネルにコンテンツを追加し、チャネルをディスプレイに割り当てます。

#### 手順1:AEM Screens Player（デバイス）の起動 {#step-starting-an-aem-screens-player-device}

1. 別のブラウザーウィンドウを起動します。
1. Go to Screens player using the *web browser*, that is,`https://localhost:4502/content/mobileapps/cq-screens-player/firmware.html` or launch the AEM Screens app. デバイスを開くと、デバイスの状態が未登録であることがわかります。

>[!NOTE]
>
>AEM Screensプレーヤーは、ダウンロードしたAEM Screensアプリを使用するか、Webブラウザーを使用して開くことができます。

#### 手順2:作成者のデバイスの登録 {#step-registering-a-device-on-author}

1. プロジェクト `https://localhost:4502/screens.html/content/screens/we-retail` に移動するか、プロジェクトを選択し、デバイス/デバイスマネージャーに移動します。
1. 「 **Register Device**」を選択します。
1. 「 **Device Registration** 」をクリックしてデバイスを表示します。
1. 登録するデバイスを選択して、「**デバイスを登録**」をクリックします。
1. 登録コードを確認し、「 **Validate**」をクリックします。
1. デバイスのタイトルを入力し、「登録」をクリッ **クします**。

#### Step 3: Assigning the Device to Display {#step-assigning-the-device-to-display}

1. 前の手順 **で、ダイアログ** ・ボックスから「表示の割り当て」をクリックします。
1. [場所]フォルダからチャネルの表示パスを選択 **します** 。
1. 「**割り当て**」をクリックします。
1. Click **Finish** to complete the process, and now the device is assigned.

プレイヤーを確認すると、チャネルに追加したコンテンツが表示されます。

#### 手順4:発行インスタンスへの発行デバイス設定 {#step-publishing-device-configuration-to-publish-instances}

**デバイスの確認**

以下の手順を実行する前に、デバイスIDを確認してください。 検証するには、CRXDELiteでデバイスIDを検索し、パスを */home/users/screens/{project}/devicesにします*。

次の手順に従って、デバイスユーザーを複製します。

1. ユーザー管理ページに移動します(例： `https://localhost:4502/useradmin`
1. screens-devices- **masterグループの検索**
1. グループを右クリックし、「 **Activate」をクリックします。**

>[!CAUTION]
>
>作成者ジョブで使用されるシステムユーザーであるauthor-publish-screens-serviceはアクティブにしないでください。

デバイス管理コンソールからデバイスをアクティブ化することもできます。 次の手順に従います。

1. 画面プロジェクト/デバイスに移動 **します**。
1. アクションバーで「**デバイスマネージャ**」をクリックします。
1. 次の図に示すように、デバ **イスを選択し** 、アクションバーの「アクティブ化」をクリックします。

![screen_shot_2019-02-21at11036am](assets/screen_shot_2019-02-21at111036am.png)

>[!NOTE]
>
>または、デバイスをアクティベートしたら、アクションバーの「**サーバーのURLを編集**」をクリックして、サーバーURLを編集または更新することもできます。次の図に示すように、変更がAEM Screensプレーヤーに反映されます。

![screen_shot_2019-02-21at105527am](assets/screen_shot_2019-02-21at105527am.png)

### 発行チェックリスト {#publishing-check-list}

以下に、発行チェックリストの概要を示します。

* *Screens Device User* — これはAEMユーザーとして保存され、ツール/セキュリティ/ユーザーからア **クテ** ィブ化 **されます******。 ユーザーには、長いシリアライズされた文字列を含む「screens」というプリフィックスが付けられます。

* *プロジェクト* - AEM Screensプロジェクト。
* *場所* — デバイスが接続されている場所。
* *Channel(s)* — 場所に表示されている1つ以上のチャネル
* *スケジュール* — スケジュールを使用する場合は、この公開を確認する
* *場所、スケジュール、チャネルフォルダ* — 対応するリソースがフォルダ内にある場合。

チェックリストを確認したら、チャネルでの次の変更/動作を確認する必要があります。

* デバイス設定の公開後、画面プレーヤー設定を開き、発行インスタンスを指定します。 また、デバイス管理コンソールからデバイスをアクティブにすることもできます。
* 作成者のチャネルコンテンツを更新して公開し、更新されたチャネルがAEM Screensプレーヤーに表示されることを確認します。
* 画面プレーヤーを別の発行インスタンスに接続し、上記の動作を確認します。

#### 手順5:管理パネルでのデバイスの発行インスタンスの指定 {#step-pointing-the-device-to-publish-instance-in-the-admin-panel}

1. 管理UIは画面プレーヤーから表示し、左上隅を長押しして管理メニューを開くか、タッチ対応のAEM Screensプレーヤーで開くか、マウスを使用して表示します。
1. サイドパネル **で** 「設定」オプションをクリックします。
1. 作成者インスタンスを **Serverの発行インスタンスに変更**。

AEM Screensプレーヤーで変更を表示します。

また、次の手順を使用して、デバイス管理コンソールからサーバーURLを更新または編集することもできます。

1. AEM Screensプロジェクトに移動し、 **Devicesフォルダーを選択し** ます。
1. アクションバーから「**デバイスマネージャー**」をクリックします。
1. デバイスを選択し、アクションバーで「**サーバーURL **を編集」をクリックします。次の図に示すように、変更内容がAEM Screensプレーヤーに反映されます。

![screen_shot_2019-02-07at31028pm](assets/screen_shot_2019-02-07at31028pm.png)


