<!-- 
# Tools &amp; Resources
 -->

# ツール &amp; リソース

<!-- 
Whether you’re building your very first theme or your tenth, the following resources are meant to help ease the process. Keep in mind that there are various community tools not mentioned here as well but that still might aid in your efforts. 
 -->

あなたの初めてのテーマ構築でも、あるいはあなたの10個目のテーマ構築でも、以下のリソースはそのプロセスを容易にするために用意されています。ここで言及されていないさまざまなコミュニティ・ツールも存在し、それらがあなたの取り組みを助ける可能性があることを覚えておいてください。

<!-- 
## Block themes
 -->

## ブロック・テーマ

<!-- 
A block theme is a type of WordPress theme built using blocks. You can read more about these themes in the [Block Theme section](https://developer.wordpress.org/themes/block-themes/).
 -->

ブロック・テーマとは、ブロックを使用して構築された WordPress テーマの一種です。これらのテーマの詳細については、[ブロック・テーマのセクション](https://developer.wordpress.org/themes/block-themes/) をご覧ください。

<!-- 
[**Create Block Theme plugin**](https://wordpress.org/plugins/create-block-theme/) 
 -->

[**Create Block Theme プラグイン**](https://wordpress.org/plugins/create-block-theme/) 

<!-- 
This plugin was created by various community members. This tool can create standalone block themes and child themes, depending on your needs. Here are the high-level steps: 
 -->

本プラグインは、さまざまなコミュニティ・メンバーによって制作されました。本ツールは、必要に応じてスタンドアローンのブロック・テーマや子テーマを作成できます。主な手順は以下の通りです:  

<!-- 
1.  Install and activate the [Create Block Theme](https://github.com/WordPress/create-block-theme) plugin. You will also need to be running the latest version of the [Gutenberg](https://wordpress.org/plugins/gutenberg/) plugin.
2.  Make changes to your site design using the Customizer and Site Editor.
3.  Edit your templates using the Site Editor. For some things, you might need to edit the template files again later.
4.  In the WordPress Admin Dashboard, under Appearance there will be a new page called “Create Block Theme”. You can add the details for the theme here. These details will be used in the style.css file. 
5.  Click the “Create Block Theme” button. From there, a zip file will be downloaded which will contain all the files for your theme.
 -->

1.  [Create Block Theme](https://github.com/WordPress/create-block-theme) プラグインをインストールして有効化します。[Gutenberg](https://wordpress.org/plugins/gutenberg/) プラグインも最新版を実行している必要があります。
2.  「カスタマイザー」と「サイト・エディター」を使用して、あなたのサイトデザインを変更します。
3.  「サイト・エディター」を使用してあなたのテンプレートを編集します。後で再度テンプレート・ファイルを編集する必要がある場合があります。
4.  WordPress 管理ダッシュボードの「外観」に「ブロックテーマを作成」という新しいページが表示されます。ここでテーマの詳細情報を追加できます。これらの情報は style.css ファイルで使用されます。
5.  「ブロックテーマを作成」ボタンをクリックします。すると、あなたのテーマの全ファイルを含む zip ファイルがダウンロードされます。

<!-- 
[**Theme Generator**](https://fullsiteediting.com/block-theme-generator/)
 -->

[**Theme Generator**](https://fullsiteediting.com/block-theme-generator/)

<!-- 
This tool was created by Carolina Nymark and it allows you to create three different types of themes to start from:
 -->

本ツールは Carolina Nymark によって制作され、以下の3種類のテーマを作成して開始できます:

<!-- 
*   No Code: for non-developers who want to start from a blank theme and build directly in the Site Editor.
*   Empty: for developers to make their own with six templates and a theme.json with empty settings for you to complete.
*   Basic: for developers to explore with six templates, two template parts, three block patterns, and two custom block styles alongside some initial theme.json settings.
*   Advanced: for developers to explore with seven templates, five template parts, seven patterns, various block styles, and a more robust theme.json. It’s common to want to remove some of the examples.
 -->

*   No Code: 白紙のテーマから始め、サイト・エディターで直接構築したい、非開発者向けです。
*   Empty: 6つのテンプレートと設定が空の theme.json を含む、完全なテーマを自作したい、開発者向けです。
*   Basic: 6つのテンプレート、2つのテンプレート・パーツ、3つのブロック・パターン、2つのカスタム・ブロック・スタイルに加え、初期設定の theme.json を備えた、探求的な開発者向けです。
*   Advanced: 7つのテンプレート、5つのテンプレート・パーツ、7つのパターン、多様なブロック・スタイル、より堅牢な theme.json を備えた、探求的な開発者向けです。サンプルの一部を削除したい場合がよくあります。

<!-- 
**Comparison Chart**
 -->

**比較表**

<!-- 
<table><tbody><tr><td><strong>Tool</strong></td><td><strong>Child theme options?</strong></td><td><strong>Template creation?</strong></td><td><strong>Theme.json Controls</strong></td><td><strong>Demo content</strong></td></tr><tr><td>Create Block Theme plugin</td><td>Yes</td><td>Yes</td><td>No</td><td>No</td></tr><tr><td>Theme Generator</td><td>No</td><td>Yes</td><td>Yes</td><td>Yes</td></tr></tbody></table>
 -->

<table><tbody><tr><td><strong>ツール</strong></td><td><strong>子テーマ・オプション ?</strong></td><td><strong>テンプレート制作 ?</strong></td><td><strong>Theme.json コントロール</strong></td><td><strong>デモ・コンテンツ</strong></td></tr><tr><td>Create Block Theme プラグイン</td><td>Yes</td><td>Yes</td><td>No</td><td>No</td></tr><tr><td>Theme Generator</td><td>No</td><td>Yes</td><td>Yes</td><td>Yes</td></tr></tbody></table>

<!-- 
## Classic themes
 -->

## クラシック・テーマ

<!-- 
A classic theme is built with PHP templates, functions.php, and more. You can read more about these themes in the [Classic Theme section](https://developer.wordpress.org/themes/classic-themes/).
 -->

クラシック・テーマは、PHP テンプレート、functions.php などで構築されています。これらのテーマの詳細については [クラシック・テーマのセクション](https://developer.wordpress.org/themes/classic-themes/) をご覧ください。

<!-- 
The [\_s (Underscores)](https://underscores.me/) starter theme is a tool for initializing and creating a classic theme.
 -->

[\_s (Underscores)](https://underscores.me/) スターター・テーマは、クラシック・テーマを初期化および制作するためのツールです。

<!-- 
## Tools
 -->

## ツール

<!-- 
**WordPress Coding Standards for PHP\_CodeSniffer**
 -->

**`PHP_CodeSniffer` 用 WordPress コーディング標準**

<!-- 
This project is a collection of [PHP\_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer) rules (sniffs) that are used to validate code developed for WordPress, but can also be used when developing themes and plugins. They encompass coding style along with established best practices regarding interoperability, translatability, and security in the WordPress ecosystem, according to the official [WordPress Coding Standards](https://make.wordpress.org/core/handbook/best-practices/coding-standards/).
 -->

本プロジェクトは、WordPress 向けに開発されたコードの検証に使用される [PHP\_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer) ルール (スニッフ) のコレクションです。テーマやプラグインの開発時にも利用可能です。これらは公式の [WordPress コーディング標準](https://make.wordpress.org/core/handbook/best-practices/coding-standards/) にもとづき、WordPress エコ・システムにおける相互運用性、翻訳可能性、セキュリティに関する確立されたベスト・プラクティスとともに、コーディング・スタイルを網羅して定めています。

<!-- 
[WordPress Coding Standards for PHP\_CodeSniffer](https://github.com/WordPress/WordPress-Coding-Standards)
 -->

[`PHP_CodeSniffer` 用 WordPress コーディング標準](https://github.com/WordPress/WordPress-Coding-Standards)

<!-- 
The WPThemeReview Standards for PHP\_CodeSniffer are a collection of sniffs that aim to automate the code analysis part of the [Theme Review Process](https://make.wordpress.org/themes/handbook/review/) as much as possible using static code analysis.  
The WPThemeReview Standards require the WordPress Coding Standards.
 -->

`PHP_CodeSniffer` 用 WPThemeReview 標準は、静的コード解析を用いて [テーマ審査プロセス](https://make.wordpress.org/themes/handbook/review/) のコード分析部分を可能な限り自動化することを目的としたスニッフのコレクションです。
WPThemeReview 標準は、WordPress コーディング標準を前提としています。

<!-- 
[WPThemeReview Standards for PHP\_CodeSniffer](https://github.com/WPTT/WPThemeReview) 
 -->

[WPThemeReview Standards for PHP\_CodeSniffer](https://github.com/WPTT/WPThemeReview) 

<!-- 
[**Theme Check Plugin**](https://wordpress.org/plugins/theme-check/)
 -->

[**Theme Check プラグイン**](https://wordpress.org/plugins/theme-check/)

<!-- 
The theme check plugin is an easy way to test your theme and make sure it’s up to spec with the latest [theme review](https://make.wordpress.org/themes/handbook/review/) standards. With it, you can run all the same automated testing tools on your theme that WordPress.org uses for theme submissions. This allows you to resolve any issues that might come up before trying to submit your theme to the theme repository. 
 -->

Theme Check プラグインは、あなたのテーマをテストし、最新の [テーマ審査](https://make.wordpress.org/themes/handbook/review/) 標準に準拠していることを確認する簡単な方法です。これを使用すると、WordPress.org がテーマの提出に使用するのと同じ自動テストツールを、あなたのテーマに対してすべて実行できます。これにより、あなたのテーマをテーマリポジトリに提出しようとする前に、発生する可能性のある課題を解決できます。

<!-- 
## Training material
 -->

## 練習素材

<!-- 
Site Design with Full Site Editing: [Part 1](https://learn.wordpress.org/course/simple-site-design-with-full-site-editing/), [Part 2](https://learn.wordpress.org/course/part-2-personalized-site-design-with-full-site-editing-and-theme-blocks/), [Part 3](https://learn.wordpress.org/course/part-3-advanced-site-design-with-full-site-editing-site-editor-templates-and-template-parts/)
 -->

フルサイト編集によるサイト・デザイン: [パート1](https://learn.wordpress.org/course/simple-site-design-with-full-site-editing/)、[パート2](https://learn.wordpress.org/course/part-2-personalized-site-design-with-full-site-editing-and-theme-blocks/)、[パート3](https://learn.wordpress.org/course/part-3-advanced-site-design-with-full-site-editing-site-editor-templates-and-template-parts/)

<!-- 
[Anatomy of a Block Theme](https://learn.wordpress.org/tutorial/anatomy-of-a-block-theme/)
 -->

[ブロック・テーマの解剖学](https://learn.wordpress.org/tutorial/anatomy-of-a-block-theme/)

<!-- 
[Creating a landing page with a block theme](https://learn.wordpress.org/tutorial/creating-a-landing-page-with-a-block-theme/)
 -->

[ブロック・テーマを使用した、ランディング・ページの制作](https://learn.wordpress.org/tutorial/creating-a-landing-page-with-a-block-theme/)

<!-- 
[Building a home page with a block theme](https://learn.wordpress.org/tutorial/building-a-home-page-with-a-block-theme/)
 -->

[ブロック・テーマで、ホームページの構築](https://learn.wordpress.org/tutorial/building-a-home-page-with-a-block-theme/)

<!-- 
[Using Schema with WordPress theme.json](https://learn.wordpress.org/tutorial/using-schema-with-wordpress-theme-json/)
 -->

[WordPress theme.json で Schema の使用](https://learn.wordpress.org/tutorial/using-schema-with-wordpress-theme-json/)

<!-- 
[Create a Basic Child Theme for Block Themes](https://learn.wordpress.org/lesson-plan/create-a-basic-child-theme-for-block-themes/)
 -->

[ブロック・テーマ用の、基本子テーマの制作](https://learn.wordpress.org/lesson-plan/create-a-basic-child-theme-for-block-themes/)

<!-- 
Find more theme lessons on [learn.wordpress.org](https://learn.wordpress.org/?s=theme).
 -->

[learn.wordpress.org](https://learn.wordpress.org/?s=theme) で、さらに多くのテーマ・レッスンをご覧ください。