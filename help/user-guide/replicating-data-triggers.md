---
title: データ・トリガーをパブリッシュ・サーバに複製
seo-title: データ・トリガーをパブリッシュ・サーバに複製
description: データトリガーをパブリッシュサーバに複製します。
seo-description: データトリガーをパブリッシュサーバに複製します。
translation-type: tm+mt
source-git-commit: a8ded0c15e0e3cbaf0999da796789991b20d24cb

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

### ContextHub設定の複製 {#replicating-contexthub-configurations}

1. ツール/デプロ **イメント** /配布 **/発行エージェ** ントhttp://localhost:4502/libs/granite/distribution/content/distribution-agent.html?agentName=publishに ********&#x200B;移動します。
1. 「接続をテスト」ボタンをクリックして、作成者が発行インスタンスと正しく通信できることを検証します
1. テストが失敗した場合は、作成者と発行の間のレプリケーションエージェント設定を修正する必要があります
1. エンドポイントURLが、Distribution agentで公開サーバーURLも指していることを確認します
1. 編集/インポーターエンドポイント
1. 「分布」タブをクリックします
1. [ツリーの追加]ラジオボタン
1. パスブラウザーで、プロジェクトの設定パス(/conf/screens/settings/cloudsettings/configuration)
1. 「送信」をクリックします

### オーディエンスの複製 {#replicating-audiences}

1. ツール/パーソナライゼーション/オーディエンスhttp://localhost:4502/libs/cq/personalization/touch-ui/content/v2/audiences.htmlに移動します。
1. プロジェクトフォルダー(/conf/screens/)
1. UIですべてのオーディエンス/セグメントを選択
1. [パブリケーションの管理]をクリックします
1. 「次へ」をクリックします。
1. 「公開」をクリックします

### アクティビティの複製 {#replicating-activities}

1. ツール/パーソナライゼーション/アクティビティhttp://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.htmlに移動します。
1. プロジェクトフォルダー(/content/campaigns/screens/...)
1. UI内のすべてのアクティビティを選択
1. [パブリケーションの管理]をクリックします
1. 「次へ」をクリックします。
1. 「公開」をクリックします

> [!N注]
>ContextHubの設定とオーディエンスの複製は、プロジェクトのセットアップ中に行われ、アクティビティの複製が行われます。また、チャネル内でターゲット設定が変更されるたびに必要になります。

#### 結果 {#result}

複製が成功した場合は、発行インスタンスで次の構造を表示する必要があります（または、プロジェクトで同様の構造を表示する必要があります）。

`/conf/screens/settings/cloudsettings/configuration/…`
`/conf/screens/settings/wcm/segments/…`
`/content/campaigns/screens/…`