<!-- 
# Introduction to Patterns
 -->

# パターン入門

<!-- 
Block patterns (“patterns,” for short) are one of the most powerful features at a theme author’s disposal. Introduced in WordPress 5.4, patterns made it easier for users to insert more complex layouts from the block editor while opening a world of possibilities to designers.
 -->

ブロック・パターン (略して「パターン」) は、テーマ作者が自由裁量で使える最も強力な機能のひとつです。WordPress 5.4で導入されたパターンは、ブロック・エディターからより複雑なレイアウトを簡単に挿入できるようにし、同時にデザイナーの可能性を広げました。

<!-- 
This article provides an overarching definition of what patterns are and how they work. This will serve as a foundation as you read through the other articles in this chapter.
 -->

本稿では、パターンとは何か、パターンのしくみについて、包括的な定義を提供します。これは、本章の他の記事を読む際の基礎となります。

<!-- 
## What are patterns?
 -->

## パターンって ?

<!-- 
Essentially, a pattern is nothing more than one or more blocks that have been pre-configured and presented to the end-user. Think of them as reusable groups of blocks.
 -->

基本的に、パターンとは、あらかじめ構成され、エンドユーザーに提示された、1つ以上のブロックにほかなりません。再利用可能なブロックのグループと考えてください。

<!-- 
And that’s it. *Really.* Patterns are just groups of blocks.
 -->

それで終わりです。*本当に。* パターンは、単なるブロックの集まりです。

<!-- 
They are ideal as starting points for users to insert into their post and page content, but they are also useful when used inside of templates.
 -->

これらは、ユーザーが投稿やページのコンテンツに挿入するための出発点として理想的ですが、テンプレート内で使用する場合にも便利です。

<!-- 
Users can insert them directly into a template from the Site Editor or into their content from the Post Editor:
 -->

ユーザーは、サイト・エディターからテンプレートに直接挿入したり、投稿エディターからコンテンツに挿入できます:

<!-- 
[![WordPress editor with the Patterns inserter panel open. The Page sub-panel is open and shows a list of page patterns.](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-inserter.jpg?resize=2048%2C1019&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-inserter.jpg?ssl=1)
 -->

[![「パターン・インサーター」パネルを開いた WordPress エディター。「ページ」サブパネルが開き、ページ・パターンのリストが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-inserter.jpg?resize=2048%2C1019&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-inserter.jpg?ssl=1)

<!-- 
In comparison to template parts, which is a similar feature for reusable groups of blocks, patterns also give you access to PHP when you bundle them inside a theme. This means that you can internationalize text within them, dynamically add URLs to include images, and more. And you will learn more about these things throughout this chapter.
 -->

再利用可能なブロックのグループと同様の機能であるテンプレート・パーツと比較して、パターンもまた、テーマ内にバンドルする際に PHP へのアクセスを提供します。つまり、パターン内のテキストを国際化したり、画像を含む URL を動的に追加したり、その他いろいろなことができるのです。本章では、これらのことについて詳しく説明します。

<!-- 
Note that users can create and manage custom patterns from the **Appearance > Editor > Patterns** screen in the admin. You can also use this screen to manage your own patterns in your development install:
 -->

ユーザーは管理画面の **外観 > エディター > パターン** からカスタム・パターンを制作および管理できます。また、この画面を使用して、開発用のインストールで独自のパターンを管理できます:

<!-- 
[![Pattern library in the WordPress site editor, which shows a 4-column grid of all available patterns.](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-libary.jpg?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-libary.jpg?ssl=1)
 -->

[![WordPress サイト・エディターに、4カラムのグリッドで利用可能な全パターンを表示している、パターン・ライブラリ。](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-libary.jpg?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-libary.jpg?ssl=1)

<!-- 
If you are building a classic theme, this screen is unavailable. But, as of WordPress 6.5, you can access patterns through the **Appearance > Patterns** screen instead.
 -->

クラシック・テーマを構築している場合、この画面は利用できません。しかし、WordPress 6.5以降、代わりに **外観 > パターン** 画面からパターンにアクセスできるようになりました。

<!-- 
## Types of patterns
 -->

## パターンのタイプ

<!-- 
Essentially, there are two types of patterns:
 -->

基本的に、パターンには2つのタイプがあります:

<!-- 
*   **Synced:** Patterns that remain unchanged regardless of how many times or where it’s used on the website. These were formerly called “reusable blocks” in older versions of WordPress. *Note: these can only be created and managed from the WordPress admin.*
*   **Not synced:** Patterns that, when inserted via the Block Editor, create a new instance of the pattern’s blocks. Any changes made to the inserted blocks do not affect other uses of the pattern. Changes to the pattern in the future also do not affect prior uses of it.
 -->

*   **同期:** Web サイトのどこで何回使われても変化しない、というパターンです。WordPress の旧バージョンでは「再利用可能」ブロックと呼ばれていました。*注意: これらは WordPress の管理画面からしか、制作・管理できません。*
*   **非同期:** ブロック・エディター経由で挿入すると、該当ブロック・パターンの新規インスタンスが追加される、というパターンです。挿入されたブロックに加えられた変更は、パターンの他の利用には影響しません。また、将来そのパターンを変更しても、以前の利用には影響しません。

<!-- 
By the nature of how the pattern system works, all patterns registered by the theme are of the **Not synced** type. There is an [open ticket for syncing theme-registered patterns](https://github.com/WordPress/gutenberg/issues/59272), but it is not currently possible.
 -->

パターン・システムのしくみの性質上、テーマによって登録されたパターンはすべて **非同期** タイプです。[テーマ登録済みパターンの同期に関するチケットを開く](https://github.com/WordPress/gutenberg/issues/59272) もありますが、現在のところ不可能です。

<!-- 
## Managing patterns in the WordPress admin
 -->

## WordPress 管理画面でのパターン管理

<!-- 
Even when building a theme, you will often build patterns directly from the admin before bundling and registering them from within the theme itself. This can also be a good way to store and manage your patterns locally until you are satisfied that they are ready to include in your theme.
 -->

テーマの構築であっても、テーマ自体の中からパターンのバンドルおよび登録の前に、管理画面から直接パターンを構築することがよくあります。また、この方法は、テーマに含める準備が整うまで、パターンをローカルに保存・管理し、満足するまで使用するのに適しています。

<!-- 
It’s also good practice to get a feel for how users interact with patterns.
 -->

また、ユーザーのパターンへの接し方を知ることも、良い練習になるでしょう。

<!-- 
You can manage patterns by visiting the **Appearance > Editor** screen in your WordPress admin and clicking on the **Patterns** item in the sidebar.
 -->

あなたの WordPress 管理画面の **外観 > エディター** 画面にアクセスし、サイドバーの **パターン** 項目をクリックすると、パターンを管理できます。

<!-- 
### Creating custom patterns
 -->

### カスタム・パターンの制作

<!-- 
On the **Patterns** screen, you must click on the **Create pattern** button (**+** icon), which will give you a choice to create several options:
 -->

**パターン** 画面で、追加するための選択肢がいくつか表示される、**パターンを追加** ボタン (**+** アイコン) をクリックする必要があります:

<!-- 
*   Create pattern
*   Create template part
*   Import pattern from JSON
 -->

*   パターンを追加
*   テンプレート・パーツを追加
*   JSON からパターンをインポート

<!-- 
Select the **Create pattern** option, which will trigger an overlay modal that looks like this:
 -->

**パターンを追加** を選択すると、次のようなオーバーレイ・モーダルが表示されます:

<!-- 
[![WordPress pattern library with the "Create pattern" modal overlaying the screen. It has name, categories, and synced fields.](https://i0.wp.com/developer.wordpress.org/files/2024/04/create-pattern-modal.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/create-pattern-modal.webp?ssl=1)
 -->

[![「パターンを追加」モーダルが画面にオーバーレイ表示されている、WordPress パターン・ライブラリー。名称、カテゴリー、同期のフィールドがある。](https://i0.wp.com/developer.wordpress.org/files/2024/04/create-pattern-modal.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/create-pattern-modal.webp?ssl=1)

<!-- 
You’ll need to fill out three fields:
 -->

3つの項目を入力する必要があります:

<!-- 
*   **Name:** Decide on a name for the pattern you are creating.
*   **Categories:** Add one or more categories that your pattern will fit into.
*   **Synced:** Decide on whether your pattern should be synced. If you plan to ship this with your theme, you should toggle this option off just so that it behaves the same as it would coming from a theme.
 -->

*   **名称:** 制作するパターンの名称を決定します。
*   **カテゴリー:** あなたのパターンが当てはまるカテゴリーを1つ以上追加します。
*   **同期:** あなたのパターンを同期させるか否かを決定します。あなたのテーマと組み合わせるつもりなら、このオプションをオフに切り替えて、テーマから来るのと同じように動作するようにします。

<!-- 
Once you click the **Create** button, it will take you to the Pattern Editor. From there, it works just like any other Editor in WordPress. Add the blocks that you want to in your pattern and adjust their settings and styles to suit your needs.
 -->

**追加** ボタンをクリックすると、パターン・エディターに移動します。そこからは WordPress の他のエディターと同じように使えます。パターンに入れたいブロックを追加し、その設定やスタイルをニーズに合わせて調整してください。

<!-- 
Here is an example of a basic “Welcome Hero” pattern:
 -->

以下は、基本的な「Welcome Hero」パターンの例です:

<!-- 
[![WordPress pattern editor that shows a basic Cover block with a black background and white demo text in the content area.](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-editor.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-editor.webp?ssl=1)
 -->

[![コンテンツ・エリアに黒の背景と白のデモ・テキストを使った、基本的な「カバー」ブロックを表示している WordPress パターン・エディター。](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-editor.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-editor.webp?ssl=1)

<!-- 
Just be sure to hit the **Save** button. From there, you can use your pattern just like you’d use any other pattern on your site.
 -->

**保存** ボタンを必ずクリックしてください。そこから、あなたのサイトで他のパターンを使用するのと同じように、あなたのパターンを使用できます。

<!-- 
You can also view and edit any custom patterns you’ve created via the **Patterns > My Patterns** section in the sidebar:
 -->

また、サイドバーの **パターン > マイパターン** セクション経由で、作成したカスタム・パターンを表示したり編集できます:

<!-- 
[![WordPress pattern library with the "My patterns" sub-panel selected. It shows a single pattern that has been created by the user.](https://i0.wp.com/developer.wordpress.org/files/2024/04/my-patterns.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/my-patterns.webp?ssl=1)
 -->

[![「マイパターン」サブパネルを選択した WordPress パターン・ライブラリ。ユーザーが作成した1つのパターンが表示される。](https://i0.wp.com/developer.wordpress.org/files/2024/04/my-patterns.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/my-patterns.webp?ssl=1)

<!-- 
The **My Patterns** section is always where any user-created patterns will appear in the WordPress admin. They will also appear under the **All patterns** section and any other categories they were assigned to.
 -->

**マイパターン** セクションは、WordPress 管理画面でユーザー作成パターンが常に表示される場所です。また、**すべてのパターン** セクションや、その他割り当てられたカテゴリー以下にも表示されます。

<!-- 
### Copying a pattern to your theme
 -->

### パターンを、あなたのテーマにコピー

<!-- 
The Editor interface is a nice and easy method for creating patterns. But this is the Theme Handbook, so you’re probably wanting to know how to bundle this pattern that you’ve created with your theme.
 -->

「エディター」インターフェイスは、パターンを制作するための簡単で良い手段です。しかし、これはテーマ・ハンドブックですので、おそらく、作成したこのパターンをあなたのテーマにバンドルする方法を知りたいことでしょう。

<!-- 
For that, you need to copy the pattern code itself. You’ll learn what to do with pattern code in the [Registering Patterns](https://developer.wordpress.org/themes/patterns/registering-patterns/) article in this chapter.
 -->

それには、パターンコードそのものをコピーする必要があります。パターンコードで何をするかは、本章の [パターンの登録](https://developer.wordpress.org/themes/patterns/registering-patterns/) 記事で説明します。

<!-- 
There are a few different methods for copying pattern code. But the easiest way is to click the **Options** button (**⋮** icon) at the top of the editor and select the **Copy all blocks** option in the dropdown menu:
 -->

パターンコードをコピーする方法はいくつかあります。しかし最も簡単な方法は、エディター上部の **オプション** ボタン (**⋮** アイコン) をクリックし、ドロップダウン・メニューで **すべてのブロックを複製** オプションを選択することです:

<!-- 
[![WordPress pattern editor with a simple pattern of a Cover block with black background and white text shown in the content area. The editor options dropdown menu is shown with the "Copy all blocks" menu item highlighted.](https://i0.wp.com/developer.wordpress.org/files/2024/04/copy-pattern.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/copy-pattern.webp?ssl=1)
 -->

[![コンテンツ・エリアに黒の背景と白のテキストを使った、「カバー」ブロックのシンプルなパターンを表示している WordPress パターン・エディター。「すべてのブロックを複製」メニュー項目がハイライトされて表示されている、エディター・オプションのドロップダウン・メニュー。](https://i0.wp.com/developer.wordpress.org/files/2024/04/copy-pattern.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/copy-pattern.webp?ssl=1)

<!-- 
For the particular pattern shown in the screenshot, it will give you this block markup:
 -->

スクリーンショットに示した特定のパターンの場合、このようなブロック・マークアップが得られます:

```markup
<!-- wp:cover {"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull"><span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim-100 has-background-dim"></span><div class="wp-block-cover__inner-container"><!-- wp:group {"style":{"spacing":{"blockGap":"2.5rem"}},"layout":{"type":"constrained","wideSize":"%","contentSize":"75%"}} -->
<div class="wp-block-group"><!-- wp:heading {"textAlign":"center"} -->
<h2 class="wp-block-heading has-text-align-center">Welcome to My Site</h2>
<!-- /wp:heading -->

<!-- wp:paragraph {"align":"center"} -->
<p class="has-text-align-center">This is my little home away from home. Here, you will get to know me. I'll share my likes, hobbies, and more. Every now and then, I'll even have something interesting to say in a blog post.</p>
<!-- /wp:paragraph -->

<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
<div class="wp-block-buttons"><!-- wp:button {"className":"is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button">See My Popular Posts →︎</a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group --></div></div>
<!-- /wp:cover -->
```

<!-- 
In the [Registering Patterns](https://developer.wordpress.org/themes/patterns/registering-patterns/) documentation, you will learn how to take that block markup and bundle it as a pattern with your theme.
 -->

[パターンの登録](https://developer.wordpress.org/themes/patterns/registering-patterns/) ドキュメントでは、そのブロック・マークアップを受け取り、パターンとしてテーマにバンドルする方法を学びます。

<!-- 
## Managing theme-bundled patterns
 -->

## テーマ・バンドル・パターンの管理

<!-- 
There is currently no standard for theme authors to manage their patterns or port them directly to their theme without going through the process outlined above.
 -->

現在のところ、テーマ作者が上記のプロセスを経ずにパターンを管理したり、自身のテーマに直接移植したりするための標準はありません。

<!-- 
For the moment, it’s entirely up to you to decide how you want to integrate pattern management into your workflow. Some things to consider:
 -->

今のところ、パターン管理をあなたのワークフローにどのように組み込むかは、すべてあなたの決定次第です。考慮すべき点がいくつかあります:

<!-- 
*   You’ll need to manually copy and paste a pattern’s block markup from the admin UI to your theme.
*   If you need to make changes to a pattern’s block markup, there’s no way to keep the pattern in your theme and the version you built in the admin in sync.
 -->

*   パターンのブロック・マークアップを、管理 UI からあなたのテーマに手動でコピー & ペーストする必要があります。
*   パターンのブロック・マークアップを変更する必要がある場合、あなたのテーマ内のパターンと、管理画面で構築したバージョンを同期させる方法はありません。

<!-- 
These are certainly challenges that you’ll encounter when deciding the best method to use. There is an [open discussion](https://github.com/WordPress/create-block-theme/issues/287) for the official Create Block Theme plugin that would explore pattern management, and that is the best place to discuss with other theme authors the best path forward.
 -->

これらは、使用する最善の方法を決定する際に、たしかに遭遇する課題です。公式 Create Block Theme プラグインには、パターン管理を探求する [オープン・ディスカッション](https://github.com/WordPress/create-block-theme/issues/287) があり、そこは、他のテーマ作者と最善の道筋について議論するのに最適な場所です。