---
title: AEM プラットフォーム設定
description: ここでは、AEM Platform の設定について説明します
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 44%

---

# AEM Platform 設定  {#platform-configurations}

>[!NOTE]
>
>このアクティビティの典型的な関係者は、AEM 実装担当者です。

以下の節に従って、AEM Screensの基本を学び、AEM Platform 設定をセットアップします

## サーバー設定 {#server-configurations}

サーバ構成をセットアップするには、を参照してください。 [サーバー設定](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration).

## オーサー – パブリッシュ {#author-publish}

参照： [AEM Screensでのオーサーとパブリッシュの設定](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

>[!NOTE]
>
>オーサーとパブリッシュが 1 つしかない場合は、の手順にのみ従います **オーサー環境へのレプリケーションエージェントのセットアップ** 。対象： [AEM Screensでのオーサーとパブリッシュの設定](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish) ページ。

## Dispatcher 設定 {#dispatcher-configurations}

Dispatcher は、Adobe Experience Managerのキャッシュおよびロードバランシングツールです。 AEM Dispatcher を使用すると、AEM サーバーを攻撃から保護するのにも役立ちます。したがって、エンタープライズクラスの web サーバーと共に Dispatcher を使用することで、AEM インスタンスのセキュリティを高められます。

参照： **[AEM Screensの Dispatcher 設定](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)** AEM Screens プロジェクトの Dispatcher を設定する際のガイドラインについて説明します。

## FFMpeg とビデオレンディションのインストール {#installing-ffmpeg}

適切な OS（通常は RHEL）の手順に従って、FFmpeg をインストールします。

1. EPEL と RPMFusion を有効にしてインストールする場合は、すべての gstreamer コーデックをインストールして、FFmpeg 変換のサポートを拡張できます。
1. AAC コーデックが実験的としてマークされている場合、ffmpeg 変換は失敗します。 これを回避するには、次を追加します `-strict -2` をビデオプロファイル（AEM 6.3 では/etc/dam/video）に追加し、AEM 6.4 では/libs/settings/dam/video に移動しました。

   >[!NOTE]
   >
   >この `-strict -2` は、パラメーターのリストの最後のパラメーターである必要があります。 また、AEM 6.4 では、の下にノードをコピーする必要があります */libs/settings/dam/video* 対象： */conf/global/settings/dam/video* ～で述べたように [ビデオレンディション](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions).
1. ビデオ変換がおこなわれ、レンディションが作成されていることを確認します。

## パスワード制限 {#password-restrictions}

AEMのパスワードポリシーは、AMS インスタンスで無効にする必要があります。 これは、Screens デバイスサービスを使用して web コンソールで交互に設定できます *com.adobe.cq.screens.device.impl.DeviceService*
参照： **パスワード制限** のセクション[AEM Screensでのオーサーとパブリッシュの設定](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)

## 環境のセットアップ {#setting-up-environments}

お使いのバージョンの Adobe Experience Manager（AEM）用に、次のパッケージの最新バージョンをインストールして実行します。

* AEM サービスパック
* Screens 機能パック
* AEM 累積修正パック

上記に加えて、必要な開発用パッケージ（WCM コアコンポーネントなど）やサードパーティ製ツールキット（SAP Hybris など）を特定します。ローカル開発環境に同じソフトウェアパッケージをインストールします。 QA サーバー、ステージサーバー、実稼働サーバーのすべてで同じ設定を使用するように、クライアントに指示します。サーバー設定が一致しないと、デプロイおよびテスト時に問題が発生します。

>[!NOTE]
>
>AEM Screensの最新の機能パックをインストールするには、以下を参照してください。 [リリースノート](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/aem-screens-introduction).

## ACL の設定 {#setting-up-acls}

「ACL の設定」では、各個人またはチームが独自のプロジェクトを処理できるようにプロジェクトを区別する方法について説明します。

詳しくは、[ACL の設定](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/setting-up-acls)を参照してください。
