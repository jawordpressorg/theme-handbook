<!-- 
# Taxonomy Templates
 -->

# タクソノミー・テンプレート

<!-- 
When a visitor clicks on a hyperlink to category, tag or custom taxonomy, WordPress displays a page of posts in reverse chronological order filtered by that taxonomy.
 -->

訪問者がカテゴリー、タグ、またはカスタム・タクソノミーへのハイパーリンクをクリックすると、WordPress は、そのタクソノミーでフィルタリングされた投稿を、新しい順に並べたページを表示します。

<!-- 
By default, this page is generated using the *index.php* template file. You can create optional template files to override and refine the *index.php* template files. This section explains how to use and create such templates.
 -->

デフォルトでは、本ページは、テンプレート・ファイル *`index.php`* を使用して生成されます。追加のテンプレート・ファイルを作成することで、*`index.php`* テンプレート・ファイルをオーバーライドし、改善できます。本セクションでは、そのようなテンプレートの使用方法と作成方法について説明します。

<!-- 
## Taxonomy Template Hierarchy
 -->

## タクソノミー・テンプレート階層

<!-- 
WordPress display posts in the order determined by the [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/ "Template Hierarchy").
 -->

WordPress は、[テンプレート階層](https://developer.wordpress.org/themes/basics/template-hierarchy/ "Template Hierarchy") で決定された順序で、投稿を表示します。

<!-- 
The *category.php*, *tag.php*, and *taxonomy.php* templates allow posts **filtered** by taxonomy to be treated differently from **unfiltered** posts or posts **filtered by a different taxonomy**. (Note: post refers to any post type – posts, pages, custom post types, etc.). These files let you target specific taxonomies or specific taxonomy terms. For example:
 -->

*`category.php`*、*`tag.php`*、*`taxonomy.php`* テンプレートを使用すると、タクソノミーで **フィルタリングされた** 投稿を、**フィルタリングされていない** 投稿や **別のタクソノミーでフィルタリングされた** 投稿とは異なる方法で、扱うことができます (注: 投稿とは、任意の投稿タイプ – 投稿、ページ、カスタム投稿タイプなど – を指す)。これらのファイルを使用すると、特定のタクソノミーまたは特定のタクソノミー・タームをターゲットにできます。たとえば:

<!-- 
*   *taxonomy-{taxonomy}-{term}.php*
*   *taxonomy-{taxonomy}.php*
*   *tag-{slug}.php*
*   *tag-{id}.php*
*   *category-{slug}.php*
*   *category-{ID}.php*
 -->

*   *`taxonomy-{taxonomy}-{term}.php`*
*   *`taxonomy-{taxonomy}.php`*
*   *`tag-{slug}.php`*
*   *`tag-{id}.php`*
*   *`category-{slug}.php`*
*   *`category-{ID}.php`*

<!-- 
So you could format all posts in an animal taxonomy named *news* on a page that looks different from posts filtered in other categories.
 -->

つまり、*news* と名付けられた `animal` タクソノミーに属するすべての投稿を、他のカテゴリーでフィルタリングされた投稿とは見た目が異なるページで、フォーマットできます。

<!-- 
The *archive.php* template provides the most general form of control, providing a layout for all archives; that is, a page that displays a list of posts.
 -->

*`archive.php`* テンプレートは、最も汎用的な制御形式を提供し、すべてのアーカイブ用のレイアウトを提供します; つまり、投稿の一覧を表示するページです。

<!-- 
### Category
 -->

### カテゴリー

<!-- 
For categories, WordPress looks for the *category-{slug}.php* file. If it doesn’t exist, WordPress then looks for a file for the next hierarchical level, *category-{ID}.php*, and so on. If WordPress fails to find any specialized templates or an *archive.php* template file, it reverts to the default behavior, using *index.php*.
 -->

カテゴリーの場合、WordPress は、*`category-{slug}.php`* ファイルを検索します。このファイルが存在しない場合、WordPress は、次の階層レベルのファイル *`category-{ID}.php`* を検索し、以降も同様の手順で続けます。WordPress が、任意の専用テンプレートや *`archive.php`* テンプレート・ファイルを見つけられなかった場合、デフォルト挙動に切り替わり、*`index.php`* を使用します。

<!-- 
The category hierarchy is listed below:
 -->

カテゴリー階層は、以下の通りです:

<!-- 
1.  *category-{slug}.php*: For example, if the category’s slug is named “news,” WordPress would look for a file named *category-news.php.*
2.  *category-{ID}.php*: For example, if the category’s ID is “6”, WordPress would look for a file named *category-6.php.*
3.  *category.php*
4.  *archive.php*
5.  *index.php*
 -->

1.  *`category-{slug}.php`*: たとえば、カテゴリーのスラッグが「news」と名付けられている場合、WordPress は、*`category-news.php`* という名称のファイルを検索します。
2.  *`category-{ID}.php`*: たとえば、カテゴリーの ID が「6」の場合、WordPress は、*`category-6.php`* という名称のファイルを検索します。
3.  *`category.php`*
4.  *`archive.php`*
5.  *`index.php`*

<!-- 
### Tag
 -->

### タグ

<!-- 
For tags, WordPress looks for the *tag-{slug}.php* file. If it doesn’t exist, WordPress then looks for a file for the next hierarchical level, *tag-{ID}.php*, and so on. If WordPress fails to find any specialized templates or an *archive.php* template file, it will revert to the default behavior, using *index.php*.
 -->

タグの場合、WordPress は、*`tag-{slug}.php`* ファイルを検索します。存在しない場合、WordPress は、次の階層レベルのファイル *`tag-{ID}.php`* を検索し、以降も同様の手順で続けます。WordPress が、任意の専用テンプレートや *`archive.php`* テンプレート・ファイルを見つけられなかった場合、デフォルト挙動に切り替わり、*`index.php`* を使用します。

<!-- 
The tag hierarchy is listed below:
 -->

タグ階層は、以下の通りです:

<!-- 
1.  *tag-{slug}.php*: For example, if the tag’s slug is named “sometag,” WordPress would look for a file named *tag-sometag.php.*
2.  *tag-{id}.php*: For example, if the tag’s ID were “6,” WordPress would look for a file named *tag-6.php*.
3.  *tag.php*
4.  *archive.php*
5.  *index.php*
 -->

1.  *`tag-{slug}.php`*: たとえば、タグのスラッグが「sometag」の場合、WordPress は、*`tag-sometag.php`* という名称のファイルを検索します。
2.  *`tag-{id}.php`*: たとえば、タグの ID が「6」の場合、WordPress は、*`tag-6.php`* という名称のファイルを検索します。
3.  *`tag.php`*
4.  *`archive.php`*
5.  *`index.php`*

<!-- 
### Custom Taxonomy
 -->

### カスタム・タクソノミー

<!-- 
A custom taxonomy hierarchy works similarly to the categories and tags hierarchies described above. WordPress looks for the *taxonomy-{taxonomy}-{term}.php* file. If it doesn’t exist, WordPress then looks for a file for the next hierarchical level, *taxonomy-{taxonomy}.php*, and so on. If WordPress fails to find any specialized templates or an *archive.php* template file, it will revert to the default behavior, using *index.php*.
 -->

カスタム・タクソノミー階層は、前述のカテゴリー階層やタグ階層と同様に機能します。WordPress は、*`taxonomy-{taxonomy}-{term}.php`* ファイルを検索します。このファイルが存在しない場合、WordPress は、次の階層レベルのファイル *`taxonomy-{taxonomy}.php`* を検索し、以降も同様の手順で続きます。WordPress が、専用テンプレートや *`archive.php`* テンプレートファイルを一切見つけることができない場合、デフォルト挙動に切り替わり、*`index.php`* を使用します。

<!-- 
The hierarchy for a custom taxonomy is listed below:
 -->

カスタム・タクソノミーにおける階層は、以下の通りです:

<!-- 
1.  *taxonomy-{taxonomy}-{term}.php*: For example, if the taxonomy is named “sometax,” and the taxonomy’s term is “someterm,” WordPress would look for a file named *taxonomy-sometax-someterm.php*.
2.  *taxonomy-{taxonomy}.php*: For example, if the taxonomy is named “sometax,” WordPress would look for a file named *taxonomy-sometax.php*
3.  *taxonomy.php*
4.  *archive.php*
5.  *index.php*
 -->

1.  *`taxonomy-{taxonomy}-{term}.php`*: たとえば、タクソノミーが「sometax」という名称で、そのタクソノミーのタームが「someterm」の場合、WordPress は、*`taxonomy-sometax-someterm.php`* という名称のファイルを検索します。
2.  *`taxonomy-{taxonomy}.php`*: たとえば、タクソノミーが「sometax」という名称の場合、WordPress は、*`taxonomy-sometax.php`* という名称のファイルを検索します。
3.  *`taxonomy.php`*
4.  *`archive.php`*
5.  *`index.php`*

<!-- 
## Creating Taxonomy Template Files
 -->

## タクソノミー・テンプレート・ファイルの作成

<!-- 
Now you’ve decided that you need to create custom designs for content based on taxonomies, where do you start?
 -->

タクソノミーにもとづくコンテンツ向けにカスタム・デザインを作成する必要があると決定したところですが、さて、どこから始めればよいでしょうか ?

<!-- 
Rather than starting from a blank file, it is good practice to **copy the next file in the hierarchy**, if it exists. If you’ve already created an *archive.php*, make a copy called *category.php* and modify that to suit your design needs. If you don’t have an *archive.php* file, use a copy of your theme’s *index.php* as a starting point.
 -->

空白のファイルから始めるよりも、存在する場合、**階層構造で次のファイルをコピーする** のが、グッド・プラクティスです。*`archive.php`* をすでに作成している場合は、*`category.php`* という名称でコピーを作成し、あなたのデザインに合わせて修正しましょう。*`archive.php`* ファイルがない場合は、あなたのテーマの *`index.php`* のコピーを出発点として使用しましょう。

<!-- 
Follow the same procedure if you are creating any taxonomy template file. Use a copy of your *archive.php*, *category.php*, *tag.php*, or *index.php* as a starting point.
 -->

タクソノミー・テンプレート・ファイルを作成する場合も、同様の手順に従ってください。*`archive.php`*、*`category.php`*、*`tag.php`*、または *`index.php`* のコピーを起点として使用しましょう。

<!-- 
## Examples
 -->

## 例

<!-- 
Now that you’ve selected the template file in your theme’s directory that you need to modify, let’s look at some examples.
 -->

あなたのテーマ・ディレクトリ内で、変更が必要なテンプレート・ファイルを選択したところで、いくつかの例を見ていきましょう。

<!-- 
### Adding Text to Category Pages
 -->

### カテゴリー・ページへの、テキスト追加

<!-- 
#### Static Text Above Posts
 -->

#### 投稿上の固定テキスト

<!-- 
Suppose you want some static text displayed before the list of posts on your category page(s). “Static” is text that remains the same, no matter which posts are displayed below, and no matter which category is displayed.
 -->

カテゴリー・ページ上の投稿リストの前に、固定テキストを表示したい場合を考えてみましょう。「固定」とは、下に表示される投稿や表示されるカテゴリーに関係なく、常に同じままのテキストを指します。

<!-- 
Open your file and above [The Loop](https://developer.wordpress.org/themes/basics/the-loop/ "The Loop") section of your Template file, insert the following code:
 -->

あなたのファイルを開き、あなたの「テンプレート」ファイルの [ループ](https://developer.wordpress.org/themes/basics/the-loop/ "The Loop") セクションの上に、以下のコードを挿入してください:

```markup
<p>This is some text that will display at the top of the Category page.</p>
```

<!-- 
This text will only display on an archive page displaying posts in that category.
 -->

本テキストは、そのカテゴリーの投稿を表示するアーカイブ・ページでのみ、表示されます。

<!-- 
#### Different Text on Some Category Pages
 -->

#### 一部のカテゴリー・ページで、異なるテキストの表示

<!-- 
What if you want to display different text based on the category page that the visitor is using? You could add default text to the main *category.php* file, and create special *category-{slug}.php* files each with their own version of the text, but this would create lots of files in your theme. Instead, you can use [conditional tags](https://developer.wordpress.org/themes/basics/conditional-tags/ "Conditional Tags").
 -->

訪問者が閲覧しているカテゴリー・ページに応じて、異なるテキストを表示したい場合は、どうすればよいでしょうか ? メインの *`category.php`* ファイルにデフォルトのテキストを追加し、それぞれ独自のテキスト版を持つ、特別な *`category-{slug}.php`* ファイルも作成できますが、その方法では、あなたのテーマ内に多数のファイルが生成されてしまいます。代わりに、[条件付きタグ](https://developer.wordpress.org/themes/basics/conditional-tags/ "Conditional Tags") を使用できます。

<!-- 
Again, this code would be added before the loop:
 -->

再び、本コードは、ループの前に追加します:

```php
<?php if ( is_category( 'Category A' ) ) : ?>
	<p>This is the text to describe category A.</p>
<?php elseif ( is_category( 'Category B' ) ) : ?>
	<p>This is the text to describe category B.</p>
<?php else : ?>
	<p>This is some generic text to describe all other category pages, I could be left blank.</p>
<?php endif; ?>
```

<!-- 
This code does the following:
 -->

本コードは、次のことを行います:

<!-- 
1.  Checks to see if the visitor has requested Category A. If yes, it displays the first piece of text.
2.  Checks for category B if the user didn’t request category A. If yes, it displays the second piece of text.
3.  Displays the default text, if neither was requested.
 -->

1.  訪問者がカテゴリー「A」をリクエストしたかどうかをチェックします。該当する場合、最初のテキストを表示します。
2.  ユーザーがカテゴリー「A」をリクエストしなかった場合、カテゴリー「B」をチェックします。該当する場合、2番目のテキストを表示します。
3.  どちらもリクエストされなかった場合、デフォルトのテキストを表示します。

<!-- 
#### Display Text only on First Page of Archive
 -->

#### アーカイブの最初のページにのみ、テキストの表示

<!-- 
If you have more posts than fits on one page of your archive, the category splits into multiple pages. Perhaps you want to display static text, if the user is on the first page of the results.
 -->

あなたのアーカイブに1ページに収まらない投稿がある場合、カテゴリーは複数のページに分割されます。おそらく、ユーザーが検索結果の最初のページにいる場合に、固定テキストを表示したいでしょう。

<!-- 
To do this, use a PHP if statement that looks at the value of the $paged WordPress variable.
 -->

これを処理するには、WordPress の `$paged` 変数の値を判定する PHP の `if` 文を使用します。

<!-- 
Put the following above The Loop:
 -->

以下の内容を、「ループ」の上に、挿入してください:

```php
<?php if ( $paged < 2 ) : ?>
	<p>Text for first page of Category archive.</p>
<?php endif; ?>
```

<!-- 
This code asks whether the page displayed is the first page of the archive. If it is, the text for the first page is displayed. Otherwise, the text for the subsequent pages is displayed.
 -->

本コードは、表示されているページが、アーカイブの最初のページかどうかを判定します。該当する場合、最初のページ用のテキストが表示されます。該当しない場合、以降のページ用のテキストが表示されます。

<!-- 
### Modify How Posts are Displayed
 -->

### 投稿の表示方法の調整

<!-- 
#### Excerpts vs. Full Posts
 -->

#### 抜粋 vs. 全文投稿

<!-- 
You can choose whether to display full posts or just excerpts. By displaying excerpts, you shorten the length of your archive page.
 -->

投稿全文を表示するか、抜粋のみを表示するかを選択できます。抜粋を表示することで、あなたのアーカイブ・ページの長さを短縮できます。

<!-- 
Open your file and find the loop. Look for:
 -->

あなたのファイルを開き、ループを探索してください。以下を検索して:

```php
the_content()
```

<!-- 
And replace it with:
 -->

それを、以下のように置き換えてください:

```php
the_excerpt()
```

<!-- 
And if your theme is displaying excerpts but you want to display the full content, replace `the_excerpt` with `the_content`.
 -->

あなたのテーマが抜粋を表示している場合、全文を表示したいなら、`the_excerpt` を `the_content` に置き換えてください。