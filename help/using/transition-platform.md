---
title: プラットフォームへの移行
description: AEM Screens でのプラットフォームへの移行について説明します。
exl-id: e69f504f-d20b-4cdb-b567-5c9c1df4d331
TQID: https://experienceleague.adobe.com/xefeUV4bgG-I7zVOGcAnNkcdx1Y-XQfmAr2bFT5nFN0
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 225
ht-degree: 79%

---

# プラットフォームへの移行 {#transition-platform}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

>[!NOTE]
>
>このアクティビティの典型的な関係者は、AEM 実装担当者です。

プロジェクトが戦略ビジョンからワイヤーフレーム化された現実のものへと進むにつれて、デプロイできる Screens プロジェクトを AEM で実際に作成する準備が必要です。

このプロジェクトには、プラットフォーム固有の設定を、プロトタイプ段階で大まかに定義した要件にマッピングすることが含まれます。

例としては、以下を使用する方法とタイミングが挙げられます。

* **エクスペリエンスフラグメント**（コンテンツのグループ化を作成するため）
* **コンテンツフラグメント**（テキストのバリエーションを作成するため）
* **Context Hub**（インタラクティブなエクスペリエンスの外部データストアや SPA を作成するため）
* **OSGi サービス**（ネットワークアラート用）
* **アセットリンク**（Creative Cloud ソーシング用）
* **ネットワークフォルダー**（アセット割り当て用）
* **テキストオーバーレイ**（リアルタイムデータ用）
* **スケジュール**（ディスプレイ／チャネルグループ化のため）
* **ワークフロー**（自動コンテンツ編集用）

このフェーズでは、注意が必要なすべての必須タスクおよびアクティビティを確認し適切に文書化して、割り当てたタスクをデプロイメントフェーズで適切に追跡できるようにします。

また、このフェーズでは、事前に定義されたすべてのアクティビティを自動化可能な候補としてレビューします。
