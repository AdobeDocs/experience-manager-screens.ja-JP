---
title: 機能パック 202001 のリリースノート
seo-title: Release Notes for Feature Pack 202001
description: 2020 年 1 月 31 日にリリースされた AEM Screens 機能パック 202001 について説明します。
seo-description: Follow this page to get information for AEM Screens Feature Pack 202001 released on January 31, 2020.
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: c1a0b394-97dc-4104-b2b4-41fcbb63a22e
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 77%

---

# 機能パック 202001 のリリースノート{#release-notes-for-feature-pack}

>[!CAUTION]
>
>最新バージョンの Adobe Experience Manager（AEM）にアップグレードすることをお勧めします。Screens では、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供しています。

## 入手方法 {#availability}

AEM Screens では、AEM 6.5 機能パック 3 をリリースしました。

Adobe ID を使用して、AEM Screens 6.5.3 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して「**AEM 6.5 Screens FP3**」というタイトルが付いた最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens 機能パック 202001 のリリース日は 2020年1月31日（PT）です。

### 新機能 {#what-s-new}

* **アセット再生のコマンド同期**
コマンド同期を使用すると、異なるプレーヤー間で再生を同期させることができます。 プレーヤーごとに異なるコンテンツを再生できますが、各アセットの再生時間は同じにする必要があります。
コマンド同期の詳細と、マスターとクライアントの設定方法については、を参照してください。 [コマンド同期の使用](using-command-sync.md).

* **HTTPS のステータスを表示し、空のリファラーを許可するヘルスチェックフレームワーク**：
AEM Screens プロジェクトを実行する前に、ヘルスチェックフレームワークを使用して 2 つの必要な設定（空のリファラー要求の許可および Apache Felix Jetty Based HTTP Service の許可）が設定されているかどうかを確認できます。

  ヘルスチェックフレームワークについて詳しくは、 [ヘルスチェックフレームワーク](/help/user-guide/configuring-screens-introduction.md#health-check-framework).

* **デフォルトのトランジションタイプの更新**：
デフォルトでは、トランジションコンポーネントのプロパティは、例えば、「**タイプ**」は「**フェード**」に、「**デュレーション（ms）**」は「**1600**」に設定されています。

  参照： [切り替えの適用](/help/user-guide/applying-transitions.md) ユースケースを参照してください。


### リリースされている AEM Screens Player {#released-aem-screens-players}

AEM 6.4 機能パック 7 および AEM 6.5 機能パック 3 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Android

#### AEM Screens Player のダウンロード   {#aem-screens-player-downloads}

最新のAEM Screens Player のダウンロードとバグ修正について詳しくは、以下を参照してください。 [**AEM Screens Player のダウンロード**](https://download.macromedia.com/screens/).
