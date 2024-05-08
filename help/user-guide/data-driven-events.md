---
title: データ駆動型イベント
description: ヌル
page-status-flag: never-activated
contentOwner: jsyal
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 12%

---


# データ駆動型イベント{#data-driven-events}

デジタルサイネージでは、データ駆動型のイベントにより、デジタルメニューやビデオウォールをインタラクティブに使用して、情報をリアルタイムで惹きつけ、伝えます。 データ駆動型イベントでユーザーエクスペリエンスを最大化できます。

## データ駆動型イベントに対する Context Hub の使用 {#using-context-hub-for-data-driven-events}

AEM Screens では、Context Hub を使用してデータ駆動型イベントを実現します。Context Hub を使用すると、リアルタイムで使用できます。

### データドリブンイベントの分類 {#categorizing-data-driven-events}

データ駆動型イベントは、次の 4 つの異なるカテゴリに分類されます。

* 運用データ
* プレゼンテーション内のデータ
* アクションにつながるデータ出力
* Data out presentational

#### 運用データ {#data-in-operational}

このイベントは、さらにチャネル割り込みとプレースホルダーに分類できます。

#### プレゼンテーション内のデータ {#data-in-presentation}

データが一時チャンネルで実行中で、トリガー後にチャンネル内のアセットが変更される。

#### アクションにつながるデータ出力 {#data-out-actionable}

LCD 画面にコマンドが送信され、画面のオン/オフが切り替えられたとき。 例えば、画面の明るさやボリュームなどです。

#### Data out presentational {#data-out-presentational}

情報をフィードバックループに集約したグラフ。 Analytics を使用してイベントを評価し、通知します。
