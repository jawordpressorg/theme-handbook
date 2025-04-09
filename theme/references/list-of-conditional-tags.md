# List of Conditional Tags

Conditional Tags are a boolean data type that can be used in your Template Files to alter the display of content depending on the conditions that the current page matches. They tell WordPress what code to display under specific conditions. Conditional Tags usually work with PHP [if](http://php.net/manual/en/control-structures.if.php "PHP if conditional") /[else](http://php.net/manual/en/control-structures.else.php "PHP else conditional") Conditional Statements and have close relation with WOrdPress [Template Hierarchy](https://codex.wordpress.org/Template_Hierarchy "Template Hierarchy"). .

**Warning: You can only use conditional query tags after the [WP\_Query](https://developer.wordpress.org/reference/classes/wp_query/) is set up or  with [action hook](https://codex.wordpress.org/Plugin_API/Action_Reference#Actions_Run_During_a_Typical_Request "Plugin API/Action Reference").**

## Complete List of Conditional Tags

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

## The Conditions For …

All of the Conditional Tags test to see whether a certain condition is met, and then returns either TRUE or FALSE. The conditions under which various tags output TRUE is listed below. Those tags which can accept parameters are so noted.

### The Main Page

*   [is\_home()](https://codex.wordpress.org/Function_Reference/is_home "Function Reference/is home")

### The Front Page

*   [is\_front\_page()](https://codex.wordpress.org/Function_Reference/is_front_page "Function Reference/is front page")

### The Blog Page

*   [is\_front\_page()](https://codex.wordpress.org/Function_Reference/is_front_page "Function Reference/is front page")
*   [is\_home()](https://codex.wordpress.org/Function_Reference/is_home "Function Reference/is home")

### A Single Post Page

*   [is\_single()](https://codex.wordpress.org/Function_Reference/is_single "Function Reference/is single")

### A PAGE Page

*   [is\_page()](https://codex.wordpress.org/Function_Reference/is_page "Function Reference/is page")
*   [is\_page\_template()](https://codex.wordpress.org/Function_Reference/is_page_template "Function Reference/is page template")

### Has Post Thumbnail

*   [has\_post\_thumbnail( $post\_id )](https://codex.wordpress.org/Function_Reference/has_post_thumbnail "Function Reference/has post thumbnail")

### A Single Page, a Single Post, an Attachment or Any Other Custom Post Type

*   [is\_singular()](https://codex.wordpress.org/Function_Reference/is_singular "Function Reference/is singular")

### A Category Page

*   [is\_category( $category )](https://codex.wordpress.org/Function_Reference/is_category "Function Reference/is category")

### A Tag Page

*   [is\_tag()](https://codex.wordpress.org/Function_Reference/is_tag "Function Reference/is tag")
*   [has\_tag()](https://codex.wordpress.org/Function_Reference/has_tag "Function Reference/has tag")

### A Taxonomy Page (and related)

*   [is\_tax()](https://codex.wordpress.org/Function_Reference/is_tax "Function Reference/is tax")
*   [has\_term()](https://codex.wordpress.org/Function_Reference/has_term "Function Reference/has term")
*   [term\_exists( $term, $taxonomy, $parent )](https://codex.wordpress.org/Function_Reference/term_exists "Function Reference/term exists")
*   [is\_taxonomy\_hierarchical( $taxonomy )](https://codex.wordpress.org/Function_Reference/is_taxonomy_hierarchical "Function Reference/is taxonomy hierarchical")
*   [taxonomy\_exists( $taxonomy )](https://codex.wordpress.org/Function_Reference/taxonomy_exists "Function Reference/taxonomy exists")

### An Author Page

*   [is\_author()](https://codex.wordpress.org/Function_Reference/is_author "Function Reference/is author")

### A Date Page

*   [is\_date()](https://codex.wordpress.org/Function_Reference/is_date "Function Reference/is date")
*   [is\_year()](https://codex.wordpress.org/Function_Reference/is_year "Function Reference/is year")
*   [is\_month()](https://codex.wordpress.org/Function_Reference/is_month "Function Reference/is month")
*   [is\_day()](https://codex.wordpress.org/Function_Reference/is_day "Function Reference/is day")
*   [is\_time()](https://codex.wordpress.org/Function_Reference/is_time "Function Reference/is time")
*   [is\_new\_day()](https://codex.wordpress.org/Function_Reference/is_new_day "Function Reference/is new day")

### Any Archive Page

*   [is\_archive()](https://codex.wordpress.org/Function_Reference/is_archive "Function Reference/is archive")

### A Search Result Page

*   [is\_search()](https://codex.wordpress.org/Function_Reference/is_search "Function Reference/is search")

### A 404 Not Found Page

*   [is\_404()](https://codex.wordpress.org/Function_Reference/is_404 "Function Reference/is 404")

### Is Dynamic SideBar

*   [is\_dynamic\_sidebar()](https://codex.wordpress.org/Function_Reference/is_dynamic_sidebar "Function Reference/is dynamic sidebar")

### Is Sidebar Active

*   [is\_active\_sidebar()](https://codex.wordpress.org/Function_Reference/is_active_sidebar "Function Reference/is active sidebar")

### Is Widget Active

*   [is\_active\_widget( $widget\_callback, $widget\_id )](https://codex.wordpress.org/Function_Reference/is_active_widget "Function Reference/is active widget")

### Is User Logged in

*   [is\_user\_logged\_in()](https://codex.wordpress.org/Function_Reference/is_user_logged_in "Function Reference/is user logged in")

### Email Exists

*   [email\_exists( $email )](https://codex.wordpress.org/Function_Reference/email_exists "Function Reference/email exists")

### Username Exists

*   [username\_exists( $username )](https://codex.wordpress.org/Function_Reference/username_exists "Function Reference/username exists")

### A Paged Page

*   [is\_paged()](https://codex.wordpress.org/Function_Reference/is_paged "Function Reference/is paged")

### Right To Left Reading

*   [is\_rtl()](https://codex.wordpress.org/Function_Reference/is_rtl "Function Reference/is rtl")

### An Attachment

*   [is\_attachment()](https://codex.wordpress.org/Function_Reference/is_attachment "Function Reference/is attachment")

### Attachment Is Image

*   [wp\_attachment\_is\_image( $post\_id )](https://codex.wordpress.org/Function_Reference/wp_attachment_is_image "Function Reference/wp attachment is image")

### A Local Attachment

*   [is\_local\_attachment( $url )](https://codex.wordpress.org/Function_Reference/is_local_attachment "Function Reference/is local attachment")

### Post Type Exists

*   [post\_type\_exists( $post\_type )](https://codex.wordpress.org/Function_Reference/post_type_exists "Function Reference/post type exists")

### Is Main Query

*   [is\_main\_query()](https://codex.wordpress.org/Function_Reference/is_main_query "Function Reference/is main query")

### A New Day

*   [is\_new\_day()](https://codex.wordpress.org/Function_Reference/is_new_day "Function Reference/is new day")

### A Syndication

*   [is\_feed()](https://codex.wordpress.org/Function_Reference/is_feed "Function Reference/is feed")

### A Trackback

*   [is\_trackback()](https://codex.wordpress.org/Function_Reference/is_trackback "Function Reference/is trackback")

### A Preview

*   [is\_preview()](https://codex.wordpress.org/Function_Reference/is_preview "Function Reference/is preview")

### Has An Excerpt

*   [has\_excerpt()](https://codex.wordpress.org/Function_Reference/has_excerpt "Function Reference/has excerpt")

### Has A Nav Menu Assigned

*   [has\_nav\_menu()](https://codex.wordpress.org/Function_Reference/has_nav_menu "Function Reference/has nav menu")

### Is Blog Installed

*   [is\_blog\_installed()](https://codex.wordpress.org/Function_Reference/is_blog_installed "Function Reference/is blog installed")

### Part of a Network (Multisite)

*   [is\_multisite()](https://codex.wordpress.org/Function_Reference/is_multisite "Function Reference/is multisite")
*   [is\_main\_site()](https://codex.wordpress.org/Function_Reference/is_main_site "Function Reference/is main site")
*   [is\_super\_admin()](https://codex.wordpress.org/Function_Reference/is_super_admin "Function Reference/is super admin")

### An Active Plugin

*   [is\_plugin\_active( $path )](https://codex.wordpress.org/Function_Reference/is_plugin_active "Function Reference/is plugin active")
*   [is\_plugin\_inactive( $path )](https://codex.wordpress.org/Function_Reference/is_plugin_inactive "Function Reference/is plugin inactive")
*   [is\_plugin\_active\_for\_network( $path )](https://codex.wordpress.org/Function_Reference/is_plugin_active_for_network "Function Reference/is plugin active for network")
*   [is\_plugin\_page()](https://codex.wordpress.org/Function_Reference/is_plugin_page "Function Reference/is plugin page")

### A Child Theme

*   [is\_child\_theme()](https://codex.wordpress.org/Function_Reference/is_child_theme "Function Reference/is child theme")

### Theme supports a feature

*   [current\_theme\_supports()](https://codex.wordpress.org/Function_Reference/current_theme_supports "Function Reference/current theme supports")

### Is Previewed in the Customizer

*   [is\_customize\_preview()](https://codex.wordpress.org/Function_Reference/is_customize_preview "Function Reference/is customize preview")