<!-- 
# Sidebars
 -->

# サイドバー

<!-- 
## What are Sidebars
 -->

## サイドバーとは

<!-- 
A sidebar is any widgetized area of your theme. Widget areas are places in your theme where users can add their own widgets. You do not need to include a sidebar in your theme, but including a sidebar means users can add content to the widget areas through the Customizer or the Widgets Admin Panel.
 -->

サイドバーとは、あなたのテーマ内の任意のウィジェット対応エリアのことです。ウィジェットエリアとは、ユーザーが自身のウィジェットを追加できるあなたのテーマ内の場所です。あなたのテーマにサイドバーを含める必要はありませんが、サイドバーを含めることで、ユーザーは「カスタマイザー」または「ウィジェット管理パネル」を通じて、ウィジェットエリアにコンテンツを追加できます。

<!-- 
Widgets can be employed for a variety of purposes, ranging from listing recent posts to conducting live chats.
 -->

ウィジェットは、最近の投稿の表示からライブチャットの進行まで、さまざまな目的に活用できます。

<!-- 
The name “sidebars” comes from a time when widget areas were normally created in a long strip to the lefthand or righthand side of a blog. Today, sidebars have evolved beyond their original name. They can be included anywhere on your website. Think of a sidebar as **any area that contains widgets**.
 -->

「サイドバー」という名称は、ウィジェットエリアがブログの左手側または右手側に、細長い帯状に配置されていた時代に由来します。今日、サイドバーはその名称の由来を超えた進化を遂げています。あなたの Web サイト上のどこにでも配置できます。サイドバーとは、**ウィジェットを含むあらゆるエリア** ととらえましょう。

<!-- 
## Registering a Sidebar
 -->

## サイドバーの登録

<!-- 
To use sidebars, you must register them in `functions.php`.
 -->

サイドバーを使用するには、`functions.php` で登録する必要があります。

<!-- 
To begin, `register_sidebar()` has several parameters that should always be defined regardless of whether they are marked as optional. These include x, y, and z.
 -->

まず、`register_sidebar()` には、`optional` とマークされているかどうかにかかわらず、常に定義すべきパラメータがいくつかあります。これには x、y、z が含まれます。

<!-- 
*   **name** – your name for the sidebar. This is the name users will see in the Widgets panel.
*   **id** – must be lowercase. You will call this in your theme using the `dynamic_sidebar` function.
*   **description** – A description of the sidebar. This will also be shown in the admin Widgets panel.
*   **class** – The CSS class name to assign to the widget’s HTML.
*   **before\_widget** – HTML that is placed before every widget.
*   **after\_widget** – HTML that is placed after every widget. Should be used to close tags from `before_widget`.
*   **before\_title** – HTML that is placed before the title of each widget, such as a header tag.
*   **after\_title** – HTML that is placed after every title. Should be used to close tags from `before_title`.
 -->

*   **name** – サイドバーに付ける名称です。「ウィジェット」パネルに表示される名称になります。
*   **id** – 小文字で指定する必要があります。あなたのテーマでは `dynamic_sidebar` 関数を使用してこれをコールします。
*   **description** – サイドバーの説明文です。管理画面の「ウィジェット」パネルにも表示されます。
*   **class** – ウィジェットの HTML に割り当てる、CSS クラス名です。
*   **`before_widget`** – 各ウィジェットの前に配置される HTML です。
*   **`after_widget`** – 各ウィジェットの後に配置される HTML です。`before_widget` で開始したタグを閉じるために使用します。
*   **`before_title`** – ヘッダータグなど、各ウィジェットのタイトル前に配置される HTML です。
*   **`after_title`** – 各タイトル後に配置される HTML です。`before_title` で開始したタグを閉じるために使用します。

<!-- 
To register a sidebar we use `register_sidebar` and the `widgets_init` function.
 -->

サイドバーを登録するには、`register_sidebar` と `widgets_init` 関数を使用します。

```php
<?php
function themename_widgets_init() {
	register_sidebar( array(
		'name'          => __( 'Primary Sidebar', 'theme_name' ),
		'id'            => 'sidebar-1',
		'before_widget' => '<aside id="%1$s" class="widget %2$s">',
		'after_widget'  => '</aside>',
		'before_title'  => '<h3 class="widget-title">',
		'after_title'   => '</h3>',
	) );
	register_sidebar( array(
		'name'          => __( 'Secondary Sidebar', 'theme_name' ),
		'id'            => 'sidebar-2',
		'before_widget' => '<ul><li id="%1$s" class="widget %2$s">',
		'after_widget'  => '</li></ul>',
		'before_title'  => '<h3 class="widget-title">',
		'after_title'   => '</h3>',
	) );
}
```

<!-- 
Registering a sidebar tells WordPress that you’re creating a new widget area in **Appearance > Widgets** that users can drag their widgets to. There are two functions for registering sidebars:
 -->

サイドバーを登録すると、WordPress は **外観 > ウィジェット** でユーザーがウィジェットをドラッグできる、新規ウィジェットエリアが作成されたことを認識します。サイドバーを登録する関数は、2つあります:

<!-- 
*   [register\_sidebar()](https://developer.wordpress.org/reference/functions/register_sidebar/)
*   [register\_sidebars()](https://developer.wordpress.org/reference/functions/register_sidebars/)
 -->

*   [`register_sidebar()`](https://developer.wordpress.org/reference/functions/register_sidebar/)
*   [`register_sidebars()`](https://developer.wordpress.org/reference/functions/register_sidebars/)

<!-- 
The first lets you register one sidebar and the second lets you register multiple sidebars.
 -->

前者は1つのサイドバーを登録でき、後者は複数のサイドバーを登録できます。

<!-- 
It is recommended that you register sidebars individually as it allows you to give unique and descriptive names to each sidebar.
 -->

個々のサイドバーに固有でわかりやすい名前を付けることができるため、サイドバーは個別に登録することをおすすめします。

<!-- 
## Examples
 -->

## 例

<!-- 
For widget areas in header and footer, it makes sense to name them “Header Widget Area” and “Footer Widget Area”,  rather than “Sidebar 1” and “Sidebar 2” (which is the default). This provides a useful description of where the sidebar is located.
 -->

ヘッダーとフッターのウィジェットエリアに名前を付ける場合、(デフォルトの)「サイドバー1」や「サイドバー2」ではなく、「ヘッダーウィジェットエリア」や「フッターウィジェットエリア」と命名するのが適切です。これにより、サイドバーの位置を明確に伝えられます。

<!-- 
The following code, added to `functions.php` registers a sidebar:
 -->

以下のコードを `functions.php` に追加すると、サイドバーを登録します:

```php
<?php
add_action( 'widgets_init', 'my_register_sidebars' );
function my_register_sidebars() {
	/* Register the 'primary' sidebar. */
	register_sidebar(
		array(
			'id'            => 'primary',
			'name'          => __( 'Primary Sidebar' ),
			'description'   => __( 'A short description of the sidebar.' ),
			'before_widget' => '<div id="%1$s" class="widget %2$s">',
			'after_widget'  => '</div>',
			'before_title'  => '<h3 class="widget-title">',
			'after_title'   => '</h3>',
		)
	);
	/* Repeat register_sidebar() code for additional sidebars. */
}
```

<!-- 
The code does the following:
 -->

このコードは、以下のことを行います:

<!-- 
*   `register_sidebar` – tells WordPress that you’re registering a sidebar
*   `'name' => __( 'Primary Widget Area', 'mytheme' ),` – is the widget area’s name that will appear in Appearance > Widgets
*   `'id' => 'sidebar-1'` – assigns an ID to the sidebar. WordPress uses ‘id’ to assign widgets to a specific sidebar.
*   `before_widget`/`after_widget` – a wrapper element for widgets assigned to the sidebar. The “%1$s” and “%2$s” should always be left in `id` and `class` respectively so that plugins can make use of them. By default, WordPress sets these as list items but in the above example they have been altered to div.
*   `before_title`/`after_title` – the wrapper elements for the widget’s title. By default, WordPress sets it to h2 but using h3 makes it more semantic.
 -->

*   `register_sidebar` – サイドバーの登録を、WordPress に通知します。
*   `'name' => __( 'Primary Widget Area', 'mytheme' ),` – **外観 > ウィジェット** に表示される、ウィジェットエリアの名称です。
*   `'id' => 'sidebar-1'` – サイドバーに ID を割り当てます。WordPress は、「id」を使用して、特定のサイドバーにウィジェットを割り当てます。
*   `before_widget`/`after_widget` – サイドバーに割り当てられた、ウィジェット用のラッパー要素です。プラグインが利用できるように、`%1$s` と `%2$s` は常にそれぞれ `id` と `class` に残しておく必要があります。デフォルトでは、WordPress は、これらをリスト項目として設定しますが、上記の例では `div` に変更されています。
*   `before_title`/`after_title` – ウィジェットのタイトル用のラッパー要素です。デフォルトでは、WordPress は `h2` に設定しますが、`h3` を使用することで、よりセマンティックにできます。

<!-- 
Once your sidebar is registered, you can display it in your theme.
 -->

あなたのサイドバーを登録したら、あなたのテーマで表示できます。

<!-- 
## Displaying Sidebars in your Theme
 -->

## あなたのテーマでの、サイドバーの表示

<!-- 
Now that your sidebars are registered, you will want to display them  in  your theme. To do this, there are two steps:
 -->

さあ、あなたのサイドバーが登録されたので、あなたのテーマに表示させたいと思うでしょう。これを行うには、次の2つのステップがあります:

<!-- 
1.  Create the `sidebar.php` template file and display the sidebar using the `dynamic_sidebar` function
2.  Load in your theme using the `get_sidebar` function
 -->

1.  `sidebar.php` テンプレートファイルを作成し、`dynamic_sidebar` 関数を使用してサイドバーを表示します。
2.  `get_sidebar` 関数を使用して、あなたのテーマをロードします。

<!-- 
### Create a Sidebar Template File
 -->

### サイドバーテンプレートファイルの作成

<!-- 
A sidebar template contains the code for your sidebar. WordPress recognizes the file  `sidebar.php`  and any template file with the name `sidebar-{name}.php`.  This means that you can organize your files with each sidebar in its own template file.
 -->

サイドバーテンプレートには、あなたのサイドバー用のコードが含まれます。WordPress は、ファイル `sidebar.php` と、`sidebar-{name}.php` という名称の任意のテンプレートファイルを認識します。これは、各サイドバーをそれぞれ独自テンプレートファイルで管理できることを意味します。

<!-- 
### Example:
 -->

### 例:

<!-- 
1\. Create `sidebar-primary.php`

2\. Add the following code:
 -->

1. `sidebar-primary.php` を作成します。
2. 以下のコードを追加します:

```php
<div id="sidebar-primary" class="sidebar">
	<?php dynamic_sidebar( 'primary' ); ?>
</div>
```

<!-- 
Note that `dynamic_sidebar` takes a single parameter of `$index`, which can be either the sidebar’s name or id.
 -->

`dynamic_sidebar` は、サイドバーの名称または ID のいずれかである、`$index` という単一のパラメータを受け取ることに注意しましょう。

<!-- 
### Load your Sidebar
 -->

### あなたのサイドバーのロード

<!-- 
To load your sidebar in your theme, use the `get_sidebar` function. This should be inserted into the template file where you want the sidebar to display. To load the default `sidebar.php` use the following:
 -->

あなたのテーマであなたのサイドバーをロードするには、`get_sidebar` 関数を使用しましょう。これは、サイドバーを表示させたいテンプレートファイルに挿入する必要があります。デフォルトの `sidebar.php` をロードするには、以下のコードを使用しましょう:

```php
<?php get_sidebar(); ?>
```

<!-- 
To display the Primary sidebar, pass the `$name` parameter to the function:
 -->

「プライマリ」サイドバーを表示するには、関数に `$name` パラメータを渡します:

```php
<?php get_sidebar( 'primary' ); ?>
```

<!-- 
## Customizing your Sidebar
 -->

## あなたのサイドバーの、カスタマイズ

<!-- 
There are lots of ways that you can customize your sidebars. Here are some examples:
 -->

あなたのサイドバーをカスタマイズする方法は、たくさんあります。以下にいくつかの例を示します:

<!-- 
### Display Default Sidebar Content
 -->

### デフォルトのサイドバーコンテンツの表示

<!-- 
You may wish to display content if the user hasn’t added any widgets to the sidebar yet. To do this, you use the `is_sidebar_active()` function to check to see if the sidebar has any widgets. This accepts the `$index` parameter which should be the ID of the sidebar that you wish to check.
 -->

ユーザーがサイドバーにウィジェットを追加していない場合、コンテンツを表示したい場合があります。これを行うには、`is_sidebar_active()` 関数を使用して、サイドバーにウィジェットが存在するか否かをチェックします。この関数は、チェック対象のサイドバーの ID を表す `$index` パラメータを受け取ります。

<!-- 
This code checks to see if the sidebar is active, if not it displays some content:
 -->

このコードは、サイドバーがアクティブか否かをチェックし、非アクティブの場合は、任意のコンテンツを表示します:

```php
<div id="sidebar-primary" class="sidebar">
	<?php if ( is_active_sidebar( 'primary' ) ) : ?>
		<?php dynamic_sidebar( 'primary' ); ?>
	<?php else : ?>
		<!-- Time to add some widgets! -->
	<?php endif; ?>
</div>
```

<!-- 
### Display Default Widgets
 -->

### デフォルトのウィジェットの表示

<!-- 
You may want your sidebar to be populated with some widgets by default. For example, display the Search, Archive, and Meta Widgets.  To do this you would use:
 -->

デフォルトで、あなたのサイドバーにいくつかのウィジェットを表示させたい場合もあるでしょう。たとえば、「検索」ウィジェット、「アーカイブ」ウィジェット、「メタ」ウィジェットを表示する、などです。これを行うには、以下を使用します:

```php
<div id="primary" class="sidebar">

	<?php do_action( 'before_sidebar' ); ?>

	<?php if ( ! dynamic_sidebar( 'sidebar-primary' ) ) : ?>

		<aside id="search" class="widget widget_search">
			<?php get_search_form(); ?>
		</aside><!-- #search -->

		<aside id="archives" class"widget">
			<h3 class="widget-title"><?php _e( 'Archives', 'shape' ); ?></h3>
			<ul>
				<?php wp_get_archives( array( 'type' => 'monthly' ) ); ?>
			</ul>
		</aside><!-- #archives -->

		<aside id="meta" class="widget">
			<h3 class="widget-title"><?php _e( 'Meta', 'shape' ); ?></h3>
			<ul>
				<?php wp_register(); ?>
				<li><?php wp_loginout(); ?></li>
				<?php wp_meta(); ?>
			</ul>
		</aside><!-- #meta -->

	<?php endif; ?>

</div><!-- #primary -->
```