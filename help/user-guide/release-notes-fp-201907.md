---
title: 機能パック 201907 のリリースノート
seo-title: Release Notes for Feature Pack 201907
description: 2019 年 7 月 31 日にリリースされた AEM Screens 機能パック 201907 について説明します。
seo-description: Follow this page to get information for AEM Screens Feature Pack 201907 released on July 31, 2019.
uuid: e5349c92-d532-4f04-a757-7c4545cdb074
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: release-notes
content-type: reference
discoiquuid: 826d1599-02d1-4d24-b15d-26c1ffee36a2
docset: aem65
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 6a05a014-aedf-4261-849d-abf1ce070964
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 84%

---

# 機能パック 201907 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>
>最新バージョンの Adobe Experience Manager（AEM）にアップグレードすることをお勧めします。Screens では、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供しています。

AEM 6.4.5 機能パック 5 および AEM 6.5.1 機能パック 1 向けの AEM Screens がリリースされました。詳細は以下のとおりです。

## リリース日 {#release-date}

AEM Screens 機能パック 201907 のリリース日は 2019 年 7 月 31 日です。

### 新機能 {#what-s-new}

* **AEM Screens チャネルのアセット変更を駆動するデータトリガー**

プレーヤーは、緊急システムで発生したイベントを受信すると、緊急情報を表示するチャネルに切り替わります。緊急事態が終わるまで、そのチャネルだけが再生されます。

参照： [緊急チャネル](emergency-channel.md) 実装のユースケース。

* 非同期コンポーネントのターゲティングが有効

AEM Screens プロジェクトで使用されるアセットに対してターゲティングを有効にできるようになりました。

AEM Screens プロジェクトでアセットのターゲティングを有効にする方法については、 [AEM Screensでの ContextHub の設定](configuring-context-hub.md).

AEM Screens プロジェクトに ContextHub を設定したら、以下の様々な使用例を通じて、データでトリガーされるアセットが様々な業界でいかに重要な役割を果たしているかを理解できます。

**[小売店向けの在庫に応じたアクティベーション](retail-inventory-activation.md)**

**[旅行センター向けの気温に応じたアクティベーション](local-temperature-activation.md)**

**[接客業向けの予約状況に応じたアクティベーション](hospitality-reservation-activation.md)**

* **更新ハンドラーの機能改善**

更新ハンドラーでは、エクスペリエンスフラグメントを解析し、関連する画像、ビデオ、製品を収集するようになりました。

* **ローンチ**

ローンチにより、コンテンツ作成者はチャネルの将来バージョンを作成できます。ローンチを利用して、作成者はローンチの各チャネルをプレビューでき、レビュー要求も開始できます。承認者グループは通知を受け取り、要求を承認または拒否できます。ライブ日付に達すると、コンテンツがデバイスで再生されます。参照： [ローンチ](launches.md) を参照してください。

* **エクスペリエンスフラグメントでのオフライン設定**

Screens エクスペリエンスフラグメントの設定時に、オフライン設定（クライアント側ライブラリや静的ファイル）を追加できるようになりました。参照： [エクスペリエンスフラグメントの使用](experience-fragments-in-screens.md) を参照してください。

### リリースされている AEM Screens Player {#released-aem-screens-players}

AEM 6.4.5 機能パック 5 および AEM 6.5.1 機能パック 1 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Android

#### AEM Screens Player のダウンロード   {#aem-screens-player-downloads}

最新のAEM Screens Player のダウンロードとバグ修正について詳しくは、以下を参照してください。 [AEM Screens Player のダウンロード](https://download.macromedia.com/screens/).
