<!-- 
# The Customizer JavaScript API
 -->

# カスタマイザー JavaScript API

<!-- 
In WordPress 4.1, newly-expanded JavaScript APIs were introduced for all customizer objects. The entire JavaScript API is currently located in a single file, [wp-admin/js/customize-controls.js](https://core.trac.wordpress.org/browser/trunk/src/js/_enqueues/wp/customize/controls.js), which contains models for all objects, core custom controls, and more.
 -->

WordPress v4.1では、すべてのカスタマイザーオブジェクト向けに新たに拡張された JavaScript API が導入されました。現在、JavaScript API 全体は単一のファイル [`wp-admin/js/customize-controls.js`](https://core.trac.wordpress.org/browser/trunk/src/js/_enqueues/wp/customize/controls.js) に配置されており、すべてのオブジェクトのモデル、コアのカスタムコントロールなどが含まれています。

<!-- 
## Preview JS and Controls JS
 -->

## JS のプレビューと、JS の制御

<!-- 
The customizer app is currently split into two distinct areas: the customizer controls “pane” and the customize preview. The preview is currently in an iframe, meaning that all JS runs either in the controls pane or in the preview. The postMessage API is used to communicate between the preview and the controls.
 -->

カスタマイザーアプリは現在、以下の2つの独立したエリアに分割されています: カスタマイザーコントロール「ペイン」とカスタマイズプレビューです。プレビューは現在 iframe 内に配置されており、すべての JavaScript は、コントロールペインまたはプレビューのいずれかで実行されます。プレビューとコントロール間の通信には、postMessage API が使用されています。

<!-- 
Most themes only implement JavaScript in the customize preview, and use it to implement instant previewing of settings via postMessage. However, JS on the controls side can be used for many things, such as dynamically showing and hiding controls based on the values of other settings, changing the previewed URL, focusing parts of the preview, and more. Here’s an example from core of controls-side JS that interacts with the preview, in this case changing the previewed URL when the page for posts changes:
 -->

ほとんどのテーマでは、カスタマイズプレビュー内で JavaScript を実装し、postMessage を介した設定の即時プレビューを実現しています。しかし、コントロール側の JS は、他の設定値にもとづいてコントロールを動的に表示/非表示にしたり、プレビュー URL を変更したり、プレビューの一部をフォーカスしたりなど、さまざまな用途に使用できます。以下は、コアのコントロール側 JS がプレビューとインタラクションする例で、本ケースでは投稿ページが変更された際にプレビュー対象の URL を変更しています:

```javascript
// Change the previewed URL to the selected page when changing the page_for_posts.
wp.customize(
	'page_for_posts',
	function( setting ) {
		setting.bind( function( pageId ) {
			pageId = parseInt( pageId, 10 );
			if ( pageId > 0 ) {
				api.previewer.previewUrl.set( api.settings.url.home + '?page_id=' + pageId );
			}
		});
	}
);
```

<!-- 
Similar logic can be used to `activate` UI objects based on the value of a setting. The Twenty Seventeen theme includes some useful examples for leveraging the customize JS API for improved user experience. Note that there is one JS file for the controls pane, named `customize-controls.js` and one file for the customize preview, named customize-preview.js. For clarity, all themes and plugins are recommended to follow this naming convention, even if customize JS is only provided in the controls or preview but not both.
 -->

同様のロジックを用いて、設定値にもとづいて UI オブジェクトを `activate` できます。Twenty Seventeen テーマには、ユーザーエクスペリエンス向上のために カスタマイズ JS API を活用する有用な例がいくつか含まれています。コントロールパネル用には `customize-controls.js` という名前の JS ファイルが、カスタマイズプレビュー用には `customize-preview.js` という名前のファイルが、それぞれ用意されている点に留意しましょう。明確化のため、カスタマイズ JS がコントロールパネルのみ、またはプレビューのみに提供されている場合でも、すべてのテーマとプラグインは、この命名規則に従うことが推奨されます。

<!-- 
The rest of this page is dedicated primarily to the controls-side JS API that was built-out in WordPress 4.1.
 -->

本ページの後半は、主に WordPress v4.1で実装された、コントロール側 JS API について解説します。

<!-- 
## Models for Controls, Sections, and Panels
 -->

## コントロール、セクション、およびパネル用のモデル

<!-- 
As in PHP, each Customizer object type has a corresponding object in JavaScript. There are `wp.customize.Control,` `wp.customize.Panel,` and `wp.customize.Section` models, as well as `wp.customize.panel,` `wp.customize.section, and` `wp.customize.control` collections (yes, they are singular) that store all control instances. You can iterate over panels, sections, and controls via:
 -->

PHP と同様に、各「カスタマイザー」オブジェクトタイプには、JavaScript で対応するオブジェクトが存在します。`wp.customize.Control`、`wp.customize.Panel`、`wp.customize.Section` モデルに加え、すべてのコントロールインスタンスを格納する `wp.customize.panel`、`wp.customize.section`、`wp.customize.control` コレクション (そう、これらはいずれも単数形) があります。以下を通じて、パネル、セクション、コントロールを反復処理できます:

```javascript
wp.customize.panel.each( function ( panel ) { /* ... */ } );
wp.customize.section.each( function ( section ) { /* ... */ } );
wp.customize.control.each( function ( control ) { /* ... */ } );
```

<!-- 
## Relating Controls, Sections, and Panels together
 -->

## コントロール、セクション、パネル相互の連携

<!-- 
When registering a new control in PHP, you pass in the parent section ID:
 -->

PHP で新規コントロールを登録する際、親セクション ID を渡します:

```php
<?php
$wp_customize->add_control(
	'blogname',
	array(
		'label'   => __( 'Site Title' ),
		'section' => 'title_tagline',
	)
);
?>
```

<!-- 
In the JavaScript API, a control’s section can be obtained predictably:
 -->

JavaScript API では、コントロールのセクションを予測可能な方法で取得できます:

```javascript
id = wp.customize.control( 'blogname' ).section(); // returns title_tagline by default
```

<!-- 
To get the section object from the ID, look up the section by the ID as normal: `wp.customize.section( id )`.
 -->

ID からセクションオブジェクトを取得するには、通常通り、ID でセクションを参照します: `wp.customize.section(id)`。

<!-- 
You can move a control to another section using this `section` state as well, here moving it to the Navigation section:
 -->

同様に、この `section` ステートを使用してコントロールを別のセクションに移動でき、ここでは「ナビゲーション」セクションに移動します:

```javascript
wp.customize.control( 'blogname' ).section( 'nav' );
```

<!-- 
Likewise, you can get a section’s panel ID in the same way:
 -->

同様に、セクションのパネル ID も、同様の方法で取得できます:

```javascript
id = wp.customize.section( 'sidebar-widgets-sidebar-1' ).panel(); // returns widgets by default
```

<!-- 
You can go the other way as well, to get the children of panels and sections:  
 -->

同様に逆方向にも進め、パネルやセクションの子要素を取得できます:  

```javascript
sections = wp.customize.panel( 'widgets' ).sections();controls = wp.customize.section( 'title_tagline' ).controls();
```

<!-- 
You can use these to move all controls from one section to another:
 -->

これらを使用して、すべてのコントロールを、あるセクションから別のセクションに移動できます:

```javascript
_.each( wp.customize.section( 'title_tagline' ).controls(), function ( control ) {  
    control.section( 'nav' );
} );
```

<!-- 
## Contextual Panels, Sections, and Controls
 -->

## コンテキストに応じたパネル、セクション、コントロール

<!-- 
`Control,` `Panel,` and `Section` instances have an `active` state (a `wp.customize.Value` instance). When the `active` state changes, the panel, section, and control instances invoke their respective `onChangeActive` method, which by default slides the container element up and down, if `false` and `true` respectively. There are also `activate()` and `deactivate()` methods now for manipulating this `active` state, for panels, sections, and controls. The primary purpose of these states is to show or hide the object without removing it entirely from the Customizer.
 -->

`Control`、`Panel`、`Section` インスタンスには `active` ステート (`wp.customize.Value` インスタンス) があります。`active` ステートが変更されると、パネル、セクション、コントロールの各インスタンスはそれぞれの `onChangeActive` メソッドを呼び出し、デフォルトでは、コンテナ要素をそれぞれ `false` の場合は下に、`true` の場合は上に、スライドさせます。また、パネル、セクション、コントロールの `active` ステートを操作するための `activate()` および `deactivate()` メソッドが、新たに追加されました。これらのステートの主目的は、オブジェクトを完全に削除することなく、「カスタマイザー」上で表示/非表示を切り替えることです。

```javascript
wp.customize.section( 'nav' ).deactivate(); // slide up
wp.customize.section( 'nav' ).activate({ duration: 1000 }); // slide down slowly
wp.customize.section( 'colors' ).deactivate({ duration: 0 }); // hide immediately
wp.customize.section( 'nav' ).deactivate({ completeCallback:
function () {  
    wp.customize.section( 'colors' ).activate(); // show after nav hides completely
} } );
```

<!-- 
Note that manually changing the `active` state would only stick until the preview refreshes or loads another URL. The `activate()`/`deactivate()` methods are designed to follow the pattern of the new `expanded` state.
 -->

手動で `active` ステートを変更しても、プレビューがリフレッシュされるか別の URL がロードされるまでしか持続しないことに留意しましょう。`activate()`/`deactivate()` メソッドは、新しい `expanded` ステートのパターンに従うように設計されています。

<!-- 
## Focusing UI Objects
 -->

## UI オブジェクトのフォーカス

<!-- 
Building upon the `expand()`/`collapse()` methods for panels, sections, and controls, these models also support a `focus()` method which not only expands all of the necessary elements, but also scrolls the target container into view and puts the browser focus on the first focusable element in the container. For instance, to expand the “Static Front Page” section and focus on select dropdown for the “Front page”:
 -->

パネル、セクション、コントロール用の `expand()`/`collapse()` メソッドを基盤とし、これらのモデルは `focus()` メソッドもサポートしており、必要な要素をすべて展開するだけでなく、対象コンテナをスクロールして視界に収め、コンテナ内の最初のフォーカス可能な要素に、ブラウザのフォーカスを移します。たとえば、「固定ホームページ」セクションを展開し、「ホームページ」の選択ドロップダウンにフォーカスするには、以下のようにします:

```javascript
wp.customize.control( 'page_on_front' ).focus()
```

<!-- 
The focus functionality is used to implement [autofocus](https://core.trac.wordpress.org/ticket/28650 "#28650: Allow Customizer elements (controls, sections, and panels) to be deep-linked"): deep-linking to panels, sections, and controls inside of the customizer. Consider these URLs:
 -->

フォーカス機能は、[オートフォーカス](https://core.trac.wordpress.org/ticket/28650 "#28650: Allow Customizer elements (controls, sections, and panels) to be deep-linked") を実装するために使用されます: カスタマイザー内のパネル、セクション、コントロールへのディープリンクです。以下のような URL を考えてみましょう:

<!-- 
*   …/wp-admin/customize.php?autofocus\[panel\]=widgets
*   …/wp-admin/customize.php?autofocus\[section\]=colors
*   …/wp-admin/customize.php?autofocus\[control\]=blogname
 -->

*   `…/wp-admin/customize.php?autofocus[panel]=widgets`
*   `…/wp-admin/customize.php?autofocus[section]=colors`
*   `…/wp-admin/customize.php?autofocus[control]=blogname`

<!-- 
This is used in WordPress core to [add a link](https://core.trac.wordpress.org/ticket/28032 "#28032: Headers, Backgrounds, and Widgets in the Customizer are not discoverable from their separate admin screens.") on the widgets admin page to link directly to the widgets panel within the customizer, as well as to connect visible edit shortcuts in the customize preview with the associated controls in the customize pane.
 -->

これは WordPress コアにおいて、ウィジェット管理ページに [リンクを追加](https://core.trac.wordpress.org/ticket/28032 "#28032: Headers, Backgrounds, and Widgets in the Customizer are not discoverable from their separate admin screens.") し、カスタマイザー内のウィジェットパネルへ直接リンクするために使用され、また、カスタマイズプレビュー内に表示されている編集ショートカットを、カスタマイズペイン内の関連コントロールと接続するためにも使用されます。

<!-- 
## Priorities
 -->

## 優先順位

<!-- 
When registering a panel, section, or control in PHP, you can supply a `priority` parameter. This value is stored in a `wp.customize.Value` instance for each respective `Panel`, `Section`, and `Control` instance. For example, you can obtain the priority for the widgets panel via:
 -->

PHP でパネル、セクション、またはコントロールを登録する際、`priority` パラメータを指定できます。この値は、各 `Panel`、`Section`、`Control` インスタンスに対応する `wp.customize.Value` インスタンスに格納されます。たとえば、ウィジェットパネル用の優先度を、以下のように取得できます:

```javascript
priority = wp.customize.panel( 'widgets' ).priority(); // returns 110 by default
```

<!-- 
You can then dynamically change the priority and the Customizer UI will automatically re-arrange to reflect the new priorities:
 -->

その後、優先度を動的に変更すると、「カスタマイザー」UI が自動的に再配置され、新しい優先度を反映します:

```javascript
wp.customize.panel( 'widgets' ).priority( 1 ); // move Widgets to the top
```

<!-- 
## Custom Controls, Panels, and Sections
 -->

## カスタムコントロール、パネル、セクション

<!-- 
When working with custom Customizer objects in JS, it is usually easiest to examine the custom objects in WordPress core to understand the code structure. See [wp-admin/js/customize-controls.js](https://core.trac.wordpress.org/browser/trunk/src/js/_enqueues/wp/customize/controls.js), particularly the wp.customize.Panel|Section|Control models. Note several examples in the core code, particularly in the media controls, which build on each others’ functionality though object hierarchy.
 -->

カスタム「カスタマイザー」オブジェクトを JS で扱う場合、コード構造を理解するには、通常 WordPress コア内のカスタムオブジェクトを参照するのが最も簡単です。[`wp-admin/js/customize-controls.js`](https://core.trac.wordpress.org/browser/trunk/src/js/_enqueues/wp/customize/controls.js) を、特に `wp.customize.Panel`、`wp.customize.Section`、`wp.customize.Control` モデルを参照しましょう。コアコード内の複数の例、特に、オブジェクト階層を通じて互いの機能性を構築している、メディアコントロールの例に留意しましょう。