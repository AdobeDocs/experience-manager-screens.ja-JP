---
title: '直接配置ワークフローの設定 '
seo-title: 直接配置ワークフローの設定
description: このページでは、直接配置ワークフローの設定について説明します。
seo-description: このページでは、直接配置ワークフローの設定について説明します。
translation-type: tm+mt
source-git-commit: 19baf90409eab4c72fb38e992c272338b0098d89

---


# 直接配置ワークフローの設定 {#direct-placement-workflow}

このページでは、事前定義されたAEM Screensワークフローにプログラムによってアセットを挿入できるアセットワークフローの設定について説明します。チャネル

ここでは、以下のトピックについて説明します。

* 概要
* 直接配置ワークフローの設定

## 概要 {#overview}

Direct Placement Workflow Configurationは、AEM Screensプロジェクトチャネルをアセット内の特定のフォルダにマップし、そのフォルダ内の任意のアセットを配置できるようにします。 パブリケーションを完了するには、オフラインでの一括更新をトリガーすることをお勧めします。

また、コンテンツ作成者は、「オフラインコンテンツを手動で更新」をク **リックすることもできま**&#x200B;す。

>[!NOTE]
> オフラインで一括更新を使用する方法については、「サービスとしてのコンテ [ンツの更新」を参照してくださ](/help/user-guide/content-update-as-a-service.md)い。

## 直接配置ワークフローの設定 {#configuring-workflow}

>[!IMPORTANT]
> 設定を開始する前に、デモパッケージをインストールする [必要がありま](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)す。 パッケージをインストールすると、AEMインスタンスの表示/ツール（アイコン）/ワークフロー **/ワークフローモデルからアクセ** スできます ****。

次の手順に従って、直接配置ワークフローを設定します。

1. AEMインスタンスからAEM Screensに移動し、「アセットワークフロー」という名前の画面プロジェクト **を作成します**。

1. Create a channel titled as **Workflow-Assets** under **Channels** folder.

1. 
