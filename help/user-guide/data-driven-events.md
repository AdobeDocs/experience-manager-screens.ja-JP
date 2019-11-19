---
title: データ駆動型イベント
seo-title: データ駆動型イベント
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: 138ceff2-84a2-47f2-981a-755522502c16
contentOwner: jsyal
discoiquuid: b662831c-8cb0-48d8-9b4b-cc11a573d1b5
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# データ駆動型イベント{#data-driven-events}

デジタルサイネージでは、データ駆動型イベントは、デジタルメニューおよびビデオウォールをインタラクティブに使用することで、情報をリアルタイムに伝えることができます。データ駆動型イベントでユーザー体験を最大化できます。

## データ駆動型イベントに対する ContextHub の使用 {#using-context-hub-for-data-driven-events}

AEM Screens では、ContextHub を使用してデータ駆動型イベントを実現します。Context Hubを使用すると、リアルタイムで

### データ駆動型イベントのカスタマイズ {#categorizing-data-driven-events}

データ駆動型イベントは、次の 4 つの異なるカテゴリに分類されます。

* Data in Operational
* Data in Presentation
* Data out Actionable
* Data out Presentational

#### Data in Operational {#data-in-operational}

これはさらに Channel Interrupt と Placeholder に分類されます。

#### Data in Presentation {#data-in-presentation}

データは、一時チャネルで実行され、トリガー後、チャネル内のアセットを変更します。

#### Data out Actionable {#data-out-actionable}

コマンドが液晶画面に送信されると、画面のオンおよびオフが切り替わります（例えば、画面の明るさやボリュームなど）。

#### Data out Presentational {#data-out-presentational}

フィードバックループに情報を収集するグラフ。分析に使用され、イベントを評価および通知します。
