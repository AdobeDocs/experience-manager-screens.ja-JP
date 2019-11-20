---
title: ContentSyncからSmartSyncへの移行
seo-title: ContentSyncからSmartSyncへの移行
description: このページでは、SmartSyncの機能およびContentSyncからSmartSyncへの移行方法について説明します。
seo-description: このページでは、SmartSyncの機能およびContentSyncからSmartSyncへの移行方法について説明します。
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
translation-type: tm+mt
source-git-commit: 66c741bb73bd5deb2bb5b06dd46f2e407d9c4b7e

---


# ContentSyncからSmartSyncへの移行 {#transitioning-from-contentsync-to-smartsync}

ここでは、SmartSync機能の概要と、サーバの負荷/ストレージとネットワークトラフィックを最小限に抑えてコストを削減する方法について説明します。

## 概要 {#overview}

SmartSyncは、AEM Screensで使用される最新のメカニズムです。 これは、オフラインチャネルをキャッシュし、プレイヤーに配信するために使用される現在の方法の代わりになります。

サーバー側とクライアント側の両方で実行されます。

**On Server-side**:

* アセットを含むチャネルのコンテンツは、/var/contentsync *にキャッシュされます*。
* キャッシュは、ディスプレイに使用可能なコンテンツを記述するマニフェストを介してプレーヤーに公開されます。

**クライアント側**:

* プレイヤーは、上記で生成されたマニフェストに基づいてコンテンツを更新します。

### SmartSyncを使用する利点 {#benefits-of-using-smartsync}

SmartSync機能は、AEM Screensプロジェクトに多くの利点を提供します。 これは

* ネットワークトラフィックとサーバ側のストレージ要件の大幅な削減
* プレイヤーは、アセットが見つからないか変更された場合にのみ、アセットをインテリジェントにダウンロードします
* サーバ側およびクライアント側のストレージ最適化

>[!NOTE]
>
>AEM ScreensプロジェクトにSmartSyncを使用することを強くお勧めします。

## ContentSyncからSmartSyncへの移行 {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>AEM 6.3 Feature Pack 5およびAEM 6.4 Feature Pack 3を既にインストール済みの場合は、SmartSyncを有効にしてアセットを使用できるようにし、ディスク領域の使用量を増やすことができます。 SmartSyncを有効にするには、次の節に従ってContentSyncからSmartSyncに移行し、SmartSyncを有効にします。
>
>SmartSyncは、サポートされるサーバーAEM 6.4.3 FP3を備えたScreens playerで使用できます。
>
>最新のプレーヤーをダウンロ [ードするには、『](https://download.macromedia.com/screens/) AEM Screens Player Downloads』を参照してください。 次の表に、各プラットフォームに必要な最小限のプレーヤーバージョンを示します。

| **プラットフォーム** | **サポートされるプレイヤーの最小バージョン** |
|---|---|
| Android | 3.3.72 |
| Chrome OS | 1.0.136 |
| Windows | 1.0.136 |

次の手順に従って、ContentSyncからSmartSyncに移行します。

1. ContentSyncからSmartSyncに移行するには、SmartSyncをアクティブ化する前にContentSyncキャッシュをクリアする必要があります。

   次の図に示すように、リンクhttps://localhost:4502/libs/cq/contentsync/content/console.htmlを使用してインスタンスからContentSync ***コンソールに移動し*** 、「 **キャッシュをクリア**」をクリックします。

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >SmartSyncを初めて使用する前に、すべてのコンテンツキャッシュをクリアする必要があります。

1. AEMインスタンス **—&gt;ハンマーアイコン —&gt;操作** —&gt; **WebコンソールからAdobe Experience Manager Web Console Configurationに移動します******。

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. **Adobe Experience Manager Web Console Configuration **が開きます。 offlinecontentservicesを検 *索します*。

   Screens Offline Content Serviceプロパティを検索するには、 **Command** +F **(Mac** )と **F** (Windows)Control( ******** Windows)Control(Windows)Control(Windows))を押します。

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. 「保存」 **をクリッ** クして「Screens Offline Content Services **** 」プロパティを有効にします。したがって、AEM ScreensでSmartSyncを使用します。
1. SmartSyncを有効にしたら、次の図に示すように、プロジェクトに移動し、「 **Update Offline Content**** （オフラインコンテンツを更新）」（アクションバーから）をクリックする必要があります。

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)