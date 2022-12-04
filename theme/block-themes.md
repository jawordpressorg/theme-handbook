<!--
# Block themes
-->
# ブロックテーマ

<!--
A block theme is a type of WordPress theme built using blocks. You can edit all parts of a block theme in the [Site Editor](https://wordpress.org/support/article/site-editor/).
-->
ブロックテーマは WordPress のテーマのひとつのタイプで、ブロックを使って構築します。[サイトエディター](https://wordpress.org/support/article/site-editor/)からブロックテーマのすべてのパーツを編集できます。

<!--
WordPress supports block themes from version 5.9. Together with the [Styles interface](https://wordpress.org/support/article/styles-overview/), block themes are part of full site editing. They are sometimes called full site editing themes. [Learn about the background to full site editing](https://developer.wordpress.org/block-editor/getting-started/full-site-editing/).
-->
WordPress はバージョン 5.9 からブロックテーマをサポートしています。[スタイルインターフェース](https://wordpress.org/support/article/styles-overview/) と一緒で、ブロックテーマはフルサイト編集の一部です。これらは時々フルサイト編集テーマとも呼ばれます。[フルサイト編集の背景についてはこちらで学べます](https://developer.wordpress.org/block-editor/getting-started/full-site-editing/)。

<!--
You may also be interested in reading the [support article about block themes](https://wordpress.org/support/article/block-themes/).
-->
[ブロックテーマについてのサポート記事](https://wordpress.org/support/article/block-themes/)を読むのもおもしろいかもしれません。

<!--
In this part of the handbook, you will learn about:
-->
ハンドブックのこのパートでは、以下のについて学ぶことができます

<!--
*   The differences between classic themes and block themes
*   Block theme setup
*   Templates and template parts
*   The theme.json configuration file
*   Converting classic themes to block themes
-->
*   クラシックテーマとブロックテーマの違い
*   ブロックテーマの設定
*   テンプレートとテンプレートパーツ
*   theme.json 設定ファイル
*   クラシックテーマからブロックテーマへの変換

<!--
Prerequisits for this chapter: [Theme Basics](https://developer.wordpress.org/themes/basics/)
-->
この章の前提条件: [テーマの基礎](https://developer.wordpress.org/themes/basics/)

<!--
## The benefits of block themes
-->
## ブロックテーマの利点

<!--
Why should you create block themes? While WordPress continues to support classic themes, block themes are built to improve scalability and performance.
-->
どうしてブロックテーマを作成するべきなのでしょうか ? WordPress はクラシックテーマのサポートを続けていますが、ブロックテーマは拡張性とパフォーマンスを向上させるために作られています。

<!--
*   [Block themes enhances loading performance](https://make.wordpress.org/core/2021/07/01/block-styles-loading-enhancements-in-wordpress-5-8/) by loading styles only for rendered blocks on a page
*   Block themes are not required to manually enqueue stylesheets for both front-end and editors
*   Theme.json handles all aspects of [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/)
*   Accessibility features such as Skip to content, keyboard navigation, and landmarks are generated automatically without adding additional code
*   With a block theme, the user can edit all parts of their website without code
*   By using the Styles interface, users can customize colors and typography for the website and for the blocks
-->

*  ブロックテーマは、ページに描写されるブロックについてのみのスタイルを読み込むことで[読み込みのパフォーマンスを向上させています](https://make.wordpress.org/core/2021/07/01/block-styles-loading-enhancements-in-wordpress-5-8/)
*  ブロックテーマは、フロントエンドとエディターそれぞれのタイルシートを手動でエンキューする必要がありません
*  Theme.json は、[add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) が担う全ての機能を処理できます
*  コンテンツのスキップや、キーボードのナビゲーション、ランドマークといったアクセシビリティ機能は特別なコードを追加することなく自動で生成されます
*  ブロックテーマでは、ユーザーはコードなしで Web サイトのすべての部分を編集することができます
*  「スタイル」インターフェースにより、Web サイトやブロックの色やタイポグラフィをカスタマイズすることができます

<!--
## Differences and similarities between classic themes and block themes
-->
## クラシックテーマとブロックテーマとの相違点・共通点

<!--
Many concepts and features are the same for both classic and block themes, and in some cases, the handbook will refer to a chapter about classic themes.
-->
多くのコンセプトや機能はクラシックテーマでもブロックテーマでも同じであり、このハンドブックではクラシックテーマに関する章を参照する場合もあります。

<!--
For theme developers that are accustomed to creating classic themes, there is a comparison table:
-->
クラシックテーマを作り慣れているテーマ開発者のために、比較表が用意されています:

<!--
<table><tbody><tr><td><strong>Classic themes</strong>:</td><td><strong>Block themes</strong>:</td></tr><tr><td>Uses PHP files to display parts and content.</td><td>Uses HTML files to display blocks.<br>Uses PHP files as a fallback if WordPress can not find the HTML file.<br><em>single.html is the equivalent of using single.php.</em></td></tr><tr><td>Uses the <a href="https://developer.wordpress.org/themes/basics/template-hierarchy/" data-type="URL" data-id="https://developer.wordpress.org/themes/basics/template-hierarchy/">template hierarchy</a></td><td>Uses the template hierarchy</td></tr><tr><td>Uses PHP functions such as <a href="https://developer.wordpress.org/themes/basics/template-tags/" data-type="URL" data-id="https://developer.wordpress.org/themes/basics/template-tags/">template tags</a> to display content</td><td>Uses blocks for everything.<br><em>The post content block is the equivalent of using <code>the_content()</code>.</em></td></tr><tr><td>Use&nbsp;<a rel="noreferrer noopener" href="https://developer.wordpress.org/apis/handbook/internationalization/" target="_blank">PHP functions</a>&nbsp;to make text translatable</td><td>Text in HTML files is not translatable.<br><a rel="noreferrer noopener" href="https://developer.wordpress.org/block-editor/reference-guides/block-api/block-patterns/" target="_blank">Block patterns</a>&nbsp;can use PHP functions to make text translatable.</td></tr><tr><td>Uses PHP functions for <a href="https://developer.wordpress.org/themes/basics/conditional-tags/" data-type="URL" data-id="https://developer.wordpress.org/themes/basics/conditional-tags/">if/else conditionals</a></td><td>Uses block settings to achieve different results</td></tr><tr><td>Uses <a href="https://developer.wordpress.org/themes/basics/the-loop/" data-type="URL" data-id="https://developer.wordpress.org/themes/basics/the-loop/">the loop</a> to display different posts and post types</td><td>Uses the <a href="https://wordpress.org/support/article/query-loop-block/" data-type="URL" data-id="https://wordpress.org/support/article/query-loop-block/">query block</a> and the post template block</td></tr><tr><td>Can use <a href="https://developer.wordpress.org/themes/functionality/sidebars/" data-type="URL" data-id="https://developer.wordpress.org/themes/functionality/sidebars/">widget areas (sidebars)</a> and <a href="https://developer.wordpress.org/themes/functionality/widgets/" data-type="URL" data-id="https://developer.wordpress.org/themes/functionality/widgets/">widgets</a></td><td>Uses blocks instead of widgets. <em>Widgets included in WordPress have been converted to blocks.</em></td></tr><tr><td>Can use the <a href="https://developer.wordpress.org/themes/customize-api/" data-type="URL" data-id="https://developer.wordpress.org/themes/customize-api/">Customizer</a></td><td>Uses the Site Editor. Can optionally enable the Customizer menu</td></tr><tr><td>Must register a <a href="https://developer.wordpress.org/themes/functionality/navigation-menus/" data-type="URL" data-id="https://developer.wordpress.org/themes/functionality/navigation-menus/">navigation menu</a> to include a menu</td><td>Uses the <a href="https://wordpress.org/support/article/navigation-block/" data-type="URL" data-id="https://wordpress.org/support/article/navigation-block/">navigation block</a></td></tr><tr><td>Can register a <a href="https://developer.wordpress.org/themes/functionality/custom-headers/" data-type="URL" data-id="https://developer.wordpress.org/themes/functionality/custom-headers/">custom header</a></td><td>Uses blocks to fully customize site headers including images</td></tr><tr><td>Can register a <a href="https://developer.wordpress.org/themes/functionality/custom-logo/" data-type="URL" data-id="https://developer.wordpress.org/themes/functionality/custom-logo/">custom logo</a></td><td>Uses the site logo block</td></tr><tr><td>Can enqueue <a href="https://developer.wordpress.org/themes/basics/including-css-javascript/" data-type="URL" data-id="https://developer.wordpress.org/themes/basics/including-css-javascript/">custom CSS and scripts</a></td><td>Can enqueue custom CSS and scripts but relies more on blocks and the theme.json configuration file</td></tr><tr><td>Can use <a href="https://developer.wordpress.org/themes/advanced-topics/theme-json/" data-type="URL" data-id="https://developer.wordpress.org/themes/advanced-topics/theme-json/">theme.json</a>, but theme authors need to enqueue the styles for the front.</td><td>Can use theme.json, and the styles are enqueued automatically to the editor and front</td></tr><tr><td>Can place template files in the root directory</td><td>Places template files in the <strong>templates</strong> folder</td></tr><tr><td>Can place template parts in any directory</td><td>Places template parts in the <strong>parts</strong> folder</td></tr><tr><td>Can not create and edit site templates like 404 and archive pages in the Site Editor</td><td>Can create and edit site templates like 404 and archive pages in the Site Editor</td></tr><tr><td>Can create and edit block templates in the Template Editor<em> with theme support</em></td><td>Can create and edit block templates in the Template Editor</td></tr></tbody></table>
-->
| クラシックテーマ: | ブロックテーマ: |
|---|---|
| コンテンツの表示に PHP ファイルを使用。 | ブロックの表示に HTML を使用。HTML ファイルを WordPress が見つけられない場合に PHP をフォールバックとして使用。 *single.html は single.php に相当* |
| [テンプレート階層](https://ja.wordpress.org/team/handbook/theme-development/basics/template-hierarchy/)を使用 | テンプレート階層を使用 |
| コンテンツの表示に[テンプレートタグ](https://developer.wordpress.org/themes/basics/template-tags/)のような PHP 関数を使用 | 全てにブロックを使用。*投稿コンテンツブロックは `the_content()` に相当* |
| テキストを翻訳可能にするために [PHP 関数](https://developer.wordpress.org/apis/handbook/internationalization/)を使用 | HTML ファイルのテキストは翻訳不可能。[ブロックパターン](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-patterns/)は PHP 関数を使用して翻訳可能にできる |
| [if/else の条件分岐](https://developer.wordpress.org/themes/basics/conditional-tags/)に PHP の関数を使用 | ブロックの設定を使い分ける |
| 異なる投稿や投稿タイプを表示するために[「ループ」]((https://developer.wordpress.org/themes/basics/the-loop/))を使用 | [クエリーループブロック](https://wordpress.org/support/article/query-loop-block/)と投稿テンプレートブロックを使用 |
| [ウィジェットエリア (サイドバー)](https://developer.wordpress.org/themes/functionality/sidebars/)と[ウィジェット](https://developer.wordpress.org/themes/functionality/widgets/)を使用可能 | ウィジェットの代わりにブロックを使用。*WordPress に（標準で）搭載されているウィジェットはブロック化されています。* |
| [カスタマイザー](https://developer.wordpress.org/themes/customize-api/)を使用可能 | サイトエディターを使用。カスタマイザーメニューはオプションで使用可能。 |
| メニューを含めるには[ナビゲーションメニュー](https://developer.wordpress.org/themes/functionality/navigation-menus/)の登録が必要 | [ナビゲーションブロック](https://wordpress.org/support/article/navigation-block/)を使用 |
| [カスタムヘッダー](https://developer.wordpress.org/themes/functionality/custom-headers/)を登録可能 | ブロックを使って画像を含むサイトヘッダーをフルカスタマイズ可能 |
| [カスタムロゴ](https://developer.wordpress.org/themes/functionality/custom-logo/)を登録可能 | サイトロゴブロックを使用 |
| [カスタム CSS とスクリプト](https://developer.wordpress.org/themes/basics/including-css-javascript/)をエンキューすることが可能 | カスタム CSS とスクリプトをエンキューすることもできるが theme.json 設定ファイルに依存する部分が多い |
| [theme.json](https://developer.wordpress.org/themes/advanced-topics/theme-json/)を使用できるが、テーマ作者がフロント用のスタイルをエンキューする必要がある。 | theme.json を使用可能、スタイルはエディターとフロントに自動的にエンキューされる |
| テンプレートファイルをルートディレクトリに配置可能 | テンプレートファイルを **templates** フォルダーに配置 |
| テンプレートパーツファイルをどのディレクトリにも配置可能 | テンプレートパーツを **parts** フォルダーに配置 |
| サイトエディターを使用して 404 ページやアーカイブページなどのサイトテンプレートの作成や編集は不可能 | サイトエディターを使用して 404 ページやアーカイブページなどのサイトテンプレートの作成や編集が可能 |
| *対応しているテーマでは*テンプレートエディターでブロックテンプレートの作成や編集が可能 | テンプレートエディターでブロックテンプレートの作成や編集が可能 |
