# Reworking Theme Files &amp; Organization

![basics-theme-files-organization-01](https://i0.wp.com/developer.wordpress.org/files/2014/08/basics-theme-files-organization-01.jpg?resize=1024%2C384&ssl=1)

## Theme folder and file structure

While WordPress themes technically only require two files (`index.php` and `style.css`), they usually are made up of many files and can become quickly disorganized.

In the last section, [Template Files](# "Template Files"), you set up your `header.php, footer.php, page.php, home.php, and single.php` files.

Let’s look at  the [Twenty Twelve theme](https://wordpress.org/themes/twentytwelve) default themes as one example of good file structure and organization.  While this may be a bit overwhelming at first, let’s break it down.  Can you find the templates you just built?

![basics-theme-files-organization-02](https://i0.wp.com/developer.wordpress.org/files/2014/08/basics-theme-files-organization-02.png?resize=629%2C1500&ssl=1)

While there are still a lot of files, their names help provide a context of what they are.  Basically each file handles a feature of WordPress.  I.e. `comments.php` deals with how the theme will handle comments; `image.php` instructs the theme how to handle images, etc.  Don’t worry about adding these files unless you need them.

You can see that the main theme template files are in the theme’s root directory, while JavaScript, languages, CSS, and page template files are placed within their own folders.

At this time there are **no required folders within a WordPress theme**. However, WordPress does recognize the following folders by default:

### Page templates folder

![basics-theme-files-organization-03](https://i0.wp.com/developer.wordpress.org/files/2014/08/basics-theme-files-organization-03.png?resize=400%2C124&ssl=1)

The [custom page templates](https://developer.wordpress.org/themes/basics/page-templates/ "Custom Page Templates"), named *page-templates* (since: 3.4.0) allows for better organization of template files. Custom page template files placed in this folder are automatically recognized by WordPress.

### Language folder

![basics-theme-files-organization-04](https://i0.wp.com/developer.wordpress.org/files/2014/08/basics-theme-files-organization-04.png?resize=400%2C85&ssl=1)

If you wish to [internationalize your theme](https://developer.wordpress.org/themes/functionality/internationalization/ "Internationalization") so it’s usable in other languages, you can create a *languages* folder to contain translations.