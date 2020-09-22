---
title: AEM プラットフォーム設定
seo-title: AEM プラットフォーム設定
description: ここでは、AEM プラットフォームの設定について説明します
seo-description: ここでは、AEM プラットフォームの設定について説明します
translation-type: ht
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: ht
source-wordcount: '522'
ht-degree: 100%

---

# AEM プラットフォーム設定 {#platform-configurations}

>[!NOTE]
>
>このアクティビティの典型的な関係者は、AEM 実装担当者です。

AEM Screens の使用を開始するには、まず、以下の節に従って AEM プラットフォームの設定をおこないます。

## サーバーの設定 {#server-configurations}

サーバーの設定をおこなうには、[サーバーの設定](https://helpx.adobe.com/jp/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration)を参照してください。

## オーサーとパブリッシュ {#author-publish}

オーサーとパブリッシュを設定するには、[AEM Screens でのオーサーとパブリッシュの設定](https://helpx.adobe.com/jp/experience-manager/6-5/screens/using/author-and-publish.html)を参照してください。

>[!NOTE]
>
>オーサーとパブリッシュが 1 つだけの場合は、[AEM Screens でのオーサーとパブリッシュの設定](https://helpx.adobe.com/jp/experience-manager/6-5/screens/using/author-and-publish.html)の&#x200B;**オーサー環境でのレプリケーションエージェントの設定**&#x200B;で示されている手順に従うだけです。

## Dispatcher の設定 {#dispatcher-configurations}

Dispatcher は、Adobe Experience Manager のキャッシュやロードバランシングを管理するツールです。AEM の Dispatcher は、AEM サーバーを攻撃から保護する目的にも役立ちます。したがって、Dispatcher をエンタープライズクラスの Web サーバーと組み合わせて使用すれば、AEM インスタンスのセキュリティを強化できます。

AEM Screens プロジェクトの Dispatcher を設定する際のガイドラインを説明している **[AEM Screens の Dispatcher 設定](https://helpx.adobe.com/jp/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)**&#x200B;を参照してください。

## FFmpeg とビデオレンディションのインストール {#installing-ffmpeg}

適切な OS（通常は RHEL）の手順に従って、FFmpeg をインストールします。

1. EPEL と RMFusion を有効にしてインストールする場合は、すべての gstreamer コーデックをインストールして、FFmpeg 変換のサポートを拡張できます。
1. AAC コーデックが試行用とマークされている場合、FFmpeg 変換は失敗します。この問題を回避するには、ビデオプロファイル（AEM 6.3 では /etc/dam/video、AEM 6.4 では /libs/settings/dam/video）に -strict -2 を追加します。
   >[!NOTE]
   >
   > なお、-strict -2 パラメーターは、パラメーターリストの最後に記述する必要があります。さらに、AEM 6.4 では、[ビデオレンディション](https://helpx.adobe.com/jp/experience-manager/6-5/screens/using/generating-renditions.html)で言及しているように、*/libs/settings/dam/video* 配下のノードを */conf/global/settings/dam/video* にコピーする必要があります。
1. ビデオ変換がおこなわれ、レンディションが作成されていることを確認します。

## パスワード制限 {#password-restrictions}

AMS インスタンスで AEM のパスワードポリシーを無効にする必要があります。または、Screens デバイスサービス *com.adobe.cq.screens.device.impl.DeviceService* を使用して、Web コンソールでこれを設定することもできます。詳しくは、[AEM Screens でのオーサーとパブリッシュの設定](https://helpx.adobe.com/jp/experience-manager/6-5/screens/using/author-and-publish.html)の&#x200B;**パスワード制限**&#x200B;の節を参照してください。

## 環境の設定 {#setting-up-environments}

お使いのバージョンの Adobe Experience Manager（AEM）用に、次のパッケージの最新バージョンをインストールして実行します。

* AEM サービスパック
* Screens 機能パック
* AEM 累積修正パック

上記に加えて、必要な開発用パッケージ（WCM コアコンポーネントなど）やサードパーティ製ツールキット（SAP Hybris など）を特定します。同じソフトウェアパッケージをローカルの開発環境にインストールします。QA サーバー、ステージサーバー、実稼働サーバーのすべてで同じ設定を使用するように、クライアントに指示します。サーバー設定が一致しないと、デプロイ時およびテスト時に問題が発生します。

>[!NOTE]
>
>AEM Screens の最新の機能パックをインストールするには、[リリースノート](https://helpx.adobe.com/jp/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js)を参照してください。

## ACL の設定 {#setting-up-acls}

「ACL の設定」では、各個人またはチームが独自のプロジェクトを処理できるようにプロジェクトを区別する方法について説明します。

詳しくは、[ACL の設定](https://helpx.adobe.com/jp/experience-manager/6-5/screens/using/setting-up-acls.html)を参照してください。
