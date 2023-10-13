---
title: Cloud Player の実装
seo-title: Implementing Cloud Player
description: このページでは、Cloud Player の実装について説明します。
seo-description: Follow  this page to learn about the implementation of the Cloud Player.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
source-git-commit: 718ef76b620accd7096be2e4b7ac53658cb7fce7
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# Cloud Player の実装  {#implementing-cloud-player}

この節では、Cloud Player の実装方法について説明します。

>[!NOTE]
>
>Cloud Player の互換性を使用するには、様々なデバイスで一貫したパフォーマンスを実現するために、PWAがサポートされている最新のブラウザーが必要です。

## Cloud Player のインストール {#installing-cloud-player}

Cloud Player のインストールは、プラットフォームによって異なる場合があります。 一般に、最新のブラウザーを持つプラットフォームでは、次の手順に従って Cloud Player アプリケーションを実行できます。

1. ブラウザーを開き、 [Cloud Player URL](https://player.adobescreens.com) をクリックします。
1. ブラウザーは、Cloud Player がインストール可能かどうかを確認し、アドレスバーにインストールアイコンを表示します。

![画像](/help/user-guide/assets/cloud-player-install.png)

1. 確認ダイアログで、インストールアイコンをクリックし、インストールボタンをクリックします。 Cloud Player は、スタンドアロンアプリケーションとしてデバイスにインストールされ、アイコンを使用して起動できます。

### Cloud Player のインストールオプション {#cloud-player-install-option}

1. PWAのインストールオプションは、「ホーム画面に追加」または A2HS 機能とも呼ばれます。  Web からのPWAのインストールに対するサポートは、ブラウザーおよびプラットフォームによって異なります。
1. ブラウザーアプリがインストール可能かどうかを確認するための異なるPWAの条件があります。 一般に、ブラウザーは次の項目をチェックします（詳しくは、こちらを参照）。
   * アプリケーションに、プラットフォームにアプリをインストールするために必要な最小限のキーを持つマニフェスト json ファイル（名前、アイコン、start_url、表示）がある場合
   * アプリケーションに、フェッチイベントリスナーを含むサービスワーカーファイルがある場合。
   * アプリは https 経由で提供される必要があります。
1. インストールオプションは、ブラウザーやデバイスの種類に応じて異なる場所に表示される場合があります。 一部のブラウザーでは、オプションメニューバーのインストールアイコンが非表示になる場合があります。

## Cloud Player の一括プロビジョニング {#bulk-provisioning}

複数のデバイスでクラウドプレーヤーの一括プロビジョニングをおこなうには、次の手順を実行します。

1. URL を持つブラウザーをキオスクモードで実行できる MDM ソリューションを選択します。
1. 次の手順に従うことで、すべてのデバイスに同じ設定を適用できます。
   1. サーバー上で config.json をホストし、次のようにアクセス可能にします。 https://&lt;config_server_host>/config.json
   1. クラウドプレーヤーをインストールし、ホスト設定を適用するには、次のようなクラウドプレーヤー URL を使用します。 https://player.adobescreens.com?playerConfigAddress=https://&lt;config_server_host>
   1. Cloud Player アプリケーションは、のルートで config.json を探します。 &lt;config_server_host>を解析し、config.json を解析してカスタム設定を取得し、それらの設定を適用します。
   1. これらの設定は、プレーヤーの再読み込みのたびに適用されます。

## Chrome OS での一括プロビジョニング {#bulk-provisioning-chrome}

Chrome OS での一括プロビジョニングについて詳しくは、以下を参照してください。 [Chrome OS での Cloud Player のインストール](https://main--screens-franklin-documentation--hlxscreens.hlx.page/updates/cloud-player/guides/chromeos-install-cloud-player).

## AEMインスタンスに必要な設定 {#bulk-provisioning-config-aem}

AEMインスタンスのタイプに基づいて、次のガイドのいずれかを選択し、AEMおよび Cloud Player との CORS を有効にします。
* [AEMオンプレミス/AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams)
* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs)

