---
title: コマンド同期の使用
description: AEM Screens でコマンド同期を使用する方法について詳しく説明します。
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3314e0b5-0001-4bce-8ec6-5a6ffbb20f7b
TQID: https://experienceleague.adobe.com/61R-NNkhkgGx2S0KOeteDn674PiOpX5k4YOVKBmQZIs
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 743
ht-degree: 85%

---

# コマンド同期 {#command-sync}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド &#x200B;](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

以下では、コマンド同期の使用方法について説明します。 コマンド同期を使用すると、異なるプレーヤー間で再生を同期させることができます。 プレーヤーごとに異なるコンテンツを再生できますが、各アセットの再生時間は同じにする必要があります。

>[!IMPORTANT]
>
>この機能は、埋め込みシーケンス、動的埋め込みシーケンス、アプリケーションチャネル、トランジションをサポートしていません。

## 概要 {#overview}

デジタルサイネージソリューションでは、ビデオウォールと同期再生をサポートする必要があります。 このシナリオは、新年のカウントダウンや大きなビデオを分割して複数の画面で再生するようなシナリオをサポートしようとする場合に当てはまります。 このようなシナリオでは、コマンド同期が役立ちます。

コマンド同期を使用するには、1 つのプレーヤーが&#x200B;*プライマリ*&#x200B;として機能し、コマンドを送信します。他のすべてのプレーヤーは&#x200B;*クライアント*&#x200B;として機能し、コマンドを受信したときにコンテンツを再生します。

*プライマリ*&#x200B;は、コンテンツ項目の再生を開始しようとするときに、登録済みのすべてのクライアントにコマンドを送信します。 再生する項目のインデックスや再生する要素の外部 HTML、あるいはその両方が、このアクションのペイロードになります。

## コマンド同期の実装 {#using-command-sync}

次の節では、AEM Screens プロジェクトでコマンド同期を使用する方法について説明します。

>[!NOTE]
>
>同期再生をおこなうには、すべてのハードウェアデバイスのハードウェア仕様が同じ（できればオペレーティングシステムも同じ）である必要があります。 異なるハードウェアとオペレーティングシステム間での同期はお勧めしません。

### プロジェクトのセットアップ {#setting-up}

コマンド同期機能を使用する前に、プロジェクトと、プロジェクト用にコンテンツが設定されたチャネルがあることを確認します。

1. 次の例は、**CommandSyncDemo** という名前のデモプロジェクトと、シーケンスチャネル **ChannelLobby** を示しています。

   ![image1](assets/command-sync/command-sync1-1.png)

   >[!NOTE]
   >
   >チャネルを作成する方法、またはチャネルにコンテンツを追加する方法については、[チャネルの作成と管理](/help/user-guide/managing-channels.md)を参照してください。

   下の図に示すように、チャネルには次のコンテンツが含まれます。

   ![image1](assets/command-sync/command-sync2-1.png)

1. 次の図に示すように、**ロビー**&#x200B;というロケーションを作成し、**Locations** フォルダーに **LobbyDisplay** というタイトルのディスプレイを作成します。
   ![image1](assets/command-sync/command-sync3-1.png)

1. チャネル **ChannelLobby**&#x200B;を&#x200B;**LobbyDisplay**&#x200B;に割り当てます。ディスプレイ ダッシュボードから、ディスプレイに割り当てられたチャネルを表示できるようになりました。
   ![image1](assets/command-sync/command-sync4-1.png)

   >[!NOTE]
   >
   >ディスプレイにチャネルを割り当てる方法については、[ディスプレイの作成と管理](/help/user-guide/managing-displays.md)を参照してください

1. **デバイス**&#x200B;フォルダーに移動します。
1. アクションバーの「**デバイスマネージャー**」をクリックします。

   ![image1](assets/command-sync5.png)

   >[!NOTE]
   >
   >デバイスの登録方法については、[デバイス登録](/help/user-guide/device-registration.md)を参照してください。

1. デモ用に、この例では、Chrome デバイスとWindows Playerを2つの別々のデバイスとして示します。両方のデバイスが同じディスプレイを指しています。
   ![image1](assets/command-sync6.png)

### チャネル設定の更新

1. **ChannelLobby** に移動します。
1. アクションバーの「**編集**」をクリックします。
1. チャネル全体をクリックします（下図を参照）。
   ![image1](assets/command-sync/command-sync7-1.png)

1. レンチアイコンをクリックします。
   ![image1](assets/command-sync/command-sync8-1.png)

1. **ページ**&#x200B;ダイアログボックスの「**戦略**」フィールドに&#x200B;*同期済み*キーワードを入力します。
   ![image1](assets/command-sync/command-sync9-1.png)


### プライマリの設定 {#setting-up-primary}

1. **CommandSyncDemo** > **Locations** > **Lobby** > **LobbyDisplay**&#x200B;からディスプレイダッシュボードに移動します。次に、アクションバーから「**ダッシュボード**」をクリックします。
**DEVICES** パネルの2つのデバイス（ChromeとWindows Player）に注意してください。次を参照してください。
   ![image1](assets/command-sync/command-sync10-1.png)

1. **デバイス**&#x200B;パネルから、プライマリとして設定するデバイスをクリックします。 次の例は、Chrome デバイスをプライマリデバイスとして設定する方法を示しています。 「**プライマリデバイスとして設定**」をクリックします。

   ![image1](assets/command-sync/command-sync11-1.png)

1. **プライマリデバイスとして設定**&#x200B;のフィールドに IP アドレスを入力し、「**保存**」をクリックします。

   ![image1](assets/command-sync/command-sync12-1.png)

>[!NOTE]
>
>複数のデバイスをプライマリデバイスとして設定できます。

### プライマリとの同期 {#sync-up-primary}

1. Chrome デバイスをプライマリとして設定した後、他のデバイス（この場合はWindows Player）をプライマリと同期させます。
**デバイス** パネルから別のデバイス（この場合はWindows Player）をクリックし、**プライマリデバイス**&#x200B;に同期をクリックします。

   ![image1](assets/command-sync/command-sync13-1.png)

1. リストからデバイスをクリックし、「**保存**」をクリックします。

   >[!NOTE]
   >
   > **プライマリデバイスに同期**&#x200B;ダイアログボックスに、プライマリデバイスのリストが表示されます。 必要な項目を選択します。

1. デバイス（この例では Windows プレーヤー）がプライマリ（この例では Chrome プレーヤー）に同期されると、同期されたデバイスを&#x200B;**デバイス**&#x200B;パネルに表示できます。

   ![image1](assets/command-sync/command-sync14-1.png)

### プライマリとの同期解除 {#desync-up-primary}

1 つ以上のデバイスをプライマリに同期した後は、そのデバイスから同期の割り当てを解除できます。

>[!NOTE]
>
>プライマリデバイスの同期を解除すると、そのプライマリデバイスと関連付けられているすべてのクライアントデバイスのリンクも解除されます。

プライマリデバイスから同期を解除するには、次の手順に従います。

1. **デバイス**&#x200B;パネルに移動し、デバイスをクリックします。

1. 「**デバイスの同期を解除**」をクリックして、プライマリデバイスからクライアントの同期を解除します。

   ![image1](assets/command-sync/command-sync15-1.png)

1. 「**確認**」をクリックして、選択したデバイスの同期をプライマリから解除します。

   >[!NOTE]
   >
   > プライマリデバイスをクリックして同期解除オプションを使用すると、プライマリに接続されているすべてのデバイスの同期がワンステップで解除されます。
