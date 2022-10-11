# List of Conditional Tags

Conditional Tags are a boolean data type that can be used in your Template Files to alter the display of content depending on the conditions that the current page matches. They tell WordPress what code to display under specific conditions. Conditional Tags usually work with PHP [if](http://php.net/manual/en/control-structures.if.php "PHP if conditional") /[else](http://php.net/manual/en/control-structures.else.php "PHP else conditional") Conditional Statements and have close relation with WOrdPress [Template Hierarchy](https://codex.wordpress.org/Template_Hierarchy "Template Hierarchy"). .

**Warning: You can only use conditional query tags after the [WP\_Query](https://developer.wordpress.org/reference/classes/wp_query/) is set up or  with [action hook](https://codex.wordpress.org/Plugin_API/Action_Reference#Actions_Run_During_a_Typical_Request "Plugin API/Action Reference").**

## Complete List of Conditional Tags

*   [](https://codex.wordpress.org/Function_Reference/is_front_page "Function Reference/is front page")[is\_front\_page()](https://developer.wordpress.org/reference/functions/is_front_page/)
*   [](https://codex.wordpress.org/Function_Reference/is_home "Function Reference/is home")[is\_home()](https://developer.wordpress.org/reference/functions/is_home/)
*   [](https://codex.wordpress.org/Function_Reference/is_front_page "Function Reference/is front page")[is\_front\_page()](https://developer.wordpress.org/reference/functions/is_front_page/)
*   [](https://codex.wordpress.org/Function_Reference/is_home "Function Reference/is home")[is\_home()](https://developer.wordpress.org/reference/functions/is_home/)
*   [](https://codex.wordpress.org/Function_Reference/is_admin "Function Reference/is admin")[is\_admin()](https://developer.wordpress.org/reference/functions/is_admin/)
*   [](https://codex.wordpress.org/Function_Reference/is_network_admin "Function Reference/is network admin")[is\_network\_admin()](https://developer.wordpress.org/reference/functions/is_network_admin/)
*   [](https://codex.wordpress.org/Function_Reference/is_admin_bar_showing "Function Reference/is admin bar showing")[is\_admin\_bar\_showing()](https://developer.wordpress.org/reference/functions/is_admin_bar_showing/)
*   [](https://codex.wordpress.org/Function_Reference/is_single "Function Reference/is single")[is\_single()](https://developer.wordpress.org/reference/functions/is_single/)
*   [](https://codex.wordpress.org/Function_Reference/is_sticky "Function Reference/is sticky")[is\_sticky()](https://developer.wordpress.org/reference/functions/is_sticky/)
*   [is\_post\_type\_hierarchical( $post\_type )](https://codex.wordpress.org/Function_Reference/is_post_type_hierarchical "Function Reference/is post type hierarchical")
*   [](https://codex.wordpress.org/Function_Reference/is_post_type_archive "Function Reference/is post type archive")[is\_post\_type\_archive()](https://developer.wordpress.org/reference/functions/is_post_type_archive/)
*   [](https://codex.wordpress.org/Function_Reference/is_comments_popup "Function Reference/is comments popup")[is\_comments\_popup()](https://developer.wordpress.org/reference/functions/is_comments_popup/)
*   [](https://codex.wordpress.org/Function_Reference/comments_open "Function Reference/comments open")[comments\_open()](https://developer.wordpress.org/reference/functions/comments_open/)
*   [](https://codex.wordpress.org/Function_Reference/pings_open "Function Reference/pings open")[pings\_open()](https://developer.wordpress.org/reference/functions/pings_open/)
*   [](https://codex.wordpress.org/Function_Reference/is_page "Function Reference/is page")[is\_page()](https://developer.wordpress.org/reference/functions/is_page/)
*   [](https://codex.wordpress.org/Function_Reference/is_page_template "Function Reference/is page template")[is\_page\_template()](https://developer.wordpress.org/reference/functions/is_page_template/)
*   [is\_category( $category )](https://codex.wordpress.org/Function_Reference/is_category "Function Reference/is category")
*   [](https://codex.wordpress.org/Function_Reference/is_tag "Function Reference/is tag")[is\_tag()](https://developer.wordpress.org/reference/functions/is_tag/)
*   [](https://codex.wordpress.org/Function_Reference/is_tax "Function Reference/is tax")[is\_tax()](https://developer.wordpress.org/reference/functions/is_tax/)
*   [](https://codex.wordpress.org/Function_Reference/has_term "Function Reference/has term")[has\_term()](https://developer.wordpress.org/reference/functions/has_term/)
*   [term\_exists( $term, $taxonomy, $parent )](https://codex.wordpress.org/Function_Reference/term_exists "Function Reference/term exists")
*   [is\_taxonomy\_hierarchical( $taxonomy )](https://codex.wordpress.org/Function_Reference/is_taxonomy_hierarchical "Function Reference/is taxonomy hierarchical")
*   [taxonomy\_exists( $taxonomy )](https://codex.wordpress.org/Function_Reference/taxonomy_exists "Function Reference/taxonomy exists")
*   [](https://codex.wordpress.org/Function_Reference/is_author "Function Reference/is author")[is\_author()](https://developer.wordpress.org/reference/functions/is_author/)
*   [](https://codex.wordpress.org/Function_Reference/is_date "Function Reference/is date")[is\_date()](https://developer.wordpress.org/reference/functions/is_date/)
*   [](https://codex.wordpress.org/Function_Reference/is_year "Function Reference/is year")[is\_year()](https://developer.wordpress.org/reference/functions/is_year/)
*   [](https://codex.wordpress.org/Function_Reference/is_month "Function Reference/is month")[is\_month()](https://developer.wordpress.org/reference/functions/is_month/)
*   [](https://codex.wordpress.org/Function_Reference/is_day "Function Reference/is day")[is\_day()](https://developer.wordpress.org/reference/functions/is_day/)
*   [](https://codex.wordpress.org/Function_Reference/is_time "Function Reference/is time")[is\_time()](https://developer.wordpress.org/reference/functions/is_time/)
*   [](https://codex.wordpress.org/Function_Reference/is_new_day "Function Reference/is new day")[is\_new\_day()](https://developer.wordpress.org/reference/functions/is_new_day/)
*   [](https://codex.wordpress.org/Function_Reference/is_archive "Function Reference/is archive")[is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/)
*   [](https://codex.wordpress.org/Function_Reference/is_search "Function Reference/is search")[is\_search()](https://developer.wordpress.org/reference/functions/is_search/)
*   [](https://codex.wordpress.org/Function_Reference/is_404 "Function Reference/is 404")[is\_404()](https://developer.wordpress.org/reference/functions/is_404/)
*   [](https://codex.wordpress.org/Function_Reference/is_paged "Function Reference/is paged")[is\_paged()](https://developer.wordpress.org/reference/functions/is_paged/)
*   [](https://codex.wordpress.org/Function_Reference/is_attachment "Function Reference/is attachment")[is\_attachment()](https://developer.wordpress.org/reference/functions/is_attachment/)
*   [wp\_attachment\_is\_image( $post\_id )](https://codex.wordpress.org/Function_Reference/wp_attachment_is_image "Function Reference/wp attachment is image")
*   [is\_local\_attachment( $url )](https://codex.wordpress.org/Function_Reference/is_local_attachment "Function Reference/is local attachment")
*   [](https://codex.wordpress.org/Function_Reference/is_singular "Function Reference/is singular")[is\_singular()](https://developer.wordpress.org/reference/functions/is_singular/)
*   [post\_type\_exists( $post\_type )](https://codex.wordpress.org/Function_Reference/post_type_exists "Function Reference/post type exists")
*   [](https://codex.wordpress.org/Function_Reference/is_main_query "Function Reference/is main query")[is\_main\_query()](https://developer.wordpress.org/reference/functions/is_main_query/)
*   [](https://codex.wordpress.org/Function_Reference/is_new_day "Function Reference/is new day")[is\_new\_day()](https://developer.wordpress.org/reference/functions/is_new_day/)
*   [](https://codex.wordpress.org/Function_Reference/is_feed "Function Reference/is feed")[is\_feed()](https://developer.wordpress.org/reference/functions/is_feed/)
*   [](https://codex.wordpress.org/Function_Reference/is_trackback "Function Reference/is trackback")[is\_trackback()](https://developer.wordpress.org/reference/functions/is_trackback/)
*   [](https://codex.wordpress.org/Function_Reference/is_preview "Function Reference/is preview")[is\_preview()](https://developer.wordpress.org/reference/functions/is_preview/)
*   [](https://codex.wordpress.org/Function_Reference/in_the_loop "Function Reference/in the loop")[in\_the\_loop()](https://developer.wordpress.org/reference/functions/in_the_loop/)
*   [](https://codex.wordpress.org/Function_Reference/is_dynamic_sidebar "Function Reference/is dynamic sidebar")[is\_dynamic\_sidebar()](https://developer.wordpress.org/reference/functions/is_dynamic_sidebar/)
*   [](https://codex.wordpress.org/Function_Reference/is_active_sidebar "Function Reference/is active sidebar")[is\_active\_sidebar()](https://developer.wordpress.org/reference/functions/is_active_sidebar/)
*   [is\_active\_widget( $widget\_callback, $widget\_id )](https://codex.wordpress.org/Function_Reference/is_active_widget "Function Reference/is active widget")
*   [](https://codex.wordpress.org/Function_Reference/is_blog_installed "Function Reference/is blog installed")[is\_blog\_installed()](https://developer.wordpress.org/reference/functions/is_blog_installed/)
*   [](https://codex.wordpress.org/Function_Reference/is_rtl "Function Reference/is rtl")[is\_rtl()](https://developer.wordpress.org/reference/functions/is_rtl/)
*   [](https://codex.wordpress.org/Function_Reference/is_multisite "Function Reference/is multisite")[is\_multisite()](https://developer.wordpress.org/reference/functions/is_multisite/)
*   [](https://codex.wordpress.org/Function_Reference/is_main_site "Function Reference/is main site")[is\_main\_site()](https://developer.wordpress.org/reference/functions/is_main_site/)
*   [](https://codex.wordpress.org/Function_Reference/is_super_admin "Function Reference/is super admin")[is\_super\_admin()](https://developer.wordpress.org/reference/functions/is_super_admin/)
*   [](https://codex.wordpress.org/Function_Reference/is_user_logged_in "Function Reference/is user logged in")[is\_user\_logged\_in()](https://developer.wordpress.org/reference/functions/is_user_logged_in/)
*   [email\_exists( $email )](https://codex.wordpress.org/Function_Reference/email_exists "Function Reference/email exists")
*   [username\_exists( $username )](https://codex.wordpress.org/Function_Reference/username_exists "Function Reference/username exists")
*   [is\_plugin\_active( $path )](https://codex.wordpress.org/Function_Reference/is_plugin_active "Function Reference/is plugin active")
*   [is\_plugin\_inactive( $path )](https://codex.wordpress.org/Function_Reference/is_plugin_inactive "Function Reference/is plugin inactive")
*   [is\_plugin\_active\_for\_network( $path )](https://codex.wordpress.org/Function_Reference/is_plugin_active_for_network "Function Reference/is plugin active for network")
*   [](https://codex.wordpress.org/Function_Reference/is_plugin_page "Function Reference/is plugin page")[is\_plugin\_page()](https://developer.wordpress.org/reference/functions/is_plugin_page/)
*   [](https://codex.wordpress.org/Function_Reference/is_child_theme "Function Reference/is child theme")[is\_child\_theme()](https://developer.wordpress.org/reference/functions/is_child_theme/)
*   [](https://codex.wordpress.org/Function_Reference/current_theme_supports "Function Reference/current theme supports")[current\_theme\_supports()](https://developer.wordpress.org/reference/functions/current_theme_supports/)
*   [has\_post\_thumbnail( $post\_id )](https://codex.wordpress.org/Function_Reference/has_post_thumbnail "Function Reference/has post thumbnail")
*   [wp\_script\_is( $handle, $list )](https://codex.wordpress.org/Function_Reference/wp_script_is "Function Reference/wp script is")

## The Conditions For …

All of the Conditional Tags test to see whether a certain condition is met, and then returns either TRUE or FALSE. The conditions under which various tags output TRUE is listed below. Those tags which can accept parameters are so noted.

### The Main Page

*   [](https://codex.wordpress.org/Function_Reference/is_home "Function Reference/is home")[is\_home()](https://developer.wordpress.org/reference/functions/is_home/)

### The Front Page

*   [](https://codex.wordpress.org/Function_Reference/is_front_page "Function Reference/is front page")[is\_front\_page()](https://developer.wordpress.org/reference/functions/is_front_page/)

### The Blog Page

*   [](https://codex.wordpress.org/Function_Reference/is_front_page "Function Reference/is front page")[is\_front\_page()](https://developer.wordpress.org/reference/functions/is_front_page/)
*   [](https://codex.wordpress.org/Function_Reference/is_home "Function Reference/is home")[is\_home()](https://developer.wordpress.org/reference/functions/is_home/)

### A Single Post Page

*   [](https://codex.wordpress.org/Function_Reference/is_single "Function Reference/is single")[is\_single()](https://developer.wordpress.org/reference/functions/is_single/)

### A PAGE Page

*   [](https://codex.wordpress.org/Function_Reference/is_page "Function Reference/is page")[is\_page()](https://developer.wordpress.org/reference/functions/is_page/)
*   [](https://codex.wordpress.org/Function_Reference/is_page_template "Function Reference/is page template")[is\_page\_template()](https://developer.wordpress.org/reference/functions/is_page_template/)

### Has Post Thumbnail

*   [has\_post\_thumbnail( $post\_id )](https://codex.wordpress.org/Function_Reference/has_post_thumbnail "Function Reference/has post thumbnail")

### A Single Page, a Single Post, an Attachment or Any Other Custom Post Type

*   [](https://codex.wordpress.org/Function_Reference/is_singular "Function Reference/is singular")[is\_singular()](https://developer.wordpress.org/reference/functions/is_singular/)

### A Category Page

*   [is\_category( $category )](https://codex.wordpress.org/Function_Reference/is_category "Function Reference/is category")

### A Tag Page

*   [](https://codex.wordpress.org/Function_Reference/is_tag "Function Reference/is tag")[is\_tag()](https://developer.wordpress.org/reference/functions/is_tag/)
*   [](https://codex.wordpress.org/Function_Reference/has_tag "Function Reference/has tag")[has\_tag()](https://developer.wordpress.org/reference/functions/has_tag/)

### A Taxonomy Page (and related)

*   [](https://codex.wordpress.org/Function_Reference/is_tax "Function Reference/is tax")[is\_tax()](https://developer.wordpress.org/reference/functions/is_tax/)
*   [](https://codex.wordpress.org/Function_Reference/has_term "Function Reference/has term")[has\_term()](https://developer.wordpress.org/reference/functions/has_term/)
*   [term\_exists( $term, $taxonomy, $parent )](https://codex.wordpress.org/Function_Reference/term_exists "Function Reference/term exists")
*   [is\_taxonomy\_hierarchical( $taxonomy )](https://codex.wordpress.org/Function_Reference/is_taxonomy_hierarchical "Function Reference/is taxonomy hierarchical")
*   [taxonomy\_exists( $taxonomy )](https://codex.wordpress.org/Function_Reference/taxonomy_exists "Function Reference/taxonomy exists")

### An Author Page

*   [](https://codex.wordpress.org/Function_Reference/is_author "Function Reference/is author")[is\_author()](https://developer.wordpress.org/reference/functions/is_author/)

### A Date Page

*   [](https://codex.wordpress.org/Function_Reference/is_date "Function Reference/is date")[is\_date()](https://developer.wordpress.org/reference/functions/is_date/)
*   [](https://codex.wordpress.org/Function_Reference/is_year "Function Reference/is year")[is\_year()](https://developer.wordpress.org/reference/functions/is_year/)
*   [](https://codex.wordpress.org/Function_Reference/is_month "Function Reference/is month")[is\_month()](https://developer.wordpress.org/reference/functions/is_month/)
*   [](https://codex.wordpress.org/Function_Reference/is_day "Function Reference/is day")[is\_day()](https://developer.wordpress.org/reference/functions/is_day/)
*   [](https://codex.wordpress.org/Function_Reference/is_time "Function Reference/is time")[is\_time()](https://developer.wordpress.org/reference/functions/is_time/)
*   [](https://codex.wordpress.org/Function_Reference/is_new_day "Function Reference/is new day")[is\_new\_day()](https://developer.wordpress.org/reference/functions/is_new_day/)

### Any Archive Page

*   [](https://codex.wordpress.org/Function_Reference/is_archive "Function Reference/is archive")[is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/)

### A Search Result Page

*   [](https://codex.wordpress.org/Function_Reference/is_search "Function Reference/is search")[is\_search()](https://developer.wordpress.org/reference/functions/is_search/)

### A 404 Not Found Page

*   [](https://codex.wordpress.org/Function_Reference/is_404 "Function Reference/is 404")[is\_404()](https://developer.wordpress.org/reference/functions/is_404/)

### Is Dynamic SideBar

*   [](https://codex.wordpress.org/Function_Reference/is_dynamic_sidebar "Function Reference/is dynamic sidebar")[is\_dynamic\_sidebar()](https://developer.wordpress.org/reference/functions/is_dynamic_sidebar/)

### Is Sidebar Active

*   [](https://codex.wordpress.org/Function_Reference/is_active_sidebar "Function Reference/is active sidebar")[is\_active\_sidebar()](https://developer.wordpress.org/reference/functions/is_active_sidebar/)

### Is Widget Active

*   [is\_active\_widget( $widget\_callback, $widget\_id )](https://codex.wordpress.org/Function_Reference/is_active_widget "Function Reference/is active widget")

### Is User Logged in

*   [](https://codex.wordpress.org/Function_Reference/is_user_logged_in "Function Reference/is user logged in")[is\_user\_logged\_in()](https://developer.wordpress.org/reference/functions/is_user_logged_in/)

### Email Exists

*   [email\_exists( $email )](https://codex.wordpress.org/Function_Reference/email_exists "Function Reference/email exists")

### Username Exists

*   [username\_exists( $username )](https://codex.wordpress.org/Function_Reference/username_exists "Function Reference/username exists")

### A Paged Page

*   [](https://codex.wordpress.org/Function_Reference/is_paged "Function Reference/is paged")[is\_paged()](https://developer.wordpress.org/reference/functions/is_paged/)

### Right To Left Reading

*   [](https://codex.wordpress.org/Function_Reference/is_rtl "Function Reference/is rtl")[is\_rtl()](https://developer.wordpress.org/reference/functions/is_rtl/)

### An Attachment

*   [](https://codex.wordpress.org/Function_Reference/is_attachment "Function Reference/is attachment")[is\_attachment()](https://developer.wordpress.org/reference/functions/is_attachment/)

### Attachment Is Image

*   [wp\_attachment\_is\_image( $post\_id )](https://codex.wordpress.org/Function_Reference/wp_attachment_is_image "Function Reference/wp attachment is image")

### A Local Attachment

*   [is\_local\_attachment( $url )](https://codex.wordpress.org/Function_Reference/is_local_attachment "Function Reference/is local attachment")

### Post Type Exists

*   [post\_type\_exists( $post\_type )](https://codex.wordpress.org/Function_Reference/post_type_exists "Function Reference/post type exists")

### Is Main Query

*   [](https://codex.wordpress.org/Function_Reference/is_main_query "Function Reference/is main query")[is\_main\_query()](https://developer.wordpress.org/reference/functions/is_main_query/)

### A New Day

*   [](https://codex.wordpress.org/Function_Reference/is_new_day "Function Reference/is new day")[is\_new\_day()](https://developer.wordpress.org/reference/functions/is_new_day/)

### A Syndication

*   [](https://codex.wordpress.org/Function_Reference/is_feed "Function Reference/is feed")[is\_feed()](https://developer.wordpress.org/reference/functions/is_feed/)

### A Trackback

*   [](https://codex.wordpress.org/Function_Reference/is_trackback "Function Reference/is trackback")[is\_trackback()](https://developer.wordpress.org/reference/functions/is_trackback/)

### A Preview

*   [](https://codex.wordpress.org/Function_Reference/is_preview "Function Reference/is preview")[is\_preview()](https://developer.wordpress.org/reference/functions/is_preview/)

### Has An Excerpt

*   [](https://codex.wordpress.org/Function_Reference/has_excerpt "Function Reference/has excerpt")[has\_excerpt()](https://developer.wordpress.org/reference/functions/has_excerpt/)

### Has A Nav Menu Assigned

*   [](https://codex.wordpress.org/Function_Reference/has_nav_menu "Function Reference/has nav menu")[has\_nav\_menu()](https://developer.wordpress.org/reference/functions/has_nav_menu/)

### Is Blog Installed

*   [](https://codex.wordpress.org/Function_Reference/is_blog_installed "Function Reference/is blog installed")[is\_blog\_installed()](https://developer.wordpress.org/reference/functions/is_blog_installed/)

### Part of a Network (Multisite)

*   [](https://codex.wordpress.org/Function_Reference/is_multisite "Function Reference/is multisite")[is\_multisite()](https://developer.wordpress.org/reference/functions/is_multisite/)
*   [](https://codex.wordpress.org/Function_Reference/is_main_site "Function Reference/is main site")[is\_main\_site()](https://developer.wordpress.org/reference/functions/is_main_site/)
*   [](https://codex.wordpress.org/Function_Reference/is_super_admin "Function Reference/is super admin")[is\_super\_admin()](https://developer.wordpress.org/reference/functions/is_super_admin/)

### An Active Plugin

*   [is\_plugin\_active( $path )](https://codex.wordpress.org/Function_Reference/is_plugin_active "Function Reference/is plugin active")
*   [is\_plugin\_inactive( $path )](https://codex.wordpress.org/Function_Reference/is_plugin_inactive "Function Reference/is plugin inactive")
*   [is\_plugin\_active\_for\_network( $path )](https://codex.wordpress.org/Function_Reference/is_plugin_active_for_network "Function Reference/is plugin active for network")
*   [](https://codex.wordpress.org/Function_Reference/is_plugin_page "Function Reference/is plugin page")[is\_plugin\_page()](https://developer.wordpress.org/reference/functions/is_plugin_page/)

### A Child Theme

*   [](https://codex.wordpress.org/Function_Reference/is_child_theme "Function Reference/is child theme")[is\_child\_theme()](https://developer.wordpress.org/reference/functions/is_child_theme/)

### Theme supports a feature

*   [](https://codex.wordpress.org/Function_Reference/current_theme_supports "Function Reference/current theme supports")[current\_theme\_supports()](https://developer.wordpress.org/reference/functions/current_theme_supports/)

### Is Previewed in the Customizer

*   [](https://codex.wordpress.org/Function_Reference/is_customize_preview "Function Reference/is customize preview")[is\_customize\_preview()](https://developer.wordpress.org/reference/functions/is_customize_preview/)