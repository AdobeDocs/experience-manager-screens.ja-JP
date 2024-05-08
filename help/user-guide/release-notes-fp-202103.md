---
title: 機能パック 202103 のリリースノート
description: 2021 年 3 月 5 日にリリースされたAEM Screens機能パック 202103 の詳細情報。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: a8741cc7-de4f-4e5a-b69e-852a43597123
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 24%

---

# 機能パック 202103 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobeでは、最新バージョンのAdobe Experience Manager（AEM）にアップグレードすることをお勧めします。 AEM Screensは、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供します。

## 入手方法 {#availability}

AEM Screens は、AEM 6.5 機能パック 7 をリリースしました。

AEM Screens 6.5.7 リリースの最新の機能パックは、からダウンロードできます。 [ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) Adobe IDを使用する。 に移動します。 **Adobe Experience Manager** タブで「」を検索 **スクリーン** というタイトルの最新の機能パックを取得するには **AEM 6.5 Screens FP7**.

## リリース日 {#release-date}

AEM Screens 機能パック 202103 のリリース日は 2021 年 3 月 5 日です。

### 新機能 {#what-is-new}

* **AEM Screens のプレーヤーの自動登録**

  何千人ものプレーヤーを手動で一括登録するのは面倒で、時間とコストが増えます。 このプロセスを簡単にするために、プレーヤーの自動登録機能を使用して、AEMで事前共有キーを指定できます。 このキーは、設定ファイルまたはモバイルデバイス管理（MDM）ソリューションを使用して、プレーヤーにプロビジョニングできます。

  参照： [プレーヤーの自動登録](/help/user-guide/auto-registration-players.md) を参照してください。


* **エンタープライズモビリティ管理を使用した Android™ プレーヤーの一括プロビジョニング**

  Android™ プレーヤーを一括でデプロイする場合、すべてのプレーヤーをAEMに手動で登録するのは面倒になります。 次のような EMM （エンタープライズモビリティ管理）ソリューションを使用することを強くお勧めします `VMWare Airwatch`, `MobileIron`、または `Samsung Knox` デプロイメントをリモートでプロビジョニングおよび管理します。 AEM Screens Android™ プレーヤーは、業界標準の EMM AppConfig をサポートしており、リモートプロビジョニングが可能です。

  参照： [エンタープライズモビリティ管理を使用した Android™ プレーヤーの一括プロビジョニング](/help/user-guide/implementing-android-player.md#implementation) を参照してください。


### バグの修正 {#bug-fixes}

* `clientlib` と `asset hashes` の計算のパフォーマンスが向上しました。

* キャッシュが無効化されていない場合、スマート同期の移行によってプレーヤーが機能しなくなります。

* 割り当てに *OfflineConfig* が含まれる場合にオフラインキャッシュが作成されない問題を修正しました。

* 更新先 `Tizen` リファラーポリシーがクロスオリジンの場合に厳格なオリジン設定をサポートしていないことが原因で破損したプレーヤー。

* 割り当てられたチャネルのスケジュールの変更 *繰り返し* フィールドで UI が機能しませんでした。

* クエリの例外が発生して「オフラインコンテンツを更新」が正常に機能しない問題を修正しました。

* インタラクティブエクスペリエンスでのインタラクション中のトランジション間のタイムラグが修正されました。

* 設定更新リクエストが失敗したため、画面が空白になりました。

### リリースされている AEM Screens Player

AEM Screens 6.5 機能パック 7 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Linux®

#### AEM Screens Player のダウンロード 

最新のAEM Screens Player のダウンロードとバグ修正について詳しくは、以下を参照してください。 **[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/index.html)**.
