---
title: 機能パック 202103 のリリースノート
description: 2021 年 3 月 5 日にリリースされたAEM Screens機能パック 202103 の詳細情報。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 10c168cd00b79964d229e3d2a14049e799d89d77
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 47%

---

# 機能パック 202103 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobeでは、最新バージョンのAdobe Experience Manager（AEM）にアップグレードすることをお勧めします。 AEM Screensは、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供します。

## 入手方法 {#availability}

AEM Screens は、AEM 6.5 機能パック 7 をリリースしました。

Adobe ID を使用して、AEM Screens 6.5.7 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して「**AEM 6.5 Screens FP7**」というタイトルが付いた最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens 機能パック 202103 のリリース日は 2021 年 3 月 5 日です。

### 新機能 {#what-is-new}

* **AEM Screens のプレーヤーの自動登録**

  何千人ものプレーヤーを手動で一括登録するのは面倒で、時間とコストが増えます。 このプロセスを簡単にするために、プレーヤーの自動登録機能を使用して、AEMで事前共有キーを指定できます。 このキーは、設定ファイルまたはモバイルデバイス管理（MDM）ソリューションを使用して、プレーヤーにプロビジョニングできます。

  参照： [プレーヤーの自動登録](/help/user-guide/auto-registration-players.md) を参照してください。


* **エンタープライズモビリティ管理を使用した Android™ プレーヤーの一括プロビジョニング**

  Android™ プレーヤーを一括でデプロイする場合は、すべてのプレーヤーをAEMに手動で登録するのが面倒になります。 次のような EMM （エンタープライズモビリティ管理）ソリューションを使用することを強くお勧めします `VMWare Airwatch`, `MobileIron`、または `Samsung Knox` デプロイメントをリモートでプロビジョニングおよび管理します。 AEM Screens Android™ プレーヤーは、業界標準の EMM AppConfig をサポートしており、リモートプロビジョニングが可能です。

  参照： [エンタープライズモビリティ管理を使用した Android™ プレーヤーの一括プロビジョニング](/help/user-guide/implementing-android-player.md#implementation) を参照してください。


### バグの修正 {#bug-fixes}

* `clientlib` と `asset hashes` の計算のパフォーマンスが向上しました。

* キャッシュを無効にしなかった場合、スマート同期への移行でプレーヤーが正常に動作しなくなる問題を修正しました。

* 割り当てに *OfflineConfig* が含まれる場合にオフラインキャッシュが作成されない問題を修正しました。

* 更新先 `Tizen` リファラーポリシーがクロスオリジンの場合に厳格なオリジン設定をサポートしていないことが原因で破損したプレーヤー。

* 割り当てたチャネルのスケジュールの「*繰り返し*」フィールドを変更すると UI が正常に動作しなくなる問題を修正しました。

* クエリの例外が発生して「オフラインコンテンツを更新」が正常に機能しない問題を修正しました。

* インタラクティブなエクスペリエンスにおけるインタラクションで発生する、トランジション間のタイムラグを修正しました。

* 設定更新リクエストの失敗により画面が空白になる問題を修正しました。

### リリースされている AEM Screens Player

AEM Screens 6.5 機能パック 7 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Linux®

#### AEM Screens Player のダウンロード 

最新のAEM Screens Player のダウンロードとバグ修正について詳しくは、以下を参照してください。 **[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/index.html)**.
