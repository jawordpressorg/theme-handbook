<!-- 
# Post Template Files
 -->

# 投稿テンプレート・ファイル

<!-- 
There are many [template files](https://developer.wordpress.org/themes/basics/template-files/) that WordPress uses to display the Post [post type](https://developer.wordpress.org/themes/basics/post-types/). Any content dealing with a blog or its posts are within the Post post type.
 -->

WordPress が [投稿タイプ](https://developer.wordpress.org/themes/basics/post-types/)「投稿」を表示するために使用する [テンプレート・ファイル](https://developer.wordpress.org/themes/basics/template-files/) は、多数存在します。ブログやその投稿に関連するコンテンツは、すべて、投稿タイプ「投稿」内に含まれます。

<!-- 
## Index.php
 -->

## index.php

<!-- 
`index.php` will display Post post types if there is no other template file in place. As stated in many places, every theme must have an `index.php` file to be valid. Many basic themes can get away with just using the `index.php` to display their Post post types, but the use cases given above would justify creating other template files.
 -->

`index.php` は、他のテンプレート・ファイルが存在しない場合、投稿タイプ「投稿」を表示します。多くの場所で述べられているように、有効なテーマであるためには、すべてのテーマに `index.php` ファイルが必要です。多くの基本テーマは、投稿タイプ「投稿」を表示するために `index.php` だけを使用することで事足りる場合がありますが、上記のユース・ケースでは、他のテンプレート・ファイルを作成する正当な理由になります。

<!-- 
Often you will want unique content structure or layout depending on what is being displayed. There are many templates you can use to customize content structure based on the context within the site. The two most notable post template files are `home.php` and `single.php` which display a feed of posts and a single post respectively.
 -->

表示内容に応じて、独自のコンテンツ構造やレイアウトが必要になる場合が、よくあります。サイト内の文脈にもとづいて、コンテンツ構造をカスタマイズするために使用できるテンプレートは、多数存在します。最も注目すべき投稿テンプレート・ファイルは、投稿のフィードを表示する `home.php` と、個別投稿を表示する `single.php` の2つです。

<!-- 
## Home.php
 -->

## home.php

<!-- 
When a static front page is used and the site has a page defined for the blog list the `home.php` file is used for the designated blog list page. Use of this template is encouraged over creating a custom page template because blog pagination on a custom page template will not work properly. If there is no `home.php` in the theme `index.php` will be used instead.
 -->

固定フロント・ページが使用され、サイトにブログリスト用のページが定義されている場合、指定されたブログリスト・ページには `home.php` ファイルが使用されます。カスタム・ページ・テンプレートでは、ブログのページ・ネーションが正しく機能しないため、カスタム・ページ・テンプレートを作成するよりも、このテンプレートの使用が推奨されます。テーマ内に `home.php` が存在しない場合、代わりに `index.php` が使用されます。

<!-- 
## Single.php
 -->

## single.php

<!-- 
It’s good sense to build as simply as possible in your template structure and not make more templates unless you have real need for them. Therefore, most theme developers don’t create a single-post.php file because single.php is specific enough. For the most part, all themes should have a `single.php`. Below is an example of a `single.php` file from the theme Twenty Fifteen.
 -->

あなたのテンプレート構造は、可能な限りシンプルに構築し、真に必要でない限り、追加のテンプレートを作成しないのが賢明です。したがって、ほとんどのテーマ開発者は、`single.php` で十分に機能するため、`single-post.php` ファイルを作成しません。基本的に、すべてのテーマには `single.php` が必要です。以下は「Twenty Fifteen」テーマにおける `single.php` ファイルの例です。

```php
<?php
/**
 * The template for displaying all single posts and attachments
 *
 * @package WordPress
 * @subpackage Twenty_Fifteen
 * @since Twenty Fifteen 1.0
 */
 
get_header(); ?>
 
    <div id="primary" class="content-area">
        <main id="main" class="site-main" role="main">
 
        <?php
        // Start the loop.
        while ( have_posts() ) : the_post();
 
            /*
             * Include the post format-specific template for the content. If you want to
             * use this in a child theme, then include a file called called content-___.php
             * (where ___ is the post format) and that will be used instead.
             */
            get_template_part( 'content', get_post_format() );
 
            // If comments are open or we have at least one comment, load up the comment template.
            if ( comments_open() || get_comments_number() ) :
                comments_template();
            endif;
 
            // Previous/next post navigation.
            the_post_navigation( array(
                'next_text' => '<span class="meta-nav" aria-hidden="true">' . __( 'Next', 'twentyfifteen' ) . '</span> ' .
                    '<span class="screen-reader-text">' . __( 'Next post:', 'twentyfifteen' ) . '</span> ' .
                    '<span class="post-title">%title</span>',
                'prev_text' => '<span class="meta-nav" aria-hidden="true">' . __( 'Previous', 'twentyfifteen' ) . '</span> ' .
                    '<span class="screen-reader-text">' . __( 'Previous post:', 'twentyfifteen' ) . '</span> ' .
                    '<span class="post-title">%title</span>',
            ) );
 
        // End the loop.
        endwhile;
        ?>
 
        </main><!-- .site-main -->
    </div><!-- .content-area -->
 
<?php get_footer(); ?>
```

<!-- 
In the code example above you can see the header is pulled in with `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)` then there are a two html tags. Next [the Loop](https://developer.wordpress.org/themes/basics/the-loop/) starts and the [template tag](https://developer.wordpress.org/themes/basics/template-tags/) `[get_template_part](https://developer.wordpress.org/reference/functions/get_template_part/)(` `'content'``, get_post_format());` pulls in the appropriate content by determining the post type with `[get_post_format()](https://developer.wordpress.org/reference/functions/get_post_format/)`. Next, [comments](https://developer.wordpress.org/themes/functionality/comments/) are pulled in with the template tag [comments\_template()](https://developer.wordpress.org/reference/functions/comments_template/). Then there is some [pagination](https://developer.wordpress.org/themes/functionality/pagination/). Lastly, the content divs are closed and then footer is pulled in with `[get_footer()](https://developer.wordpress.org/reference/functions/get_footer/)`.
 -->

上記のコード例では、ヘッダーが `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)` で取得され、その後2つの HTML タグが続くことがわかります。次いで [ループ](https://developer.wordpress.org/themes/basics/the-loop/) が開始され、[テンプレート・タグ](https://developer.wordpress.org/themes/basics/template-tags/) `[get_template_part](https://developer.wordpress.org/reference/functions/get_template_part/)(` `'content'``, get_post_format());` が、`[get_post_format()](https://developer.wordpress.org/reference/functions/get_post_format/)` で投稿タイプを判別し、適切なコンテンツを取得します。その後、テンプレート・タグ [`comments_template()`](https://developer.wordpress.org/reference/functions/comments_template/) で [コメント](https://developer.wordpress.org/themes/functionality/comments/) が取得されます。続いて [ページ・ネーション](https://developer.wordpress.org/themes/functionality/pagination/) が行われます。最後に、コンテンツの div タグが閉じられ、`[get_footer()](https://developer.wordpress.org/reference/functions/get_footer/)` でフッターが取得されます。

<!-- 
## Singular.php
 -->

## singular.php

<!-- 
WordPress Version 4.3 added `singular.php` that comes in the hierarchy after `single.php` for posts, `page.php` for pages, and the variations of each. This template follows the rules of [is\_singular()](https://developer.wordpress.org/reference/functions/is_singular/) and is used for a single post, regardless of post type. Themes that used the same code for both of those files (or included one in the other) can now simplify down to the one template.
 -->

WordPress v4.3では、投稿用の `single.php`、ページ用の `page.php`、およびそれぞれのバリエーションに続く階層として `singular.php` が追加されました。本テンプレートは [`is_singular()`](https://developer.wordpress.org/reference/functions/is_singular/) のルールに従い、投稿タイプに関係なく、個別投稿に使用されます。これまでに両ファイルで同一コードを使用していた (あるいは、一方を他方に包含していた) テーマは、ひとつのテンプレートに簡素化できます。

<!-- 
## Archive.php
 -->

## archive.php

<!-- 
Unless a developer includes meta data with permalinks in their templates, the `archive.php` will not be used. Meta data is information tied to the post. For example the date something was posted on, the author, and any [categories, tags, or taxonomies](https://developer.wordpress.org/themes/functionality/categories-tags-custom-taxonomies/) used for the post are all examples of meta data. When a visitor to a website clicks on the meta data, the `archive.php` will render any posts associated with that piece of meta data. For example, if a visitor clicks on the name of an author, the `archive.php` will display all posts by that author.
 -->

開発者がテンプレートにパーマリンクのメタデータを含めない限り、`archive.php` は使用されません。メタデータとは、投稿に紐づく情報です。たとえば、投稿日時、作者、投稿に適用された [カテゴリー、タグ、タクソノミー](https://developer.wordpress.org/themes/functionality/categories-tags-custom-taxonomies/) などがメタデータの例です。Web サイト訪問者がメタデータをクリックすると、`archive.php` は、そのメタデータに関連付けられた投稿を表示します。たとえば、訪問者が作者の名前をクリックすると、`archive.php` は、その作者の全投稿を表示します。

<!-- 
Commonly, the title of the page being displayed by `archive.php` will be the name of the meta data the user clicked on. So if the user clicked on the Author’s name, the page name displaying all the other author’s posts will be the Author’s name and frequently there might be an additional description about the meta data. Here is a code example from Twenty Fifteen on their `archive.php` file. This snippet is the only piece of code that makes the `archive.php` file different from a `home.php` or `index.php` file.
 -->

通常、`archive.php` で表示されるページのタイトルは、ユーザーがクリックしたメタデータの名称になります。したがって、ユーザーが「作者」の名前をクリックした場合、作者の他のすべての投稿を表示するページ名は、「作者」の名前となり、多くの場合、メタデータに関する追加の説明が記載されます。以下は、「Twenty Fifteen」テーマにおける `archive.php` ファイルのコード例です。このコード・スニペットこそが、`archive.php` ファイルを `home.php` や `index.php` ファイルと区別する唯一の部分です。

```php
<header class="page-header">
    <?php
        the_archive_title( '<h1 class="page-title">', '</h1>' );
        the_archive_description( '<div class="taxonomy-description">', '</div>' );
    ?>
</header>
<!-- .page-header -->
```

<!-- 
## Author.php and Date.php
 -->

## author.php と date.php

<!-- 
`Author.php` and `date.php` are more specific archive type files. If you need a refresher check out where they fit within the [template heirarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/). Generally, `archive.php` will suffice for most themes’ needs and you won’t need to create these templates.
 -->

`author.php` および `date.php` は、より特定のアーカイブ・タイプ用のファイルです。復習が必要な場合は、[テンプレート階層](https://developer.wordpress.org/themes/basics/template-hierarchy/) における位置付けを確認してください。一般的に、ほとんどのテーマでは `archive.php` で十分であり、これらのテンプレートを作成する必要はありません。

<!-- 
### Author.php
 -->

### author.php

<!-- 
If you are building a theme designed for multiple authors, it might make sense to build an author.php template. In the `author.php` template you could provide more information about an author, their gravatar, pull in their social media sites, and then all posts written by them. This would be a step up from relying just on the `archive.php` file.
 -->

複数作者向けテーマを構築する場合、`author.php` テンプレートを作成すると便利です。`author.php` テンプレートでは、作者の詳細情報、グラバター、ソーシャルメディア・サイトの連携、そしてその作者が書いた全投稿を提示できます。これは `archive.php` ファイルだけに依存するよりも、一歩進んだ方法です。

<!-- 
Additionally, you can build specific `author.php` files for individual author’s by using their author ID or nicename. For example, say John Doe is the head author for a site with many guest authors. You may want all the guest authors’ information to display with author.php but you might build a specific author page with more information for John Doe by creating `author-johndoe.php` or `author-3.php` if his author ID is 3.
 -->

さらに、個々の作者 ID またはニックネームを使用して、特定の `author.php` ファイルも作成できます。たとえば、多くのゲスト作者が参加するサイトの、主たる作者が「John Doe」だとしましょう。ゲスト作者全員の情報は `author.php` で表示しつつ、作者名が「John Doe」であれば `author-johndoe.php`、作者 ID が3であれば `author-3.php` のような、より詳細な情報を含む専用作者ページを作成できます。

<!-- 
### Date.php
 -->

### date.php

<!-- 
Similarly, if you are building a theme directed at magazine or news websites, a `date.php` file might make sense to build as these websites frequently organize their articles and posts by date or issue. Additionally, you could build a `day.php`, `month.php`, or `year.php` if you found enough justification for it.
 -->

同様に、雑誌やニュースサイト向けのテーマを構築する場合、記事や投稿を、日付や号ごとに整理することが多いため、`date.php` ファイルを作成するのが合理的でしょう。さらに、十分な根拠がある場合は、`day.php`、`month.php`、`year.php` も作成できます。

<!-- 
## Category.php, Tag.php, and Taxonomy.php
 -->

## category.php、tag.php、taxonomy.php

<!-- 
If you need a refresher on what [categories, tags, & taxonomies](https://developer.wordpress.org/themes/basics/categories-tags-custom-taxonomies/) are you can look at their page. Often you won’t need to build out these template files. However, in an example of building a theme for food bloggers, there are some use cases for building these specific templates. In a food blogger website, the categories could be Great Restaurants, Beautiful Food, Ethnic Cuisine, and Recipes.
 -->

[カテゴリー、タグ、タクソノミー](https://developer.wordpress.org/themes/basics/categories-tags-custom-taxonomies/) について復習が必要な場合は、それぞれのページをご覧ください。多くの場合、これらのテンプレート・ファイルを構築する必要はほとんどありません。ただし、フード・ブロガー向けテーマ構築の例では、これらの特定のテンプレートを作成するユース・ケースが存在します。フード・ブロガーの Web サイトでは、カテゴリーとして「おすすめレストラン」「美しい料理」「エスニック料理」「レシピ」などが考えられます。

<!-- 
You might want most of your blog posts to display the same way except for any blogs that are categorized as recipes, because all recipes have ingredients and instrucitons sections. Therefore, you may want to build a `category-recipe.php` file to display your recipe blog posts in a grid view with some of the important details about the recipe visible.
 -->

ほとんどのブログ投稿は同一の表示形式でも、「レシピ」カテゴリーに分類される投稿は、材料や手順のセクションを含めるため、例外にしたい場合があります。このようなとき`category-recipe.php` ファイルを作成すると、レシピに関する重要な詳細の一部とともにグリッドビューでブログ投稿を表示できます。

<!-- 
Additionally, perhaps chocolate is a really important tag for the theme you’re building. It might make sense to build a `tag-chocolate.php` file so that you can display a specialized banner image of chocolate.
 -->

さらに、あなたが構築しているテーマにとって「チョコレート」というタグが、非常に重要かもしれません。`tag-chocolate.php` ファイルを作成すると、チョコレート専用のバナー画像を表示できるようになるため、理に適っているかもしれません。

<!-- 
## Search.php
 -->

## search.php

<!-- 
Most themes have a search.php file so it is clear to users that their query went through. It is common to have some sort of header identifying the query results such as this snippet found int twenty fifteen’s theme.
 -->

ほとんどのテーマには、`search.php` ファイルが存在するため、ユーザーは検索クエリーが正常に処理されたことを、明確に認識できます。検索結果を識別するヘッダーを設けるのが一般的であり、たとえば「Twenty Fifteen」テーマでは、以下のようなスニペットが使用されています。

```php
<header class="page-header">
<h1 class="page-title">
    <?php printf( __( 'Search Results for: %s', 'twentyfifteen' ), get_search_query() ); ?>
</h1>
</header><!-- .page-header -->
```

<!-- 
This code snippet pulls in the query that was searched with `get_search_query()`. Often `search.php` will only pull in the excerpt instead of the full content since the user is trying to determine if the article or page fits their search.
 -->

本コードスニペットは、`get_search_query()` で検索されたクエリーを取得します。多くの場合、`search.php` は、記事やページが検索条件に合致するか判断するため、全文ではなく抜粋のみを取得します。