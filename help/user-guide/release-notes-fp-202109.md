---
title: 機能パック 202109 のリリースノート
description: 2021年9月24日にリリースされたAEM Screens機能パック202109について説明します。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e1794013-59ce-4ddc-93c0-601668c75cd1
source-git-commit: 609cb66ea1cc34262bb57c020eb07fd18bd31f0d
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 16%

---

# 機能パック 202109 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>最新バージョンの Adobe Experience Manager（AEM）にアップグレードすることをお勧めします。Screens では、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供しています。

## 入手方法 {#availability}

AEM Screens は、AEM 6.5 機能パック 9 をリリースしました。

Adobe ID を使用して、AEM Screens 6.5.9 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して「**AEM 6.5 Screens FP9**」というタイトルが付いた最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens機能パック202109のリリース日は2021年9月24日です。

### 新機能 {#what-is-new}

* **ビデオのサムネールのサポート**

   でのビデオのサムネールのサポートがAEM Screensでサポートされるようになりました。 コンテンツ作成者は、ビデオのサムネールを定義して、画像をプレースホルダーとして使用し、コンテンツの再生とターゲティングを適切にテストしながら、実際のビデオを適切なチームで確定できます。 ビデオの再生に失敗した場合にも、画像を使用できます。
詳しくは、[ビデオのサムネールのサポート](/help/user-guide/thumbnail-support.md)を参照してください。

* **基本的な再生の監視**

   AEM Screensは、基本的な再生監視をサポートするようになりました。 プレーヤーでは、各pingで様々な再生指標がレポートされるようになります（デフォルトは30秒）。 指標に基づいて、様々なエッジケース（動きのないエクスペリエンス、空白画面、スケジュールの問題など）を検出できます。 この機能を使用すると、プレーヤーがコンテンツを適切に再生しているかどうかをチームがリモートで監視し、空白の画面やフィールド内のエクスペリエンスの破損に対する反応性を向上し、エンドユーザーに壊れたエクスペリエンスを表示するリスクを低減できます。
詳しくは、[基本的な再生監視](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/installing-screens-player.html?lang=en#playback-monitoring)を参照してください。

* **コンテンツ割り当てレポートの更新**

   コンテンツ割り当てレポートが最適化され、ユーザーエクスペリエンスが強化されました。 ダウンロード可能なレポートでは、場所、ディスプレイ、デバイスなどのプレーヤー関連のエンティティが1つのスプレッドシートタブに表示され、コンテンツプロバイダー情報（チャネルやアセットなど）が他のタブに表示されます。
詳しくは、[コンテンツ割り当てレポート](/help/user-guide/content-assignment-report.md)を参照してください。

* **アダプティブレンディション**

   アダプティブレンディションを使用すると、デバイスは、顧客定義のルールに基づいて、デバイスに最適なレンディションを自動的に選択できます。

   AEM Screens開発者は、すべてのコンテンツバリエーションを手動で作成することなく、デバイス固有のアセットレンディションをダウンロードして自動的に再生するように設定できるようになりました。 [アダプティブレンディションを参照してください。アーキテクチャの概要と設定](/help/user-guide/adaptive-renditions.md)を参照してください。

   さらに、AEM Screensコンテンツ作成者は、AEM Screensプロジェクトでアダプティブレンディションを使用し、大規模なネットワークに移行戦略を適用できるようになりました。

* **V3マニフェストのサポート**

   マニフェストバージョンv3用にDispatcherを設定できるようになりました。 詳しくは、 [マニフェストバージョンv3](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens.html?lang=en#configuring-dispatcherv3)のDispatcherの設定を参照してください。
また、カスタムコンポーネントをv3マニフェストの一部として使用する場合は、「[カスタムハンドラーのテンプレート](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/developing/developing-custom-component-tutorial-develop.html?lang=en#custom-handlers)」を参照してください。


### バグ修正 {#bug-fixes}

**プレーヤーサイド**

* アセットをレンディションに置き換えることで、ファイルキャッシュのエラーを解決しました。

* レンディションマッピングが存在する場合、プレーヤーがアセットレンディションのみを公開するようになりました。

* 応答が有効なJSONでない場合に再認証するpingの機能が強化されました。

* 数値のチャネル名/役割により画面が空白になる。

* スマート同期を使用して最適化されたレンディションをダウンロードします。

* マッピングをレンディションキーのリストに変換しました。

* Windowsプレーヤーでの`cmd.exe`および`reg.exe`へのアクセスを削除しました。

* プレーヤーは、最後に成功した再生イベントを報告する必要があります。

* プレーヤーは、再生ステータスを報告する必要があります。

* `ALL`キャッシュがクリアされると、プレーヤーがアセットを再ダウンロードしない。

* プレーヤー管理者は、プレーヤー名を選択できるようになりました。

* ディスプレイからチャネル割り当てを削除しても、プレーヤーには反映されません。

* チャネル更新のダウンロード中にプレーヤーが再読み込みされると、プレーヤーは更新を無視します。

* 埋め込みページコンポーネントは、タッチイベントに従うようになりました。

* Tizenプレーヤーのリモートプロビジョニングがサポートされるようになりました。

**サーバー側**

* Targetビデオが表示されない
* 放送表示データのシーケンスへの競合状態。

* チャネルプレビューは、ビデオを含むチャネルでは機能しません。

* 分割画面チャネルのプレビューモードが空白で表示される。

* アダプティブレンディションが有効な場合、ビデオサムネールは空白でレンダリングされます。

* 参照されるページが公開された場合に、チャネルマニフェストを自動的に更新します。

* 削除されたデバイスで、Screensレプリケーションキューがブロックされなくなりました。

* マニフェストにターゲットコンテンツまたはSites埋め込みページが含まれていません。 この問題は修正されました。

* 新しいコア画像コンポーネントがチャネルマニフェストに追加されました。

* スマート同期を使用した最適化されたレンディションのダウンロードがサポートされるようになりました。

* すべてのアセットに対して最適化されたレンディションを再生します。

* 複数のコンテンツプロバイダータイプのサポートを追加

* 埋め込みシーケンス再生戦略が壊れ、これが修正されました。

* HTMLエントリのリクエストパラメーター`wcmmode`を使用してオフラインマニフェストをキャッシュできなくします。

* 動的埋め込みシーケンスが空の場合、画面が空白になることがある。

* プレーヤーが再生ステータスを報告するようになりました。

* ビデオが`Tiny mode`で再生され、デバイスでフルスクリーンビデオとして再生されなかったので、問題が修正されました。

### リリースされている AEM Screens Player {#released-aem-screens-players}

AEM Screens 6.5 機能パック 9 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Tizen
* Android
* Linux

#### AEM Screens Player のダウンロード   {#aem-screens-player-downloads}

最新の AEM Screens Player のダウンロードとバグ修正について詳しくは、**[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/index.html)**&#x200B;を参照してください。
