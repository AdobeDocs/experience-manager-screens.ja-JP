---
title: Screens Player のインストール
description: AEM Screens Player を正しくインストールする方法を説明します。
contentOwner: jsyal
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: bb979a71-7235-429f-b520-6d85b8b666fa
TQID: https://experienceleague.adobe.com/Lu1KYTTaDEiaC1xP4k0V8KqDVoe5gIzqkut-JB0G4fg
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 552
ht-degree: 86%

---

# AEM Screens Player のインストール {#installing-player}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

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

プレーヤーは、各 `ping`（デフォルトは 30 秒）で様々な再生指標を報告します。 これらの指標にもとづいて、エクスペリエンスの停滞、空白の画面、スケジュール設定の問題など、さまざまなエッジケースを検出できます。 これにより、デバイスの問題を把握してトラブルシューティングできるので、調査や修正を迅速に行えます。

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
>
>オプションで、プレーヤーの環境設定（「再生モニタリングを有効にする」）から、次の高度なプロパティを有効にすることができます。
>
>| プロパティ | 説明 |
>|---|---|
>| isContentRendering {boolean} | GPU が実際のコンテンツを再生していることを（ピクセル分析に基づいて）確認できる場合は true |

### 制限事項 {#limitations}

基本的な再生モニタリングに関するいくつかの制限事項を以下に示します。

* プレーヤーが自分自身の再生状態をサーバーに報告するので、アクティブな接続が必要です。

* GPU をチェックする `isContentRendering` プロパティは、リソースを大量に消費するので、デフォルトで有効にするのではなく、プレーヤーの環境設定から明示的にオプトインする必要があります。 アドビでは、実稼動環境のビデオと組み合わせて使用しないことをお勧めします。

* この機能はシーケンスチャネルの場合にのみサポートされており、インタラクティブチャネル（SPA）のユースケースにはまだ対応していません。

* 指標は、まだ完全にはお客様に公開されていませんが、アドビは、近日中にダッシュボードに似たレポートおよび警告メカニズムを実現できるように取り組んでいます。

### その他のリソース {#additional-resources}

詳しくは、以下のトピックを参照してください。

* Android™ プレーヤーをダウンロードするには、**Google Play** にアクセスします。 Android™ ウォッチドッグの実装については、[Android™ プレーヤーの実装](implementing-android-player.md)を参照してください。

* Chrome OS プレーヤーの実装について詳しくは、[Chrome 管理コンソール](implementing-chrome-os-player.md)を参照してください。

* Windows 版 AEM Screens Player を設定するには、[Windows プレーヤーの実装](implementing-windows-player.md)を参照してください。
