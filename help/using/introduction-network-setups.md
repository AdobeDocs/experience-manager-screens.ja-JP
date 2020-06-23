---
title: 標準ネットワーク設定の概要
seo-title: 標準ネットワーク設定の概要
description: このページでは、標準ネットワーク設定について説明します。
seo-description: このページでは、標準ネットワーク設定について説明します。
translation-type: tm+mt
source-git-commit: 0be82fcc46166ec0613bd658a0caeab83bd72551
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 36%

---


# ネットワークトラフィックの管理 {#managing-network-traffic}

ネットワーク設定は、様々な構造にすることができます。この節では、環境にデプロイされるネットワーク構造の概要を説明します。一から実装する設定も異なります。

この節では、プロキシサーバの概要と、異なる組織内で設定される異なるネットワーク構造の概要について説明します。

>[!NOTE]
>**AEM Screensネットワーク要件&#x200B;**>AEM ScreensはAEMCloud Serviceと直接通信するので、これらの2つのノード間に安定した接続を確立する必要があります。 ファイアウォールは、商用のインターネットアクセスでは絶対に必須です。お客様は、ファイアウォールや、お客様が管理する他のITセキュリティ関連のネットワークコンポーネントで開く必要がある通信ポートを知る必要があります。

## プロキシサーバー{#proxy-servers}

プロキシサーバーとは、コンピューターなどのエンドポイントデバイスと、ユーザーやクライアントからのサービス要求の送信先となる別のサーバーとの間で仲介役として機能する専用コンピューターまたはコンピューター上で動作するソフトウェアシステムです。プロキシサーバーは、ファイアウォールサーバーと同じマシンに存在することもあれば、別のサーバーに存在することもあります。後者の場合は、このサーバーからリクエストがファイアウォール経由で転送されます。

プロキシサーバーの利点の 1 つは、サーバーのキャッシュがすべてのユーザーの役に立つことです。1 つまたは複数のインターネットサイトが頻繁に要求される場合、それらのサイトはプロキシのキャッシュに格納されている可能性が高いので、ユーザーへの応答時間が向上します。プロキシでは、やり取りをログに記録することもできます。これは、トラブルシューティングに役に立ちます。

## Understanding the Standard Network Setups {#network-setups}

ネットワークセットアップを実装するには、次のシナリオを強みと導入の詳細と共に参照する必要があります。

ネットワーク設定には、主に次の 3 つのタイプがあります。

1. [ダイレクトインターネットネットワーク（有線/ワイヤレス）](/help/using/direct-internet-network.md)
1. [Direct Mobile Network](/help/using/mobile-network.md)
1. [モバイルデータルータとアクティブなネットワークコンポーネントを備えたモバイルネットワーク](/help/using/mobile-network-router.md)
1. [同封の企業ネットワーク（有線/無線）](/help/using/enclosed-corporate-network.md)

次の表に、さまざまなタイプのネットワーク設定と、長所と短所を示します。

<table>
 <tbody>
  <tr>
   <td><strong>ネットワーク設定</strong></td>
   <td><strong>メリット</strong></td>
   <td><strong>デメリット</strong></td>
  </tr>
  <tr>
   <td><strong>直接インターネットアクセス</strong></td>
   <td>中規模または大規模なインストール<br>専用ネットワークのSetUp<br>Good選択に簡単かつ簡単に進むことができ<br>ます。障害の発生点は<br>少なく、比較的安価で<br>優れた拡張性</td>
   <td>適切なインターネットデータ計画は必須です</td>
  </tr>
    <tr>
   <td><strong>Direct Mobile Network</strong></td>
   <td>SetUp<br>Good選択肢は中規模以上の環境に適しています。優れた拡張性を備えた<br><br>カプセル化された画面
</td>
   <td>適切なインターネット接続は必須です</td>
  </tr>
    <tr>
<tr>
   <td><strong>モバイルデータルータとアクティブなネットワークコンポーネントを備えたモバイルネットワーク</strong></td>
   <td>中規模または大規模な導入に適したSetUp<br>Good選択に簡単かつ簡単に進む<br>専用ネットワークは、<br>少数の障害点をカプセル化でき<br>ます。比較的安価で<br>優れた拡張性</br></td>
   <td>適切なインターネットデータ計画は必須です</td>
  </tr>
    <tr>

<td><strong>閉じた企業ネットワーク</strong></td>
   <td>高い柔軟性と拡張性<br>高いセキュリティ<br>。異なるDefense<br>Encapsulated Networks<br>Easy to Monitor and Maintance Refile(DEEnesencapsulated Networks)により、高いセキュリティを実現</td>
   <td>複雑で高価な<br>ネットワークスペシャリストまたはシステムインテグレータを推奨</td>
  </tr>
  </tr>
 </tbody>
</table>


