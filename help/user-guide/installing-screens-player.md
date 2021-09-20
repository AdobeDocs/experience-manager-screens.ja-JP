---
title: Screens Player のインストール
seo-title: Installing Screens Player
description: このページでは、使用可能な AEM Screens Player のインストールについて説明します。
seo-description: Installing Screens Player
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: c6506ca62e806ec11d3380d6ac7670bcfcf13adb
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 36%

---

# AEM Screens Player のインストール {#installing-player}

ここでは、AEM Screens Player のインストール方法について説明します。

## 使用可能な Screens Player {#available-players}

AEM Screens Player は Android、Chrome OS、Windows で使用できます。

**AEM Screens Player** をダウンロードするには、[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/)ページにアクセスします。

>[!NOTE]
>
>最新のプレーヤー（*.exe*）をダウンロードしたら、以下の手順に従ってプレイヤーのアドホックインストールを完了します。
>
>1. 左上隅を長押しして、管理パネルを開きます。
>1. 左のアクションメニューから「**設定**」に移動し、AEM インスタンスの場所のアドレスを「**サーバー**」に入力して、「**保存**」をクリックします。
>1. 左のアクションメニューの「**登録**」リンクをクリックし、以下の手順でデバイス登録プロセスを完了します。


## 基本的な再生の監視 {#playback-monitoring}

プレーヤーが様々な再生指標をレポートする際に、各`ping`のデフォルト値が30秒に設定されます。 これらの指標に基づいて、動きのないエクスペリエンス、空白の画面、スケジュールの問題など、様々なエッジケースを検出できます。 これにより、デバイスの問題を把握し、トラブルシューティングでき、調査や修正に関する措置を迅速におこなえます。

AEM Screens Playerの基本的な再生監視では、次のことが可能です。

* プレーヤーがコンテンツを適切に再生している場合は、リモートで監視します。

* フィールド内の空白の画面や壊れたエクスペリエンスに対する反応性を向上させます。

* エンドユーザーにエクスペリエンスが壊れるリスクを軽減します。

### プロパティについて {#understand-properties}

各`ping`には、次のプロパティが含まれます。

| プロパティ | 詳細 |
|---|---|
| id {string} | プレーヤー識別子 |
| activeChannel {string} | 現在再生中のチャネルパス。何もスケジュールされていない場合はnull。 |
| activeElements {string} | コンマ区切りの文字列。現在は、すべての再生シーケンスチャネルに表示される要素（マルチゾーンレイアウトの場合は複数） |
| isDefaultContent {boolean} | 再生チャネルがデフォルトチャネルまたはフォールバックチャネルと見なされる（つまり、優先度が1でスケジュールが設定されていない）場合はtrue |
| hasContentChanged {boolean} | 過去5分間にコンテンツが変更された場合はtrue 、それ以外の場合はfalse |
| lastContentChange {string} | 前回のコンテンツ変更のタイムスタンプ |

>[!NOTE]
>オプションで、プレーヤーの環境設定（「再生監視を有効にする」）から、より高度なプロパティを有効にできます。つまり、
>|プロパティ|説明|
>|—|—|
>|isContentRendering {boolean}|GPUが実際のコンテンツの再生を確認できる場合はtrue（ピクセル分析に基づく）|

### 制限事項 {#limitations}

基本的な再生監視に関する制限の一部を以下に示します。

* プレーヤーがサーバーに独自の再生状態を報告するので、アクティブな接続が必要です。

* GPUをチェックする`isContentRendering`プロパティは、現在、デフォルトで有効にするにはリソースの消費が多すぎるので、プレーヤーの環境設定から明示的なオプトインが必要です。 実稼動環境では、ビデオと組み合わせて使用しないことをお勧めします。

* この機能はシーケンスチャネルに対してのみサポートされ、まだインタラクティブチャネル(SPA)の使用例には対応していません。

* 指標はまだお客様に完全に公開されていないので、近い将来、ダッシュボードに似たレポートおよびアラートメカニズムを有効にするよう、取り組んでいます。

### その他のリソース {#additional-resources}

詳細については、以下のトピックを参照してください。

* Android プレーヤーをダウンロードするには、**Google Play** にアクセスします。Android ウォッチドッグの実装については、[Android プレーヤーの実装](implementing-android-player.md)を参照してください。

* Chrome OS プレーヤーの実装について詳しくは、[Chrome 管理コンソール](implementing-chrome-os-player.md)を参照してください。

* Windows 版 AEM Screens Player を設定するには、[Windows 10 プレーヤーの実装](implementing-windows-player.md)を参照してください。
