<!-- 
# Custom Post Type Template Files
 -->

# カスタム投稿タイプのテンプレート・ファイル

<!-- 
The WordPress theme system supports custom [templates](https://developer.wordpress.org/themes/basics/template-files/) for custom post types. Custom templates for the single display of posts belonging to custom post types have been supported since WordPress [Version 3.0](https://codex.wordpress.org/Version_3.0) and the support for custom templates for archive displays was added in [Version 3.1](https://codex.wordpress.org/Version_3.1).
 -->

WordPress のテーマ・システムは、カスタム投稿タイプ用のカスタム [テンプレート](https://developer.wordpress.org/themes/basics/template-files/) をサポートしています。カスタム投稿タイプに属する投稿の個別表示用のカスタム・テンプレートは、WordPress [v3.0](https://codex.wordpress.org/Version_3.0) からサポートされており、アーカイブ表示用のカスタム・テンプレートのサポートは [v3.1](https://codex.wordpress.org/Version_3.1) で追加されました。

<!-- 
## Custom Post Type – Template Hierarchy
 -->

## カスタム投稿タイプ – テンプレート階層

<!-- 
WordPress will work through the [template hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/) and use the template file it comes across first. So if you want to create a custom template for your `acme_product` custom post type, a good place to start is by copying the `single.php` file, saving it as `single-acme_product.php` and editing that.
 -->

WordPress は、[テンプレート階層](https://developer.wordpress.org/themes/basics/template-hierarchy/) に沿って処理を行い、最初に遭遇したテンプレート・ファイルを使用します。したがって、あなたのカスタム投稿タイプ `acme_product` 用にカスタム・テンプレートを作成したい場合、良い出発点は `single.php` ファイルをコピーし、`single-acme_product.php` として保存して編集することです。

<!-- 
However if you don’t want to create custom template files, WordPress will use the files already present in your theme, which would be `archive.php` and `single.php` and `index.php` files.
 -->

ただし、カスタム・テンプレート・ファイルを作成したくない場合、WordPress は、あなたのテーマにすでに存在するファイル、つまり `archive.php`、`single.php`、`index.php` ファイルを使用します。

<!-- 
Single posts and their archives can be displayed using the `single.php` and `archive.php` template files respectively,
 -->

個別の投稿とそのアーカイブは、それぞれ `single.php` および `archive.php` テンプレート・ファイルを使用して、表示できます。

<!-- 
*   single posts of a custom post type will use **single-{post\_type}.php**
*   and their archives will use **archive-{post\_type}.php**
*   and if you don’t have this post type archive page you can pass **BLOG\_URL?post\_type={post\_type}**
 -->

*   カスタム投稿タイプの個別投稿には、**`single-{post_type}.php`** が使用され、
*   それらのアーカイブには、**`archive-{post_type}.php`** が使用され、
*   この投稿タイプのアーカイブ・ページがない場合、**`BLOG_URL?post_type={post_type}`** が渡されます

<!-- 
where `{post_type}` is the `$post_type` argument of the [register\_post\_type()](https://developer.wordpress.org/reference/functions/register_post_type/) function.
 -->

ここで、`{post_type}` は [`register_post_type()`](https://developer.wordpress.org/reference/functions/register_post_type/) 関数の `$post_type` 引数です。

<!-- 
So for the above example, you could create `single-acme_product.php` and `archive-acme_product.php` template files for single product posts and their archives.
 -->

上記の例では、`product` の個別投稿用とアーカイブ用として、それぞれ `single-acme_product.php` と `archive-acme_product.php` というテンプレート・ファイルを作成できます。

<!-- 
Alternatively, you can use the `is_post_type_archive()` function in any template file to check if the query shows an archive page of a given post types(s), and the `post_type_archive_title()` to display the post type title.
 -->

あるいは、任意のテンプレート・ファイルで `is_post_type_archive()` 関数を使用し、クエリーが特定の投稿タイプのアーカイブ・ページを表示しているかどうかを確認し、また、`post_type_archive_title()` 関数を使用して、投稿タイプのタイトルを表示できます。

<!-- 
## Custom Post Type templates
 -->

## カスタム投稿タイプのテンプレート

<!-- 
*   **single-{post-type}.php**  
    The single post template used when a visitor requests a single post from a custom post type. For example, `single-acme_product.php` would be used for displaying single posts from a custom post type named `acme_product`.
*   **archive-{post-type}.php**  
    The archive post type template is used when visitors request a custom post type archive. For example, `archive-acme_product.php` would be used for displaying an archive of posts from the custom post type named `acme_product`. The `archive.php` template file is used if the `archive-{post-type}.php` is not present.
*   **index.php**  
    The `index.php` is used if a specific query template (`single-{post-type}.php, single.php, archive-{post-type}.php, archive.php, search.php`) for the custom post type is not present.
 -->

*   **`single-{post-type}.php`**  
    訪問者がカスタム投稿タイプの個別投稿をリクエストした際に使用される、個別投稿テンプレートです。たとえば、`acme_product` という名称のカスタム投稿タイプにおける個別投稿の表示には、`single-acme_product.php` が使用されます。
*   **`archive-{post-type}.php`**  
    訪問者がカスタム投稿タイプのアーカイブをリクエストした際に使用されるアーカイブ投稿タイプ・テンプレートです。たとえば、`acme_product` という名称のカスタム投稿タイプにおける投稿のアーカイブを表示するには、`archive-acme_product.php` が使用されます。`archive-{post-type}.php` が存在しない場合、`archive.php` テンプレート・ファイルが使用されます。
*   **`index.php`**  
    カスタム投稿タイプ用の特定のクエリー・テンプレート (`single-{post-type}.php`、`single.php`、`archive-{post-type}.php`、`archive.php`、`search.php`) が存在しない場合に、`index.php` が使用されます。

<!-- 
## Function Reference
 -->

## 関数リファレンス

<!-- 
*   [register\_post\_type()](https://developer.wordpress.org/reference/functions/register_post_type/) : Registers a post type.
*   [is\_post\_type\_archive()](https://developer.wordpress.org/reference/functions/is_post_type_archive/) : Checks if the query for an existing post type archive page.
*   [post\_type\_archive\_title()](https://developer.wordpress.org/reference/functions/post_type_archive_title/) : Display or retrieve title for a post type archive.
 -->

*   [`register_post_type()`](https://developer.wordpress.org/reference/functions/register_post_type/): 投稿タイプを登録します。
*   [`is_post_type_archive()`](https://developer.wordpress.org/reference/functions/is_post_type_archive/): クエリーが既存の投稿タイプ・アーカイブ・ページを対象としているかを、チェックします。
*   [`post_type_archive_title()`](https://developer.wordpress.org/reference/functions/post_type_archive_title/): 投稿タイプ・アーカイブ用のタイトルを、表示または取得します。