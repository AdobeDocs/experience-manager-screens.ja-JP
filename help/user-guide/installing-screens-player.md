---
title: Screens Player のインストール
description: AEM Screens Player を正しくインストールする方法を説明します。
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: 02929219a064e3b936440431e77e67e0bf511bf6
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 52%

---

# AEM Screens Player のインストール {#installing-player}

ここでは、AEM Screens Player のインストール方法について説明します。

## 使用可能な Screens Player {#available-players}

AEM Screens Player は、Android™、Chrome OS および Windows で使用できます。

**AEM Screens Player** をダウンロードするには、[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/)ページにアクセスします。

>[!NOTE]
>
>最新の Player をダウンロードしたら、*.exe*）、プレーヤーの手順に従ってアドホックインストールを完了します。
>
>1. 左上隅のを長押して、管理パネルを開きます。
>1. 左のアクションメニューから「**設定**」に移動し、AEM インスタンスの場所のアドレスを「**サーバー**」に入力して、「**保存**」をクリックします。
>1. クリック **登録** 左側のアクションメニューからのリンクと以下の手順に従って、デバイス登録プロセスを完了します。

## 基本的な再生モニタリング {#playback-monitoring}

プレーヤーは、各 `ping`（デフォルトは 30 秒）で様々な再生指標を報告します。これらの指標に基づいて、様々なエッジケース（動きのないエクスペリエンス、空白の画面、スケジュールの問題など）を検出できます。 これにより、デバイスの問題を把握してトラブルシューティングできるので、調査や修正を迅速に行えます。

AEM Screens Player での基本的な再生モニタリングにより、次の操作を行うことができます。

* プレーヤーがコンテンツを適切に再生しているかどうかのリモート監視

* 空白の画面やフィールド内のエクスペリエンスの不具合に対する反応性の向上

* 不具合のあるエクスペリエンスがエンドユーザーに表示されるリスクの軽減

### プロパティについて {#understand-properties}

各 `ping` には、次のプロパティが含まれています。

| プロパティ | 説明 |
|---|---|
| id {string} | プレーヤーの識別子 |
| activeChannel {string} | 現在再生中のチャネルパス。何もスケジュールされていない場合は null |
| activeElements {string} | コンマ区切りの文字列。再生中のすべてのシーケンスチャネルに現在表示されている要素（マルチゾーンレイアウトは複数）を表します |
| isDefaultContent {boolean} | 再生チャネルがデフォルトチャネルまたはフォールバックチャネルと見なされる（つまり、優先度が 1 でスケジュールが設定されていない）場合は true |
| hasContentChanged {boolean} | コンテンツが過去 5 分間に変更された場合は true、それ以外の場合は false |
| lastContentChange {string} | 最後にコンテンツが変更されたときのタイムスタンプ |

>[!NOTE]
>オプションで、プレーヤーの環境設定（「再生モニタリングを有効にする」）から、次の高度なプロパティを有効にすることができます。
>
>| プロパティ | 説明 |
>|---|---|
>| isContentRendering {boolean} | gpu が実際のコンテンツを再生していることを（ピクセル分析に基づいて）確認できる場合は true |

### 制限事項 {#limitations}

基本的な再生モニタリングに関するいくつかの制限事項を以下に示します。

* プレーヤーが自分自身の再生状態をサーバーに報告するので、アクティブな接続が必要です。

* この `isContentRendering` gpu が大量のリソースを消費しているかどうかを確認するプロパティがデフォルトで有効になっている必要があり、プレーヤーの環境設定で明示的にオプトインする必要があります。 Adobeでは、実稼動環境のビデオでは使用しないことをお勧めします。

* この機能はシーケンスチャネルの場合にのみサポートされており、インタラクティブチャネル（SPA）のユースケースにはまだ対応していません。

* これらの指標は、まだ顧客に完全には公開されておらず、Adobeでは、ダッシュボードのようなレポートおよびアラートのメカニズムの有効化に間もなく取り組んでいます。

### その他のリソース {#additional-resources}

詳しくは、次のトピックを参照してください。

* Android™ Player をダウンロードするには、以下を参照してください： **Google Play**. Android™ ウォッチドッグの実装については、以下を参照してください。 [Android™ プレーヤーの実装](implementing-android-player.md).

* Chrome OS プレーヤーを実装するには、を参照してください。 [Chrome 管理コンソール](implementing-chrome-os-player.md) を参照してください。

* AEM Screens Windows プレーヤーを設定するには、以下を参照してください。 [Windows プレーヤーの実装](implementing-windows-player.md).
