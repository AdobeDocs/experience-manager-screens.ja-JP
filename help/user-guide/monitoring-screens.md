---
title: デバイスコントロールセンターのトラブルシューティング
description: デバイスダッシュボードを使用して、AEM Screens Player のアクティビティやデバイスのパフォーマンスを監視およびトラブルシューティングを行う方法について説明します。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
docset: aem65
feature: Digital Signage, Content, Players
role: Developer
level: Intermediate
exl-id: 57105d6d-51ff-44ca-bbf2-ae9cce8addd0
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 100%

---

# デバイスコントロールセンターのトラブルシューティング {#troubleshooting-device-control-center}

デバイスダッシュボードを使用して、AEM Screens Player のアクティビティやデバイスのパフォーマンスの監視とトラブルシューティングを行うことができます。このページでは、Screens Player や割り当てられているデバイスを監視し、確認されたパフォーマンスの問題をトラブルシューティングする方法について説明します。

## デバイスコントロールセンターからの監視およびトラブルシューティング {#monitor-and-troubleshoot-from-device-control-center}

デバイスダッシュボードを使用して、アクティビティを監視し、AEM Screens Player をトラブルシューティングできます。

### デバイスダッシュボード {#device-dashboard}

デバイスダッシュボードに移動するには、次の手順を実行します。

1. プロジェクトからデバイスダッシュボードに移動します（例：***テストプロジェクト***／***デバイス***）。

   アクションバーの「**デバイス**」および「**デバイスマネージャー**」をクリックします。

   ![screen_shot_2019-09-03at13823pm](assets/screen_shot_2019-09-03at13823pm.png)

1. 割り当て済みデバイスと未割り当てデバイスがリストに表示されます（下図を参照）。

   ![screen_shot_2019-09-05at12823pm](assets/screen_shot_2019-09-05at12823pm.png)

1. デバイス（**NewTestDevice**）をクリックし、アクションバーの「**ダッシュボード**」をクリックします。

   ![screen_shot_2019-09-05at13341pm](assets/screen_shot_2019-09-05at13341pm.png)

1. このページには、デバイスのアクティビティや機能を監視できるように、デバイス情報、アクティビティおよびデバイスの詳細が表示されます。

   ![screen_shot_2019-09-05at13700pm](assets/screen_shot_2019-09-05at13700pm.png)

### デバイスアクティビティの監視 {#monitor-device-activity}

**アクティビティ**&#x200B;パネルには、AEM Screens Player の最後の ping がタイムスタンプと共に表示されます。最後の ping は、デバイスがサーバーに最後にアクセスした時間と一致します。

![chlimage_1](assets/chlimage_1.png)

さらに、**アクティビティ**&#x200B;パネルの右上隅にある「**ログを収集**」をクリックすると、プレーヤーのログが表示されます。

### デバイス詳細の更新 {#update-device-details}

デバイスの IP、ストレージ使用状況、ファームウェアバージョンおよびプレーヤー稼動時間を確認するには、**デバイスの詳細**&#x200B;パネルをチェックします。

![chlimage_1-1](assets/chlimage_1-1.png)

また、このパネルでは、「**キャッシュをクリア**」や「**アップデート**」をクリックして、デバイスのキャッシュをクリアしたり、[ファームウェア](screens-glossary.md)バージョンをアップデートしたりすることもできます。

また、**デバイスの詳細**&#x200B;パネルの右上隅にある「**...**」をクリックして、プレーヤーを再起動したり、ステータスを更新したりすることもできます。

![chlimage_1-2](assets/chlimage_1-2.png)

### デバイス情報の更新 {#update-device-information}

**デバイス情報**&#x200B;パネルを確認します。ここでは、設定の更新、デバイスモデル、デバイス OS、シェル情報などを表示できます。

![screen_shot_2019-09-05at13853pm](assets/screen_shot_2019-09-05at13853pm.png)

また、デバイス情報パネルの右上隅にある「**...**」をクリックして、プロパティを表示したり、デバイスをアップデートしたりすることもできます。

![screen_shot_2019-09-05at14017pm](assets/screen_shot_2019-09-05at14017pm.png)

「**プロパティ**」をクリックすると、**デバイスのプロパティ**&#x200B;ダイアログボックスが表示されます。デバイスのタイトルを編集したり、設定の更新のオプションとして「**手動**」または「**自動**」を選択したりすることができます。

>[!NOTE]
>
>デバイスの自動更新または手動更新に関連するイベントについて詳しくは、***チャネルの管理***&#x200B;の[自動アップデートとデバイスダッシュボードからの手動アップデート](managing-channels.md)の節を参照してください。

![screen_shot_2019-09-05at14112pm](assets/screen_shot_2019-09-05at14112pm.png)

### プレーヤーのスクリーンショットの表示 {#view-player-screenshot}

**プレーヤーのスクリーンショット**&#x200B;パネルを使用すると、デバイスからプレーヤーのスクリーンショットを表示できます。

プレーヤーのスクリーンショットパネルの右上隅にある（「**...**」）をクリックし、「**スクリーンショットを更新**」をクリックすると、実行中のプレーヤーのスナップショットが表示されます。

![screen_shot_2019-09-05at14205pm](assets/screen_shot_2019-09-05at14205pm.png)

### 環境設定の管理 {#manage-preferences}

**環境設定**&#x200B;パネルでは、デバイスの&#x200B;**管理 UI**、**チャネルスイッチャー**、**リモートデバッグ**&#x200B;の環境設定を変更できます。

>[!NOTE]
>これらのオプションについて詳しくは、[AEM Screens Player](working-with-screens-player.md) を参照してください。

![screen_shot_2019-09-05at14250pm](assets/screen_shot_2019-09-05at14250pm.png)

また、右上隅の「**設定**」をクリックして、デバイスの環境設定を更新します。更新できる環境設定は次のとおりです。

* **サーバー URL**
* **解像度**
* **スケジュールを再起動**
* **保存するログファイルの最大数**
* **ログレベル**

![screen_shot_2019-09-05at14511pm](assets/screen_shot_2019-09-05at14511pm.png)

>[!NOTE]
>クリックできるログレベルは次のいずれかです。
>* **無効**
>* **デバッグ**
>* **情報**
>* **警告**
>* **エラー**

![screen_shot_2019-09-05at15645pm](assets/screen_shot_2019-09-05at15645pm.png)

## OSGi 設定のトラブルシューティング {#troubleshoot-osgi-settings}

デバイスからサーバーへのデータの投稿を許可するには、空のリファラーを有効にします。例えば、空のリファラーのプロパティが無効になっていると、デバイスからスクリーンショットを投稿できません。

現在、これらの機能の一部は、OSGi 設定で *Apache Sling Referrer Filter の Allow Empty 設定*&#x200B;が有効になっている場合にのみ使用できます。ダッシュボードには、セキュリティ設定がこれらの機能の一部の動作を妨げる可能性があることを示す警告が表示される場合があります。

Apache Sling Referrer Filter の Allow Empty 設定を有効にするには、次の手順を実行します。

1. **Adobe Experience Manager Web Console Configuration**（`https://localhost:4502/system/console/configMgr/org.apache.sling.security.impl.ReferrerFilter`）に移動します。
1. 「**allow.empty**」オプションをオンにします。
1. 「**保存**」をクリックします。

![chlimage_1-3](assets/chlimage_1-3.png)

### レコメンデーション {#recommendations}

次の節では、ヘルスを把握したり、問題に対処したりするために、ネットワークリンク、サーバーおよびプレーヤーを監視することが推奨されています。

AEM には、次を監視する機能が組み込まれています。

* 5 秒間隔の&#x200B;*ハートビート*&#x200B;は、AEM Screens Player が動作中であることを示します。
* プレーヤーの&#x200B;*スクリーンショット*&#x200B;は、プレーヤーに何が表示されているかを示します。
* *AEM Screens Player ファームウェア*&#x200B;バージョンはプレーヤーにインストールされます。
* プレーヤー上に&#x200B;*空きストレージ領域*&#x200B;が存在すること。

サードパーティ製ソフトウェアによるリモート監視の推奨事項は、次のとおりです。

* プレーヤーの CPU 使用率。
* AEM Screens Player プロセスが実行中かどうかを確認します。
* プレーヤーのリモート再起動。
* リアルタイム通知。

リモートログインで問題を診断して、プレーヤーを再起動を再起動できるように、プレーヤーのハードウェアと OS をデプロイすることをお勧めします。

#### その他のリソース {#additional-resources}

チャネルで再生するビデオのデバッグとトラブルシューティングを行う場合は、[ビデオ再生の設定とトラブルシューティング](troubleshoot-videos.md)を参照してください。
