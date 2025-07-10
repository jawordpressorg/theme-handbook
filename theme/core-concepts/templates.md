<!-- 
# Templates
 -->

# テンプレート

<!-- 
In block themes, templates are made up of a collection of blocks. You might have a Site Logo block sitting next to a Navigation block in the header area. You might put Social Icons in the footer above a copyright notice.
 -->

ブロック・テーマでは、テンプレートはブロックの集合体で構成されています。ヘッダーエリアに「サイトロゴ」ブロックと「ナビゲーション」ブロックが並んでいる場合があります。著作権表示の上部、フッターに「ソーシャル・アイコン」を配置する場合もあります。

<!-- 
As you build out your own themes, you will get to decide how your templates come together. *That’s at least half the fun of theming!*
 -->

あなた独自のテーマを構築して行く中で、あなたのテンプレートがどのように組み合わさるかを決めることができます。*それがテーマ制作の楽しみの半分以上を占めるのです!*

<!-- 
In this document, you will learn the basic terminology around templating in WordPress. Reading through this quick primer on the subject will provide you with some foundational knowledge moving forward. There is a dedicated [Templates](https://developer.wordpress.org/themes/templates/) chapter that provides a full overview of working with templates.
 -->

このドキュメントでは、WordPress における、テンプレートに関する基本的な用語について学びます。その主題に関するこの簡易解説を読むことで、今後進むうえで必要な基礎知識を得ることができます。テンプレートの操作に関する概要を網羅した [テンプレート](https://developer.wordpress.org/themes/templates/) 章があります。

<!-- 
## What are templates?
 -->

## テンプレートとは ?

<!-- 
Theme templates represent the markup of the webpage. They create the document structure and print both static data (e.g., paragraph text) and dynamic data (e.g., post content) to the front end of your site.
 -->

テーマ・テンプレートは、Web ページのマークアップを表現します。これらはドキュメント構造を作成し、あなたのサイトのフロントエンドに静的データ (例: パラグラフ・テキスト) および動的データ (例: 投稿コンテンツ) を出力します。

<!-- 
Let’s take a look at a template from the default Twenty Twenty-Three theme.
 -->

デフォルトの Twenty Twenty-Three テーマのテンプレートを見てみましょう。

<!-- 
Go to **Appearance > Editor > Templates > Single Posts** in your WordPress admin. This will show you what a Single post template looks like:
 -->

WordPress の管理画面で **外観 > エディター > テンプレート > 個別投稿** に移動してください。これにより、「個別投稿」テンプレートの表示方法を確認できます:

<!-- 
[![WordPress Site Editor with a focus on the Single Post template.](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-single-template-editor.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-single-template-editor.jpg?ssl=1)
 -->

[![「個別投稿」テンプレートに焦点を当てた WordPress サイトエディター。](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-single-template-editor.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-single-template-editor.jpg?ssl=1)

<!-- 
Single post template of the default Twenty Twenty-Three theme.
 -->

デフォルトの Twenty Twenty-Three テーマの「個別投稿」テンプレート。

<!-- 
As shown above, the template is made up of various blocks. Some of them are in placeholder states and will dynamically display content based on what page is being viewed on the front end of the site.
 -->

上記の通り、テンプレートはさまざまなブロックで構成されています。その一部はプレースホルダー状態にあり、サイトのフロントエンドで表示されているページに応じて、動的にコンテンツを表示します。

<!-- 
If you select the **⋮ (Options)** button in the template editor and select the **Code editor** option, you will see the block markup of the template:
 -->

テンプレート・エディターで **⋮ (オプション)** ボタンを選択し、**コードエディター** オプションを選択すると、テンプレートのブロック・マークアップが表示されます:

<!-- 
[![WordPress site editor showing the Single Post template in code view, which shows the block markup.](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-single-template-code.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-single-template-code.jpg?ssl=1)
 -->

[![WordPress サイトエディターで、「個別投稿」テンプレートをコードビューで表示しているところ。ブロックのマークアップが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-single-template-code.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-single-template-code.jpg?ssl=1)

<!-- 
Code view of the default Twenty Twenty-Three theme’s single post template.
 -->

デフォルトの Twenty Twenty-Three テーマの「個別投稿」テンプレートのコード表示。

<!-- 
One of the great things about templating in WordPress is that you never really have to interact directly with template code. You have the visual Site Editor to make any and all customizations you want. But the code is there if you need it.
 -->

WordPress のテンプレート作成のすばらしい点の一つは、テンプレートコードを直接操作する必要がまったくないことです。ビジュアルなサイトエディターを使用して、必要なカスタマイズをすべて行うことができます。しかし、必要に応じてコードも利用できます。

<!-- 
Ultimately, the template produces HTML markup on the front end like this (shortened for clarity):
 -->

最終的に、テンプレートはフロントエンドで、次のような HTML マークアップを生成します (説明のため簡略化):

```markup
<!DOCTYPE html>
<html lang="en-US">
<head>
	<title>Post Title</title>
	<!-- Scripts, styles, and meta here. -->
</head>

<body class="post-template single single-post">
	<div class="wp-site-blocks">
		<header class="wp-block-template-part">
			<!-- Header blocks here. -->
		</header>
		<main class="wp-block-group is-layout-flow wp-block-group-is-layout-flow">
			<!-- Nested blocks here. -->
		</main>
		<footer class="wp-block-template-part">
			<!-- Footer blocks here. -->
		</footer>
	</div>
</body>
</html>
```

<!-- 
WordPress automatically handles the final markup for you, so all you need to do is create the templates.
 -->

WordPress は最終的なマークアップを自動的に処理するので、テンプレートを制作するだけで済みます。

<!-- 
## How the templating system works
 -->

## テンプレート・システムの動作原理

<!-- 
Whenever you visit a page on the front end of your website, WordPress must determine which template file to load. In the example above, the Single post template (`single.html`) is used to display the content of single blog posts.
 -->

Web サイトのフロントエンドのページにアクセスするたびに、WordPress はどのテンプレート・ファイルをロードするかを決定する必要があります。上記の例では、個別ブログ投稿のコンテンツを表示するために、「個別投稿」テンプレート (`single.html`) が使用されています。

<!-- 
But there are many other types of templates. For example, you might have a Page template (`page.html`) for displaying the content of your site’s pages or an Author template (`author.html`) for displaying post author archives.
 -->

しかし、他にも多くの種類のテンプレートが存在します。たとえば、サイトのページのコンテンツを表示するための「ページ」テンプレート (`page.html`) や、投稿者アーカイブを表示するための「投稿者」テンプレート (`author.html`) などがあります。

<!-- 
WordPress uses the template hierarchy to determine which template file to load. It is essentially a set of rules that defines which template to use based on the web page being viewed. If a template doesn’t exist, WordPress will continue looking down through the hierarchy until it finds one that does. 
 -->

WordPress は、テンプレート階層を使用して、ロードするテンプレートファイルを決定します。これは、基本的に、表示される Web ページにもとづいて、使用するテンプレートを定義する一連のルールです。テンプレートが存在しない場合、WordPress は、存在するテンプレートが見つかるまで、階層を下に向かって検索し続けます。

<!-- 
If no specific template is found, it will fall back to the Index template: `index.html`. As you learned in [Theme Structure](https://developer.wordpress.org/themes/core-concepts/theme-structure/), this is the minimum required template for a block theme to function.
 -->

特定のテンプレートが見つからない場合、「インデックス」テンプレートにフォールバックします: `index.html`。[テーマ構造](https://developer.wordpress.org/themes/core-concepts/theme-structure/) で学んだように、これはブロック・テーマが機能するために必要な、最小限のテンプレートです。

<!-- 
The [Templates](https://developer.wordpress.org/themes/templates/) chapter covers the hierarchy in full detail. There, you will learn which templates are loaded for each page of a WordPress site.
 -->

[テンプレート](https://developer.wordpress.org/themes/templates/) 章では、その階層について詳しく説明しています。そこでは、WordPress サイトの各ページにどのテンプレートがロードされるかを学ぶことができます。

<!-- 
### Template files
 -->

### テンプレート・ファイル

<!-- 
WordPress expects template files to be located under the `/templates` folder in your theme. A typical theme will have several templates, which would be organized like this:
 -->

WordPress は、テンプレート・ファイルが、あなたのテーマの `/templates` フォルダーの下にあることを想定しています。典型的なテーマには複数のテンプレートがあり、次のように編成されます:

<!-- 
*   `templates/`
    *   `404.html`
    *   `archive.html`
    *   `author.html`
    *   `index.html` (required)
    *   `page.html`
    *   `single.html`
    *   `search.html`
 -->

*   `templates/`
    *   `404.html`
    *   `archive.html`
    *   `author.html`
    *   `index.html` (必須)
    *   `page.html`
    *   `single.html`
    *   `search.html`

<!-- 
These are some of the common templates you will find a theme:
 -->

これらは、テーマでよく目にする一般的なテンプレートの一部です:

<!-- 
*   **`index.html`:** The fallback template file. It is required in all themes.
*   **`404.html`:** The 404 template is used when WordPress cannot find a post, page, or other content that matches the visitor’s request.
*   **`archive.html`:** The archive template is used when visitors request posts by archive-type views like category, author, or date and a more-specific template is unavailable.
*   **`author.html`:** The author page template is used whenever a visitor loads an author archive.
*   **`category.html`:** The category template is used when visitors request posts by category.
*   **`page.html`:** The page template is used when visitors request individual pages.
*   **`search.html`:** The search results template is used to display a visitor’s search results.
*   **`single.html`:**  The single post template is used when a visitor requests a single post.
*   **`tag.html`:** The tag template is used when visitors request posts by tag.
 -->

*   **`index.html`:** フォールバックのテンプレート・ファイル。すべてのテーマで必要です。
*   **`404.html`:** WordPress がビジターのリクエストに一致する投稿、ページ、その他のコンテンツを見つけられない場合、「404」テンプレートが使用されます。
*   **`archive.html`:** ビジターがカテゴリー、投稿者、日付などのアーカイブ形式の表示で投稿をリクエストし、より具体的なテンプレートが利用できない場合、「アーカイブ」テンプレートが使用されます。
*   **`author.html`:** ビジターが投稿者アーカイブをロードする際に、「投稿者ページ」テンプレートが使用されます。
*   **`category.html`:** ビジターがカテゴリー別の投稿をリクエストした際に、「カテゴリー」テンプレートが使用されます。
*   **`page.html`:** ビジターが個々のページをリクエストした際に、「ページ」テンプレートが使用されます。
*   **`search.html`:** 「検索結果」テンプレートは、ビジターの検索結果を表示するために使用されます。
*   **`single.html`:** ビジターが個別投稿をリクエストした際に、「個別投稿」テンプレートが使用されます。
*   **`tag.html`:** ビジターがタグで投稿をリクエストする際に、「タグ」テンプレートが使用されます。

<!-- 
This is not an exhaustive list. You will learn the ins and outs of every template file as you dive deeper into the [Templates](https://developer.wordpress.org/themes/templates/) chapter. The goal for now is to give you a baseline understanding of what to expect.
 -->

これは網羅的なリストではありません。[テンプレート](https://developer.wordpress.org/themes/templates/) 章を深く掘り下げていく中で、各テンプレート・ファイルの細部まで理解できます。現在の目標は、期待すべき基本的な理解を、あなたに提供することです。

<!-- 
## Template parts
 -->

## テンプレート・パーツ

<!-- 
Template parts, or “parts” for short, are another integral part of the templating system in WordPress. As the name suggests, template parts are a “part” of a template.
 -->

テンプレート・パーツ、略して「パーツ」は、WordPress のテンプレート・システムに不可欠なもうひとつの要素です。その名前が示すとおり、テンプレート・パーツは、テンプレートの「一部」です。

<!-- 
A template may consist of none, one, or more parts.
 -->

テンプレートは、0個、1個、または複数のパーツから構成される場合があります。

<!-- 
The great thing about parts is they help you follow the DRY (Don’t Repeat Yourself) principle. By including parts in your templates, you avoid having to repeat building the same block code over and over.
 -->

パーツのすばらしい点は、DRY (Don't Repeat Yourself。繰り返しを避ける) 原則に従うのに役立つことです。テンプレートにパーツを含めることで、同じブロックコードを繰り返し作成する必要がなくなります。

<!-- 
On most websites, there are sections of the page that typically stay the same, regardless of the page that you are viewing. *Can you think of any repeated sections that are common on websites?*
 -->

ほとんどの Web サイトでは、閲覧しているページに関係なく、ページの一部が常に同じままのセクションが存在します。*Web サイトでよく見られる、繰り返し登場するセクションを思いつきますか ?*

<!-- 
The site header and footer are likely the most recognizable “parts” of a webpage, and they just so happen to be the most common template parts you’ll find in themes. While it’s not required to include them, they are *de facto* standards.
 -->

サイトのヘッダーとフッターは、Web ページの最も認識しやすい「部分」であり、テーマで最もよく見られるテンプレート・パーツでもあります。これらを含める必要はありませんが、*事実上の* 標準となっています。

<!-- 
Go to **Appearance > Editor > Patterns > Template Parts** in your WordPress admin. Here is what the Header template part looks like from the default Twenty Twenty-Three theme:
 -->

WordPress 管理画面の **外観 > エディター > パターン > テンプレート・パーツ** に移動します。デフォルトの Twenty Twenty-Three テーマの「ヘッダー」テンプレート・パーツは、以下のようになっています:

<!-- 
[![WordPress Patterns library showing Header Template parts.](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-template-parts.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-template-parts.jpg?ssl=1)
 -->

[![「ヘッダー」テンプレート・パーツを表示する WordPress パターン・ライブラリ。](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-template-parts.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-template-parts.jpg?ssl=1)

<!-- 
Headers for the Twenty Twenty-Three theme.
 -->

Twenty Twenty-Three テーマ用のヘッダー。

<!-- 
WordPress looks for template parts in your theme’s `/parts` folder, which should be organized like this:
 -->

WordPress は、あなたのテーマの `/parts` フォルダー内でテンプレート・パーツを探します。このフォルダーは、次のように編成する必要があります:

<!-- 
*   `parts/`
    *   `header.html`
    *   `footer.html`
 -->

*   `parts/`
    *   `header.html`
    *   `footer.html`

<!-- 
Other common template parts are for the comments area and sidebars, but your theme can have as few or as many parts as you want. 
 -->

他の一般的なテンプレート・パーツには、コメントエリアやサイドバー用のものがありますが、テーマには必要な数だけパーツを自由に追加できます。

<!-- 
You’ll learn more about how to register and create custom parts in the [Template Parts](https://developer.wordpress.org/themes/templates/template-parts/) documentation.
 -->

[テンプレート・パーツ](https://developer.wordpress.org/themes/templates/template-parts/) ドキュメントで、カスタム・パーツの登録方法と制作方法について詳しく学ぶことができます。