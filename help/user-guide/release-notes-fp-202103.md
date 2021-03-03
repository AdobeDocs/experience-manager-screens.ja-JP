---
title: 機能パック 202103 のリリースノート
description: このページでは、機能パック202103のリリースノートが強調表示されます。
translation-type: tm+mt
source-git-commit: 34f93df3fa212eaae713b0c8686d95beeb0c7b67
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 40%

---


# 機能パック 202103 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>最新バージョンの Adobe Experience Manager（AEM）にアップグレードすることをお勧めします。Screens では、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供しています。

## 利用可能場所 {#availability}

AEM Screens は、AEM 6.5 機能パック 7 をリリースしました。

Adobe ID を使用して、AEM Screens 6.5.7 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して「**AEM 6.5 Screens FP7**」というタイトルが付いた最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens機能パック202103のリリース日は2021年3月8日です。

### 新機能 {#what-is-new}

* **AEM Screens一括登録と割り当て**

   何千ものプレーヤーを手動で登録すると非常に面倒で、時間とコストがかかります。 このプロセスを簡単にするために、一括登録機能を使用して、設定ファイルまたはMobile Device Management(MDM)ソリューションを介してプレイヤーにプロビジョニングできるAEMの事前共有キーを指定できます。

* **Enterprise Mobility Managementを使用したAndroid Playerの一括プロビジョニング**

   Androidプレーヤーを一括してデプロイする場合、すべてのプレーヤーをAEMに手動で登録するのは面倒です。 VMWare Airwatch、MobileIron、Samsung KnoxなどのEMM(Enterprise Mobility Management)ソリューションを使用して、展開のプロビジョニングと管理をリモートで行うことを強くお勧めします。 AEM ScreensAndroidプレイヤーは、業界標準のEMM AppConfigをサポートしており、リモートプロビジョニングが可能です。


### バグ修正 {#bug-fixes}

* `clientlib`と`asset hashes`の計算のパフォーマンスが向上しました。

* キャッシュが無効化されない場合、SmartSyncの移行によってプレイヤーが中断されます。

* 割り当てに&#x200B;*OfflineConfig*&#x200B;が含まれる場合、オフラインキャッシュは作成されませんでした。

* 転送者ポリシーの接触チャネル時に厳密に接触チャネルすることがサポートされていないため、Tizen Playerの問題に対する更新が行われました。

* 割り当てられたチャネルのスケジュール「繰り返し」フィールドを変更すると、UIが無効になっていた問題を修正しました。

* クエリの例外が発生してオフラインコンテンツの更新に失敗していた問題を修正しました。

* キャッシュが無効化されなかった場合、SmartSyncの移行がプレイヤーを中断していました


### リリースされている AEM Screens Player {#released-aem-screens-players}

AEM Screens 6.5 機能パック 7 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Android
* Tizen
* Linux

#### AEM Screens Player のダウンロード {#aem-screens-player-downloads}

最新の AEM Screens Player のダウンロードとバグ修正について詳しくは、**[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/index.html)**&#x200B;を参照してください。
