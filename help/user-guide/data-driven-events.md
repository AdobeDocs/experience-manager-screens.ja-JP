---
title: データ駆動型イベント
description: null
page-status-flag: never-activated
contentOwner: jsyal
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 100%

---


# データ駆動型イベント{#data-driven-events}

デジタルサイネージでは、データ駆動型イベントは、デジタルメニューおよびビデオウォールをインタラクティブに使用することで、情報をリアルタイムに伝えることができます。データ駆動型イベントでユーザーエクスペリエンスを最大化できます。

## データ駆動型イベントに対する Context Hub の使用 {#using-context-hub-for-data-driven-events}

AEM Screens では、Context Hub を使用してデータ駆動型イベントを実現します。Context Hub ではリアルタイムに使用できます。

### データ駆動型イベントのカスタマイズ {#categorizing-data-driven-events}

データ駆動型イベントは、次の 4 つの異なるカテゴリに分類されます。

* 運用中のデータ
* プレゼンテーション内のデータ
* 実用的なデータ出力
* プレゼンテーション用のデータ出力

#### 運用中のデータ {#data-in-operational}

このイベントはさらに、チャネル割り込みとプレースホルダーに分類できます。

#### プレゼンテーション内のデータ {#data-in-presentation}

データは、一時チャネルで実行され、トリガー後、チャネル内のアセットを変更します。

#### 実用的なデータ出力 {#data-out-actionable}

コマンドが液晶画面に送信されると、画面のオンおよびオフが切り替わります例えば、画面の明るさやボリュームなど。

#### プレゼンテーション用のデータ出力 {#data-out-presentational}

フィードバックループに情報を収集するグラフ。分析に使用され、イベントを評価および通知します。
