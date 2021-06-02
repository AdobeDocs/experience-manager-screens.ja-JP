---
title: ワークフローを使用した AEM Screens チャネルのアセット更新の自動化
seo-title: ワークフローを使用した AEM Screens チャネルのアセット更新の自動化
description: Adobe Experience Manager にアップロードされたアセットを自動的に処理して Screens チャネルに動的に割り当てるワークフローを作成する方法について説明します。この例では、画像が特定のフォルダーに追加されると、動的な透かしを適用してその画像を Screens チャネルに割り当てるワークフローがトリガーされます。この例で得た知見は、様々な自動化シナリオに適用できます。
seo-description: Adobe Experience Manager にアップロードされたアセットを自動的に処理して Screens チャネルに動的に割り当てるワークフローを作成する方法について説明します。この例では、画像が特定のフォルダーに追加されると、動的な透かしを適用してその画像を Screens チャネルに割り当てるワークフローがトリガーされます。この例で得た知見は、様々な自動化シナリオに適用できます。
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Screens の開発
role: Developer
level: Intermediate
source-git-commit: 8d1633dab9e70ea988516cf9ee4d1b0a780bc7e9
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 100%

---


# ワークフローを使用した AEM Screens チャネルのアセット更新の自動化 {#automate-channel-updates-workflow}

Adobe Experience Manager にアップロードされたアセットを自動的に処理して Screens チャネルに動的に割り当てるワークフローを作成する方法について説明します。この例では、画像が特定のフォルダーに追加されると、動的なオーバーレイ（透かし処理）を適用してその画像を Screens チャネルに割り当てるワークフローがトリガーされます。この例で得た知見は、様々な自動化シナリオに適用できます。

## 前提条件 {#prerequisites}

このチュートリアルを完了するには、以下が必要です。

1. [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=ja)
1. [AEM サービスパック 8 以降](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=ja)
1. [AEM 6.5 Screens FP7 以降](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103.html?lang=ja)

## クイックセットアップ {#quick-setup}

次のビデオでは、Adobe Experience Manager に新しいワークフローを導入するサンプルコードパッケージのインストール方法を説明します。この機能を使用すると、Screens チャネルを指すように AEM Assets のフォルダーのプロパティを更新できます。そのフォルダーに画像が追加されると、その画像は指定された Screens チャネルに追加されます。

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. コンパイル済みコードパッケージ **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)** をダウンロードします。
1. AEM パッケージマネージャーを使用して、上記パッケージをインストールします。

## ワークフローモデル {#workflow-model}

画像の追加先となる Screens チャネルを記述するカスタムフォルダーメタデータスキーマが作成されました。2 つのワークフローモデルを使用して、アセットの処理が自動化されています。カスタムワークフロー **Screens Demo Asset Processing** を呼び出すように、**DAM アセットの更新**&#x200B;ワークフローが変更されています。このカスタムワークフローでは、アセットの格納フォルダーを調べて、追加先となる Screens チャネルを決定します。また、**Screens Demo Asset Processing** ワークフローでは、画像への透かしの適用も行います。

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## カスタムワークフロープロセスステップ {#workflow-process-step}

**Screens Demo Asset Processing** ワークフローの一部として使用されている 2 つのカスタムワークフロープロセスステップについて調べてみましょう。

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

1 つ目のカスタムワークフロープロセスステップ `AssetProcessingCheck.java` では、ワークフローのペイロードを確認して、ペイロードがアセットかどうか、および格納フォルダーが Screens チャネルを指すように設定されているかどうかを判定します。この要件が満たされた場合、このプロセスステップは `screen-channel` と `asset-path` の 2 つのプロパティをワークフローのメタデータに保存します。

もう 1 つのカスタムワークフロープロセスステップ `AddAssetToChannel.java` では、ワークフローのメタデータを調べ、画像を参照するように Screens チャネルを更新します。

1. ソースコード **[screens-demo-main.zip](./assets/screens-demo-main.zip)** をダウンロードします。
1. コードを解凍し、お気に入りの IDE を使用して表示します。
