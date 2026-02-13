<!-- 
# Navigation Menus
 -->

# ナビゲーションメニュー

<!-- 
Navigation Menus are customizable menus in your theme. They allow users to add Pages, Posts, Categories, and URLs to the menu. To create a navigation menu you’ll need to register it, and then display the menu in the appropriate location in your theme.
 -->

「ナビゲーションメニュー」は、あなたのテーマ内でカスタマイズ可能なメニューです。ユーザーは、メニューに「ページ」「投稿」「カテゴリー」「URL」を追加できます。ナビゲーションメニューを作成するには、メニューを登録し、次いであなたのテーマ内の適切な場所に、メニューを表示する必要があります。

<!-- 
## Register Menus
 -->

## メニューの登録

<!-- 
In your theme’s functions.php, you need to register your menu(s). This sets the name that will appear at **Appearance -> Menus**.
 -->

あなたのテーマの `functions.php` 内で、あなたのメニューを登録する必要があります。これにより、**外観->メニュー** に表示されるメニュー名を設定します。

<!-- 
First of all, you will use [register\_nav\_menus()](https://developer.wordpress.org/reference/functions/register_nav_menus/) to register the menu.
 -->

まず最初に、メニューを登録するために [`register_nav_menus()`](https://developer.wordpress.org/reference/functions/register_nav_menus/) を使用します。

<!-- 
In this example, two locations are added to the “Manage Locations” tab: “Header Menu” and “Extra Menu”.
 -->

本例では、「場所の管理」タブに2つの場所 -「ヘッダーメニュー」と「拡張メニュー」- が追加されます。

```php
function register_my_menus() {
  register_nav_menus(
    array(
      'header-menu' => __( 'Header Menu' ),
      'extra-menu' => __( 'Extra Menu' )
     )
   );
 }
 add_action( 'init', 'register_my_menus' );
```

<!-- 
## Display Menus
 -->

## メニューの表示

<!-- 
Once you’ve registered your menus, you need to use [wp\_nav\_menu()](https://developer.wordpress.org/reference/functions/wp_nav_menu/) to tell your theme where to display them. For example, add the following code to your `header.php` file to display the header-menu that was registered above.
 -->

あなたのメニューを登録したら、あなたのテーマに対してメニューを表示する場所を指定するため、[`wp_nav_menu()`](https://developer.wordpress.org/reference/functions/wp_nav_menu/) を使用する必要があります。たとえば、上記で登録した `header-menu` を表示するには、次のコードを `header.php` ファイルに追加しましょう。

```php
wp_nav_menu( array( 'theme_location' => 'header-menu' ) );
```

<!-- 
A full list of parameters can be found in the [wp\_nav\_menu()](https://developer.wordpress.org/reference/functions/wp_nav_menu/) page in the function reference
 -->

パラメータの完全な一覧は、関数リファレンスの [`wp_nav_menu()`](https://developer.wordpress.org/reference/functions/wp_nav_menu/) ページで確認できます。

<!-- 
Repeat this process for any additional menus you want to display in your theme. Optionally, you can add a container class which allows you to style the menu with CSS.
 -->

あなたのテーマに表示したい任意の追加メニューについても、この手順を繰り返してください。オプションとして、CSS でメニューをスタイリングできる、コンテナクラスも追加できます。

```php
wp_nav_menu(
  array(
    'theme_location' => 'extra-menu',
    'container_class' => 'my_extra_menu_class'
  )
);
```

<!-- 
A full list of CSS Classes can be found in the [wp\_nav\_menu()](https://developer.wordpress.org/reference/functions/wp_nav_menu/) page in the function reference. You can use these to style your menus.
 -->

CSS クラスの完全な一覧は、関数リファレンスの [`wp_nav_menu()`](https://developer.wordpress.org/reference/functions/wp_nav_menu/) ページで確認できます。これらを使用して、あなたのメニューをスタイリングできます。

<!-- 
## Display Additional Contents
 -->

## 追加コンテンツの表示

<!-- 
Below is a simplified version of the Twenty Seventeen footer social menu, which displays `span` elements before and after the menu item label text.
 -->

以下は「Twenty Seventeen」フッター・ソーシャルメニューの簡略版で、メニュー項目ラベルテキストの前後に `span` 要素を表示します。

```php
wp_nav_menu(
  array(
    'menu' => 'primary',
    'link_before' => '<span class="screen-reader-text">',
    'link_after' => '</span>',
  )
);
```

<!-- 
The output will display as…
 -->

出力は、以下のように表示されます…

<!-- 
\[html\]  
<div class="menu-social-container">  
<ul id="menu-social">  
<li id="menu-item-1">  
<a href="http://twitter.com/"><span class="screen-reader-text">Twitter</span>  
</li>  
</ul>  
</div>  
\[/html\]
 -->

```
<html>  
<div class="menu-social-container">  
<ul id="menu-social">  
<li id="menu-item-1">  
<a href="http://twitter.com/"><span class="screen-reader-text">Twitter</span>  
</li>  
</ul>  
</div>  
</html>
```

<!-- 
To display text between the `<li>` and `<a>` elements for each menu item, use `before` and `after` parameters.
 -->

各メニュー項目について、`<li>` 要素と `<a>` 要素の間にテキストを表示するには、`before` および `after` パラメータを使用します。

<!-- 
## Define Callback
 -->

## コールバックの定義

<!-- 
By default, WordPress displays the first non-empty menu when the specified menu or location is not found, or generates a Page menu when there is no custom menu selected. To prevent this, use the `theme_location` and `fallback_cb` parameters.
 -->

デフォルトでは、WordPress は、指定されたメニューや場所が見つからない場合、最初に空でないメニューを表示し、カスタムメニューが選択されていない場合は、「ページ」メニューを生成します。これを防ぐには、`theme_location` および `fallback_cb` パラメータを使用しましょう。

```php
wp_nav_menu(
  array(
    'menu' => 'primary',
    // do not fall back to first non-empty menu
    'theme_location' => '__no_such_location',
    // do not fall back to wp_page_menu()
    'fallback_cb' => false
  )
);
```