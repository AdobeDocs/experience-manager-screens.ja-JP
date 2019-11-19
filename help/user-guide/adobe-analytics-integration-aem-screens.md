---
title: AEM ScreensとのAdobe Analyticsの統合
seo-title: AEM ScreensとのAdobe Analyticsの統合
description: このページでは、AEM ScreensとAdobe Analyticsの統合について説明し、再生の証明を提供します。
seo-description: このページでは、AEM ScreensとAdobe Analyticsの統合について説明し、再生の証明を提供します。
uuid: 80d61af7-bf4d-46ca-a026-99a666c2e1a0
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: b1a0e00e-0368-42c9-8bcd-5f00b4d0990c
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# AEM ScreensとのAdobe Analyticsの統合 {#adobe-analytics-integration-with-aem-screens}

>[!CAUTION]
>
>このAEM Screens機能は、AEM 6.4.2機能パック2およびAEM 6.3.3機能パック4をインストールしている場合にのみ使用できます。

>これらのFeature packのいずれかにアクセスするには、アドビサポートに問い合わせてアクセスをリクエストする必要があります。 アクセス権が付与されると、パッケージ共有から機能パックをダウンロードできるようになります。
>
この節では、以下のトピックについて説明します。

* **概要**
* **建築の詳細**
* **プロパティの設定**

## 概要 {#overview}

***AEM Screensは*** 、Adobe Analyticsを活用し、場所に表示されるコンテンツを他のデータソースとクロスチャネル分析するなど、市場で独自のものを実現できます。

AEM Screensは、Adobe Analyticsとの初期設定の統合機能を提供し、再生の証明を提供します。

ここでは、AEM ScreensプロジェクトのAdobe Analyticsとの接続に関する以下の機能について説明します。

* デバイス別の再生の証明レポートを許可
* アセット別の再生の証明レポートを許可します
* すべてのプレーヤーイベントがキャプチャされ、タイムスタンプが設定されていることを確認します。
* 再生がネットワークに接続されていない場合に、すべてのプレーヤーイベントがローカルに保存されるようにします
* 再生イベントを時間の経過と共に追跡するフィードバックループの作成を可能にします。
* コンテンツ作成者が定義した成功条件に基づいて、システムがコンテンツとレイアウトを変更できるようにします

Adobe AnalyticsとAEM Screensの統合により、次の目標が適用され *ます*。

* デジタル署名の導入によるROIの実現
* Analyticsを統合して、使用状況情報の収集と分析を将来有効にする

## 建築の詳細 {#architectural-details}

AEM Screensのお客様は、どのコンテンツがいつ表示され、どの程度の期間（集計）表示されたかを把握する必要があります。 これは、サイネージソリューションの一般的な機能です。 独自の解析を作成する代わりに、AEM ScreensはAdobe Analyticsを利用し、場所に表示されるコンテンツを他のデータソースとクロスチャネル解析するなど、市場で独自の解析を実現します。

次のアーキテクチャ図は、Adobe AnalyticsとAEM Screensの統合を説明しています。

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## AEM ScreensでのAdobe Analyticsの有効化 {#enabling-adobe-analytics-in-aem-screens}

Adobe Analyticsの設定は、OSGiコンソールから設定できます。

次の図に **示すように、** Adobe Experience Manager Web Console Configurationに移動して、AEM Screens用のAdobe Analyticsを設定します。

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## 画面分析：有効化フロー {#screens-analytics-enablement-flow}

>[!CAUTION]
プロパティを設定する前に、Adobe Relationship Managerに連絡して、AEM Screensで使用する **Analytics API keyおよび** Analytics Projectを取得するためのチケットを作成してください **** 。

![]()

### プロパティの設定 {#configuring-the-properties}

>[!CAUTION]
プロパティを設定する前に、Adobe Relationship Managerに連絡して、AEM Screensで使用する **Analytics API keyおよび** Analytics Projectを取得するためのチケットを作成してください **** 。

次の表に、AEM Screens用のAdobe Analyticsを設定するためのプロパティとその説明を示します。

<table>
 <tbody>
  <tr>
   <td><strong>プロパティ</strong></td>
   <td><strong>説明</strong></td>
  </tr>
  <tr>
   <td><strong>Analytics URL</strong></td>
   <td>プレイヤーからの投稿分析データのURL<br /> </td>
  </tr>
  <tr>
   <td><strong>Analytics APIキー</strong></td>
   <td>Adobe Analyticsサーバーに対する認証用のAPIキー（アカウントマネージャーから提供）</td>
  </tr>
  <tr>
   <td><strong>Analyticsプロジェクト</strong></td>
   <td>データを受け取るようにAnalytics上で設定されたAEM Screensプロジェクト（アカウントマネージャーから提供）</td>
  </tr>
  <tr>
   <td><strong>環境</strong></td>
   <td><p>ステージ環境または実稼働環境。</p> <p><em>開発/ステージ</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> For Production <em></em> - https://cc-api-data.adobe.io/ingest/</p> </td>
  </tr>
  <tr>
   <td><strong>Analytics送信頻度</strong></td>
   <td>プレーヤーから分析データを送信する頻度（分）。 デフォルトでは、15分に設定されています。</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
デフォルトでは、**Analytics送信頻度**は15分です。

#### AEM ScreensでのAdobe Analytics Serviceの使用 {#using-adobe-analytics-service-in-aem-screens}

このシナリオは、ファームウェアのAnalyticsサービスからREST呼び出しを介してAnalytics APIを呼び出し、個々の使用例に固有のイベントを明示的に作成して送信し、カスタム開発チャネルから任意のカスタムメッセージをAnalyticsに送信できるようにします。

Analyticsイベントは、オフラインでindexedDBに保存され、後でチャンク化されてクラウドに送信されます。

>[!NOTE]
イベント用シーケンスおよび標準 ***デー*** タモデルの詳細については ***、「AEM Screens用のAdobe Analytics***&#x200B;の設定」を参照してください **[](configuring-adobe-analytics-aem-screens.md)**。

