---
title: 機能パック 202001 のリリースノート
description: 2020 年 1 月 31 日にリリースされたAEM Screens機能パック 202001 について説明します。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: c1a0b394-97dc-4104-b2b4-41fcbb63a22e
source-git-commit: 02929219a064e3b936440431e77e67e0bf511bf6
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 41%

---

# 機能パック 202001 のリリースノート{#release-notes-for-feature-pack}

>[!CAUTION]
>
>最新バージョンのAdobe Experience Manager（AEM）にアップグレードしてください。 AEM Screensは、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供します。

## 可用性 {#availability}

AEM Screens では、AEM 6.5 機能パック 3 をリリースしました。

Adobe ID を使用して、AEM Screens 6.5.3 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して「**AEM 6.5 Screens FP3**」というタイトルが付いた最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens 機能パック 202001 のリリース日は 2020年1月31日（PT）です。

### 新機能 {#what-s-new}

* **アセット再生のコマンド同期**

コマンド同期を使用すると、異なるプレーヤー間で再生を同期させることができます。プレーヤーは異なるコンテンツを再生できますが、各アセットのデュレーションは同じである必要があります。
コマンド同期の詳細と、プライマリとクライアントの設定方法については、を参照してください。 [コマンド同期の使用](using-command-sync.md).

* **https のステータスを表示し、空のリファラーを許可するためのヘルスチェックフレームワーク**

ヘルスチェックフレームワークを使用すると、AEM Screens プロジェクトを実行する前に 2 つの必要な設定（空のリファラーリクエストと Apache Felix Jetty ベースの HTTP サービスを許可）がセットアップされているかどうかを確認できます。

ヘルスチェックフレームワークについて詳しくは、 [ヘルスチェックフレームワーク](/help/user-guide/configuring-screens-introduction.md#health-check-framework).

* **デフォルトのトランジションタイプの更新**
トランジションコンポーネントのプロパティ（例：） **タイプ** はに設定されました **フェード** および **期間** as **1600 ミリ秒**（デフォルト）。

  参照： [切り替えの適用](/help/user-guide/applying-transitions.md) ユースケースを参照してください。


### リリースされている AEM Screens Player

AEM 6.4 機能パック 7 および AEM 6.5 機能パック 3 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Android™

#### AEM Screens Player のダウンロード 

最新のAEM Screens Player のダウンロードとバグ修正について詳しくは、以下を参照してください。 [**AEM Screens Player のダウンロード**](https://download.macromedia.com/screens/).
