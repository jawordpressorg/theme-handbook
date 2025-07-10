<!-- 
# Theme Structure
 -->

# テーマ構造

<!-- 
In the [Getting Started](https://developer.wordpress.org/themes/getting-started/) chapter, you learned the basics of what a theme is and how to get one up and running without code. A no-code approach is perfectly OK for simple themes, but once you want to add things that are not possible in the user interface, you’ll need to start working directly with code.
 -->

[はじめに](https://developer.wordpress.org/themes/getting-started/) 章では、テーマの基本概念と、コードを書かずにテーマをセットアップする方法について学びました。シンプルなテーマの場合、コードを書かないアプローチは問題ありませんが、ユーザーインターフェースでは実現できない機能を追加したい場合は、コードを直接編集する必要があります。

<!-- 
The first step of customizing theme code is to open the theme in your preferred file editor. You can use any theme for this, even the one you created from the Getting Started chapter.
 -->

テーマのコードをカスタマイズする最初のステップは、お好みのファイルエディターでテーマを開くことです。この作業には、どのテーマでも、たとえば、「はじめに」章で作成したテーマでも、使用できます。

<!-- 
It’s a good idea to familiarize yourself with what others are doing, so feel free to look at several [block themes](https://wordpress.org/themes/tags/full-site-editing/) from the WordPress theme directory.
 -->

他の人がどのようなことを行っているかを確認しておくことは良いアイデアですので、WordPress テーマ・ディレクトリからいくつかの [ブロック・テーマ](https://wordpress.org/themes/tags/full-site-editing/) を自由に閲覧してみてください。

<!-- 
This document will walk you through what the file and folder structure will look like in a typical block theme.
 -->

このドキュメントでは、典型的なブロック・テーマにおけるファイルとフォルダーの構造が、どのように構成されるかを説明します。

<!-- 
## Files and folders
 -->

## ファイルとフォルダー

<!-- 
WordPress themes are nothing more than a collection of various files that rely on different web technologies, such as HTML, CSS, and PHP. Block themes also follow a standard structure in how many of those files are laid out.
 -->

WordPress テーマは、HTML、CSS、PHP などのさまざまな Web 技術に依存する複数のファイルの集合体に過ぎません。ブロック・テーマも、それらのファイルの配置方法における標準的な構造に従っています。

<!-- 
At its most basic, a theme’s structure will look similar to the following. Take note of the files/folders marked **required** because they are necessary for a block theme to work:
 -->

最も基本的なレベルでは、テーマの構造は次のようなものになります。ブロック・テーマが機能するために必要ですので、**必須** とマークされたファイル/フォルダーに注意してください:

<!-- 
*   `parts/`
    *   `footer.html`
    *   `header.html`
*   `patterns/`
    *   `example.php`
*   `styles/`
    *   `example.json`
*   `templates/`
    *   `404.html`
    *   `archive.html`
    *   `index.html` (required)
    *   `singular.html`
*   `README.txt`
*   `functions.php`
*   `screenshot.png`
*   `style.css` (required)
*   `theme.json`
 -->

*   `parts/`
    *   `footer.html`
    *   `header.html`
*   `patterns/`
    *   `example.php`
*   `styles/`
    *   `example.json`
*   `templates/`
    *   `404.html`
    *   `archive.html`
    *   `index.html` (必須)
    *   `singular.html`
*   `README.txt`
*   `functions.php`
*   `screenshot.png`
*   `style.css` (必須)
*   `theme.json`

<!-- 
### Required files
 -->

### 必須ファイル

<!-- 
There are two necessary files for WordPress to recognize your block theme, and you will learn more about these in the coming documentation:
 -->

WordPress がブロック・テーマを認識するために必要なファイルは2つあって、これらは次のドキュメントで詳しく説明しています:

<!-- 
*   **`style.css`** ([Main Stylesheet](https://developer.wordpress.org/themes/core-concepts/main-stylesheet/)): This file is required for configuring theme data, such as its name and description. It can also be used for adding custom CSS.
*   **`templates/index.html`** ([Templates](https://developer.wordpress.org/themes/core-concepts/templates/)): The default/fallback template. This is necessary for WordPress to consider this a block theme.
 -->

*   **`style.css`** ([メイン・スタイルシート](https://developer.wordpress.org/themes/core-concepts/main-stylesheet/)): このファイルは、テーマの名前や説明などのテーマデータを設定するために必要です。また、カスタム CSS を追加するためにも使用できます。
*   **`templates/index.html`** ([テンプレート](https://developer.wordpress.org/themes/core-concepts/templates/)): デフォルト/フォールバック・テンプレート。これは、WordPress がブロック・テーマだと認識するために必要です。

<!-- 
### Optional files
 -->

### 任意のファイル

<!-- 
A theme can include any number of custom files other than the required list above. WordPress also looks for a few other files and uses them if they are available:
 -->

テーマには、上記の必須ファイル一覧以外にも、任意の数のカスタムファイルを含めることができます。さらに、WordPress は、その他のいくつかのファイルも検索し、それらが利用可能な場合はそれらを使用します:

<!-- 
*   **`README.txt`** ([Theme Review: Files](https://make.wordpress.org/themes/handbook/review/required/#9-files)): This is not used directly by the WordPress software. But it is a required file when submitting a theme to the official WordPress theme directory, meant to provide information about the theme to users.
*   **`functions.php`** ([Custom Functionality](https://developer.wordpress.org/themes/core-concepts/custom-functionality/)): A PHP file that WordPress automatically loads after the theme is initialized during the page-loading process. You can use it to run custom PHP.
*   **`screenshot.png`**: A 1200×900 screenshot image of your theme. Used for displaying your theme under **Appearance > Themes** in the WordPress admin and in the WordPress theme directory (if submitted there). Both `.png` and `.jpg` are acceptable file formats. 
*   **`theme.json`** ([Global Settings and Styles](https://developer.wordpress.org/themes/core-concepts/global-settings-and-styles/)): Used to configure settings and styles for the site, integrating with the user interface.
 -->

*   **`README.txt`** ([テーマ・レビュー: ファイル](https://make.wordpress.org/themes/handbook/review/required/#9-files)): これは WordPress ソフトウェアでは、直接使用されません。しかし、WordPress の公式テーマ・ディレクトリにテーマを提出する際に、ユーザーに対して、テーマに関する情報を提供するために必要なファイルです。
*   **`functions.php`** ([カスタム機能](https://developer.wordpress.org/themes/core-concepts/custom-functionality/)): ページ読み込みプロセス中にテーマが初期化された後、WordPress が自動的にロードする PHP ファイルです。カスタム PHP を実行するために使用できます。
*   **`screenshot.png`**: あなたのテーマの、1200×900ピクセルのスクリーンショット画像です。WordPress 管理画面の **外観 > テーマ** および (提出した場合には) WordPress テーマディレクトリ内で、あなたのテーマを表示するために使用されます。`.png` と `.jpg` の両方のファイルフォーマットが使用可能です。
*   **`theme.json`** ([グローバル設定とスタイル](https://developer.wordpress.org/themes/core-concepts/global-settings-and-styles/)): ユーザー・インターフェースと統合され、サイトの設定とスタイルを設定するために使用されます。

<!-- 
### Standard folders
 -->

### 標準フォルダー

<!-- 
In the example above, there were a few folders included. A theme can have many more folders, but WordPress has designated a few of them for specific features. You will learn more about these folders as you read through this chapter:
 -->

上記の例では、いくつかのフォルダーが含まれていました。テーマにはさらに多くのフォルダーが含まれる可能性がありますが、WordPress ではそのうちのいくつかを、特定の機能用に指定しています。本章を読み進めるうちに、これらのフォルダーについてさらに詳しく理解できます:

<!-- 
*   **`parts`** ([Template Parts](https://developer.wordpress.org/themes/templates/template-parts/)): Houses custom template parts for your theme. Parts are smaller sections that you can include within top-level templates. Often, this will include things like headers, footers, and sidebars.
*   **`patterns`** ([Block Patterns](https://developer.wordpress.org/themes/features/block-patterns/)): Reusable patterns made up of one or more blocks that users can insert via the editor interface. WordPress will automatically register files included in this folder.
*   **`styles`** ([Style Variations](https://developer.wordpress.org/themes/global-settings-and-styles/style-variations/)): Variations on the theme’s global settings and styles stored in individual JSON files.
*   **`templates`** ([Templates](https://developer.wordpress.org/themes/templates/templates/)): Files that represent the overall document structure of the front-end. Templates are made up of block markup and are what site visitors see.
 -->

*   **`parts`** ([テンプレート・パーツ](https://developer.wordpress.org/themes/templates/template-parts/)): あなたのテーマ用の、カスタム・テンプレート・パーツを格納します。パーツは、トップレベル・テンプレート内に含めることができる、小さなセクションです。通常、ヘッダー、フッター、サイドバーなどが含まれます。
*   **`patterns`** ([ブロック・パターン](https://developer.wordpress.org/themes/features/block-patterns/)): ユーザーがエディター・インターフェース経由で挿入できる、1つまたは複数のブロックから構成される、再利用可能なパターンです。WordPress は、このフォルダーに含まれるファイルを自動的に登録します。
*   **`styles`** ([スタイル・バリエーション](https://developer.wordpress.org/themes/global-settings-and-styles/style-variations/)): テーマのグローバル設定とスタイルのバリエーションで、個別の JSON ファイルに保存されます。
*   **`templates`** ([テンプレート](https://developer.wordpress.org/themes/templates/templates/)): フロントエンドの全体的なドキュメント構造を表すファイルです。テンプレートはブロック・マークアップで構成されており、サイト訪問者が目にするものです。

<!-- 
## Advanced theme structure
 -->

## 高度なテーマ構造

<!-- 
This section is meant to familiarize you with some of the common files you’ll see in themes but not to cover every possibility in detail. These files are entirely optional and will differ from theme to theme. You may skip this section for now if you are not comfortable with more advanced development methods.
 -->

このセクションでは、テーマ内でよく見かける一般的なファイルについて説明しますが、すべての可能性を詳細にカバーするものではありません。これらのファイルは完全に任意であり、テーマによって異なります。より高度な開発方法に慣れていない場合は、このセクションをスキップしてもかまいません。

<!-- 
In reality, block themes can contain many more files and folders. The more complex the project becomes, the more complex its structure will be. 
 -->

実際、ブロック・テーマには、さらに多くのファイルやフォルダーが含まれることがあります。プロジェクトが複雑になるほど、その構造も複雑になります。

<!-- 
Let’s add a few extra files and folders to the original example:
 -->

元の例に、追加のファイルとフォルダーをいくつか追加してみましょう:

<!-- 
*   `assets/`
    *   `css/`
        *   `core-site-title.css`
    *   `images/`
        *   `header-background.png`
    *   `js/`
        *   `navigation.js`
*   `inc/`
    *   `ClassName.php`
    *   `functions-helpers.php`
*   `parts/`
    *   `footer.html`
    *   `header.html`
*   `patterns/`
    *   `example.php`
*   `styles/`
    *   `example.jso`n
*   `templates/`
    *   `404.html`
    *   `archive.html`
    *   `index.html` (required)
    *   `singular.html`
*   `.editorconfig`
*   `.gitattributes`
*   `.gitignore`
*   `CHANGELOG.md`
*   `LICENSE.md`
*   `README.txt`
*   `functions.php`
*   `package.json`
*   `screenshot.png`
*   `style.css` (required)
*   `theme.json`
 -->

*   `assets/`
    *   `css/`
        *   `core-site-title.css`
    *   `images/`
        *   `header-background.png`
    *   `js/`
        *   `navigation.js`
*   `inc/`
    *   `ClassName.php`
    *   `functions-helpers.php`
*   `parts/`
    *   `footer.html`
    *   `header.html`
*   `patterns/`
    *   `example.php`
*   `styles/`
    *   `example.jso`n
*   `templates/`
    *   `404.html`
    *   `archive.html`
    *   `index.html` (必須)
    *   `singular.html`
*   `.editorconfig`
*   `.gitattributes`
*   `.gitignore`
*   `CHANGELOG.md`
*   `LICENSE.md`
*   `README.txt`
*   `functions.php`
*   `package.json`
*   `screenshot.png`
*   `style.css` (必須)
*   `theme.json`

<!-- 
### Optional folders
 -->

### 任意のフォルダー

<!-- 
There is no limit on what folders may be included, but the above example added two of the most common use cases you’ll come across in WordPress themes:
 -->

フォルダーの追加に制限はありませんが、上記の例では WordPress テーマでよく遭遇する、最も一般的な2つのユースケースを追加しています:

<!-- 
*   **`assets`** ([Including Assets](https://developer.wordpress.org/themes/core-concepts/including-assets/)): Many theme authors use this folder to store additional CSS, Images/Media, and JavaScript needed for their theme. This folder may also have other names, such as `resources` or `public`.
*   **`inc`** ([Custom Functionality](https://developer.wordpress.org/themes/core-concepts/custom-functionality/)): Themes will often have custom PHP classes or files stored in this folder for additional functionality. This folder may also be seen named as `includes`, `src`, and more.
 -->

*   **`assets`** ([アセットを含む](https://developer.wordpress.org/themes/core-concepts/including-assets/)): 多くのテーマ作成者は、自身のテーマに必要な追加の CSS、画像/メディア、JavaScript を、このフォルダーに保存しています。このフォルダーは、`resources` や `public` など、他の名前で呼ばれることもあります。
*   **`inc`** ([カスタム機能](https://developer.wordpress.org/themes/core-concepts/custom-functionality/)): テーマによっては、追加の機能を実現するために、このフォルダーにカスタム PHP クラスやファイルが格納されている場合があります。このフォルダーは、`includes` や `src` など、他の名前で呼ばれることもあります。

<!-- 
### Optional files
 -->

### 任意のファイル

<!-- 
This list is nowhere near exhaustive, but it includes some common files used in theme development. *(Note: most of the following links lead to external, third-party sites and are not affiliated with WordPress.)*
 -->

このリストは決して網羅的なものではありませんが、テーマ開発でよく使用される一般的なファイルの一部を含んでいます。*(注意: 以下のリンクのほとんどは、外部サイトやサードパーティのサイトにリンクしており、WordPress とは一切関係がありません。)*

<!-- 
*   **`.editorconfig`** ([EditorConfig](https://editorconfig.org/)): Used for configuring formatting, such as line endings and spacing, for code editors.
*   **`.gitattributes`** ([Git: Attributes](https://git-scm.com/docs/gitattributes)): Configures attributes with the Git version control system.
*   **`.gitignore`** ([Git: Ignore](https://git-scm.com/docs/gitignore)): Defines files to ignore when committing code to a Git repository.
*   **`CHANGELOG.md`** ([Keep a Changelog](https://keepachangelog.com/)): A human-readable log of important changes for each release of your theme.
*   **`LICENSE.md`** ([Theme Review: Licensing & Copyright](https://make.wordpress.org/themes/handbook/review/required/#1-licensing-copyright)): Defines the license for the theme. Note that all themes submitted to the WordPress theme directory must be licensed under the GPL v2+.
*   **`package.json`** ([npm: package.json](https://docs.npmjs.com/files/package.json/)): Often used to define a build process and development dependencies within a Node environment.
 -->

*   **`.editorconfig`** ([EditorConfig](https://editorconfig.org/)): コードエディターの行末やスペースなどのフォーマットを設定するために使用されます。
*   **`.gitattributes`** ([Git: 属性](https://git-scm.com/docs/gitattributes)): Git バージョン管理システムで、属性を設定します。
*   **`.gitignore`** ([Git: 無視](https://git-scm.com/docs/gitignore)): Git リポジトリにコードをコミットする際に、無視するファイルを定義します。
*   **`CHANGELOG.md`** ([変更履歴の保持](https://keepachangelog.com/)): あなたのテーマの各リリースにおける重要な変更点を、人間が読みやすいログとして記録します。
*   **`LICENSE.md`** ([テーマ・レビュー: ライセンスと著作権](https://make.wordpress.org/themes/handbook/review/required/#1-licensing-copyright)): テーマのライセンスを定義します。WordPress テーマ・ディレクトリに提出されるすべてのテーマは、GPL v2以上のライセンス下にある必要があることに注意してください。
*   **`package.json`** ([npm: package.json](https://docs.npmjs.com/files/package.json/)): Node 環境内で、ビルドプロセスと開発での依存関係を定義するために、頻繁に使用されます。

<!-- 
Don’t feel discouraged if you do not understand all of these files and their purposes yet. Again, these are entirely optional elements of a developer’s workflow. Feel free to learn more about them at your own pace at a later time.
 -->

これらのファイルとその目的をすべて理解できていないからといって、落胆しないでください。繰り返しになりますが、これらは開発者のワークフローにおいて、完全に任意の要素です。自身のペースで、後日いつでも詳しく学ぶことができます。

<!-- 
### Code editor view
 -->

### コードエディター画面

<!-- 
Here is a quick editor view of a real-world theme with an advanced structure:
 -->

以下は、高度な構造を持つ実際のテーマのクイックエディター画面です:

<!-- 
[![Visual Studio Code editor showing the structure of a theme's files and folders. In the code area, a theme.json file is shown.](https://i0.wp.com/developer.wordpress.org/files/2023/11/theme-file-structure.png?resize=2048%2C1143&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/theme-file-structure.png?ssl=1)
 -->

[![Visual Studio Code エディターで、テーマのファイルとフォルダーの構造が表示されている。コードエリアには、theme.json ファイルが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/11/theme-file-structure.png?resize=2048%2C1143&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/theme-file-structure.png?ssl=1)

<!-- 
This is vastly more complex than the basics that this documentation is introducing. The point is that, even when building block themes following standard practices, you will have a lot of freedom to customize things. You may want to integrate with version control systems, add in a build process, and more.
 -->

これは、このドキュメントで説明している基本的な内容よりも、はるかに複雑です。要点は、標準的な実践に従ってブロックテーマを構築する場合でも、カスタマイズする自由度が非常に高いということです。バージョン管理システムとの統合、ビルドプロセスの追加など、さらに多くのことも行いたいかもしれません。

<!-- 
So, consider this documentation the foundation in which you can build upon. But there is no harm in keeping it simple and sticking with the basics.
 -->

つまり、このドキュメントを基盤として、その上に構築していくことを検討してはいかがでしょう。しかし、シンプルに保ち、基本に忠実であることに害はありません。