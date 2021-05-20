---
title: 機能パック 202103 のリリースノート
description: 「2021 年 3 月 5 日にリリースされた AEM Screens 機能パック 202103 について説明します。」
feature: 機能パック
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 60a6583dd3bf79ef09099506107705bf0bce1e07
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 100%

---

# 機能パック 202103 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>最新バージョンの Adobe Experience Manager（AEM）にアップグレードすることをお勧めします。Screens では、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供しています。

## 入手方法 {#availability}

AEM Screens は、AEM 6.5 機能パック 7 をリリースしました。

Adobe ID を使用して、AEM Screens 6.5.7 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して「**AEM 6.5 Screens FP7**」というタイトルが付いた最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens 機能パック 202103 のリリース日は 2021 年 3 月 5 日です。

### 新機能 {#what-is-new}

* **AEM Screens のプレーヤーの自動登録**

   何千ものプレーヤーを手動で一括登録するのは非常に面倒で、時間とコストが余計にかかります。このプロセスを簡単にするために、プレーヤーの自動登録機能では、設定ファイルまたはモバイルデバイス管理（MDM）ソリューションを通じてプレーヤーにプロビジョニングできる事前共有キーを AEM に指定できます。

   詳しくは、[プレーヤーの自動登録](/help/user-guide/auto-registration-players.md)を参照してください。


* **エンタープライズモビリティ管理を使用した Android プレーヤーの一括プロビジョニング**

   Android プレーヤーを一括デプロイする場合、プレーヤーを 1 つずつ手動で AEM に登録するのは非常に面倒です。VMWare Airwatch、MobileIron、Samsung Knox などの EMM（エンタープライズモビリティ管理）ソリューションを使用して、デプロイメントのプロビジョニングと管理をリモートでおこなうことを強くお勧めします。AEM Screens Android プレーヤーでは、業界標準の EMM AppConfig をサポートしているので、リモートプロビジョニングが可能です。

   詳しくは、[エンタープライズモビリティ管理を使用した Android プレーヤーの一括プロビジョニング](/help/user-guide/implementing-android-player.md#implementation)を参照してください。


### バグ修正 {#bug-fixes}

* `clientlib` と `asset hashes` の計算のパフォーマンスが向上しました。

* キャッシュを無効にしなかった場合、スマート同期への移行でプレーヤーが正常に動作しなくなる問題を修正しました。

* 割り当てに *OfflineConfig* が含まれる場合にオフラインキャッシュが作成されない問題を修正しました。

* リファラーポリシー strict-origin-when-cross-origin をサポートしていないので正常に動作しなかった Tizen プレーヤーを更新しました。

* 割り当てたチャネルのスケジュールの「*繰り返し*」フィールドを変更すると UI が正常に動作しなくなる問題を修正しました。

* クエリの例外が発生して「オフラインコンテンツを更新」が正常に機能しない問題を修正しました。

* インタラクティブなエクスペリエンスにおけるインタラクションで発生する、トランジション間のタイムラグを修正しました。

* 設定更新リクエストの失敗により画面が空白になる問題を修正しました。

### リリースされている AEM Screens Player {#released-aem-screens-players}

AEM Screens 6.5 機能パック 7 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Linux

#### AEM Screens Player のダウンロード {#aem-screens-player-downloads}

最新の AEM Screens Player のダウンロードとバグ修正について詳しくは、**[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/index.html)**&#x200B;を参照してください。
