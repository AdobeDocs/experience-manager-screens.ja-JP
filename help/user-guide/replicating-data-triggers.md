---
title: データ・トリガーをパブリッシュ・サーバに複製
seo-title: データ・トリガーをパブリッシュ・サーバに複製
description: データトリガーをパブリッシュサーバに複製します。
seo-description: データトリガーをパブリッシュサーバに複製します。
translation-type: tm+mt
source-git-commit: ae6ec7dd240b1d6f6adb46359e702eefc167b7b8

---


# データトリガーの公開サーバへの複製 {#replicating-data-triggers}

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
   >または、を使用して画面に直 `http://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publish` 接移動し、接続を設定およびテストすることもできます。

1. 次の図に **示すように、アクションバーの「接続をテスト** 」をクリックして、発行インスタンスとの作成者の通信を検証します。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers2.png)

   >[!N注]
   >テストが失敗した場合は、作成者インスタンスと発行インスタンス間の複製エージェントの設定を修正する必要があります。 詳細は、「Troubleshooting Test Connection [](/help/user-guide/replicating-data-triggers.md#troubleshoot-test) （テスト接続のトラブルシューティング）」を参照してください。

1. [ **Distribution** Agent **]画面ツリーで[Add]を選択し、プロジェクトの設定パスを選択します(例：**`/conf/screens/settings/cloudsettings/configuration)`)。

1. Click **Submit**

### オーディエンスの複製 {#replicating-audiences}

1. AEMインスタンス/パーソナライゼーション **/オーディエ** ンス **に移動するか、を使用**`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.html` して直接移動します。

1. 例えば、プロジェクトフォルダーにドリルダウンしま `/conf/screens/`す。

   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers5.png)

1. ユーザーインターフェイスからすべてのオーディエンスとセグメントを選択します。

1. アクショ **ンバーで[パブリケーションの管理** ]をクリックします。

1. 「次へ」 **と「公開** 」をクリ **ックします**。

### アクティビティの複製 {#replicating-activities}

1. AEMインスタンス/パーソナライゼーション/ア **クティビティ** (Personalization/ **Activities** )に移動するか、を使用 `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html` して直接移動します。

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

1. ツール/デプロイメント/配 **布** /発行エ **ージェ** ントに移動します ****。

1. アクシ **ョンバーで「編集** 」をクリックし、「インポーターエンドポイント **** 」フィールドのエンドポイントURLが、Distribution agentのパブリッシュサーバーURLも指していることを確認します。
   ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers3.png)

1. デフォルトの管理者資格情報を使用しない場合は、別の管理者パスワードを使用して配布エージェントを設定する必要があります。
その場合は、次の手順に従います。

   1. ツール/操作 **/** Web Console **** に移動し `http://localhost:4502/system/console/configMgr`て、Adobe Experience Manager Web Console画面を開きます ****。

   1. Search for **Apache Sling Distribution Transport Credentials - User Credentials based DistributionTransportSecretProvider**

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers6.png)

   1. 名前、ユーザー名 **、パスワ**&#x200B;ード **(例：slingTransportSecretProvider** )を入力して ******、設定を作成します。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers7.png)

   1. 「**保存**」をクリックします。

   1. 設定を `Cmd +F` 開き、 **Transport Secret Providerを検索するには、Apache Sling Distribution Agent - Forward Agents Factory** を使用します ****。

      ![image1](/help/user-guide/assets/replicating-triggers/replicating-triggers8.png)

   1. をに更新し `(name=default)` ます `(name=slingTransportSecretProvider)`。

   1. 「 **Save** 」をクリックし、AEMインスタンスから **** Distribution agent画面から再びテスト接続を実行します。

