---
title: 直接モバイルネットワーク
description: AEM Screens での直接モバイルネットワーク設定について説明します。
exl-id: 6775bd10-7625-422f-a7af-4f7b8793fa42
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 97%

---

# 直接モバイルネットワーク {#mobile-network-setup}

 AEM Screens Player は、3G ネットワーク以上のモバイルネットワークまたは携帯電話ネットワークを使用して接続することもできます。

AEM Screens 内では、必要なコンテンツがプレーヤーコントローラーまたはコンピューターに物理的にダウンロードされ、基になるオペレーティングシステムに正しく保存されます。したがって、指定された帯域幅は、初期ダウンロード時間とコンテンツの更新にのみ影響し、ディスプレイの通常の再生パフォーマンスには影響しません。

AEM Screens Player を携帯電話 3/4/5G でモバイルサービスデータプロバイダーに接続する利点は、モバイルルーターを最適な場所に配置できることです。これにより、利用可能で最適なネットワークカバレッジが確保されます。この場所は通常、周囲にコンクリートや金属製の建造物ができるだけ少ない、高所の開けた位置です。

このセットアップでは、AEM Screens に接続する固定回線接続が必要ないので、AEM Screen ユーザーは極めて柔軟に接続できます。この方法は、一時的なセットアップやモバイルのセットアップでは興味深いものです。

次の図は、モバイルネットワークの直接設定を示します。1 つの単一のネットワーク接続セグメントと、各プレーヤーのモバイルまたは携帯電話データネットワークへの接続で構成されます。

![](/help/using/assets/direct-mobile-1.png)

## AEM Screens Player の直接モバイルネットワークへの接続

この設定で AEM Screen Player が正しく接続されていることを確認するには、次の手順に従います。

1. 各 AEM Screen プレイヤーがルーターのネットワークに接続されていることを確認します。

1. システムブラウザーで URL を呼び出して、インターネット接続をテストします。

   >[!NOTE]
   >エラーメッセージが表示された場合は、ネットワーク設定を確認し、十分なネットワークリンクがあるかどうかをクロスチェックします。また、オペレーティングシステムのファイアウォールが、設定済みの AEM Screens 通信ポートの使用中にネットワークアクセスを許可するように設定されていることも確認します。

1. URL 呼び出しが成功した場合は、AEM Screens のインストールを続行し、登録を行うことができます。AEM Screens を開始します。

## 直接モバイルネットワークの設定 {#requirements-direct}

ネットワークセットアップは、次の 2 つのブロックに論理的に分割できます。

* モバイルインターネット接続

* ローカルエリアネットワーク

### モバイルインターネット接続 {#mobile-internet-connection}

このインターネット接続は、ネットワーク到達性に加えて、AEM Screens をスムーズに動作させるのに十分な帯域幅を提供します。

直接モバイルネットワークでは、各プレーヤーは単一のモバイルデータカードを使用して、プロバイダーのデータネットワークに接続します。

次の表は、標準的な帯域幅のデータネットワークの概要です。

| データネットワーク | 帯域幅 |
|--- |--- |
| 3G | 42 Mbps |
| 4G | 150 Mbps |
| 5G | 1000～10000 Mbps |

使用するデータネットワークを検討する際には、次の点を考慮してください。

使用可能なネットワーク速度は、特定のモバイルデータプロバイダーのプランと、AEM Screens コントローラーの場所で利用可能なカバレッジによって異なります。
この設定を使用する際には、使用可能な帯域幅に加えて、モバイルデータプロバイダーのプランによって、特定の時間内に接続して受信できるデータ量が制限されることも考慮する必要があります。データと帯域幅の量に十分な容量があることを確認する必要があります。
そのため、最小限必要なデータパッケージは、次のとおりです。

`Data Package Capacity = # of Clients * (# of Content Files * Average File Size)`


>[!IMPORTANT]
>メディアファイルの初回アップロードの場合、新しいプレーヤーを統合する際に、データ量とダウンロード時間の増加が予想され、前述の前提が反映されます。有効範囲が&#x200B;*良好*&#x200B;で、データ量が&#x200B;*無制限*&#x200B;の 4G ネットワークは、このネットワークセットアップで最も一般的なインストールと一致する必要があります。

>[!NOTE]
>ネットワークカバレッジが良好な最小限の 3G プランは、AEM Screens Player にとって許容できるダウンロードパフォーマンスを提供します。適正な利用範囲が特定の場所に限られている場合は、ネットワークのセットアップ全体を[モバイルデータルータとアクティブネットワークコンポーネントを使用したモバイルネットワーク](/help/using/mobile-network-router.md)に切り替えることを検討してください。


### ローカルエリアネットワーク {#lan-connection}

ローカルエリアネットワーク（LAN）は、ネットワーク到達性に加えて、AEM Screens をスムーズに動作させるのに十分な帯域幅を提供します。LAN ネットワークの速度に関するレコメンデーションは、少なくとも 100 Mbps のネットワークから開始することです。これにより、多くのデバイスを接続するのに十分な帯域幅でシステムに対する良好なパフォーマンスを保つことができます。

他のアクティブなネットワークコンポーネントを使用する場合は、それらのすべてがネットワーク帯域幅の要件に一致している必要があります。 例えば、ネットワークコンポーネントは、最低でも 100 Mbps 標準、かつインターネットアクセスやルーターの仕様で規定される帯域幅と一致する必要があります。そうしない場合、ネットワークチェーン内の最も弱いリンクによって総帯域幅が制限されます。

## メディアとアセットのダウンロード {#download}

AEM Screens は、デジタルサイネージのユーザーに大きなメリットをもたらします。画像やビデオなど、必要なメディアファイルはすべてダウンロードされ、ローカルに保存されます。主なネットワークトラフィックは、特定のディスプレイに表示される新しいコンテンツがある場合に発生します。

通常の操作（日中頻繁に更新される定義済みのプレイリストなど）については、すべてのファイルがプレイヤーに保存されると、ほぼネットワークに依存しない操作を実現できます。

センサーやトリガーおよび動的コンテンツとのやり取りが多い場合、画面の即時応答で最高のカスタマーエクスペリエンスを保証するには、高速で信頼性の高いネットワーク接続が不可欠です。

ネットワーク接続の主要データの概要を次の表に示します。

>[!NOTE]
>
>インターネットソースをリクエストしてダウンロードするネットワーク内の各デバイスの消費量が、これらの情報からわかります。これらのリクエストがすべて合計されて、ダウンロード時間が延長されます。

![](/help/using/assets/download-times-mobile.png)
