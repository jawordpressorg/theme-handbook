<!-- 
# Testing
 -->

# テスト

<!-- 
Whether you are planning to share your WordPress theme with a broad audience or aiming for a specific platform, this article will help you get your theme ready for release. It focuses on general theme testing to ensure your theme’s quality and compatibility across various environments. 
 -->

あなたの WordPress テーマを幅広い読者と共有することを計画している場合でも、特定のプラットフォーム向けにする場合でも、本稿は、あなたのテーマをリリース準備するのに役立ちます。あなたのテーマの品質とさまざまな環境での互換性を保証するための一般的なテーマのテストに焦点を当てています。

<!-- 
Expanding on the principles from previous sections, this article covers things like code quality, compatibility, and responsiveness. By the end, your theme will be ready to use on a live site.
 -->

前セクションの原則を発展させ、本稿では、コード品質、互換性、レスポンシブ性などについて説明します。最後には、あなたのテーマが本番サイトで使えます。

<!-- 
## Testing environment
 -->

## テスト環境

<!-- 
When building your theme, it is good practice to test from within some type of development environment. In this section, you will get an overview of a couple of methods that you can explore further on your own.
 -->

あなたのテーマを構築する際に、何らかの開発環境の中でテストを実施することは、良い習慣です。本セクションでは、自身でさらに調べることができる、いくつかの方法の概要を知ることができます。

<!-- 
### Local environment
 -->

### ローカル環境

<!-- 
A local development environment provides a controlled space for developing and testing your theme without impacting your live site. Some of the available options are listed in the [Tools and Setup](https://developer.wordpress.org/themes/getting-started/tools-and-setup/) documentation.
 -->

ローカル開発環境は、あなたの本番サイトに影響を与えることなく、あなたのテーマを開発しテストするための制御された空間を提供します。利用可能な選択肢のいくつかは、[ツールとセットアップ](https://developer.wordpress.org/themes/getting-started/tools-and-setup/) ドキュメントにリストアップされています。

<!-- 
When developing locally, you should always have debugging enabled. Check out the [Debugging](https://developer.wordpress.org/advanced-administration/debug/debug-wordpress/) documentation for information on debugging techniques and tools that will help you handle errors and optimize your theme development process.
 -->

ローカルで開発する際には、常にデバッグを有効にしておくべきです。エラーを処理し、あなたのテーマ開発プロセスを最適化するのに役立つ、デバッグのテクニックやツールについては、[デバッグ](https://developer.wordpress.org/advanced-administration/debug/debug-wordpress/) ドキュメントをご覧ください。

<!-- 
### WordPress Playground
 -->

### WordPress Playground

<!-- 
[WordPress Playground](https://wordpress.org/playground/) is another option for testing. It operates entirely in the browser, providing a controlled space for testing.
 -->

[WordPress Playground](https://wordpress.org/playground/) は、テスト用のもう一つの選択肢です。これは完全にブラウザ上で動作し、テストのための制御された空間を提供します。

<!-- 
Here is a look at the default Twenty Twenty-Four theme running in Playground:
 -->

ここでは、Playground で動作しているデフォルト Twenty Twenty-Four テーマを見てみましょう:

<!-- 
[![Screenshot of a default setup on the WordPress Playground, showing the homepage of the Twenty Twenty-Four theme. There is a top bar for managing the setup.](https://i0.wp.com/developer.wordpress.org/files/2024/02/wordpress-playground.webp?resize=2048%2C1055&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/02/wordpress-playground.webp?ssl=1)
 -->

[![Twenty Twenty-Four テーマのホームページを表示している、WordPress Playground のデフォルトセットアップのスクリーンショット。セットアップを管理するためのトップバーがある。](https://i0.wp.com/developer.wordpress.org/files/2024/02/wordpress-playground.webp?resize=2048%2C1055&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/02/wordpress-playground.webp?ssl=1)

<!-- 
To become more familiar with using this platform, please refer to the official [WordPress Playground documentation](https://wordpress.github.io/wordpress-playground/).
 -->

このプラットフォームをより使いこなすために、公式 [WordPress Playground ドキュメント](https://wordpress.github.io/wordpress-playground/) をご覧ください。

<!-- 
## Theme Unit Test Data
 -->

## テーマ・ユニットテスト・データ

<!-- 
When developing a WordPress theme, ensuring that it can handle a variety of content is fundamental. To assist in this process, WordPress provides a set of [Theme Unit Test Data](https://github.com/WordPress/theme-test-data/blob/master/themeunittestdata.wordpress.xml) via an importable XML file. To be clear, this is just one part of a larger theme testing process.
 -->

WordPress テーマを開発する際、さまざまなコンテンツに対応できるようにすることは、基本です。このプロセスを支援するために、WordPress は、インポート可能な XML ファイル経由で、[「テーマ・ユニットテスト・データ」](https://github.com/WordPress/theme-test-data/blob/master/themeunittestdata.wordpress.xml) のセットを提供します。はっきりさせておきたいのは、これはより大きなテーマテストのプロセスの一部にすぎないということです。

<!-- 
The test data is a collection of posts, pages, comments, and media that you can import into your WordPress installation. By testing with this data, you can check how your theme handles edge cases, such as extremely long titles, images of varying sizes, nested comments, and a mix of HTML elements.
 -->

テストデータは、あなたの WordPress インストールにインポートできる投稿、ページ、コメント、メディアのコレクションです。このデータでテストすることで、極端に長いタイトル、さまざまなサイズの画像、ネストされたコメント、HTML 要素の混在など、特殊なケースをテーマがどのように扱うかを確認できます。

<!-- 
To test your theme with the Theme Unit Test Data, you need to:
 -->

「テーマ・ユニットテスト・データ」を使ってあなたのテーマをテストするには、以下のことが必要です:

<!-- 
*   **Download the data:** Get the latest version from the [GitHub repository](https://github.com/WordPress/theme-test-data/blob/master/themeunittestdata.wordpress.xml).
*   **Import the data:** Use the [WordPress Importer](https://wordpress.org/plugins/wordpress-importer/) tool to import the data into your WordPress environment.
 -->

*   **データのダウンロード:** [GitHub リポジトリー](https://github.com/WordPress/theme-test-data/blob/master/themeunittestdata.wordpress.xml) から、最新版を入手します。
*   **データのインポート:** [WordPress インポーター](https://wordpress.org/plugins/wordpress-importer/) ツールを使用して、あなたの WordPress 環境にデータをインポートします。

<!-- 
Once you’ve imported the content into your test install, examine how each piece of content is displayed. Pay special attention to areas where your theme might be prone to issues. Also be sure to view your theme on various devices and screen sizes to make sure the content is displayed as expected.
 -->

コンテンツをあなたのテスト・インストールにインポートしたら、各コンテンツがどのように表示されるかを検証します。あなたのテーマに問題がありそうな部分には、特に注意を払ってください。また、さまざまなデバイスや画面サイズであなたのテーマを表示し、コンテンツが期待通りに表示されていることを確認してください。

<!-- 
## Tools and resources
 -->

## ツールとリソース

<!-- 
When testing your theme, it is important to use tools that will check every aspect of your theme for potential issues. 
 -->

あなたのテーマをテストする際には、あなたのテーマのあらゆる面に、潜在的な問題がないかチェックするツールを使うことが重要です。

<!-- 
The [Theme Check Plugin](https://wordpress.org/plugins/theme-check/) evaluates your theme against the [Theme Review Guidelines](https://make.wordpress.org/themes/handbook/review/required/) before submitting to the official directory. Even if not submitting to the directory, it can also be useful for making sure your theme meets some baseline standards.
 -->

[Theme Check Plugin](https://wordpress.org/plugins/theme-check/) は、公式ディレクトリに提出する前に、あなたのテーマを [テーマレビュー・ガイドライン](https://make.wordpress.org/themes/handbook/review/required/) に照らして評価します。ディレクトリに提出しない場合でも、あなたのテーマがいくつかの基本基準を満たしていることを確認するのにも役立ちます。

<!-- 
Some other WordPress plugins you should include in your testing suite are:
 -->

テスト・スイートに含めるべき WordPress プラグインは、他にもいくつかあります:

<!-- 
*   [Debug Bar](https://wordpress.org/plugins/debug-bar/): Adds an admin bar to your WordPress admin and provides a central location for debugging.
*   [Query Monitor](https://wordpress.org/plugins/query-monitor/): Allows debugging of database queries, API requests, and AJAX used to generate theme pages and functionality.
*   [Log Deprecated Notices](https://wordpress.org/plugins/log-deprecated-notices/): Logs incorrect function usage, deprecated file usage, and deprecated function usage in your theme.
*   [Monster Widget](https://wordpress.org/plugins/monster-widget/): Consolidates the core WordPress widgets into a single widget, making it easier to test them all at once (*classic themes only*).
 -->

*   [Debug Bar](https://wordpress.org/plugins/debug-bar/): あなたの WordPress 管理画面に管理バーを追加し、デバッグのための中心的な場所を提供します。
*   [Query Monitor](https://wordpress.org/plugins/query-monitor/): データベース・クエリー、API リクエスト、テーマページや機能の生成に使用される AJAX のデバッグを可能にします。
*   [Log Deprecated Notices](https://wordpress.org/plugins/log-deprecated-notices/): あなたのテーマの間違った関数の使い方、非推奨のファイルの使い方、非推奨の関数の使い方をログに記録します。
*   [Monster Widget](https://wordpress.org/plugins/monster-widget/): コア WordPress ウィジェットを単一のウィジェットに統合し、一度にすべてのウィジェットをテストしやすくします (*クラシック・テーマのみ*)。

<!-- 
For effective cross-browser compatibility testing of block themes, it is important to use the developer tools available with modern browsers, such as:
 -->

ブロック・テーマの効果的なクロスブラウザー互換性テストには、モダンブラウザーで利用可能な開発者ツールを使用することが重要です、たとえば:

<!-- 
*   [Firefox: Developer Edition](https://www.mozilla.org/firefox/developer/)
*   [Chrome DevTools](https://developer.chrome.com/docs/devtools)
 -->

*   [Firefox: 開発者版](https://www.mozilla.org/firefox/developer/)
*   [Chrome DevTools](https://developer.chrome.com/docs/devtools)

<!-- 
## Functional testing
 -->

## 機能テスト

<!-- 
Testing your theme’s compatibility with basic WordPress features is necessary. This step ensures that your theme not only looks good but also works with WordPress’s core functionality.
 -->

基本 WordPress の機能で、あなたのテーマの互換性をテストすることが必要です。このステップでは、あなたのテーマが見た目が良いだけでなく、WordPress のコア機能で動作することを保証します。

<!-- 
### Testing basic WordPress features
 -->

### 基本 WordPress 機能のテスト

<!-- 
It is important that your theme works with core features and behaves as expected. The following are some of the basic features to test:
 -->

あなたのテーマがコア機能と連動し、期待通りに動作することが重要です。以下はテストすべき基本的な機能の一部です:

<!-- 
*   **Posts and pages:**
    *   Create a variety of posts and pages using the block editor. Experiment with different types of content, including text, images, and videos.
    *   Pay attention to how all standard blocks (paragraphs, images, headings, lists, etc.) are displayed. Are they aligning correctly? Is the spacing consistent?
*   **Block settings:**
    *   Test the settings of each block to ensure they function as intended. For instance, when you change the alignment of an image or the color of a heading, does the theme reflect these changes accurately?
*   **Responsiveness:**
    *   Check how these elements adapt to different screen sizes. Ensure the layout remains intuitive and user-friendly on mobile devices.
*   **Comments:**
    *   Look at the comments section of your posts. Are comments and replies displaying correctly?
    *   Ensure that threaded comments are displayed in a nested format, making it easy to follow conversations.
    *   Test the comment block in the block editor. Does it integrate well with your theme? Are there styling or functionality issues?
 -->

*   **投稿とページ:**
    *   ブロック・エディターを使って、さまざまな投稿やページを作成しましょう。テキスト、画像、動画など、さまざまなタイプのコンテンツを試してみましょう。
    *   すべての標準ブロック (段落、画像、見出し、リスト、等) がどのように表示されているかに注意を払いましょう。正しく配置されていますか ? 間隔は一定ですか ?
*   **ブロック設定:**
    *   各ブロックの設定をテストし、意図したとおりに機能することを確認しましょう。たとえば、画像の配置や見出しの色を変更した際には、その変更がテーマに正確に反映されますか ?
*   **レスポンシブ性:**
    *   これらの要素が、異なる画面サイズにどのように適応するかをチェックしましょう。レイアウトが、モバイル・デバイスでも、直感的でユーザー・フレンドリーであることを確認しましょう。
*   **コメント:**
    *   あなたの投稿のコメント欄を見てみましょう。コメントや返信は正しく表示されていますか ?
    *   スレッド化されたコメントが、ネストされたフォーマットで表示されるようにし、会話を追いやすくしましょう。
    *   ブロック・エディターで、「コメント」ブロックをテストしましょう。あなたのテーマとうまく統合されていますか ? スタイルや機能に、課題はありませんか ?

<!-- 
If you’re building a block theme, as this handbook recommends, you should also test these features:
 -->

本ハンドブックが推奨しているように、ブロック・テーマを作成する際には、これらの機能もテストする必要があります:

<!-- 
*   **Site Editor:** Test the Site Editor and make sure that you can edit templates and template parts like headers and footers.
*   **Styles interface:** Check the functionality of the Styles interface, where you can customize colors, typography, and layout settings that apply across your theme.
*   **Navigation block:** Pay special attention to the Navigation block. Test its responsiveness, the ease of adding menu items, sub-menu functionality, and alignment options.
*   **Template editing:** Explore the Template Editor for creating and modifying templates for specific posts or pages.
 -->

*   **「サイト・エディター」:**「サイト・エディター」をテストし、ヘッダーやフッターのようなテンプレートやテンプレートパーツを編集できることを確認しましょう。
*   **「スタイル」インターフェイス:** あなたのテーマ全体に適用される色、タイポグラフィ、レイアウト設定をカスタマイズできる、「スタイル」インターフェイスの機能を確認しましょう。
*   **「ナビゲーション」ブロック:**「ナビゲーション」ブロックには特に注意を払いましょう。レスポンシブ性、メニュー項目の追加しやすさ、サブメニューの機能性、整列オプションなどをテストしましょう。
*   **テンプレート編集:** 特定の投稿やページのテンプレートを制作・修正するための「テンプレート・エディター」を調べましょう。

<!-- 
## Accessibility testing
 -->

## アクセシビリティ・テスト

<!-- 
Ensuring accessibility is a key aspect of responsible theme development.
 -->

アクセシビリティの確保は、責任あるテーマ開発の重要な側面です。

<!-- 
You should strive to make sure your theme meets the [WordPress Accessibility Guidelines](https://make.wordpress.org/accessibility/handbook/). This includes aspects like keyboard navigation, screen reader compatibility, and proper use of ARIA roles.
 -->

あなたのテーマが [WordPress アクセシビリティ・ガイドライン](https://make.wordpress.org/accessibility/handbook/) に適合していることを確認するよう、努める必要があります。これには、キーボード・ナビゲーション、スクリーン・リーダーとの互換性、ARIA ロールの適切な使用などの側面が含まれます。

<!-- 
Tools like [aXe](https://www.deque.com/axe/) and [WAVE](https://wave.webaim.org/) are invaluable in identifying potential accessibility issues. Regularly use them during development to find and fix any problems. This proactive approach helps in creating a theme that is accessible to all users, regardless of how they navigate the web.
 -->

[aXe](https://www.deque.com/axe/) や [WAVE](https://wave.webaim.org/) のようなツールは、潜在的なアクセシビリティの課題を特定するうえで、非常に貴重です。開発中に定期的に使用し、問題を発見して修正しましょう。この積極的なアプローチは、Web をどのようにナビゲートするかに関係なく、すべてのユーザーがアクセスしやすいテーマ作りに役立ちます。

<!-- 
## Performance testing
 -->

## 性能テスト

<!-- 
You should also ensure that your theme is not unnecessarily loading too many resources. For this, you can use tools like [PageSpeed Insights](https://pagespeed.web.dev/) to check your theme’s performance. These types of tools provide information on how quickly your theme loads and offers suggestions for improvement.
 -->

また、あなたのテーマが不必要に多くのリソースをロードしていないことを確認する必要があります。このため、[PageSpeed Insights](https://pagespeed.web.dev/) のようなツールを使って、あなたのテーマのパフォーマンスをチェックできます。この種のツールは、あなたのテーマがどのくらい速くロードされるかについての情報を提供し、改善のための提案を提供します。

<!-- 
When shipping media or other assets with your theme, be sure that they are optimized. This includes but is not limited to:
 -->

メディアやその他のアセットをあなたのテーマと一緒に同梱する際には、それらが最適化されていることを確認してください。これには以下が含まれますが、これらに限定されません:

<!-- 
*   **Images/Media:** Ensure media items bundled with your theme are correctly sized, in the most appropriate format, and compressed to reduce load times.
*   **CSS and JavaScript files:** Make sure to include minified assets that will be loaded by the browser.
 -->

*   **画像/メディア:** あなたのテーマにバンドルされているメディア・アイテムが、正しいサイズで、最適なフォーマットで、ロード時間を短縮するために圧縮されていることを確認しましょう。
*   **CSS ファイルおよび JavaScript ファイル:** ブラウザでロードされる、最小化されたアセットを必ず含めましょう。