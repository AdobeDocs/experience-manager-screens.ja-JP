---
title: Screens Player のインストール
description: AEM Screens Player を正しくインストールする方法を説明します。
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: ht
source-wordcount: '503'
ht-degree: 100%

---

# AEM Screens Player のインストール {#installing-player}

ここでは、AEM Screens Player のインストール方法について説明します。

## 使用可能な Screens Player {#available-players}

AEM Screens Player は Android™、Chrome OS および Windows で使用できます。

**AEM Screens Player** をダウンロードするには、[AEM 6.5 Player のダウンロード](https://download.macromedia.com/screens/)ページにアクセスします。

>[!NOTE]
>
>最新のプレーヤー（*.exe*）をダウンロードしたら、以下の手順に従ってプレイヤーのアドホックインストールを完了できます。
>
>1. 左上隅を長押しして、管理パネルを開きます。
>1. 左のアクションメニューから「**設定**」に移動し、AEM インスタンスの場所のアドレスを「**サーバー**」に入力して、「**保存**」をクリックします。
>1. 左のアクションメニューの「**登録**」リンクをクリックし、以下の手順でデバイス登録プロセスを完了します。

## 基本的な再生モニタリング {#playback-monitoring}

プレーヤーは、各 `ping`（デフォルトは 30 秒）で様々な再生指標を報告します。これらの指標に基づいて、様々なエッジケース（動きのないエクスペリエンス、空白の画面、スケジュールの問題など）を検出できます。これにより、デバイスの問題を把握してトラブルシューティングできるので、調査や修正を迅速に行えます。

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
| activeElements {string} | コンマ区切りの文字列。再生中のすべてのシーケンスチャネルに現在表示されている要素（マルチゾーンレイアウトがある場合は複数） |
| isDefaultContent {boolean} | 再生チャネルがデフォルトチャネルまたはフォールバックチャネルと見なされる（つまり、優先度が 1 でスケジュールが設定されていない）場合は true |
| hasContentChanged {boolean} | コンテンツが過去 5 分間に変更された場合は true、それ以外の場合は false |
| lastContentChange {string} | 最後にコンテンツが変更されたときのタイムスタンプ |

>[!NOTE]
>オプションで、プレーヤーの環境設定（「再生モニタリングを有効にする」）から、次の高度なプロパティを有効にすることができます。
>
>| プロパティ | 説明 |
>|---|---|
>| isContentRendering {boolean} | GPU が実際のコンテンツを再生していることを（ピクセル分析に基づいて）確認できる場合は true |

### 制限事項 {#limitations}

基本的な再生モニタリングに関するいくつかの制限事項を以下に示します。

* プレーヤーが自分自身の再生状態をサーバーに報告するので、アクティブな接続が必要です。

* GPU をチェックする `isContentRendering` プロパティは、リソースを大量に消費するので、デフォルトで有効にするのではなく、プレーヤーの環境設定から明示的にオプトインする必要があります。アドビでは、実稼動環境のビデオと組み合わせて使用しないことをお勧めします。

* この機能はシーケンスチャネルの場合にのみサポートされており、インタラクティブチャネル（SPA）のユースケースにはまだ対応していません。

* 指標は、まだ完全にはお客様に公開されていませんが、アドビは、近日中にダッシュボードに似たレポートおよび警告メカニズムを実現できるように取り組んでいます。

### その他のリソース {#additional-resources}

詳しくは、以下のトピックを参照してください。

* Android™ プレーヤーをダウンロードするには、**Google Play** にアクセスします。Android™ ウォッチドッグの実装については、[Android™ プレーヤーの実装](implementing-android-player.md)を参照してください。

* Chrome OS プレーヤーの実装について詳しくは、[Chrome 管理コンソール](implementing-chrome-os-player.md)を参照してください。

* Windows 版 AEM Screens Player を設定するには、[Windows プレーヤーの実装](implementing-windows-player.md)を参照してください。
