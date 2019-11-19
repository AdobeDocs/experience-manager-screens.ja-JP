---
title: トラブルシューティングデバイスコントロールセンター
seo-title: Screens の監視
description: このページに従って、デバイスダッシュボードを使用して、画面プレイヤーのアクティビティとデバイスのパフォーマンスを監視し、トラブルシューティングします。
seo-description: このページに従って、デバイスダッシュボードを使用して、画面プレイヤーのアクティビティとデバイスのパフォーマンスを監視し、トラブルシューティングします。
uuid: b6895d5d-c743-4e10-a166-de573e122335
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
discoiquuid: 3f130808-71e8-4710-8181-021d953660f8
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# トラブルシューティングデバイスコントロールセンター {#troubleshooting-device-control-center}

デバイスダッシュボードを使用して、画面プレイヤーのアクティビティとデバイスのパフォーマンスを監視し、トラブルシューティングできます。 このページでは、Screens Player や割り当てられているデバイスを監視し、確認されたパフォーマンスの問題をトラブルシューティングする方法について説明します。

## デバイスコントロールセンターからの監視およびトラブルシューティング {#monitor-and-troubleshoot-from-device-control-center}

デバイスダッシュボードを使用して、アクティビティを監視し、画面プレイヤーのトラブルシューティングを行うことができます。

### デバイスダッシュボード {#device-dashboard}

デバイスダッシュボードに移動するには、次の手順を実行します。

1. Navigate to the device dashboard from your project, for example, ***Test Project*** --&gt; ***Devices***.

   Select **Devices** and **Device Manager** from the action bar.

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 次の図に示すように、割り当て済みおよび割り当てられていないデバイスがリストに表示されます。

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. デバイス(NewTestDevice **)を選択し、アクションバ**&#x200B;ーで **** 「ダッシュボード」をクリックします。

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. このページには、デバイスのアクティビティや機能を監視できるように、デバイス情報、アクティビティおよびデバイス詳細が表示されます。

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### デバイスアクティビティの監視 {#monitor-device-activity}

**アクティビティ**&#x200B;パネルには、Screens Player の最後の ping とそのタイムスタンプが表示されます。最後の ping は、デバイスがサーバーに最後にアクセスした時間と一致します。

![chlimage_1](assets/chlimage_1.png)

Additionally, click **Collect Logs** from the top right hand corner of the **Activity** panel to view the logs for your player.

### デバイス詳細の更新 {#update-device-details}

デバイスの IP、ストレージ使用状況、ファームウェアバージョンおよびプレーヤー稼動時間を確認するには、**デバイスの詳細**&#x200B;パネルをチェックします。

![chlimage_1-1](assets/chlimage_1-1.png)

さらに、このパネルでは、「**キャッシュをクリア**」および「**更新**」をクリックして、デバイスのキャッシュをクリアしたり、[ファームウェア](screens-glossary.md)バージョンを更新したりすることもできます。

また、**デバイスの詳細**&#x200B;パネルの右上隅にある **...** をクリックして、プレーヤーを再起動したり、ステータスを更新したりすることもできます。

![chlimage_1-2](assets/chlimage_1-2.png)

### デバイス情報の更新 {#update-device-information}

「 **DEVICE INFORMATION** 」パネルをチェックして、構成の更新、デバイスモデル、デバイスOS、シェル情報を表示します。

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

Additionally, click the (**...**) from the top right corner of the Device Information panel to view properties or update the device.

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

「**プロパティ**」をクリックすると、**デバイスのプロパティ**&#x200B;ダイアログボックスが表示されます。デバイスのタイトルを編集したり、設定の更新オプションとして「**手動**」または「**自動**」を選択したりすることができます。

>[!NOTE]
>
>To learn more about the events associated with device's automatic or manual updates, see the section ***Automatic versus Manual Updates from the Device Dashboard*** in [Managing Channels](managing-channels.md).

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### プレーヤーのスクリーンショットの表示 {#view-player-screenshot}

デバイス上のプレーヤーのスクリーンショットは、**PLAYERのスクリーンショット**パネルで確認できます。

Click (**...**) on the top right corner of the Player Screenshot panel and select **Refresh Screenshot **to view the snapshot of the running player.

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 環境設定の管理 {#manage-preferences}

The **PREFERENCES** panel allows the user to change preferences for **Admin UI**, **Channel Switcher**, and **Remote Debugging** for the device.

>[!NOTE]
>
>これらのオプションについて詳しくは、[AEM Screens Player](working-with-screens-player.md) を参照してください。

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

また、右上隅の **「設定** 」をクリックして、デバイスの環境設定を更新します。 次の環境設定を更新できます。

* **サーバー URL**
* **解決方法**
* **スケジュールを再起動**
* **最大番号 ログファイルの**
* **ログレベル**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>
>次のいずれかのログレベルを選択できます。
>
>* **Disable（無効）**
>* **[Debug]**
>* **情報**
>* **警告**
>* **エラー**
>



![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## OSGI 設定のトラブルシューティング {#troubleshoot-osgi-settings}

デバイスからサーバーへのデータの送信を許可するには、空のリファラーを有効にする必要があります。例えば、空のリファラーのプロパティが無効になっていると、デバイスからスクリーンショットを返送できません。

現在、これらの機能の一部は、OSGI 設定で *Apache Sling リファラーフィルターの Allow Empty 設定*&#x200B;が有効になっている場合にのみ使用できます。ダッシュボードには、セキュリティ設定がこれらの機能の一部の動作を妨げる可能性があることを示す警告が表示される場合があります。

Apache Sling リファラーフィルターの Allow Empty 設定を有効にするには、次の手順を実行します。

1. Navigate to **Adobe Experience Manager Web Console Configuration**, that is, `https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`.
1. 「**allow.empty **」オプションを選択します。
1. 「**保存**」をクリックします。

![chlimage_1-3](assets/chlimage_1-3.png)

### 推奨事項 {#recommendations}

次の節では、ヘルスを把握したり、問題に対処したりするために、ネットワークリンク、サーバーおよびプレーヤーを監視することが推奨されています。

AEM の組み込みの監視では、次の点がチェックされます。

* 5 秒間隔のハートビート&#x200B;**。これは、AEM Screens Player が動作中であることを示します。
* プレーヤーのスクリーンショット&#x200B;**。これは、プレーヤーに現在何が表示されているかを示します。
* AEM Screens Player ファームウェア&#x200B;**&#x200B;バージョンがプレーヤーにインストールされていること。
* プレーヤー上に空きストレージ領域&#x200B;**&#x200B;が存在すること。

サードパーティソフトウェアを使用してリモート監視をおこなう場合は、次の点をチェックすることが推奨されています。

* プレーヤー上の CPU 使用量。
* AEM Screens Player プロセスの動作状態。
* プレーヤーのリモート再起動。
* リアルタイム通知。

プレーヤーハードウェアおよび OS をデプロイする際には、リモートログインを許可して問題の診断やプレーヤーの再起動をおこなえるようにすることをお勧めします。

#### その他のリソース {#additional-resources}

チャネルで再生 [するビデオのデバッグとトラブルシューティングを行うには](troubleshoot-videos.md) 、ビデオ再生の設定およびトラブルシューティングを参照してください。
