---
title: データ駆動型イベント
description: ヌル
page-status-flag: never-activated
contentOwner: jsyal
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 43%

---


# データ駆動型イベント{#data-driven-events}

デジタルサイネージでは、データ駆動型のイベントにより、デジタルメニューやビデオウォールをインタラクティブに使用して、情報をリアルタイムで惹きつけ、伝えます。 データ駆動型イベントでユーザーエクスペリエンスを最大化できます。

## データ駆動型イベントに対する Context Hub の使用 {#using-context-hub-for-data-driven-events}

AEM Screens では、Context Hub を使用してデータ駆動型イベントを実現します。Context Hub を使用すると、リアルタイムで使用できます。

### データ駆動型イベントのカスタマイズ {#categorizing-data-driven-events}

データ駆動型イベントは、次の 4 つの異なるカテゴリに分類されます。

* 運用データ
* プレゼンテーション内のデータ
* アクションにつながるデータ出力
* Data out Presentational

#### 運用データ {#data-in-operational}

このイベントは、さらにチャネル割り込みとプレースホルダーに分類できます。

#### プレゼンテーション内のデータ {#data-in-presentation}

データは、一時チャネルで実行され、トリガー後、チャネル内のアセットを変更します。

#### アクションにつながるデータ出力 {#data-out-actionable}

コマンドが液晶画面に送信されると、画面のオンおよびオフが切り替わります例えば、画面の明るさやボリュームなどです。

#### Data out Presentational {#data-out-presentational}

情報をフィードバックループに集約したグラフ。 分析に使用され、イベントを評価および通知します。
