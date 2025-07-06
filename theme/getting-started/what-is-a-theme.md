<!--
# What Is a Theme?
 -->

# テーマとは ?

<!--
A WordPress theme represents the design of your website. It can control everything from colors, to fonts, to the entire layout. In essence, what you see when viewing the front-end of your site is shaped by the theme.
 -->

WordPress のテーマとは、Web サイトのデザインを表すものです。色、フォント、レイアウト全体に至るまで、あらゆる要素をコントロールできます。つまり、サイトのフロントエンドでの見え方は、テーマによって形作られているのです。

<!-- 
[![A collage of site designs at an angle.](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-two-collage.jpg?resize=2400%2C1500&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-two-collage.jpg?ssl=1)
 -->

[![斜めにコラージュされたサイトデザイン。](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-two-collage.jpg?resize=2400%2C1500&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-two-collage.jpg?ssl=1)

<!--
Templates from the default Twenty Twenty-Two theme.
 -->

WordPress 5.9デフォルトの Twenty Twenty-Two テーマのテンプレート。

<!--
There are 1,000s of free WordPress themes in the [WordPress.org Theme Directory](https://wordpress.org/themes/) and even more from third-party directories and shops. Many people and businesses also have bespoke (custom-made) themes for their sites.
 -->

[WordPress.org テーマディレクトリ](https://ja.wordpress.org/themes/)には何千もの無償 WordPress テーマがあり、サードパーティーのディレクトリやショップでもさらに多くのテーマがあります。また、多くの個人や企業が、自分たちのサイト用に特注 (カスタム・メイド) のテーマを作成しています。

<!--
## What can themes do?
 -->

## テーマは何ができるの ?

<!--
Themes take the content stored by WordPress and display it in the browser. When you create a WordPress theme, you decide how that content looks and is displayed. There are many options available to you when building your theme. The biggest limit is your imagination. 
 -->

テーマは、WordPress が格納したコンテンツを、ブラウザに表示します。WordPress のテーマを作成する際、コンテンツの見た目や表示方法を決めるのはあなたです。テーマを構築する際に利用できるオプションはたくさんあります。最大の限界は、あなたの想像力です。

<!--
As a theme creator, you can:
 -->

テーマ作者として、あなたは次のことができます:

<!--
*   Create different layouts, such as one, two or more columns.
*   Control the typography of the site with custom font choices.
*   Skin the site with any color scheme you want.
*   Put a sidebar on the left or right side of the page. Or, have no sidebar at all.
*   Display featured images alongside posts.
 -->

*   1カラム、2カラム、またはそれ以上のカラムなど、さまざまなレイアウトを作成する。
*   独自のフォントなどを使って、サイトのタイポグラフィを指定する。
*   好きなカラースキームで、サイトを装飾する。
*   サイドバーをページの左側や右側に配置する。あるいは、サイドバーを表示しない。
*   投稿に、アイキャッチ画像を表示する。

<!-- 
[![The WordPress site editor showing the homepage template with a dotted black background and a three-column grid of posts.](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-three-style-variation.jpg?resize=2400%2C1255&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-three-style-variation.jpg?ssl=1)
 -->

[![WordPress サイトエディターでは、黒を基調としたドット柄の背景と、3カラムの投稿グリッドで構成されたホームページのテンプレートが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-three-style-variation.jpg?resize=2400%2C1255&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-three-style-variation.jpg?ssl=1)

<!-- 
Editing a Twenty Twenty-Three theme style variation.
 -->

Twenty Twenty-Three テーマのスタイルバリエーションを編集する。

<!--
The WordPress theming system is incredibly powerful. As with every web design project, a good theme is more than defining a layout or two and a few custom colors. The best themes improve engagement with a website’s content *in addition* to being beautiful.
 -->

WordPress のテーマシステムは極めて強力です。Web デザインプロジェクトと同様、良いテーマはレイアウトをいくつか定義したり、いくつかのカスタムカラーを設定するだけではありません。最高のテーマは、美しくする *だけでなく*、Web サイトのコンテンツとのエンゲージメントを向上させます。

<!-- 
There really are not many limits to the possibilities. Outside of your imagination, theme creation requires some baseline knowledge, which is covered in the [Reading this handbook](https://developer.wordpress.org/themes/getting-started/reading-this-handbook/) page of this chapter. That’s what this handbook is all about—*teaching you what you need to know to build themes of your own*.
 -->

本当に可能性は無限です。あなたの想像力以外では、テーマの作成にはいくつかの基本的な知識が必要で、それは本章の [このハンドブックを読む](https://developer.wordpress.org/themes/getting-started/reading-this-handbook/) ページでカバーされています。それがこのハンドブックのすべて — *あなた独自のテーマを構築するために知るべきことを教えること* です。

<!-- 
## Theme types
 -->

## テーマの種類

<!-- 
WordPress supports two primary types of themes: **block** and **classic**.
 -->

WordPress は、主に2種類のテーマをサポートしています: **ブロック** と **クラシック**です。

<!-- 
There is also a classic subtype that is called a **hybrid** theme, and you’ll learn about it below, too. But the most important distinction is block vs. classic.
 -->

また、**ハイブリッド** テーマと呼ばれる、クラシックのサブタイプもあり、それについても後述します。しかし、最も重要な相違は、ブロックとクラシックです。

<!-- 
Technically, you can even build your own theming system altogether. That’s outside the scope of this handbook, but it’s at least worth noting that WordPress lets you build pretty much whatever you set your mind to.
 -->

技術的には、完全に独自のテーマ設定システムも構築できます。それはこのハンドブックの範囲外ですが、WordPress は、あなたが思い描くほとんどすべてのものを構築できるということは、少なくとも注目に値します。

<!-- 
### Block themes
 -->

### ブロック・テーマ

<!-- 
Block themes are the modern method of building WordPress themes. They generally follow a standard set of conventions and are built entirely out of blocks. This handbook will primarily focus on building themes using this method because it is the future of the WordPress project.
 -->

ブロックテーマは、WordPress テーマを構築する最新の方法です。通常、標準的な一連の規約に従い、完全にブロックで構築されます。このハンドブックでは、主にこの方法でテーマを構築することに焦点を当てます。なぜなら、これが WordPress プロジェクトの未来なのですから。

<!-- 
Block themes rely on HTML-based [block templates](https://developer.wordpress.org/themes/templates/) that contain block markup. Both creators and users can edit the templates in the Site Editor. Users can also customize [global settings and styles](https://developer.wordpress.org/themes/global-settings-and-styles/) defined by the theme’s `theme.json` file through the Styles interface. 
 -->

ブロックテーマは、ブロック・マークアップを含む HTML ベースの [ブロックテンプレート](https://developer.wordpress.org/themes/templates/) に依存しています。作成者もユーザーも、サイトエディターでテンプレートを編集できます。また、ユーザーは、スタイル・インターフェースを通じて、テーマの `theme.json` ファイルで定義された [グローバル設定とスタイル](https://developer.wordpress.org/themes/global-settings-and-styles/) をカスタマイズできます。

<!-- 
It’s also possible to export a theme directly from the Site Editor without touching any code. Technically, you cannot create a new theme from scratch entirely from the editor, but you can modify the templates and styles of an existing theme—in essence, creating a custom theme of your own.
 -->

また、コードを一切触ることなく、サイトエディターから直接テーマをエクスポートできます。技術的には、エディターで完全にゼロから新しいテーマを作成できませんが、既存のテーマのテンプレートやスタイルを変更できます - 要するに、独自のカスタムテーマを作成するのです。

<!-- 
[![WordPress site editor with a single post template that shows a design with a yellow background and black text.](https://i0.wp.com/developer.wordpress.org/files/2023/11/site-editor-styles.png?resize=2400%2C1255&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/site-editor-styles.png?ssl=1)
 -->

[![WordPress サイトエディターで、黄色い背景と黒いテキストのデザインを示す単一投稿テンプレート。](https://i0.wp.com/developer.wordpress.org/files/2023/11/site-editor-styles.png?resize=2400%2C1255&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/site-editor-styles.png?ssl=1)

<!-- 
Editing a theme’s styles in the Site Editor.
 -->

サイトエディターでテーマのスタイルを編集する。

<!-- 
### Classic themes
 -->

### クラシック・テーマ

<!-- 
Classic themes use a PHP-based templating system, which is still supported in WordPress today. They are still in wide use because they were built on the theming system that was first introduced in 2005 with the launch of [WordPress 1.5](https://wordpress.org/news/2005/02/strayhorn/). There is a long and deep history of classic theming in WordPress, which continues on. For this reason, the handbook maintains documentation for classic themes in the [Classic Themes](https://developer.wordpress.org/themes/classic-themes/) chapter.
 -->

クラシック・テーマは、PHP ベースのテンプレートシステムを使用しており、WordPress では、現在もサポートされています。これらは、2005年に [WordPress 1.5](https://wordpress.org/news/2005/02/strayhorn/) のリリースとともに初めて導入されたテーマシステムにもとづいて構築されているため、現在も広く使用されています。WordPress には、クラシック・テーマ設定の長く深い歴史があり、それは今も続いています。このため、ハンドブックでは [クラシック・テーマ](https://developer.wordpress.org/themes/classic-themes/) の章に、クラシック・テーマに関するドキュメントを維持しています。

<!-- 
Unlike block themes, classic themes have far fewer standards to adhere to, but there are APIs you can use for specific features. The classic theme creation process also requires some minimal PHP, HTML, and CSS code knowledge, at least.
 -->

ブロック・テーマとは異なり、クラシック・テーマは遵守すべき基準がはるかに少ないですが、特定の機能を実現するための API を利用できます。クラシック・テーマの作成プロセスでは、少なくとも基本的な PHP、HTML、CSS のコード知識も必要です。

<!-- 
[![WordPress customizer showing the Twenty Twenty-Two theme. On the left is a list of options, and on the right a preview of the site homepage.](https://i0.wp.com/developer.wordpress.org/files/2023/11/customizer-twenty-twenty.jpg?resize=2400%2C1255&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/customizer-twenty-twenty.jpg?ssl=1)
 -->

[![Twenty Twenty-Two テーマを表示する WordPress カスタマイザー。左側はオプションのリスト、右側はサイトのホームページのプレビュー。](https://i0.wp.com/developer.wordpress.org/files/2023/11/customizer-twenty-twenty.jpg?resize=2400%2C1255&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/customizer-twenty-twenty.jpg?ssl=1)

<!-- 
Editing the default Twenty Twenty theme styles in the customizer.
 -->

カスタマイザーで WordPress 4.7デフォルトの Twenty Twenty テーマのスタイルを編集する。

<!-- 
### Hybrid themes
 -->

### ハイブリッド・テーマ

<!-- 
Hybrid themes are merely classic themes that have adopted some modern block-related features, such as [global settings and styles](https://developer.wordpress.org/themes/global-settings-and-styles/) or [block template parts](https://developer.wordpress.org/themes/templates/template-parts/). This is a widely agreed-upon term by the community, but it is not an “official” theme type. At the end of the day, hybrids are still classic themes.
 -->

ハイブリッド・テーマとは、[グローバル設定とスタイル](https://developer.wordpress.org/themes/global-settings-and-styles/) や [ブロックテンプレート・パーツ](https://developer.wordpress.org/themes/templates/template-parts/) などのモダンなブロック関連機能を採用したクラシック・テーマに過ぎません。これはコミュニティによって広く認められている用語ですが、「公式」テーマタイプではありません。結局のところ、ハイブリッドは依然としてクラシック・テーマであることに変わりはありません。

<!-- 
## Become familiar with themes
 -->

## テーマに習熟する

<!-- 
To build a WordPress theme of your own, you should familiarize yourself with how themes work from a user’s viewpoint. Before diving into the creation process, try [installing a theme](https://wordpress.org/documentation/article/work-with-themes/) and playing around with it.
 -->

独自の WordPress テーマを作成するには、ユーザーの視点からテーマのしくみを熟知する必要があります。作成プロセスに入る前に、[テーマのインストール](https://wordpress.org/documentation/article/work-with-themes/) を試して、遊んでみてください。

<!-- 
WordPress comes with several default themes, titled *Twenty \[Year\]*, but you should also try other themes from the [Theme Directory](https://wordpress.org/themes/) just to get a feel for the possibilities.
 -->

WordPress には *Twenty \[Year\]* と題されたいくつかのデフォルトのテーマが付属していますが、その可能性を実感するために、[テーマディレクトリ](https://wordpress.org/themes/) にある他のテーマも試してみてください。

<!--
## What are themes made of?
 -->

## テーマは何でできているの ?

<!--
Themes can include many different folders and file types. The list below is non-exhaustive, but it includes some of common things you might see:
 -->

テーマには、さまざまなフォルダーやファイル形式が含まれる場合があります。以下のリストは網羅的なものではありませんが、よく見かけるものも含まれています:

<!--
*   Templates (`.html` in block themes and `.php` in classic themes)
*   CSS Stylesheets
*   JavaScript
*   PHP
*   Media (images, audio, video, etc.)
*   JSON
 -->

*   テンプレート (ブロック・テーマでは `.html`、クラシック・テーマでは `.php`)
*   CSS スタイルシート
*   JavaScript
*   PHP
*   メディア (画像、音声、動画など)
*   JSON

<!--
You will learn more about the specific folders and files used to create a theme in the next chapter: [Core Concepts](https://developer.wordpress.org/themes/core-concepts).
 -->

テーマを作成するための具体的なフォルダーやファイルについては、次の章で詳しく学習します: 
[コア・コンセプト](https://developer.wordpress.org/themes/core-concepts) を参照してください。

<!--
## What is the difference between themes and plugins?
 -->

## テーマとプラグインの違いとは ?

<!--
It is common for there to be overlap between features found in themes and plugins. However, best practices are:
 -->

テーマとプラグインに存在する機能には、重複する部分があることが一般的です。しかし、ベストプラクティスは:

<!--
*   Themes control the *presentation* of content.
*   Plugins control the behaviors and features of your site.
 -->

*   テーマは、コンテンツの **表示** をコントロールする。
*   プラグインは、サイトの挙動や機能をコントロールする。

<!--
Any theme that you create should not add site-critical functionality. Doing so means that a user loses access to that functionality when they change their theme.
 -->

作成するテーマは、サイトに不可欠な機能を追加すべきではありません。そうすると、ユーザーがテーマを変更した際に、その機能へのアクセスを失うことになります。

<!-- 
For example, say you build a theme with a portfolio feature. Users who build their portfolio with your feature will lose it when they change themes. By leaving critical features to plugins, you make it possible to change the design of a website while its features remain intact.
 -->

たとえば、ポートフォリオ機能付きのテーマを構築したとします。あなたの機能でポートフォリオを構築したユーザーは、テーマを変更するとそのポートフォリオを失うことになるでしょう。重要な機能をプラグインに委ねることで、機能をそのままに Web サイトのデザインを変更することが可能になるのです。

<!-- 
Remember, some users switch themes often. It is best practice to make sure any functionality their sites require, even if the design changes, is in a separate plugin.
 -->

テーマを頻繁に変更するユーザーもいることを覚えておいてください。たとえデザインが変わっても、彼らのサイトが必要とする機能を、別々のプラグインに分離しておくことがベストプラクティスです。
