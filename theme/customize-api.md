# Theme Options &#8211; The Customize API

The Customize API (Customizer) is a framework for live-previewing any change to WordPress. It provides a unified interface for users to customize various aspects of their theme and their site, from colors and layouts to widgets, menus, and more. Themes and plugins alike can add options to the Customizer. The Customizer is the canonical way to add options to your theme.

[![The customizer as it appears in WordPress 4.6 with the Twenty Fifteen theme.](https://i0.wp.com/developer.wordpress.org/files/2014/10/customize-4.6.png?resize=640%2C360&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2014/10/customize-4.6.png?ssl=1)

The customizer as it appears in WordPress 4.6 with the Twenty Fifteen theme.

Customizer options can be granted to users with different capabilities on a granular basis, so while most options are visible only to administrators by default, other users may access certain options if you want them to be able to. Different parts of the Customizer can also be contextual to whether they’re relevant to the front-end context that the user is previewing. For example, the core widgets functionality only shows widget areas that are displayed on the current page; other widget areas are shown when the user navigates to a page that includes them within the Customizer preview window.

This section contains an overview of the Customize API, including code examples and discussion of best practices. For more details, it is strongly recommended that developers study the core customizer code (all core files containing “customize”). This is considered the canonical, official documentation for the Customize API outside of the inline documentation within the core code.