<!-- 
# Testing
 -->

# テスト

<!-- 
If you’ve followed this handbook, you’ll already have a good grasp on the testing required before submitting your theme to the WordPress.org theme directory. If you haven’t, this page will give you a quick refresher.
 -->

このハンドブックに沿って進めてきたなら、WordPress.org テーマディレクトリにあなたのテーマを提出する前にテストすべき事項について、すでにしっかり理解できているはずです。もしそうでない場合、このページで簡単に復習できます。

<!-- 
Testing is incredibly important before releasing a theme. You may have built the most beautiful WordPress theme, but if it breaks when someone tries to comment or insert an image, your theme isn’t ready for real world usage.
 -->

テーマをリリースする前にテストを行うことは、非常に重要です。最も美しい WordPress テーマを作成したとしても、誰かがコメントを投稿したり画像を挿入しようとした際に不具合が発生するなら、あなたのテーマは実環境での使用に耐えられる状態ではありません。

<!-- 
Before testing your theme, make sure you’ve setup a development environment. There are a number of ways to setup your environment, many of which are documented on the [Setting up a Development Environment](https://developer.wordpress.org/themes/getting-started/setting-up-a-development-environment/) page.
 -->

あなたのテーマをテストする前に、開発環境がセットアップされていることを確認してください。あなたの環境をセットアップする方法はいくつかあり、その多くは [開発環境のセットアップ](https://developer.wordpress.org/themes/getting-started/setting-up-a-development-environment/) ページに記載されています。

<!-- 
## Theme Unit Test
 -->

## テーマ・ユニットテスト

<!-- 
After you’ve setup your development environment, you’ll need test content to test your theme with. While you can create your own test content, the theme review team has created the [Theme Unit Test](https://codex.wordpress.org/Theme_Unit_Test), which includes many different types of content. This will help ensure that your theme works in circumstances you may not have anticipated.
 -->

あなたの開発環境をセットアップしたら、あなたのテーマをテストするためのテストコンテンツが必要になります。独自のテストコンテンツも作成できますが、テーマレビューチームが [テーマ・ユニットテスト](https://codex.wordpress.org/Theme_Unit_Test) (日本語版は[こちら](https://github.com/jawordpressorg/theme-test-data-ja)) を作成しており、これにはさまざまな種類のコンテンツが含まれています。これにより、想定していなかった状況でもあなたのテーマが正常に動作することを確認できます。

<!-- 
The Theme Unit Test is a WordPress export file that can be imported into any WordPress installation by using the WordPress Importer. You should import it into your local development environment.
 -->

テーマ・ユニットテストは、WordPress インポーターを使用して任意の WordPress インストール環境にインポート可能な WordPress エクスポート・ファイルです。あなたのローカル開発環境にインポートしてください。

<!-- 
## WordPress Settings
 -->

## WordPress 設定

<!-- 
Making tweaks and changes to your WordPress installation is another good way to ensure that you’ve built your theme to handle numerous scenarios. Use the following settings to test your theme.
 -->

あなたの WordPress インストールに微調整や変更を加えることは、あなたのテーマがさまざまなシナリオに対応できるように構築されていることを確認するもう一つの良い方法です。以下の設定を使用して、あなたのテーマをテストしてください。

<!-- 
**General**  
Set the Site Title to something long and set the Tagline to something even longer. These settings will test how your theme handles edge cases for site titles and taglines.
 -->

**一般設定**

「サイトのタイトル」を長いものに設定し、「キャッチフレーズ」はさらに長いものに設定してください。これらの設定により、あなたのテーマが「サイトのタイトル」と「キャッチフレーズ」の特殊なケースを、どのように処理するかがテストされます。

<!-- 
**Reading**  
Set “Blog pages show at most” to 5. This setting will ensure that index/archive pagination is triggered.
 -->

**表示設定**

「1ページに表示する最大投稿数」を、5に設定してください。この設定により、インデックス/アーカイブのページネーションが確実に作動します。

<!-- 
**Discussion**  
Enable “Threaded Comments” at least 3 levels deep. This setting will facilitate testing of your theme’s comment list styling.
 -->

**ディスカッション**

「スレッド (入れ子) にするコメントの階層数」を、少なくとも3階層まで有効にしてください。この設定により、テーマのコメントリストのスタイル設定をテストし易くします。

<!-- 
Enable “Break comments into pages” and set 5 comments per page to test the pagination and styling of comments.
 -->

「コメントを複数ページに分割する」を有効にし、1ページあたり5件のコメントを設定して、コメントのページネーションとスタイルをテストしてください。

<!-- 
**Media**  
Remove the values for the large size of media to test the theme’s `$content_width` setting.
 -->

**メディア設定**

画像サイズの大サイズ用の値を削除し、テーマの `$content_width` 設定をテストしてください。

<!-- 
**Permalinks**  
Change the permalink setting a few times to ensure your theme can handle various URL formats.
 -->

**パーマリンク設定**

パーマリンク構造を数回変更し、あなたのテーマがさまざまな URL 形式に対応できることを確認してください。

<!-- 
For more setup instructions, take a look at the [Theme Unit Test](https://codex.wordpress.org/Theme_Unit_Test#Setup) page in the WordPress Codex.
 -->

詳細なセットアップ手順については、WordPress Codex の [テーマ・ユニットテスト](https://codex.wordpress.org/Theme_Unit_Test#Setup) ページをご覧ください。

<!-- 
## WordPress Beta Tester
 -->

## WordPress ベータ・テスター

<!-- 
WordPress releases happen three times a year. It’s a good idea to test your theme against the next version of WordPress so you can anticipate issues when the next version is released. This can be done easily with the [WordPress Beta Tester](https://wordpress.org/plugins/wordpress-beta-tester/) plugin. The plugin makes it easy to download either the latest nightly version of WordPress or the latest branch version (for minor bugfix releases). This is especially useful when anticipating a new major release or developing for an upcoming feature.
 -->

WordPress リリースは年に3回行われます。あなたのテーマを WordPress の次期バージョンでテストすることは良い考えです。そうすれば、次期バージョンがリリースされた際に発生する可能性のある課題を事前に予測できます。これは [WordPress Beta Tester](https://wordpress.org/plugins/wordpress-beta-tester/) プラグインで簡単に実現できます。このプラグインを使えば、WordPress の最新ナイトリー版または最新ブランチ版 (マイナーなバグ修正リリース用) を簡単にダウンロードできます。これは、新しいメジャーリリースを予測する場合や、今後の機能開発を行う場合に特に有用です。

<!-- 
## Testing and debugging tools
 -->

## テストおよびデバッグツール

<!-- 
### Theme Check
 -->

### Theme Check

<!-- 
Each theme goes through an automated check before a reviewer even sees it. If there are any immediate problems with the theme, identified by the automated check, the theme will be rejected with notes on how to resolve the issues. The [Theme Check](https://wordpress.org/plugins/theme-check/) plugin adds a dashboard link under Appearance so you can run the exact same checks that WordPress.org does right from your administration panel. Doing this prior to uploading your theme lets you know what needs to be addressed prior to submission. Running the check will give you a list of any warnings your theme has generated and what items are required for the theme to be accepted in the WordPress.org theme directory, as well as any recommended items that may be missing from your theme.
 -->

各テーマは、審査担当者が確認する前に、自動チェックを経ます。自動チェックでテーマにただちに対処すべき問題が検出された場合、その課題の解決方法に関する注記とともにテーマは却下されます。[Theme Check](https://wordpress.org/plugins/theme-check/) プラグインは、ダッシュボードの「外観」メニュー下にリンクを追加します。これにより、WordPress.org と同じチェックを管理パネルから直接実行できます。あなたのテーマをアップロードする前にこれを行うことで、提出前に修正すべき点を把握できます。チェックを実行すると、あなたのテーマが生成した警告の一覧と、WordPress.org テーマディレクトリで承認されるために必要な項目が表示され、あなたのテーマに不足している可能性のある推奨項目も表示されます。

<!-- 
### Developer
 -->

### Developer

<!-- 
The [Developer](https://wordpress.org/plugins/developer/) plugin is really just a tool to automatically download and install some of the plugins you’ll want when developing your theme. Some of the ones discussed in this handbook will already be installed and active. Others you can install as soon as you activate the plugin.
 -->

[Developer](https://wordpress.org/plugins/developer/) プラグインは、あなたのテーマ開発時に必要となるプラグインの一部を自動的にダウンロードしてインストールするための、ツールに過ぎません。本ハンドブックで取り上げるプラグインの一部は、すでにインストールされ有効化されていることでしょう。その他のプラグインは、このプラグインを有効化するとすぐにインストールできます。

<!-- 
### Debug Bar
 -->

### Debug Bar

<!-- 
[Debug Bar](https://wordpress.org/plugins/debug-bar/) pushes all debug messages to a separate page where they are listed in an easy-to-read layout and organized by type of message. There are also a number of [other plugins](https://wordpress.org/plugins/search.php?q=debug+bar) that add on to Debug Bar, extending its features or adding more information.
 -->

[Debug Bar](https://wordpress.org/plugins/debug-bar/) は、すべてのデバッグメッセージを別のページに表示し、そこではメッセージが読み易いレイアウトで一覧表示され、メッセージの種類ごとに整理されます。また、Debug Bar に機能追加や情報提供する [他のプラグイン](https://wordpress.org/plugins/search.php?q=debug+bar) も多数存在します。

<!-- 
### Log Deprecated Notices
 -->

### Log Deprecated Notices

<!-- 
[Log Deprecated Notices](https://wordpress.org/plugins/log-deprecated-notices/) displays a list of the deprecated function notices in your theme and where the code can be found. This should be run, at minimum, after every major release of WordPress, so you can resolve and remove any deprecated code and functions from your theme.
 -->

[Log Deprecated Notices](https://wordpress.org/plugins/log-deprecated-notices/) は、あなたのテーマ内の非推奨関数に関する通知と、そのコードが存在する場所の一覧を表示します。これは、少なくとも、WordPress のメジャーリリースごとに実行すべきで、これにより、あなたのテーマから非推奨のコードや関数を解決・削除できます。

<!-- 
### Browser testing
 -->

### ブラウザー・テスト

<!-- 
When submitting your theme to WordPress.org, it’s expected that it works well in modern browsers and at any resolution. You should test your theme against a number of popular browsers before submitting, both mobile and desktop. Many browsers have built-in features making it easy to test, for example the [Chrome Developer Tools](https://developer.chrome.com/devtools), [Firefox Developer Tools](https://developer.mozilla.org/en-US/docs/Tools), and the [Microsoft Edge tools](http://dev.modern.ie). Note that [Internet Explorer is no longer supported by WordPress](https://make.wordpress.org/core/2021/04/22/ie-11-support-phase-out-plan/) since 5.8 release.
 -->

WordPress.org にあなたのテーマを提出する際には、モダン・ブラウザーとあらゆる解像度で適切に動作することが求められます。提出前に、モバイルとデスクトップの両方を含む、複数の主要なブラウザーであなたのテーマをテストすべきです。多くのブラウザーにはテストを容易にする組込み能が備わっており、たとえば [Chrome Developer Tools](https://developer.chrome.com/devtools)、[Firefox Developer Tools](https://developer.mozilla.org/en-US/docs/Tools)、[Microsoft Edge ツール](http://dev.modern.ie) などが挙げられます。5.8リリース以降、[Internet Explorer は WordPress によってもはやサポートされていない](https://make.wordpress.org/core/2021/04/22/ie-11-support-phase-out-plan/) ことに注意してください。

<!-- 
### Validation
 -->

### バリデーション

<!-- 
Likewise, your theme should use valid HTML5 and CSS code. There are a variety of tools that will test your site for valid code, include [this HTML5 validator](http://html5.validator.nu/) and [this CSS validator](http://jigsaw.w3.org/css-validator/).
 -->

同様に、あなたのテーマは有効な HTML5および CSS コードを使用すべきです。あなたのサイトが有効なコードであるかどうかをテストするさまざまなツールがあり、[この HTML5 バリデーター](http://html5.validator.nu/) や [この CSS バリデーター](http://jigsaw.w3.org/css-validator/) などが含まれます。