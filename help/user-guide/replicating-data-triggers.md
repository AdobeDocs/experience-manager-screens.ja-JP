---
title: データトリガーの公開サーバーへのレプリケーション
description: AEM Screens の公開サーバーにデータトリガーをレプリケートする方法を説明します。
feature: Administering Screens, Data Trigger
role: Developer
level: Intermediate
exl-id: 6f90b864-eaa0-4b74-a47e-b0967a550552
source-git-commit: cdff56f0807f6d5fea4a4b1d545aecb1e80245bb
workflow-type: ht
source-wordcount: '523'
ht-degree: 100%

---

# データトリガーの公開サーバーへのレプリケーション {#replicating-data-triggers}

ContextHub と AEM ターゲティングエンジンを使用して、オーサーとパブリッシュのセットアップ時のデータトリガーに基づいてコンテンツをカスタマイズする場合、ContextHub とパーソナライズ機能に関連するすべての設定は、公開時にチャネルへ自動的にレプリケーションされません。

このページでは、これらの設定を個別に公開するために必要な手動による手順を説明します。

このプロセスでは基本的に、次の操作を手動で公開することになります。

1. ContextHub ストアと UI モジュールの設定
1. オーディエンスのパーソナライズ
1. アクティビティのパーソナライズ

## データトリガーの公開サーバーへのレプリケーション手順 {#replicating-data-triggers-publish}

次の手順に従って、データトリガーをパブリッシュサーバーにレプリケートします。

### 手順 1：ContextHub 設定のレプリケーション {#replicating-contexthub-configurations}

1. **ツール**／**デプロイメント**／**配布**／**公開エージェント**&#x200B;に移動し、設定を行う公開エージェントをクリックします。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!NOTE]
   >
   >または、`http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` を使用して画面に直接移動し、接続の設定とテストを行うこともできます。

1. 次の図に示すように、アクションバーの「**接続をテスト**」をクリックして、オーサーとパブリッシュインスタンスの通信を検証します。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!NOTE]
   >
   >テストが失敗した場合は、オーサーインスタンスとパブリッシュインスタンス間のレプリケーションエージェントの設定を修正してください。詳しくは、[テスト接続のトラブルシューティング](/help/user-guide/replicating-data-triggers.md#troubleshoot-test)を参照してください。

1. **配布エージェント**&#x200B;画面のツリーから「**追加**」をクリックし、プロジェクトの設定パスをクリックします（例：`/conf/screens/settings/cloudsettings/configuration`）。

1. 「**送信**」をクリックします。

### オーディエンスのレプリケーション {#replicating-audiences}

1. AEM インスタンス／**パーソナライズ機能**／**オーディエンス**&#x200B;に移動するか、`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` を使用して直接移動します。

1. プロジェクトフォルダーにドリルダウンします（例：`/conf/screens/`）。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers10.png)

1. ユーザーインターフェイスからすべてのオーディエンスとセグメントをクリックします。

1. アクションバーの&#x200B;**公開の管理**&#x200B;をクリックします。

1. 「**次へ**」と「**公開する**」をクリックします。

### アクティビティのレプリケーション {#replicating-activities}

1. AEM インスタンス／**パーソナライズ機能**／**アクティビティ**&#x200B;に移動するか、`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` を使用して直接移動します。

1. プロジェクトフォルダー（`/content/campaigns/screens/…`）にドリルダウンします。

1. ユーザーインターフェイスからすべてのアクティビティをクリックします。

1. アクションバーの&#x200B;**公開の管理**&#x200B;をクリックします。

1. 「**次へ**」と「**公開する**」をクリックします。

>[!IMPORTANT]
>
>ContextHub 設定とオーディエンスは、アクティビティのレプリケーションと同時に、プロジェクトの設定中にレプリケーションされ、またレプリケーションはチャネル内でターゲット設定が変更されるたびに必要になります。

#### 結果 {#result}

レプリケーションが成功した場合は、パブリッシュインスタンスで次の構造が表示されます（または、プロジェクトに応じて同様の構造が表示されます）。

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## テスト接続のトラブルシューティング {#troubleshoot-test}

ContextHub 設定をレプリケーション中にテスト接続が失敗した場合は、次の手順に従って問題のトラブルシューティングを行ってください。

1. **ツール**／**デプロイメント**／**配布**／**パブリッシュエージェント**&#x200B;に移動します。

1. アクションバーで「**編集**」をクリックし、「**インポーターエンドポイント**」フィールドのエンドポイント URL も配布エージェントの公開サーバー URL を指していることを確認します。
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers9.png)

1. デフォルトの管理者認証情報を使用していない場合は、別のユーザー名とパスワードを使用して配布エージェントを設定する必要があります。

   次の手順に従います。

   1. ツール／**操作**／**web コンソール** `http://localhost:4502/system/console/configMgr` に移動すると、**Adobe Experience Manager web コンソール画面**&#x200B;を開くことができます。
   1. **Apache Sling Distribution トランスポート認証情報 - ユーザ認証情報に基づく DistributionTransportSecretProvider** を探します。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. **名前**、**ユーザー名**、**パスワード**&#x200B;を入力して、設定を作成します（例：*slingTransportSecretProvider*）。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. 「**保存**」をクリックします。
   1. 設定を開くには、`Cmd +F` を使用して **Apache Sling 配布エージェント - フォワードエージェントファクトリー**&#x200B;を検索し、それから&#x200B;**トランスポートシークレットプロバイダー**&#x200B;を検索します。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. `(name=default)` を `(name=slingTransportSecretProvider)` に更新します。
   1. 「**保存**」をクリックし、AEM インスタンスの&#x200B;**配布エージェント**&#x200B;画面から再びテスト接続を実行します。
