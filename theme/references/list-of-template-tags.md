<!-- 
# List of Template Tags
 -->

# テンプレートタグのリスト

<!-- 
## Complete List of Template Tags
 -->

## テンプレートタグの完全リスト

<!-- 
Template tags files are stored in the `[wp-includes](https://core.trac.wordpress.org/browser/trunk/src/wp-includes)` directory. The files have the suffix of “-template.php” to distinguish them from other WordPress files. There are 9 template tags files:
 -->

テンプレートタグファイルは、[`wp-includes`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes) ディレクトリに保存されています。これらのファイルは、他の WordPress ファイルと区別するため、`-template.php` という接尾辞が付いています。テンプレートタグファイルは、9種類あります:

<!-- 
*   `[wp-includes/general-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/general-template.php#L0)`
*   `[wp-includes/author-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/author-template.php#L0)`
*   `[wp-includes/bookmark-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/bookmark-template.php#L0)`
*   `[wp-includes/category-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/category-template.php#L0)`
*   `[wp-includes/comment-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/comment-template.php#L0)`
*   `[wp-includes/link-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/link-template.php#L0)`
*   `[wp-includes/post-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/post-template.php#L0)`
*   `[wp-includes/post-thumbnail-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/post-thumbnail-template.php#L0)`
*   `[wp-includes/nav-menu-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/nav-menu-template.php#L0)`
 -->

*   [`wp-includes/general-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/general-template.php#L0)
*   [`wp-includes/author-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/author-template.php#L0)
*   [`wp-includes/bookmark-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/bookmark-template.php#L0)
*   [`wp-includes/category-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/category-template.php#L0)
*   [`wp-includes/comment-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/comment-template.php#L0)
*   [`wp-includes/link-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/link-template.php#L0)
*   [`wp-includes/post-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/post-template.php#L0)
*   [`wp-includes/post-thumbnail-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/post-thumbnail-template.php#L0)
*   [`wp-includes/nav-menu-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/nav-menu-template.php#L0)

<!-- 
## Tags
 -->

## タグ

<!-- 
### General tags
 -->

### 「一般」タグ

<!-- 
`[wp-includes/general-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/general-template.php#L0)`
 -->

[`wp-includes/general-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/general-template.php#L0)

<!-- 
*   [get\_header()](https://developer.wordpress.org/reference/functions/get_header/)
*   [get\_footer()](https://developer.wordpress.org/reference/functions/get_footer/ "Function Reference/get footer")
*   [get\_sidebar()](https://developer.wordpress.org/reference/functions/get_sidebar/ "Function Reference/get sidebar")
*   [get\_template\_part()](https://developer.wordpress.org/reference/functions/get_template_part/ "Function Reference/get template part")
*   [get\_search\_form()](https://developer.wordpress.org/reference/functions/get_search_form "Function Reference/get search form")
*   [wp\_loginout()](https://developer.wordpress.org/reference/functions/wp_loginout/ "Function Reference/wp loginout")
*   [wp\_logout\_url()](https://developer.wordpress.org/reference/functions/wp_logout_url/ "Function Reference/wp logout url")
*   [wp\_login\_url()](https://developer.wordpress.org/reference/functions/wp_login_url/ "Function Reference/wp login url")
*   [wp\_login\_form()](https://developer.wordpress.org/reference/functions/wp_login_form/ "Function Reference/wp login form")
*   [wp\_lostpassword\_url()](https://developer.wordpress.org/reference/functions/wp_lostpassword_url/ "Function Reference/wp lostpassword url")
*   [wp\_register()](https://developer.wordpress.org/reference/functions/wp_register/ "Function Reference/wp register")
*   [wp\_meta()](https://developer.wordpress.org/reference/functions/wp_meta/ "Function Reference/wp meta")
*   [bloginfo()](https://developer.wordpress.org/reference/functions/bloginfo/ "Function Reference/bloginfo")
*   [get\_bloginfo()](https://developer.wordpress.org/reference/functions/get_bloginfo/ "Function Reference/get bloginfo")
*   [get\_current\_blog\_id()](https://developer.wordpress.org/reference/functions/get_current_blog_id "Function Reference/get current blog id")
*   [wp\_title()](https://developer.wordpress.org/reference/functions/wp_title)
*   [single\_post\_title()](https://developer.wordpress.org/reference/functions/single_post_title)
*   [post\_type\_archive\_title()](https://developer.wordpress.org/reference/functions/post_type_archive_title)
*   [single\_cat\_title()](https://developer.wordpress.org/reference/functions/single_cat_title)
*   [single\_tag\_title()](https://developer.wordpress.org/reference/functions/single_tag_title)
*   [single\_term\_title()](https://developer.wordpress.org/reference/functions/single_term_title)
*   [single\_month\_title()](https://developer.wordpress.org/reference/functions/single_month_title)
*   [get\_archives\_link()](https://developer.wordpress.org/reference/functions/get_archives_link)
*   [wp\_get\_archives()](https://developer.wordpress.org/reference/functions/wp_get_archives)
*   [calendar\_week\_mod()](https://developer.wordpress.org/reference/functions/calendar_week_mod)
*   [get\_calendar()](https://developer.wordpress.org/reference/functions/get_calendar)
*   [delete\_get\_calendar\_cache()](https://developer.wordpress.org/reference/functions/delete_get_calendar_cache/)
*   [allowed\_tags()](https://developer.wordpress.org/reference/functions/allowed_tags/)
*   [wp\_enqueue\_script()](https://developer.wordpress.org/reference/functions/wp_enqueue_script)
 -->

*   [`get_header()`](https://developer.wordpress.org/reference/functions/get_header/)
*   [`get_footer()`](https://developer.wordpress.org/reference/functions/get_footer/ "Function Reference/get footer")
*   [`get_sidebar()`](https://developer.wordpress.org/reference/functions/get_sidebar/ "Function Reference/get sidebar")
*   [`get_template_part()`](https://developer.wordpress.org/reference/functions/get_template_part/ "Function Reference/get template part")
*   [`get_search_form()`](https://developer.wordpress.org/reference/functions/get_search_form "Function Reference/get search form")
*   [`wp_loginout()`](https://developer.wordpress.org/reference/functions/wp_loginout/ "Function Reference/wp loginout")
*   [`wp_logout_url()`](https://developer.wordpress.org/reference/functions/wp_logout_url/ "Function Reference/wp logout url")
*   [`wp_login_url()`](https://developer.wordpress.org/reference/functions/wp_login_url/ "Function Reference/wp login url")
*   [`wp_login_form()`](https://developer.wordpress.org/reference/functions/wp_login_form/ "Function Reference/wp login form")
*   [`wp_lostpassword_url()`](https://developer.wordpress.org/reference/functions/wp_lostpassword_url/ "Function Reference/wp lostpassword url")
*   [`wp_register()`](https://developer.wordpress.org/reference/functions/wp_register/ "Function Reference/wp register")
*   [`wp_meta()`](https://developer.wordpress.org/reference/functions/wp_meta/ "Function Reference/wp meta")
*   [`bloginfo()`](https://developer.wordpress.org/reference/functions/bloginfo/ "Function Reference/bloginfo")
*   [`get_bloginfo()`](https://developer.wordpress.org/reference/functions/get_bloginfo/ "Function Reference/get bloginfo")
*   [`get_current_blog_id()`](https://developer.wordpress.org/reference/functions/get_current_blog_id "Function Reference/get current blog id")
*   [`wp_title()`](https://developer.wordpress.org/reference/functions/wp_title)
*   [`single_post_title()`](https://developer.wordpress.org/reference/functions/single_post_title)
*   [`post_type_archive_title()`](https://developer.wordpress.org/reference/functions/post_type_archive_title)
*   [`single_cat_title()`](https://developer.wordpress.org/reference/functions/single_cat_title)
*   [`single_tag_title()`](https://developer.wordpress.org/reference/functions/single_tag_title)
*   [`single_term_title()`](https://developer.wordpress.org/reference/functions/single_term_title)
*   [`single_month_title()`](https://developer.wordpress.org/reference/functions/single_month_title)
*   [`get_archives_link()`](https://developer.wordpress.org/reference/functions/get_archives_link)
*   [`wp_get_archives()`](https://developer.wordpress.org/reference/functions/wp_get_archives)
*   [`calendar_week_mod()`](https://developer.wordpress.org/reference/functions/calendar_week_mod)
*   [`get_calendar()`](https://developer.wordpress.org/reference/functions/get_calendar)
*   [`delete_get_calendar_cache()`](https://developer.wordpress.org/reference/functions/delete_get_calendar_cache/)
*   [`allowed_tags()`](https://developer.wordpress.org/reference/functions/allowed_tags/)
*   [`wp_enqueue_script()`](https://developer.wordpress.org/reference/functions/wp_enqueue_script)

<!-- 
### Author tags
 -->

### 「著者」タグ

<!-- 
`[wp-includes/author-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/author-template.php#L0)`
 -->

[`wp-includes/author-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/author-template.php#L0)

<!-- 
*   [the\_author()](https://developer.wordpress.org/reference/functions/the_author)
*   [get\_the\_author()](https://developer.wordpress.org/reference/functions/get_the_author)
*   [the\_author\_link()](https://developer.wordpress.org/reference/functions/the_author_link)
*   [get\_the\_author\_link()](https://developer.wordpress.org/reference/functions/get_the_author_link)
*   [the\_author\_meta()](https://developer.wordpress.org/reference/functions/the_author_meta)
*   [the\_author\_posts()](https://developer.wordpress.org/reference/functions/the_author_posts)
*   [the\_author\_posts\_link()](https://developer.wordpress.org/reference/functions/the_author_posts_link)
*   [wp\_dropdown\_users()](https://developer.wordpress.org/reference/functions/wp_dropdown_users)
*   [wp\_list\_authors()](https://developer.wordpress.org/reference/functions/wp_list_authors)
*   [get\_author\_posts\_url()](https://developer.wordpress.org/reference/functions/get_author_posts_url)
 -->

*   [`the_author()`](https://developer.wordpress.org/reference/functions/the_author)
*   [`get_the_author()`](https://developer.wordpress.org/reference/functions/get_the_author)
*   [`the_author_link()`](https://developer.wordpress.org/reference/functions/the_author_link)
*   [`get_the_author_link()`](https://developer.wordpress.org/reference/functions/get_the_author_link)
*   [`the_author_meta()`](https://developer.wordpress.org/reference/functions/the_author_meta)
*   [`the_author_posts()`](https://developer.wordpress.org/reference/functions/the_author_posts)
*   [`the_author_posts_link()`](https://developer.wordpress.org/reference/functions/the_author_posts_link)
*   [`wp_dropdown_users()`](https://developer.wordpress.org/reference/functions/wp_dropdown_users)
*   [`wp_list_authors()`](https://developer.wordpress.org/reference/functions/wp_list_authors)
*   [`get_author_posts_url()`](https://developer.wordpress.org/reference/functions/get_author_posts_url)

<!-- 
### Bookmark tags
 -->

### 「ブックマーク」タグ

<!-- 
`[wp-includes/bookmark-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/bookmark-template.php#L0)` and `[wp-includes/bookmark.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/bookmark.php#L0)`
 -->

[`wp-includes/bookmark-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/bookmark-template.php#L0) および [`wp-includes/bookmark.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/bookmark.php#L0)

<!-- 
*   [wp\_list\_bookmarks()](https://developer.wordpress.org/reference/functions/wp_list_bookmarks)
*   [get\_bookmark()](https://developer.wordpress.org/reference/functions/get_bookmark)
*   [get\_bookmark\_field()](https://developer.wordpress.org/reference/functions/get_bookmark_field)
*   [get\_bookmarks()](https://developer.wordpress.org/reference/functions/get_bookmarks)
 -->

*   [`wp_list_bookmarks()`](https://developer.wordpress.org/reference/functions/wp_list_bookmarks)
*   [`get_bookmark()`](https://developer.wordpress.org/reference/functions/get_bookmark)
*   [`get_bookmark_field()`](https://developer.wordpress.org/reference/functions/get_bookmark_field)
*   [`get_bookmarks()`](https://developer.wordpress.org/reference/functions/get_bookmarks)

<!-- 
### Category tags
 -->

### 「カテゴリー」タグ

<!-- 
`[wp-includes/category-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/category-template.php#L0)`
 -->

[`wp-includes/category-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/category-template.php#L0)

<!-- 
*   [category\_description()](https://developer.wordpress.org/reference/functions/category_description)
*   [single\_cat\_title()](https://developer.wordpress.org/reference/functions/single_cat_title)
*   [the\_category()](https://developer.wordpress.org/reference/functions/the_category)
*   [the\_category\_rss()](https://developer.wordpress.org/reference/functions/the_category_rss)
*   [wp\_dropdown\_categories()](https://developer.wordpress.org/reference/functions/wp_dropdown_categories)
*   [wp\_list\_categories()](https://developer.wordpress.org/reference/functions/wp_list_categories/)
*   [single\_tag\_title()](https://developer.wordpress.org/reference/functions/single_tag_title)
*   [tag\_description()](https://developer.wordpress.org/reference/functions/tag_description)
*   [the\_tags()](https://developer.wordpress.org/reference/functions/the_tags)
*   [wp\_generate\_tag\_cloud()](https://developer.wordpress.org/reference/functions/wp_generate_tag_cloud)
*   [wp\_tag\_cloud()](https://developer.wordpress.org/reference/functions/wp_tag_cloud)
*   [term\_description()](https://developer.wordpress.org/reference/functions/term_description)
*   [single\_term\_title()](https://developer.wordpress.org/reference/functions/single_term_title)
*   [get\_the\_term\_list()](https://developer.wordpress.org/reference/functions/get_the_term_list)
*   [the\_terms()](https://developer.wordpress.org/reference/functions/the_terms)
*   [the\_taxonomies()](https://developer.wordpress.org/reference/functions/the_taxonomies)
 -->

*   [`category_description()`](https://developer.wordpress.org/reference/functions/category_description)
*   [`single_cat_title()`](https://developer.wordpress.org/reference/functions/single_cat_title)
*   [`the_category()`](https://developer.wordpress.org/reference/functions/the_category)
*   [`the_category_rss()`](https://developer.wordpress.org/reference/functions/the_category_rss)
*   [`wp_dropdown_categories()`](https://developer.wordpress.org/reference/functions/wp_dropdown_categories)
*   [`wp_list_categories()`](https://developer.wordpress.org/reference/functions/wp_list_categories/)
*   [`single_tag_title()`](https://developer.wordpress.org/reference/functions/single_tag_title)
*   [`tag_description()`](https://developer.wordpress.org/reference/functions/tag_description)
*   [`the_tags()`](https://developer.wordpress.org/reference/functions/the_tags)
*   [`wp_generate_tag_cloud()`](https://developer.wordpress.org/reference/functions/wp_generate_tag_cloud)
*   [`wp_tag_cloud()`](https://developer.wordpress.org/reference/functions/wp_tag_cloud)
*   [`term_description()`](https://developer.wordpress.org/reference/functions/term_description)
*   [`single_term_title()`](https://developer.wordpress.org/reference/functions/single_term_title)
*   [`get_the_term_list()`](https://developer.wordpress.org/reference/functions/get_the_term_list)
*   [`the_terms()`](https://developer.wordpress.org/reference/functions/the_terms)
*   [`the_taxonomies()`](https://developer.wordpress.org/reference/functions/the_taxonomies)

<!-- 
### Comment tags
 -->

### 「コメント」タグ

<!-- 
`[wp-includes/comment-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/comment-template.php#L0)`
 -->

[`wp-includes/comment-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/comment-template.php#L0)

<!-- 
*   [cancel\_comment\_reply\_link()](https://developer.wordpress.org/reference/functions/cancel_comment_reply_link)
*   [comment\_author()](https://developer.wordpress.org/reference/functions/comment_author)
*   [comment\_author\_email()](https://developer.wordpress.org/reference/functions/comment_author_email)
*   [comment\_author\_email\_link()](https://developer.wordpress.org/reference/functions/comment_author_email_link)
*   [comment\_author\_IP()](https://developer.wordpress.org/reference/functions/comment_author_IP)
*   [comment\_author\_link()](https://developer.wordpress.org/reference/functions/comment_author_link)
*   [comment\_author\_rss()](https://developer.wordpress.org/reference/functions/comment_author_rss)
*   [comment\_author\_url()](https://developer.wordpress.org/reference/functions/comment_author_url)
*   [comment\_author\_url\_link()](https://developer.wordpress.org/reference/functions/comment_author_url_link)
*   [comment\_class()](https://developer.wordpress.org/reference/functions/comment_class)
*   [comment\_date()](https://developer.wordpress.org/reference/functions/comment_date)
*   [comment\_excerpt()](https://developer.wordpress.org/reference/functions/comment_excerpt)
*   [comment\_form\_title()](https://developer.wordpress.org/reference/functions/comment_form_title)
*   [comment\_form()](https://developer.wordpress.org/reference/functions/comment_form)
*   [comment\_ID()](https://developer.wordpress.org/reference/functions/comment_ID)
*   [comment\_id\_fields()](https://developer.wordpress.org/reference/functions/comment_id_fields)
*   [comment\_reply\_link()](https://developer.wordpress.org/reference/functions/comment_reply_link)
*   [comment\_text()](https://developer.wordpress.org/reference/functions/comment_text)
*   [comment\_text\_rss()](https://developer.wordpress.org/reference/functions/comment_text_rss)
*   [comment\_time()](https://developer.wordpress.org/reference/functions/comment_time)
*   [comment\_type()](https://developer.wordpress.org/reference/functions/comment_type)
*   [comments\_link()](https://developer.wordpress.org/reference/functions/comments_link)
*   [comments\_number()](https://developer.wordpress.org/reference/functions/comments_number)
*   [comments\_popup\_link()](https://developer.wordpress.org/reference/functions/comments_popup_link)
*   [get\_avatar()](https://developer.wordpress.org/reference/functions/get_avatar)
*   [next\_comments\_link()](https://developer.wordpress.org/reference/functions/next_comments_link)
*   [paginate\_comments\_links()](https://developer.wordpress.org/reference/functions/paginate_comments_links)
*   [permalink\_comments\_rss()](https://developer.wordpress.org/reference/functions/permalink_comments_rss)
*   [previous\_comments\_link()](https://developer.wordpress.org/reference/functions/previous_comments_link)
*   [wp\_list\_comments()](https://developer.wordpress.org/reference/functions/wp_list_comments)
 -->

*   [`cancel_comment_reply_link()`](https://developer.wordpress.org/reference/functions/cancel_comment_reply_link)
*   [`comment_author()`](https://developer.wordpress.org/reference/functions/comment_author)
*   [`comment_author_email()`](https://developer.wordpress.org/reference/functions/comment_author_email)
*   [`comment_author_email_link()`](https://developer.wordpress.org/reference/functions/comment_author_email_link)
*   [`comment_author_IP()`](https://developer.wordpress.org/reference/functions/comment_author_IP)
*   [`comment_author_link()`](https://developer.wordpress.org/reference/functions/comment_author_link)
*   [`comment_author_rss()`](https://developer.wordpress.org/reference/functions/comment_author_rss)
*   [`comment_author_url()`](https://developer.wordpress.org/reference/functions/comment_author_url)
*   [`comment_author_url_link()`](https://developer.wordpress.org/reference/functions/comment_author_url_link)
*   [`comment_class()`](https://developer.wordpress.org/reference/functions/comment_class)
*   [`comment_date()`](https://developer.wordpress.org/reference/functions/comment_date)
*   [`comment_excerpt()`](https://developer.wordpress.org/reference/functions/comment_excerpt)
*   [`comment_form_title()`](https://developer.wordpress.org/reference/functions/comment_form_title)
*   [`comment_form()`](https://developer.wordpress.org/reference/functions/comment_form)
*   [`comment_ID()`](https://developer.wordpress.org/reference/functions/comment_ID)
*   [`comment_id_fields()`](https://developer.wordpress.org/reference/functions/comment_id_fields)
*   [`comment_reply_link()`](https://developer.wordpress.org/reference/functions/comment_reply_link)
*   [`comment_text()`](https://developer.wordpress.org/reference/functions/comment_text)
*   [`comment_text_rss()`](https://developer.wordpress.org/reference/functions/comment_text_rss)
*   [`comment_time()`](https://developer.wordpress.org/reference/functions/comment_time)
*   [`comment_type()`](https://developer.wordpress.org/reference/functions/comment_type)
*   [`comments_link()`](https://developer.wordpress.org/reference/functions/comments_link)
*   [`comments_number()`](https://developer.wordpress.org/reference/functions/comments_number)
*   [`comments_popup_link()`](https://developer.wordpress.org/reference/functions/comments_popup_link)
*   [`get_avatar()`](https://developer.wordpress.org/reference/functions/get_avatar)
*   [`next_comments_link()`](https://developer.wordpress.org/reference/functions/next_comments_link)
*   [`paginate_comments_links()`](https://developer.wordpress.org/reference/functions/paginate_comments_links)
*   [`permalink_comments_rss()`](https://developer.wordpress.org/reference/functions/permalink_comments_rss)
*   [`previous_comments_link()`](https://developer.wordpress.org/reference/functions/previous_comments_link)
*   [`wp_list_comments()`](https://developer.wordpress.org/reference/functions/wp_list_comments)

<!-- 
### Link tags
 -->

### 「リンク」タグ

<!-- 
`[wp-includes/link-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/link-template.php#L0)`
 -->

[`wp-includes/link-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/link-template.php#L0)

<!-- 
*   [the\_permalink()](https://developer.wordpress.org/reference/functions/the_permalink)
*   [user\_trailingslashit()](https://developer.wordpress.org/reference/functions/user_trailingslashit)
*   [permalink\_anchor()](https://developer.wordpress.org/reference/functions/permalink_anchor)
*   [get\_permalink()](https://developer.wordpress.org/reference/functions/get_permalink)
*   [get\_post\_permalink()](https://developer.wordpress.org/reference/functions/get_post_permalink)
*   [get\_page\_link()](https://developer.wordpress.org/reference/functions/get_page_link)
*   [get\_attachment\_link()](https://developer.wordpress.org/reference/functions/get_attachment_link)
*   [wp\_shortlink\_header()](https://developer.wordpress.org/reference/functions/wp_shortlink_header/)
*   [wp\_shortlink\_wp\_head()](https://developer.wordpress.org/reference/functions/wp_shortlink_wp_head/)
*   [edit\_bookmark\_link()](https://developer.wordpress.org/reference/functions/edit_bookmark_link)
*   [edit\_comment\_link()](https://developer.wordpress.org/reference/functions/edit_comment_link)
*   [edit\_post\_link()](https://developer.wordpress.org/reference/functions/edit_post_link)
*   [get\_edit\_post\_link()](https://developer.wordpress.org/reference/functions/get_edit_post_link/)
*   [get\_delete\_post\_link()](https://developer.wordpress.org/reference/functions/get_delete_post_link)
*   [edit\_tag\_link()](https://developer.wordpress.org/reference/functions/edit_tag_link)
*   [get\_admin\_url()](https://developer.wordpress.org/reference/functions/get_admin_url)
*   [get\_home\_url()](https://developer.wordpress.org/reference/functions/get_home_url)
*   [get\_site\_url()](https://developer.wordpress.org/reference/functions/get_site_url)
*   [home\_url()](https://developer.wordpress.org/reference/functions/home_url)
*   [site\_url()](https://developer.wordpress.org/reference/functions/site_url)
*   [get\_search\_link()](https://developer.wordpress.org/reference/functions/get_search_link)
*   [get\_search\_query()](https://developer.wordpress.org/reference/functions/get_search_query)
*   [the\_feed\_link()](https://developer.wordpress.org/reference/functions/the_feed_link)
*   [the\_privacy\_policy\_link()](https://developer.wordpress.org/reference/functions/the_privacy_policy_link/)
*   [get\_the\_privacy\_policy\_link()](https://developer.wordpress.org/reference/functions/get_the_privacy_policy_link/)
 -->

*   [`the_permalink()`](https://developer.wordpress.org/reference/functions/the_permalink)
*   [`user_trailingslashit()`](https://developer.wordpress.org/reference/functions/user_trailingslashit)
*   [`permalink_anchor()`](https://developer.wordpress.org/reference/functions/permalink_anchor)
*   [`get_permalink()`](https://developer.wordpress.org/reference/functions/get_permalink)
*   [`get_post_permalink()`](https://developer.wordpress.org/reference/functions/get_post_permalink)
*   [`get_page_link()`](https://developer.wordpress.org/reference/functions/get_page_link)
*   [`get_attachment_link()`](https://developer.wordpress.org/reference/functions/get_attachment_link)
*   [`wp_shortlink_header()`](https://developer.wordpress.org/reference/functions/wp_shortlink_header/)
*   [`wp_shortlink_wp_head()`](https://developer.wordpress.org/reference/functions/wp_shortlink_wp_head/)
*   [`edit_bookmark_link()`](https://developer.wordpress.org/reference/functions/edit_bookmark_link)
*   [`edit_comment_link()`](https://developer.wordpress.org/reference/functions/edit_comment_link)
*   [`edit_post_link()`](https://developer.wordpress.org/reference/functions/edit_post_link)
*   [`get_edit_post_link()`](https://developer.wordpress.org/reference/functions/get_edit_post_link/)
*   [`get_delete_post_link()`](https://developer.wordpress.org/reference/functions/get_delete_post_link)
*   [`edit_tag_link()`](https://developer.wordpress.org/reference/functions/edit_tag_link)
*   [`get_admin_url()`](https://developer.wordpress.org/reference/functions/get_admin_url)
*   [`get_home_url()`](https://developer.wordpress.org/reference/functions/get_home_url)
*   [`get_site_url()`](https://developer.wordpress.org/reference/functions/get_site_url)
*   [`home_url()`](https://developer.wordpress.org/reference/functions/home_url)
*   [`site_url()`](https://developer.wordpress.org/reference/functions/site_url)
*   [`get_search_link()`](https://developer.wordpress.org/reference/functions/get_search_link)
*   [`get_search_query()`](https://developer.wordpress.org/reference/functions/get_search_query)
*   [`the_feed_link()`](https://developer.wordpress.org/reference/functions/the_feed_link)
*   [`the_privacy_policy_link()`](https://developer.wordpress.org/reference/functions/the_privacy_policy_link/)
*   [`get_the_privacy_policy_link()`](https://developer.wordpress.org/reference/functions/get_the_privacy_policy_link/)

<!-- 
### Post tags
 -->

### 「投稿」タグ

<!-- 
`[wp-includes/post-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/post-template.php#L0)`
 -->

[`wp-includes/post-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/post-template.php#L0)

<!-- 
*   [body\_class()](https://developer.wordpress.org/reference/functions/body_class)
*   [next\_image\_link()](https://developer.wordpress.org/reference/functions/next_image_link)
*   [next\_post\_link()](https://developer.wordpress.org/reference/functions/next_post_link)
*   [next\_posts\_link()](https://developer.wordpress.org/reference/functions/next_posts_link)
*   [post\_class()](https://developer.wordpress.org/reference/functions/post_class)
*   [post\_password\_required()](https://developer.wordpress.org/reference/functions/post_password_required)
*   [posts\_nav\_link()](https://developer.wordpress.org/reference/functions/posts_nav_link)
*   [previous\_image\_link()](https://developer.wordpress.org/reference/functions/previous_image_link)
*   [previous\_post\_link()](https://developer.wordpress.org/reference/functions/previous_post_link)
*   [previous\_posts\_link()](https://developer.wordpress.org/reference/functions/previous_posts_link)
*   [single\_post\_title()](https://developer.wordpress.org/reference/functions/single_post_title)
*   [the\_category()](https://developer.wordpress.org/reference/functions/the_category)
*   [the\_category\_rss()](https://developer.wordpress.org/reference/functions/the_category_rss)
*   [the\_content()](https://developer.wordpress.org/reference/functions/the_content)
*   [the\_excerpt()](https://developer.wordpress.org/reference/functions/the_excerpt)
*   [the\_excerpt\_rss()](https://developer.wordpress.org/reference/functions/the_excerpt_rss)
*   [the\_ID()](https://developer.wordpress.org/reference/functions/the_ID)
*   [the\_meta()](https://developer.wordpress.org/reference/functions/the_meta)
*   [the\_tags()](https://developer.wordpress.org/reference/functions/the_tags)
*   [the\_title()](https://developer.wordpress.org/reference/functions/the_title)
*   [get\_the\_title()](https://developer.wordpress.org/reference/functions/get_the_title)
*   [the\_title\_attribute()](https://developer.wordpress.org/reference/functions/the_title_attribute)
*   [the\_title\_rss()](https://developer.wordpress.org/reference/functions/the_title_rss)
*   [wp\_link\_pages()](https://developer.wordpress.org/reference/functions/wp_link_pages)
*   [get\_attachment\_link()](https://developer.wordpress.org/reference/functions/get_attachment_link)
*   [wp\_get\_attachment\_link()](https://developer.wordpress.org/reference/functions/wp_get_attachment_link)
*   [the\_attachment\_link()](https://developer.wordpress.org/reference/functions/the_attachment_link)
*   [the\_search\_query()](https://developer.wordpress.org/reference/functions/the_search_query)
*   [is\_attachment()](https://developer.wordpress.org/reference/functions/is_attachment)
*   [wp\_attachment\_is\_image()](https://developer.wordpress.org/reference/functions/wp_attachment_is_image)
*   [wp\_get\_attachment\_image()](https://developer.wordpress.org/reference/functions/wp_get_attachment_image)
*   [wp\_get\_attachment\_image\_src()](https://developer.wordpress.org/reference/functions/wp_get_attachment_image_src)
*   [wp\_get\_attachment\_metadata()](https://developer.wordpress.org/reference/functions/wp_get_attachment_metadata)
*   [get\_the\_date()](https://developer.wordpress.org/reference/functions/get_the_date)
*   [single\_month\_title()](https://developer.wordpress.org/reference/functions/single_month_title)
*   [the\_date()](https://developer.wordpress.org/reference/functions/the_date)
*   [the\_date\_xml()](https://developer.wordpress.org/reference/functions/the_date_xml)
*   [the\_modified\_author()](https://developer.wordpress.org/reference/functions/the_modified_author)
*   [the\_modified\_date()](https://developer.wordpress.org/reference/functions/the_modified_date)
*   [the\_modified\_time()](https://developer.wordpress.org/reference/functions/the_modified_time)
*   [the\_time()](https://developer.wordpress.org/reference/functions/the_time)
*   [the\_shortlink()](https://developer.wordpress.org/reference/functions/the_shortlink)
*   [wp\_get\_shortlink()](https://developer.wordpress.org/reference/functions/wp_get_shortlink)
 -->

*   [`body_class()`](https://developer.wordpress.org/reference/functions/body_class)
*   [`next_image_link()`](https://developer.wordpress.org/reference/functions/next_image_link)
*   [`next_post_link()`](https://developer.wordpress.org/reference/functions/next_post_link)
*   [`next_posts_link()`](https://developer.wordpress.org/reference/functions/next_posts_link)
*   [`post_class()`](https://developer.wordpress.org/reference/functions/post_class)
*   [`post_password_required()`](https://developer.wordpress.org/reference/functions/post_password_required)
*   [`posts_nav_link()`](https://developer.wordpress.org/reference/functions/posts_nav_link)
*   [`previous_image_link()`](https://developer.wordpress.org/reference/functions/previous_image_link)
*   [`previous_post_link()`](https://developer.wordpress.org/reference/functions/previous_post_link)
*   [`previous_posts_link()`](https://developer.wordpress.org/reference/functions/previous_posts_link)
*   [`single_post_title()`](https://developer.wordpress.org/reference/functions/single_post_title)
*   [`the_category()`](https://developer.wordpress.org/reference/functions/the_category)
*   [`the_category_rss()`](https://developer.wordpress.org/reference/functions/the_category_rss)
*   [`the_content()`](https://developer.wordpress.org/reference/functions/the_content)
*   [`the_excerpt()`](https://developer.wordpress.org/reference/functions/the_excerpt)
*   [`the_excerpt_rss()`](https://developer.wordpress.org/reference/functions/the_excerpt_rss)
*   [`the_ID()`](https://developer.wordpress.org/reference/functions/the_ID)
*   [`the_meta()`](https://developer.wordpress.org/reference/functions/the_meta)
*   [`the_tags()`](https://developer.wordpress.org/reference/functions/the_tags)
*   [`the_title()`](https://developer.wordpress.org/reference/functions/the_title)
*   [`get_the_title()`](https://developer.wordpress.org/reference/functions/get_the_title)
*   [`the_title_attribute()`](https://developer.wordpress.org/reference/functions/the_title_attribute)
*   [`the_title_rss()`](https://developer.wordpress.org/reference/functions/the_title_rss)
*   [`wp_link_pages()`](https://developer.wordpress.org/reference/functions/wp_link_pages)
*   [`get_attachment_link()`](https://developer.wordpress.org/reference/functions/get_attachment_link)
*   [`wp_get_attachment_link()`](https://developer.wordpress.org/reference/functions/wp_get_attachment_link)
*   [`the_attachment_link()`](https://developer.wordpress.org/reference/functions/the_attachment_link)
*   [`the_search_query()`](https://developer.wordpress.org/reference/functions/the_search_query)
*   [`is_attachment()`](https://developer.wordpress.org/reference/functions/is_attachment)
*   [`wp_attachment_is_image()`](https://developer.wordpress.org/reference/functions/wp_attachment_is_image)
*   [`wp_get_attachment_image()`](https://developer.wordpress.org/reference/functions/wp_get_attachment_image)
*   [`wp_get_attachment_image_src()`](https://developer.wordpress.org/reference/functions/wp_get_attachment_image_src)
*   [`wp_get_attachment_metadata()`](https://developer.wordpress.org/reference/functions/wp_get_attachment_metadata)
*   [`get_the_date()`](https://developer.wordpress.org/reference/functions/get_the_date)
*   [`single_month_title()`](https://developer.wordpress.org/reference/functions/single_month_title)
*   [`the_date()`](https://developer.wordpress.org/reference/functions/the_date)
*   [`the_date_xml()`](https://developer.wordpress.org/reference/functions/the_date_xml)
*   [`the_modified_author()`](https://developer.wordpress.org/reference/functions/the_modified_author)
*   [`the_modified_date()`](https://developer.wordpress.org/reference/functions/the_modified_date)
*   [`the_modified_time()`](https://developer.wordpress.org/reference/functions/the_modified_time)
*   [`the_time()`](https://developer.wordpress.org/reference/functions/the_time)
*   [`the_shortlink()`](https://developer.wordpress.org/reference/functions/the_shortlink)
*   [`wp_get_shortlink()`](https://developer.wordpress.org/reference/functions/wp_get_shortlink)

<!-- 
### Post Thumbnail tags
 -->

### 「投稿サムネイル」タグ

<!-- 
`[wp-includes/post-thumbnail-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/post-thumbnail-template.php#L0)`
 -->

[`wp-includes/post-thumbnail-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/post-thumbnail-template.php#L0)

<!-- 
*   [has\_post\_thumbnail()](https://developer.wordpress.org/reference/functions/has_post_thumbnail)
*   [get\_post\_thumbnail\_id()](https://developer.wordpress.org/reference/functions/get_post_thumbnail_id)
*   [the\_post\_thumbnail()](https://developer.wordpress.org/reference/functions/the_post_thumbnail)
*   [get\_the\_post\_thumbnail()](https://developer.wordpress.org/reference/functions/get_the_post_thumbnail)
 -->

*   [`has_post_thumbnail()`](https://developer.wordpress.org/reference/functions/has_post_thumbnail)
*   [`get_post_thumbnail_id()`](https://developer.wordpress.org/reference/functions/get_post_thumbnail_id)
*   [`the_post_thumbnail()`](https://developer.wordpress.org/reference/functions/the_post_thumbnail)
*   [`get_the_post_thumbnail()`](https://developer.wordpress.org/reference/functions/get_the_post_thumbnail)

<!-- 
### Navigation Menu tags
 -->

### 「ナビゲーションメニュー」タグ

<!-- 
`[wp-includes/nav-menu-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/nav-menu-template.php#L0)`
 -->

[`wp-includes/nav-menu-template.php`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/nav-menu-template.php#L0)

<!-- 
*   [wp\_nav\_menu()](https://developer.wordpress.org/reference/functions/wp_nav_menu)
*   [walk\_nav\_menu\_tree()](https://developer.wordpress.org/reference/functions/walk_nav_menu_tree/)
 -->

*   [`wp_nav_menu()`](https://developer.wordpress.org/reference/functions/wp_nav_menu)
*   [`walk_nav_menu_tree()`](https://developer.wordpress.org/reference/functions/walk_nav_menu_tree/)

<!-- 
## See Also
 -->

## 関連項目

<!-- 
*   [Conditional Tags](https://developer.wordpress.org/themes/basics/conditional-tags/) -->

*   [条件付きタグ](https://developer.wordpress.org/themes/basics/conditional-tags/)