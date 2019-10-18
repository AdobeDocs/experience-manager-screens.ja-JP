---
title: AEMプラットフォーム設定
seo-title: AEMプラットフォーム設定
description: このページでは、AEMプラットフォームの設定について説明します。
seo-description: このページでは、AEMプラットフォームの設定について説明します。
translation-type: tm+mt
source-git-commit: 5c83a2b59769dfd3736a830f7d7d3cc35137c182

---

# AEM Platform Configurations  {#platform-configurations}

>[!NOTE]
>
>このアクティビティの一般的なステークホルダーは、AEM実装者です。

AEM Screensを使用する前にAEMプラットフォームの設定を行うには、次の節に従ってください。

## サーバーの設定 {#server-configurations}

サーバー設定を設定するには、「サーバー設定」を参 [照してください](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration)。

## 作成者 — 発行 {#author-publish}

作成者と公開を設定する方法については、「AEM画面で [の作成者と公開の設定」を参照してください。](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
> 発行者が1人だけの場合は、「AEM画面での作成者と発行の設定」の「作成者での複製エージェントの設定 **** 」 [](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html) の手順に従うだけです。

## Dispatcher の設定 {#dispatcher-configurations}

Dispatcher は、Adobe Experience Manager のキャッシュやロードバランシングを管理するツールです。AEM の Dispatcher は、AEM サーバーを攻撃から保護する目的にも役立ちます。したがって、Dispatcher をエンタープライズクラスの Web サーバーと組み合わせて使用すれば、AEM インスタンスのセキュリティを強化できます。

AEM Screensプロジェクトのディスパ **[ッチャー設定のガイドラインについては](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** 、「AEM Screensのディスパッチャー設定」を参照してください。

## FFMpegとビデオレンディションのインストール {#installing-ffmpeg}

適切なOS（通常はRHEL）の手順に従ってFFMpegをインストールします。

1. EPELとRMFusionを有効にしてインストールする場合は、すべてのgstreamerコーデックをインストールして、FFmpeg変換のサポートを拡張できます
1. AACコーデックが試験的とマークされている場合、ffmpeg変換は失敗します。 この問題を回避するには、ビデオプロファイル（AEM 6.3では/etc/dam/video、AEM 6.4では/libs/settings/dam/video）に —strict -2を追加します。
   >[!NOTE]
   >
   > -strict -2は、パラメーターのリストの最後のパラメーターである必要があります。 また、AEM 6.4では、ビデオレンディションで説明されているように、 */libs/settings/dam/video* の下のノードを/conf/global/settings/dam/video *にコピーする必要が* あります [](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html)。
1. ビデオの変換が行われ、レンディションが作成されていることを確認します。

## パスワードの制限 {#password-restrictions}

AEMのパスワードポリシーをAMSインスタンスで無効にする必要があります。 Webコンソールで、Screensデバイスサービスcom.adobe.cq.screens.device.impl.DeviceService *「AEM Screensでの作成者と公開の設定」の「パスワードの制限***** 」セクション[を使用して、これを設定することもできます。](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)

## Setting up the Environments {#setting-up-environments}

お使いのバージョンのAdobe Experience Manager(AEM)用に、次のパッケージの最新バージョンをインストールして実行します。

* AEM Service Pack
* 画面機能パック
* AEM Cumulative Fix Pack

上記に加えて、必要な開発パッケージ（WCM Corecomponentsなど）やサードパーティのツールキット（SAP Hybrisなど）を特定します。
ローカル開発環境に同じソフトウェアパッケージをインストールします。 すべてのQA、Stage、実稼働サーバーで同じ設定を採用するようにクライアントに指示します。 サーバー設定が一致しない場合は、展開およびテスト時に問題が発生します。

>[!NOTE]
> 最新のAEM Screens機能パックをインストールするには、リリースノートを参 [照してください](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js)。

## ACL の設定 {#setting-up-acls}

ACLの設定では、各個人またはチームが独自のプロジェクトを処理できるように、プロジェクトを分類する方法について説明します。

詳細は、 [「ACLの設定](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) 」を参照してください。
