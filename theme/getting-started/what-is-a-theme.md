<!-- # What is a Theme? -->
# テーマとは

<!-- A WordPress theme changes the design of your website, often including its layout. Changing your theme changes how your site looks on the front-end, i.e. what a visitor sees when they browse to your site on the web. There are thousands of free WordPress themes in the [WordPress.org Theme Directory](https://wordpress.org/themes/), though many WordPress sites use custom themes. -->
WordPress のテーマは、Web サイトのデザインを変更するもので、多くの場合、そのレイアウトも含みます。テーマを変更すると、フロントエンドでのサイトの見え方が変わります。つまり、訪問者がウェブ上であなたのサイトを閲覧したときに見えるものということです。多くの WordPress サイトはカスタムテーマを使用していますが、WordPress.org のテーマディレクトリには何千もの無料の WordPress テーマがあります。

<!-- ## What can themes do? -->
## テーマでできること

<!-- 
Themes take the content and data stored by WordPress and display it in the browser. When you create a WordPress theme, you decide how that content looks and is displayed. There are many options available to you when building your theme. For example:

*   Your theme can have different layouts, such as static or responsive, using one column or two.
*   Your theme can display content anywhere you want it to be displayed.
*   Your theme can specify which devices or actions make your content visible.
*   Your theme can customize its typography and design elements using CSS.
*   Other design elements like images and videos can be included anywhere in your theme.

WordPress themes are incredibly powerful. But, as with every web design project, a theme is more than color and layout. Good themes improve engagement with your website’s content *in addition* to being beautiful.
-->
テーマは、WordPress が保存しているコンテンツやデータを、ブラウザに表示します。WordPress のテーマを作成すると、そのコンテンツがどのように見えるか、どのように表示されるかが決まります。テーマを構築する際には、さまざまなオプションが用意されています。例えば、以下のようなものがあります。

* テーマには、静的レイアウトやレスポンシブレイアウト、1列や2列のレイアウトなど、さまざまなレイアウトを設定できる。
* テーマでは、コンテンツを表示したい場所に表示することができる。
* テーマでは、コンテンツが表示されるデバイスやアクションを指定できる。
* タイポグラフィやデザイン要素をCSSでカスタマイズできる。
* 画像や動画などのデザイン要素を、テーマのどこにでも入れることができる。

WordPress のテーマは非常に強力です。しかし、他のウェブデザインプロジェクトと同様に、テーマは色やレイアウトだけではありません。優れたテーマは、美しさに加えて、ウェブサイトのコンテンツへのエンゲージメントを高めます。


<!-- ## What are themes made of? -->
## テーマは何でできているの？

<!-- At their most basic level, WordPress themes are collections of different files that work together to create what you see, as well as how your site behaves. -->
WordPressテーマは、最も基本的なレベルではさまざまなファイルの集合体であり、それらが連動してサイトの表示や動作を作ります。

<!-- ### Required files -->
### 必要なファイル

<!--
There are only **two files absolutely required in a WordPress** theme:

1.  `index.php` – the main template file
2.  `style.css` – the main style file

Though not required, you may see additional files in a theme’s folder including:

*   PHP files – including [template files](https://developer.wordpress.org/themes/basics/template-files/ "Template Files Page")
*   [Localization files](https://developer.wordpress.org/theme/functionality/localization/ "Link to the localization section of the theme developer handbook")
*   CSS files
*   Graphics
*   JavaScript
*   Text files – usually license info*,* `readme.txt` instructions, and a changelog file
-->

WordPress テーマに **絶対に必要な2つのファイル** は:

1.  `index.php` – テンプレートのメインファイル
2.  `style.css` – メインのスタイルファイル

必須ではありませんが、テーマのフォルダ内に以下のような追加ファイルが表示される場合があります。
*   PHP ファイル - [テンプレートファイル](https://developer.wordpress.org/themes/basics/template-files/ "Template Files Page")として読み込まれます
*   [ローカライゼーションファイル](https://developer.wordpress.org/theme/functionality/localization/ "Link to the localization section of the theme developer handbook")
*   CSS ファイル
*   グラフィック
*   JavaScript
*   テキストファイル – `readme.txt` 説明などのライセンス情報や変更のログファイルによく使われます

<!-- ## What is the difference between a theme and a plugin? -->
## テーマとプラグインの違いは?
<!--
It is common to find cross-over between features found in themes and plugins. However, best practices are:

*   a theme controls the *presentation* of content; whereas
*   a plugin is used to control the behavior and features of your WordPress site.

**Any theme you create should not add critical functionality.** Doing so means that when a user changes their theme, they lose access to that functionality. For example, say you build a theme with a portfolio feature. Users who build their portfolio with your feature will lose it when they change themes.

By moving critical features to plugins, you make it possible for the design of your website to change, while the functionality remains the same.

Note: Remember, some users switch themes often. It is best practice to make sure any functionality your site requires, even if the design changes, is in a separate plugin.
-->
テーマとプラグインの機能が混在しているのはよくあることです。しかし、ベストプラクティスは次の通りです。

*   テーマは、コンテンツの「見せ方」をコントロールするもの
*   プラグインは、WordPress サイトの動作や機能をコントロールするもの

**作成したテーマは、重要な機能を追加するべきではありません。** ユーザーがテーマを変更したときに、その機能が使えなくなってしまいます。例えば、あなたがポートフォリオ機能を持つテーマを作ったとします。この機能を使ってポートフォリオを作成したユーザーは、テーマを変更するとその機能を失うことになります。

<!-- ## Themes on WordPress.org -->
## WordPress.org 上のテーマ

<!-- One of the safest places to download WordPress themes is in the [WordPress.org Theme Directory](https://wordpress.org/themes/ "WordPress Theme Directory"). All themes are closely reviewed, and must meet rigorous [theme review guidelines](https://developer.wordpress.org/theme/release/theme-review-guidelines/ "WordPress Theme Review Guidelines") to ensure quality and security. -->
WordPress のテーマをダウンロードする最も安全な場所のひとつに、[WordPress.org のテーマディレクトリ](https://wordpress.org/themes/ "WordPress Theme Directory")があります。すべてのテーマは厳密に審査され、品質と安全性を確保するための厳格な[テーマ審査ガイドライン](https://developer.wordpress.org/theme/release/theme-review-guidelines/ "WordPress Theme Review Guidelines")をクリアしなければなりません。

<!-- ## Getting Started -->
## はじめる

<!-- Now you know what a theme is it’s time to get started. If you haven’t already done so yet, you should [set up your local development environment](https://developer.wordpress.org/themes/getting-started/setting-up-a-development-environment/). You can then [check out some examples of WordPress themes](https://developer.wordpress.org/themes/getting-started/theme-development-examples/) or, if you can’t wait any longer to get started, [dive into building your first theme](https://developer.wordpress.org/themes/basics/). -->

テーマとは何かを理解したところで、いよいよ始めましょう。まだやっていなければ、[ローカルの開発環境をセットアップ](https://developer.wordpress.org/themes/getting-started/setting-up-a-development-environment/)してください。その後、[WordPress テーマの例をいくつかチェック](https://developer.wordpress.org/themes/getting-started/theme-development-examples/)したり、待ちきれないという方は、[最初のテーマを作ることにしましょう](https://developer.wordpress.org/themes/basics/)。
