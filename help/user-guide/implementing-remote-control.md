---
title: リモートコントロールの実装
seo-title: Impementing the Remote Control
description: ここでは、Screens のリモート制御機能について説明します。
seo-description: Follow  this page to learn about using the Screens Remote Control Feature.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
source-git-commit: a256f624c4b647deb4cee7668665ad7b576932e7
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Screens リモートコントロールの使用  {#implementing-remote-control}

リモート制御機能を使用すると、Admin UI、チャネルスイッチャー、またはキャッシュのクリアや再読み込みなどの機能に簡単にアクセスできます。 さらに、プレーヤー上のローカルファームウェアのバージョンとシステム情報を確認する方法も提供されます。 この機能は、AEMとの接続が切れた場合に、マウスを接続したり、手の届かない実稼動デバイスで操作したりするのが難しい場合があるので、特に便利です。 解像度の違いにより、マウスを使用して Admin UI を見つけて開くのが非常に困難になるので、これは Samsung RMS を使用する場合にも便利です。

## 共通のリモート制御キーの組み合わせ {#using-common-remote-control}

すべてのプレーヤーで、Screens リモートコントロールで次のキーの組み合わせを使用できます。

1. 管理 UI の切り替え — Ctrl + 1
1. チャネルスイッチャーを切り替え — Ctrl + 2
1. キャッシュをクリア — Ctrl + Alt + 3
1. プレーヤーを再読み込み — Ctrl + 4

## Tizen 固有のリモートコントロールキーの組み合わせ {#using-tizen-remote-control}

Tizen プレーヤーに固有の機能は、ハードウェアリモートまたは Samsung RMS で利用可能なソフトウェアリモートを使用して、次の機能にアクセスできます。

1. A — 管理 UI を切り替え
1. B — チャネルスイッチャーの切り替え
1. C — キャッシュをクリア
1. D — プレーヤーを再読み込み

## その他の使用上の注意 {#using-additional-remote-control}

1. Admin UI が開いている状態で、上下の矢印を使用してタブを移動し、タブ間の情報を表示できます。
1. チャネルスイッチャーを開いた状態で、上下の矢印キーを使用してチャネルを移動し、Enter キー（またはリモートの矢印の中央にあるボタン）を押してチャネルを切り替えることができます。

次の図は、Samsung リモートでの主な使用方法を示しています。
![画像](assets/tizen/remote.png)

>[!NOTE]
>デバイス設定の値 enableAdminUI や enableOSD を false に設定した場合、リモートは管理 UI とチャネルスイッチャーを切り替えません。 また、矢印キーを使用して Admin UI やチャネルをナビゲートすることもできません。 ただし、キャッシュをクリアしてプレーヤーを再読み込みすることはできます。 次のコードを使用して、いずれかのキーボードの組み合わせがインタラクティブコンテンツと競合する場合に、リモート制御機能を無効にできます。

```
require(['util/ScreensDisplay'], function() {window.ScreensDisplay.ignoreRemoteControl = true;}); 
```
