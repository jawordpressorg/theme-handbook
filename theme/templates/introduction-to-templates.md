<!-- 
# Introduction to Templates
 -->

# テンプレート入門

<!-- 
Like nearly all content management systems, WordPress uses a templating system to handle the output of content on the front end of a website. In modern block themes, templates are HTML files with [block markup](https://developer.wordpress.org/block-editor/explanations/architecture/key-concepts/).
 -->

ほぼすべてのコンテンツ管理システムと同様に、WordPress は Web サイトのフロントエンドで、コンテンツの出力を処理するためにテンプレート・システムを使用しています。最新のブロック・テーマでは、テンプレートは [ブロック・マークアップ](https://developer.wordpress.org/block-editor/explanations/architecture/key-concepts/) を備えた HTML ファイルです。

<!-- 
In this document, you will learn how the templating system in WordPress works. After that, you can jump ahead to the more detailed [Templates](https://developer.wordpress.org/themes/templates/templates/) and [Template Parts](https://developer.wordpress.org/themes/templates/template-parts/) documentation.
 -->

本ドキュメントでは、WordPress のテンプレート・システムのしくみを学びます。その後、より詳細な [テンプレート](https://developer.wordpress.org/themes/templates/templates/) や [テンプレート・パーツ](https://developer.wordpress.org/themes/templates/template-parts/) ドキュメントに進んでください。

<!-- 
## What are templates?
 -->

## テンプレートって ?

<!-- 
In a nutshell, templates take dynamic data and wrap it into structured HTML markup, which is then sent to the browser. It is not a particularly revolutionary concept, and it is one that nearly every website system with dynamic data uses.
 -->

一言で言えば、テンプレートは動的データを構造化された HTML マークアップに包み込み、ブラウザーに送信します。これは特に画期的な概念ではなく、動的データを扱うほぼすべての Web サイト・システムが使用しているものです。

<!-- 
 The templating system in WordPress does a few important things:
 -->

WordPress のテンプレート・システムは、いくつかの重要なことを行います:

<!-- 
*   Parses block markup, which is used to reference static and dynamic data.
*   Retrieves dynamic data (e.g., post content, site options, etc.) from the database.
*   Sends the resulting HTML to the visitor’s browser.
 -->

*   静的データと動的データを参照するために用いられる、ブロック・マークアップを解析します。
*   データベースから動的データ (例: 投稿内容、サイト・オプション、など) を取得します。
*   訪問者のブラウザーに、結果の HTML を送信します。

<!-- 
The major difference between WordPress and most other platforms is the inclusion of block markup. Block theme templates are made entirely of blocks, which can both represent static or dynamic data. The WordPress templating system parses these blocks to ensure they output the correct content when it is sent to the visitor’s browser.
 -->

WordPress と他のほとんどのプラットフォームとの大きな違いは、ブロック・マークアップが含まれていることです。ブロック・テーマのテンプレートは、静的データまたは動的データの両方を表現できるブロックで完全に作られています。WordPress のテンプレート・システムは、これらのブロックを解析し、訪問者のブラウザーに送信されたときに正しいコンテンツが出力されるようにします。

<!-- 
Another thing that WordPress does well is provide a visual interface to build or customize templates directly from the admin:
 -->

WordPress が優れているもう一つの点は、管理画面から直接テンプレートの構築やカスタマイズができるビジュアル・インターフェイスを提供していることです:

<!-- 
[![WordPress Site Editor with the Templates section open, showing the site's homepage.](https://i0.wp.com/developer.wordpress.org/files/2023/10/templates-interface.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/templates-interface.jpg?ssl=1)
 -->

[![WordPress サイトエディターでテンプレート・セクションを開き、サイトのトップページを表示。](https://i0.wp.com/developer.wordpress.org/files/2023/10/templates-interface.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/templates-interface.jpg?ssl=1)

<!-- 
The Site Editor also lets your theme’s users overwrite your block templates and parts from within the administration interface. Any changes that users make are saved in their site’s database. These customizations are stored the same way in the database as they are in template files: as block markup.
 -->

また、サイトエディターでは、テーマのユーザーが管理インターフェイス内から、あなたのブロック・テンプレートやパーツを上書きできます。ユーザーが加えた変更は、すべてサイトのデータベースに保存されます。これらのカスタマイズはテンプレート・ファイルと同じようにデータベースに保存されます: ブロック・マークアップとして。

<!-- 
### Templates vs. plain HTML
 -->

### テンプレート vs プレーン HTML

<!-- 
If you’ve already learned some basic HTML, you’ve probably built out a webpage or two. But it can be very hard to build out a full website with HTML because you must constantly update every file anytime you make a global change across the entire site.
 -->

基本的な HTML を学んだことがある人なら、Web ページの1つや2つは作ったことがあるでしょう。しかし、HTML で完全な Web サイトを構築するのは非常に難しいことです。なぜなら、サイト全体にグローバルな変更を加えるときはいつでも、すべてのファイルを常に更新しなければならないからです。

<!-- 
This is because HTML is a document language. It does not know how to handle dynamic data, nor can it be used to dynamically load reusable pieces of code.
 -->

なぜなら、HTML は文書言語だからです。動的データの扱い方を知らないし、再利用可能なコードを動的にロードするためにも使用できません。

<!-- 
Technically, block templates are `.html` files. However, they contain specialized block markup that is parsed by WordPress’ templating system, which is built in PHP (on the front end) and JavaScript (in the editor). Using this system, blocks can be dynamic, despite existing within `.html` files.
 -->

技術的には、ブロック・テンプレートは `.html` ファイルです。しかし、ブロック・テンプレートは、PHP (フロントエンド側) と JavaScript (エディター側) で構築された WordPress のテンプレート・システムによって解析される、特殊なブロック・マークアップを含んでいます。このシステムを使うことで、ブロックは `.html` ファイルの中に存在するにもかかわらず、動的なものになります。

<!-- 
#### Dynamic data
 -->

#### 動的データ

<!-- 
The major difference between a template and writing plain HTML files is that templates have the ability to insert dynamic data. Let’s look at an example of what this would look like if you were building your website from scratch and not using a CMS like WordPress.
 -->

テンプレートとプレーンな HTML ファイルを書くことの大きな違いは、テンプレートには動的なデータを挿入する機能があることです。もしあなたが WordPress のような CMS を使わず、ゼロから Web サイトを構築する場合、これがどのようなものか、例を見てみましょう。

<!-- 
Suppose you wanted to output your site title in plain HTML. You would traditionally wrap it in an `<h1>` tag and manually type your site name:
 -->

サイトのタイトルをプレーンな HTML で出力したいとしましょう。従来は `<h1>` タグで囲み、手動でサイト名をタイプしていたでしょう:

<!-- 
```markup
<h1>Your Website Name</h1>
```
 -->

```markup
<h1>あなたの Web サイト名</h1>
```

<!-- 
With WordPress, you don’t need to know the correct HTML or the name of the site. Because a theme can be used on any WordPress site, the site title is dynamic data that will be different from one site to the next.
 -->

WordPress では、正しい HTML やサイト名を知る必要はありません。テーマは WordPress のどのサイトでも使用できるため、サイトのタイトルは、サイトごとに異なる動的なデータとなります。

<!-- 
To output the correct site title and its associated HTML in a block theme, you add the block markup instead:
 -->

ブロック・テーマで正しいサイト・タイトルとそれに関連する HTML を出力するには、代わりにブロック・マークアップを追加します:

```markup
<!-- wp:site-title /-->
```

<!-- 
By using the block markup, your theme will work anywhere WordPress is installed.
 -->

ブロック・マークアップを使用することで、WordPress がインストールされている環境であれば、どこでもあなたのテーマが動作します。

<!-- 
#### Reusability
 -->

#### 再利用性

<!-- 
One of the principles of good web design is DRY (Don’t Repeat Yourself). When building websites with plain HTML, you must recode all of that HTML for every single page of the site. 
 -->

優れた Web デザインの原則のひとつに DRY (Don't Repeat Yourself。繰り返しを避ける) 原則があります。プレーンな HTML で Web サイトを構築する場合、サイトの各ページごとに HTML をすべてコーディングし直す必要があります。

<!-- 
For example, most website headers and footers are exactly the same across every page of the site. So it doesn’t make sense to repeat that code for every page. A template system lets you write the code once and reuse it everywhere.
 -->

たとえば、ほとんどの Web サイトのヘッダーとフッターは、サイトのすべてのページでまったく同じです。そのため、すべてのページでそのコードを繰り返すのは、意味がありません。テンプレート・システムを使えば、一度書いたコードをあらゆる場所で再利用できます。

<!-- 
In WordPress, these smaller, reusable sections of a template are called template parts (or simply, parts).
 -->

WordPress では、テンプレートの小さな再利用可能なセクションを、テンプレート・パーツ (または単にパーツ) と呼びます。

<!-- 
If you were to create a template part named `header.html`, you could include it using the correct block markup in any template:
 -->

`header.html` という名前のテンプレート・パーツを作れば、どのテンプレートにも正しいブロック・マークアップを使ってそれを含めることができるでしょう:

```markup
<!-- wp:template-part {"slug":"header","tagName":"header"} /-->
```

<!-- 
This lets you reuse the header part in all of your templates, but you only need to create the `header.html` file once.
 -->

これにより、すべてのテンプレートでヘッダー部分を再利用できますが、`header.html` ファイルを制作するのは一度だけです。

<!-- 
## Block markup
 -->

## ブロック・マークアップ

<!-- 
Templates and template parts are files that are made entirely of block markup that represents individual blocks and their settings. WordPress parses this block markup and translates it to its final HTML markup, which can be understood by web browsers.
 -->

テンプレートとテンプレート・パーツは、個々のブロックとその設定を表現するブロック・マークアップのみで構成されるファイルです。WordPress はこのブロック・マークアップを解析し、Web ブラウザーが理解できる最終的な HTML マークアップに変換します。

<!-- 
Unlike [classic themes](https://developer.wordpress.org/themes/classic-themes/), WordPress automatically outputs some standard HTML elements for block themes.  This includes the wrapping `<html>` and `<body>` tags, `<head>`, and an outer `<div class="wp-site-blocks">`. WordPress and plugins also automatically output meta, styles, and scripts. In comparison to classic themes, block themes are not responsible for adding PHP hooks.
 -->

WordPress は、[クラシック・テーマ](https://developer.wordpress.org/themes/classic-themes/) とは異なり、ブロック・テーマ用にいくつかの標準的な HTML 要素を自動的に出力します。これには、`<html>` や `<body>` タグ、`<head>`、外側の `<div class="wp-site-blocks">` が含まれます。また、WordPress とプラグインは、メタ、スタイル、スクリプトを自動的に出力します。クラシック・テーマと比較して、ブロック・テーマは PHP フックを追加する責任はありません。

<!-- 
Block markup is technically valid HTML. WordPress uses a custom HTML comment syntax with a standardized format for the markup.
 -->

ブロック・マークアップは、技術的に妥当な HTML です。WordPress は、マークアップ用に標準化されたフォーマットの、カスタム HTML コメント構文を使用しています。

<!-- 
Let’s take a look at a fictional block’s markup in a template:
 -->

テンプレート内の架空のブロックのマークアップを、見てみましょう:

```markup
<!-- wp:namespace/slug {"align":"full"} /-->
```

<!-- 
As you can see, the code is wrapped with an opening `<!--` and closing `/-->` HTML comment tag. This tells WordPress to look for block markup. The markup can then be broken down into a four parts:
 -->

ご覧のように、コードは開始 `<!--` と終了 `/-->` HTML コメントタグで包まれています。これは WordPress にブロック・マークアップを探すように指示するものです。マークアップは4つの部分に分解できます:

<!-- 
*   **Prefix:** The `wp:` prefix tells WordPress that this is a block that needs to be parsed and not just an ordinary HTML comment. This is necessary for core and third-party blocks.
*   **Namespace:** The namespace for the block to parse.
*   **Slug:** The slug for the block to parse.
*   **Block Settings:** Valid JSON code that represents the block’s settings.
 -->

*   **接頭辞:** `wp:` 接頭辞は、WordPress に、これが解析が必要なブロックであり、普通の HTML コメントではないことを伝えます。これはコアのブロックやサードパーティーのブロックに必要です。
*   **名前空間:** 解析するブロック用の名前空間です。
*   **スラッグ:** 解析するブロック用のスラッグです。
*   **ブロック設定:** ブロックの設定を表現する妥当な JSON コードです。

<!-- 
When working with core WordPress blocks, you do not use the block namespace. For example, the `core/site-title` block doesn’t include the preceding `core/` when called:
 -->

WordPress のコアのブロックを扱う場合、ブロックの名前空間は使用しません。たとえば、`core/site-title` ブロックがコールされた際、直前の `core/` は含まれません:

```markup
<!-- wp:site-title /-->
```

<!-- 
References to third-party blocks must include the namespace.
 -->

サードパーティーのブロックへの参照には、名前空間を含める必要があります。

<!-- 
### How to create block markup
 -->

### ブロック・マークアップの制作方法

<!-- 
You could certainly learn to manually write all of the block markup for your theme by hand. But it can be tough to remember all of the possible block settings, and it is also easy to make an error, resulting in a broken website.
 -->

たしかに、テーマのブロック・マークアップをすべて手作業で記述することを学べるかもしれません。しかし、可能なブロック設定をすべて覚えるのは大変ですし、エラーを起こしやすく、結果として Web サイトが壊れてしまいます。

<!-- 
Instead, when building block templates, you will almost always want to build via the block editor and either save directly in the database or copy the block markup into your theme’s template files.
 -->

代わりに、ブロック・テンプレートを構築する場合、ほとんどの場合、ブロック・エディター経由で構築し、データベースに直接保存するか、ブロック・マークアップをテーマのテンプレート・ファイルにコピーします。

<!-- 
The easiest way to build an entire template is to do so via **Appearance > Editor > Templates** in the WordPress admin. Here is a look at the Twenty Twenty-Three’s **Home** template from that screen:
 -->

テンプレート全体を構築する最も簡単な方法は、WordPress 管理画面の **外観 > エディター > テンプレート** から行うことです。ここでは、その画面から Twenty Twenty-Three の **ホーム** テンプレートを見てみましょう:

<!-- 
[![Home template in the Site Editor, which shows a three-column grid of posts.](https://i0.wp.com/developer.wordpress.org/files/2023/10/templates-tt3-home.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/templates-tt3-home.jpg?ssl=1)
 -->

[![サイト・エディターの「ホーム」テンプレートでは、3列のグリッドで投稿が表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/templates-tt3-home.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/templates-tt3-home.jpg?ssl=1)

<!-- 
You can customize the template entirely using the visual Site Editor by adding, moving, or deleting blocks. You can also adjust individual block settings.
 -->

ビジュアルなサイト・エディターを使って、ブロックを追加、移動、削除することで、テンプレートを完全にカスタマイズできます。また、個々のブロックの設定も調整できます。

<!-- 
Once your template is designed just like you want, you click the **Options** button (**⋮** icon) in the toolbar and select the **Code Editor** option. This will give you the block markup for your template. From there, copy and paste it into your template file:
 -->

テンプレートが思い通りにデザインできたら、ツールバーの **オプション** ボタン (**⋮** アイコン) をクリックし、**コード・エディター** オプションを選択します。これでテンプレートのブロック・マークアップが得られます。これをコピーしてテンプレートファイルに貼り付けます:

<!-- 
[![Code view of the Home template code in the Site Editor.](https://i0.wp.com/developer.wordpress.org/files/2023/10/template-code-view.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/template-code-view.jpg?ssl=1)
 -->

[![サイト・エディターの「ホーム」テンプレートのコードビュー。](https://i0.wp.com/developer.wordpress.org/files/2023/10/template-code-view.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/template-code-view.jpg?ssl=1)

<!-- 
In the case of the Home template, you would paste the block markup in the `/templates/home.html` template of your theme.
 -->

「ホーム」テンプレートの場合、あなたのテーマの `/templates/home.html` テンプレートにブロック・マークアップをペーストします。

<!-- 
Of course, you only need to do this if you plan on distributing the theme to other people. If this is your own site, you can save the template from that screen, and it will be saved to the database, overwriting the `/templates/home.html` template file.
 -->

もちろん、これを行う必要があるのは、テーマを他の人に配布する予定がある場合だけです。独自サイトであれば、この画面からテンプレートを保存すれば、`/templates/home.html` テンプレートファイルを上書きしてデータベースに保存されます。

<!-- 
Another technique that some theme authors employ is to build from either the Post/Page Editor or Template Editor. Sometimes, they will create certain smaller sections to copy and paste directly into their templates or template parts.
 -->

テーマ作者が採用しているもう一つのテクニックは、投稿/ページ・エディターかテンプレート・エディターのどちらかで構築することです。時には、テンプレートやテンプレート・パーツに直接コピー & ペーストするために、特定の小さなセクションを制作することもあります。

<!-- 
To copy blocks from the Post Editor, select the blocks that you want to use and click the **Options** button (**⋮** icon) from the block-editing toolbar. Then click the **Copy** button from the dropdown:
 -->

投稿エディターからブロックをコピーするには、使用したいブロックを選択し、ブロック編集ツールバーの **オプション** ボタン (**⋮** アイコン) をクリックします。次に、ドロップダウンから **コピー** ボタンをクリックします:

<!-- 
[![WordPress post editor showing a row of buttons. A dropdown menu from the toolbar is open with the Copy command highlighted.](https://i0.wp.com/developer.wordpress.org/files/2023/10/copy-blocks.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/copy-blocks.jpg?ssl=1)
 -->

[![ボタンの並ぶ WordPress 投稿エディター。ツールバーからドロップダウン・メニューが開き、「コピー」コマンドがハイライトされている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/copy-blocks.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/copy-blocks.jpg?ssl=1)

<!-- 
From there, you can paste the copied code into your template or template part file. You can also switch to the **Code Editor** mode from this screen just like in the Site Editor and copy block markup in the same way.
 -->

そこから、コピーしたコードをあなたのテンプレートまたはテンプレート・パーツのファイルにペーストできます。また、サイト・エディターのように、この画面から **コード・エディター** モードに切り替えて、同じようにブロック・マークアップをコピーできます。

<!-- 
## The relationship between templates and parts
 -->

## テンプレートとパーツの関連性

<!-- 
Templates represent the overall HTML output that gets sent to the browser. An easy way to think of these is as “top-level templates” because they are the top, outermost level of the template system.
 -->

テンプレートは、ブラウザーに送信される HTML 出力全体を表現します。テンプレート・システムの最上位、一番外側のレベルですので、これらを「トップレベル・テンプレート」と考えるのは簡単な方法です。

<!-- 
Template parts are partial templates that live within top-level templates. Parts make it easy to include reusable sections without having to recreate the block markup for each of the templates.
 -->

テンプレート・パーツは、トップレベル・テンプレート内に存在する部分テンプレートです。パーツを使うことで、テンプレートごとにブロック・マークアップを再作成することなく、再利用可能なセクションを簡単に含めることができます。

<!-- 
In your theme, your templates and template parts will be located in the `/templates` and `/parts` folders, respectively. Here is example of what that structure may look like:
 -->

あなたのテーマでは、あなたのテンプレートとテンプレート・パーツは、それぞれ `/templates` と `/parts` フォルダーに配置されます。以下は、その構造がどのように見えるかの例です:

<!-- 
*   `parts/`
    *   `footer.html`
    *   `header.html`
*   `templates/`
    *   `404.html`
    *   `archive.html`
    *   `index.html` (required)
    *   `singular.html`
 -->

*   `parts/`
    *   `footer.html`
    *   `header.html`
*   `templates/`
    *   `404.html`
    *   `archive.html`
    *   `index.html` (必須)
    *   `singular.html`

<!-- 
Let’s look at an example of an archive template (`archive.html`) and its block markup:
 -->

「アーカイブ」テンプレート (`archive.html`) とそのブロック・マークアップの例を見てみましょう:

```markup
<!-- wp:template-part {"slug":"header","tagName":"header"} /-->

<!-- wp:group {"tagName":"main","layout":{"type":"constrained"}} -->
<main class="wp-block-group">
	<!-- wp:template-part {"slug":"loop","align":"full"} /-->
</main>
<!-- /wp:group -->

<!-- wp:template-part {"slug":"footer","tagName":"footer"} /-->
```

<!-- 
This template basically behaves as a wrapper that includes three template parts:
 -->

このテンプレートは、基本的に、3つのテンプレート・パーツを含むラッパーとして動作します:

*   `/parts/header.html`
*   `/parts/loop.html`
*   `/parts/footer.html`

<!-- 
This is not the technique that all block themes use, but it is a common practice. Whenever you have code that is repeated across multiple templates, it’s generally a good idea to copy that code into a template part file and include it in your top-level templates.
 -->

これはすべてのブロック・テーマが使っている手法ではありませんが、一般的な慣習です。複数のテンプレートで繰り返されるコードがある場合は、一般的に、そのコードをテンプレート・パーツのファイルにコピーして、トップレベル・テンプレートに含めることをおすすめします。

<!-- 
At this point, you’ve only been learning about templates at an overarching high level. Now it’s time to dive more deeply into the templating system and how each piece of it works. For your next steps, follow along with these docs:
 -->

この時点では、テンプレートについて包括的な高いレベルでしか学んでいません。次は、テンプレート・システムとその各部分がどのように機能するのかについて、より深く掘り下げる番です。次のステップでは、以下のドキュメントに従ってください:

<!-- 
*   [Templates](https://developer.wordpress.org/themes/templates/templates/)
*   [Template Parts](https://developer.wordpress.org/themes/templates/template-parts/)
 -->

*   [テンプレート](https://developer.wordpress.org/themes/templates/templates/)
*   [テンプレート・パーツ](https://developer.wordpress.org/themes/templates/template-parts/)