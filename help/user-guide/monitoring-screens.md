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
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 40%

---

# デバイスコントロールセンターからのトラブルシューティング {#troubleshooting-device-control-center}

デバイスダッシュボードを使用して、AEM Screens Player アクティビティとデバイスのパフォーマンスの監視とトラブルシューティングを行うことができます。 このページでは、Screens Player や割り当てられているデバイスを監視し、確認されたパフォーマンスの問題をトラブルシューティングする方法について説明します。

## デバイスコントロールセンターからの監視およびトラブルシューティング {#monitor-and-troubleshoot-from-device-control-center}

デバイスダッシュボードを使用して、アクティビティ監視、AEM Screensプレーヤーのトラブルシューティングを行うことができます。

### デバイスダッシュボード {#device-dashboard}

デバイスダッシュボードに移動するには、次の手順を実行します。

1. プロジェクトからデバイスダッシュボード(テスト プロジェクト ****** >***デバイス***&#x200B;など)に移動します。

   アクションバーから「**デバイス**」および「**デバイスマネージャー**」を選択します。

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 割り当て済みデバイスと未割り当てデバイスがリストに表示されます（下図を参照）。

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. デバイス（**NewTestDevice**）を選択し、アクションバーの「**ダッシュボード**」をクリックします。

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. ページには、デバイス情報、アクティビティ、およびデバイスアクティビティーと機能監視ためのデバイス詳細が表示されます。

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### デバイスアクティビティの監視 {#monitor-device-activity}

アクティビティ&#x200B;**パネルには**、AEM Screensプレーヤーの最後の ping がタイムスタンプとともに表示されます。最後の ping は、デバイスがサーバーに最後にアクセスした時間と一致します。

![chlimage_1](assets/chlimage_1.png)

また、[アクティビティ&#x200B;**]**&#x200B;パネルの右上隅にある [ログ&#x200B;**の収集] を選択して**、プレーヤーのログ表示します。

### デバイスの詳細を更新 {#update-device-details}

を確認します **デバイスの詳細** パネルを使用すると、デバイスの IP、ストレージの使用状況、ファームウェアバージョン、プレーヤーの稼動時間を確認できます。

![chlimage_1-1](assets/chlimage_1-1.png)

次も選択します **キャッシュのクリア** および **更新** デバイスのキャッシュをクリアし、 [ファームウェア](screens-glossary.md) このパネルのバージョン。

次も選択します **...** の右上隅から **デバイスの詳細** パネルを開いて、プレーヤーのステータスを再起動または更新します。

![chlimage_1-2](assets/chlimage_1-2.png)

### デバイス情報の更新 {#update-device-information}

**デバイス情報**&#x200B;パネルを確認します。ここでは、構成の更新、デバイスモデル、デバイス OS、およびシェル情報を表示できます。

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

また、[デバイスの情報] パネルの右上隅にある [**...**] を選択して、プロパティ表示たり、デバイスを更新したりします。

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

プロパティ&#x200B;**を選択して**、[**デバイスのプロパティ**] ダイアログ ボックス表示できるようにします。デバイスのタイトルを編集するか、設定更新のオプションを次のように選択できます **手動** または **自動**.

>[!NOTE]
>
>デバイスの自動更新または手動更新に関連するイベントについて詳しくは、***チャネルの管理***&#x200B;の[自動アップデートとデバイスダッシュボードからの手動アップデート](managing-channels.md)の節を参照してください。

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### View Player Screenshot {#view-player-screenshot}

**プレーヤーのスクリーンショット**&#x200B;パネルを使用すると、デバイスからプレーヤーのスクリーンショットを表示できます。

プレーヤーのスクリーンショット パネルの右上隅にある (**...**) をクリックし更新 [スクリーンショット&#x200B;**] を選択して**、実行中のプレーヤーのスナップショット表示ます。

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 環境設定の管理 {#manage-preferences}

**環境設定**&#x200B;パネルでは、デバイスの&#x200B;**管理 UI**、**チャネルスイッチャー**、**リモートデバッグ**&#x200B;の環境設定を変更できます。

>[!NOTE]
>これらのオプションの詳細については、「AEM Screens Player](working-with-screens-player.md)」を参照してください[。

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

次も選択します **設定** をクリックして、デバイスの環境設定を更新します。 更新できる環境設定は次のとおりです。

* **サーバー URL**
* **解像度**
* **スケジュールを再起動**
* **最大数 保持するログファイルの**
* **ログレベル**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>選択できるログレベルは次のいずれかです。
>* **無効**
>* **デバッグ**
>* **情報**
>* **警告**
>* **エラー**

![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## トラブルシューティング OSGi 設定 {#troubleshoot-osgi-settings}

空のリファラーを有効にして、デバイスがサーバーにデータを POST できるようにします。 例えば、空のリファラーのプロパティが無効になっていると、デバイスからスクリーンショットを投稿できません。

現在、これらの機能の一部は、OSGi 設定で *Apache Sling Referrer Filter の Allow Empty 設定*&#x200B;が有効になっている場合にのみ使用できます。ダッシュボードには、セキュリティ設定がこれらの機能の一部の動作を妨げる可能性があることを示す警告が表示される場合があります。

Apache Sling Referrer Filter の Allow Empty 設定を有効にするには、次の手順を実行します。

1. **Adobe Experience Manager Web Console Configuration**（`https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`）に移動します。
1. 「**allow.empty**」オプションをオンにします。
1. 「**保存**」をクリックします。

![chlimage_1-3](assets/chlimage_1-3.png)

### レコメンデーション {#recommendations}

次のセクションでは、ネットワークリンク、サーバー、およびプレーヤーを監視して、正常性を理解し、問題に対応することをお勧めします。

AEM には、次の監視機能が組み込まれています。

* *ハートビート* AEM Screens Player が実行中であることを示す値で、5 秒ごと。
* *スクリーンショット* Player に表示される内容を表示する Player から。
* AEM Screens Player *ファームウェア*&#x200B;バージョンがプレーヤーにインストールされていること。
* プレーヤー上に&#x200B;*空きストレージ領域*&#x200B;が存在すること。

サードパーティソフトウェアによるリモート監視のRecommendations:

* プレーヤー上の CPU 使用量。
* プレーヤープロセスAEM Screens実行中かどうかを確認します。
* プレーヤーのリモート再起動。
* リアルタイム通知。

リモートログイン問題を診断してプレーヤーを再起動できるように、プレーヤーのハードウェアと OS デプロイことをお勧めします。

#### その他のリソース {#additional-resources}

参照： [ビデオ再生の設定とトラブルシューティング](troubleshoot-videos.md) チャネルで再生されるビデオをデバッグおよびトラブルシューティングする場合。
