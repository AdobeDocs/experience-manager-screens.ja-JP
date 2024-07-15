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
source-git-commit: 6720e20f5254e869bde814bd167730e426d0f8fe
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 100%

---

# Cloud Player の実装 {#implementing-cloud-player}

AEM Screens は従来、ChromeOS、Windows、Android™、`Tizen` などの様々なプラットフォームに個別のネイティブプレーヤーアプリケーションを提供してきました。しかし、ユーザーの進化するニーズに応えて、革新的なソリューションである AEM Screens Cloud Player を導入しました。

Cloud Player は、以前のネイティブアプリケーションとは大きく異なります。これは、サーバー上でホストされるプログレッシブ web アプリ（PWA）です。この革新的なアプローチにより、お客様は web ブラウザー内で直接実行される、プラットフォームに依存しないプレーヤーを活用できます。

Cloud Player へのアクセスは、`https://player.adobescreens.com` にアクセスするだけで簡単です。ユーザーは、どのプラットフォームを使用しているかに関わらず、このアプリをデバイスにインストールでき、シームレスなデジタルサイネージエクスペリエンスをお楽しみいただけます。Cloud Player の互換性は、PWA をサポートする最新のブラウザーの存在に左右されますが、様々なデバイス間で一貫したパフォーマンスを実現します。手動更新が不要になりました。修正と機能を自動的に提供するプレーヤーを使用すれば、常に最新の機能をすぐに使用できます。PWA ベースの Cloud Player へのこの移行により、アドビのデジタルサイネージ製品は画期的に進化し、これまで以上にアクセスしやすく、多用途で、ユーザーにわかりやすくなりました。

この節では、Cloud Player の実装方法について説明します。

>[!NOTE]
>
>Cloud Player の互換性には、様々なデバイスで一貫したパフォーマンスを実現するために、PWA をサポートする最新のブラウザーが必要です。

## Cloud Player のインストール {#installing-cloud-player}

Cloud Player のインストールは、プラットフォームによって異なる場合があります。一般に、最新のブラウザーを備えたプラットフォームでは、次の手順に従って Cloud Player アプリケーションを実行できます。

1. ブラウザーを開き、アドレスバーに [Cloud Player の URL](https://player.adobescreens.com/content/dam/universal-player/firmware.html) を入力します。
1. ブラウザーで Cloud Player がインストール可能かどうかが確認され、その後アドレスバーにインストールアイコンが表示されます。

   ![画像](/help/user-guide/assets/cloud-player-install.png)

1. 確認ダイアログボックスで、インストールアイコンとインストールボタンをクリックします。Cloud Player は、スタンドアロンアプリケーションとしてデバイスにインストールされ、アイコンを使用して起動できます。

>[!NOTE]
>
>### Cloud Player のインストールオプション {#cloud-player-install-option}
>
1. PWA のインストールオプションは、「ホーム画面に追加」または A2HS 機能とも呼ばれます。Web からの PWA のインストールに対するサポートは、ブラウザーとプラットフォームによって異なります。
1. ブラウザーごとに、PWA アプリがインストール可能かどうかを確認するための条件が異なります。通常、ブラウザーでは次の項目を確認できます（詳しくは、こちらを参照）。
>
* アプリケーションに、プラットフォームにアプリをインストールするために必要な最小限のキー（name、icons、start_url、display）を含むマニフェスト JSON ファイルがあるかどうか
* アプリケーションに、フェッチイベントリスナーを含むサービスワーカーファイルがあるかどうか
* アプリは https 経由で提供する必要がある
>
1. インストールオプションは、ブラウザーやデバイスのタイプに応じて異なる場所に表示される場合があります。一部のブラウザーでは、オプションメニューバーのインストールアイコンが非表示になる場合があります。

## Cloud Player の一括プロビジョニング {#bulk-provisioning}

複数のデバイスで Cloud Player の一括プロビジョニングを行うには、次の手順に従います。

1. キオスクモードでの URL を使用したブラウザーの実行をサポートする MDM ソリューションを選択します。
1. すべてのデバイスに同じ設定を適用するには、次の手順に従います。

   1. `https://<config_server_host>/config.json` のように、アクセスできるようにサーバー上で config.json をホストします。
   1. Cloud Player をインストールし、ホストされた設定を適用するには、`https://player.adobescreens.com?playerConfigAddress=https://<config_server_host>` のような Cloud Player の URL を使用します。
   1. Cloud Player アプリケーションは、&lt;config_server_host> のルートで config.json を検索し、config.json を解析してカスタム設定を取得および適用します。
   1. これらの設定は、プレーヤーのリロードごとに適用されます。

## Chrome OS での一括プロビジョニング {#bulk-provisioning-chrome}

Chrome OS での一括プロビジョニングの詳細を説明します。[Chrome OS への Cloud Player のインストール](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/chromeos-install-cloud-player)を参照してください。&lt;!-- `https://www.adobe.com/go/aem_screens_cloud_player_en` >

## AEM インスタンスに必要な設定 {#bulk-provisioning-config-aem}

AEM インスタンスのタイプに基づいて、次のガイドのいずれかをクリックし、AEM および Cloud Player との CORS を有効にします。

* [AEM オンプレミス／AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams) <!-- `https://www.adobe.com/go/aem_screens_cors_ams_en` -->

* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs) <!-- `https://www.adobe.com/go/aem_screens_cors_aemaacs_en` -->


>[!NOTE]
>
## Googleによる Chrome アプリの非推奨（廃止予定）
>
1. Chrome OS ハードウェア上の Chrome アプリ：
>
Google は、PWA アプリを優先して Chrome アプリの非推奨（廃止予定）を積極的に進めており、2025年1月までに移行を完了する予定です。そのため、Chrome OS 上の AEM Screens Player アプリは、共有タイムラインに基づいて機能しなくなります。アドビは、現在 Chrome Player を実稼動環境で使用しているユーザーに対して、Screens Cloud Player への移行を計画するように促します。
>
1. Mac、Windows および Linux® 上の Chrome 拡張機能プレーヤー：
>
Google の非推奨（廃止予定）プロセスに伴い、Google Chrome バージョン 114 以降、Screens Chrome 拡張機能プレーヤーはサポートされなくなりました。すべての開発およびテスト要件に対応するには、Screens Cloud Player に移行することをお勧めします。

## 外部コンテンツ取得のオフラインサポート {#offline-support}

様々な使用シナリオでは、チャネルは、本質的にオフラインサポートを提供できない外部ソース（天気予報ウィジェットやコマース統合単一ページアプリケーションなど）からのコンテンツの取得を必要とする場合があります。これらの特定のユースケースでオフライン機能を有効にするために、Cloud Player ではカスタムヘッダーのサポートを提供します。

Cloud Player では、ネットワークファーストのキャッシュ戦略を採用しています。つまり、ネットワークからコンテンツを取得し（その後、最新でキャッシュを更新し）、キャッシュされたコンテンツが使用可能な場合はフォールバックします。このようなコンテンツ取得のオフラインサポートを実装するには、リクエストにカスタムヘッダーを含める必要があります。その後、カスタムヘッダーを含むリクエストがプレーヤーにキャッシュされ、ネットワークファーストのキャッシュ戦略を維持しながらコンテンツへのオフラインアクセスが簡単になります。

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

アドビでは、お客様のフィードバックを大切にしています。この[フォーム](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4TFE0b_GjstOj6I1uGs9vLpURVdWWklQQTZZRTFVNEhRVlBWWldMWlJXOC4u)を通じてご意見をお聞かせください。
