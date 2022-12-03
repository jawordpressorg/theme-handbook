<!--
# Block themes
-->
# ブロックテーマ

<!--
A block theme is a type of WordPress theme built using blocks. You can edit all parts of a block theme in the [Site Editor](https://wordpress.org/support/article/site-editor/).
-->
ブロックテーマはWordPress のテーマのひとつのタイプで、ブロックを使って構築します。[サイトエディタ](https://wordpress.org/support/article/site-editor/)からブロックテーマのすべてのパーツを編集することができます。

<!--
WordPress supports block themes from version 5.9. Together with the [Styles interface](https://wordpress.org/support/article/styles-overview/), block themes are part of full site editing. They are sometimes called full site editing themes. [Learn about the background to full site editing](https://developer.wordpress.org/block-editor/getting-started/full-site-editing/).
-->
WordPress はバージョン 5.9 からブロックテーマをサポートしています。[Styles interface](https://wordpress.org/support/article/styles-overview/) と一緒で、ブロックテーマはフルサイト編集の一部です。これらは時々フルサイト編集テーマとも呼ばれます[フルサイト編集の背景についてはこちらで学べます](https://developer.wordpress.org/block-editor/getting-started/full-site-editing/)。

<!--
You may also be interested in reading the [support article about block themes](https://wordpress.org/support/article/block-themes/).
-->
[ブロックテーマについてのサポート記事](https://wordpress.org/support/article/block-themes/)を読むのも面白いかも知れません。

<!--
In this part of the handbook, you will learn about:
-->
このハンドブックの箇所では以下のについて学ぶことができます

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
どうしてブロックテーマを作成するべきなのでしょうか? WordPress はクラシックテーマのサポートを続けていますが、ブロックテーマは拡張性とパフォーマンスを向上させるために作られています。

*   [Block themes enhances loading performance](https://make.wordpress.org/core/2021/07/01/block-styles-loading-enhancements-in-wordpress-5-8/) by loading styles only for rendered blocks on a page
*   Block themes are not required to manually enqueue stylesheets for both front-end and editors
*   Theme.json handles all aspects of [add_theme_support()](https://developer.wordpress.org/reference/functions/add_theme_support/)
*   Accessibility features such as Skip to content, keyboard navigation, and landmarks are generated automatically without adding additional code
*   With a block theme, the user can edit all parts of their website without code
*   By using the Styles interface, users can customize colors and typography for the website and for the blocks

*  ブロックテーマはページに描写されるブロックについてのみのスタイルを読み込むことで[読み込みのパフォーマンスを向上させています](https://make.wordpress.org/core/2021/07/01/block-styles-loading-enhancements-in-wordpress-5-8/)
*  ブロックテーマはフロントエンドとエディタそれぞれのタイルシートを手動でエンキューする必要がありません
*  Theme.json は [add_theme_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) の担う全てを処理できます
*  コンテンツのスキップや、キーボードのナビゲーション、ランドマークといったアクセシビリティ機能は特別なコードを追加することなく自動で生成されます
*  ブロックテーマでは、ユーザーはコードなしでウェブサイトのすべての部分を編集することができます
*  「スタイル」インターフェースにより、ウェブサイトやブロックの色やタイポグラフィーをカスタマイズすることができます。

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
クラシックなテーマを作り慣れているテーマ開発者のために、比較表が用意されています:

<table><tbody><tr><td><strong>Classic themes</strong>:</td><td><strong>Block themes</strong>:</td></tr><tr><td>Uses PHP files to display parts and content.</td><td>Uses HTML files to display blocks.<br>Uses PHP files as a fallback if WordPress can not find the HTML file.<br><em>single.html is the equivalent of using single.php.</em></td></tr><tr><td>Uses the <a href="https://developer.wordpress.org/themes/basics/template-hierarchy/" data-type="URL" data-id="https://developer.wordpress.org/themes/basics/template-hierarchy/">template hierarchy</a></td><td>Uses the template hierarchy</td></tr><tr><td>Uses PHP functions such as <a href="https://developer.wordpress.org/themes/basics/template-tags/" data-type="URL" data-id="https://developer.wordpress.org/themes/basics/template-tags/">template tags</a> to display content</td><td>Uses blocks for everything.<br><em>The post content block is the equivalent of using <code>the_content()</code>.</em></td></tr><tr><td>Use&nbsp;<a rel="noreferrer noopener" href="https://developer.wordpress.org/apis/handbook/internationalization/" target="_blank">PHP functions</a>&nbsp;to make text translatable</td><td>Text in HTML files is not translatable.<br><a rel="noreferrer noopener" href="https://developer.wordpress.org/block-editor/reference-guides/block-api/block-patterns/" target="_blank">Block patterns</a>&nbsp;can use PHP functions to make text translatable.</td></tr><tr><td>Uses PHP functions for <a href="https://developer.wordpress.org/themes/basics/conditional-tags/" data-type="URL" data-id="https://developer.wordpress.org/themes/basics/conditional-tags/">if/else conditionals</a></td><td>Uses block settings to achieve different results</td></tr><tr><td>Uses <a href="https://developer.wordpress.org/themes/basics/the-loop/" data-type="URL" data-id="https://developer.wordpress.org/themes/basics/the-loop/">the loop</a> to display different posts and post types</td><td>Uses the <a href="https://wordpress.org/support/article/query-loop-block/" data-type="URL" data-id="https://wordpress.org/support/article/query-loop-block/">query block</a> and the post template block</td></tr><tr><td>Can use <a href="https://developer.wordpress.org/themes/functionality/sidebars/" data-type="URL" data-id="https://developer.wordpress.org/themes/functionality/sidebars/">widget areas (sidebars)</a> and <a href="https://developer.wordpress.org/themes/functionality/widgets/" data-type="URL" data-id="https://developer.wordpress.org/themes/functionality/widgets/">widgets</a></td><td>Uses blocks instead of widgets. <em>Widgets included in WordPress have been converted to blocks.</em></td></tr><tr><td>Can use the <a href="https://developer.wordpress.org/themes/customize-api/" data-type="URL" data-id="https://developer.wordpress.org/themes/customize-api/">Customizer</a></td><td>Uses the Site Editor. Can optionally enable the Customizer menu</td></tr><tr><td>Must register a <a href="https://developer.wordpress.org/themes/functionality/navigation-menus/" data-type="URL" data-id="https://developer.wordpress.org/themes/functionality/navigation-menus/">navigation menu</a> to include a menu</td><td>Uses the <a href="https://wordpress.org/support/article/navigation-block/" data-type="URL" data-id="https://wordpress.org/support/article/navigation-block/">navigation block</a></td></tr><tr><td>Can register a <a href="https://developer.wordpress.org/themes/functionality/custom-headers/" data-type="URL" data-id="https://developer.wordpress.org/themes/functionality/custom-headers/">custom header</a></td><td>Uses blocks to fully customize site headers including images</td></tr><tr><td>Can register a <a href="https://developer.wordpress.org/themes/functionality/custom-logo/" data-type="URL" data-id="https://developer.wordpress.org/themes/functionality/custom-logo/">custom logo</a></td><td>Uses the site logo block</td></tr><tr><td>Can enqueue <a href="https://developer.wordpress.org/themes/basics/including-css-javascript/" data-type="URL" data-id="https://developer.wordpress.org/themes/basics/including-css-javascript/">custom CSS and scripts</a></td><td>Can enqueue custom CSS and scripts but relies more on blocks and the theme.json configuration file</td></tr><tr><td>Can use <a href="https://developer.wordpress.org/themes/advanced-topics/theme-json/" data-type="URL" data-id="https://developer.wordpress.org/themes/advanced-topics/theme-json/">theme.json</a>, but theme authors need to enqueue the styles for the front.</td><td>Can use theme.json, and the styles are enqueued automatically to the editor and front</td></tr><tr><td>Can place template files in the root directory</td><td>Places template files in the <strong>templates</strong> folder</td></tr><tr><td>Can place template parts in any directory</td><td>Places template parts in the <strong>parts</strong> folder</td></tr><tr><td>Can not create and edit site templates like 404 and archive pages in the Site Editor</td><td>Can create and edit site templates like 404 and archive pages in the Site Editor</td></tr><tr><td>Can create and edit block templates in the Template Editor<em> with theme support</em></td><td>Can create and edit block templates in the Template Editor</td></tr></tbody></table>
