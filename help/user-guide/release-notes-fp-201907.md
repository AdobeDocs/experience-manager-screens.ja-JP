---
title: 機能パック 201907 のリリースノート
description: 2019年7月31日にリリースされた AEM Screens 機能パック 201907 について説明します。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: release-notes
content-type: reference
docset: aem65
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 6a05a014-aedf-4261-849d-abf1ce070964
TQID: https://experienceleague.adobe.com/fbTrzAj52dW2JuRe-6InIkh-dT52Au9pGgoAEjR7WW8
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 378
ht-degree: 100%

---

# 機能パック 201907 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>
>最新バージョンの Adobe Experience Manager（AEM）にアップグレードすることをお勧めします。 AEM Screens では、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供しています。

AEM Screens は、AEM 6.4.5 機能パック 5 および AEM 6.5.1 機能パック 1 をリリースしました。詳細は以下のとおりです。

## リリース日 {#release-date}

AEM Screens 機能パック 201907 のリリース日は 2019年7月31日（PT）です。

### 新機能 {#what-s-new}

* **AEM Screens チャネルのアセット変更を駆動するデータトリガー**

プレーヤーは、緊急情報を表示するチャネルに切り替わります。 緊急システムは、イベントを受け取ると、この情報を送信します。 緊急事態が終わるまで、そのチャネルだけが再生されます。


実装については、[緊急チャネル](emergency-channel.md)のユースケースを参照してください。

* **非同期コンポーネントのターゲティングが有効に

AEM Screens プロジェクトで使用されるアセットに対してターゲティングを有効にできるようになりました。

AEM Screens プロジェクトでアセットのターゲティングを有効にする方法について詳しくは、[AEM Screens での ContextHub の設定](configuring-context-hub.md)を参照してください。

AEM Screens プロジェクトに ContextHub を設定したら、以下の様々な使用例に従って、データでトリガーされるアセットが様々な業界でいかに重要な役割を果たしているかを理解できます。

**[小売店向けの在庫に応じたアクティベーション](retail-inventory-activation.md)**

**[旅行センター向けの気温に応じたアクティベーション](local-temperature-activation.md)**

**[接客業向けの予約状況に応じたアクティベーション](hospitality-reservation-activation.md)**

* **更新ハンドラーの機能改善**

更新ハンドラーでは、エクスペリエンスフラグメントを解析し、関連する画像、ビデオ、製品を収集するようになりました。

* **ローンチ**

ローンチを使用すると、コンテンツ作成者はチャネルの今後のバージョンを作成できます。 ローンチを利用して、作成者はローンチの各チャネルをプレビューでき、レビューリクエストも開始できます。 承認者グループは通知を受け取り、リクエストを承認または却下できます。 ライブ日付に達すると、コンテンツがデバイスで再生されます。
詳しくは、[ローンチ](launches.md)を参照してください。

* **エクスペリエンスフラグメントでのオフライン設定**

Screens エクスペリエンスフラグメントの設定時に、オフライン設定（クライアントサイドライブラリや静的ファイル）を追加できるようになりました。 詳しくは、[エクスペリエンスフラグメントの使用](experience-fragments-in-screens.md)を参照してください。

### リリースされている AEM Screens Player

AEM 6.4.5 機能パック 5 および AEM 6.5.1 機能パック 1 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Android™

#### AEM Screens Player のダウンロード

最新の AEM Screens Player のダウンロードとバグ修正について詳しくは、[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/)を参照してください。
