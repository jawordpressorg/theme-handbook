# Navigation Menus

Navigation Menus are customizable menus in your theme. They allow users to add Pages, Posts, Categories, and URLs to the menu. To create a navigation menu you’ll need to register it, and then display the menu in the appropriate location in your theme.

## Register Menus

In your theme’s functions.php, you need to register your menu(s). This sets the name that will appear at **Appearance -> Menus**.

First of all, you will use [register\_nav\_menus()](https://developer.wordpress.org/reference/functions/register_nav_menus/) to register the menu.

In this example, two locations are added to the “Manage Locations” tab: “Header Menu” and “Extra Menu”.

function register\_my\_menus() {
  register\_nav\_menus(
    array(
      'header-menu' => \_\_( 'Header Menu' ),
      'extra-menu' => \_\_( 'Extra Menu' )
     )
   );
 }
 add\_action( 'init', 'register\_my\_menus' );

## Display Menus

Once you’ve registered your menus, you need to use [wp\_nav\_menu()](https://developer.wordpress.org/reference/functions/wp_nav_menu/) to tell your theme where to display them. For example, add the following code to your `header.php` file to display the header-menu that was registered above.

wp\_nav\_menu( array( 'theme\_location' => 'header-menu' ) );

Note: A full list of parameters can be found in the [wp\_nav\_menu()](https://developer.wordpress.org/reference/functions/wp_nav_menu/) page in the function reference

Repeat this process for any additional menus you want to display in your theme. Optionally, you can add a container class which allows you to style the menu with CSS.

wp\_nav\_menu(
  array(
    'theme\_location' => 'extra-menu',
    'container\_class' => 'my\_extra\_menu\_class' 
  )
);

Note: A full list of CSS Classes can be found in the [wp\_nav\_menu()](https://developer.wordpress.org/reference/functions/wp_nav_menu/) page in the function reference. You can use these to style your menus.

## Display Additional Contents

Below is a simplified version of the Twenty Seventeen footer social menu, which displays `span` elements before and after the menu item label text.

wp\_nav\_menu(
  array(
    'menu' => 'primary',
    'link\_before' => '<span class="screen-reader-text">',
    'link\_after' => '</span>',
  )
);

The output will display as…

<div class="menu-social-container">
  <ul id="menu-social">
    <li id="menu-item-1">
      <a href="http://twitter.com/"><span class="screen-reader-text">Twitter</span>
    </li>
  </ul>
</div>

Note: To display text between the `<li>` and `<a>` elements for each menu item, use `before` and `after` parameters.

## Define Callback

By default, WordPress displays the first non-empty menu when the specified menu or location is not found, or generates a Page menu when there is no custom menu selected. To prevent this, use the `theme_location` and `fallback_cb` parameters.

wp\_nav\_menu(
  array(
    'menu' => 'primary',
    // do not fall back to first non-empty menu
    'theme\_location' => '\_\_no\_such\_location',
    // do not fall back to wp\_page\_menu()
    'fallback\_cb' => false
  )
);