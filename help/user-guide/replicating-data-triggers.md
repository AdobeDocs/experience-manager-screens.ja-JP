---
title: データトリガーのパブリッシュサーバーへのレプリケーション
seo-title: データトリガーのパブリッシュサーバーへのレプリケーション
description: データトリガーのパブリッシュサーバーへのレプリケーション。
seo-description: データトリガーのパブリッシュサーバーへのレプリケーション。
translation-type: tm+mt
source-git-commit: 081db31efda17ac12cdc88f79ed2f4e1fbfc7edf
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 100%

---


# データトリガーのパブリッシュサーバーへのレプリケーション {#replicating-data-triggers}

ContextHub と AEM ターゲティングエンジンを使用して、オーサーとパブリッシュのセットアップ時のデータトリガーに基づいてコンテンツをカスタマイズする場合、ContextHub とパーソナライズ機能に関連するすべての設定は、公開時にチャネルへ自動的にレプリケーションされません。

このページでは、これらの設定を個別に公開するために必要な手順を説明します。

これは基本的に、手動で公開をおこなうものです。

1. ContextHub ストアと UI モジュールの設定
1. オーディエンスのパーソナライズ
1. アクティビティのパーソナライズ

## データトリガーのパブリッシュサーバーへのレプリケーション手順 {#replicating-data-triggers-publish}

次の手順に従って、データトリガーをパブリッシュサーバにレプリケーションします。

### 手順 1：ContextHub 設定のレプリケーション {#replicating-contexthub-configurations}

1. **ツール**／**デプロイメント**／**配布**／**発行エージェント**&#x200B;に移動し、設定する発行エージェントをクリックします。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >または、次の URL を使用して画面に直接移動し、接続の設定とテストをおこなうこともできます。`http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish`

1. 次の図に示すように、アクションバーの&#x200B;**接続のテスト**&#x200B;をクリックして、オーサーとパブリッシュインスタンスの通信を検証します。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >テストが失敗した場合は、オーサーインスタンスとパブリッシュインスタンス間のレプリケーションエージェントの設定を修正する必要があります。詳細は、[テスト接続のトラブルシューティング](/help/user-guide/replicating-data-triggers.md#troubleshoot-test)を参照してください。

1. **配布エージェント**&#x200B;画面のツリーから「**追加**」を選択し、プロジェクトの設定パスを選択します（例：`/conf/screens/settings/cloudsettings/configuration`）。

1. 「**送信**」をクリックします。

### オーディエンスのレプリケーション {#replicating-audiences}

1. AEM インスタンス／**パーソナライズ機能**／**オーディエンス**&#x200B;に移動するか、次の URL を使用して直接移動します。`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html`

1. プロジェクトフォルダーにドリルダウンします（例：`/conf/screens/`）。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. ユーザーインターフェイスからすべてのオーディエンスとセグメントを選択します。

1. アクションバーの&#x200B;**公開の管理**&#x200B;をクリックします。

1. 「**次へ**」と「**公開する**」をクリックします。

### アクティビティのレプリケーション {#replicating-activities}

1. AEM インスタンス／**パーソナライズ機能**／**アクティビティ**&#x200B;に移動するか、次の URL を使用して直接移動します。`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html`

1. プロジェクトフォルダ（`/content/campaigns/screens/…`）にドリルダウンします。

1. ユーザーインターフェイスからすべてのアクティビティを選択します。

1. アクションバーの&#x200B;**公開の管理**&#x200B;をクリックします。

1. 「**次へ**」と「**公開する**」をクリックします。

>[!IMPORTANT]
>
>ContextHub 設定とオーディエンスは、アクティビティのレプリケーションと同時に、プロジェクトのセットアップ中にレプリケーションされ、またレプリケーションはチャネル内でターゲット設定が変更されるたびに必要になります。

#### 結果 {#result}

レプリケーションが成功した場合は、パブリッシュインスタンスで次の構造が表示されます（または、プロジェクトに応じて同様の構造が表示されます）。

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## テスト接続のトラブルシューティング {#troubleshoot-test}

ContextHub 設定をレプリケーション中にテスト接続が失敗した場合は、次の手順に従って問題のトラブルシューティングをおこなってください。

1. ツール／**デプロイメント**／**配布**／**発行エージェント**&#x200B;に移動します。

1. アクションバーで&#x200B;**編集**&#x200B;をクリックし、「**インポーターエンドポイント**」フィールドのエンドポイント URL も配布エージェントのパブリッシュサーバー URL を指していることを確認します。
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. デフォルトの管理者認証情報を使用しない場合は、別のユーザー名とパスワードを使用して配布エージェントを設定する必要があります。

   その場合は、次の手順に従います。

   1. ツール／**操作**／**Web コンソール** `http://localhost:4502/system/console/configMgr` に移動して、**Adobe Experience Manager Web コンソール画面**&#x200B;を開きます。
   1. **Apache Sling Distribution トランスポート認証情報 - ユーザ認証情報に基づく DistributionTransportSecretProvider** を探します。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. **名前**、**ユーザー名**、**パスワード**&#x200B;を入力して、設定を作成します（例：*slingTransportSecretProvider*）。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. 「**保存**」をクリックします。
   1. 設定を開くには、`Cmd +F` を使用して **Apache Sling Distribution Agent - Forward Agents Factory** を検索し、それから **Transport Secret Provider** を検索します。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. `(name=default)` を `(name=slingTransportSecretProvider)` に更新します。
   1. 「**保存**」をクリックし、AEM インスタンスの&#x200B;**配布エージェント**&#x200B;画面から再びテスト接続を実行します。
