---
title: ワークフローを使用したAEM Screens チャネルのアセット更新の自動化
description: Adobe Experience Managerにアップロードされたアセットを自動処理して Screens チャネルに動的に割り当てるワークフローを作成する方法について説明します。
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 42%

---


# ワークフローを使用したAEM Screens チャネルのアセット更新の自動化 {#automate-channel-updates-workflow}

Adobe Experience Manager にアップロードされたアセットを自動的に処理して Screens チャネルに動的に割り当てるワークフローを作成する方法について説明します。この例では、画像が特定のフォルダーに追加されると、ワークフローがトリガーされます。 ワークフローにより、ダイナミックテキストオーバーレイ（透かし処理）が適用され、画像が Screens チャネルに割り当てられます。 この例で得た知見は、様々な自動化シナリオに適用できます。

## 前提条件 {#prerequisites}

このチュートリアルを完了するには、以下が必要です。

1. [AEM 6.5](https://experienceleague.adobe.com/ja/docs/experience-manager-65)
1. [AEM サービスパック 8 以降](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/release-notes/release-notes)
1. [AEM 6.5 Screens FP7 以降](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/release-notes/release-notes-fp-202103)

## クイックセットアップ {#quick-setup}

次のビデオでは、Adobe Experience Managerに新しいワークフローを導入するサンプルコードパッケージのインストール方法を説明します。 この機能を使用すると、Screens チャネルを指すように AEM Assets のフォルダーのプロパティを更新できます。そのフォルダーに画像が追加されると、その画像は指定されたAEM Screens チャンネルに追加されます。

>[!VIDEO](https://video.tv.adobe.com/v/333174/?quality=12&learn=on)

1. コンパイル済みコードパッケージ **[screens-demo.all-2.0.0-SNAPSHOT.zip](./assets/screens-demo.all-2.0.0-SNAPSHOT.zip)** をダウンロードします。
1. AEM パッケージマネージャーを使用して、上記パッケージをインストールします。

## ワークフローモデル {#workflow-model}

画像の追加先となる Screens チャネルを記述するカスタムフォルダーメタデータスキーマが作成されました。2 つのワークフローモデルを使用して、アセット処理が自動化されています。 この **DAM アセットの更新** ワークフローを編集して、カスタムワークフロー**Screens Demo Asset Processing を呼び出します。このカスタムワークフローでは、アセットの格納フォルダーを調べて、追加先となる Screens チャネルを決定します。 また、**Screens Demo Asset Processing** ワークフローでは、画像への透かしの適用も行います。

>[!VIDEO](https://video.tv.adobe.com/v/333175/?quality=12&learn=on)

## カスタムワークフロープロセスステップ {#workflow-process-step}

**Screens Demo Asset Processing** ワークフローの一部として使用されている 2 つのカスタムワークフロープロセスステップについて調べてみましょう。

>[!VIDEO](https://video.tv.adobe.com/v/333179/?quality=12&learn=on)

この `AssetProcessingCheck.java` カスタムワークフローは、ワークフローのペイロードに対してチェックを実行するプロセスです。 ペイロードがアセットかどうか、および格納フォルダーがAEM Screens チャネルを指すように設定されているかどうかを判断します。 この要件が満たされた場合、このプロセスステップは `screen-channel` と `asset-path` の 2 つのプロパティをワークフローのメタデータに保存します。

この `AddAssetToChannel.java` カスタムワークフローは、ワークフローのメタデータを調べ、画像を参照するようにAEM Screens チャネルを更新するプロセスステップです。

1. ソースコード **[screens-demo-main.zip](./assets/screens-demo-main.zip)** をダウンロードします。
1. コードを解凍し、お気に入りの IDE を使用して表示します。
