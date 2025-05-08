# Tools and Setup

In this document, you will learn about the tools that you will need to get off to a solid start when building WordPress themes. You will also find resources on setting up a development environment for testing your projects. 

While it is definitely possible to create and build block themes without any of these tools, they are foundational pieces of a good workflow.

## Development environment

When building WordPress themes, it is a good idea to do it within an environment that is separate from a live (i.e., production) site. Before creating your first WordPress theme, you should set up a development environment.

Don’t let this process scare you if it’s your first time. In the long run, you will be happy you learned how to set this up.

### Why set up a development environment?

Development environments allow you to test code before it goes live on a production site. You don’t want to change something, push it live, and later realize you created a fatal error that took down the whole website. 

By using a development environment, you can test things to ensure they work before they are live.

Your development environment can either be local (on your computer) or on a remote server. But configuring a local environment to work on your theme is beneficial for several reasons:

*   You do not need an internet connection to build your theme.
*   You can build your theme without relying on a remote server. This speeds up the building process, and you can see changes instantly in your browser.
*   You can test your theme from many perspectives. This is important if you plan on releasing it to a larger audience and want maximum compatibility.

### Setting up a local development environment

For developing WordPress themes, you need to set up a development environment that is suited to WordPress. This list is not exhaustive, but here are several options to choose from:

*   [@wordpress/env](https://developer.wordpress.org/block-editor/getting-started/devenv/get-started-with-wp-env/) (local WordPress environment package)
*   [Docker](https://www.docker.com/)
*   [Local](https://localwp.com/)
*   [MAMP](https://www.mamp.info/en/mamp/mac/)
*   [Studio](https://developer.wordpress.com/studio/)
*   [Varying Vagrant Vagrants](https://varyingvagrantvagrants.org/) (VVV)
*   [XAMPP](https://www.apachefriends.org/)

For more information, read the [Setting Up a Development Environment](https://make.wordpress.org/core/handbook/tutorials/installing-a-local-server/) documentation in the Core Handbook.

## Installing WordPress

Before you begin building themes in your development environment, you must also install WordPress. 

Some of the development environments include methods for automatically installing an instance of WordPress. You can skip this step if this is the case for you.

To install WordPress on your own, follow the [How to install WordPress](https://developer.wordpress.org/advanced-administration/before-install/howto-install/) documentation from the Advanced Administration handbook. Then, of course, come back here and learn more about creating WordPress themes!

## Code editor

> *A good code editor is worth its weight in gold.*
> 
> Someone Wise

On a more serious note, a good code editor gives you proper syntax highlighting, error reporting, integration with version control systems (VCS), and much more. It’s there to make your life easier.

Technically, you could edit code in a plain text editor, but you’d be missing out on all the best features that true code editors and IDEs (Integrated Development Environments) bring to life.

[![Visual Studio Code editor program with a theme's single.html file open, showing block markup.](https://i0.wp.com/developer.wordpress.org/files/2023/11/vs-code-editor.png?resize=2757%2C1497&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/vs-code-editor.png?ssl=1)

Editing a theme’s `single.html` template in Visual Studio Code

There are many free and open-source editors to choose from. Here are some of the more popular ones:

*   [Visual Studio Code](https://code.visualstudio.com/) (VS Code)
*   [VIM](https://www.vim.org/)
*   [Brackets](https://brackets.io/)
*   [Notepad++](https://notepad-plus-plus.org/)
*   [GNU Emacs](https://www.gnu.org/software/emacs/)
*   [TextMate](https://macromates.com/)

There are also many proprietary editors that are free or cost a fee to use. Whatever you decide to use, pick something you feel comfortable with.

## Other development tools

A code editor and development environment are the foundational pieces of creating a WordPress theme. However, there are other tools and resources that you will likely find useful for your project.

### Test data

WordPress allows you to [import XML files](https://wordpress.org/documentation/article/importing-content/) containing real or dummy data for testing your themes. This lets you see how your theme performs with different types of content and layouts. Here are two options for importing:

*   [WordPress.org Theme Test Data](https://codex.wordpress.org/Theme_Unit_Test)
*   [WordPress.com Theme Test Data](http://themetest.wordpress.com/) *(includes WordPress.com-specific data)*

If nothing else, you need some type of demo/test content to see what your theme looks like in action. You could even create test posts and pages of your own!

### Plugins

In addition to test data, there are several WordPress plugins that can help make sure your theme is following standard practices and not producing debugging notices. These are optional but can be useful:

*   [Theme Check](https://wordpress.org/plugins/theme-check/): Tests your theme for compliance with the latest WordPress standards and practices.
*   [Debug Bar](https://wordpress.org/plugins/debug-bar/): Adds an admin bar to your WordPress admin and provides a central location for debugging.
*   [Query Monitor](https://wordpress.org/plugins/query-monitor/): Allows debugging of database queries, API requests, and AJAX used to generate theme pages and functionality.
*   [Log Deprecated Notices](https://wordpress.org/plugins/log-deprecated-notices/): Logs incorrect function usage, deprecated file usage, and deprecated function usage in your theme.
*   [Monster Widget](https://wordpress.org/plugins/monster-widget/): Consolidates the core WordPress widgets into a single widget, making it easier to test them all at once (*classic themes only*).

## WordPress.org Theme Review Guidelines

It is a good idea to stay up to date with the [theme guidelines](https://make.wordpress.org/themes/handbook/review/required/) provided by the WordPress.org Themes Team. These guidelines are required if you plan to submit your theme to the official [Theme Directory](https://wordpress.org/themes), but they are also good principles for anyone creating a theme.

You should also follow the [WordPress Coding Standards](https://make.wordpress.org/core/handbook/best-practices/coding-standards/) when writing any code for your theme. This will help make sure what you are creating meets some minimum quality standards.