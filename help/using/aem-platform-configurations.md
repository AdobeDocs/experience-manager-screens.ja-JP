---
title: AEM Platform 設定
description: ここでは、AEM Platform の設定について説明します
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 96%

---

# AEM Platform 設定 {#platform-configurations}

>[!NOTE]
>
>このアクティビティの典型的な関係者は、AEM 実装担当者です。

以下の節に従って、AEM Screens の基本を学び、AEM Platform 設定をセットアップします

## サーバーの設定 {#server-configurations}

サーバーの設定を行うには、[サーバーの設定](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration)を参照してください。

## オーサーとパブリッシュ {#author-publish}

[AEM Screens でのオーサーとパブリッシュの設定](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)を参照してください。

>[!NOTE]
>
>オーサーとパブリッシュが 1 つだけの場合は、[AEM Screens でのオーサーとパブリッシュの設定](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)内にある&#x200B;**オーサーでのレプリケーションエージェントの設定**&#x200B;で示されている手順に従うだけです。

## Dispatcher 設定 {#dispatcher-configurations}

Dispatcher は、Adobe Experience Manager のキャッシュおよびロードバランシングを管理するツールです。AEM Dispatcher を使用すると、AEM サーバーを攻撃から保護するのにも役立ちます。したがって、エンタープライズクラスの web サーバーと共に Dispatcher を使用することで、AEM インスタンスのセキュリティを高められます。

AEM Screens プロジェクトの Dispatcher を設定する際のガイドラインを説明している **[AEM Screens の Dispatcher 設定](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)**&#x200B;を参照してください。

## FFmpeg とビデオレンディションのインストール {#installing-ffmpeg}

適切な OS（通常は RHEL）の手順に従って、FFmpeg をインストールします。

1. EPEL と RPMFusion を有効にしてインストールする場合は、すべての gstreamer コーデックをインストールして、FFmpeg 変換のサポートを拡張できます。
1. AAC コーデックが試行用とマークされている場合、FFmpeg 変換は失敗します。この問題を回避するには、`-strict -2` をビデオプロファイルに追加します（AEM 6.3 では `/etc/dam/video`、`/libs/settings/dam/video in AEM 6.4` に移動しました）

   >[!NOTE]
   >
   >この `-strict -2` は、パラメーターのリストの最後のパラメーターである必要があります。さらに、AEM 6.4 では、[ビデオレンディション](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions)で言及しているように、*/libs/settings/dam/video* 配下のノードを */conf/global/settings/dam/video* にコピーする必要があります。
1. ビデオ変換が行われ、レンディションが作成されていることを確認します。

## パスワード制限 {#password-restrictions}

AMS インスタンスで AEM のパスワードポリシーを無効にする必要があります。または、Screens デバイスサービス *com.adobe.cq.screens.device.impl.DeviceService* を使用して、web コンソールでこれを設定することもできます。
詳しくは、[AEM Screens でのオーサーとパブリッシュの設定](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)内の&#x200B;**パスワード制限**&#x200B;の節を参照してください。

## 環境の設定 {#setting-up-environments}

お使いのバージョンの Adobe Experience Manager（AEM）用に、次のパッケージの最新バージョンをインストールして実行します。

* AEM サービスパック
* Screens 機能パック
* AEM 累積修正パック

上記に加えて、必要な開発用パッケージ（WCM コアコンポーネントなど）やサードパーティ製ツールキット（SAP Hybris など）を特定します。同じソフトウェアパッケージをローカルの開発環境にインストールします。QA サーバー、ステージサーバー、実稼動サーバーのすべてで同じ設定を使用するように、クライアントに指示します。サーバー設定が一致しないと、デプロイ時およびテスト時に問題が発生します。

>[!NOTE]
>
>AEM Screens の最新の機能パックをインストールするには、[リリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/aem-screens-introduction)を参照してください。

## ACL の設定 {#setting-up-acls}

「ACL の設定」では、各個人またはチームが独自のプロジェクトを処理できるようにプロジェクトを区別する方法について説明します。

詳しくは、[ACL の設定](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/administering/setting-up-acls)を参照してください。
