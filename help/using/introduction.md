---
title: AEM Screens の概要
description: AEM Screens の概要と機能について説明します。
exl-id: 11781e0b-0aca-4d08-aaad-87a7aaf28c24
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 100%

---

# AEM Screens の概要 {#introduction}

**AEM Screens** は、動的でインタラクティブなデジタルエクスペリエンスを作成、公開、再生できるデジタルサイネージソリューションです。これには、包括的なオムニチャネルデジタルマーケティング戦略と連携して、様々なタイプの会場ディスプレイ画面が含まれます。

AEM Screens では、以下を作成できます。

* **専用のデジタルメニューボード**
* **商品レコメンデーション**
* **背景のライフスタイル画像**

また、Screens には、アプリケーションがデプロイされるドメインに基づいて、顧客や従業員向けの独自アプリケーションが多数用意されています。例えば、次のようなものです。

* **インタラクティブなディスプレイ**
* **ウェイファインディング**
* **ブランディング**
* **環境へのアンビエンスの追加**

AEM Screens を使用したデジタルサイネージネットワークの作成と管理はシンプルかつ直感的です。プレーヤーアプリケーションは、顧客や実装パートナーが AEM Screens 向けに作成したコンテンツチャネルをホストします。*場所*&#x200B;は、事前に定義された場所階層を管理し、ディスプレイを含んでいます。各&#x200B;*ディスプレイ*&#x200B;には、関連付けられている様々なデバイスや画面を表示するダッシュボードがあります。AEM Screens のコンテンツは&#x200B;*チャネル*&#x200B;で管理されます。チャネル内に存在するコンテンツが *AEM Screens Player* によってディスプレイにレンダリングされます。

>[!NOTE]
>
>AEM Screens プロジェクトの開発と管理に関する様々な機能について詳しくは、**[AEM Screens ユーザーガイド](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/aem-screens-introduction)**&#x200B;を参照してください。

## AEM Sites と AEM Screens の比較 {#aem-sites-screens}

>[!NOTE]
>
>AEM Sites アプリケーションを扱った経験が実装チームにある場合は、AEM Sites と AEM Screens の違いを理解しておくことが重要です。

AEM Screens は、公共の場所にあるデジタルサイネージデバイスにコンテンツをデプロイするための統合オーサリング／再生プラットフォームを提供します。エクスペリエンス作成者は、Web チャネルと会場内チャネル間の一貫性を保つように努力する必要がありますが、両者にはいくつか違いがあるので、注意してください。

* **滞留時間**：通常、web ページは、比較的長い時間にわたって利用できる豊富な情報を提供するように設計されています。これに対して、会場内のデジタルエクスペリエンスでは、閲覧者のニーズを予測し、ユーザーが関与する方法と理由を明確かつ簡潔に伝える必要があります。このように注意すると、ターゲットをより絞り込んで、さらにキュレートされた、コンテキストに沿ったエクスペリエンスになります。

* **表示距離**：表示距離は、web サイトでユーザーが経験する通常の表示距離よりも長いか遠くなります。その結果、通常はテキストサイズを大きくし、実際の物理空間で予想される画面サイズと配置に基づいて、テキストや画像などの補助コンテンツ間の間隔をテストする必要があります。

* **永続性**：プレイヤーデバイスの接続状態によって、ユーザーに提供されるデジタルエクスペリエンスに影響がないようにしてください。プレーヤーデバイスの接続状態に関係なく、常に 1 つ以上のエクスペリエンスが持続しユーザーに配信できるように、プレーヤーを設計する必要があります。

* **メディアループのセグメント化**：プレイヤーデバイスごとに独自のループセグメントを設定すると、ローカライズされたコンテンツを容易に作成、公開し、デジタルエクスペリエンス全体で再生できるようになります。埋め込みシーケンスチャネル内に含まれるメディアアセットが前のループセグメントに追加され、ロケーショングループごとに、メディアループセグメントをターゲットにする機会が生まれます。

* **インタラクティブなエクスペリエンス**：AEM および SPA エディターを使用して、タッチ操作対応のキオスクアプリケーションを作成し、Screens チャネルに配信できます。一貫性のあるオムニチャネルデザインプロパティ、エクスペリエンスをリセットするための無操作状態タイマー、アプリケーションで実行できるタスクを明確に示すコールトゥアクションを適用することを、ベストプラクティスとしてお勧めします。ランディングページは、ユーザーに価値を伝え、ユーザーを画面に引き付け、ユーザーに関与を促すように設計された主要なデジタル要素で構成する必要があります。

AEM Screens は、物理デバイスにコンテンツをデプロイするためのフレームワークを提供します。コンテンツは Screens 内のチャネルに割り当てられます。チャネルには、メディアコンテンツやタッチスクリーンアプリケーションを含めることができます。このフレームワーク内では、チャネルを通じて AEM Sites アプリケーションをコンテンツとして配信することもできます。

AEM サイトは、目的とする表示デバイスのサイズで使用できるようにフォーマットする必要があります。フォーマットは Screens のチャネルにドロップする前に行う必要があります。

>[!NOTE]
>多くの AEM Sites コンポーネントは、AEM Screens と互換性がありません。AEM Screens には、すぐに使用できる独自のコンポーネントが多数付属しており、それらをそのまま使用してデジタルエクスペリエンスを構築できます。プロジェクト要件が許す限り、できるだけ組み込みの AEM Screens 機能を使用してください。
