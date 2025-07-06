<!-- 
# Tools and Setup
 -->

# ツールとセットアップ

<!-- 
In this document, you will learn about the tools that you will need to get off to a solid start when building WordPress themes. You will also find resources on setting up a development environment for testing your projects. 
 -->

このドキュメントでは、WordPress テーマを構築する際に、確実にスタートを切るために必要なツールについて学びます。また、プロジェクトをテストするための開発環境のセットアップに関する参考資料も掲載してます。

<!-- 
While it is definitely possible to create and build block themes without any of these tools, they are foundational pieces of a good workflow.
 -->

これらのツールなしでもブロック・テーマを制作し、構築できますが、これらのツールは良好なワークフローの基盤となる重要な要素です。

<!-- 
## Development environment
 -->

## 開発環境

<!-- 
When building WordPress themes, it is a good idea to do it within an environment that is separate from a live (i.e., production) site. Before creating your first WordPress theme, you should set up a development environment.
 -->

WordPress テーマを構築する際には、ライブ (つまり本番) サイトとは別の環境で行うことをおすすめします。あなたの最初の WordPress テーマを制作する前に、開発環境をセットアップしておく必要があります。

<!-- 
Don’t let this process scare you if it’s your first time. In the long run, you will be happy you learned how to set this up.
 -->

初めての方でも、このプロセスに怖がらないでください。長期的に見れば、このセットアップ方法を学んだことを喜ぶでしょう。

<!-- 
### Why set up a development environment?
 -->

### なぜ開発環境をセットアップするのですか ?

<!-- 
Development environments allow you to test code before it goes live on a production site. You don’t want to change something, push it live, and later realize you created a fatal error that took down the whole website. 
 -->

開発環境では、コードを本番サイトで公開する前にテストできます。何かを変更し、本番環境にプッシュした後で、Web サイト全体をダウンさせる致命的なエラーを発生させたことに後で気付くようなことは避けたいものです。

<!-- 
By using a development environment, you can test things to ensure they work before they are live.
 -->

開発環境を使用することで、本番環境で公開する前に、機能が正常に動作するかどうかをテストできます。

<!-- 
Your development environment can either be local (on your computer) or on a remote server. But configuring a local environment to work on your theme is beneficial for several reasons:
 -->

開発環境は、(ご自身のコンピューターの) ローカルまたはリモートサーバー上に設定できます。ただし、テーマの開発にローカル環境を構成することは、いくつかの理由から有益です:

<!-- 
*   You do not need an internet connection to build your theme.
*   You can build your theme without relying on a remote server. This speeds up the building process, and you can see changes instantly in your browser.
*   You can test your theme from many perspectives. This is important if you plan on releasing it to a larger audience and want maximum compatibility.
 -->

*   あなたのテーマを構築する際、インターネット接続は必須ではありません。
*   リモートサーバーに依存せずに、あなたのテーマを構築できます。これにより構築プロセスが高速化し、あなたのブラウザ上で変更内容を即時確認できます。
*   あなたのテーマを多様な視点からテストできます。これは、大規模なユーザー層に公開する予定で、最大限の互換性を確保したい場合に重要です。

<!-- 
### Setting up a local development environment
 -->

### ローカル開発環境のセットアップ

<!-- 
For developing WordPress themes, you need to set up a development environment that is suited to WordPress. This list is not exhaustive, but here are several options to choose from:
 -->

WordPress テーマの開発には、WordPress に適した開発環境をセットアップする必要があります。このリストは網羅的なものではありませんが、いくつかの選択肢を紹介します:

<!-- 
*   [@wordpress/env](https://developer.wordpress.org/block-editor/getting-started/devenv/get-started-with-wp-env/) (local WordPress environment package)
*   [Docker](https://www.docker.com/)
*   [Local](https://localwp.com/)
*   [MAMP](https://www.mamp.info/en/mamp/mac/)
*   [Studio](https://developer.wordpress.com/studio/)
*   [Varying Vagrant Vagrants](https://varyingvagrantvagrants.org/) (VVV)
*   [XAMPP](https://www.apachefriends.org/)
 -->

*   [@wordpress/env](https://developer.wordpress.org/block-editor/getting-started/devenv/get-started-with-wp-env/) (ローカル WordPress 環境パッケージ)
*   [Docker](https://www.docker.com/)
*   [Local](https://localwp.com/)
*   [MAMP](https://www.mamp.info/en/mamp/mac/)
*   [Studio](https://developer.wordpress.com/studio/)
*   [Varying Vagrant Vagrants](https://varyingvagrantvagrants.org/) (VVV)
*   [XAMPP](https://www.apachefriends.org/)

<!-- 
For more information, read the [Setting Up a Development Environment](https://make.wordpress.org/core/handbook/tutorials/installing-a-local-server/) documentation in the Core Handbook.
 -->

詳細については、コア・ハンドブックの [開発環境のセットアップ](https://make.wordpress.org/core/handbook/tutorials/installing-a-local-server/) ドキュメントを御覧ください。

<!-- 
## Installing WordPress
 -->

## WordPress のインストール

<!-- 
Before you begin building themes in your development environment, you must also install WordPress. 
 -->

開発環境でテーマの構築を始める前に、WordPress もインストールしておく必要があります。

<!-- 
Some of the development environments include methods for automatically installing an instance of WordPress. You can skip this step if this is the case for you.
 -->

開発環境によっては、WordPress のインスタンスを自動的にインストールする手段が用意されているものもあります。その場合は、この手順をスキップしてください。

<!-- 
To install WordPress on your own, follow the [How to install WordPress](https://developer.wordpress.org/advanced-administration/before-install/howto-install/) documentation from the Advanced Administration handbook. Then, of course, come back here and learn more about creating WordPress themes!
 -->

自身で WordPress をインストールするには、上級管理ハンドブックの [WordPress のインストール方法](https://developer.wordpress.org/advanced-administration/before-install/howto-install/) ドキュメントに従ってください。もちろん、その後、ここに戻って WordPress テーマの制作についてさらに詳しく学んでください !

<!-- 
## Code editor
 -->

## コードエディター

<!-- 
> *A good code editor is worth its weight in gold.*
> 
> Someone Wise
 -->

> *優れたコードエディターは、その価値は金に匹敵する。*
> 
> とある賢者

<!-- 
On a more serious note, a good code editor gives you proper syntax highlighting, error reporting, integration with version control systems (VCS), and much more. It’s there to make your life easier.
 -->

本題に戻ると、優れたコードエディターは、適切なシンタックス・ハイライト、エラー報告、バージョン管理システム (VCS) との統合など、多くの機能を提供します。それは、あなたの作業を効率化するために存在しています。

<!-- 
Technically, you could edit code in a plain text editor, but you’d be missing out on all the best features that true code editors and IDEs (Integrated Development Environments) bring to life.
 -->

技術的には、プレーンなテキストエディターでもコードを編集できますが、真のコードエディターや統合開発環境 (IDE) が提供する最高の機能の恩恵を受けることができません。

<!-- 
[![Visual Studio Code editor program with a theme's single.html file open, showing block markup.](https://i0.wp.com/developer.wordpress.org/files/2023/11/vs-code-editor.png?resize=2757%2C1497&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/vs-code-editor.png?ssl=1)
 -->

[![Visual Studio Code エディターで、テーマの single.html ファイルが開かれており、ブロック・マークアップが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/11/vs-code-editor.png?resize=2757%2C1497&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/vs-code-editor.png?ssl=1)

<!-- 
Editing a theme’s `single.html` template in Visual Studio Code
 -->

Visual Studio Code でテーマの `single.html` テンプレートを編集する

<!-- 
There are many free and open-source editors to choose from. Here are some of the more popular ones:
 -->

無償かつオープンソースのエディターは数多く存在します。以下に、特に人気の高いものの一部を挙げます:

<!-- 
*   [Visual Studio Code](https://code.visualstudio.com/) (VS Code)
*   [VIM](https://www.vim.org/)
*   [Brackets](https://brackets.io/)
*   [Notepad++](https://notepad-plus-plus.org/)
*   [GNU Emacs](https://www.gnu.org/software/emacs/)
*   [TextMate](https://macromates.com/)
 -->

*   [Visual Studio Code](https://code.visualstudio.com/) (VS Code)
*   [VIM](https://www.vim.org/)
*   [Brackets](https://brackets.io/)
*   [Notepad++](https://notepad-plus-plus.org/)
*   [GNU Emacs](https://www.gnu.org/software/emacs/)
*   [TextMate](https://macromates.com/)

<!-- 
There are also many proprietary editors that are free or cost a fee to use. Whatever you decide to use, pick something you feel comfortable with.
 -->

また、無償または有償で利用できる専用エディターも数多く存在します。どのようなツールを選択するにせよ、ご自身にとって使いやすく感じるものを選んでください。

<!-- 
## Other development tools
 -->

## その他の開発ツール

<!-- 
A code editor and development environment are the foundational pieces of creating a WordPress theme. However, there are other tools and resources that you will likely find useful for your project.
 -->

コードエディターと開発環境は、WordPress テーマを制作するための基礎的な要素です。しかし、プロジェクトに役立つその他のツールや参考資料も数多くあります。

<!-- 
### Test data
 -->

### テストデータ

<!-- 
WordPress allows you to [import XML files](https://wordpress.org/documentation/article/importing-content/) containing real or dummy data for testing your themes. This lets you see how your theme performs with different types of content and layouts. Here are two options for importing:
 -->

WordPress では、あなたのテーマのテスト用に実際のデータまたはダミーデータを含む [XML ファイルのインポート](https://wordpress.org/documentation/article/importing-content/) が可能です。これにより、あなたのテーマで、さまざまな種類のコンテンツやレイアウトがどのように表示されるかを確認できます。インポートには、次の2つのオプションがあります:

<!-- 
*   [WordPress.org Theme Test Data](https://codex.wordpress.org/Theme_Unit_Test)
*   [WordPress.com Theme Test Data](http://themetest.wordpress.com/) *(includes WordPress.com-specific data)*
 -->

*   [WordPress.org テーマ・テストデータ](https://codex.wordpress.org/Theme_Unit_Test)
*   [WordPress.com テーマ・テストデータ](http://themetest.wordpress.com/) *(WordPress.com 独自のデータを含む)*
*   [WordPress.org テーマ・テストデータ](https://github.com/jawordpressorg/theme-test-data-ja) *日本語版*

<!-- 
If nothing else, you need some type of demo/test content to see what your theme looks like in action. You could even create test posts and pages of your own!
 -->

少なくとも、あなたのテーマが実際にどのように機能するかを確認するために、何らかのデモ/テスト・コンテンツが必要です。自分でテスト用の投稿やページも制作できます !

<!-- 
### Plugins
 -->

### プラグイン

<!-- 
In addition to test data, there are several WordPress plugins that can help make sure your theme is following standard practices and not producing debugging notices. These are optional but can be useful:
 -->

テストデータに加え、あなたのテーマが標準的な実践に従っていることを確認し、デバッグ通知を生成しないようにするのを助ける WordPress プラグインがいくつかあります。これらは任意ですが、役立つ場合があります:

<!-- 
*   [Theme Check](https://wordpress.org/plugins/theme-check/): Tests your theme for compliance with the latest WordPress standards and practices.
*   [Debug Bar](https://wordpress.org/plugins/debug-bar/): Adds an admin bar to your WordPress admin and provides a central location for debugging.
*   [Query Monitor](https://wordpress.org/plugins/query-monitor/): Allows debugging of database queries, API requests, and AJAX used to generate theme pages and functionality.
*   [Log Deprecated Notices](https://wordpress.org/plugins/log-deprecated-notices/): Logs incorrect function usage, deprecated file usage, and deprecated function usage in your theme.
*   [Monster Widget](https://wordpress.org/plugins/monster-widget/): Consolidates the core WordPress widgets into a single widget, making it easier to test them all at once (*classic themes only*).
 -->

*   [Theme Check](https://wordpress.org/plugins/theme-check/): あなたのテーマが最新の WordPress 標準および実践に準拠しているかどうかをテストします。
*   [Debug Bar](https://wordpress.org/plugins/debug-bar/): WordPress 管理画面に管理バーを追加し、デバッグのための一元的な場所を提供します。
*   [Query Monitor](https://wordpress.org/plugins/query-monitor/): あなたのテーマのページや機能を生成するために使用される、データベース・クエリー、API リクエスト、AJAX のデバッグを可能にします。
*   [Log Deprecated Notices](https://wordpress.org/plugins/log-deprecated-notices/): あなたのテーマ内の、関数の不適切な使用、非推奨のファイルの使用、および非推奨の関数の使用をログに記録します。
*   [Monster Widget](https://wordpress.org/plugins/monster-widget/): WordPress のコア・ウィジェットを1つのウィジェットに統合し、それらを一度に簡単にテストできるようにします (*クラシック・テーマのみ*)。

<!-- 
## WordPress.org Theme Review Guidelines
 -->

## WordPress.org テーマのレビュー・ガイドライン

<!-- 
It is a good idea to stay up to date with the [theme guidelines](https://make.wordpress.org/themes/handbook/review/required/) provided by the WordPress.org Themes Team. These guidelines are required if you plan to submit your theme to the official [Theme Directory](https://wordpress.org/themes), but they are also good principles for anyone creating a theme.
 -->

WordPress.org テーマチームが提供する [テーマ・ガイドライン](https://make.wordpress.org/themes/handbook/review/required/) の最新情報を常に把握しておくことをおすすめします。このガイドラインは、公式 [テーマ・ディレクトリ](https://wordpress.org/themes) にあなたのテーマを提出する場合に必須ですが、テーマを制作するすべてのユーザーにとって良い指針となります。

<!-- 
You should also follow the [WordPress Coding Standards](https://make.wordpress.org/core/handbook/best-practices/coding-standards/) when writing any code for your theme. This will help make sure what you are creating meets some minimum quality standards.
 -->

また、あなたのテーマ用のコードを書く際には、[WordPress コーディング規約](https://make.wordpress.org/core/handbook/best-practices/coding-standards/)、[日本語版 WordPress コーディング規約](https://ja.wordpress.org/team/handbook/coding-standards/wordpress-coding-standards/) に従う必要があります。これにより、制作物が最低限の品質標準を満たしていることを確認できます。