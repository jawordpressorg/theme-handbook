<!-- 
# List of Conditional Tags
 -->

# 条件付きタグのリスト

<!-- 
Conditional Tags are a boolean data type that can be used in your Template Files to alter the display of content depending on the conditions that the current page matches. They tell WordPress what code to display under specific conditions. Conditional Tags usually work with PHP [if](http://php.net/manual/en/control-structures.if.php "PHP if conditional") /[else](http://php.net/manual/en/control-structures.else.php "PHP else conditional") Conditional Statements and have close relation with WOrdPress [Template Hierarchy](https://codex.wordpress.org/Template_Hierarchy "Template Hierarchy"). .
 -->

「条件付きタグ」は、真偽値データ型であり、あなたのテンプレートファイル内で、現在のページが合致する条件に応じて、コンテンツの表示を変化させるために使用できます。これらは、特定の条件下でどのコードを表示すべきかを、WordPress に通知します。「条件付きタグ」は通常、PHP の [if](http://php.net/manual/en/control-structures.if.php "PHP if conditional") / [else](http://php.net/manual/en/control-structures.else.php "PHP else conditional") 条件文と連携して動作し、WordPress の [テンプレート階層](https://codex.wordpress.org/Template_Hierarchy "Template Hierarchy") と密接に関連しています。

<!-- 
**Warning: You can only use conditional query tags after the [WP\_Query](https://developer.wordpress.org/reference/classes/wp_query/) is set up or  with [action hook](https://codex.wordpress.org/Plugin_API/Action_Reference#Actions_Run_During_a_Typical_Request "Plugin API/Action Reference").**
 -->

**警告: 条件付きクエリータグは、[`WP_Query`](https://developer.wordpress.org/reference/classes/wp_query/) が設定された後、または [アクションフック](https://codex.wordpress.org/Plugin_API/Action_Reference#Actions_Run_During_a_Typical_Request "Plugin API/Action Reference") と組み合わせてのみ使用できます。**

<!-- 
## Complete List of Conditional Tags
 -->

## 条件付きタグの完全リスト

<!-- 
*   [is\_front\_page()](https://codex.wordpress.org/Function_Reference/is_front_page "Function Reference/is front page")
*   [is\_home()](https://codex.wordpress.org/Function_Reference/is_home "Function Reference/is home")
*   [is\_front\_page()](https://codex.wordpress.org/Function_Reference/is_front_page "Function Reference/is front page")
*   [is\_home()](https://codex.wordpress.org/Function_Reference/is_home "Function Reference/is home")
*   [is\_admin()](https://codex.wordpress.org/Function_Reference/is_admin "Function Reference/is admin")
*   [is\_network\_admin()](https://codex.wordpress.org/Function_Reference/is_network_admin "Function Reference/is network admin")
*   [is\_admin\_bar\_showing()](https://codex.wordpress.org/Function_Reference/is_admin_bar_showing "Function Reference/is admin bar showing")
*   [is\_single()](https://codex.wordpress.org/Function_Reference/is_single "Function Reference/is single")
*   [is\_sticky()](https://codex.wordpress.org/Function_Reference/is_sticky "Function Reference/is sticky")
*   [is\_post\_type\_hierarchical( $post\_type )](https://codex.wordpress.org/Function_Reference/is_post_type_hierarchical "Function Reference/is post type hierarchical")
*   [is\_post\_type\_archive()](https://codex.wordpress.org/Function_Reference/is_post_type_archive "Function Reference/is post type archive")
*   [is\_comments\_popup()](https://codex.wordpress.org/Function_Reference/is_comments_popup "Function Reference/is comments popup")
*   [comments\_open()](https://codex.wordpress.org/Function_Reference/comments_open "Function Reference/comments open")
*   [pings\_open()](https://codex.wordpress.org/Function_Reference/pings_open "Function Reference/pings open")
*   [is\_page()](https://codex.wordpress.org/Function_Reference/is_page "Function Reference/is page")
*   [is\_page\_template()](https://codex.wordpress.org/Function_Reference/is_page_template "Function Reference/is page template")
*   [is\_category( $category )](https://codex.wordpress.org/Function_Reference/is_category "Function Reference/is category")
*   [is\_tag()](https://codex.wordpress.org/Function_Reference/is_tag "Function Reference/is tag")
*   [is\_tax()](https://codex.wordpress.org/Function_Reference/is_tax "Function Reference/is tax")
*   [has\_term()](https://codex.wordpress.org/Function_Reference/has_term "Function Reference/has term")
*   [term\_exists( $term, $taxonomy, $parent )](https://codex.wordpress.org/Function_Reference/term_exists "Function Reference/term exists")
*   [is\_taxonomy\_hierarchical( $taxonomy )](https://codex.wordpress.org/Function_Reference/is_taxonomy_hierarchical "Function Reference/is taxonomy hierarchical")
*   [taxonomy\_exists( $taxonomy )](https://codex.wordpress.org/Function_Reference/taxonomy_exists "Function Reference/taxonomy exists")
*   [is\_author()](https://codex.wordpress.org/Function_Reference/is_author "Function Reference/is author")
*   [is\_date()](https://codex.wordpress.org/Function_Reference/is_date "Function Reference/is date")
*   [is\_year()](https://codex.wordpress.org/Function_Reference/is_year "Function Reference/is year")
*   [is\_month()](https://codex.wordpress.org/Function_Reference/is_month "Function Reference/is month")
*   [is\_day()](https://codex.wordpress.org/Function_Reference/is_day "Function Reference/is day")
*   [is\_time()](https://codex.wordpress.org/Function_Reference/is_time "Function Reference/is time")
*   [is\_new\_day()](https://codex.wordpress.org/Function_Reference/is_new_day "Function Reference/is new day")
*   [is\_archive()](https://codex.wordpress.org/Function_Reference/is_archive "Function Reference/is archive")
*   [is\_search()](https://codex.wordpress.org/Function_Reference/is_search "Function Reference/is search")
*   [is\_404()](https://codex.wordpress.org/Function_Reference/is_404 "Function Reference/is 404")
*   [is\_paged()](https://codex.wordpress.org/Function_Reference/is_paged "Function Reference/is paged")
*   [is\_attachment()](https://codex.wordpress.org/Function_Reference/is_attachment "Function Reference/is attachment")
*   [wp\_attachment\_is\_image( $post\_id )](https://codex.wordpress.org/Function_Reference/wp_attachment_is_image "Function Reference/wp attachment is image")
*   [is\_local\_attachment( $url )](https://codex.wordpress.org/Function_Reference/is_local_attachment "Function Reference/is local attachment")
*   [is\_singular()](https://codex.wordpress.org/Function_Reference/is_singular "Function Reference/is singular")
*   [post\_type\_exists( $post\_type )](https://codex.wordpress.org/Function_Reference/post_type_exists "Function Reference/post type exists")
*   [is\_main\_query()](https://codex.wordpress.org/Function_Reference/is_main_query "Function Reference/is main query")
*   [is\_new\_day()](https://codex.wordpress.org/Function_Reference/is_new_day "Function Reference/is new day")
*   [is\_feed()](https://codex.wordpress.org/Function_Reference/is_feed "Function Reference/is feed")
*   [is\_trackback()](https://codex.wordpress.org/Function_Reference/is_trackback "Function Reference/is trackback")
*   [is\_preview()](https://codex.wordpress.org/Function_Reference/is_preview "Function Reference/is preview")
*   [in\_the\_loop()](https://codex.wordpress.org/Function_Reference/in_the_loop "Function Reference/in the loop")
*   [is\_dynamic\_sidebar()](https://codex.wordpress.org/Function_Reference/is_dynamic_sidebar "Function Reference/is dynamic sidebar")
*   [is\_active\_sidebar()](https://codex.wordpress.org/Function_Reference/is_active_sidebar "Function Reference/is active sidebar")
*   [is\_active\_widget( $widget\_callback, $widget\_id )](https://codex.wordpress.org/Function_Reference/is_active_widget "Function Reference/is active widget")
*   [is\_blog\_installed()](https://codex.wordpress.org/Function_Reference/is_blog_installed "Function Reference/is blog installed")
*   [is\_rtl()](https://codex.wordpress.org/Function_Reference/is_rtl "Function Reference/is rtl")
*   [is\_multisite()](https://codex.wordpress.org/Function_Reference/is_multisite "Function Reference/is multisite")
*   [is\_main\_site()](https://codex.wordpress.org/Function_Reference/is_main_site "Function Reference/is main site")
*   [is\_super\_admin()](https://codex.wordpress.org/Function_Reference/is_super_admin "Function Reference/is super admin")
*   [is\_user\_logged\_in()](https://codex.wordpress.org/Function_Reference/is_user_logged_in "Function Reference/is user logged in")
*   [email\_exists( $email )](https://codex.wordpress.org/Function_Reference/email_exists "Function Reference/email exists")
*   [username\_exists( $username )](https://codex.wordpress.org/Function_Reference/username_exists "Function Reference/username exists")
*   [is\_plugin\_active( $path )](https://codex.wordpress.org/Function_Reference/is_plugin_active "Function Reference/is plugin active")
*   [is\_plugin\_inactive( $path )](https://codex.wordpress.org/Function_Reference/is_plugin_inactive "Function Reference/is plugin inactive")
*   [is\_plugin\_active\_for\_network( $path )](https://codex.wordpress.org/Function_Reference/is_plugin_active_for_network "Function Reference/is plugin active for network")
*   [is\_plugin\_page()](https://codex.wordpress.org/Function_Reference/is_plugin_page "Function Reference/is plugin page")
*   [is\_child\_theme()](https://codex.wordpress.org/Function_Reference/is_child_theme "Function Reference/is child theme")
*   [current\_theme\_supports()](https://codex.wordpress.org/Function_Reference/current_theme_supports "Function Reference/current theme supports")
*   [has\_post\_thumbnail( $post\_id )](https://codex.wordpress.org/Function_Reference/has_post_thumbnail "Function Reference/has post thumbnail")
*   [wp\_script\_is( $handle, $list )](https://codex.wordpress.org/Function_Reference/wp_script_is "Function Reference/wp script is")
 -->

*   [`is_front_page()`](https://codex.wordpress.org/Function_Reference/is_front_page "Function Reference/is front page")
*   [`is_home()`](https://codex.wordpress.org/Function_Reference/is_home "Function Reference/is home")
*   [`is_front_page()`](https://codex.wordpress.org/Function_Reference/is_front_page "Function Reference/is front page")
*   [`is_home()`](https://codex.wordpress.org/Function_Reference/is_home "Function Reference/is home")
*   [`is_admin()`](https://codex.wordpress.org/Function_Reference/is_admin "Function Reference/is admin")
*   [`is_network_admin()`](https://codex.wordpress.org/Function_Reference/is_network_admin "Function Reference/is network admin")
*   [`is_admin_bar_showing()`](https://codex.wordpress.org/Function_Reference/is_admin_bar_showing "Function Reference/is admin bar showing")
*   [`is_single()`](https://codex.wordpress.org/Function_Reference/is_single "Function Reference/is single")
*   [`is_sticky()`](https://codex.wordpress.org/Function_Reference/is_sticky "Function Reference/is sticky")
*   [`is_post_type_hierarchical($post_type)`](https://codex.wordpress.org/Function_Reference/is_post_type_hierarchical "Function Reference/is post type hierarchical")
*   [`is_post_type_archive()`](https://codex.wordpress.org/Function_Reference/is_post_type_archive "Function Reference/is post type archive")
*   [`is_comments_popup()`](https://codex.wordpress.org/Function_Reference/is_comments_popup "Function Reference/is comments popup")
*   [`comments_open()`](https://codex.wordpress.org/Function_Reference/comments_open "Function Reference/comments open")
*   [`pings_open()`](https://codex.wordpress.org/Function_Reference/pings_open "Function Reference/pings open")
*   [`is_page()`](https://codex.wordpress.org/Function_Reference/is_page "Function Reference/is page")
*   [`is_page_template()`](https://codex.wordpress.org/Function_Reference/is_page_template "Function Reference/is page template")
*   [`is_category($category)`](https://codex.wordpress.org/Function_Reference/is_category "Function Reference/is category")
*   [`is_tag()`](https://codex.wordpress.org/Function_Reference/is_tag "Function Reference/is tag")
*   [`is_tax()`](https://codex.wordpress.org/Function_Reference/is_tax "Function Reference/is tax")
*   [`has_term()`](https://codex.wordpress.org/Function_Reference/has_term "Function Reference/has term")
*   [`term_exists($term, $taxonomy, $parent)`](https://codex.wordpress.org/Function_Reference/term_exists "Function Reference/term exists")
*   [`is_taxonomy_hierarchical($taxonomy)`](https://codex.wordpress.org/Function_Reference/is_taxonomy_hierarchical "Function Reference/is taxonomy hierarchical")
*   [`taxonomy_exists($taxonomy)`](https://codex.wordpress.org/Function_Reference/taxonomy_exists "Function Reference/taxonomy exists")
*   [`is_author()`](https://codex.wordpress.org/Function_Reference/is_author "Function Reference/is author")
*   [`is_date()`](https://codex.wordpress.org/Function_Reference/is_date "Function Reference/is date")
*   [`is_year()`](https://codex.wordpress.org/Function_Reference/is_year "Function Reference/is year")
*   [`is_month()`](https://codex.wordpress.org/Function_Reference/is_month "Function Reference/is month")
*   [`is_day()`](https://codex.wordpress.org/Function_Reference/is_day "Function Reference/is day")
*   [`is_time()`](https://codex.wordpress.org/Function_Reference/is_time "Function Reference/is time")
*   [`is_new_day()`](https://codex.wordpress.org/Function_Reference/is_new_day "Function Reference/is new day")
*   [`is_archive()`](https://codex.wordpress.org/Function_Reference/is_archive "Function Reference/is archive")
*   [`is_search()`](https://codex.wordpress.org/Function_Reference/is_search "Function Reference/is search")
*   [`is_404()`](https://codex.wordpress.org/Function_Reference/is_404 "Function Reference/is 404")
*   [`is_paged()`](https://codex.wordpress.org/Function_Reference/is_paged "Function Reference/is paged")
*   [`is_attachment()`](https://codex.wordpress.org/Function_Reference/is_attachment "Function Reference/is attachment")
*   [`wp_attachment_is_image($post_id)`](https://codex.wordpress.org/Function_Reference/wp_attachment_is_image "Function Reference/wp attachment is image")
*   [`is_local_attachment($url)`](https://codex.wordpress.org/Function_Reference/is_local_attachment "Function Reference/is local attachment")
*   [`is_singular()`](https://codex.wordpress.org/Function_Reference/is_singular "Function Reference/is singular")
*   [`post_type_exists($post_type)`](https://codex.wordpress.org/Function_Reference/post_type_exists "Function Reference/post type exists")
*   [`is_main_query()`](https://codex.wordpress.org/Function_Reference/is_main_query "Function Reference/is main query")
*   [`is_new_day()`](https://codex.wordpress.org/Function_Reference/is_new_day "Function Reference/is new day")
*   [`is_feed()`](https://codex.wordpress.org/Function_Reference/is_feed "Function Reference/is feed")
*   [`is_trackback()`](https://codex.wordpress.org/Function_Reference/is_trackback "Function Reference/is trackback")
*   [`is_preview()`](https://codex.wordpress.org/Function_Reference/is_preview "Function Reference/is preview")
*   [`in_the_loop()`](https://codex.wordpress.org/Function_Reference/in_the_loop "Function Reference/in the loop")
*   [`is_dynamic_sidebar()`](https://codex.wordpress.org/Function_Reference/is_dynamic_sidebar "Function Reference/is dynamic sidebar")
*   [`is_active_sidebar()`](https://codex.wordpress.org/Function_Reference/is_active_sidebar "Function Reference/is active sidebar")
*   [`is_active_widget($widget_callback, $widget_id)`](https://codex.wordpress.org/Function_Reference/is_active_widget "Function Reference/is active widget")
*   [`is_blog_installed()`](https://codex.wordpress.org/Function_Reference/is_blog_installed "Function Reference/is blog installed")
*   [`is_rtl()`](https://codex.wordpress.org/Function_Reference/is_rtl "Function Reference/is rtl")
*   [`is_multisite()`](https://codex.wordpress.org/Function_Reference/is_multisite "Function Reference/is multisite")
*   [`is_main_site()`](https://codex.wordpress.org/Function_Reference/is_main_site "Function Reference/is main site")
*   [`is_super_admin()`](https://codex.wordpress.org/Function_Reference/is_super_admin "Function Reference/is super admin")
*   [`is_user_logged_in()`](https://codex.wordpress.org/Function_Reference/is_user_logged_in "Function Reference/is user logged in")
*   [`email_exists($email)`](https://codex.wordpress.org/Function_Reference/email_exists "Function Reference/email exists")
*   [`username_exists($username)`](https://codex.wordpress.org/Function_Reference/username_exists "Function Reference/username exists")
*   [`is_plugin_active($path)`](https://codex.wordpress.org/Function_Reference/is_plugin_active "Function Reference/is plugin active")
*   [`is_plugin_inactive($path)`](https://codex.wordpress.org/Function_Reference/is_plugin_inactive "Function Reference/is plugin inactive")
*   [`is_plugin_active_for_network($path)`](https://codex.wordpress.org/Function_Reference/is_plugin_active_for_network "Function Reference/is plugin active for network")
*   [`is_plugin_page()`](https://codex.wordpress.org/Function_Reference/is_plugin_page "Function Reference/is plugin page")
*   [`is_child_theme()`](https://codex.wordpress.org/Function_Reference/is_child_theme "Function Reference/is child theme")
*   [`current_theme_supports()`](https://codex.wordpress.org/Function_Reference/current_theme_supports "Function Reference/current theme supports")
*   [`has_post_thumbnail($post_id)`](https://codex.wordpress.org/Function_Reference/has_post_thumbnail "Function Reference/has post thumbnail")
*   [`wp_script_is($handle, $list)`](https://codex.wordpress.org/Function_Reference/wp_script_is "Function Reference/wp script is")

<!-- 
## The Conditions For …
 -->

## …の条件

<!-- 
All of the Conditional Tags test to see whether a certain condition is met, and then returns either TRUE or FALSE. The conditions under which various tags output TRUE is listed below. Those tags which can accept parameters are so noted.
 -->

すべての「条件付きタグ」は、特定の条件が成立しているかどうかをチェックし、真または偽を返します。各種タグが真を出力する条件を、以下に列挙します。パラメータを受け付けるタグには、その旨を明記しています。

<!-- 
### The Main Page
 -->

### メインページか

<!-- 
*   [is\_home()](https://codex.wordpress.org/Function_Reference/is_home "Function Reference/is home")
 -->

*   [`is_home()`](https://codex.wordpress.org/Function_Reference/is_home "Function Reference/is home")

<!-- 
### The Front Page
 -->

### フロントページか

<!-- 
*   [is\_front\_page()](https://codex.wordpress.org/Function_Reference/is_front_page "Function Reference/is front page")
 -->

*   [`is_front_page()`](https://codex.wordpress.org/Function_Reference/is_front_page "Function Reference/is front page")

<!-- 
### The Blog Page
 -->

### ブログページか

<!-- 
*   [is\_front\_page()](https://codex.wordpress.org/Function_Reference/is_front_page "Function Reference/is front page")
*   [is\_home()](https://codex.wordpress.org/Function_Reference/is_home "Function Reference/is home")
 -->

*   [`is_front_page()`](https://codex.wordpress.org/Function_Reference/is_front_page "Function Reference/is front page")
*   [`is_home()`](https://codex.wordpress.org/Function_Reference/is_home "Function Reference/is home")

<!-- 
### A Single Post Page
 -->

### 単一の「投稿」ページか

<!-- 
*   [is\_single()](https://codex.wordpress.org/Function_Reference/is_single "Function Reference/is single")
 -->

*   [`is_single()`](https://codex.wordpress.org/Function_Reference/is_single "Function Reference/is single")

<!-- 
### A PAGE Page
 -->

### 「固定」ページか

<!-- 
*   [is\_page()](https://codex.wordpress.org/Function_Reference/is_page "Function Reference/is page")
*   [is\_page\_template()](https://codex.wordpress.org/Function_Reference/is_page_template "Function Reference/is page template")
 -->

*   [`is_page()`](https://codex.wordpress.org/Function_Reference/is_page "Function Reference/is page")
*   [`is_page_template()`](https://codex.wordpress.org/Function_Reference/is_page_template "Function Reference/is page template")

<!-- 
### Has Post Thumbnail
 -->

### 「アイキャッチ画像」が設定されているか

<!-- 
*   [has\_post\_thumbnail( $post\_id )](https://codex.wordpress.org/Function_Reference/has_post_thumbnail "Function Reference/has post thumbnail")
 -->

*   [`has_post_thumbnail($post_id)`](https://codex.wordpress.org/Function_Reference/has_post_thumbnail "Function Reference/has post thumbnail")

<!-- 
### A Single Page, a Single Post, an Attachment or Any Other Custom Post Type
 -->

### 単一の「ページ」、単一の「投稿」、「添付ファイル」、または任意のその他の「カスタム投稿タイプ」か

<!-- 
*   [is\_singular()](https://codex.wordpress.org/Function_Reference/is_singular "Function Reference/is singular")
 -->

*   [`is_singular()`](https://codex.wordpress.org/Function_Reference/is_singular "Function Reference/is singular")

<!-- 
### A Category Page
 -->

### 「カテゴリー」ページか

<!-- 
*   [is\_category( $category )](https://codex.wordpress.org/Function_Reference/is_category "Function Reference/is category")
 -->

*   [`is_category($category)`](https://codex.wordpress.org/Function_Reference/is_category "Function Reference/is category")

<!-- 
### A Tag Page
 -->

### 「タグ」ページか

<!-- 
*   [is\_tag()](https://codex.wordpress.org/Function_Reference/is_tag "Function Reference/is tag")
*   [has\_tag()](https://codex.wordpress.org/Function_Reference/has_tag "Function Reference/has tag")
 -->

*   [`is_tag()`](https://codex.wordpress.org/Function_Reference/is_tag "Function Reference/is tag")
*   [`has_tag()`](https://codex.wordpress.org/Function_Reference/has_tag "Function Reference/has tag")

<!-- 
### A Taxonomy Page (and related)
 -->

### 「タクソノミー」ページ (および関連項目) か

<!-- 
*   [is\_tax()](https://codex.wordpress.org/Function_Reference/is_tax "Function Reference/is tax")
*   [has\_term()](https://codex.wordpress.org/Function_Reference/has_term "Function Reference/has term")
*   [term\_exists( $term, $taxonomy, $parent )](https://codex.wordpress.org/Function_Reference/term_exists "Function Reference/term exists")
*   [is\_taxonomy\_hierarchical( $taxonomy )](https://codex.wordpress.org/Function_Reference/is_taxonomy_hierarchical "Function Reference/is taxonomy hierarchical")
*   [taxonomy\_exists( $taxonomy )](https://codex.wordpress.org/Function_Reference/taxonomy_exists "Function Reference/taxonomy exists")
 -->

*   [`is_tax()`](https://codex.wordpress.org/Function_Reference/is_tax "Function Reference/is tax")
*   [`has_term()`](https://codex.wordpress.org/Function_Reference/has_term "Function Reference/has term")
*   [`term_exists($term, $taxonomy, $parent)`](https://codex.wordpress.org/Function_Reference/term_exists "Function Reference/term exists")
*   [`is_taxonomy_hierarchical($taxonomy)`](https://codex.wordpress.org/Function_Reference/is_taxonomy_hierarchical "Function Reference/is taxonomy hierarchical")
*   [`taxonomy_exists($taxonomy)`](https://codex.wordpress.org/Function_Reference/taxonomy_exists "Function Reference/taxonomy exists")

<!-- 
### An Author Page
 -->

### 「投稿者アーカイブ」ページか

<!-- 
*   [is\_author()](https://codex.wordpress.org/Function_Reference/is_author "Function Reference/is author")
 -->

*   [`is_author()`](https://codex.wordpress.org/Function_Reference/is_author "Function Reference/is author")

<!-- 
### A Date Page
 -->

### 「日付」ページか

<!-- 
*   [is\_date()](https://codex.wordpress.org/Function_Reference/is_date "Function Reference/is date")
*   [is\_year()](https://codex.wordpress.org/Function_Reference/is_year "Function Reference/is year")
*   [is\_month()](https://codex.wordpress.org/Function_Reference/is_month "Function Reference/is month")
*   [is\_day()](https://codex.wordpress.org/Function_Reference/is_day "Function Reference/is day")
*   [is\_time()](https://codex.wordpress.org/Function_Reference/is_time "Function Reference/is time")
*   [is\_new\_day()](https://codex.wordpress.org/Function_Reference/is_new_day "Function Reference/is new day")
 -->

*   [`is_date()`](https://codex.wordpress.org/Function_Reference/is_date "Function Reference/is date")
*   [`is_year()`](https://codex.wordpress.org/Function_Reference/is_year "Function Reference/is year")
*   [`is_month()`](https://codex.wordpress.org/Function_Reference/is_month "Function Reference/is month")
*   [`is_day()`](https://codex.wordpress.org/Function_Reference/is_day "Function Reference/is day")
*   [`is_time()`](https://codex.wordpress.org/Function_Reference/is_time "Function Reference/is time")
*   [`is_new_day()`](https://codex.wordpress.org/Function_Reference/is_new_day "Function Reference/is new day")

<!-- 
### Any Archive Page
 -->

### 任意の「アーカイブ」ページか

<!-- 
*   [is\_archive()](https://codex.wordpress.org/Function_Reference/is_archive "Function Reference/is archive")
 -->

*   [`is_archive()`](https://codex.wordpress.org/Function_Reference/is_archive "Function Reference/is archive")

<!-- 
### A Search Result Page
 -->

### 「検索結果」ページか

<!-- 
*   [is\_search()](https://codex.wordpress.org/Function_Reference/is_search "Function Reference/is search")
 -->

*   [`is_search()`](https://codex.wordpress.org/Function_Reference/is_search "Function Reference/is search")

<!-- 
### A 404 Not Found Page
 -->

### 「404 Not Found」ページか

<!-- 
*   [is\_404()](https://codex.wordpress.org/Function_Reference/is_404 "Function Reference/is 404")
 -->

*   [`is_404()`](https://codex.wordpress.org/Function_Reference/is_404 "Function Reference/is 404")

<!-- 
### Is Dynamic SideBar
 -->

### 動的サイドバーか

<!-- 
*   [is\_dynamic\_sidebar()](https://codex.wordpress.org/Function_Reference/is_dynamic_sidebar "Function Reference/is dynamic sidebar")
 -->

*   [`is_dynamic_sidebar()`](https://codex.wordpress.org/Function_Reference/is_dynamic_sidebar "Function Reference/is dynamic sidebar")

<!-- 
### Is Sidebar Active
 -->

### サイドバーに、ウィジェットが配置されているか

<!-- 
*   [is\_active\_sidebar()](https://codex.wordpress.org/Function_Reference/is_active_sidebar "Function Reference/is active sidebar")
 -->

*   [`is_active_sidebar()`](https://codex.wordpress.org/Function_Reference/is_active_sidebar "Function Reference/is active sidebar")

<!-- 
### Is Widget Active
 -->

### ウィジェットが有効化されているか

<!-- 
*   [is\_active\_widget( $widget\_callback, $widget\_id )](https://codex.wordpress.org/Function_Reference/is_active_widget "Function Reference/is active widget")
 -->

*   [`is_active_widget($widget_callback, $widget_id)`](https://codex.wordpress.org/Function_Reference/is_active_widget "Function Reference/is active widget")

<!-- 
### Is User Logged in
 -->

### ユーザーがログインしているか

<!-- 
*   [is\_user\_logged\_in()](https://codex.wordpress.org/Function_Reference/is_user_logged_in "Function Reference/is user logged in")
 -->

*   [`is_user_logged_in()`](https://codex.wordpress.org/Function_Reference/is_user_logged_in "Function Reference/is user logged in")

<!-- 
### Email Exists
 -->

### メールアドレスが登録されているか

<!-- 
*   [email\_exists( $email )](https://codex.wordpress.org/Function_Reference/email_exists "Function Reference/email exists")
 -->

*   [`email_exists($email)`](https://codex.wordpress.org/Function_Reference/email_exists "Function Reference/email exists")

<!-- 
### Username Exists
 -->

### ユーザー名が登録されているか

<!-- 
*   [username\_exists( $username )](https://codex.wordpress.org/Function_Reference/username_exists "Function Reference/username exists")
 -->

*   [`username_exists($username)`](https://codex.wordpress.org/Function_Reference/username_exists "Function Reference/username exists")

<!-- 
### A Paged Page
 -->

### 「ページ分割された」ページか

<!-- 
*   [is\_paged()](https://codex.wordpress.org/Function_Reference/is_paged "Function Reference/is paged")
 -->

*   [`is_paged()`](https://codex.wordpress.org/Function_Reference/is_paged "Function Reference/is paged")

<!-- 
### Right To Left Reading
 -->

### 言語設定が「右から左へ読む」か

<!-- 
*   [is\_rtl()](https://codex.wordpress.org/Function_Reference/is_rtl "Function Reference/is rtl")
 -->

*   [`is_rtl()`](https://codex.wordpress.org/Function_Reference/is_rtl "Function Reference/is rtl")

<!-- 
### An Attachment
 -->

### 添付ファイルか

<!-- 
*   [is\_attachment()](https://codex.wordpress.org/Function_Reference/is_attachment "Function Reference/is attachment")
 -->

*   [`is_attachment()`](https://codex.wordpress.org/Function_Reference/is_attachment "Function Reference/is attachment")

<!-- 
### Attachment Is Image
 -->

### 添付ファイルが、画像か

<!-- 
*   [wp\_attachment\_is\_image( $post\_id )](https://codex.wordpress.org/Function_Reference/wp_attachment_is_image "Function Reference/wp attachment is image")
 -->

*   [`wp_attachment_is_image($post_id)`](https://codex.wordpress.org/Function_Reference/wp_attachment_is_image "Function Reference/wp attachment is image")

<!-- 
### A Local Attachment
 -->

### 添付ファイルが、自サイトのメディアライブラリに存在するか

<!-- 
*   [is\_local\_attachment( $url )](https://codex.wordpress.org/Function_Reference/is_local_attachment "Function Reference/is local attachment")
 -->

*   [`is_local_attachment($url)`](https://codex.wordpress.org/Function_Reference/is_local_attachment "Function Reference/is local attachment")

<!-- 
### Post Type Exists
 -->

### 投稿タイプが登録されているか

<!-- 
*   [post\_type\_exists( $post\_type )](https://codex.wordpress.org/Function_Reference/post_type_exists "Function Reference/post type exists")
 -->

*   [`post_type_exists($post_type)`](https://codex.wordpress.org/Function_Reference/post_type_exists "Function Reference/post type exists")

<!-- 
### Is Main Query
 -->

### メインクエリーか

<!-- 
*   [is\_main\_query()](https://codex.wordpress.org/Function_Reference/is_main_query "Function Reference/is main query")
 -->

*   [`is_main_query()`](https://codex.wordpress.org/Function_Reference/is_main_query "Function Reference/is main query")

<!-- 
### A New Day
 -->

### 直前の投稿の日付と異なるか

<!-- 
*   [is\_new\_day()](https://codex.wordpress.org/Function_Reference/is_new_day "Function Reference/is new day")
 -->

*   [`is_new_day()`](https://codex.wordpress.org/Function_Reference/is_new_day "Function Reference/is new day")

<!-- 
### A Syndication
 -->

### フィードページか

<!-- 
*   [is\_feed()](https://codex.wordpress.org/Function_Reference/is_feed "Function Reference/is feed")
 -->

*   [`is_feed()`](https://codex.wordpress.org/Function_Reference/is_feed "Function Reference/is feed")

<!-- 
### A Trackback
 -->

### トラックバックエンジンに登録されているか

<!-- 
*   [is\_trackback()](https://codex.wordpress.org/Function_Reference/is_trackback "Function Reference/is trackback")
 -->

*   [`is_trackback()`](https://codex.wordpress.org/Function_Reference/is_trackback "Function Reference/is trackback")

<!-- 
### A Preview
 -->

### プレビュー画面か

<!-- 
*   [is\_preview()](https://codex.wordpress.org/Function_Reference/is_preview "Function Reference/is preview")
 -->

*   [`is_preview()`](https://codex.wordpress.org/Function_Reference/is_preview "Function Reference/is preview")

<!-- 
### Has An Excerpt
 -->

### 「抜粋」が存在するか

<!-- 
*   [has\_excerpt()](https://codex.wordpress.org/Function_Reference/has_excerpt "Function Reference/has excerpt")
 -->

*   [`has_excerpt()`](https://codex.wordpress.org/Function_Reference/has_excerpt "Function Reference/has excerpt")

<!-- 
### Has A Nav Menu Assigned
 -->

### メニューを設定済みか

<!-- 
*   [has\_nav\_menu()](https://codex.wordpress.org/Function_Reference/has_nav_menu "Function Reference/has nav menu")
 -->

*   [`has_nav_menu()`](https://codex.wordpress.org/Function_Reference/has_nav_menu "Function Reference/has nav menu")

<!-- 
### Is Blog Installed
 -->

### ブログが初期設定を完了しているか

<!-- 
*   [is\_blog\_installed()](https://codex.wordpress.org/Function_Reference/is_blog_installed "Function Reference/is blog installed")
 -->

*   [`is_blog_installed()`](https://codex.wordpress.org/Function_Reference/is_blog_installed "Function Reference/is blog installed")

<!-- 
### Part of a Network (Multisite)
 -->

### ネットワークの一部 (マルチサイト) か

<!-- 
*   [is\_multisite()](https://codex.wordpress.org/Function_Reference/is_multisite "Function Reference/is multisite")
*   [is\_main\_site()](https://codex.wordpress.org/Function_Reference/is_main_site "Function Reference/is main site")
*   [is\_super\_admin()](https://codex.wordpress.org/Function_Reference/is_super_admin "Function Reference/is super admin")
 -->

*   [`is_multisite()`](https://codex.wordpress.org/Function_Reference/is_multisite "Function Reference/is multisite")
*   [`is_main_site()`](https://codex.wordpress.org/Function_Reference/is_main_site "Function Reference/is main site")
*   [`is_super_admin()`](https://codex.wordpress.org/Function_Reference/is_super_admin "Function Reference/is super admin")

<!-- 
### An Active Plugin
 -->

### プラグインが有効化されているか

<!-- 
*   [is\_plugin\_active( $path )](https://codex.wordpress.org/Function_Reference/is_plugin_active "Function Reference/is plugin active")
*   [is\_plugin\_inactive( $path )](https://codex.wordpress.org/Function_Reference/is_plugin_inactive "Function Reference/is plugin inactive")
*   [is\_plugin\_active\_for\_network( $path )](https://codex.wordpress.org/Function_Reference/is_plugin_active_for_network "Function Reference/is plugin active for network")
*   [is\_plugin\_page()](https://codex.wordpress.org/Function_Reference/is_plugin_page "Function Reference/is plugin page")
 -->

*   [`is_plugin_active($path)`](https://codex.wordpress.org/Function_Reference/is_plugin_active "Function Reference/is plugin active")
*   [`is_plugin_inactive($path)`](https://codex.wordpress.org/Function_Reference/is_plugin_inactive "Function Reference/is plugin inactive")
*   [`is_plugin_active_for_network($path)`](https://codex.wordpress.org/Function_Reference/is_plugin_active_for_network "Function Reference/is plugin active for network")
*   [`is_plugin_page()`](https://codex.wordpress.org/Function_Reference/is_plugin_page "Function Reference/is plugin page")

<!-- 
### A Child Theme
 -->

### 子テーマか

<!-- 
*   [is\_child\_theme()](https://codex.wordpress.org/Function_Reference/is_child_theme "Function Reference/is child theme")
 -->

*   [`is_child_theme()`](https://codex.wordpress.org/Function_Reference/is_child_theme "Function Reference/is child theme")

<!-- 
### Theme supports a feature
 -->

### テーマがサポートする機能

<!-- 
*   [current\_theme\_supports()](https://codex.wordpress.org/Function_Reference/current_theme_supports "Function Reference/current theme supports")
 -->

*   [`current_theme_supports()`](https://codex.wordpress.org/Function_Reference/current_theme_supports "Function Reference/current theme supports")

<!-- 
### Is Previewed in the Customizer
 -->

### 「カスタマイザー」のプレビュー画面か

<!-- 
*   [is\_customize\_preview()](https://codex.wordpress.org/Function_Reference/is_customize_preview "Function Reference/is customize preview")
 -->

*   [`is_customize_preview()`](https://codex.wordpress.org/Function_Reference/is_customize_preview "Function Reference/is customize preview")