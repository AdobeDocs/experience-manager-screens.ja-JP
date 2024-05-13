---
title: ダイレクト配置ワークフロー設定
description: このページでは、ダイレクト配置ワークフロー設定について説明します。
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 84%

---


# ダイレクト配置ワークフロー設定 {#direct-placement-workflow}

このページでは、事前定義された AEM Screens チャネルにプログラムでアセットを挿入できるアセットワークフローの設定について説明します。

ここでは、以下のトピックについて説明します。

* 概要
* ダイレクト配置ワークフローの設定

## 概要 {#overview}

ダイレクト配置ワークフローの設定は、AEM Screens プロジェクトチャネルをアセット内の特定のフォルダーにマップし、そのフォルダー内の任意のアセットを配置できるようにします。アドビでは、オフライン一括アップデートをトリガーして公開を完了することをお勧めします。

または、コンテンツ作成者が手動でクリックすることもできます。 **オフラインコンテンツを更新**.

>[!NOTE]
>
>オフラインで一括更新を使用する方法については、[サービスとしてのコンテンツ更新](/help/user-guide/content-update-as-a-service.md)を参照してください。

## ダイレクト配置ワークフローの設定 {#configuring-workflow}

>[!IMPORTANT]
>
>設定を開始する前に、をインストールします `[Demo  Package](https://github.com/godanny86/screens-demo/releases/download/v.0.0.1/screens-demo.all-1.0-SNAPSHOT.zip)`. パッケージをインストールすると、AEM インスタンス／ツール（アイコン）／**ワークフロー**／**ワークフローモデル**&#x200B;から表示してアクセスできます。

ダイレクト配置ワークフローを設定するには、次の手順を実行します。

1. AEM インスタンスから AEM Screens に移動し、**アセットワークフロー**&#x200B;という名前の Screens プロジェクトを作成します。

1. というタイトルのチャネルの作成 **Workflow-Assets** の下 **チャネル** フォルダー。

