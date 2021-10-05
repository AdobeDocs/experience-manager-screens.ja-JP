---
title: 機能パック 202109 のリリースノート
description: 2021 年 9 月 24 日にリリースされたAEM Screens機能パック202109について説明します。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: 6d9dab9fd59289aafdb688682fea47589d3ec873
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 44%

---

# 機能パック 202109 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>最新バージョンの Adobe Experience Manager（AEM）にアップグレードすることをお勧めします。Screens では、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供しています。

## 入手方法 {#availability}

AEM Screens は、AEM 6.5 機能パック 9 をリリースしました。

Adobe ID を使用して、AEM Screens 6.5.9 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して「**AEM 6.5 Screens FP9**」というタイトルが付いた最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens機能パック202109のリリース日は 2021 年 9 月 23 日です。

### 新機能 {#what-is-new}

* **ビデオのサムネールサポート**

   ビデオのサムネールが AEM Screens でサポートされるようになりました。コンテンツ作成者は、ビデオのサムネールを定義して、その画像をプレースホルダーとして使用できるようにし、実際のビデオを該当チームが仕上げている間に、コンテンツの再生とターゲティングを適切にテストすることができます。その画像は、ビデオの再生に失敗した場合でも使用できます。
詳しくは、[ ビデオのサムネールのサポート ](/help/user-guide/thumbnail-support.md) を参照してください。

* **基本的な再生モニタリング**

   AEM Screens では、基本的な再生モニタリングをサポートするようになりました。プレーヤーでは、各 ping（デフォルトは 30 秒）で様々な再生指標がレポートされるようになります。指標に基づいて、様々なエッジケース（動きのないエクスペリエンス、空白の画面、スケジュールの問題など）を検出できます。この機能を使用すると、プレーヤーがコンテンツを適切に再生しているかどうかをチームがリモートで監視できます。また、空白の画面やフィールド内のエクスペリエンスの不具合に対する反応性が向上し、不具合のあるエクスペリエンスがエンドユーザーに表示されるリスクが低くなります。
詳しくは、[ 基本的な再生監視 ](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/installing-screens-player.html?lang=en#playback-monitoring) を参照してください。

* **コンテンツ割り当てレポートの更新**

   コンテンツ割り当てレポートが最適化され、ユーザーエクスペリエンスが向上しました。 ダウンロード可能なレポートでは、1 つのスプレッドシートタブに場所、ディスプレイ、デバイスなどのプレーヤー関連のエンティティが改善され、他のタブにチャネルやアセットなどのコンテンツプロバイダー情報が表示されます。
詳しくは、[ コンテンツ割り当てレポート ](/help/user-guide/content-assignment-report.md) を参照してください。

* **アダプティブレンディション**

   アダプティブレンディションを使用すると、顧客定義のルールに基づいて、デバイスに最適なレンディションをデバイスで自動的に選択できます。

   AEM Screens開発者は、すべてのコンテンツバリエーションを手動で作成する必要なく、デバイス固有のアセットレンディションをダウンロードして自動的に再生するように設定できるようになりました。 [ アダプティブレンディションを参照してください。アーキテクチャの概要と設定 ](/help/user-guide/adaptive-renditions.md) を参照してください。

   また、AEM Screensコンテンツ作成者は、アダプティブレンディションを使用するようにアセットを設定し、大規模なネットワーク用にデバイスを移行して、AEM Screensチャネルでこの機能を利用することもできます。 詳しくは、[AEM Screensでのアダプティブレンディションの使用 ](/help/user-guide/using-adaptive-renditions.md) を参照してください。

* **V3 マニフェストのサポート**

   マニフェストバージョン v3 に対応するように Dispatcher を設定できるようになりました。詳しくは、[マニフェストバージョン v3 に対応した Dispatcher の設定](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=ja#configuring-dispatcherv3)を参照してください。
さらに、カスタムコンポーネントを v3 マニフェストの一部として使用する場合は、[カスタムハンドラーのテンプレート](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=ja#custom-handlers)を参照してください。


### バグ修正 {#bug-fixes}

**プレーヤーサイド**

* アセットをレンディションに置き換えることで、ファイルのキャッシュエラーを解決しました。

* レンディションマッピングが存在する場合、プレーヤーがアセットレンディションのみを公開するようになりました。

* 応答が有効な JSON でない場合に再認証する ping を強化しました。

* 数値のチャネル名/役割によって画面が空白になる。

* スマート同期を使用して最適化されたレンディションをダウンロードします。

* マッピングをレンディションキーのリストに変換しました。

* Windows プレーヤーでの `cmd.exe` および `reg.exe` へのアクセスを削除しました。

* プレーヤーは、最後に成功した再生イベントを報告する必要があります。

* プレーヤーは、再生ステータスを報告する必要があります。

* `ALL` キャッシュがクリアされても、プレーヤーがアセットを再ダウンロードしない。

* プレーヤー管理者は、プレーヤー名を選択できるようになりました。

* ディスプレイからチャネル割り当てを削除しても、プレーヤーには反映されません。

* チャネル更新のダウンロード中にプレーヤーが再読み込みされると、プレーヤーは更新を無視します。

* 埋め込みページコンポーネントは、タッチイベントに従うようになりました。

* Tizen プレーヤーのリモートプロビジョニングがサポートされるようになりました。

**サーバー側**

* ターゲットビデオが表示されない
* 放送表示データのレース状態から後続へ。

* チャネルプレビューは、ビデオを含むチャネルでは機能しません。

* 分割画面チャネルのプレビューモードが空白で表示される。

* ビデオサムネールは、有効なアダプティブレンディションで空白でレンダリングされます。

* 参照先のページが公開された場合に、チャネルマニフェストを自動的に更新します。

* 削除されたデバイスで、Screens レプリケーションキューがブロックされなくなりました。

* マニフェストに、ターゲットコンテンツまたは Sites 埋め込みページが含まれていません。 この問題は修正されました。

* 新しいコア画像コンポーネントがチャネルマニフェストに追加されました。

* スマート同期を使用した最適化されたレンディションのダウンロードがサポートされるようになりました。

* すべてのアセットに最適化されたレンディションを再生します。

* 複数のコンテンツプロバイダータイプのサポートを追加

* 埋め込みシーケンス再生戦略が壊れ、これが修正されました。

* HTML エントリに対してリクエストパラメーター `wcmmode` を使用してオフラインマニフェストをキャッシュできなくします。

* 空の動的埋め込みシーケンスが原因で、画面が空白になることがありました。

* プレーヤーで再生ステータスが報告されるようになりました。

* ビデオが `Tiny mode` で再生され、デバイスでフルスクリーンビデオとして再生されなかったので、問題が修正されました。

### リリースされている AEM Screens Player {#released-aem-screens-players}

AEM Screens 6.5 機能パック 9 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Tizen
* Android
* Linux

#### AEM Screens Player のダウンロード   {#aem-screens-player-downloads}

最新の AEM Screens Player のダウンロードとバグ修正について詳しくは、**[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/index.html)**&#x200B;を参照してください。
