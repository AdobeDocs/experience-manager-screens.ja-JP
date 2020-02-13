---
title: データ・トリガーをパブリッシュ・サーバに複製
seo-title: データ・トリガーをパブリッシュ・サーバに複製
description: データトリガーをパブリッシュサーバに複製します。
seo-description: データトリガーをパブリッシュサーバに複製します。
translation-type: tm+mt
source-git-commit: 47e0204ea734a1348385ddd3c7108038c88d1933

---


# データトリガーのパブリッシュサーバーへの複製 {#replicating-data-triggers}

ContextHubおよびAEM Targeting engineを使用して、作成者/発行設定でデータトリガーに基づいてコンテンツをカスタマイズする場合、すべてのContextHubおよびパーソナライゼーション関連設定が、公開時にチャネルに自動的に複製されません。

このページでは、これらの設定を個別に発行するために必要なマニュアルの手順を説明します。

これは基本的に、手動での投稿に関するものです。

1. ContextHubストアモジュールとUIモジュールの設定
1. パーソナライゼーションオーディエンス
1. 個人設定アクティビティ

## データトリガーをパブリッシュサーバーに複製する手順 {#replicating-data-triggers-publish}

次の手順に従って、公開サーバにデータトリガーを複製します。

### 手順1:ContextHub設定の複製 {#replicating-contexthub-configurations}

1. ツール/デプロイ **メント** /配布 **/発行エージェ********** ントに移動し、発行エージェントをクリックして設定を指定します。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers1.png)

   >[!N注]
   >または、リンクを使用して [画面に直接](http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish) 、接続を設定およびテストすることもできます。

1. 次の図に **示すように、アクションバーの「接続をテスト** 」をクリックして、発行インスタンスとの作成者の通信を検証します。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!N注]
   >テストが失敗した場合は、作成者インスタンスと発行インスタンス間の複製エージェントの設定を修正する必要があります。 詳細は、「Troubleshooting Test Connection [](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) （テスト接続のトラブルシューティング）」を参照してください。

1. 上の画 **面で「編集** 」をクリックし、「インポーターエンドポイント」フィールドのエンドポイントURLが **** Distribution agentのパブリッシュサーバーURLも指していることを確認します。
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers3.png)

1. [ **Distribution** Agent **]画面ツリーで[Add]を選択し、プロジェクトの設定パス(つまり、**`/conf/screens/settings/cloudsettings/configuration)`)を選択します。

1. Click **Submit**

### オーディエンスの複製 {#replicating-audiences}

1. ツール/パーソナライゼーション **/オーディエ** ンス **に移動するには** 、リンクを ****[](http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html) 使用して直接移動します。

1. プロジェクトフォルダ、つまり、をドリルダウンしま `/conf/screens/`す。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers5.png)

1. ユーザーインターフェイスからすべてのオーディエンスとセグメントを選択します。

1. アクショ **ンバーで[パブリケーションの管理** ]をクリックします。

1. 「次へ」 **と「公開** 」をクリ **ックします**。

### アクティビティの複製 {#replicating-activities}

1. ツール/パーソナライゼーショ **ン** /アクテ **ィビティ** に移動します **。リンクを使**[](http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html) 用して直接移動します。

1. プロジェクトフォルダ、つまり、をドリルダウンしま `/content/campaigns/screens/…`す。

1. ユーザーインターフェイスからすべてのアクティビティを選択します。

1. アクショ **ンバーで[パブリケーションの管理** ]をクリックします。

1. 「次へ」 **と「公開** 」をクリ **ックします**。

   > [!N注]
   >ContextHubの設定とオーディエンスの複製は、プロジェクトのセットアップ中に行われ、アクティビティの複製が行われます。また、チャネル内でターゲット設定が変更されるたびに必要になります。

#### 結果 {#result}

複製が成功した場合は、発行インスタンスで次の構造を表示する必要があります（または、プロジェクトで同様の構造を表示する必要があります）。

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`

## テスト接続のトラブルシューティング {#troubleshoot-test}

ContextHub設定の複製中にテスト接続が失敗した場合は、次の節に従って問題のトラブルシューティングを行ってください。

1. 「インポーター **エンドポイント** 」フィールドに移動し、エンドポイントURLがDistribution agentのパブリッシュサーバーURLを指していることを確認します。

1. デフォルトの資格情報を使用しない場合は、別の管理者パスワードを使用して配布エージェントを設定する必要があります。
その場合は、次の手順に従います。

   1. ツール/操作 **/Webコンソール**に移** 動して `http://localhost:4502/system/console/configMgr`Adobe Experience Manager Web Console画面を開きます ****。

   1. Search for **Apache Sling Distribution Transport Credentials - User Credentials based DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 名前、ユーザー名 **、パスワ**&#x200B;ード **(例：slingTransportSecretProvider** )を入力して ******、設定を作成します。.
   1. 「**保存**」をクリックします。

   1. を使用して、配布エージェントの名前を検索しま `Cmd +F`す。

   1. 配布エージェントのosgi設定をクリックして開きます。

   1. osgi設定でTransport Secret Providerを探し、それを更新します `"(name=slingTransportSecretProvider)"`。

   1. 「保存」 **をクリックし** 、テスト接続を実行します。

