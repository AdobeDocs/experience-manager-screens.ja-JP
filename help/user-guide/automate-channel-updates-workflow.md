---
title: ワークフローを使用したAEM Screensチャネルのアセットの更新の自動化
seo-title: ワークフローを使用したAEM Screensチャネルのアセットの更新の自動化
description: Adobe Experience Managerにアップロードされたアセットを自動的に処理し、アセットを画面チャネルに動的に割り当てるワークフローを作成する方法について説明します。 この例では、画像が特定のフォルダーに追加されると、動的な透かしを適用し、画像を画面チャネルーに割り当てるワークフローがトリガーされます。 この例で学んだ教訓は、様々な自動化シナリオに適用できます。
seo-description: Adobe Experience Managerにアップロードされたアセットを自動的に処理し、アセットを画面チャネルに動的に割り当てるワークフローを作成する方法について説明します。 この例では、画像が特定のフォルダーに追加されると、動的な透かしを適用し、画像を画面チャネルーに割り当てるワークフローがトリガーされます。 この例で学んだ教訓は、様々な自動化シナリオに適用できます。
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Screens の開発
role: Developer
level: Intermediate
source-git-commit: 8d1633dab9e70ea988516cf9ee4d1b0a780bc7e9
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 4%

---


# ワークフローを使用したAEM Screensチャネルのアセットの更新の自動化{#automate-channel-updates-workflow}

Adobe Experience Managerにアップロードされたアセットを自動的に処理し、アセットを画面チャネルに動的に割り当てるワークフローを作成する方法について説明します。 この例では、画像が特定のフォルダーに追加されると、動的テキストオーバーレイ（透かしプロセス）を適用し、画像をScreensチャネルーに割り当てるワークフローがトリガーされます。 この例で学んだ教訓は、様々な自動化シナリオに適用できます。

## 前提条件 {#prerequisites}

このチュートリアルを完了するには、以下が必要です。

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=ja)
1. [AEM Service Pack 8以降](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=ja)
1. [AEM 6.5 Screens FP7以降](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html)

## クイックセットアップ{#quick-setup}

次のビデオでは、新しいワークフローをAdobe Experience Managerに導入するサンプルコードパッケージのインストール方法を説明します。 この機能を使用すると、ユーザーは、画面チャネルーを指すようにAEM Assetsのフォルダーのプロパティを更新できます。 画像がそのフォルダに追加されるたびに、指定したscreensチャネルに追加されます。

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. コンパイル済みコードパッケージのダウンロード：**[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)**
1. AEM Package Managerを使用して、上記のパッケージをインストールします。

## ワークフローモデル {#workflow-model}

画像を追加するターゲット画面チャネルを取り込むために、カスタムフォルダーのメタデータスキーマが作成されました。 2つのワークフローモデルを使用して、アセットの処理を自動化します。 **DAM Update Asset**&#x200B;ワークフローが変更され、カスタムワークフロー&#x200B;**Screens Demo Asset Processing**&#x200B;が呼び出されます。これにより、ターゲット画面のチャネルを決定するために、アセットの含まれるフォルダーが調べられます。 **画面デモアセット処理**&#x200B;ワークフローも、画像に透かしを適用します。

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## カスタムワークフロープロセスの手順{#workflow-process-step}

Inspectでは、**Screens Demo Asset Processing**&#x200B;ワークフローの一部として使用される2つのカスタムワークフロープロセスステップが示されています。

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

`AssetProcessingCheck.java` は、ワークフローのペイロードに対してチェックを実行し、ペイロードがアセットであるかどうか、およびペイロードフォルダーが画面チャネルーを指すように設定されているかどうかを確認するカスタムワークフロープロセスです。要件が満たされた場合、プロセスステップは、`screen-channel`と`asset-path`の2つのプロパティをワークフローのメタデータに保持します。

`AddAssetToChannel.java` は、ワークフローのメタデータを調べ、画像を参照するようにScreensチャネルを更新するカスタムワークフロープロセスステップです。

1. ソースコードのダウンロード：**[screens-demo-main.zip](./assets/screens-demo-main.zip)**
1. お気に入りのIDEを使用して、コードを解凍し、表示します。
