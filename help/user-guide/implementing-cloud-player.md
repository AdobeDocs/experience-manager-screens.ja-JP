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
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 8d1b955e54650daf3a09b5f1c16f92f2e1143f2c
workflow-type: ht
source-wordcount: '582'
ht-degree: 100%

---

# Cloud Player の実装  {#implementing-cloud-player}

この節では、Cloud Player の実装方法について説明します。

>[!NOTE]
>
>Cloud Player の互換性には、様々なデバイスで一貫したパフォーマンスを実現するために、PWA をサポートする最新のブラウザーが必要です。

## Cloud Player のインストール {#installing-cloud-player}

Cloud Player のインストールは、プラットフォームによって異なる場合があります。一般に、最新のブラウザーを備えたプラットフォームでは、次の手順に従って Cloud Player アプリケーションを実行できます。

1. ブラウザーを開き、アドレスバーに [Cloud Player の URL](https://player.adobescreens.com) を入力します。
1. ブラウザーでは、Cloud Player がインストール可能かどうかが確認され、アドレスバーにインストールアイコンが表示されます。

![画像](/help/user-guide/assets/cloud-player-install.png)

1. 確認ダイアログで、インストールアイコンとインストールボタンをクリックします。Cloud Player は、スタンドアロンアプリケーションとしてデバイスにインストールされ、アイコンを使用して起動できます。

### Cloud Player のインストールオプション {#cloud-player-install-option}

1. PWA のインストールオプションは、「ホーム画面に追加」または A2HS 機能とも呼ばれます。Web からの PWA のインストールに対するサポートは、ブラウザーとプラットフォームによって異なります。
1. ブラウザーごとに、PWA アプリがインストール可能かどうかを確認するための条件が異なります。一般に、ブラウザーでは次の項目が確認されます（詳しくは、こちらを参照）。
   * アプリケーションに、プラットフォームにアプリをインストールするために必要な最小限のキー（名前、アイコン、start_url、表示）を含むマニフェスト JSON ファイルがある場合
   * アプリケーションに、フェッチイベントリスナーを含むサービスワーカーファイルがある場合。
   * アプリは、https 経由で提供する必要があります。
1. インストールオプションは、ブラウザーやデバイスのタイプに応じて異なる場所に表示される場合があります。一部のブラウザーでは、オプションメニューバーのインストールアイコンが非表示になる場合があります。

## Cloud Player の一括プロビジョニング {#bulk-provisioning}

複数のデバイスで Cloud Player の一括プロビジョニングを行うには、次の手順に従います。

1. キオスクモードでの URL を使用したブラウザーの実行をサポートする MDM ソリューションを選択します。
1. すべてのデバイスに同じ設定を適用するには、次の手順に従います。
   1. https://&lt;config_server_host>>/config.json のように、アクセスできるようにサーバー上で config.json をホストします。
   1. Cloud Player をインストールし、ホストされた設定を適用するには、https://player.adobescreens.com?playerConfigAddress=https://&lt;config_server_host> のような Cloud Player の URL を使用します。
   1. Cloud Player アプリケーションは、&lt;config_server_host> のルートで config.json を検索し、config.json を解析してカスタム設定を取得および適用します。
   1. これらの設定は、プレーヤーのリロードごとに適用されます。

## Chrome OS での一括プロビジョニング {#bulk-provisioning-chrome}

Chrome OS での一括プロビジョニングについて詳しくは、[Chrome OS での Cloud Player のインストール](https://main--screens-franklin-documentation--hlxscreens.hlx.page/updates/cloud-player/guides/chromeos-install-cloud-player)を参照してください。

## AEM インスタンスに必要な設定 {#bulk-provisioning-config-aem}

AEM インスタンスのタイプに基づいて、次のガイドのいずれかを選択し、AEM および Cloud Player との CORS を有効にします。
* [AEM オンプレミス／AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams)
* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs)

## 外部コンテンツ取得のオフラインサポート {#offline-support}

様々な使用シナリオでは、チャネルは、本質的にオフラインサポートを提供できない外部ソース（天気予報ウィジェットやコマース統合単一ページアプリケーションなど）からのコンテンツの取得を必要とする場合があります。これらの特定のユースケースでオフライン機能を有効にするために、Cloud Player ではカスタムヘッダーのサポートを提供します。
Cloud Player では、ネットワークファーストのキャッシュ戦略を採用しています。つまり、ネットワークからコンテンツを取得し（その後、最新でキャッシュを更新し）、キャッシュされたコンテンツが使用用可能な場合はフォールバックします。このようなコンテンツ取得のオフラインサポートを実装するには、リクエストにカスタムヘッダーを含める必要があります。その後、カスタムヘッダーを含むリクエストがプレーヤーにキャッシュされ、ネットワークファーストのキャッシュ戦略を維持しながらコンテンツへのオフラインアクセスが簡単になります。

```
// Sample fetch request with the 'X-Cache-Strategy' header
fetch(externalUrl, {
  headers: {
    'X-Cache-Strategy': 'external-cache'
  }
})
  .then(response => {
    // Handle the response, which may be from the network or cache.
    // Your logic here.
  })
  .catch(error => {
    // Handle any errors that may occur during the fetch operation.
    // Your error handling logic here.
  }); 
```
