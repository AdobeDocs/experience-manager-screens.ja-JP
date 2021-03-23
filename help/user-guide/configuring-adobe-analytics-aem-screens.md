---
title: AEM Screens と連携する Adobe Analytics の設定
seo-title: AEM Screens と連携する Adobe Analytics の設定
description: 'ここでは、オフライン Adobe Analytics を使用したカスタムイベントのシーケンス化と送信について詳しく説明します '
seo-description: 'ここでは、オフライン Adobe Analytics を使用したカスタムイベントのシーケンス化と送信について詳しく説明します '
uuid: e685e553-c05b-4db4-8fa5-9ef45268b094
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: 3cec9266-4032-46b9-9c75-16da64bfea7d
docset: aem65
feature: Screens の管理
role: 管理者、デベロッパー
level: 中間
translation-type: tm+mt
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 99%

---


# AEM Screens と連携する Adobe Analytics の設定 {#configuring-adobe-analytics-with-aem-screens}

>[!CAUTION]
>
>この AEM Screens 機能は、AEM 6.4.2 機能パック 2 と AEM 6.3.3 機能パック 4 がインストールされている場合にのみ使用できます。
>
>このいずれかの機能パックにアクセスするには、アドビサポートに連絡してアクセス権をリクエストする必要があります。アクセス権が付与されると、パッケージ共有から機能パックをダウンロードできるようになります。

ここでは、以下のトピックについて説明します。

* **AEM Screens と連携する Adobe Analytics でのシーケンス化**
* **オフライン Adobe Analytics を使用したカスタムイベントの送信**

## AEM Screens と連携する Adobe Analytics でのシーケンス化 {#sequencing-in-adobe-analytics-with-aem-screens}

***シーケンス化***&#x200B;は、Adobe Analytics サービスをアクティブにするデータストレージサービスで開始されます。チャネルコンテンツは、データテストキャプチャを含んだ Adobe Analytics イベントを Windows I/O に送信し、滞在イベントがトリガーされます。これらのイベントはインデックス DB に保存され、さらにオブジェクトストアに格納されます。管理者が設定したスケジュールに基づいて、データがオブジェクトストアから切り出され、さらにチャンクストアに転送されます。接続時に、最大量のデータ送信が試みられます。

### シーケンス図 {#sequencing-diagram}

次のシーケンス図は、Adobe Analytics と AEM Screens の統合を説明しています。

![analytics_chunking](assets/analytics_chunking.png)

## オフライン Adobe Analytics を使用したカスタムイベントの送信 {#sending-custom-events-using-offline-adobe-analytics}

イベントの標準データモデルを次の表にまとめます。Adobe Analytics に送信されるすべてのフィールドが一覧されています。

<table>
 <tbody>
  <tr>
   <td><strong>セクション</strong></td> 
   <td><strong>プロパティラベル</strong></td> 
   <td><strong>プロパティ名／キー</strong></td> 
   <td><strong>必須</strong></td> 
   <td><strong>データタイプ</strong></td> 
   <td><strong>プロパティタイプ</strong><br /> </td> 
   <td><strong>説明</strong></td> 
  </tr>
  <tr>
   <td><strong><em>コア／イベント</em></strong></td> 
   <td>イベント GUID</td> 
   <td>event.guid</td> 
   <td>推奨</td> 
   <td>文字列</td> 
   <td>UUID</td> 
   <td>イベントのインスタンスを識別する一意の ID</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>イベントの収集日時</td> 
   <td>event.coll_dts</td> 
   <td>オプション</td> 
   <td>文字列</td> 
   <td>タイムスタンプ - UTC</td> 
   <td>収集日時</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>イベントの日時（開始）</td> 
   <td>event.dts_start</td> 
   <td>推奨</td> 
   <td>文字列</td> 
   <td>タイムスタンプ - UTC</td> 
   <td>イベント開始日時。指定しない場合、イベントの時刻はサーバーで受信された時刻と見なされます</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>イベントの日時（終了）</td> 
   <td>event.dts_end</td> 
   <td>オプション</td> 
   <td>文字列</td> 
   <td>タイムスタンプ - UTC</td> 
   <td>イベント完了日時</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>ワークフロー</td> 
   <td>event.workflow</td> 
   <td>推奨</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>ワークフロー名（Screens）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>メイン DMe カテゴリ</td> 
   <td>event.category</td> 
   <td>必須</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>メインカテゴリ（DESKTOP、MOBILE、WEB、PROCESS、SDK、SERVICE、ECOSYSTEM）- <strong>プレーヤーに送信する</strong>イベントタイプの分類</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>サブカテゴリ</td> 
   <td>event.subcategory</td> 
   <td>推奨</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>サブカテゴリ - ワークフローのセクション、スクリーンの領域など（最近使用したファイル、CC ファイル、モバイル作品など）。</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>イベント／アクションタイプ</td> 
   <td>event.type</td> 
   <td>必須</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>イベントタイプ（レンダリング、クリック、ピンチ、ズーム）- 主要なユーザーアクション</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>サブタイプ</td> 
   <td>event.subtype</td> 
   <td>推奨</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>イベントサブタイプ（作成、更新、削除、公開など）- ユーザーアクションの追加の詳細情報</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>オフライン</td> 
   <td>event.offline</td> 
   <td>オプション</td> 
   <td>ブール型</td> 
   <td> </td> 
   <td>アクションがオフライン／オンラインの間にイベントが生成された（オフラインの場合は true、オンラインの場合は false）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>ユーザーエージェント</td> 
   <td>event.user_agent</td> 
   <td>推奨（Web プロパティ）</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>ユーザーエージェント</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>言語／ロケール</td> 
   <td>event.language</td> 
   <td>推奨</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>ユーザーロケールは、RFC 3066 の言語タグ付け規則に基づく文字列です（例：en-US、fr-FR、es-ES）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>デバイス GUID</td> 
   <td>event.device_guid</td> 
   <td>オプション</td> 
   <td>文字列<br /> </td> 
   <td>UUID</td> 
   <td>デバイス GUID（例：マシン ID、IP アドレス + サブネットマスク + ネットワーク ID + ユーザーエージェントのハッシュなど）を識別します。登録時に生成されたプレーヤーユーザー名をここに送信します。</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>回数</td> 
   <td>event.count</td> 
   <td>オプション</td> 
   <td>数値</td> 
   <td> </td> 
   <td>イベントの発生回数 - ビデオの長さを送信します</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>値</td> 
   <td>event.value</td> 
   <td>オプション</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>イベントの値（例：設定のオン／オフ）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>ページ名</td> 
   <td>event.pagename</td> 
   <td>AA に必要</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>Adobe Analytics でのカスタムページ名のサポート</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>URL</td> 
   <td>event.url</td> 
   <td>オプション</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>Web プロパティまたはモバイルスキーマの URL - 完全修飾 URL を含める必要があります</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>エラーコード</td> 
   <td>event.error_code</td> 
   <td> </td> 
   <td>文字列</td> 
   <td> </td> 
   <td>失敗コード</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>エラータイプ</td> 
   <td>event.error_type</td> 
   <td> </td> 
   <td>文字列</td> 
   <td> </td> 
   <td>失敗タイプ</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>エラーの説明</td> 
   <td>event.error_description</td> 
   <td> </td> 
   <td>文字列</td> 
   <td> </td> 
   <td>失敗の説明<br /> </td> 
  </tr>
  <tr>
   <td><strong><em>ソース／元の製品</em></strong></td> 
   <td>名前</td> 
   <td>source.name</td> 
   <td>必須</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>アプリ名（AEM Screens）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>バージョン</td> 
   <td>source.version</td> 
   <td>必須</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>ファームウェアバージョン</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>プラットフォーム</td> 
   <td>source.platform</td> 
   <td>必須</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>navigator.platform</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>デバイス</td> 
   <td>source.device</td> 
   <td>必須（例外あり）</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>プレーヤー名</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>OS バージョン</td> 
   <td>source.os_version</td> 
   <td>必須（例外あり）</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>オペレーティングシステムのバージョン</td> 
  </tr>
  <tr>
   <td><strong><em>コンテンツ</em></strong></td> 
   <td>アクション</td> 
   <td>content.action</td> 
   <td>必須</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>実際に再生されたレンディションを含むアセットの URL</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>MIME タイプ</td> 
   <td>content.mimetype</td> 
   <td>オプション</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>コンテンツの MIME タイプ</td> 
  </tr>
  <tr>
   <td><strong><em>トランザクション</em></strong></td> 
   <td>トランザクション番号</td> 
   <td>trn.number</td> 
   <td>必須</td> 
   <td>文字列</td> 
   <td>UUID</td> 
   <td>一意の ID（UUID v4 に準拠することが望ましい）</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>製品の説明</td> 
   <td>trn.product</td> 
   <td>必須</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>アセット（レンディション以外）の URL</td> 
  </tr>
  <tr>
   <td> </td> 
   <td>数量</td> 
   <td>trn.quantity</td> 
   <td>必須</td> 
   <td>文字列</td> 
   <td> </td> 
   <td>再生時間</td> 
  </tr>
 </tbody>
</table>

