<!-- 
# Reworking Theme Files &amp; Organization
 -->

# テーマ・ファイルの再構築 &amp; 編成

<!-- 
![basics-theme-files-organization-01](https://i0.wp.com/developer.wordpress.org/files/2014/08/basics-theme-files-organization-01.jpg?resize=1024%2C384&ssl=1)
 -->

![basics-theme-files-organization-01](https://i0.wp.com/developer.wordpress.org/files/2014/08/basics-theme-files-organization-01.jpg?resize=1024%2C384&ssl=1)

<!-- 
## Theme folder and file structure
 -->

## テーマ・フォルダーとファイルの構造

<!-- 
While WordPress themes technically only require two files (`index.php` and `style.css`), they usually are made up of many files and can become quickly disorganized.
 -->

WordPress テーマは、技術的には2つのファイル (`index.php` および `style.css`) のみで構成されますが、実際には多くのファイルで構成されることが多く、すぐに無秩序になりがちです。

<!-- 
In the last section, [Template Files](# "Template Files"), you set up your `header.php, footer.php, page.php, home.php, and single.php` files.
 -->

前のセクション [テンプレート・ファイル](# "Template Files") では、あなたの `header.php、footer.php、page.php、home.php、single.php` ファイルを設定しました。

<!-- 
Let’s look at  the [Twenty Twelve theme](https://wordpress.org/themes/twentytwelve) default themes as one example of good file structure and organization.  While this may be a bit overwhelming at first, let’s break it down.  Can you find the templates you just built?
 -->

[Twenty Twelve テーマ](https://wordpress.org/themes/twentytwelve) デフォルト・テーマを、優れたファイル構造と編成の一例として見てみましょう。最初は少し圧倒されるかもしれませんが、分解して見ていきましょう。先程構築したテンプレートを見つけられますか ?

<!-- 
![basics-theme-files-organization-02](https://i0.wp.com/developer.wordpress.org/files/2014/08/basics-theme-files-organization-02.png?resize=629%2C1500&ssl=1)
 -->

![basics-theme-files-organization-02](https://i0.wp.com/developer.wordpress.org/files/2014/08/basics-theme-files-organization-02.png?resize=629%2C1500&ssl=1)

<!-- 
While there are still a lot of files, their names help provide a context of what they are.  Basically each file handles a feature of WordPress.  I.e. `comments.php` deals with how the theme will handle comments; `image.php` instructs the theme how to handle images, etc.  Don’t worry about adding these files unless you need them.
 -->

ファイルは依然として多いですが、それぞれのファイル名からその役割が推測できます。基本的に各ファイルは WordPress の機能を扱っています。たとえば、`comments.php` は、テーマがコメントをどう処理するかを定義します; `image.php` は、画像の処理方法をテーマに指示する、などです。これらのファイルを追加する必要がない限り、心配する必要はありません。

<!-- 
You can see that the main theme template files are in the theme’s root directory, while JavaScript, languages, CSS, and page template files are placed within their own folders.
 -->

メインテーマのテンプレート・ファイルは、テーマのルート・ディレクトリ内に配置されているのに対し、JavaScript、言語ファイル、CSS、ページ・テンプレート・ファイルは、それぞれ専用のフォルダー内に配置されていることがわかります。

<!-- 
At this time there are **no required folders within a WordPress theme**. However, WordPress does recognize the following folders by default:
 -->

現時点では、**WordPress テーマ内に必須のフォルダーは存在しません**。しかしながら、WordPress はデフォルトで以下のフォルダーを認識します:

<!-- 
### Page templates folder
 -->

### ページ・テンプレート・フォルダー

<!-- 
![basics-theme-files-organization-03](https://i0.wp.com/developer.wordpress.org/files/2014/08/basics-theme-files-organization-03.png?resize=400%2C124&ssl=1)
 -->

![basics-theme-files-organization-03](https://i0.wp.com/developer.wordpress.org/files/2014/08/basics-theme-files-organization-03.png?resize=400%2C124&ssl=1)

<!-- 
The [custom page templates](https://developer.wordpress.org/themes/basics/page-templates/ "Custom Page Templates"), named *page-templates* (since: 3.4.0) allows for better organization of template files. Custom page template files placed in this folder are automatically recognized by WordPress.
 -->

*ページ・テンプレート* (v3.4.0以降) と呼ばれる、[カスタム・ページ・テンプレート](https://developer.wordpress.org/themes/basics/page-templates/ "Custom Page Templates") により、テンプレート・ファイルの構成が改善されます。本フォルダーに配置されたカスタム・ページ・テンプレート・ファイルは、WordPress によって自動的に認識されます。

<!-- 
### Language folder
 -->

### Language フォルダー

<!-- 
![basics-theme-files-organization-04](https://i0.wp.com/developer.wordpress.org/files/2014/08/basics-theme-files-organization-04.png?resize=400%2C85&ssl=1)
 -->

![basics-theme-files-organization-04](https://i0.wp.com/developer.wordpress.org/files/2014/08/basics-theme-files-organization-04.png?resize=400%2C85&ssl=1)

<!-- 
If you wish to [internationalize your theme](https://developer.wordpress.org/themes/functionality/internationalization/ "Internationalization") so it’s usable in other languages, you can create a *languages* folder to contain translations.
 -->

[あなたのテーマを国際化](https://developer.wordpress.org/themes/functionality/internationalization/ "Internationalization") したい場合、つまり他の言語でも使用できるようにしたい場合は、*languages* フォルダーを作成し、そこに翻訳ファイルを格納できます。