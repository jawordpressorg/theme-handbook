# List of Template Tags

## Complete List of Template Tags

Template tags files are stored in the `[wp-includes](https://core.trac.wordpress.org/browser/trunk/src/wp-includes)` directory. The files have the suffix of “-template.php” to distinguish them from other WordPress files. There are 9 template tags files:

*   `[wp-includes/general-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/general-template.php#L0)`
*   `[wp-includes/author-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/author-template.php#L0)`
*   `[wp-includes/bookmark-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/bookmark-template.php#L0)`
*   `[wp-includes/category-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/category-template.php#L0)`
*   `[wp-includes/comment-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/comment-template.php#L0)`
*   `[wp-includes/link-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/link-template.php#L0)`
*   `[wp-includes/post-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/post-template.php#L0)`
*   `[wp-includes/post-thumbnail-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/post-thumbnail-template.php#L0)`
*   `[wp-includes/nav-menu-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/nav-menu-template.php#L0)`

## Tags

### General tags

`[wp-includes/general-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/general-template.php#L0)`

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

### Author tags

`[wp-includes/author-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/author-template.php#L0)`

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

### Bookmark tags

`[wp-includes/bookmark-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/bookmark-template.php#L0)` and `[wp-includes/bookmark.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/bookmark.php#L0)`

*   [wp\_list\_bookmarks()](https://developer.wordpress.org/reference/functions/wp_list_bookmarks)
*   [get\_bookmark()](https://developer.wordpress.org/reference/functions/get_bookmark)
*   [get\_bookmark\_field()](https://developer.wordpress.org/reference/functions/get_bookmark_field)
*   [get\_bookmarks()](https://developer.wordpress.org/reference/functions/get_bookmarks)

### Category tags

`[wp-includes/category-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/category-template.php#L0)`

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

### Comment tags

`[wp-includes/comment-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/comment-template.php#L0)`

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

### Link tags

`[wp-includes/link-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/link-template.php#L0)`

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

### Post tags

`[wp-includes/post-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/post-template.php#L0)`

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

### Post Thumbnail tags

`[wp-includes/post-thumbnail-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/post-thumbnail-template.php#L0)`

*   [has\_post\_thumbnail()](https://developer.wordpress.org/reference/functions/has_post_thumbnail)
*   [get\_post\_thumbnail\_id()](https://developer.wordpress.org/reference/functions/get_post_thumbnail_id)
*   [the\_post\_thumbnail()](https://developer.wordpress.org/reference/functions/the_post_thumbnail)
*   [get\_the\_post\_thumbnail()](https://developer.wordpress.org/reference/functions/get_the_post_thumbnail)

### Navigation Menu tags

`[wp-includes/nav-menu-template.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/nav-menu-template.php#L0)`

*   [wp\_nav\_menu()](https://developer.wordpress.org/reference/functions/wp_nav_menu)
*   [walk\_nav\_menu\_tree()](https://developer.wordpress.org/reference/functions/walk_nav_menu_tree/)

## See Also

*   [Conditional Tags](https://developer.wordpress.org/themes/basics/conditional-tags/)