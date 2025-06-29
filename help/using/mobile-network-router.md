---
title: モバイルデータルーターとアクティブなネットワークコンポーネントを使用したモバイルネットワーク
description: このページは、モバイルデータルーターとアクティブなネットワークコンポーネントを使用したモバイルネットワークについて説明しています
exl-id: a6b44a04-438d-49d4-ac98-32629c11dcdb
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 98%

---

# モバイルデータルーターとアクティブなネットワークコンポーネントを使用したモバイルネットワーク {#mobile-network-setup}

Adobe AEM Screens Player は、3G ネットワーク以上のモバイルネットワークまたは携帯電話ネットワークを使用して接続することもできます。

AEM Screens 内では、必要なコンテンツがプレーヤーコントローラーまたはコンピューターに物理的にダウンロードされ、基になるオペレーティングシステムに正しく保存されます。したがって、指定された帯域幅は、初期ダウンロード時間とコンテンツの更新にのみ影響し、ディスプレイの通常の再生パフォーマンスには影響しません。

このセットアップの利点は、モバイルルーターを最適な場所に配置して、利用可能なネットワークカバレッジを最大限に確保できることです。この最適な場所とは、通常、周囲にコンクリートや金属製の建造物ができるだけ少ない、高所の開けた位置です。
このセットアップを使用すると、AEM Screens を固定回線に接続する必要がないので、AEM Screen ユーザーの柔軟性が高まります。また、一時的なセットアップやモバイルセットアップにとっても興味深いものです。

次の図は、モバイルデータルーターとアクティブなネットワークコンポーネント設定を使用したモバイルネットワークについて説明しています。これには、独自の 3/4/5G データリンクを使用したインターネットアクセスによる任意の AEM Screens コントローラーのインターネットアクセスが含まれています。

![](/help/using/assets/mobile-network-1.png)

## モバイルデータルーターとアクティブなネットワークコンポーネントを使用したモバイルネットワークへの AEM Screens Player の接続 {#connecting-aem-screens-players}

この設定で AEM Screen Player が正しく接続されていることを確認するには、次の手順に従います。

この設定は、専用の 3／4／5G データリンクを使用して直接インターネットにアクセスすることにより、各 AEM Screens コントローラに対してインターネットアクセスを割り当てます。

1. OS 内の指示に従って、モバイルデータルーターがセルラーデータネットワークに正しく接続されていることを確認します。さらに、各 AEM Screen プレイヤーがルーターネットワークに接続されていることを確認します。
1. システムブラウザーで URL を呼び出して、インターネット接続をテストします。

   >[!NOTE]
   >エラーが発生した場合は、ネットワーク設定を確認します。適切なネットワーク接続には、基本的に次の 2 つのオプションがあります。
   >* DHCP
   >* 手動による IP 設定

1. ネットワークアダプタの設定がルーターの設定と一致していることを確認します。

1. ルーターがインターネットサービスプロバイダーのワイドエリアネットワーク（インターネットリンク）に正しく接続されているかどうかを確認します。この接続は、標準ルーターのシグナル LED で確認できます。
1. URL 呼び出しが成功した場合は、AEM Screens のインストールを続行し、登録をおこなうことができます。AEM Screens を開始します。

   >[!TIP]
   >AEM Screens 接続が正常に動作していないという問題が発生する場合があります。期待されたコンテンツが表示されません。このような場合には、インターネットルーターファイアウォールに `TCP/IP Port 80/443` に関する制限があるかどうかを確認します。


## モバイルデータルータとアクティブなネットワークコンポーネントを使用したモバイルネットワークのセットアップ {#requirements-direct}

ネットワークセットアップは、次の 2 つのブロックに論理的に分割できます。

* モバイルインターネット接続

* ローカルエリアネットワーク

### モバイルインターネット接続 {#mobile-internet-connection}

このインターネット接続は、既に説明したネットワーク到達性に加えて、AEM Screens コンテンツのダウンロードをスムーズに実行するのに十分な帯域幅を提供する性能を備えています。

*十分*かどうかは、接続されている AEM Screens デバイスの数によります。また、スマートフォン、タブレット、レジ、コンピューター、ゲスト Wi-Fi ネットワークなど、ネットワーク内の他のユーザーの使用状況によって異なります。
すべてのデバイスはインターネット接続に同時にアクセスできるので、ネットワークにユーザーやコンピューターを追加すると帯域幅は直線的に減少します。
特定の理論上のネットワーク接続を確保するだけでなく、モバイルルーターのカバレッジが、少なくとも*良好*&#x200B;であることを確認する必要があります。また、基本的な月々プランは、接続された LAN 内の接続されたすべてのクライアントに対応するのに十分なデータ容量と帯域幅のプランにする必要があります。

次の表は、標準的な帯域幅のデータネットワークの概要です。

| データネットワーク | 帯域幅 |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000～10000 Mbps |

使用するデータネットワークを検討するときには、アドビでは次の質問に答えることをお勧めします。

* ルーターに接続されているクライアント数
* 予想されるコンテンツ変更の回数と、ファイルの平均的なサイズ

>[!NOTE]
>
>最低限必要なデータパッケージは、次の通りです。
>
>`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`

>[!IMPORTANT]
>
>新しいプレーヤーを統合する際、メディアファイルの初回アップロードでは、データ量とダウンロード時間の増加が予想されます。この予測は、前述の前提にも反映されます。カバレッジが&#x200B;*良好*&#x200B;で、データ量が無制限の 4G ネットワークは、このネットワークセットアップで最も一般的なインストールと一致するはずです。


### ローカルエリアネットワーク {#lan-connection}

この LAN は、既に説明したネットワーク到達性に加えて、AEM Screens コンテンツのダウンロードをスムーズに操作するのに十分な帯域幅を提供する性能を備えています。最近の LAN ネットワークは、通常、最低でも 100 Mbps のネットワークに匹敵するため、多くのデバイスを高パフォーマンスでシステムに接続するのに十分な帯域幅が必要となります。他のアクティブなネットワークコンポーネントを使用する場合は、それらのすべてがネットワーク帯域幅の要件に一致している必要があります。

例えば、ネットワークコンポーネントは、最低でも 100 Mbps 標準に匹敵し、インターネットアクセスやルーターの仕様で規定されている帯域幅と一致している必要があります。

Wi-Fi ソリューションで画面をインターネットリンクに接続することを想定している場合、少なくとも IEEE `802.11g` などの最新の Wi-Fi 標準を使用することをお勧めします。この標準では、最大 54 Mbps までの接続をサポートします。`802.11h-n` のような&#x200B;*新しい*&#x200B;標準はどれも高品質です。Wi-Fi リピーターが必要な場合は、アドビでは Google Nest Mesh Wi-Fi などのメッシュ Wi-Fi アクセスポイントテクノロジーを使用することをお勧めします。

## メディアとアセットのダウンロード {#download}

AEM Screens は、デジタルサイネージのユーザーに大きなメリットをもたらします。画像やビデオなど、必要なメディアファイルはすべてダウンロードされ、ローカルに保存されます。この考え方により、特定の画面に新しいコンテンツが表示される場合、大量のネットワークトラフィックが発生します。
通常の操作（あまり頻繁に変更されない定義済みのプレイリストがある場合）については、すべてのファイルがプレイヤーに保存されると、ほぼネットワークに依存しない操作になります。
センサーや他のトリガーとのやり取りが多く、コンテンツが動的であるユースケースの場合は、画面の即時応答を実現するには、高速で信頼性の高いネットワーク接続が不可欠です。これにより、考えられる最善のカスタマーエクスペリエンスが保証されます。
ネットワーク接続の主要データと、それぞれの場合に予想されるパフォーマンスおよび潜在的な待ち時間の概要を次の表に示します。

>[!NOTE]
>
>インターネットソースをリクエストしてダウンロードするネットワーク内の各デバイスの消費量が、これらの情報からわかります。これらのリクエストがすべて合計されて、ダウンロード時間が延長されます。

![](/help/using/assets/mobile-router-download.png)
