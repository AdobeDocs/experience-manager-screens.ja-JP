---
title: Adobe Analytics と AEM Screens の統合
description: 標準で利用できる、AEM Screens と Adobe Analytics の統合について説明し、提供される再生検証機能についても紹介します。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
docset: aem65
feature: Administering Screens
role: Admin, Developer
level: Intermediate
exl-id: 92c8c42b-7c1e-4d4a-8662-18c99666e9c6
TQID: https://experienceleague.adobe.com/4Qdx25kNW3IszlXshNPGYGMJNE9E2QQlndLjJICDrI4
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 739
ht-degree: 93%

---

# Adobe Analytics と AEM Screens の統合 {#adobe-analytics-integration-with-aem-screens}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

>[!CAUTION]
>
>この AEM Screens 機能は、AEM 6.4.2 機能パック 2 の最小バージョンまたは AEM 6.3.3 機能パック 4 がインストールされている場合にのみ使用できます。 AEM Screens Cloud Service のお客様の場合、Screens Cloud でAdobe Analytics を有効にするには、アドビリレーションシップマネージャーにお問い合わせください。

>[!NOTE]
>
>このいずれかの機能パックにアクセスするには、アドビサポートに利用申請を行います。 AEM Screens の最新の機能パックは、Adobe ID を使用して[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/ja/aem.html)からダウンロードできます。

ここでは、以下のトピックについて説明します。

* **概要**
* **アーキテクチャの詳細**
* **プロパティの設定**

## 概要 {#overview}

***AEM Screens*** で Adobe Analytics を使用することにより、特定の場所に表示されるコンテンツと他のデータソースとの関連性を探るのに役立つ、ユニークなクロスチャネル分析を実現できます。

AEM Screens は、標準で Adobe Analytics と統合されており、再生検証機能を提供します。

ここでは、AEM Screens プロジェクトと Adobe Analytics の連携に関係する以下の機能について説明します。

* デバイス別の再生検証レポートが可能
* アセット別の再生検証レポートが可能
* すべてのプレーヤーイベントをキャプチャしタイムスタンプを設定できる
* 再生がネットワークに接続されていない場合、すべてのプレーヤーイベントをローカルに保存できる
* フィードバックループを作成して再生イベントを経時的に追跡できる
* コンテンツ作成者が定義した成功条件に基づいてシステムがコンテンツやレイアウトを編集できる

Adobe Analytics と AEM Screens の統合により、*次の*&#x200B;目標を達成できます。

* デジタルサイネージの実装による ROI の実現
* 使用状況情報の収集と分析を将来可能にする基盤として Analytics を統合

## アーキテクチャの詳細 {#architectural-details}

AEM Screens の顧客は、どのコンテンツが、いつ、どのくらいの時間（集計）表示されたかを把握したいと考えています。 この要求は、サイネージソリューションの一般的な機能です。 AEM Screens では、別の分析アプリケーションを作成するのではなく、Adobe Analytics を使用します。 この組み合わせにより、特定の場所に表示されるコンテンツと他のデータソースとの関連性を探るのに役立つユニークなクロスチャネル分析を実現できます。

次のアーキテクチャ図では、Adobe Analytics と AEM Screens の統合について説明しています。

![screen_shot_2018-09-12at85611am](assets/screen_shot_2018-09-12at85611am.png)

## AEM Screens での Adobe Analytics の有効化 {#enabling-adobe-analytics-in-aem-screens}

Adobe Analytics の設定は、OSGi コンソールから設定できます。

**Adobe Experience Manager web コンソール設定**&#x200B;に移動すると、AEM Screens 用に Adobe Analytics を設定できます。

![screen_shot_2018-09-04at25550pm](assets/screen_shot_2018-09-04at25550pm.png)

## Screens 用 Analytics：有効化フロー {#screens-analytics-enablement-flow}

>[!CAUTION]
>
>プロパティを設定する前に、アドビのリレーションシップマネージャーに連絡して、AEM Screens で使用する **Analytics API キー**&#x200B;と **Analytics プロジェクト**&#x200B;を取得するためのチケットを作成してください。

### プロパティの設定 {#configuring-the-properties}

>[!CAUTION]
>
>プロパティを設定する前に、アドビのリレーションシップマネージャーに連絡して、AEM Screens で使用する **Analytics API キー**&#x200B;と **Analytics プロジェクト**&#x200B;を取得するためのチケットを作成してください。

Adobe Analytics を AEM Screens 用に設定するためのプロパティとその説明を次の表に示します。

<table>
 <tbody>
  <tr>
   <td><strong>プロパティ</strong></td>
   <td><strong>説明</strong></td>
  </tr>
  <tr>
   <td><strong>Analytics URL</strong></td>
   <td>プレーヤーから得られる分析データを投稿するための URL。 <br>
   開発／ステージング環境の場合</em> - https://cc-api-data-stage.adobe.io/ingest/<br /> <em>プロダクション環境の場合</em> - https://cc-api-data.adobe.io/ingest/<br /> <br /></td>
  </tr>
  <tr>
   <td><strong>Analytics API キー</strong></td>
   <td>Adobe Analytics サーバーに対して認証をおこなうための API キー（アカウントマネージャーから提供される）。</td>
  </tr>
  <tr>
   <td><strong>Analytics プロジェクト</strong></td>
   <td>データを受け取るように Analytics 上で設定された AEM Screens プロジェクト（アカウントマネージャーから提供される）。</td>
  </tr>
  <tr>
   <td><strong>環境</strong></td>
   <td><p>ステージング環境または本番環境（「ステージング」か「本番」のいずれかを選択）。</p></td>
  </tr>
  <tr>
   <td><strong>分析送信頻度</strong></td>
   <td>プレーヤーから分析データを送信する頻度（分）。 デフォルトでは 15 分に設定されています。</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>デフォルトでは、**分析送信頻度**&#x200B;は 15 分です。

#### AEM Screens での Adobe Analytics サービスの使用 {#using-adobe-analytics-service-in-aem-screens}

このシナリオでは、ファームウェアの分析サービスからの REST 呼び出しを通じて Analytics API を呼び出します。 また、AEM Screens コアコンポーネントも実装して、特定のユースケースに固有のイベントを作成および送信します。 これらすべての機能により、カスタム開発されたチャネルからカスタムメッセージを Analytics に送信できる拡張性が実現します。

Analytics イベントは、IndexedDB にオフラインで保存され、後でまとめてクラウドに送信されます。

>[!NOTE]
>
>***シーケンス***&#x200B;と&#x200B;***イベントの標準データモデル***&#x200B;について詳しくは、**[AEM Screens 用の Adobe Analytics の設定](configuring-adobe-analytics-aem-screens.md)**&#x200B;を参照してください。
