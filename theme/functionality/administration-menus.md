<!-- 
# Administration Menus
 -->

# 管理メニュー

<!-- 
This is no longer the recommended way to work with theme options. The [Customizer API](https://developer.wordpress.org/themes/customize-api/) is the recommended way to give more control and flexibility to your users
 -->

これはもはやテーマ・オプションを扱う推奨方法では、ありません。[カスタマイザー API](https://developer.wordpress.org/themes/customize-api/) は、あなたのユーザーに対して、さらなるコントロールと柔軟性を提供するための推奨方法です。

<!-- 
Theme authors might need to provide a settings screen, so users can customize how their theme is used or works. The best way to do this is to create an administration menu item that allows the user to access that settings screen from all the administration screens.
 -->

テーマ作者は、ユーザーがテーマの使用方法や動作をカスタマイズできるように、設定画面を提供する必要がある場合があります。これを行う最善の方法は、ユーザーがすべての管理画面からその設定画面にアクセス可能な、管理メニュー項目を作成することです。

<!-- 
## Function Reference
 -->

## 関数リファレンス

<!-- 
### Menu Pages
 -->

### メニュー・ページ

<!-- 
[add\_menu\_page()](https://codex.wordpress.org/Function_Reference/add_menu_page)  
[add\_object\_page()](https://codex.wordpress.org/Function_Reference/add_object_page)  
[add\_utility\_page()](https://codex.wordpress.org/Function_Reference/add_utility_page)  
[remove\_menu\_page()](https://codex.wordpress.org/Function_Reference/remove_menu_page)
 -->

[`add_menu_page()`](https://codex.wordpress.org/Function_Reference/add_menu_page)  
[`add_object_page()`](https://codex.wordpress.org/Function_Reference/add_object_page)  
[`add_utility_page()`](https://codex.wordpress.org/Function_Reference/add_utility_page)  
[`remove_menu_page()`](https://codex.wordpress.org/Function_Reference/remove_menu_page)

<!-- 
### Sub-menu Pages
 -->

### サブメニュー・ページ

<!-- 
[add\_submenu\_page()](https://codex.wordpress.org/Function_Reference/add_submenu_page)  
[remove\_submenu\_page()](https://codex.wordpress.org/Function_Reference/remove_submenu_page)
 -->

[`add_submenu_page()`](https://codex.wordpress.org/Function_Reference/add_submenu_page)  
[`remove_submenu_page()`](https://codex.wordpress.org/Function_Reference/remove_submenu_page)

<!-- 
### WordPress Administration Menus
 -->

### WordPress 管理メニュー

<!-- 
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
 -->

[`add_dashboard_page()`](https://codex.wordpress.org/Function_Reference/add_dashboard_page)  
[`add_posts_page()`](https://codex.wordpress.org/Function_Reference/add_posts_page)  
[`add_media_page()`](https://codex.wordpress.org/Function_Reference/add_media_page)  
[`add_links_page()`](https://codex.wordpress.org/Function_Reference/add_links_page)  
[`add_pages_page()`](https://codex.wordpress.org/Function_Reference/add_pages_page)  
[`add_comments_page()`](https://codex.wordpress.org/Function_Reference/add_comments_page)  
[`add_theme_page()`](https://codex.wordpress.org/Function_Reference/add_theme_page)  
[`add_plugins_page()`](https://codex.wordpress.org/Function_Reference/add_plugins_page)  
[`add_users_page()`](https://codex.wordpress.org/Function_Reference/add_users_page)  
[`add_management_page()`](https://codex.wordpress.org/Function_Reference/add_management_page)  
[`add_options_page()`](https://codex.wordpress.org/Function_Reference/add_options_page)

<!-- 
## Every Plot Needs a Hook
 -->

## すべてのプロットには、フックが必要だ

<!-- 
To add an administration menu, there are three things you need to do:
 -->

管理メニューを追加するには、次の3つのステップが必要です:

<!-- 
1.  Create a function that contains the menu-building code.
2.  Register the above function using the `admin_menu` action hook – or `network_admin_menu`, if you are adding a menu for the Network.
3.  Create the HTML output for the screen, displayed when the menu item is clicked.
 -->

1.  メニュー構築コードを含む関数を、作成します。
2.  上記の関数を `admin_menu` アクション・フック – または、ネットワーク用のメニューを追加する場合は `network_admin_menu` – を使用して、登録します。
3.  メニュー項目がクリックされた際に表示される画面の、HTML 出力を作成します。

<!-- 
Most developers overlook the second step in this list. You can’t simply call the menu code. You need to put it **inside a function**, and then register this function.
 -->

ほとんどの開発者は、このリストの2番目のステップを見落としています。メニュー・コードを単に呼び出すだけでは、いけません。**関数内に記述** し、その関数を登録する必要があります。

<!-- 
Here is a simple example of these three steps described. This will add a sub-level menu item under the Settings top-level menu. When selected, that menu item will show a very basic screen.
 -->

以下に、これら3つのステップを説明する、簡単な例を示します。これにより、設定の最上位メニューの下に、下位メニュー項目が追加されます。選択すると、そのメニュー項目は非常に基本的な画面を表示します。

```php
<?php
/** Step 2 (from text above). */
add_action( 'admin_menu', 'my_menu' );

/** Step 1. */
function my_menu() {
	add_options_page(
		'My Options',
		'My Menu',
		'manage_options',
		'my-unique-identifier',
		'my_options'
	);
}

/** Step 3. */
function my_options() {
	if ( ! current_user_can( 'manage_options' ) ) {
		wp_die( __( 'You do not have sufficient permissions to access this page.' ) );
	}
	echo 'Here is where I output the HTML for my screen.';
	echo '</div><pre>';
}
```

<!-- 
In this example, the function `my_menu()` adds a new item to the Settings administration menu via the [`add_options_page()`](https://codex.wordpress.org/Function_Reference/add_options_page) function.
 -->

この例では、関数 `my_menu()` が [`add_options_page()`](https://codex.wordpress.org/Function_Reference/add_options_page) 関数を経由して、設定管理メニューに新しい項目を追加します。

<!-- 
*Note:* Note that the [add\_action()](https://codex.wordpress.org/Function_Reference/add_action) call in Step 2 *registers* the my\_menu() function under the [admin\_menu](https://codex.wordpress.org/Plugin_API/Action_Reference/admin_menu) hook. **Without that, [add\_action()](https://developer.wordpress.org/reference/functions/add_action/) call, a PHP error for undefined function will be thrown**. Finally, the `add_options_page()` call refers to the `my_options()` function which contains the actual page to be displayed (and PHP code to be processed) when someone clicks the menu item.
 -->

*注:* ステップ2の [`add_action()`](https://codex.wordpress.org/Function_Reference/add_action) コールは、`my_menu()` 関数を [`admin_menu`](https://codex.wordpress.org/Plugin_API/Action_Reference/admin_menu) フック下に *登録* します。**この [`add_action()`](https://developer.wordpress.org/reference/functions/add_action/) コールがなければ、未定義関数に関する PHP エラーが、スローされます**。最後に、`add_options_page()` コールは `my_options()` 関数を参照します。この関数には、メニュー項目がクリックされた際に表示される、実際のページ (および処理される PHP コード) が含まれています。

<!-- 
These steps are described in more detail in the sections below. Remember to enclose the creation of the menu and the page in functions, and use the `admin_menu` [hook](https://codex.wordpress.org/Plugin_API/Action_Reference) to get the whole process started at the right time.
 -->

これらのステップについて、以下のセクションで、より詳細に説明します。メニューとページの作成を、関数でカプセル化し、`admin_menu` [フック](https://codex.wordpress.org/Plugin_API/Action_Reference) を使用して、適切なタイミングでプロセス全体を開始することを、忘れないでください。

<!-- 
## Determining Location for New Menus
 -->

## 新規メニュー設置場所の決定

<!-- 
Before creating a new menu, first decide if the menu should be a **top-level** menu, or a **sub-level** menu item. A top-level menu displays as new section in the administration menus and contains sub-level menu items. This means a sub-level menu item is a member of an existing top-level menu.
 -->

新規メニューを作成する前に、まずそのメニューを **最上位レベル** メニューにするか、**下位レベル** メニュー項目にするかを、決定してください。最上位レベル・メニューは、管理メニュー内で新規セクションとして表示され、下位レベル・メニュー項目を内部に含みます。これは、下位レベル・メニュー項目が、既存の最上位レベル・メニューの構成要素であることを意味します。

<!-- 
It is rare that a theme would require the creation of a new top-level menu. If the theme introduces an entirely new concept to WordPress and needs many screens to do it, then that theme may warrant a new top-level menu. Adding a top-level menu should only be considered if you really need multiple, related screens to make WordPress do something it was not originally designed to accomplish. Examples of new top-level menus might include job management or conference management. Please note that, with the native [post type](https://codex.wordpress.org/Glossary#Post_Type) registration, WordPress automatically creates top-level menus to manage this kind of features.
 -->

テーマが新規の最上位メニューの作成を必要とするケースは、まれです。テーマが WordPress にまったく新しいコンセプトを導入し、それを実現するために多数の画面を必要とする場合、そのテーマは、新規の最上位メニューを設ける価値があるかもしれません。WordPress が本来想定していない機能を実現するために、複数の関連画面が必要不可欠な場合にのみ、最上位メニューの追加を検討すべきです。新規の最上位メニューの例としては、ジョブ管理や会議管理などが挙げられます。ネイティブの [投稿タイプ](https://codex.wordpress.org/Glossary#Post_Type) 登録では、WordPress がこの種の機能を管理するための、最上位メニューを自動的に作成することに注意してください。

<!-- 
If the creation of a top-level menu is not necessary, you need to decide under what top-level menu to place your new sub-level menu item. As a point of reference, several themes add sub-level menu items underneath existing WordPress top-level menus.
 -->

最上位メニューの作成が不要な場合、あなたの新規の下位メニュー項目を、どの最上位メニュー下に配置するかを、決定する必要があります。参考までに、いくつかのテーマでは、既存の WordPress 最上位メニュー下に、下位メニュー項目を追加します。

<!-- 
Use this guide of the WordPress top-level menus to determine the correct location for your sub-level menu item:
 -->

WordPress の最上位メニューの本ガイドを使用して、あなたの下位メニュー項目の、正しい配置場所を決定しましょう:

<!-- 
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
 -->

*   ダッシュボード – あなたのサイトの情報の中枢であり、WordPress のコア、プラグイン、テーマを更新するための「更新」オプションが含まれています。
*   投稿 – 投稿 (時間軸に沿ったコンテンツ) 作成のためのツールを表示します。
*   メディア – あなたの画像、動画、音声のアップロードしたり、管理します。
*   リンク – 興味のある他ブログやサイトへのリファレンスを管理します。
*   ページ – ページと称される、静的コンテンツ作成のためのツールを表示します。
*   コメント – 投稿への読者の反応をコントロールし管理します。
*   外観 – テーマ/スタイル・ファイル、サイドバーなどの操作に関するコントロールを提示します。
*   プラグイン – プラグイン自体の設定オプションではなく、プラグイン管理に関連するコントロールを表示します。
*   ユーザー – ユーザー管理のためのコントロールを表示します。
*   ツール – ブログ・データのエクスポート、インポート、さらにはバックアップを管理します。
*   設定 – 管理者だけが表示すべき、プラグイン・オプションを表示します。
*   ネットワーク管理者 –「ネットワーク」でセットされた、プラグイン・オプションを表示します。`admin_menu` の代わりに `network_admin_menu` を使用する必要があります ([ネットワークの作成](https://codex.wordpress.org/Create_A_Network) 参照)。

<!-- 
### Top-Level Menus
 -->

### 最上位メニュー

<!-- 
If you have decided your theme requires a brand-new top-level menu, the first thing you’ll need to do is to create one with the `add_menu_page()` function. *Note:* skip to [Sub-Level Menus](#sub-level-menus) if you don’t need a top-level menu.
 -->

あなたのテーマにまったく新規の最上位メニューが必要だと判断した場合、最初に `add_menu_page()` 関数を使用して、メニューを作成する必要があります。*注:* 最上位メニューが不要な場合は、[下位レベル・メニュー](#sub-level-menus) にスキップしましょう。

<!-- 
Parameter values:
 -->

パラメータ値:

<!-- 
*   `page_title` – the text to be displayed in the title tags of the page when the menu is selected.
*   `menu_title` – the on-screen name text for the menu.
*   `capability` – the capability required for this menu to be displayed to the user. When using the Settings API to handle your form, you should use `manage_options` here as the user won’t be able to save options without it. User levels are deprecated and should not be used here.
*   `menu_slug` – the slug name to refer to this menu by (should be unique for this menu). Prior to Version 3.0 this was called the file (or handle) parameter. If the function parameter is omitted, the `menu_slug` should be the PHP file that handles the display of the menu page content.
*   `function` – the function that displays the page content for the menu page.
*   `icon_url` – the URL to the icon to be used for this menu. This parameter is optional.
*   `position` – the position in the menu order this menu should appear. By default, if this parameter is omitted, the menu will appear at the bottom of the menu structure. To see the current menu positions, use `print_r( $GLOBALS[ 'menu' ] )` after the menu has loaded.
*   Sub-Level Menus – once your top-level menu is defined, or you have chosen to use an existing WordPress top-level menu, you are ready to define one or more sub-level menu items using the `add_submenu_page()` function.
 -->

*   `page_title` – メニューが選択された際に、ページのタイトル・タグに表示されるテキストです。
*   `menu_title` – メニューの「画面上に表示される」名称テキストです。
*   `capability` – 本メニューをユーザーに表示するために必要な権限です。設定 API を使用してあなたのフォームを処理する場合、ユーザーはこの権限なしではオプションを保存できないため、ここでは `manage_options` を使用する必要があります。ユーザー・レベルは非推奨であり、ここでは使用しないでください。
*   `menu_slug` – 本メニューを参照するための (このメニュー内で一意である必要がある) スラッグ名称です。v3.0以前は、これはファイル (またはハンドル) パラメータと呼ばれていました。関数パラメータが省略された場合、`menu_slug` は、メニュー・ページ・コンテンツの表示を処理する、PHP ファイルである必要があります。
*   `function` – メニュー・ページにおける、ページ・コンテンツを表示する関数です。
*   `icon_url` – 本メニューで使用する、アイコンの URL です。本パラメータは、任意です。
*   `position` – メニュー内で本メニューが表示される順位です。デフォルトでは、本パラメータが省略された場合、メニューはメニュー構造の最下部に表示されます。現在のメニュー順位を確認するには、メニュー・ロード後に `print_r( $GLOBALS[ 'menu' ] )` を使用しましょう。
*   下位レベル・メニュー – あなたの最上位メニューを定義した後、または既存の WordPress 最上位メニューを使用することを選択した後、`add_submenu_page()` 関数を使用して、1つ以上の下位レベル・メニュー項目を定義する準備が整います。

<!-- 
### Sub-Level Menus
 -->

### 下位レベル・メニュー

<!-- 
If you want your new menu item to be a sub-menu item, you can create it using the `add_submenu_page()` function instead.
 -->

あなたの新規メニュー項目を、下位メニュー項目として追加したい場合は、代わりに `add_submenu_page()` 関数を使用して、作成できます。

<!-- 
Parameter values:
 -->

パラメータ値:

<!-- 
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
 -->

*   `parent_slug` – 親メニューのスラッグ名称、またはあなたの下位メニューを挿入したい最上位メニューを提供する、標準 WordPress 管理ファイルのファイル名、あるいはこの下位メニューをカスタム最上位メニューに配置する場合の、あなたのプラグイン・ファイル名です。例:
    *   ダッシュボード – `add_submenu_page('index.php', ...)`
    *   投稿 – `add_submenu_page('edit.php', ...)`
    *   メディア – `add_submenu_page('upload.php', ...)`
    *   リンク – `add_submenu_page('link-manager.php', ...)`
    *   ページ – `add_submenu_page('edit.php?post_type=page', ...)`
    *   コメント – `add_submenu_page('edit-comments.php', ...)`
    *   カスタム投稿タイプ – `add_submenu_page('edit.php?post_type=your_post_type', ...)`
    *   外観 – `add_submenu_page('themes.php', ...)`
    *   プラグイン – `add_submenu_page('plugins.php', ...)`
    *   ユーザー – `add_submenu_page('users.php', ...)`
    *   ツール – `add_submenu_page('tools.php', ...)`
    *   設定 – `add_submenu_page('options-general.php', ...)`
*   `page_title` – 下位メニューが選択された際に、ページの HTML ページ・タイトルに挿入される、テキストです。
*   `menu_title` – メニューが選択された際に、ページのタイトル・タグに表示される、テキストです。
*   `capability` – 本メニューをユーザーに表示するために必要な、権限です。ユーザー・レベルは非推奨であり、ここでは使用しないでください。
*   `menu_slug` – 既存の WordPress メニューの場合は、メニュー・ページのコンテンツ表示を処理する PHP ファイルです。カスタム最上位メニューの下位メニューの場合は、本下位メニュー・ページの一意の識別子です。
*   `function` – メニュー・ページのコンテンツをページに表示する関数です。技術的には、`add_menu_page` 関数と同様に、この関数パラメータは任意ですが、指定しない場合、WordPress は基本的に、関数をコールせずとも PHP ファイルのインクルードによって管理画面が生成されると想定します。

<!-- 
### Using Wrapper Functions
 -->

### ラッパー関数の使用

<!-- 
Since most sub-level menus belong under the Settings, Tools, or Appearance menus, WordPress supplies wrapper functions that make adding a sub-level menu items to these top-level menus easier. Note that the function names may not match the names seen in the admin UI as they have changed over time:
 -->

ほとんどの下位メニューは設定、ツール、または外観メニュー下に属するため、WordPress ではこれらの最上位メニューに下位メニュー項目を追加しやすくする、ラッパー関数を用意しています。なお、時間の経過とともに変更されているため、関数名は、管理画面 UI で表示される名称と一致しない場合があることに、注意してください:

<!-- 
#### Dashboard
 -->

#### ダッシュボード

```php
<?php
add_dashboard_page(
	$page_title,
	$menu_title,
	$capability,
	$menu_slug,
	$function
);
```

<!-- 
#### Posts
 -->

#### 投稿

```php
<?php
add_posts_page(
	$page_title,
	$menu_title,
	$capability,
	$menu_slug,
	$function
);
```

<!-- 
#### Media
 -->

#### メディア

```php
<?php
add_media_page(
	$page_title,
	$menu_title,
	$capability,
	$menu_slug,
	$function
);
```

<!-- 
#### Links
 -->

#### リンク

```php
<?php
add_links_page(
	$page_title,
	$menu_title,
	$capability,
	$menu_slug,
	$function
);
```

<!-- 
#### Pages
 -->

#### ページ

```php
<?php
add_pages_page(
	$page_title,
	$menu_title,
	$capability,
	$menu_slug,
	$function
);
```

<!-- 
#### Comments
 -->

#### コメント

```php
add_comments_page(
	$page_title,
	$menu_title,
	$capability,
	$menu_slug,
	$function
);
```

<!-- 
#### Appearance
 -->

#### 外観

```php
<?php
add_theme_page(
	$page_title,
	$menu_title,
	$capability,
	$menu_slug,
	$function
);
```

<!-- 
#### Plugins
 -->

#### プラグイン

```php
<?php
add_plugins_page(
	$page_title,
	$menu_title,
	$capability,
	$menu_slug,
	$function
);
```

<!-- 
#### Users
 -->

#### ユーザー

```php
<?php
add_users_page(
	$page_title,
	$menu_title,
	$capability,
	$menu_slug,
	$function
);
```

<!-- 
#### Tools
 -->

#### ツール

```php
<?php
add_management_page(
	$page_title,
	$menu_title,
	$capability,
	$menu_slug,
	$function
);
```

<!-- 
#### Settings
 -->

#### 設定

```php
<?php
add_options_page(
	$page_title,
	$menu_title,
	$capability,
	$menu_slug,
	$function
);
```

<!-- 
Also see [Theme Options](https://developer.wordpress.org/themes/customize-api/) for the currently recommended way of creating options via the Customizer API.
 -->

また、カスタマイザー API を介してオプションを作成する、現在推奨されている方法については、[テーマ・オプション](https://developer.wordpress.org/themes/customize-api/) もご覧ください。

<!-- 
### Example
 -->

### 例

<!-- 
Here’s a quick example illustrating how to insert a top-level menu page and a sub-menu page, where the title on the sub-menu page is different from the top-level page. In this example, `register_my_theme_more_settings_menu` is the name of the function that displays the first sub-menu page:
 -->

以下は、最上位メニュー・ページと下位メニュー・ページを挿入する、簡単な例です。下位メニュー・ページのタイトルは、最上位ページとは異なります。本例では、`register_my_theme_more_settings_menu` は、最初の下位メニュー・ページを表示する、関数の名称です:

```php
<?php
function register_my_theme_settings_menu() {
	add_menu_page(
		"My Theme's Settings",
		'My Theme',
		'manage_options',
		'my-theme-settings-menu'
	);
}

function register_my_theme_more_settings_menu() {
	add_submenu_page(
		'my-theme-settings-menu',
		'More Settings for My Theme',
		'More Settings',
		'manage_options',
		'my-theme-more-settings-menu'
	);
}

add_action( 'admin_menu', 'register_my_theme_settings_menu' );
add_action( 'admin_menu', 'register_my_theme_more_settings_menu' );
```

<!-- 
Here’s an example of adding an option page under a custom post type menu block (see also here):
 -->

以下は、カスタム投稿タイプのメニュー・ブロック下に、オプション・ページを追加する例です (参照):

<!-- 
CODE
 -->

コード

<!-- 
## Inserting the Pages
 -->

## ページの挿入

<!-- 
Here is an example of how to insert multiple menus into various places:
 -->

以下は、複数のメニューを、さまざまな場所に挿入する方法の例です:

```php
<?php
// Hook for adding admin menus
add_action( 'admin_menu', 'mt_add_pages' );

// Action function for hook above
function mt_add_pages() {
	// Add a new submenu under Settings:
	add_options_page( __( 'Test Settings', 'menu-test' ), __( 'Test Settings', 'menu-test' ), 'manage_options', 'testsettings', 'mt_settings_page' );

	// Add a new submenu under Tools:
	add_management_page( __( 'Test Tools', 'menu-test' ), __( 'Test Tools', 'menu-test' ), 'manage_options', 'testtools', 'mt_tools_page' );

	// Add a new top-level menu (ill-advised):
	add_menu_page( __( 'Test Toplevel', 'menu-test' ), __( 'Test Top-level', 'menu-test' ), 'manage_options', 'mt-top-level-handle', 'mt_toplevel_page' );

	// Add a submenu to the custom top-level menu:
	add_submenu_page( 'mt-top-level-handle', __( 'Test Sub-Level', 'menu-test' ), __( 'Test Sub-Level', 'menu-test' ), 'manage_options', 'sub-page', 'mt_sublevel_page' );

	// Add a second submenu to the custom top-level menu:
	add_submenu_page( 'mt-top-level-handle', __( 'Test Sub-Level 2', 'menu-test' ), __( 'Test Sub-Level 2', 'menu-test' ), 'manage_options', 'sub-page2', 'mt_sublevel_page2' );
}

// mt_settings_page() displays the page content for the Test settings sub-menu.
function mt_settings_page() {
	echo '</pre><h2>' . __( 'Test Settings', 'menu-test' ) . '</h2><pre>';
}

// mt_tools_page() displays the page content for the Test Tools sub-menu.
function mt_tools_page() {
	echo '</pre><h2>' . __( 'Test Tools', 'menu-test' ) . '</h2><pre>';
}

// mt_toplevel_page() displays the page content for the custom Test Top-Level menu.
function mt_toplevel_page() {
	echo '</pre><h2>' . __( 'Test Top-Level', 'menu-test' ) . '</h2><pre>';
}

// mt_sublevel_page() displays the page content for the first sub-menu of the custom Test Toplevel menu.
function mt_sublevel_page() {
	echo '</pre><h2>' . __( 'Test Sub-Level', 'menu-test' ) . '</h2><pre>';
}

// mt_sublevel_page2() displays the page content for the second sub-menu of the custom Test Top-Level menu.
function mt_sublevel_page2() {
	echo '</pre><h2>' . __( 'Test Sub-Level 2', 'menu-test' ) . '</h2><pre>';
}
```

<!-- 
## Sample Menu Page
 -->

## サンプル・メニュー・ページ

<!-- 
*Note:* See the [Settings API](https://codex.wordpress.org/Settings_API) for information on creating settings pages.
 -->

*注:* 設定ページの作成方法については、[設定 API](https://codex.wordpress.org/Settings_API) をご覧ください。

<!-- 
The previous example contains several dummy functions, such as `mt_settings_page()`, as placeholders for actual page content. Let’s expand on them. What if you wanted to create an option called `mt_favorite_color` that allows the site owner to type in their favorite color via a Settings page? The `mt_options_page()` function will need to output a data entry form on the screen, as well as to process the entered data.
 -->

前の例には、実際のページ・コンテンツのプレースホルダーとして、`mt_settings_page()` などのダミー関数がいくつか含まれています。これらを拡張してみましょう。サイト所有者が設定ページ経由でお気に入り色を入力できる、`mt_favorite_color` というオプションを作成したい場合、どうすれば良いでしょう ? `mt_options_page()` 関数は、画面上にデータ入力フォームを出力するとともに、入力されたデータを処理する必要があります。

<!-- 
Here is a function that does this:
 -->

以下は、その処理を行う関数です:

```php
<?php
// mt_settings_page() displays the page content for the Test settings sub-menu.
function mt_settings_page() {
	// Must check that the user has the required capability.
	if ( ! current_user_can( 'manage_options' ) ) {
		wp_die( __( 'You do not have sufficient permissions to access this page.' ) );
	}

	// Variables for the field and option names
	$opt_name          = 'mt_favorite_color';
	$hidden_field_name = 'mt_submit_hidden';
	$data_field_name   = 'mt_favorite_color';

	// Read in existing option value from database
	$opt_val = get_option( $opt_name );

	// See if the user has posted us some information. If they did, this hidden field will be set to 'Y'.
	if ( isset( $_POST[ $hidden_field_name ] ) && $_POST[ $hidden_field_name ] == 'Y' ) {
		// Read their posted value.
		$opt_val = $_POST[ $data_field_name ];

		// Save the posted value in the database.
		update_option( $opt_name, $opt_val );

		// Put a "Settings updated" message on the screen
		?>
		<div class="updated"></div><!-- .updated -->

		<div class="wrap">
			<?php echo '<h2>' . __( 'Menu Test Settings', 'menu-test' ) . '</h2>'; ?>
			<form action="" method="post" name="form1"></form>
			<?php _e( 'Favorite Color:', 'menu-test' ); ?>
			<hr />
		</div><!-- .wrap -->

		<?php
	}
}
```

<!-- 
**A few notes:**
 -->

**補足事項:**

<!-- 
*   The WordPress functions such as `add_menu_page()` and `add_submenu_page()` take a capability which will be used to determine whether the top-level or sub-level menu is displayed.
*   The function which is hooked in to handle the output of the page must check that the user has the required capability as well.
*   The WordPress administration functions take care of validating the user login, so you don’t have to worry about it in your function.
*   The function example above has been internationalized — see the [I18n for WordPress Developers](https://codex.wordpress.org/I18n_for_WordPress_Developers) for more details.
*   The function processes any entered data before putting the data entry form on the screen, so that the new values will be shown in the form (rather than the values from the database).
*   You don’t have to worry about this working the first time, because the WordPress `update_option` function will automatically add an option to the database if it doesn’t already exist.
*   These admin-menu-adding procedures are parsed every single time you navigate to a page in Admin. So if you are writing a theme which has no options page, but add one later, you can just add it using the instructions above and re-upload, and tweak until you’re happy with it. In other words, menus are not “permanently added” or put into a database upon activating a theme. They’re parsed on the fly, so you can add or subtract menu items at will, re-upload, and the change will be reflected right away.
 -->

*   `add_menu_page()` や `add_submenu_page()` などの WordPress 関数は、最上位メニューまたは下位メニューのどちらが表示されるかを判断するために使用される、権限を必要とします。
*   ページの出力処理を扱うフック関数では、ユーザーが必要な権限を持っていることも確認する必要があります。
*   WordPress の管理関数は、ユーザー・ログインの検証を処理するため、あなたの関数内でその点を気にする必要はありません。
*   上記の関数例は、国際化対応済みです — 詳細は [WordPress 開発者向け i18n (国際化)](https://codex.wordpress.org/I18n_for_WordPress_Developers) をご覧ください。
*   この関数は、画面にデータ入力フォームを表示する前に、入力されたデータを処理するので、フォームには (データベース内の値ではなく) 新しい値が表示されます。
*   WordPress の `update_option` 関数は、データベースにオプションが存在しない場合、自動的に追加するため、初めて実行しても動作しない心配はありません。
*   これらの管理メニュー追加手順は、管理画面でページに移動するたびに毎回解析されます。したがって、オプションページを持たないテーマを作成中で、後から追加する場合、上記の手順で追加して再アップロードし、満足いくまで調整できます。つまり、メニューはテーマ有効化時に「恒久的に追加」されたり、データベースに保存されたりすることは、ありません。メニューは動的に解析されるため、メニュー項目を自由に追加・削除し、再アップロードすれば変更が即座に反映されます。

<!-- 
## Page Hook Suffix
 -->

## ページ・フック接尾辞

<!-- 
Every function that adds a new administration menu – `add_menu_page()`, `add_submenu_page()` and its specialized versions such as `add_options_page()` – returns a special value called **Page Hook Suffix**. It can be used later as a hook to which an action called only on that particular page can be registered.
 -->

新規管理メニューを追加するすべての関数 – `add_menu_page()`、`add_submenu_page()` および `add_options_page()` のようなその特殊バージョン – は、**ページ・フック接尾辞** と呼ばれる、特別な値を返します。後で、その特定のページでのみコールされるアクションを登録するための、フックとして使用できます。

<!-- 
One such action hook is `load-{page_hook}`, where `{page_hook}` is the value returned by one of these `add_*_page()` functions. This hook is called when the particular page is loaded. In the example below, it is used to display the “Theme is not configured” notice on all admin pages except for plugin’s options page:
 -->

そのようなアクション・フックの一つが `load-{page_hook}` であり、ここで `{page_hook}` はこれらの `add_*_page()` 関数のいずれかが返す値です。本フックは、特定のページがロードされた際にコールされます。以下の例では、プラグインのオプション・ページを除くすべての管理ページに「テーマが設定されていません」という通知を表示するために、使用されます:

```php
<?php
add_action( 'admin_menu', 'my_menu' );

// Here you can check if plugin is configured (e.g. check if some option is set). If not, add new hook.
// In this example hook is always added.
add_action( 'admin_notices', 'my_admin_notices' );

function my_menu() {
	// Add the new admin menu and page and save the returned hook suffix
	$hook_suffix = add_options_page( 'My Options', 'My Theme', 'manage_options', 'my-unique-identifier', 'my_options' );
	// Use the hook suffix to compose the hook and register an action executed when plugin's options page is loaded
	add_action( 'load-' . $hook_suffix, 'my_load_function' );
}

function my_load_function() {
	// Current admin page is the options page for our plugin, so do not display the notice
	// (remove the action responsible for this)
	remove_action( 'admin_notices', 'my_admin_notices' );
}

function my_admin_notices() {
	echo '<pre><div class="updated fade" id="notice">My Plugin is not configured yet. Please do it now.</div></pre>';
}

function my_options() {
	if ( ! current_user_can( 'manage_options' ) ) {
		wp_die( __( 'You do not have sufficient permissions to access this page.' ) );
	}

	echo '</pre><div class="wrap">';
	echo 'Here is where the form would go if I actually had options.';
	echo '</div><pre>';
}
```

<!-- 
## Resources
 -->

## リソース

<!-- 
[Top Level Menu discussion on wp-hackers  
](http://comox.textdrive.com/pipermail/wp-hackers/2009-February/024632.html)[Admin Menu Editor Plugin](https://wordpress.org/extend/plugins/admin-menu-editor/)
 -->

[wp-hackers での、最上位メニューに関する議論](http://comox.textdrive.com/pipermail/wp-hackers/2009-February/024632.html)
[管理メニュー・エディター・プラグイン](https://wordpress.org/extend/plugins/admin-menu-editor/)