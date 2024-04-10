---
title: ダイレクト配置ワークフロー設定
description: このページでは、ダイレクト配置ワークフロー設定について説明します。
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 53%

---


# ダイレクト配置ワークフロー設定 {#direct-placement-workflow}

ここでは、事前定義済みのAEM Screens チャネルにアセットをプログラムで挿入できるアセットワークフローの設定について説明します。

ここでは、以下のトピックについて説明します。

* 概要
* ダイレクト配置ワークフローの設定

## 概要 {#overview}

ダイレクト配置ワークフローの設定は、AEM Screens プロジェクトチャネルをアセット内の特定のフォルダーにマップし、そのフォルダー内の任意のアセットを配置できるようにします。Adobeでは、オフライン一括アップデートをトリガーして公開を完了することをお勧めします。

また、コンテンツ作成者として、「**オフラインコンテンツを更新**」をクリックすることもできます。

>[!NOTE]
>
>オフラインで一括更新を使用する方法については、[Content Update As a Service](/help/user-guide/content-update-as-a-service.md) を参照してください。

## ダイレクト配置ワークフローの設定 {#configuring-workflow}

>[!IMPORTANT]
>
>設定を開始する前に、をインストールする必要があります `[Demo  Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)`. パッケージをインストールすると、AEM インスタンスでツール （アイコン）/パッケージを表示してアクセスできるようになります **ワークフロー** > **ワークフローモデル**.

ダイレクト配置ワークフローを設定するには、次の手順を実行します。

1. AEM インスタンスからAEM Screensに移動し、というタイトルの Screens プロジェクトを作成します。 **アセットワークフロー**.

1. **チャネル**&#x200B;フォルダーの下に&#x200B;**ワークフロー - アセット**&#x200B;というチャネルを作成します。

