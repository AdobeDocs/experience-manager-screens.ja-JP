---
title: 機能パック 201907 のリリースノート
description: 2019 年 7 月 31 日にリリースされたAEM Screens機能パック 201907 について説明します。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: release-notes
content-type: reference
docset: aem65
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 6a05a014-aedf-4261-849d-abf1ce070964
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 44%

---

# 機能パック 201907 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>
>Adobeでは、最新バージョンのAdobe Experience Manager（AEM）にアップグレードすることをお勧めします。 AEM Screensは、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供します。

AEM 6.4.5 機能パック 5 および AEM 6.5.1 機能パック 1 向けの AEM Screens がリリースされました。詳細は以下のとおりです。

## リリース日 {#release-date}

AEM Screens 機能パック 201907 のリリース日は 2019 年 7 月 31 日です。

### 新機能 {#what-s-new}

* **AEM Screens チャネルのアセット変更を駆動するデータトリガー**

プレイヤは、緊急情報を表示するチャンネルに切り替える。 緊急システムは、イベントを受け取ると、この情報を送信します。 緊急事態が終わるまで、そのチャネルだけが再生されます。


参照： [緊急チャネル](emergency-channel.md) 実装のユースケース。

* 非同期コンポーネントのターゲティングが有効

AEM Screens プロジェクトで使用されるアセットに対して、ターゲティングを有効にできるようになりました。

AEM Screens プロジェクトでアセットのターゲティングを有効にする方法について詳しくは、 [AEM Screensでの ContextHub の設定](configuring-context-hub.md).

AEM Screens プロジェクトに ContextHub を設定したら、以下の様々な使用例を通じて、データでトリガーされるアセットが様々な業界でいかに重要な役割を果たしているかを理解できます。

**[小売店向けの在庫に応じたアクティベーション](retail-inventory-activation.md)**

**[旅行センター向けの気温に応じたアクティベーション](local-temperature-activation.md)**

**[接客業向けの予約状況に応じたアクティベーション](hospitality-reservation-activation.md)**

* **更新ハンドラーの機能改善**

更新ハンドラーは、エクスペリエンスフラグメントを解析し、それに関連付けられたすべての画像、ビデオまたは製品を収集するようになりました。

* **ローンチ**

ローンチを使用すると、コンテンツ作成者はチャネルの今後のバージョンを作成できます。 ローンチを使用すると、作成者はローンチ内の各チャネルをプレビューし、レビューのリクエストを開始できます。 承認者グループは通知を受け取り、リクエストを承認または却下できます。 ライブ日付に達すると、コンテンツがデバイスで再生されます。参照： [ローンチ](launches.md) を参照してください。

* **エクスペリエンスフラグメントでのオフライン設定**

Screens エクスペリエンスフラグメントの設定時に、オフライン設定（クライアント側ライブラリと静的ファイル）を追加できるようになりました。 参照： [エクスペリエンスフラグメントの使用](experience-fragments-in-screens.md) を参照してください。

### リリースされている AEM Screens Player

AEM 6.4.5 機能パック 5 および AEM 6.5.1 機能パック 1 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Android™

#### AEM Screens Player のダウンロード 

最新のAEM Screens Player のダウンロードとバグ修正について詳しくは、以下を参照してください。 [AEM Screens Player のダウンロード](https://download.macromedia.com/screens/).
