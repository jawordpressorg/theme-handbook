# Administration Menus

Warning: This is no longer the recommended way to work with theme options. The [Customizer API](https://developer.wordpress.org/themes/customize-api/) is the recommended way to give more control and flexibility to your users

  
Theme authors might need to provide a settings screen, so users can customize how their theme is used or works. The best way to do this is to create an administration menu item that allows the user to access that settings screen from all the administration screens.

## Function Reference

### Menu Pages

[add\_menu\_page()](https://codex.wordpress.org/Function_Reference/add_menu_page)  
[add\_object\_page()](https://codex.wordpress.org/Function_Reference/add_object_page)  
[add\_utility\_page()](https://codex.wordpress.org/Function_Reference/add_utility_page)  
[remove\_menu\_page()](https://codex.wordpress.org/Function_Reference/remove_menu_page)

### Sub-menu Pages

[add\_submenu\_page()](https://codex.wordpress.org/Function_Reference/add_submenu_page)  
[remove\_submenu\_page()](https://codex.wordpress.org/Function_Reference/remove_submenu_page)

### WordPress Administration Menus

[add\_dashboard\_page()](https://codex.wordpress.org/Function_Reference/add_dashboard_page)  
[add\_posts\_page()](https://codex.wordpress.org/Function_Reference/add_posts_page)  
[add\_media\_page()](https://codex.wordpress.org/Function_Reference/add_media_page)  
[add\_links\_page()](https://codex.wordpress.org/Function_Reference/add_links_page)  
[add\_pages\_page()](https://codex.wordpress.org/Function_Reference/add_pages_page)  
[add\_comments\_page()](https://codex.wordpress.org/Function_Reference/add_comments_page)  
[add\_theme\_page()](https://codex.wordpress.org/Function_Reference/add_theme_page)  
[add\_plugins\_page()](https://codex.wordpress.org/Function_Reference/add_plugins_page)  
[add\_users\_page()](https://codex.wordpress.org/Function_Reference/add_users_page)  
[add\_management\_page()](https://codex.wordpress.org/Function_Reference/add_management_page)  
[add\_options\_page()](https://codex.wordpress.org/Function_Reference/add_options_page)

## Every Plot Needs a Hook

To add an administration menu, there are three things you need to do:

1.  Create a function that contains the menu-building code.
2.  Register the above function using the `admin_menu` action hook – or `network_admin_menu`, if you are adding a menu for the Network.
3.  Create the HTML output for the screen, displayed when the menu item is clicked.

Most developers overlook the second step in this list. You can’t simply call the menu code. You need to put it **inside a function**, and then register this function.

Here is a simple example of these three steps described. This will add a sub-level menu item under the Settings top-level menu. When selected, that menu item will show a very basic screen.

<br />
&lt;?php<br />
/\*\* Step 2 (from text above). \*/<br />
add\_action( 'admin\_menu', 'my\_menu' );</p>
<p>/\*\* Step 1. \*/<br />
function my\_menu() {<br />
	add\_options\_page(<br />
		'My Options',<br />
		'My Menu',<br />
		'manage\_options',<br />
		'my-unique-identifier',<br />
		'my\_options'<br />
	);<br />
}</p>
<p>/\*\* Step 3. \*/<br />
function my\_options() {<br />
	if ( !current\_user\_can( 'manage\_options' ) ) {<br />
		wp\_die( \_\_( 'You do not have sufficient permissions to access this page.' ) );<br />
	}<br />
	echo 'Here is where I output the HTML for my screen.';<br />
	echo '&lt;/div>&lt;pre>';<br />
}<br />
?><br />

[Expand full source code](#)[Collapse full source code](#)

In this example, the function `my_menu()` adds a new item to the Settings administration menu via the [`add_options_page()`](https://codex.wordpress.org/Function_Reference/add_options_page) function.

*Note:* Note that the [add\_action()](https://codex.wordpress.org/Function_Reference/add_action) call in Step 2 *registers* the my\_menu() function under the [admin\_menu](https://codex.wordpress.org/Plugin_API/Action_Reference/admin_menu) hook. **Without that, [add\_action()](https://developer.wordpress.org/reference/functions/add_action/) call, a PHP error for undefined function will be thrown**. Finally, the `add_options_page()` call refers to the `my_options()` function which contains the actual page to be displayed (and PHP code to be processed) when someone clicks the menu item.

These steps are described in more detail in the sections below. Remember to enclose the creation of the menu and the page in functions, and use the `admin_menu` [hook](https://codex.wordpress.org/Plugin_API/Action_Reference) to get the whole process started at the right time.

## Determining Location for New Menus

Before creating a new menu, first decide if the menu should be a **top-level** menu, or a **sub-level** menu item. A top-level menu displays as new section in the administration menus and contains sub-level menu items. This means a sub-level menu item is a member of an existing top-level menu.

It is rare that a theme would require the creation of a new top-level menu. If the theme introduces an entirely new concept to WordPress and needs many screens to do it, then that theme may warrant a new top-level menu. Adding a top-level menu should only be considered if you really need multiple, related screens to make WordPress do something it was not originally designed to accomplish. Examples of new top-level menus might include job management or conference management. Please note that, with the native [post type](https://codex.wordpress.org/Glossary#Post_Type) registration, WordPress automatically creates top-level menus to manage this kind of features.

If the creation of a top-level menu is not necessary, you need to decide under what top-level menu to place your new sub-level menu item. As a point of reference, several themes add sub-level menu items underneath existing WordPress top-level menus.

Use this guide of the WordPress top-level menus to determine the correct location for your sub-level menu item:

*   Dashboard – information central for your site and include the Updates option for updating WordPress core, plugins, and themes.
*   Posts – displays tools for writing posts (time oriented content).
*   Media – uploading and managing your pictures, videos, and audio.
*   Links – manage references to other blogs and sites of interest.
*   Pages – displays tools for writing your static content called pages.
*   Comments – controlling and regulation reader to responses to posts.
*   Appearance – displays controls for manipulation of theme/style files, sidebars, etc.
*   Plugins – displays controls dealing with plugin management, not configuration options for a plugin itself.
*   Users – displays controls for user management.
*   Tools – manage the export, import, and even backup of blog data.
*   Settings – displays plugin options that only administrators should view.
*   Network Admin – displays plugin options that are set on the Network. Instead of `admin_menu`, you should use `network_admin_menu` (see also [Create A Network](https://codex.wordpress.org/Create_A_Network))

### Top-Level Menus

If you have decided your theme requires a brand-new top-level menu, the first thing you’ll need to do is to create one with the `add_menu_page()` function. *Note:* skip to [Sub-Level Menus](#sub-level-menus) if you don’t need a top-level menu.

Parameter values:

*   `page_title` – the text to be displayed in the title tags of the page when the menu is selected.
*   `menu_title` – the on-screen name text for the menu.
*   `capability` – the capability required for this menu to be displayed to the user. When using the Settings API to handle your form, you should use `manage_options` here as the user won’t be able to save options without it. User levels are deprecated and should not be used here.
*   `menu_slug` – the slug name to refer to this menu by (should be unique for this menu). Prior to Version 3.0 this was called the file (or handle) parameter. If the function parameter is omitted, the `menu_slug` should be the PHP file that handles the display of the menu page content.
*   `function` – the function that displays the page content for the menu page.
*   `icon_url` – the URL to the icon to be used for this menu. This parameter is optional.
*   `position` – the position in the menu order this menu should appear. By default, if this parameter is omitted, the menu will appear at the bottom of the menu structure. To see the current menu positions, use `print_r( $GLOBALS[ 'menu' ] )` after the menu has loaded.
*   Sub-Level Menus – once your top-level menu is defined, or you have chosen to use an existing WordPress top-level menu, you are ready to define one or more sub-level menu items using the `add_submenu_page()` function.

### Sub-Level Menus

If you want your new menu item to be a sub-menu item, you can create it using the `add_submenu_page()` function instead.

Parameter values:

*   `parent_slug` – the slug name for the parent menu, or the file name of a standard WordPress admin file that supplies the top-level menu in which you want to insert your sub-menu, or your plugin file if this sub-menu is going into a custom top-level menu. Examples:
    *   Dashboard – `add_submenu_page('index.php', ...)`
    *   Posts – `add_submenu_page('edit.php', ...)`
    *   Media – `add_submenu_page('upload.php', ...)`
    *   Links – `add_submenu_page('link-manager.php', ...)`
    *   Pages – `add_submenu_page('edit.php?post_type=page', ...)`
    *   Comments – `add_submenu_page('edit-comments.php', ...)`
    *   Custom Post Types – `add_submenu_page('edit.php?post_type=your_post_type', ...)`
    *   Appearance – `add_submenu_page('themes.php', ...)`
    *   Plugins – `add_submenu_page('plugins.php', ...)`
    *   Users – `add_submenu_page('users.php', ...)`
    *   Tools – `add_submenu_page('tools.php', ...)`
    *   Settings – `add_submenu_page('options-general.php', ...)`
*   `page_title` – text that will go into the HTML page title for the page when the submenu is active.
*   `menu_title` – the text to be displayed in the title tags of the page when the menu is selected.
*   `capability` – the capability required for this menu to be displayed to the user. User levels are deprecated and should not be used here.
*   `menu_slug` – for existing WordPress menus, the PHP file that handles the display of the menu page content. For sub-menus of a custom top-level menu, a unique identifier for this sub-menu page.
*   `function` – the function that displays the page content for the menu page. Technically, as in the `add_menu_page` function, the function parameter is optional, but if it is not supplied, then WordPress will basically assume that including the PHP file will generate the administration screen, without calling a function.

### Using Wrapper Functions

Since most sub-level menus belong under the Settings, Tools, or Appearance menus, WordPress supplies wrapper functions that make adding a sub-level menu items to these top-level menus easier. Note that the function names may not match the names seen in the admin UI as they have changed over time:

Dashboard

<?php add\_dashboard\_page( $page\_title, $menu\_title, $capability, $menu\_slug, $function); ?>

Posts

<?php add\_posts\_page( $page\_title, $menu\_title, $capability, $menu\_slug, $function); ?>

Media

<?php add\_media\_page( $page\_title, $menu\_title, $capability, $menu\_slug, $function); ?>

Links

<?php add\_links\_page( $page\_title, $menu\_title, $capability, $menu\_slug, $function); ?>

Pages

<?php add\_pages\_page( $page\_title, $menu\_title, $capability, $menu\_slug, $function); ?>

Comments

<?php add\_comments\_page( $page\_title, $menu\_title, $capability, $menu\_slug, $function); ?>

Appearance

<?php add\_theme\_page( $page\_title, $menu\_title, $capability, $menu\_slug, $function); ?>

Plugins

<?php add\_plugins\_page( $page\_title, $menu\_title, $capability, $menu\_slug, $function); ?>

Users

<?php add\_users\_page( $page\_title, $menu\_title, $capability, $menu\_slug, $function); ?>

Tools

<?php add\_management\_page( $page\_title, $menu\_title, $capability, $menu\_slug, $function); ?>

Settings

<?php add\_options\_page( $page\_title, $menu\_title, $capability, $menu\_slug, $function); ?>

Also see [Theme Options](https://developer.wordpress.org/themes/customize-api/) for the currently recommended way of creating options via the Customizer API.

### Example

Here’s a quick example illustrating how to insert a top-level menu page and a sub-menu page, where the title on the sub-menu page is different from the top-level page. In this example, `register_my_theme_more_settings_menu` is the name of the function that displays the first sub-menu page:

<br />
function register\_my\_theme\_settings\_menu() {<br />
	add\_menu\_page(<br />
		&quot;My Theme's Settings&quot;,<br />
		&quot;My Theme&quot;,<br />
		&quot;manage\_options&quot;,<br />
		&quot;my-theme-settings-menu&quot;<br />
	);<br />
}</p>
<p>function register\_my\_theme\_more\_settings\_menu() {<br />
	add\_submenu\_page(<br />
		&quot;my-themes-settings-menu&quot;,<br />
		&quot;More Settings for My Theme&quot;,<br />
		&quot;More Settings&quot;,<br />
		&quot;manage\_options&quot;,<br />
		&quot;my-theme-more-settings-menu&quot;<br />
	);<br />
}</p>
<p>add\_action( &quot;admin\_menu&quot;, &quot;register\_my\_theme\_settings\_menu&quot;);<br />
add\_action( &quot;admin\_menu&quot;, &quot;register\_my\_theme\_more\_settings\_menu&quot;);<br />

[Expand full source code](#)[Collapse full source code](#)

Here’s an example of adding an option page under a custom post type menu block (see also here):

CODE

## Inserting the Pages

Here is an example of how to insert multiple menus into various places:

&lt;?php<br />
// Hook for adding admin menus<br />
add\_action('admin\_menu', 'mt\_add\_pages');</p>
<p>// Action function for hook above<br />
function mt\_add\_pages() {<br />
// Add a new submenu under Settings:<br />
add\_options\_page(\_\_('Test Settings','menu-test'), \_\_('Test Settings','menu-test'), 'manage\_options', 'testsettings', 'mt\_settings\_page');</p>
<p>// Add a new submenu under Tools:<br />
add\_management\_page( \_\_('Test Tools','menu-test'), \_\_('Test Tools','menu-test'), 'manage\_options', 'testtools', 'mt\_tools\_page');</p>
<p>// Add a new top-level menu (ill-advised):<br />
add\_menu\_page(\_\_('Test Toplevel','menu-test'), \_\_('Test Top-level','menu-test'), 'manage\_options', 'mt-top-level-handle', 'mt\_toplevel\_page' );</p>
<p>// Add a submenu to the custom top-level menu:<br />
add\_submenu\_page('mt-top-level-handle', \_\_('Test Sub-Level','menu-test'), \_\_('Test Sub-Level','menu-test'), 'manage\_options', 'sub-page', 'mt\_sublevel\_page');</p>
<p>// Add a second submenu to the custom top-level menu:<br />
add\_submenu\_page('mt-top-level-handle', \_\_('Test Sub-Level 2','menu-test'), \_\_('Test Sub-Level 2','menu-test'), 'manage\_options', 'sub-page2', 'mt\_sublevel\_page2');<br />
}</p>
<p>// mt\_settings\_page() displays the page content for the Test settings sub-menu<br />
function mt\_settings\_page() {<br />
	echo &quot;&lt;/pre><br />
	&lt;h2>&quot; . \_\_( 'Test Settings', 'menu-test' ) . &quot;&lt;/h2><br />
	&lt;pre><br />
	&quot;;<br />
}</p>
<p>// mt\_tools\_page() displays the page content for the Test Tools sub-menu<br />
function mt\_tools\_page() {<br />
	echo &quot;&lt;/pre><br />
	&lt;h2>&quot; . \_\_( 'Test Tools', 'menu-test' ) . &quot;&lt;/h2><br />
	&lt;pre><br />
	&quot;;<br />
}</p>
<p>// mt\_toplevel\_page() displays the page content for the custom Test Top-Level menu<br />
function mt\_toplevel\_page() {<br />
	echo &quot;&lt;/pre><br />
	&lt;h2>&quot; . \_\_( 'Test Top-Level', 'menu-test' ) . &quot;&lt;/h2><br />
	&lt;pre><br />
	&quot;;<br />
}</p>
<p>// mt\_sublevel\_page() displays the page content for the first sub-menu<br />
// of the custom Test Toplevel menu<br />
function mt\_sublevel\_page() {<br />
	echo &quot;&lt;/pre><br />
	&lt;h2>&quot; . \_\_( 'Test Sub-Level', 'menu-test' ) . &quot;&lt;/h2><br />
	&lt;pre><br />
&quot;;<br />
}</p>
<p>// mt\_sublevel\_page2() displays the page content for the second sub-menu<br />
// of the custom Test Top-Level menu<br />
function mt\_sublevel\_page2() {<br />
	echo &quot;&lt;/pre><br />
	&lt;h2>&quot; . \_\_( 'Test Sub-Level 2', 'menu-test' ) . &quot;&lt;/h2><br />
	&lt;pre><br />
&quot;;<br />
}<br />
?>

[Expand full source code](#)[Collapse full source code](#)

## Sample Menu Page

*Note:* See the [Settings API](https://codex.wordpress.org/Settings_API) for information on creating settings pages.

The previous example contains several dummy functions, such as `mt_settings_page()`, as placeholders for actual page content. Let’s expand on them. What if you wanted to create an option called `mt_favorite_color` that allows the site owner to type in their favorite color via a Settings page? The `mt_options_page()` function will need to output a data entry form on the screen, as well as to process the entered data.

Here is a function that does this:

// mt\_settings\_page() displays the page content for the Test settings sub-menu<br />
function mt\_settings\_page() {<br />
	//must check that the user has the required capability<br />
	if (!current\_user\_can('manage\_options'))<br />
	{<br />
		wp\_die( \_\_('You do not have sufficient permissions to access this page.') );<br />
	}</p>
<p>	// Variables for the field and option names<br />
	$opt\_name = 'mt\_favorite\_color';<br />
	$hidden\_field\_name = 'mt\_submit\_hidden';<br />
	$data\_field\_name = 'mt\_favorite\_color';</p>
<p>	// Read in existing option value from database<br />
	$opt\_val = get\_option( $opt\_name );</p>
<p>	// See if the user has posted us some information<br />
	// If they did, this hidden field will be set to 'Y'<br />
	if( isset($\_POST\[ $hidden\_field\_name \]) &amp;&amp; $\_POST\[ $hidden\_field\_name \] == 'Y' ) {<br />
	// Read their posted value<br />
	$opt\_val = $\_POST\[ $data\_field\_name \];</p>
<p>	// Save the posted value in the database<br />
	update\_option( $opt\_name, $opt\_val );</p>
<p>	// Put a &quot;Settings updated&quot; message on the screen<br />
?><br />
&lt;div class=&quot;updated&quot;>&lt;/div></p>
<p>&lt;div class=&quot;wrap&quot;><br />
&lt;?php<br />
// Header<br />
echo &quot;&lt;h2>&quot; . \_\_( 'Menu Test Settings', 'menu-test' ) . &quot;&lt;/h2>&quot;;</p>
<p>// Settings form<br />
?><br />
&lt;form action=&quot;&quot; method=&quot;post&quot; name=&quot;form1&quot;>&lt;/form><br />
&lt;?php \_e(&quot;Favorite Color:&quot;, 'menu-test' ); ?></p>
<p>&lt;hr /><br />
&lt;/div><br />
&lt;?php } ?>

[Expand full source code](#)[Collapse full source code](#)

**A few notes:**

*   The WordPress functions such as `add_menu_page()` and `add_submenu_page()` take a capability which will be used to determine whether the top-level or sub-level menu is displayed.
*   The function which is hooked in to handle the output of the page must check that the user has the required capability as well.
*   The WordPress administration functions take care of validating the user login, so you don’t have to worry about it in your function.
*   The function example above has been internationalized — see the [I18n for WordPress Developers](https://codex.wordpress.org/I18n_for_WordPress_Developers) for more details.
*   The function processes any entered data before putting the data entry form on the screen, so that the new values will be shown in the form (rather than the values from the database).
*   You don’t have to worry about this working the first time, because the WordPress `update_option` function will automatically add an option to the database if it doesn’t already exist.
*   These admin-menu-adding procedures are parsed every single time you navigate to a page in Admin. So if you are writing a theme which has no options page, but add one later, you can just add it using the instructions above and re-upload, and tweak until you’re happy with it. In other words, menus are not “permanently added” or put into a database upon activating a theme. They’re parsed on the fly, so you can add or subtract menu items at will, re-upload, and the change will be reflected right away.

## Page Hook Suffix

Every function that adds a new administration menu – `add_menu_page()`, `add_submenu_page()` and its specialized versions such as `add_options_page()` – returns a special value called **Page Hook Suffix**. It can be used later as a hook to which an action called only on that particular page can be registered.

One such action hook is `load-{page_hook}`, where `{page_hook}` is the value returned by one of these `add_*_page()` functions. This hook is called when the particular page is loaded. In the example below, it is used to display the “Theme is not configured” notice on all admin pages except for plugin’s options page:

&lt;?php<br />
add\_action('admin\_menu', 'my\_menu');</p>
<p>// Here you can check if plugin is configured (e.g. check if some option is set). If not, add new hook.<br />
// In this example hook is always added.<br />
add\_action( 'admin\_notices', 'my\_admin\_notices' );</p>
<p>function my\_menu() {<br />
	// Add the new admin menu and page and save the returned hook suffix<br />
	$hook\_suffix = add\_options\_page('My Options', 'My Theme', 'manage\_options', 'my-unique-identifier', 'my\_options');<br />
	// Use the hook suffix to compose the hook and register an action executed when plugin's options page is loaded<br />
	add\_action( 'load-' . $hook\_suffix , 'my\_load\_function' );<br />
}</p>
<p>function my\_load\_function() {<br />
	// Current admin page is the options page for our plugin, so do not display the notice<br />
	// (remove the action responsible for this)<br />
	remove\_action( 'admin\_notices', 'my\_admin\_notices' );<br />
}</p>
<p>function my\_admin\_notices() {<br />
	echo '&lt;pre><br />
	&lt;div class=&quot;updated fade&quot; id=&quot;notice&quot;><br />
	My Plugin is not configured yet. Please do it now.&lt;/div><br />
	&lt;/pre>';<br />
}</p>
<p>function my\_options() {<br />
	if (!current\_user\_can('manage\_options')) {<br />
	wp\_die( \_\_('You do not have sufficient permissions to access this page.') );<br />
	}</p>
<p>	echo '&lt;/pre><br />
	&lt;div class=&quot;wrap&quot;>';<br />
	echo 'Here is where the form would go if I actually had options.';<br />
	echo '&lt;/div><br />
	&lt;pre><br />
	';<br />
}<br />
?>

[Expand full source code](#)[Collapse full source code](#)

## Resources

[Top Level Menu discussion on wp-hackers  
](http://comox.textdrive.com/pipermail/wp-hackers/2009-February/024632.html)[Admin Menu Editor Plugin](https://wordpress.org/extend/plugins/admin-menu-editor/)