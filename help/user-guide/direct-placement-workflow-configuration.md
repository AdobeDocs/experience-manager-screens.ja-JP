---
title: ダイレクト配置ワークフロー設定
seo-title: Direct Placement Workflow Configuration
description: このページでは、ダイレクト配置ワークフロー設定について説明します。
seo-description: This page highlights Direct Placement Workflow Configuration.
source-git-commit: d1adadbab2cb13626dd8ce70deacced9f55aa4c9
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 87%

---


# ダイレクト配置ワークフロー設定 {#direct-placement-workflow}

このページでは、事前定義された AEM Screens チャネルにプログラムでアセットを挿入できるアセットワークフローの設定について説明します。

ここでは、以下のトピックについて説明します。

* 概要
* ダイレクト配置ワークフローの設定

## 概要 {#overview}

ダイレクト配置ワークフローの設定は、AEM Screens プロジェクトチャネルをアセット内の特定のフォルダーにマップし、そのフォルダー内の任意のアセットを配置できるようにします。公開を完了するには、オフラインで一括更新を実行することをお勧めします。

また、コンテンツ作成者として、「**オフラインコンテンツを更新**」をクリックすることもできます。

>[!NOTE]
>
>オフラインで一括更新を使用する方法については、[Content Update As a Service](/help/user-guide/content-update-as-a-service.md) を参照してください。

## ダイレクト配置ワークフローの設定 {#configuring-workflow}

>[!IMPORTANT]
>
>設定を開始する前に、[デモパッケージ](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)をインストールする必要があります。パッケージをインストールすると、AEMインスタンス/ツール（アイコン） /から、パッケージを表示してアクセスできるようになります。 **ワークフロー** > **ワークフローモデル**.

ダイレクト配置ワークフローを設定するには、次の手順を実行します。

1. AEM インスタンスから AEM Screens に移動し、**アセットワークフロー**&#x200B;という名前の Screens プロジェクトを作成します。

1. **チャネル**&#x200B;フォルダーの下に&#x200B;**ワークフロー - アセット**&#x200B;というチャネルを作成します。

