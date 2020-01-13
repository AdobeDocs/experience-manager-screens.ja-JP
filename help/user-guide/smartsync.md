---
title: コンテンツ同期からスマート同期への移行
seo-title: コンテンツ同期からスマート同期への移行
description: ここでは、スマート同期機能およびコンテンツ同期からスマート同期への移行方法について説明します。
seo-description: ここでは、スマート同期機能およびコンテンツ同期からスマート同期への移行方法について説明します。
uuid: c0619b56-1f6f-465a-a428-6df28e40b555
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 822dfbc1-3584-4509-a35c-1d68e5f84509
docset: aem65
translation-type: ht
source-git-commit: 66c741bb73bd5deb2bb5b06dd46f2e407d9c4b7e

---


# コンテンツ同期からスマート同期への移行 {#transitioning-from-contentsync-to-smartsync}

この節では、スマート同期機能の概要と、スマート同期でサーバー負荷／ストレージとネットワークトラフィックを最小限に抑えてコストを削減する方法について説明します。

## 概要 {#overview}

スマート同期は、AEM Screens で使用される最新のメカニズムです。これは、オフラインチャネルのキャッシングとプレイヤーへの配信に現在使用されている方法の代わりになります。

サーバー側とクライアント側の両方で実行されます。

**サーバー側**：

* チャネルのコンテンツ（アセットなど）は、*/var/contentsync* にキャッシュされます。
* キャッシュは、ディスプレイに使用可能なコンテンツを記述するマニフェストを通じてプレーヤーに公開されます。

**クライアント側**：

* プレーヤーは、上記で生成されたマニフェストに基づいてコンテンツを更新します。

### スマート同期を使用するメリット {#benefits-of-using-smartsync}

スマート同期機能は、AEM Screens プロジェクトに多くのメリットをもたらします。例えば、以下が可能になります。

* ネットワークトラフィックとサーバー側に必要なストレージが大幅に削減されます。
* アセットが見つからないか変更された場合にのみ、プレーヤーがアセットをダウンロードします。
* サーバー側およびクライアント側のストレージが最適化されます。

>[!NOTE]
>
>AEM Screens プロジェクトにはスマート同期を使用することを強くお勧めします。

## コンテンツ同期からスマート同期への移行 {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>AEM 6.3 機能パック 5 や AEM 6.4 機能パック 3 を既にインストールしてある場合は、アセットのスマート同期を有効にして、ディスク領域の使用量を削減することができます。スマート同期を有効にするには、以下の手順に従ってコンテンツ同期からスマート同期に移行し、スマート同期を有効にします。
>
>スマート同期は、AEM 6.4.3 機能パック 3 に対応するサーバーの場合に、Screens Player で使用できます。
>
>最新のプレーヤーをダウンロードするには、[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/)を参照してください。各プラットフォームに最低限必要なプレーヤーバージョンを次の表に示します。

| **プラットフォーム** | **サポートされているプレーヤーの最小バージョン** |
|---|---|
| Android | 3.3.72 |
| Chrome OS | 1.0.136 |
| Windows | 1.0.136 |

コンテンツ同期からスマート同期に移行するには、以下の手順に従います。

1. コンテンツ同期からスマート同期に移行する場合は、スマート同期を有効にする前にコンテンツ同期キャッシュをクリアする必要があります。

   リンク ***https://localhost:4502/libs/cq/contentsync/content/console.html*** を使用してインスタンスからコンテンツ同期コンソールに移動し、「**キャッシュをクリア**」をクリックします（下図を参照）。

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >スマート同期の使用を開始する前に、コンテンツキャッシュをすべてクリアする必要があります。

1. AEM インスタンスでハンマーアイコン／**操作**／**Web コンソール**&#x200B;をクリックして、「**Adobe Experience Manager Web コンソール設定**」に移動します。

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. 「Adobe Experience Manager Web コンソール設定」が開きます。「*offlinecontentservices*」を検索します。

   「**Screens Offline Content Service**」プロパティを検索するには、**Command + F** キー（**Mac**）または **Ctrl + F** キー（**Windows**）を押します。

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. 「**保存**」をクリックして、「**Screens Offline コンテンツサービス**」プロパティを有効にします。こうして、AEM Screens でスマート同期を使用します。
1. スマート同期を有効にしたら、プロジェクトに移動し、*（アクションバーの）*「**オフラインコンテンツを更新**」をクリックする必要があります（下図を参照）。

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)