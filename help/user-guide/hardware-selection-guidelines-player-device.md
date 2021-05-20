---
title: プレーヤーデバイスのハードウェア選定ガイドライン
description: プレーヤーデバイスのハードウェア選定ガイドライン
source-git-commit: 7fdd812c71c995424a27db18264ef2db420d5717
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 100%

---


# プレーヤーデバイスのハードウェア選定ガイドライン {#hardware-selection}

この節では、AEM Screens Player のハードウェア選定ガイドラインを示します。

## 重要な検討事項 {#important-considerations}

* PC プレーヤーにもディスプレイパネルまたはプロジェクターにも、常に&#x200B;***商用***&#x200B;または&#x200B;***工業用***&#x200B;クラスのコンポーネントを調達します。

* デジタルサイネージマーケットに商品を提供しているベンダーと常に連携します。
* 周囲の気温や相対湿度などの環境要因を常に考慮に入れます。
* 電源要件と電力調整を常に確認します。
* パフォーマンスのニーズとアプリケーションに必要な I/O ポートを慎重に確認します。

## ハードウェア構成 {#hardware-configurations}

AEM Screens プロジェクトの典型的な使用例に対応するハードウェア構成を次の表にまとめます。

<table>
 <tbody>
  <tr>
   <tr>
   <td><strong>プレーヤー設定</strong></td>
   <td><strong>プロセッサー</strong></td>
   <td><strong>メモリ</strong></td>
   <td><strong>ストレージ SSD</strong></td>
   <td><strong>GPU</strong></td>
   <td><strong>ディスプレイ</strong></td>
   <td><strong>I/O</strong></td>
   <td><strong>典型的な使用例</strong></td>
  </tr>
  <tr>
   <td>基本</td>
   <td>デュアルコア、i3 またはエントリーレベルのクアッドコア Intel® Atom プロセッサー</td>
   <td><p>4 GB のメモリ</p> <p>2 MB のキャッシュ</p> </td>
   <td><p>・Chrome OS：32 GB</p> <p>・Windows：128 GB</p> </td>
   <td>オンボード</td>
   <td>1920 x 1080</td>
   <td>DVI、<br />イーサネット／ワイヤレス、<br />USB x 2</td>
   <td>
    <ul>
     <li>標準フルスクリーンループ<br /> </li>
     <li>日分割</li>
    </ul> </td>
  </tr>
  <tr>
   <td>標準</td>
   <td>クアッドコア、Intel® Core i5 プロセッサー</td>
   <td><p>8 GB のメモリ</p> <p>4 MB のキャッシュ</p> </td>
   <td>128 GBB</td>
   <td>オンボード</td>
   <td>3840 x 2160（4K）</td>
   <td>DVI、HDMI<br /> イーサネット／ワイヤレス、<br />USB x 2</td>
   <td>
    <ul>
     <li>単一ソースの動的コンテンツ</li>
     <li>シンプルインタラクティブ</li>
     <li>1～3 ゾーンレイアウト</li>
    </ul> </td>
  </tr>
  <tr>
   <td>アドバンス</td>
   <td>ハイパースレッディング対応クアッドコア、Intel® Core i7 プロセッサー</td>
   <td><p>16 GB のメモリ</p> <p>8 MB のキャッシュ</p> </td>
   <td>256 GB</td>
   <td>専用グラフィック GPU</td>
   <td>3840 x 2160（4K）</td>
   <td>DVI、HDMI<br /> イーサネット／ワイヤレス、<br />USB x 4</td>
   <td>
    <ul>
     <li>4 つ以上のコンテンツゾーン、同時ビデオ再生</li>
     <li>複数ページインタラクティブ</li>
     <li>複数ソースデータトリガー</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
