---
title: 機能パック 202103 のリリースノート
description: このページでは、機能パック202103のリリースノートが強調表示されます。
translation-type: tm+mt
source-git-commit: 76d03e1b0232c5d6eca0a3088453982c5c142f1f
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 36%

---


# 機能パック 202103 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>最新バージョンの Adobe Experience Manager（AEM）にアップグレードすることをお勧めします。Screens では、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供しています。

## 利用可能場所 {#availability}

AEM Screens は、AEM 6.5 機能パック 7 をリリースしました。

Adobe ID を使用して、AEM Screens 6.5.7 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して「**AEM 6.5 Screens FP7**」というタイトルが付いた最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens機能パック202103のリリース日は2021年3月6日です。

### 新機能 {#what-is-new}

* **AEM Screens選手の自動登録**

   何千ものプレーヤーを手動で登録すると非常に面倒で、時間とコストがかかります。 このプロセスを簡単にするために、一括登録機能を使用して、設定ファイルまたはMobile Device Management(MDM)ソリューションを介してプレイヤーにプロビジョニングできるAEMの事前共有キーを指定できます。

   詳しくは、[プレイヤーの自動登録](/help/user-guide/auto-registration-players.md)を参照してください。


* **Enterprise Mobility Managementを使用したAndroid Playerの一括プロビジョニング**

   Androidプレーヤーを一括してデプロイする場合、すべてのプレーヤーをAEMに手動で登録するのは面倒です。 VMWare Airwatch、MobileIron、Samsung KnoxなどのEMM(Enterprise Mobility Management)ソリューションを使用して、展開のプロビジョニングと管理をリモートで行うことを強くお勧めします。 AEM ScreensAndroidプレイヤーは、業界標準のEMM AppConfigをサポートしており、リモートプロビジョニングが可能です。

   詳しくは、Enterprise Mobility Managementを使用したAndroid Playerの一括プロビジョニング](/help/user-guide/using-emm-bulkprovision-android-player.md)を参照してください。[


### バグ修正 {#bug-fixes}

* `clientlib`と`asset hashes`の計算のパフォーマンスが向上しました。

* キャッシュが無効化されない場合、SmartSyncの移行によってプレイヤーが中断されます。

* 割り当てに&#x200B;*OfflineConfig*&#x200B;が含まれる場合、オフラインキャッシュは作成されませんでした。

* 転送者ポリシーが接触チャネル時に厳密に接触チャネルされないために壊れたTizen Playerの更新がサポートされていません。

* 割り当てられたチャネルのスケジュール&#x200B;*Repeats*&#x200B;フィールドが変更されると、UIが無効になっていました。

* クエリの例外が発生してオフラインコンテンツの更新に失敗していた問題を修正しました。

* インタラクティブエクスペリエンスでのインタラクション中のトランジション間の時間のずれが修正されました。

* 構成更新要求の失敗により、空白の画面が発生していました。

### リリースされている AEM Screens Player {#released-aem-screens-players}

AEM Screens 6.5 機能パック 7 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Tizen
* Linux

#### AEM Screens Player のダウンロード {#aem-screens-player-downloads}

最新の AEM Screens Player のダウンロードとバグ修正について詳しくは、**[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/index.html)**&#x200B;を参照してください。
