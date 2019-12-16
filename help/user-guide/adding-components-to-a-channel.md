---
title: チャネルへのコンポーネントの追加
seo-title: チャネルへのコンポーネントの追加
description: このページに従って、AEM Screens プロジェクトでのチャネルへのコンポーネントの追加について学びます。
seo-description: このページに従って、AEM Screens プロジェクトでのチャネルへのコンポーネントの追加について学びます。
uuid: 205d0edd-a696-47d0-a859-5f44d48c5e4a
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: bfbdd6eb-4921-4c2d-a179-1cac4583d568
docset: aem65
translation-type: tm+mt
source-git-commit: cec2a2f8b056bf713e56a9fab08d88e29263820b

---


# チャネルへのコンポーネントの追加{#adding-components-to-a-channel}

コンポーネントは、AEM（Adobe Experience Manager）エクスペリエンスの基本的要素です。多数のコンポーネントを使用でき、AEM Screens プロジェクトのチャネルに追加できます。

## AEM Screens のコンポーネント {#components-in-aem-screens}

AEM Screens には、スクリーンプロジェクトで使用できる様々な AEM コンポーネントが用意されています。

### AEM Screens コンポーネントの表示 {#viewing-aem-screens-components}

AEM Screens プロジェクトを作成する場合はいつでも、プロジェクトに追加できるデフォルトコンポーネントのリストが表示されます。

スクリーンプロジェクトのデフォルトコンポーネントを表示するには、次の手順に従います。

1. チャネルを選択します（例：**We.Retail In-Store**／**Channels**／**Idle Channel**）。

1. アクションバーから「**編集**」をクリックして、AEM エディターを開きます。
1. サイドバーから **+** アイコンをクリックして、コンポーネントを開きます。
1. 次に示す図のように、AEM Screens プロジェクトにデフォルトで含まれるすべてのコンポーネントが表示されます。

![screen_shot_2017-12-18at21350pm](assets/screen_shot_2017-12-18at21350pm.png)

### 新しいコンポーネントの追加 {#adding-a-new-component}

AEM には、他のコンポーネントが多数用意されています。AEM Screens と互換性のある（デフォルトで含まれていない）他のコンポーネントをプロジェクトに常に追加できます。

次に、AEM Screens プロジェクトへの Livefyre コンポーネントの追加例を示します。

1. 新しいコンポーネントを追加するチャネルを選択します（例：**We.Retail In-Store**／**Channels**／**Idle Channel**）。

1. アクションバーから「**編集**」をクリックして、エディターを開きます。
1. Select **Design** mode.
1. 右側のデザインエディター全体を選択して、設定シンボルをクリックし、**ParSys Design** ダイアログボックスを開きます。
1. AEM Screens プロジェクトに読み込むコンポーネントを選択できます。次の例は、AEM Screensプロジェクトに **Livefyre** コンポーネントを追加した例です。

![adding_components](assets/adding_components.gif)

>[!NOTE]
>
>同様に、AEM Screens と互換性のある他の新しいコンポーネントをプロジェクトに好きなだけ追加できます。

## AEM Screen コンポーネントについて {#understanding-aem-screen-components}

次の節では、プロジェクトで使用できるAEM Screensコンポーネントについて説明します。

>[!NOTE]
>
>任意のコンポーネントのプロパティを表示するには、コンポーネントを選択し、ハンマーアイコンをクリックします。

### アプリケーション {#application}

**アプリケーション**&#x200B;コンポーネントを使用すると、チャネルにアプリケーションを追加できます。

アプリケーションコンポーネントには、次のプロパティがあります。

| **プロパティ** | **説明** |
|---|---|
| ***アプリケーションパス*** | アプリケーションが存在する絶対パスを選択します。 |
| ***デュレーション (ms)*** | アプリケーションのデュレーションを選択します。デフォルトでは、期間は —1に設定されています。つまり、要素は永久に実行されます（つまり、単一ページアプリ）。 デュレーションの値を 0 より大きい値に設定すると、指定されたデュレーションの間要素が表示されてから次のアプリケーションに移動します。 |

次に、アプリケーションコンポーネントを埋め込んでプロパティをプレビューする方法の例を示します。

![adding_componentsapplication](assets/adding_componentsapplication.gif)

>[!NOTE]
>
>前述の例を参照して、次の各コンポーネントのプロパティを表示します。

### チャネル {#channel}

**チャネル**&#x200B;コンポーネントを使用すると、プロジェクトにチャネル全体を追加できます。

チャネルコンポーネントには、次のプロパティがあります。

<table>
 <tbody>
  <tr>
   <td><strong>プロパティ</strong></td>
   <td><strong>説明</strong></td>
  </tr>
  <tr>
   <td><strong><em>チャネルパス</em></strong></td>
   <td>アプリケーションが存在するこの絶対パスを選択します。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>デュレーション (ms)</em></strong></td>
   <td>チャネルのデュレーション全体を選択します。時間を —1に設定した場合、埋め込まれたチャネルは特定のチャネルでその長さだけ実行されます。</td>
  </tr>
 </tbody>
</table>

### 埋め込みページ {#embedded-page}

**埋め込みページ**&#x200B;を使用すると、プロジェクトに埋め込みページを追加できます。例えば、Web アプリケーションや製品カタログにできます。

埋め込みページには、次のプロパティがあります。

<table>
 <tbody>
  <tr>
   <td><strong>プロパティ</strong></td>
   <td><strong>説明</strong></td>
  </tr>
  <tr>
   <td><strong><em>ページパス<br /> </em></strong></td>
   <td>チャネルが存在するこの絶対パスを選択します。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>デュレーション (ms)</em></strong></td>
   <td>チャネルのデュレーション全体を選択します。時間を —1に設定した場合、埋め込まれたチャネルは特定のチャネルでその長さだけ実行されます。</td>
  </tr>
 </tbody>
</table>

### 埋め込みシーケンス {#embedded-sequence}

>[!NOTE]
>
>Refer to [Embedded Sequences](embedded-sequences.md) under Authoring Screens section, to learn in detail about embedded sequences.

埋め込みシーケンスを使用すると、既存のチャネル（他のアセットを含む）内に埋め込みシーケンスチャネルを追加できます。

埋め込みシーケンスには、次のページプロパティがあります。

<table>
 <tbody>
  <tr>
   <td><strong>プロパティ</strong></td>
   <td><strong>説明</strong></td>
  </tr>
  <tr>
   <td>チャネルパス</td>
   <td>チャネルに追加するシーケンスの絶対パスを選択します。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>デュレーション (ms)</em></strong></td>
   <td>チャネルのデュレーション全体を選択します。時間を —1に設定した場合、埋め込まれたチャネルは特定のチャネルでその長さだけ実行されます。</td>
  </tr>
  <tr>
   <td><strong><em>方法</em></strong></td>
   <td>Set it to <strong>original</strong> or <strong>single</strong>. Setting the value to <strong>original</strong> means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is <strong>single</strong> and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)</td>
  </tr>
 </tbody>
</table>

### 動的埋め込みシーケンス {#dynamic-embedded-sequence}

動的埋め込みシーケンスを使用すると、チャネルロールによることを除いて、前述の方法と同じようにシーケンスを追加できます。

Refer to [Embedded Sequences](embedded-sequences.md) under Authoring Screens section, to learn in detail about embedded sequences.

動的埋め込みシーケンスには、次のプロパティがあります。

<table>
 <tbody>
  <tr>
   <td><strong>プロパティ</strong></td>
   <td><strong>説明</strong></td>
  </tr>
  <tr>
   <td><strong><em>チャネル割り当ての役割</em></strong><br /> </td>
   <td>チャネルロールを入力します。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>デュレーション (ms)</em></strong></td>
   <td>チャネルのデュレーション全体を選択します。時間を —1に設定した場合、埋め込まれたチャネルは特定のチャネルでその長さだけ実行されます。</td>
  </tr>
  <tr>
   <td><strong><em>方法</em></strong></td>
   <td>Set it to <strong>original</strong> or <strong>single</strong>. Setting the value to <strong>original</strong> means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is <strong>single</strong> and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)</td>
  </tr>
 </tbody>
</table>

### エクスペリエンスフラグメント {#experience-fragment}

エクスペリエンスフラグメントを使用すると、エクスペリエンスフラグメント（ページ内で参照できるコンテンツやレイアウトを含む1つ以上のコンポーネントのグループ）をAEM Screensチャネルに追加できます。 コンポーネントをAEMエディターにドラッグ&amp;ドロップし、エクスペリエンスフラグメントを選択します。

エクスペリエンスフラグメントを作成し、それをAEM Screensプロジェクトに活用する方法について詳しくは、「エクスペリエンスフラグメントの使用」を [参照してくださ](experience-fragments-in-screens.md)い。

![exp](assets/exp.gif)

| **プロパティ** | **説明** |
|---|---|
| **エクスペリエンスフラグメント** |
| ***エクスペリエンスフラグメント*** | エクスペリエンスフラグメントを選択します。 |
| ***期間*** | チャネルで再生するエクスペリエンスフラグメントの継続時間全体を選択します。 |
| **オフライン設定** |
| ***クライアント側ライブラリ*** | JavaScriptファイルとCSSファイル。 |
| ***静的ファイル*** | オフライン設定としてエクスペリエンスフラグメントに追加できる静的ファイル。 |

>[!NOTE]
>
>このコ **ンポーネントから追加する** Static FilesとStatic Filesは **、設定済みの** Client-side Libraries **とExperience Fragment****** Propertiesクライアントから追加したStatic Filesに追加されます。

### 画像 {#image}

画像を使用すると、チャネルに画像を追加できます。

イメージアセットには、「**画像**」、「**アクセシビリティ**」および「**シーケンス**」の 3 つのタブがあります。

| **プロパティ** | **説明** |
|---|---|
| **画像** |
| ***イメージアセット*** | イメージアセットを選択します。 |
| ***タイトル*** | 画像のタイトル。 |
| ***リンク先*** | 画像にリンクを追加します。 |
| ***説明*** | 画像の概要。 |
| ***サイズ*** | 画像のサイズ。 |
| **アクセシビリティ** |
| ***代替テキスト*** | 画像の代替テキスト。 |
| **シーケンス** |
| ***期間*** | デフォルトでは、期間は *8000 msに設定されます*。 画像の再生時間を変更する場合は、「時間」フィールドを更新 **します** 。 |

### 切り替え {#transition}

切り替えコンポーネントを使用すると、スクリーンプロジェクトに切り替えを追加できます。

次の画像は、エディターに（ドラッグ&amp;ドロップによって追加された）トランジションコンポーネントを示しています。

![screen_shot_2019-07-25at104237am](assets/screen_shot_2019-07-25at104237am.png)

トランジションアイコンを選択し、設定 **（レンチアイコン）をクリックして、トランジションダイアログ** ボックスを開きます **** 。 このダイアログボックスには3つのタブが含まれます。

* **切り替え**
* **シーケンス**
* **Activation**

>[!NOTE]
>
>デフォルトでは、シーケンスは600 msに設定されています。 「シーケンス」タブを使用して、トランジションシーケンスを別の値に更新 **できます** 。

![遷移](assets/transition.gif)

切り替えコンポーネントには、次のプロパティがあります。

<table>
 <tbody>
  <tr>
   <td><strong>プロパティ</strong></td>
   <td><strong>説明</strong></td>
  </tr>
  <tr>
   <td><strong>切り替え</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>種類</em></strong></td>
   <td><p>前の要素と後の要素の間の切り替えのタイプ。トランジション <strong>タイプ</strong> には、次のオプションが含まれます。</p>
    <ul>
     <li><strong>標準</strong></li>
     <li><strong>フェード</strong></li>
     <li><strong>右からスライドイン</strong></li>
     <li><strong>左からスライドイン</strong></li>
     <li><strong>上からスライドイン</strong></li>
     <li><strong>下からスライドイン</strong></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>シーケンス</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>期間</em></strong></td>
   <td>切り替えのデュレーション全体を選択します。デフォルトでは、600 msに設定されています。</td>
  </tr>
  <tr>
   <td><strong>Activation</strong></td>
   <td></td>
  </tr>
  <tr>
   <td><strong><em>アクティブ：開始</em></strong></td>
   <td>移行がアクティブになるタイミングを示すタイムスタンプ。<br /> </td>
  </tr>
  <tr>
   <td><strong><em>アクティブ期間</em></strong></td>
   <td>移行がアクティブになるまでを示すタイムスタンプ。</td>
  </tr>
  <tr>
   <td><strong><em>スケジュール</em></strong></td>
   <td>定義済みのスケジュールを追加します。</td>
  </tr>
 </tbody>
</table>

### ビデオ {#video}

ビデオコンポーネントを使用すると、スクリーンプロジェクトにビデオを追加できます。

ビデオコンポーネントには、次のプロパティがあります。

<table>
 <tbody>
  <tr>
   <td><strong>プロパティ</strong></td>
   <td><strong>説明</strong></td>
  </tr>
  <tr>
   <td><em><strong>ビデオアセット</strong></em></td>
   <td>ビデオへのリンクを選択します。</td>
  </tr>
  <tr>
   <td><em><strong>期間</strong></em></td>
   <td>ビデオのデュレーションを選択します。デフォルトでは、継続時間は —1に設定され、要素は永久に実行されます。 デュレーションの値を 0 より大きい値に設定すると、指定されたデュレーションの間要素が表示されてから次のアプリケーションに移動します。<br /> </td>
  </tr>
  <tr>
   <td><em><strong>レンダリング</strong></em></td>
   <td><p>ビデオの縦横比がスクリーンに合わない場合、<strong>含む</strong>または<strong>カバー</strong>のどちらかでレンダリングを調整できます。</p> <p><em>含む</em>は、ビデオ全体が表示され、足りない領域は黒い境界線で埋められることを意味します。</p> <p><em>カバー</em>は、ビデオが表示域全体を占めますが、サイドのオーバーフローする部分は非表示になります。</p> </td>
  </tr>
  <tr>
   <td><em><strong>サイズ</strong></em></td>
   <td>ビデオのサイズ。</td>
  </tr>
 </tbody>
</table>

