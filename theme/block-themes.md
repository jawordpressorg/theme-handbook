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

<!--
*   [Block themes enhances loading performance](https://make.wordpress.org/core/2021/07/01/block-styles-loading-enhancements-in-wordpress-5-8/) by loading styles only for rendered blocks on a page
*   Block themes are not required to manually enqueue stylesheets for both front-end and editors
*   Theme.json handles all aspects of [add_theme_support()](https://developer.wordpress.org/reference/functions/add_theme_support/)
*   Accessibility features such as Skip to content, keyboard navigation, and landmarks are generated automatically without adding additional code
*   With a block theme, the user can edit all parts of their website without code
*   By using the Styles interface, users can customize colors and typography for the website and for the blocks
-->

*  ブロックテーマはページに描写されるブロックについてのみのスタイルを読み込むことで[読み込みのパフォーマンスを向上させています](https://make.wordpress.org/core/2021/07/01/block-styles-loading-enhancements-in-wordpress-5-8/)
*  ブロックテーマはフロントエンドとエディタそれぞれのタイルシートを手動でエンキューする必要がありません
*  Theme.json は [add_theme_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) の担う全てを処理できます
*  コンテンツのスキップや、キーボードのナビゲーション、ランドマークといったアクセシビリティ機能は特別なコードを追加することなく自動で生成されます
*  ブロックテーマでは、ユーザーはコードなしでウェブサイトのすべての部分を編集することができます
*  「スタイル」インターフェースにより、ウェブサイトやブロックの色やタイポグラフィーをカスタマイズすることができます

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
| Classic themes: | Block themes: |
|---|---|
| Uses PHP files to display parts and content. | Uses HTML files to display blocks.Uses PHP files as a fallback if WordPress can not find the HTML file. *single.html is the equivalent of using single.php.* |
| Uses the [template hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/) | Uses the template hierarchy |
| Uses PHP functions such as [template tags](https://developer.wordpress.org/themes/basics/template-tags/) to display content | Uses blocks for everything.*The post content block is the equivalent of using `the_content()`.* |
| Use [PHP functions](https://developer.wordpress.org/apis/handbook/internationalization/) to make text translatable | Text in HTML files is not translatable.[Block patterns](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-patterns/) can use PHP functions to make text translatable. |
| Uses PHP functions for [if/else conditionals](https://developer.wordpress.org/themes/basics/conditional-tags/) | Uses block settings to achieve different results |
| Uses [the loop](https://developer.wordpress.org/themes/basics/the-loop/) to display different posts and post types | Uses the [query block](https://wordpress.org/support/article/query-loop-block/) and the post template block |
| Can use [widget areas (sidebars)](https://developer.wordpress.org/themes/functionality/sidebars/) and [widgets](https://developer.wordpress.org/themes/functionality/widgets/) | Uses blocks instead of widgets. *Widgets included in WordPress have been converted to blocks.* |
| Can use the [Customizer](https://developer.wordpress.org/themes/customize-api/) | Uses the Site Editor. Can optionally enable the Customizer menu |
| Must register a [navigation menu](https://developer.wordpress.org/themes/functionality/navigation-menus/) to include a menu | Uses the navigation block |
| Can register a [custom header](https://developer.wordpress.org/themes/functionality/custom-headers/) | Uses blocks to fully customize site headers including images |
| Can register a [custom logo](https://developer.wordpress.org/themes/functionality/custom-logo/) | Uses the site logo block |
| Can enqueue [custom CSS and scripts](https://developer.wordpress.org/themes/basics/including-css-javascript/) | Can enqueue custom CSS and scripts but relies more on blocks and the theme.json configuration file |
| Can use [theme.json](https://developer.wordpress.org/themes/advanced-topics/theme-json/), but theme authors need to enqueue the styles for the front. | Can use theme.json, and the styles are enqueued automatically to the editor and front |
| Can place template files in the root directory | Places template files in the templates folder |
| Can place template parts in any directory | Places template parts in the parts folder |
| Can not create and edit site templates like 404 and archive pages in the Site Editor | Can create and edit site templates like 404 and archive pages in the Site Editor |
| Can create and edit block templates in the Template Editor *with theme support* | Can create and edit block templates in the Template Editor |
-->
| クラシックテーマ: | ブロックテーマ: |
|---|---|
| コンテンツの表示に PHP ファイルを使用。 | ブロックの表示に HTML を使用。HTML ファイルをWordPressが見つけられない場合にPHPをフォールバックとして使用。 *single.html は single.php に相当* |
| [テンプレート階層](https://ja.wordpress.org/team/handbook/theme-development/basics/template-hierarchy/)を使用 | テンプレート階層を使用 |
| コンテンツの表示に[テンプレートタグ](https://developer.wordpress.org/themes/basics/template-tags/)のような PHP 関数を使用 | 全てにブロックを使用。*投稿コンテンツブロックは `the_content()` に相当* |
| テキストを翻訳可能にするために [PHP 関数](https://developer.wordpress.org/apis/handbook/internationalization/)を使用 | HTMLファイルのテキストは翻訳不可能。[ブロックパターン](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-patterns/)はPHP関数を使用して翻訳可能にできる |
| [if/elseの条件分岐](https://developer.wordpress.org/themes/basics/conditional-tags/)にPHPの関数を使用 | ブロックの設定を使い分ける |
| 異なる投稿や投稿タイプを表示するために[「ループ」]((https://developer.wordpress.org/themes/basics/the-loop/))を使用 | [クエリーループブロック](https://wordpress.org/support/article/query-loop-block/)と投稿テンプレートブロックを使用 |
| [ウィジェットエリア (サイドバー)](https://developer.wordpress.org/themes/functionality/sidebars/)と[ウィジェット](https://developer.wordpress.org/themes/functionality/widgets/)を使用可能 | ウィジェットの代わりにブロックを使用。*WordPress に（標準で）搭載されているウィジェットはブロック化されています。* |
| [カスタマイザー](https://developer.wordpress.org/themes/customize-api/)を使用可能 | サイトエディターを使用。カスタマイザーメニューはオプションで使用可能。 |
| メニューを含めるには[ナビゲーションメニュー](https://developer.wordpress.org/themes/functionality/navigation-menus/)の登録が必要 | [ナビゲーションブロック](https://wordpress.org/support/article/navigation-block/)を使用 |
| [カスタムヘッダー](https://developer.wordpress.org/themes/functionality/custom-headers/)を登録可能 | ブロックを使って画像を含むサイトヘッダーをフルカスタマイズ可能 |
| [カスタムロゴ](https://developer.wordpress.org/themes/functionality/custom-logo/)を登録可能 | サイトロゴブロックを使用 |
| [カスタム CSS とスクリプト](https://developer.wordpress.org/themes/basics/including-css-javascript/)をエンキューすることが可能 | カスタム CSS とスクリプトをエンキューすることもできるが theme.json 設定ファイルに依存する部分が多い |
| [theme.json](https://developer.wordpress.org/themes/advanced-topics/theme-json/)を使用できるが、テーマ作者がフロント用のスタイルをエンキューする必要がある。 | theme.json を使用可能、スタイルはエディターとフロントに自動的にエンキューされる |
| テンプレートファイルをルートディレクトリに配置可能 | テンプレートファイルをテンプレートフォルダに配置 |
| サイトエディターを使用して404ページやアーカイブページなどのサイトテンプレートの作成や編集は不可能 | サイトエディターを使用して404ページやアーカイブページなどのサイトテンプレートの作成や編集が可能 |
| *対応しているテーマでは*テンプレートエディターでブロックテンプレートの作成や編集が可能 | テンプレートエディターでブロックテンプレートの作成や編集が可能 |
