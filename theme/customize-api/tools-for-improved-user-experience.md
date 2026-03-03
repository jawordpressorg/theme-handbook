<!-- 
# Tools for Improved User Experience
 -->

# ユーザー体験向上のためのツール

<!-- 
## Contextual Controls, Sections, and Panels
 -->

## コンテキストコントロール、セクション、パネル

<!-- 
WordPress 4.0 and 4.1 also added support for making parts of the Customizer UI be visible or hidden depending on the part of the site that the user was previewing within the Customizer preview window. A simple contextual control example would be that your theme only displays the header image and the site tagline on the front page. This is a perfect use case for the Customizer Manager’s get\_ methods, as we can modify the core controls for these settings directly to make them contextual to the front page:
 -->

WordPress v4.0および v4.1では、カスタマイザーのプレビューウィンドウ内でユーザーがプレビューしているサイトのパートに依存して、「カスタマイザー UI」の特定部分を、表示または非表示にする機能も追加されました。簡単なコンテキストコントロール例として、あなたのテーマがホームページにのみヘッダー画像とサイトのキャッチコピーを表示する場合が挙げられます。これはカスタムマネージャーの `get_` メソッドの理想的な使用例であり、これらの設定に対するコアコントロールを直接変更して、ホームページにコンテキスト依存性を付与できます:

```php
// Hide core sections/controls when they aren't used on the current page.
$wp_customize->get_section( 'header_image' )->active_callback = 'is_front_page';
$wp_customize->get_control( 'blogdescription' )->active_callback = 'is_front_page';
```

<!-- 
![](//i0.wp.com/nick.halsey.co/wp-content/uploads/sites/2/2014/08/contextual-customize-controls.gif)
 -->

![](//i0.wp.com/nick.halsey.co/wp-content/uploads/sites/2/2014/08/contextual-customize-controls.gif)

<!-- 
In this contextual control example, the theme only displays the site tagline on the front page, so the corresponding field in the Customizer is hidden when the user navigates to a different page within the preview window.
 -->

コンテキストコントロールにおける本例では、テーマはホームページにのみサイトのキャッチコピーを表示するため、プレビューウィンドウ内でユーザーが別のページに移動すると、「カスタマイザー」内の対応するフィールドは非表示になります。

<!-- 
The `active_callback` parameter for Panels, Sections, and Controls takes a callback function name, either core or custom. This parameter can also be set when registering the object for objects that you add. Here’s an example from the Twenty Fourteen Theme:
 -->

「パネル」、「セクション」、「コントロール」用の `active_callback` パラメータには、コアまたはカスタムのコールバック関数名を指定します。本パラメータは、追加するオブジェクトへの登録時にもセット可能です。以下は Twenty Fourteen テーマからの例です:

```php
$wp_customize->add_section( 'featured_content', array(
  'title'       => __( 'Featured Content', 'twentyfourteen' ),
  'description' => //...
  'priority'        => 130,
  'active_callback' => 'is_front_page',
) );
```

<!-- 
In the previous example, `[is_front_page](https://developer.wordpress.org/reference/functions/is_front_page/)` is used directly. But for more complex logic, such as checking if the current view is a page (or even a specific page, by id), custom functions can be used (see [#30251](https://core.trac.wordpress.org/ticket/30251) for details on why this is needed). If you don’t need to support PHP 5.2, this can be done inline:
 -->

前の例では、[`is_front_page`](https://developer.wordpress.org/reference/functions/is_front_page/) が直接使用されています。しかし、現在のビューがページか否か (あるいは ID による、特定のページであるか否か) を確認するなど、より複雑なロジックの場合には、カスタム関数を使用できます (これが必要な理由の詳細については [#30251](https://core.trac.wordpress.org/ticket/30251) を参照)。PHP v5.2のサポートが不要な場合、これはインラインで実装できます:

```php
'active_callback' => function () { return is_page(); }
```

<!-- 
PHP 5.2 support is as simple as creating a named function and referencing it with the active\_callback parameter:
 -->

PHP v5.2のサポートは、名前付き関数を作成し、`active_callback` パラメータで参照するだけの簡単なものです:

```php
//...
'active_callback' => 'prefix_return_is_page';
//...
function prefix_return_is_page() {
  return is_page();
}
```

<!-- 
Within Custom Controls, Sections, and Panels, there is also an option to override the `active_callback` function directly within the custom Customizer object class:
 -->

「カスタムコントロール」、「セクション」、「パネル」内では、カスタム「カスタマイザー」オブジェクトクラス内で直接 `active_callback` 関数をオーバーライドするオプションも用意されています:

```php
class WP_Customize_Greeting_Control extends WP_Customize_Control {
  // ...
  function active_callback() {
    return is_front_page();
  }
}
```

<!-- 
Finally, there is a filter that can be used to override all other `active_callback` behavior:
 -->

最後に、他のすべての `active_callback` の動作をオーバーライドするために使用できる、フィルターがあります:

```php
// Hide all controls without a description when previewing single posts.
function title_tagline_control_filter( $active, $control ) {
  if ( '' === $control->description ) {
    $active = is_singular();
  }
  return $active;
}
add_filter( 'customize_control_active', 'title_tagline_control_filter', 10, 2 );
```

<!-- 
Note that the `active_callback` API works exactly the same for all of the Customizer object types (Controls, [Sections](https://developer.wordpress.org/reference/classes/wp_customize_section/active_callback/), and [Panels](https://developer.wordpress.org/reference/classes/wp_customize_panel/active_callback/)). As an added bonus, sections will automatically be hidden if all of the controls within them are contextually hidden, and the same works for panels.
 -->

`active_callback` API は、すべての「カスタマイザー」オブジェクトタイプ (「コントロール」、[「セクション」](https://developer.wordpress.org/reference/classes/wp_customize_section/active_callback/)、[「パネル」](https://developer.wordpress.org/reference/classes/wp_customize_panel/active_callback/)) でまったく同じように動作することに留意しましょう。追加のボーナスとして、それら内のすべてのコントロールがコンテキストによって非表示にされた場合、セクションは自動的に非表示になり、パネルについても同様の動作が適用されます。

<!-- 
## Selective Refresh: Fast, Accurate Updates
 -->

## 選択的リフレッシュ: 高速で、正確な更新

<!-- 
Introduced in WordPress 4.5, Selective Refresh updates in the Customizer “preview” only refresh areas whose associate settings are changed. By only updating the elements that have changed, it’s much faster and less disruptive than a full-iframe refresh. Some other benefits, as noted in [Selective Refresh In The Customizer](https://make.wordpress.org/core/2016/02/16/selective-refresh-in-the-customizer), are:
 -->

WordPress v4.5で導入された、「カスタマイザー」プレビューでの「選択的リフレッシュ」は、関連する設定が変更されたエリアのみを更新します。変更された要素のみを更新するため、iframe 全体リフレッシュよりはるかに高速で、干渉も少ないです。[「カスタマイザー」での「選択的リフレッシュ」](https://make.wordpress.org/core/2016/02/16/selective-refresh-in-the-customizer) で説明されているその他の利点は、以下の通りです:

<!-- 
*   Don’t Repeat Yourself (DRY) logic
*   Accurate preview update
*   Association between parts of the preview and associated settings and controls, along with visible edit shortcuts [as of WordPress 4.7](https://make.wordpress.org/core/2016/11/10/visible-edit-shortcuts-in-the-customizer-preview/)
 -->

*   繰り返しを避ける (DRY) ロジック
*   正確なプレビュー更新
*   プレビューのパーツと関連設定およびコントロールの間の連携、および [WordPress v4.7以降](https://make.wordpress.org/core/2016/11/10/visible-edit-shortcuts-in-the-customizer-preview/) の視覚的な編集ショートカット

<!-- 
The logic in pure-JavaScript `postMessage` updates is duplicated. The JavaScript in the Customizer must mirror the PHP that produces the markup, or take shortcuts to approximate it. But Selective Refresh is DRY as there’s no duplication of JavaScript and PHP. An Ajax request retrieves the new markup for the preview.
 -->

純粋な JavaScript の `postMessage` 更新のロジックは重複しています。「カスタマイザー」内の JavaScript は、マークアップを生成する PHP コードと同じものになるか、似たものになるよう近道を取る必要があります。しかし「選択的リフレッシュ」は DRY であり、JavaScript と PHP の重複はありません。Ajax リクエストがプレビュー用の新しいマークアップを取得します。

<!-- 
And because of this Ajax call, the refresh is **accurate**. It uses the filters that can alter the markup. It shows the same result that appears on the front end.
 -->

そしてこの Ajax コールにより、リフレッシュは **正確** です。マークアップを変化させるフィルターを使用します。フロントエンド上に現れるのと同一の結果を表示します。

<!-- 
Additionally, selective refresh partials provide an association between areas of the preview and their corresponding settings. The customizer leverages this relationship to provide visible edit shortcuts that help users find controls associated with a particular part of their site. In the future the partials API could expand to facilitate editing settings directly within the preview and to include a structured JS API for previewing settings with partials.
 -->

さらに、選択的リフレッシュパーシャルは、プレビューのエリアとそれに対応する設定との関連性を提供します。カスタマイザーはこの関係を活用し、ユーザーのサイトの特定パートに関連するコントロールをユーザーが見つけやすくする、視覚的な編集ショートカットを提供します。将来的には、パーシャル API は、プレビュー内で直接設定を編集できるように拡張するとともに、パーシャルを用いた設定のプレビューを可能にする、構造化された JavaScript API を含めることが考えられます。

<!-- 
For these reasons, all settings are strongly recommended to leverage selective refresh transport for improved user experience, with the option of providing additional JavaScript-based transport to further enhance setting previewing.
 -->

これらの理由から、すべての設定では、ユーザー体験向上のために選択的リフレッシュ転送の活用を強く推奨し、設定プレビューをさらに強化するために、追加の JavaScript ベースの転送も提供できます。

<!-- 
### Registering Partials
 -->

### パーシャルの登録

<!-- 
Setting previews need to opt-in to use Selective Refresh by registering the necessary partials. In this example, largely taken from the them [Twenty Sixteen](https://wordpress.org/themes/twentysixteen), Selective Refresh is added for the `blogdescription` setting by adding a partial with the same name.
 -->

設定プレビューで「選択的リフレッシュ」をオプトインするには、必要なパーシャルを登録する必要があります。本例では、[Twenty Sixteen](https://wordpress.org/themes/twentysixteen) から主に引用し、`blogdescription` 設定に対して、同名のパーシャルを追加することで、「選択的リフレッシュ」が追加されます。

```php
function foo_theme_customize_register( WP_Customize_Manager $wp_customize ) {
    $wp_customize->selective_refresh->add_partial( 'blogdescription', array(
        'selector' => '.site-description',
        'container_inclusive' => false,
        'render_callback' => function() {
            bloginfo( 'description' );
        },
    ) );
}
add_action( 'customize_register', 'foo_theme_customize_register' );
```

<!-- 
If the `settings` argument is not supplied, it defaults to be the same as the partial ID, in the same way as the settings for controls default to the control ID. Here are some of the key arguments for partials:
 -->

`settings` 引数が供給されない場合、デフォルトではパーシャル ID と同じになり、これは、コントロール用の設定が、デフォルトでコントロール ID と同じになるのと同じしくみです。以下は、パーシャル用のキー引数です:

<!-- 
| **Variable** | **Type** | **Description** |
| --- | --- | --- |
| `settings` | array | Setting IDs associated with the partial. |
| `selector` | string | Targets the element(s) in the page markup to be refreshed. |
| `container_inclusive` | boolean | If true, a refresh replaces the entire container. Otherwise, it only replaces the container’s children. Defaults to false. |
| `render_callback` | function | Produces the markup to be rendered on refresh. |
| `fallback_refresh` | bool | Whether or not a full page refresh should occur if the partial is not found in the document. |
 -->

| **変数** | **型** | **説明** |
| --- | --- | --- |
| `settings` | array | パーシャルに関連付けられた設定 ID です。 |
| `selector` | string | ページマークアップ内で、リフレッシュ対象となる要素を指定します。 |
| `container_inclusive` | boolean | true の場合、リフレッシュ時にコンテナ全体が置換されます。それ以外の場合、コンテナの子要素のみが置換されます。デフォルトは、false です。 |
| `render_callback` | function | リフレッシュ時にレンダリングされるマークアップを生成します。 |
| `fallback_refresh` | bool | ドキュメント内でパーシャルが見つからない場合に、ページ全体のリフレッシュを行うか否かです。 |

<!-- 
### Selective Refresh JavaScript Events
 -->

### 選択的リフレッシュ JavaScript イベント

<!-- 
These fire on `wp.customize.selectiveRefresh`:
 -->

これらは `wp.customize.selectiveRefresh` で発火します:

<!-- 
*   `partial-content-rendered`  
    When the placement is rendered. As mentioned, JavaScript-driven widgets can re-build on this event.
*   `render-partials-response`  
    When data is returned, after a request for partial rendering. The server filters this data with ‘customize\_render\_partials\_response’.
*   `partial-content-moved`  
    When a widget has moved in its sidebar. As shown above, JavaScript-driven widgets can refresh on this event.
*   `widget-updated`  
    When the `WidgetPartial` is refreshed with its `renderContent` method.
*   `sidebar-updated`  
    When a sidebar has a widget that’s refreshed or updated. Or when a sidebar’s widgets are sorted, using `reflowWidgets()`.
 -->

*   `partial-content-rendered`  
    プレースメントが、レンダリングされた場合。前述の通り、JavaScript 駆動ウィジェットは、本イベントで再構築できます。
*   `render-partials-response`  
    パーシャルレンダリングのリクエスト後に、データが返された場合。サーバーは、このデータを `customize_render_partials_response` でフィルタリングします。
*   `partial-content-moved`  
    ウィジェットが、そのサイドバー内で移動した場合。上記のように、JavaScript 駆動ウィジェットは、本イベントで更新できます。
*   `widget-updated`  
    `WidgetPartial` が、その `renderContent` メソッドでリフレッシュされた場合。
*   `sidebar-updated`  
    サイドバーが、リフレッシュまたは更新されたウィジェットを持っている場合。あるいは、`reflowWidgets()` を使用して、サイドバーのウィジェットがソートされた場合。

<!-- 
### Widgets: Opting-In To Selective Refresh
 -->

### ウィジェット: 選択的リフレッシュのオプトイン

<!-- 
Both themes and widgets **need to opt-in** to use Selective Refresh. All core widgets and themes have already enabled this.
 -->

テーマとウィジェットの双方が、「選択的リフレッシュ」を使用するには、**オプトインが必要** です。すべてのコアウィジェットとテーマは、すでにこれを有効化しています。

<!-- 
#### Theme Support In Sidebars
 -->

#### サイドバーでのテーマサポート

<!-- 
In order to allow partial refreshes of widgets in a theme’s sidebars:
 -->

テーマのサイドバー内にある、ウィジェットのパーシャルリフレッシュを可能にするために:

```php
add_theme_support( 'customize-selective-refresh-widgets' );
```

<!-- 
**Important:** Selective refresh for widgets requires that the theme include a `before_widget`/`after_widget` wrapper element around each widget that contains the widget’s ID. Such wrappers are the default when you `register_sidebar()`. For example:
 -->

**重要:** ウィジェット用「選択的リフレッシュ」には、各ウィジェットにウィジェット ID を含む `before_widget`/`after_widget` ラッパー要素が含まれるテーマが必要です。`register_sidebar()` を呼び出す際、このようなラッパーがデフォルトとなります。たとえば:

```php
function example_widgets_init() {
	register_sidebar(
		array(
			'name'          => esc_html__( 'Sidebar', 'example' ),
			'id'            => 'sidebar-1',
			'description'   => esc_html__( 'Add widgets here.', 'example' ),
			'before_widget' => '<section id="%1$s" class="widget %2$s">', // <= Key for selective refresh.
			'after_widget'  => '</section>',
			'before_title'  => '<h2 class="widget-title">',
			'after_title'   => '</h2>',
		)
	);
}
add_action( 'widgets_init', 'example_widgets_init' );
```

<!-- 
#### Widget Support
 -->

#### ウィジェットのサポート

<!-- 
Even if a theme supports Selective Refresh, widgets also have to opt-in. All core widgets have already enabled it. Here’s an example widget adding support for Selective Refresh:
 -->

テーマが「選択的リフレッシュ」をサポートしていても、ウィジェットもオプトインする必要があります。すべてのコアウィジェットは、すでに有効化されています。以下は、「選択的リフレッシュ」用サポートを追加するウィジェットの例です:

```php
class Foo_Widget extends WP_Widget {

    public function __construct() {
        parent::__construct(
            ‘foo’,
            __( 'Example', 'bar-plugin' ),
            array(
                'description' => __( ‘An example widget’, ‘bar-plugin’ ),
                'customize_selective_refresh' => true,
            )
        );

        if ( is_active_widget( false, false, $this->id_base ) || is_customize_preview() ) {
            add_action( 'wp_enqueue_scripts', array( $this, 'enqueue_scripts' ) );
        }
    }
    ...
```

<!-- 
Line 9 above enables Selective Refresh:
 -->

上記の9行目は、「選択的リフレッシュ」を有効にします:

```php
'customize_selective_refresh' => true,
```

<!-- 
Line 13 above ensures the widget’s stylesheet always appears in Customizer sessions. Adding the widget won’t cause a full-page refresh to retrieve the styling:
 -->

上記の13行目は、ウィジェットのスタイルシートが、「カスタマイザー」セッションで常に表示されることを保証します。ウィジェット追加時に、スタイリングを取得するためのページ全体リフレッシュは、発生しません:

```php
if ( is_active_widget( false, false, $this->id_base ) || is_customize_preview() ) {
    add_action( 'wp_enqueue_scripts', array( $this, 'enqueue_scripts' ) );
}
```

<!-- 
See [Implementing Selective Refresh Support for Widgets](https://make.wordpress.org/core/2016/03/22/implementing-selective-refresh-support-for-widgets/).
 -->

[ウィジェット用の「選択的リフレッシュ」サポートの実装](https://make.wordpress.org/core/2016/03/22/implementing-selective-refresh-support-for-widgets/) をご覧ください。

<!-- 
#### JavaScript-Driven Widget Support
 -->

#### JavaScript 駆動ウィジェットのサポート

<!-- 
Widgets that rely on JavaScript for their markup will need additional steps, as shown in [Implementing Selective Refresh Support for Widgets](https://make.wordpress.org/core/2016/03/22/implementing-selective-refresh-support-for-widgets/):
 -->

[ウィジェット用の「選択的リフレッシュ」サポートの実装](https://make.wordpress.org/core/2016/03/22/implementing-selective-refresh-support-for-widgets/) に示されているように、JavaScript に依存するウィジェットのマークアップには、追加の手順が必要です:

<!-- 
1.  Enqueue any JavaScript files based on `is_customize_preview()`, as shown above for stylesheets.
2.  Add a handler for the `partial-content-rendered` event, and refresh the widget as needed:
 -->

1.  前述のスタイルシートで示したように、`is_customize_preview()` にもとづいて JavaScript ファイルをキューに追加します。
2.  `partial-content-rendered` イベント用のハンドラを追加し、必要に応じてウィジェットをリフレッシュします:

```js
wp.customize.selectiveRefresh.bind( 'partial-content-rendered', function( placement ) {
    // logic to refresh
} );
```

<!-- 
1.  If the widget includes an iframe, add a handler to refresh the partial:
 -->

1.  ウィジェットが iframe を含む場合、パーシャルをリフレッシュするハンドラを追加します:

```js
wp.customize.selectiveRefresh.bind( 'partial-content-moved', function( placement ) {
    // logic to refresh, perhaps conditionally
}
```

<!-- 
## Using PostMessage For Improved Setting Previewing
 -->

## 設定プレビューの改善に向けた、postMessage の使用

<!-- 
The Customizer automatically handles previewing all settings out-of-the-box. This is done by silently reloading the entire preview window, with settings being filtered by PHP in that Ajax call. While this works just fine, it can be very slow since the entire front-end must be reloaded for every single setting change. Selective Refresh improves this experience by refreshing only the elements that have changed, but due to the Ajax call, there is still a delay in seeing the changes in the preview.
 -->

「カスタマイザー」は、すべての設定のプレビューを初期状態で自動的に処理します。これは、Ajax コール内において PHP が設定をフィルタリングしながら、プレビューウィンドウ全体を暗黙的にリロードすることで実現されています。この方法は問題なく動作しますが、設定変更のたびにフロントエンド全体をリロードする必要があるため、非常に遅くなる場合があります。「選択的リフレッシュ」は変更された要素のみを更新することで、この体験を改善しますが、Ajax コールのため、プレビューでの変更確認には、依然として遅延が生じます。

<!-- 
To further improve the user experience, the Customizer offers an API for managing setting changes directly in JavaScript, allowing for truly-live previewing. The below images show a comparison of a Custom CSS option that leverages this technology, called `postMessage`, versus the standard refresh option:
 -->

ユーザー体験をさらに向上させるため、「カスタマイザー」は、JavaScript 内で直接、設定変更を管理するための API を提供し、真のライブプレビューを実現します。以下の画像は、`postMessage` と呼ばれる本技術を活かした、カスタム CSS オプションと、標準のリフレッシュオプションとの比較を示しています:

<!-- 
![](//i0.wp.com/nick.halsey.co/wp-content/uploads/sites/2/2014/08/customize-setting-postmessage.gif)
 -->

![](//i0.wp.com/nick.halsey.co/wp-content/uploads/sites/2/2014/08/customize-setting-postmessage.gif)

<!-- 
Custom CSS setting in the Customizer with the postMessage setting transport.
 -->

`postMessage` 設定転送付き「カスタマイザー」における、カスタム CSS 設定です。

<!-- 
![](//i0.wp.com/nick.halsey.co/wp-content/uploads/sites/2/2014/08/customize-setting-refresh-1.gif)
 -->

![](//i0.wp.com/nick.halsey.co/wp-content/uploads/sites/2/2014/08/customize-setting-refresh-1.gif)

<!-- 
Custom CSS setting in the Customizer with the default refresh setting transport.
 -->

デフォルトリフレッシュ設定転送付き「カスタマイザー」における、カスタム CSS 設定です。

<!-- 
To use postMessage, first set the transport parameter to postMessage when adding your setting. Many themes also modify core settings such as the title and tagline to leverage postMessage by modifying the transport property of those settings:
 -->

`postMessage` を使用するには、あなたの設定を追加する際に、まず転送パラメータを `postMessage` にセットしましょう。多くのテーマでは、これらの設定の転送プロパティを変更することで、`postMessage` を活用するためにタイトルやキャッチコピーなどのコア設定も修正します:

```php
$wp_customize->get_setting( 'blogname' )->transport        = 'postMessage';
$wp_customize->get_setting( 'blogdescription' )->transport = 'postMessage';
```

<!-- 
Once the setting’s transport is set to postMessage, the setting will no longer trigger a refresh of the preview when its value changes. To implement the JavaScript to update the setting within the preview of the front-end, first create and enqueue a JavaScript file:
 -->

設定の転送が postMessage にセットされると、その値が変更されてもプレビューのリフレッシュはトリガーされなくなります。フロントエンドのプレビュー内で設定を更新する JavaScript を実装するには、まず JavaScript ファイルを作成してキューに追加しましょう:

```php
function my_preview_js() {
  wp_enqueue_script( 'custom_css_preview', 'path/to/file.js', array( 'customize-preview', 'jquery' ) );
}
add_action( 'customize_preview_init', 'my_preview_js' );
```

<!-- 
Your JavaScript file should look something like this:
 -->

あなたの JavaScript ファイルは、以下のような内容になるでしょう:

```js
( function( $ ) {
  wp.customize( 'setting_id', function( value ) {
    value.bind( function( to ) {
      $( '#custom-theme-css' ).html( to );
    } );
  } );
  wp.customize( 'custom_plugin_css', function( value ) {
    value.bind( function( to ) {
      $( '#custom-plugin-css' ).html( to );
    } );
  } );
} )( jQuery );
```

<!-- 
Note that you don’t necessarily need to be great with JavaScript to use postMessage – most of the code is boilerplate. The types of settings that benefit most from postMessage transport require simple JS changes such as using jQuery’s .html() or .text() methods, or swapping out a class on the `<body>` or another element to trigger a different set of CSS rules. Doing this, or simplifying the instant preview logic with fully-accurate changes updating with selective refresh, the user experience can be fast without duplicating all of the PHP logic in JS.
 -->

postMessage を使用するのに、必ずしも JavaScript に精通している必要はないことに留意しましょう – コードの大半は、定型的なものです。postMessage 転送で最も効果を発揮する設定の種類は、jQuery の `.html()` や `.text()` メソッドを使用したり、`<body>` 要素や他の要素のクラスを切り替えて、別の CSS ルール群を適用したりといった、簡単な JavaScript 変更を必要とします。この方法、あるいは選択的リフレッシュで完全かつ正確な変更を更新する即時プレビューロジックの簡素化により、PHP ロジックをすべて JavaScript に複製することなく、高速なユーザー体験を実現できます。

<!-- 
## Setting Validation
 -->

## 設定バリデーション

<!-- 
WordPress 4.6 includes new APIs related to validation of Customizer setting values. The Customizer has had sanitization of setting values since it was introduced. Sanitization involves coercing a value into something safe to persist to the database: common examples are converting a value into an integer or stripping tags from some text input. As such, sanitization is a *lossy* operation. With the addition of setting validation:
 -->

WordPress v4.6では、「カスタマイザー」設定値のバリデーションに関連した、新しい API が追加されました。「カスタマイザー」は導入当初から、設定値のサニタイズ処理を行ってきました。サニタイズ処理とは、値をデータベースに安全に永続化できる形式に変換することです: 一般的には、値を整数に変換したり、テキスト入力からタグを削除したりする処理が該当します。したがって、サニタイズ処理は、*ロスを伴う* 操作です。設定のバリデーション機能の追加により:

<!-- 
1.  All modified settings are validated up-front before any of them are saved.
2.  If any setting is invalid, the Customizer save request is rejected: a save thus becomes *transactional* with all the settings left dirty to try saving again. (The Customizer [transactions proposal](https://make.wordpress.org/core/2015/01/26/customizer-transactions-proposal/) is closely related to setting validation here.)
3.  Validation error messages are displayed to the user, prompting them to fix their mistake and try again.
 -->

1.  変更された設定はすべて、保存される前に、事前に検証されます。
2.  設定に無効なものがある場合、「カスタマイザー」の保存リクエストは拒否されます: これにより保存は、*トランザクション処理* となり、すべての設定は、未確定状態のまま再保存を試みます (「カスタマイザー」の [トランザクション提案](https://make.wordpress.org/core/2015/01/26/customizer-transactions-proposal/) は、ここでいう設定バリデーションと密接に関連しています)。
3.  バリデーションのエラーメッセージがユーザーに表示され、誤りを修正して再試行するよう、促します。

<!-- 
Sanitization and validation are also both part of the REST API infrastructure via `WP_REST_Request::sanitize_params()` and `WP_REST_Request::validate_params()`, respectively. A setting’s value goes through validation before it goes through sanitization.
 -->

サニタイゼーションとバリデーションは、それぞれ `WP_REST_Request::sanitize_params()` および `WP_REST_Request::validate_params()` を介して、REST API インフラストラクチャの一部でもあります。設定値は、サニタイゼーション処理が行われる前に、バリデーション処理を経ます。

<!-- 
For more information on the validation behavior, and additional code examples, see [the feature announcement post](https://make.wordpress.org/core/2016/07/05/customizer-apis-in-4-6-for-setting-validation-and-notifications/).
 -->

バリデーション動作に関する詳細情報と追加のコード例については、[機能発表の投稿](https://make.wordpress.org/core/2016/07/05/customizer-apis-in-4-6-for-setting-validation-and-notifications/) をご覧ください。

<!-- 
### Validating Settings in PHP
 -->

### PHP における設定の検証

<!-- 
Just as you can supply a `sanitize_callback` when registering a setting, you can also supply a `validate_callback` arg:
 -->

設定を登録する際に、`sanitize_callback` を提供できるのと同様に、`validate_callback` 引数も提供できます:

```php
$wp_customize->add_setting( 'established_year', array(
    'sanitize_callback' => 'absint',
    'validate_callback' => 'validate_established_year'
) );
function validate_established_year( $validity, $value ) {
    $value = intval( $value );
    if ( empty( $value ) || ! is_numeric( $value ) ) {
        $validity->add( 'required', __( 'You must supply a valid year.' ) );
    } elseif ( $value &lt; 1900 ) {
        $validity->add( 'year_too_small', __( 'Year is too old.' ) );
    } elseif ( $value > gmdate( 'Y' ) ) {
        $validity->add( 'year_too_big', __( 'Year is too new.' ) );
    }
    return $validity;
}
```

<!-- 
Just as supplying a `sanitize_callback` arg adds a filter for `customize_sanitize_{$setting_id}`, so too supplying a `validate_callback` arg will add a filter for `customize_validate_{$setting_id}`. Assuming that the `WP_Customize_Setting` instances apply filters on these in their `validate` methods, you can add this filter if you need to add validation for settings that have been previously added.
 -->

`sanitize_callback` 引数を提供すると、`customize_sanitize_{$setting_id}` 用のフィルターが追加されるのと同様に、`validate_callback` 引数を提供すると、`customize_validate_{$setting_id}` 用のフィルターが追加されます。`WP_Customize_Setting` インスタンスが、その `validate` メソッド内でこれらの設定にフィルターを適用すると仮定した場合、以前に追加された設定に対してバリデーションを適用する必要がある場合、このフィルターを追加できます。

<!-- 
The `validate_callback` and any `customize_validate_{$setting_id}` filter callbacks take a `WP_Error` instance is its first argument (which initially is empty of any errors added), followed by the `$value` being sanitized, and lastly the `WP_Customize_Setting` instance that is being validated.
 -->

`validate_callback` および `customize_validate_{$setting_id}` フィルターコールバックは、最初の引数として `WP_Error` インスタンス (初期状態ではエラーが追加されていない状態)、続いてサニタイズ対象の `$value`、最後に検証対象の `WP_Customize_Setting` インスタンスを受け取ります。

<!-- 
Custom setting classes can also override the `validate` method of the setting class directly.
 -->

カスタム設定クラスは、設定クラスの `validate` メソッドも直接オーバーライドできます。

<!-- 
### Client-side Validation
 -->

### クライアントサイドのバリデーション

<!-- 
If you have a setting that is previewed purely via JavaScript (and the `postMessage` transport *without* selective refresh), you should also add client-side validation. Otherwise, any validation errors will persist until a full refresh happens or a save is attempted. Client-side validation must not take the place of server-side validation, since malicious users could bypass the client-side validation to save an invalid value if corresponding server-side validation is not in place.
 -->

JavaScript のみでプレビューされる (および、選択的リフレッシュを伴わない `postMessage` 転送) 設定がある場合、クライアントサイドバリデーションも追加する必要があります。さもなければ、完全なリフレッシュが行われるか、保存が試みられるまで、バリデーションエラーは持続します。対応するサーバーサイドバリデーションが実施されていない場合、悪意のあるユーザーがクライアントサイドバリデーションを迂回して無効な値を保存する可能性があるため、クライアントサイドバリデーションは、サーバーサイドバリデーションの代わりになってはいけません。

<!-- 
There is a `validate` method available on the `wp.customize.Setting` JS class (actually, the `wp.customize.Value` base class). Its name is a bit misleading, as it actually behaves very similarly to the `WP_Customize_Setting::sanitize()` PHP method, but it can be used to both sanitize and validate a value in JS. Note that this JS runs in the context of the Customizer *pane* not the preview, so any such JS should have `customize-controls` as a dependency (not `customize-preview`) and enqueued during the `customize_controls_enqueue_scripts` action. Some example JS validation:
 -->

`wp.customize.Setting` JavaScript クラス (実際には、`wp.customize.Value` 基底クラス) には、`validate` メソッドが用意されています。その名称は少し誤解を招きやすいのですが、実際には、PHP の `WP_Customize_Setting::sanitize()` メソッドと非常に似た動作をしますが、JavaScript 内で値のサニタイズと検証の両方を行うために使用できます。この JavaScript はプレビューではなくカスタマイザーの *ペイン* コンテキストで実行されることに留意して、そのような JavaScript は、(`customize-preview` ではなく) `customize-controls` を依存関係として持つべきであり、`customize_controls_enqueue_scripts` アクション中にキューに入れる必要があります。JavaScript バリデーションの例:

```js
wp.customize( 'established_year', function ( setting ) {
	setting.validate = function ( value ) {
		var code, notification;
		var year = parseInt( value, 10 );

		code = 'required';
		if ( isNaN( year ) ) {
			notification = new wp.customize.Notification( code, {message: myPlugin.l10n.yearRequired} );
			setting.notifications.add( code, notification );
		} else {
			setting.notifications.remove( code );
		}

		code = 'year_too_small';
		if ( year &lt; 1900 ) {
			notification = new wp.customize.Notification( code, {message: myPlugin.l10n.yearTooSmall} );
			setting.notifications.add( code, notification );
		} else {
			setting.notifications.remove( code );
		}

		code = 'year_too_big';
		if ( year > new Date().getFullYear() ) {
			notification = new wp.customize.Notification( code, {message: myPlugin.l10n.yearTooBig} );
			setting.notifications.add( code, notification );
		} else {
			setting.notifications.remove( code );
		}

		return value;
	};
} );
```

<!-- 
## Notifications
 -->

## 通知

<!-- 
![Error notification](https://i0.wp.com/make.wordpress.org/core/files/2016/07/error-notification-300x112.png?resize=300%2C112&ssl=1)
 -->

![エラー通知](https://i0.wp.com/make.wordpress.org/core/files/2016/07/error-notification-300x112.png?resize=300%2C112&ssl=1)

<!-- 
Notifications provide user feedback, typically based on the value of a control’s setting. An error notification is added to a setting’s `notifications` collection when a setting’s validation routine returns a `WP_Error` instance. Each error added to a PHP `WP_Error` instance is represented as a `wp.customize.Notification` in JavaScript:
 -->

通知は、通常、コントロールの設定値にもとづいて、ユーザーにフィードバックを提供します。設定のバリデーションルーチンが `WP_Error` インスタンスを返した場合、エラー通知が設定の `notifications` コレクションに追加されます。PHP の `WP_Error` インスタンスに追加された各エラーは、JavaScript では `wp.customize.Notification` として表現されます:

<!-- 
*   A `WP_Error`‘s `code` is available as `notification.code` in JS.
*   A `WP_Error`‘s `message` is available as `notification.message` in JS. Note that if there are multiple messages added to a given error code in PHP they will be concatenated into a single message in JS.
*   A `WP_Error`‘s `data` is available as `notification.data` in JS. This is useful to pass additional error context from the server to the client.
 -->

*   `WP_Error` の `code` は、JavaScript では `notification.code` として利用可能です。
*   `WP_Error` の `message` は、JavaScript では `notification.message` として利用可能です。PHP で特定のエラーコードに複数のメッセージが追加されている場合、JavaScript では、それらが単一のメッセージに連結されることに留意しましょう。
*   `WP_Error` の `data` は、JavaScript では `notification.data` として利用可能です。これは、サーバーからクライアントに、追加のエラーコンテキストを渡すのに有用です。

<!-- 
Any time that a `WP_Error` is returned from a validation routine on the server it will result in a `wp.customize.Notification` being created with a `type` property of “error”.
 -->

サーバーサイドのバリデーションルーチンから `WP_Error` が返されるたびに、`type` プロパティが「error」である `wp.customize.Notification` が作成されます。

<!-- 
While setting non-error notifications from PHP is not currently supported (see #37281), you can also add non-error notifications with JS as follows:
 -->

PHP から非エラー通知を設定することは、現在サポートされていません ([`#37281`](https://core.trac.wordpress.org/ticket/37281) 参照) が、以下の方法で JavaScript を使用して、非エラー通知も追加できます:

```js
wp.customize( 'blogname', function( setting ) {
    setting.bind( function( value ) {
        var code = 'long_title';
        if ( value.length > 20 ) {
            setting.notifications.add( code, new wp.customize.Notification(
                code,
                {
                    type: 'warning',
                    message: 'This theme prefers title with max 20 chars.'
                }
            ) );
        } else {
            setting.notifications.remove( code );
        }
    } );
} );
```

<!-- 
You can also supply “info” as a notification’s `type`. The default `type` is “error”. Custom types may also be supplied, and the notifications can be styled with CSS selector matching `notice.notice-foo` where “foo” is the type supplied. A control may also override the default behavior for how notifications are rendered by overriding the `wp.customize.Control.renderNotifications` method.
 -->

通知の `type` として「info」も提供できます。デフォルトの `type` は「error」です。カスタムタイプも提供可能であり、`notice.notice-foo` (ここで「foo」は提供されたタイプ) に合致する CSS セレクタで、通知をスタイリングできます。コントロールは、`wp.customize.Control.renderNotifications` メソッドをオーバーライドすることで、通知のレンダリングに関するデフォルト動作も、オーバーライドできます。