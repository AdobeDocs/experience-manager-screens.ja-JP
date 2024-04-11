---
title: Cloud Player の実装
description: Cloud Player の実装について説明します。
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 10375baae631d46e9003240149a3e16d5605e7b6
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 46%

---

# Cloud Player の実装  {#implementing-cloud-player}

AEM Screensは従来、ChromeOS、Windows、Android™ および `Tizen`. しかし、ユーザーのニーズの変化に応えて、Adobeは革新的なソリューションであるAEM Screens Cloud Player を導入しました。

Cloud Player は、Adobeの以前のネイティブアプリケーションとは大きく異なります。 これは、サーバーでホストされるプログレッシブ web アプリ（PWA）です。 この革新的なアプローチにより、web ブラウザー内で直接実行される、プラットフォームに依存しないプレーヤーが顧客を強化します。

Cloud Player へのアクセスは、次のように簡単です `https://player.adobescreens.com`. ユーザーは、どのプラットフォームを使用しているかに関わらず、このアプリをデバイスにインストールでき、シームレスなデジタルサイネージエクスペリエンスをお楽しみいただけます。Cloud Player の互換性は、PWA をサポートする最新のブラウザーの存在に左右されますが、様々なデバイス間で一貫したパフォーマンスを実現します。手動更新が不要になりました。修正と機能を自動的に提供するプレーヤーを使用すれば、常に最新の機能をすぐに使用できます。PWAベースの Cloud Player への移行は、Adobeのデジタルサイネージ製品のエキサイティングな進化を示し、以前よりもアクセスしやすく、汎用性が高く、使いやすいものになっています。

この節では、Cloud Player の実装方法について説明します。

>[!NOTE]
>
>Cloud Player の互換性には、様々なデバイスで一貫したパフォーマンスを実現するために、PWA をサポートする最新のブラウザーが必要です。

## Cloud Player のインストール {#installing-cloud-player}

Cloud Player のインストールは、プラットフォームによって異なる場合があります。一般に、最新のブラウザーを備えたプラットフォームでは、次の手順に従って Cloud Player アプリケーションを実行できます。

1. ブラウザーを開き、アドレスバーに [Cloud Player の URL](https://player.adobescreens.com/content/dam/universal-player/firmware.html) を入力します。
1. ブラウザーは、クラウドプレーヤーがインストール可能かどうかを確認してから、アドレスバーにインストールアイコンを表示します。

   ![画像](/help/user-guide/assets/cloud-player-install.png)

1. 確認ダイアログ・ボックスのインストール・アイコンとインストール・ボタンを選択します。 Cloud Player は、デバイス上のスタンドアロンアプリケーションとしてインストールされ、アイコンを使用して起動できます。

>[!NOTE]
>
>### Cloud Player のインストールオプション {#cloud-player-install-option}
>
1. PWAのインストールオプションは、「ホーム画面に追加」または A2HS 機能とも呼ばれます。 Web からの PWA のインストールに対するサポートは、ブラウザーとプラットフォームによって異なります。
1. ブラウザーごとに、PWA アプリがインストール可能かどうかを確認するための条件が異なります。一般に、ブラウザーでは次の項目が確認されます（詳しくは、こちらを参照）。
>
* アプリケーションに、プラットフォームへのアプリケーションのインストールに必要な最小限のキー（名前、アイコン、start_url、ディスプレイ）を含むマニフェスト JSON ファイルがある場合
* アプリケーションに、取得イベントリスナーを含むサービスワーカーファイルがある場合
* アプリは HTTPS で提供する必要があります
>
1. インストールオプションは、異なるブラウザーやデバイスタイプの異なる場所に表示される場合があります。 一部のブラウザーでは、オプションメニューバーのインストールアイコンが非表示になる場合があります。

## Cloud Player の一括プロビジョニング {#bulk-provisioning}

複数のデバイスで Cloud Player の一括プロビジョニングを行うには、次の手順に従います。

1. キオスクモードでの URL を含むブラウザーの実行をサポートする MDM ソリューションを選択します。
1. すべてのデバイスに同じ設定を適用するには、次の手順に従います。

   1. 次のようなアクセス可能なサーバーで config.json をホストします。 `https://<config_server_host>/config.json`
   1. クラウドプレーヤーをインストールし、ホストされた設定を適用するには、次のようなクラウドプレーヤー URL を使用します。 `https://player.adobescreens.com?playerConfigAddress=https://<config_server_host>`
   1. Cloud Player アプリケーションは、&lt;config_server_host> のルートで config.json を検索し、config.json を解析してカスタム設定を取得および適用します。
   1. これらの設定は、プレーヤーがリロードされるたびに適用されます。

## Chrome OS での一括プロビジョニング {#bulk-provisioning-chrome}

Chrome OS での一括プロビジョニングについて詳しくは、 [Chrome OS への Cloud Player のインストール](https://www.adobe.com/go/aem_screens_cloud_player_en).

## AEM インスタンスに必要な設定 {#bulk-provisioning-config-aem}

AEM インスタンスのタイプに基づいて、次のガイドのいずれかを選択し、AEM および Cloud Player との CORS を有効にします。
* [AEM オンプレミス／AMS](https://www.adobe.com/go/aem_screens_cors_ams_en)
* [AEM Cloud Service](https://www.adobe.com/go/aem_screens_cors_aemaacs_en)

>[!NOTE]
>
## Googleによる Chrome アプリの非推奨（廃止予定）
>
1. Chrome OS ハードウェア上の Chrome アプリ：
>
Google は、PWA アプリを優先して Chrome アプリの非推奨（廃止予定）を積極的に進めており、2025年1月までに移行を完了する予定です。そのため、Chrome OS 上のAEM Screens Player アプリは、共有タイムラインに基づいて機能しなくなります。 Adobeは、現在 Chrome Player を実稼動環境で使用しているユーザーに対して、Screens Cloud Player への移行を計画するように促します。
>
1. Mac、Windows および Linux® の Chrome Extension Player:
>
Google の非推奨（廃止予定）プロセスに伴い、Google Chrome バージョン 114 以降、Screens Chrome 拡張機能プレーヤーはサポートされなくなりました。Adobeでは、すべての開発およびテスト要件について、対応する Screens Cloud Player に移行することをお勧めします。

## 外部コンテンツ取得のオフラインサポート {#offline-support}

様々な使用シナリオにおいて、チャネルでは、本質的にオフラインサポートを提供できない外部ソース（天気予報ウィジェットやコマース統合された単一ページアプリケーションなど）からコンテンツを取得する必要が生じる場合があります。 これらの特定のユースケースでオフライン機能を有効にするために、Cloud Player ではカスタムヘッダーのサポートを提供します。

Cloud Player では、ネットワークファーストのキャッシュ戦略を採用しています。つまり、ネットワークからコンテンツを取得し（その後、最新でキャッシュを更新し）、キャッシュされたコンテンツが使用用可能な場合はフォールバックします。このようなコンテンツ取得のオフラインサポートを実装するには、リクエストにカスタムヘッダーを含める必要があります。次に、カスタムヘッダーを含むリクエストがプレーヤーにキャッシュされ、ネットワーク上の最初のキャッシュ戦略を維持しながら、コンテンツへのオフラインアクセスが容易になります。

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

## フィードバック

Adobeはフィードバックを尊重します。 ご意見をお聞かせください [フォーム](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4TFE0b_GjstOj6I1uGs9vLpURVdWWklQQTZZRTFVNEhRVlBWWldMWlJXOC4u).
