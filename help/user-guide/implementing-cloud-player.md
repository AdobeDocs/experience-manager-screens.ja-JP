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
source-git-commit: 2b865165793b1c0f90f1351518e41096a57ea2ff
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 36%

---

# Cloud Player の実装  {#implementing-cloud-player}

AEM Screensは、従来、ChromeOS、Windows、Android™、 `Tizen`. しかし、ユーザーのニーズの進化に応えて、Adobeは革新的なソリューションであるAEM Screens Cloud Player を導入しました。

Cloud Player は、以前のネイティブアプリケーションからの大きなAdobeの脱却を表しています。 これは、サーバー上でホストされるプログレッシブ Web アプリ (PWA) です。 この変換的なアプローチにより、Web ブラウザー内で直接動作する、プラットフォームに依存しないプレーヤーを強化できます。

Cloud Player へのアクセスは、訪問と同じくらい簡単です `https://player.adobescreens.com`. ユーザーは、どのプラットフォームを使用しているかに関わらず、このアプリをデバイスにインストールでき、シームレスなデジタルサイネージエクスペリエンスをお楽しみいただけます。Cloud Player の互換性は、最新のブラウザーとPWAのサポートが存在することに左右され、様々なデバイスで一貫したパフォーマンスを実現します。 手動更新が不要になり、修正と機能を自動的に提供するプレーヤーを使用して、常に最新の機能をすぐに使用できるになります。PWAベースの Cloud Player への移行は、Adobeのデジタルサイネージ製品の飛躍的な進化を示し、これまで以上にアクセスしやすく、多目的で、使いやすくなりました。

この節では、Cloud Player の実装方法について説明します。

>[!NOTE]
>
>Cloud Player の互換性には、様々なデバイスで一貫したパフォーマンスを実現するために、PWA をサポートする最新のブラウザーが必要です。

## Cloud Player のインストール {#installing-cloud-player}

Cloud Player のインストールは、プラットフォームによって異なる場合があります。一般に、最新のブラウザーを備えたプラットフォームでは、次の手順に従って Cloud Player アプリケーションを実行できます。

1. ブラウザーを開き、アドレスバーに [Cloud Player の URL](https://player.adobescreens.com) を入力します。
1. ブラウザーは、Cloud Player がインストール可能かどうかを確認し、アドレスバーにインストールアイコンを表示します。

   ![画像](/help/user-guide/assets/cloud-player-install.png)

1. 確認ダイアログボックスで、インストールアイコンとインストールボタンを選択します。 Cloud Player は、スタンドアロンアプリケーションとしてデバイスにインストールされ、アイコンを使用して起動できます。

>[!NOTE]
>
>### Cloud Player のインストールオプション {#cloud-player-install-option}
>
1. PWAのインストールオプションは、「ホーム画面に追加」または A2HS 機能とも呼ばれます。 Web からの PWA のインストールに対するサポートは、ブラウザーとプラットフォームによって異なります。
1. ブラウザーごとに、PWA アプリがインストール可能かどうかを確認するための条件が異なります。一般に、ブラウザーでは次の項目が確認されます（詳しくは、こちらを参照）。
>
* アプリケーションに、プラットフォームにアプリをインストールするために必要な最小限のキーを持つマニフェスト json ファイルが含まれている場合（名前、アイコン、start_url、表示）。
* アプリケーションに、フェッチイベントリスナーを含むサービスワーカーファイルがある場合
* アプリは https 経由で提供する必要があります
>
1. インストールオプションは、ブラウザーやデバイスの種類に応じて異なる場所に表示される場合があります。 一部のブラウザーでは、オプションメニューバーのインストールアイコンが非表示になる場合があります。

## Cloud Player の一括プロビジョニング {#bulk-provisioning}

複数のデバイスで Cloud Player の一括プロビジョニングを行うには、次の手順に従います。

1. URL を持つブラウザーをキオスクモードで実行できる MDM ソリューションを選択します。
1. すべてのデバイスに同じ設定を適用するには、次の手順に従います。

   1. サーバー上で config.json をホストし、次のようにアクセス可能にします。 `https://<config_server_host>/config.json`
   1. クラウドプレーヤーをインストールし、ホスト設定を適用するには、次のようなクラウドプレーヤー URL を使用します。 `https://player.adobescreens.com?playerConfigAddress=https://<config_server_host>`
   1. Cloud Player アプリケーションは、&lt;config_server_host> のルートで config.json を検索し、config.json を解析してカスタム設定を取得および適用します。
   1. これらの設定は、プレーヤーの再読み込みのたびに適用されます。

## Chrome OS での一括プロビジョニング {#bulk-provisioning-chrome}

Chrome OS での一括プロビジョニングについて詳しくは、 [Chrome OS での Cloud Player のインストール](https://main--screens-franklin-documentation--hlxscreens.hlx.page/updates/cloud-player/guides/chromeos-install-cloud-player).

## AEM インスタンスに必要な設定 {#bulk-provisioning-config-aem}

AEM インスタンスのタイプに基づいて、次のガイドのいずれかを選択し、AEM および Cloud Player との CORS を有効にします。
* [AEM オンプレミス／AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams)
* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs)

>[!NOTE]
>
## Googleによる Chrome アプリの非推奨（廃止予定）
>
1. Chrome OS ハードウェア上の Chrome アプリ：
>
Googleは、PWAアプリに対して Chrome アプリを積極的に非推奨とし、2025 年 1 月までの移行を予定しています。 したがって、Chrome OS 上のAEM Screens Player アプリは共有タイムラインに基づいて機能しなくなります。 Adobeは、実稼動環境で Chrome プレーヤーを現在使用しているユーザーに対し、Screens Cloud Player への移行を計画するよう促します。
>
1. Mac、Windows および Linux®上の Chrome 拡張機能プレーヤー：
>
Googleの廃止プロセスにより、Google Chrome バージョン 114 以降、Screens Chrome Extension Player はサポートされなくなりました。 Adobeでは、Screens Cloud Player に移行する際に、開発およびテストに関するすべての要件についてお知らせします。

## 外部コンテンツ取得のオフラインサポート {#offline-support}

様々な使用シナリオでは、本質的にオフラインサポートを提供できない外部ソース（天気予報ウィジェットや Commerce 統合単一ページアプリケーションなど）からのコンテンツの取得がチャネルで必要になる場合があります。 これらの特定の使用例でオフライン機能を有効にするために、Cloud Player では、カスタムヘッダーのサポートを提供しています。

Cloud Player では、ネットワークファーストのキャッシュ戦略を採用しています。つまり、ネットワークからコンテンツを取得し（その後、最新でキャッシュを更新し）、キャッシュされたコンテンツが使用用可能な場合はフォールバックします。このようなコンテンツ取得のオフラインサポートを実装するには、リクエストにカスタムヘッダーを含める必要があります。次に、カスタムヘッダーを含むリクエストがプレーヤーにキャッシュされ、ネットワーク初回キャッシュ戦略を維持しながら、コンテンツへのオフラインアクセスが容易になります。

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

Adobeは、フィードバックを評価します。 これを通じて、皆様のご意見をお聞かせください。 [フォーム](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4TFE0b_GjstOj6I1uGs9vLpURVdWWklQQTZZRTFVNEhRVlBWWldMWlJXOC4u).
