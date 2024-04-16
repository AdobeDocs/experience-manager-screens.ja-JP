---
title: デバイスコントロールセンターからのトラブルシューティング
description: デバイスダッシュボードを使用して、AEM Screens Player アクティビティとデバイスのパフォーマンスを監視およびトラブルシューティングする方法について説明します。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 36%

---

# デバイスコントロールセンターからのトラブルシューティング {#troubleshooting-device-control-center}

デバイスダッシュボードを使用して、AEM Screens Player アクティビティとデバイスのパフォーマンスの監視とトラブルシューティングを行うことができます。 このページでは、Screens Player や割り当てられているデバイスを監視し、確認されたパフォーマンスの問題をトラブルシューティングする方法について説明します。

## デバイスコントロールセンターからの監視およびトラブルシューティング {#monitor-and-troubleshoot-from-device-control-center}

デバイスダッシュボードを使用して、アクティビティを監視し、AEM Screens Player のトラブルシューティングを行うことができます。

### デバイスダッシュボード {#device-dashboard}

デバイスダッシュボードに移動するには、次の手順を実行します。

1. プロジェクトからデバイスダッシュボード（例：）に移動します。 ***プロジェクトのテスト*** > ***デバイス***.

   クリック **デバイス** および **デバイスマネージャ** アクションバーから。

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 割り当て済みデバイスと未割り当てデバイスがリストに表示されます（下図を参照）。

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. デバイスをクリック（**NewTestDevice**）を選択し、 **Dashboard** アクションバーから。

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. このページには、デバイスの情報、アクティビティ、およびデバイスの詳細が表示され、デバイスのアクティビティと機能を監視できます。

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### デバイスアクティビティの監視 {#monitor-device-activity}

この **Activity** パネルには、AEM Screens Player の最後の ping がタイムスタンプと共に表示されます。 最後の ping は、デバイスが最後にサーバーに接続した時刻に対応します。

![chlimage_1](assets/chlimage_1.png)

また、 **ログを収集** の右上隅から **Activity** パネルを開いてプレーヤーのログを表示します。

### デバイスの詳細を更新 {#update-device-details}

を確認します **デバイスの詳細** パネルを使用すると、デバイスの IP、ストレージの使用状況、ファームウェアバージョン、プレーヤーの稼動時間を確認できます。

![chlimage_1-1](assets/chlimage_1-1.png)

また、 **キャッシュのクリア** および **更新** デバイスのキャッシュをクリアし、 [ファームウェア](screens-glossary.md) このパネルのバージョン。

また、 **...** の右上隅から **デバイスの詳細** パネルを開いて、プレーヤーのステータスを再起動または更新します。

![chlimage_1-2](assets/chlimage_1-2.png)

### デバイス情報の更新 {#update-device-information}

を確認します **デバイス情報** パネル。 ここで、設定の更新、デバイスモデル、デバイス OS、シェル情報を確認できます。

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

また、（**...**）を選択し、プロパティを表示するか、デバイスを更新します。

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

クリック **プロパティ** 以下に、 **デバイス プロパティ** ダイアログが表示されます。 デバイスのタイトルを編集するか、設定更新のオプションを次のように選択できます **手動** または **自動**.

>[!NOTE]
>
>デバイスの自動更新または手動更新に関連するイベントについて詳しくは、***チャネルの管理***&#x200B;の[自動アップデートとデバイスダッシュボードからの手動アップデート](managing-channels.md)の節を参照してください。

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### View Player Screenshot {#view-player-screenshot}

**プレーヤーのスクリーンショット**&#x200B;パネルを使用すると、デバイスからプレーヤーのスクリーンショットを表示できます。

クリック （**...**）を選択し、「」をクリックします **スクリーンショットを更新** 実行中のプレーヤーのスナップショットを表示します。

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 環境設定を管理 {#manage-preferences}

**環境設定**&#x200B;パネルでは、デバイスの&#x200B;**管理 UI**、**チャネルスイッチャー**、**リモートデバッグ**&#x200B;の環境設定を変更できます。

>[!NOTE]
>これらのオプションの詳細については、を参照してください [AEM Screens Player](working-with-screens-player.md).

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

また、 **設定** をクリックして、デバイスの環境設定を更新します。 更新できる環境設定は次のとおりです。

* **サーバー URL**
* **解像度**
* **スケジュールを再起動**
* **最大数 保持するログファイルの**
* **ログレベル**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>次のログレベルのいずれかをクリックできます。
>* **無効**
>* **デバッグ**
>* **情報**
>* **警告**
>* **エラー**

![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## OSGi 設定のトラブルシューティング {#troubleshoot-osgi-settings}

空のリファラーを有効にして、デバイスがサーバーにデータを POST できるようにします。 例えば、空のリファラーのプロパティが無効になっていると、デバイスからスクリーンショットを投稿できません。

現在、これらの機能の一部は、OSGi 設定で *Apache Sling Referrer Filter の Allow Empty 設定*&#x200B;が有効になっている場合にのみ使用できます。ダッシュボードには、セキュリティ設定がこれらの機能の一部の動作を妨げる可能性があることを示す警告が表示される場合があります。

Apache Sling Referrer Filter の Allow Empty 設定を有効にするには、次の手順を実行します。

1. **Adobe Experience Manager Web Console Configuration**（`https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`）に移動します。
1. 「**allow.empty**」オプションをオンにします。
1. 「**保存**」をクリックします。

![chlimage_1-3](assets/chlimage_1-3.png)

### レコメンデーション {#recommendations}

次の節では、ネットワークリンク、サーバーおよびプレーヤーを監視して、の正常性を把握し、問題に対処することをお勧めします。

AEMには、次の機能を備えた監視機能が組み込まれています。

* *ハートビート* AEM Screens Player が実行中であることを示す値で、5 秒ごと。
* *スクリーンショット* Player に表示される内容を表示する Player から。
* AEM Screens Player *ファームウェア*&#x200B;バージョンがプレーヤーにインストールされていること。
* プレーヤー上に&#x200B;*空きストレージ領域*&#x200B;が存在すること。

サードパーティ製ソフトウェアによるリモート監視用のRecommendations:

* プレーヤーの CPU 使用率。
* AEM Screens Player プロセスが実行中かどうかを確認します。
* プレーヤーのリモート再起動/再起動。
* リアルタイム通知。

問題を診断してプレーヤーを再起動できるように、プレーヤーのハードウェアと OS をリモートログインでデプロイすることをお勧めします。

#### その他のリソース {#additional-resources}

参照： [ビデオ再生の設定とトラブルシューティング](troubleshoot-videos.md) チャネルで再生されるビデオをデバッグおよびトラブルシューティングする場合。
