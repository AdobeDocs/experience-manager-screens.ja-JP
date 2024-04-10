---
title: パブリッシュサーバーにデータトリガーをレプリケート
description: AEM Screens用にデータトリガーをパブリッシュサーバーにレプリケートする方法を説明します。
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 45%

---

# データトリガーのパブリッシュサーバーへのレプリケーション {#replicating-data-triggers}

ContextHub と AEM ターゲティングエンジンを使用して、オーサーとパブリッシュのセットアップ時のデータトリガーに基づいてコンテンツをカスタマイズする場合、ContextHub とパーソナライズ機能に関連するすべての設定は、公開時にチャネルへ自動的にレプリケーションされません。

このページでは、これらの設定を個別に公開するために必要な手動の手順を説明します。

これは基本的に、手動公開の次になります。

1. ContextHub ストアと UI モジュールの設定
1. オーディエンスのパーソナライズ
1. アクティビティのパーソナライズ

## データトリガーをパブリッシュサーバーにレプリケートする手順 {#replicating-data-triggers-publish}

次の手順に従って、データトリガーをパブリッシュサーバーにレプリケートします。

### 手順 1:ContextHub 設定のレプリケート {#replicating-contexthub-configurations}

1. に移動します。 **ツール** > **デプロイメント** > **配分** > **公開エージェント** パブリッシングエージェントをクリックして、設定を指定します。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >または、次の URL を使用して画面に直接移動し、接続の設定とテストをおこなうこともできます。`http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish`

1. クリック **接続をテスト** アクションバーで、オーサーインスタンスとパブリッシュインスタンスとの通信を検証できます（下図を参照）。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >テストが失敗した場合は、オーサーインスタンスとパブリッシュインスタンスの間のレプリケーションエージェント設定を修正します。 参照： [接続テストのトラブルシューティング](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) を参照してください。

1. **配布エージェント**&#x200B;画面のツリーから「**追加**」を選択し、プロジェクトの設定パスを選択します（例：`/conf/screens/settings/cloudsettings/configuration`）。

1. 「**送信**」をクリックします。

### オーディエンスのレプリケート {#replicating-audiences}

1. AEM インスタンスに移動します。 **Personalization** > **オーディエンス** または使用 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` に移動し、直接移動します。

1. プロジェクトフォルダーにドリルダウンします（例：`/conf/screens/`）。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. ユーザーインターフェイスからすべてのオーディエンスとセグメントを選択します。

1. アクションバーの&#x200B;**公開の管理**&#x200B;をクリックします。

1. 「**次へ**」と「**公開する**」をクリックします。

### アクティビティのレプリケート  {#replicating-activities}

1. AEM インスタンスに移動します。 **Personalization** > **アクティビティ** または使用 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` に移動し、直接移動します。

1. プロジェクトフォルダ（`/content/campaigns/screens/…`）にドリルダウンします。

1. ユーザーインターフェイスからすべてのアクティビティを選択します。

1. アクションバーの&#x200B;**公開の管理**&#x200B;をクリックします。

1. 「**次へ**」と「**公開する**」をクリックします。

>[!IMPORTANT]
>
>ContextHub 設定およびオーディエンスのレプリケーションは、アクティビティのレプリケーション時のプロジェクト設定で行います。これは、チャネル内でターゲティングが変更されるたびに必要になります。

#### 結果 {#result}

レプリケーションが成功した場合は、パブリッシュインスタンスで次の構造が表示されます（または、プロジェクトに応じて同様の構造が表示されます）。

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## 接続テストのトラブルシューティング {#troubleshoot-test}

ContextHub 設定をレプリケーション中にテスト接続が失敗した場合は、次の手順に従って問題のトラブルシューティングをおこなってください。

1. ツール／**デプロイメント**／**配布版**／**発行エージェント**&#x200B;に移動します。

1. クリック **編集** アクションバーから、エンドポイント URL がであることを確認します。 **インポーターエンドポイント** フィールドは、配布エージェントの公開サーバー URL も指しています。
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. デフォルトの管理者資格情報を使用していない場合は、別のユーザー名とパスワードを使用して配布エージェントを設定する必要があります。

   次の手順に従います。

   1. ツール /に移動します。 **運用** > **Web コンソール** `http://localhost:4502/system/console/configMgr`次のアイコンを開きます **Adobe Experience Manager web コンソール画面**.
   1. **Apache Sling Distribution トランスポート認証情報 - ユーザ認証情報に基づく DistributionTransportSecretProvider** を探します。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 入力による設定の作成 **名前**, **ユーザー名**、および **password**、例： *slingTransportSecretProvider*.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. 「**保存**」をクリックします。
   1. 使用方法 `Cmd +F` を検索します **Apache Sling Distribution Agent - Forward Agents Factory** 設定を開き、を検索するには **トランスポート秘密鍵プロバイダー**.

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. `(name=default)` を `(name=slingTransportSecretProvider)` に更新します。
   1. 「**保存**」をクリックし、AEM インスタンスの&#x200B;**配布エージェント**&#x200B;画面から再びテスト接続を実行します。
