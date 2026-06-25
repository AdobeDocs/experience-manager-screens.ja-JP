---
title: テストと品質保証
description: AEM Screens のテストと品質保証については、ベストプラクティスガイドを参照してください。
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
TQID: https://experienceleague.adobe.com/So83gHv7n21zhdoCdWHVf0yswyQuSr1hLWmCA7uHSiE
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 376
ht-degree: 70%

---

# テストと品質保証 {#testing-quality}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

>[!NOTE]
>このアクティビティの典型的な関係者は、オーディオビデオインテグレーターです。

デジタルサイネージネットワークの導入が近づいたら、すべてのハードウェアコンポーネント、すべてのソフトウェアコンポーネント、すべてのネットワークコンポーネントを含む、ネットワークのあらゆる要素に対応するテストおよびQA プランを作成します。
フェーズでは、テストシステム全体を構築し、完全にテストする必要があります。

事前に定義した KPI をすべて特定し、KPI に照らして成果物を測定するチェックリストを作成してください。

>[!NOTE]
>
>この段階は、インストールおよびユーザーガイドを作成するためのツールとしても使用します。 どちらも後で機器に同梱し、将来の参照用に現場に保管できます。

次の要素を考慮する必要があります。

## &#x200B;1. 機械的な検討事項 {#mechanical-considerations}

以下の機械に関する考慮事項を推奨します。

* ディスプレイの取り付け
* プレイヤーの取り付け
* 換気
* 周辺機器の接続
* ケーブル管理
* デバイスネットワーク

## &#x200B;2. ソフトウェアの考慮事項 {#software-considerations}

以下のソフトウェアに関する考慮事項を推奨します。

* デバイスの登録
* メディアの公開
* 再生
* データベースの依存関係（定義済み）


## &#x200B;3. デバイス管理の考慮事項 {#device-management-considerations}

AEM Screens には、Screens Player アプリケーションエンドポイントを管理するためのデバイスコントロールセンターモジュールが含まれています。

これは、Screens player アプリケーションがインストールされ、AEMのインスタンスに登録されている&#x200B;*player* ハードウェアデバイスを指します。
このモジュールを使用すると、次のことが可能になります。

1. プレーヤーアプリケーションエラーログの監視
1. リモートスクリーンショットの管理
1. コンテンツダウンロードの管理
1. アプリケーションの再起動に関する問題の管理

***デバイスコントロールセンター***&#x200B;について詳しくは、**AEM Screens ユーザーガイド**&#x200B;の[デバイスコントロールセンターのトラブルシューティング](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens)を参照してください。

>[!CAUTION]
>
>デバイスコントロールセンターは次の用途には使用しないでください。
>
>* 新しいバージョンのプレイヤーアプリケーションのインストール
>* システムレベルのリソースの監視
>* システムレベルエラーのトラブルシューティング
>* リモートデスクトップによる介入の許可


>[!NOTE]
>
> アドビでは、すべてのデプロイメントで、専用のサードパーティのデバイス管理プラットフォームを使用することをお勧めします。

選択するプラットフォームは、***対象オペレーティングシステム***、***プロジェクト要件***、***エンドポイント数***&#x200B;など、いくつかの要因によって異なります。

次に例を示します。

* Google Chrome デバイス管理
* TeamViewer
* AirWatch
* `42Gears`
* オーディオビデオインテグレーター独自のミドルウェア
