<!-- 
# Linking Theme Files &amp; Directories
 -->

# テーマ・ファイル &amp; ディレクトリのリンク

<!-- 
## Linking to Core Theme Files
 -->

## コア・テーマ・ファイルへのリンク

<!-- 
As you’ve learned, WordPress themes are built from a number of different template files. At the very least this will usually include a `sidebar.php`, `header.php` and `footer.php`. These are called using [Template Tags](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags"), for example:
 -->

ご存じのように、WordPress テーマは、複数の異なるテンプレート・ファイルから構築されています。少なくとも通常は、`sidebar.php`、`header.php`、`footer.php` が含まれます。これらは [テンプレート・タグ](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags") を使用してコールされ、たとえば:

<!-- 
*   [get\_header()](https://developer.wordpress.org/reference/functions/get_header/) ;
*   [get\_footer()](https://developer.wordpress.org/reference/functions/get_footer/) ;
*   [get\_sidebar()](https://developer.wordpress.org/reference/functions/get_sidebar/) ;
 -->

*   [get\_header()](https://developer.wordpress.org/reference/functions/get_header/) ;
*   [get\_footer()](https://developer.wordpress.org/reference/functions/get_footer/) ;
*   [get\_sidebar()](https://developer.wordpress.org/reference/functions/get_sidebar/) ;

<!-- 
You can create custom versions of these files can be called as well by naming the file `sidebar-{your_custom_template}.php`, `header-{your_custom_template}.php` and `footer-{your_custom_template}.php`. You can then use Template Tags with the custom template name as the only parameter, like this:
 -->

これらのファイルのカスタム版を、ファイル名を `sidebar-{your_custom_template}.php`、`header-{your_custom_template}.php` や `footer-{your_custom_template}.php` などと命名することでも、コール可能です。次に、カスタム・テンプレート名を唯一のパラメータとして、このように、テンプレート・タグを使用できます:

```php
get_header( 'your_custom_template' );
get_footer( 'your_custom_template' );
get_sidebar( 'your_custom_template' );
```

<!-- 
WordPress creates pages by assembling various files. Aside from the standard files for the header, footer and sidebar, you can create custom template files and call them at any location in the page using [get\_template\_part()](https://developer.wordpress.org/reference/functions/get_template_part/) . To create a custom template file in your theme give the file an appropriate name and use the same custom template system as with the header, sidebar and footer files:
 -->

WordPress は、さまざまなファイルを組み合わせて、ページを生成します。ヘッダー、フッター、サイドバー用の標準ファイルに加え、カスタム・テンプレート・ファイルを作成し、ページ内の任意の場所で [get\_template\_part()](https://developer.wordpress.org/reference/functions/get_template_part/) を使用してコールできます。あなたのテーマ内でカスタム・テンプレート・ファイルを作成するには、ファイルに適切な名前を付け、ヘッダー、サイドバー、フッターファイルと同様のカスタム・テンプレート・システムを使用します:

```php
slug-template.php
```

<!-- 
For example, if you would like to create a custom template to handle your post content you could create a template file called `content.php` and then add a specific content layout for product content by extending the file name to `content-product.php`. You would then load this template file in your theme like this:
 -->

たとえば、あなたの投稿コンテンツを扱うカスタム・テンプレートを作成したい場合、`content.php` というテンプレート・ファイルを作成し、ファイル名を `content-product.php` と拡張することで、商品コンテンツ用の特定のコンテンツ・レイアウトを追加できます。その後、あなたのテーマ内でこのテンプレート・ファイルを次のようにロードします:

```php
get_template_part( 'content', 'product' );
```

<!-- 
If you want to add more organization to your templates, you can place them in their own directories within your theme directory. For example, suppose you add a couple more *content* templates for *profiles* and *locations*, and group them in their own directory called `content-templates`.
 -->

あなたのテンプレートにさらに整理を加えたい場合は、あなたのテーマ・ディレクトリ内にそれら専用のディレクトリを作成できます。たとえば、*プロフィール* と *場所* 用の *コンテンツ* テンプレートをいくつか追加し、それらを `content-templates` という専用のディレクトリにグループ化するとしましょう。

<!-- 
The theme hierarchy for your theme called `my-theme` might look like the following. `style.css` and `page.php` are included for context.
 -->

`my-theme` というあなたのテーマのテーマ階層は、以下のようなものになるかもしれません。`style.css` と `page.php` は文脈のために含めています。

<!-- 
*   themes
*   my-theme
*   content-templates
*   content-location.php
*   content-product.php
*   content-profile.php
*   style.css
 -->

*   themes
*   my-theme
*   content-templates
*   content-location.php
*   content-product.php
*   content-profile.php
*   style.css

<!-- 
To include your content templates, prepend the directory names to the `slug` argument like this:
 -->

あなたのコンテンツ・テンプレートをインクルードするには、以下のように、`slug` 引数の前にディレクトリ名を付加してください:

```php
get_template_part( 'content-templates/content', 'location' );
get_template_part( 'content-templates/content', 'product' );
get_template_part( 'content-templates/content', 'profile' );
```

<!-- 
## Linking to Theme Directories
 -->

## テーマ・ディレクトリへのリンク

<!-- 
To link to the theme’s directory, you can use the following function:
 -->

テーマのディレクトリにリンクさせるには、以下の関数を使用できます:

<!-- 
*   [get\_theme\_file\_uri()](https://developer.wordpress.org/reference/functions/get_theme_file_uri/) ;
 -->

*   [get\_theme\_file\_uri()](https://developer.wordpress.org/reference/functions/get_theme_file_uri/) ;

<!-- 
If you are not using a child theme, this function will return the full URI to your theme’s main folder. You can use this to reference sub-folders and files in your theme like this:
 -->

子テーマを使用していない場合、本関数は、あなたのテーマのメイン・フォルダーへの完全な URI を返します。これを使用して、あなたのテーマ内のサブフォルダーやファイルを、次のように参照できます:

```php
echo get_theme_file_uri( 'images/logo.png' );
```

<!-- 
If you are using a child theme then this function will return the URI of the file in your child theme if it exists. If the file cannot be found in your child theme, the function will return the URI of the file in the parent theme. This is particularly important to keep in mind when distributing a theme or in any other case where a child theme may or may not be active.
 -->

子テーマを使用している場合、本関数はあなたの子テーマ内にファイルが存在すれば、そのファイルの URI を返します。あなたの子テーマ内でファイルが見つからない場合、関数は親テーマ内のファイルの URI を返します。テーマを配布する場合や、子テーマが有効になっているかどうかが不明な状況では、この点を特に留意することが重要です。

<!-- 
To access the path to a file in your theme’s directories, you can use the following function:
 -->

あなたのテーマのディレクトリ内のファイルへのパスにアクセスするには、次の関数を使用できます:

<!-- 
*   [get\_theme\_file\_path()](https://developer.wordpress.org/reference/functions/get_theme_file_path/) ;
 -->

*   [get\_theme\_file\_path()](https://developer.wordpress.org/reference/functions/get_theme_file_path/) ;

<!-- 
Like [get\_theme\_file\_uri()](https://developer.wordpress.org/reference/functions/get_theme_file_uri/) , this will access the path of the file in the child theme if it exists. If the file cannot be found in the child theme, the function will access the path to the file in the parent theme.
 -->

[get\_theme\_file\_uri()](https://developer.wordpress.org/reference/functions/get_theme_file_uri/) と同様に、この関数は子テーマ内にファイルが存在する場合、そのファイルのパスにアクセスします。子テーマ内でファイルが見つからない場合、この関数は親テーマ内のファイルへのパスにアクセスします。

<!-- 
In a child theme, you can link to a file URI or path in the parent theme’s directories using the following functions:
 -->

子テーマでは、以下の関数を使用して、親テーマのディレクトリ内のファイル URI またはパスにリンクできます:

<!-- 
*   [get\_parent\_theme\_file\_uri()](https://developer.wordpress.org/reference/functions/get_parent_theme_file_uri/) ;
*   [get\_parent\_theme\_file\_path()](https://developer.wordpress.org/reference/functions/get_parent_theme_file_path/) ;
 -->

*   [get\_parent\_theme\_file\_uri()](https://developer.wordpress.org/reference/functions/get_parent_theme_file_uri/) ;
*   [get\_parent\_theme\_file\_path()](https://developer.wordpress.org/reference/functions/get_parent_theme_file_path/) ;

<!-- 
As with  `get_theme_file_uri(),` you can reference sub-folders and files like this:  
 -->

`get_theme_file_uri()` と同様に、サブフォルダーやファイルを次のように参照できます:  

```php
echo get_parent_theme_file_uri( 'images/logo.png' );
//or
echo get_parent_theme_file_path( 'images/logo.png' );
```

<!-- 
Take care when referencing files that may not be present, as these functions will return the URI or file path whether the file exists or not. If the file is missing, these functions will return a broken link.
 -->

存在しない可能性のあるファイルを参照する際は、注意してください。これらの関数は、ファイルが存在するかどうかにかかわらず、URI またはファイルパスを返します。ファイルが存在しない場合、これらの関数は壊れたリンクを返します。

<!-- 
The functions [get\_theme\_file\_uri()](https://developer.wordpress.org/reference/functions/get_theme_file_uri/) , [get\_theme\_file\_path()](https://developer.wordpress.org/reference/functions/get_theme_file_path/) , [get\_parent\_theme\_file\_uri()](https://developer.wordpress.org/reference/functions/get_parent_theme_file_uri/) , [get\_parent\_theme\_file\_path()](https://developer.wordpress.org/reference/functions/get_parent_theme_file_path/) were introduced in WordPress 4.7.
 -->

関数 [get\_theme\_file\_uri()](https://developer.wordpress.org/reference/functions/get_theme_file_uri/)、[get\_theme\_file\_path()](https://developer.wordpress.org/reference/functions/get_theme_file_path/)、[get\_parent\_theme\_file\_uri()](https://developer.wordpress.org/reference/functions/get_parent_theme_file_uri/)、[get\_parent\_theme\_file\_path()](https://developer.wordpress.org/reference/functions/get_parent_theme_file_path/) は WordPress v4.7で導入されました。

<!-- 
For previous WordPress versions, use [get\_template\_directory\_uri()](https://developer.wordpress.org/reference/functions/get_template_directory_uri/) , [get\_template\_directory()](https://developer.wordpress.org/reference/functions/get_template_directory/) , [get\_stylesheet\_directory\_uri()](https://developer.wordpress.org/reference/functions/get_stylesheet_directory_uri/) , [get\_stylesheet\_directory()](https://developer.wordpress.org/reference/functions/get_stylesheet_directory/) .
 -->

WordPress の旧バージョンでは、[get\_template\_directory\_uri()](https://developer.wordpress.org/reference/functions/get_template_directory_uri/)、[get\_template\_directory()](https://developer.wordpress.org/reference/functions/get_template_directory/)、[get\_stylesheet\_directory\_uri()](https://developer.wordpress.org/reference/functions/get_stylesheet_directory_uri/)、[get\_stylesheet\_directory()](https://developer.wordpress.org/reference/functions/get_stylesheet_directory/) を使用してください。

<!-- 
Take note that the newer 4.7 functions run the older functions anyway as part of the checking process so it makes sense to use the newer functions when possible.
 -->

新しい4.7関数は、チェック・プロセスの一環として古い関数を実行するため、可能な限り、新しい関数を使用することが合理的です。

<!-- 
## Dynamic Linking in Templates
 -->

## テンプレート内での動的リンク

<!-- 
Regardless of your permalink settings, you can link to a page or post dynamically by referring to its unique numerical ID (seen in several pages in the admin interface) with  
 -->

あなたのパーマリンク設定にかかわらず、(管理インターフェースのいくつかのページで確認できる) 一意の数値 ID を参照することで、ページや投稿に動的にリンクできます。

```php
<a href="<?php echo get_permalink($ID); ?>">This is a link</a>
```

<!-- 
This is a convenient way to create page menus as you can later change page slugs without breaking links, as IDs will stay the same. However, this might increase database queries.
 -->

これはページ・メニューを作成するのに便利な方法で、ID は変わらないため、後でページ・スラッグをリンクを壊さずに変更できます。しかしながら、これによりデータベース・クエリーが増加する可能性があります。