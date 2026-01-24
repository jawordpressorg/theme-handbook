<!-- 
# Template Files Section
 -->

# テンプレート・ファイル・セクション

<!-- 
We introduced [template files](https://developer.wordpress.org/themes/basics/template-files/) earlier in the handbook.  This next section is going to break up the different template files through the [post types](https://developer.wordpress.org/themes/basics/post-types/) that they display and provide a more in depth explanation of the purpose for these template files.  You’ll also get a handle on some practical use cases for the different template files.
 -->

ハンドブックの前半で、[テンプレート・ファイル](https://developer.wordpress.org/themes/basics/template-files/) について紹介しました。次のセクションでは、表示する [投稿タイプ](https://developer.wordpress.org/themes/basics/post-types/) ごとに異なるテンプレート・ファイルを分けて説明し、これらのテンプレート・ファイルの目的について、より詳細に解説します。また、各種テンプレート・ファイルの実用的なユースケースについても、理解を深めていただけます。

<!-- 
You’ll start with [post template files](https://developer.wordpress.org/themes/template-files-section/post-template-files/) that deal with displaying the Post post type.  Then you’ll look at [page template files](https://developer.wordpress.org/themes/template-files-section/page-template-files/) that display the Page post type and drill down into [specific page templates](https://developer.wordpress.org/themes/template-files-section/page-template-files/page-templates/) that WordPress has built in to its functionality.  Next you’ll learn about [attachment template files](https://developer.wordpress.org/themes/template-files-section/attachment-template-files/) which display the attachment post type.  You’ll also learn about how to display custom post types that are built by a plugin in the [custom post type templates](https://developer.wordpress.org/themes/template-files-section/custom-post-type-template-files/).  Lastly, you’ll touch on some [partial and miscellaneous template files](https://developer.wordpress.org/themes/template-files-section/partial-and-miscellaneous-template-files/) which are important to include but don’t necessarily display post types.
 -->

まず、投稿タイプ「投稿」を表示する、[投稿テンプレート・ファイル](https://developer.wordpress.org/themes/template-files-section/post-template-files/) から始めます。続いて、投稿タイプ「ページ」を表示する、[ページ・テンプレート・ファイル](https://developer.wordpress.org/themes/template-files-section/page-template-files/) を確認し、WordPress が、その機能にビルトインしている [特定のページ・テンプレート](https://developer.wordpress.org/themes/template-files-section/page-template-files/page-templates/) について掘り下げてみましょう。続いて、投稿タイプ「添付ファイル」を表示する、[添付テンプレート・ファイル](https://developer.wordpress.org/themes/template-files-section/attachment-template-files/) について学びます。また、プラグインによって構築されたカスタム投稿タイプを [カスタム投稿タイプ・テンプレート](https://developer.wordpress.org/themes/template-files-section/custom-post-type-template-files/) で表示する方法についても、学びます。最後に、[パーシャル・テンプレート・ファイルと、その他のテンプレート・ファイル](https://developer.wordpress.org/themes/template-files-section/partial-and-miscellaneous-template-files/) について触れることになりますが、これらは重要なインクルード対象でありながら、投稿タイプを必ずしも表示するわけではありません。

<!-- 
 It’s important to understand WordPress doesn’t really break down template files down into specific types of template files such as post template files or attachment template files. Especially since many template files, such as `index.php` or `search.php` can display many different post types. To help you reference specific template files this handbook is categorizing them based on the post types they can display.
 -->

WordPress は、投稿テンプレート・ファイルや添付テンプレート・ファイルといった、特定の種類のテンプレート・ファイルに、テンプレート・ファイルを実際に分類していないことを、理解することが重要です。特に、`index.php` や `search.php` などの多くのテンプレート・ファイルは、さまざまな投稿タイプを表示できるためです。特定のテンプレート・ファイルを参照しやすくするため、本ハンドブックでは、表示可能な投稿タイプにもとづいて、それらを分類しています。