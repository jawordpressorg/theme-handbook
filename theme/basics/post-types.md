# Post Types

There are many different types of content in WordPress. These content types are normally described as Post Types, which may be a little confusing since it refers to all different types of content in WordPress. For example, a post is a specific Post Type, and so is a page.

Internally, all of the Post Types are stored in the same place — in the wp\_posts database table — but are differentiated by a database column called post\_type.

In addition to the default Post Types, you can also create Custom Post Types.

The [Template files](https://developer.wordpress.org/themes/basics/template-files/) page briefly mentioned that different Post Types are displayed by different Template files.  As the whole purpose of a Template file is to display content a certain way, the Post Types purpose is to categorize what type of content you are dealing with. Generally speaking, certain Post Types are tied to certain template files.

## Default Post Types

There are five default Post Types readily available to users or internally used by the WordPress installation:

*   Post (Post Type: ‘post’)
*   Page (Post Type: ‘page’)
*   Attachment (Post Type: ‘attachment’)
*   Revision (Post Type: ‘revision’)
*   Navigation menu (Post Type: ‘nav\_menu\_item’)

The Post Types above can be modified and removed by a plugin or theme, but it’s not recommended that you remove built-in functionality for a widely-distributed theme or plugin.

The most common post types you will interact with as a Theme Developer are Post, Page, Attachment, and Custom Post Types.  It’s out of the scope of this handbook to flesh out the Revision and Navigation Menu Post Types.  However, it is important to note that you will interact with and build the functionality of [navigation menus](https://developer.wordpress.org/themes/functionality/navigation-menus/) and that will be detailed later in this handbook.

### Post

Posts are used in blogs. They are:

*   displayed in reverse sequential order by time, with the newest post first
*   have a date and time stamp
*   may have the default [taxonomies of categories and tags](https://developer.wordpress.org/themes/functionality/categories-tags-custom-taxonomies/) applied
*   are used for creating feeds

The template files that display the Post post type are:

*   `single.php` and `single-post.php`
*   `category.php` and all its iterations
*   `tag.php` and all its iterations
*   `taxonomy.php` and all its iterations
*   `archive.php` and all its iterations
*   `author.php` and all its iterations
*   `date.php` and all its iterations
*   `search.php`
*   `home.php`
*   `index.php`

Additionally, theme developers can display Post post types in `front-page.php` if they so desire.

[Read more about Post Template Files](https://developer.wordpress.org/themes/template-files-section/post-template-files/).

### Page

Pages are a static Post Type, outside of the normal blog stream/feed. Their features are:

*   non-time dependent and without a time stamp
*   are not organized using the categories and/or tags taxonomies
*   can have page templates applied to them
*   can be organized in a hierarchical structure — i.e. pages can be parents/children of other pages

The template files that display the Page post type are:

*   `page.php` and all its iterations
*   `$custom.php` and all its iterations
*   `front-page.php`
*   `search.php`
*   `index.php`

[Read more about Page Template Files](https://developer.wordpress.org/themes/template-files-section/page-template-files/).

### Attachment

Attachments are commonly used to display images or media in content, and may also be used to link to relevant files. Their features are:

*   contain information (such as name or description) about files uploaded through the media upload system
*   for images, this includes metadata information stored in the wp\_postmeta table (including size, thumbnails, location, etc)

The template files that display the Attachment post type are:

*   `MIME_type.php`
*   `attachment.php`
*   `single-attachment.php`
*   `single.php`
*   `index.php`

[Read more about Attachment Template Files](https://developer.wordpress.org/themes/template-files-section/attachment-template-files/).

## Custom Post Types

Using Custom Post Types, you can **create your own post type**. It is not recommend that you place this functionality in your theme. This type of functionality should be placed/created in a plugin. This ensures the portability of your user’s content, and that if the theme is changed the content stored in the Custom Post Types won’t disappear.

You can learn more about [creating custom post types in the WordPress Plugin Developer Handbook](https://developer.wordpress.org/plugins/post-types/registering-custom-post-types/).

While you generally won’t develop Custom Post Types in your theme, you may want to code ways to display Custom Post Types that were created by a plugin.  The following templates can display Custom post types:

*   `single-{post-type}.php`
*   `archive-{post-type}.php`
*   `search.php`
*   `index.php`

Additionally, Theme Developers can display Custom Post Types in any template file, often by using [multiple loops](https://developer.wordpress.org/themes/basics/the-loop/#multiple-loops).

[Read more about Custom Post Type Templates](https://developer.wordpress.org/themes/template-files-section/custom-post-type-template-files/).