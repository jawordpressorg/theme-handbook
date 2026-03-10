<!-- 
# Your First Theme
 -->

# あなたの最初のテーマ

<!-- 
## Block Theme
 -->

## ブロックテーマ

<!-- 
This section is for a [block theme](https://developer.wordpress.org/themes/block-themes/). 
 -->

本セクションは、[ブロックテーマ](https://developer.wordpress.org/themes/block-themes/) 用です。

<!-- 
### Required Files
 -->

### 必須ファイル

<!-- 
The *only* files needed for a block theme is,  
 -->

ブロックテーマで必要な *最低限の* ファイルは、

<!-- 
*   **index.html**, which is the main template to display your list of posts. Index.html needs to be placed inside a folder called templates.
*   **style.css** file to style content.  
*   **theme.json** file to set style properties in a structured way.
 -->

*   **index.html** - 投稿一覧を表示するメインテンプレートです。`index.html` は `templates` フォルダー内に配置する必要があります。
*   **style.css** - コンテンツをスタイリングするためのファイルです。
*   **theme.json** - 構造化された方法でスタイルプロパティを設定するためのファイルです。

<!-- 
[![Required Files Block Theme](https://i0.wp.com/developer.wordpress.org/files/2022/11/required-files-block-themes.png?resize=1024%2C158&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2022/11/required-files-block-themes.png?ssl=1)
 -->

[![ブロックテーマの必須ファイル](https://i0.wp.com/developer.wordpress.org/files/2022/11/required-files-block-themes.png?resize=1024%2C158&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2022/11/required-files-block-themes.png?ssl=1)

<!-- 
For advanced block theme development, you can add templates and template parts. For example, 
 -->

高度なブロックテーマ開発では、テンプレートとテンプレートパーツを追加できます。たとえば、

<!-- 
1.  You can create a templates directory inside the theme folder and put your templates there. Templates examples,
    *   index.html 
    *   archive.html
    *   single.html 
    *   page.html 
2.  You can create a parts directory inside the theme folder and put template parts. Template parts examples,
    *   header.html 
    *   footer.html
    *   sidebar.html 
 -->

1.  テーマフォルダー内に `templates` ディレクトリを作成し、あなたのテンプレートをそこに配置できます。テンプレート例は、
    *   `index.html`
    *   `archive.html`
    *   `single.html`
    *   `page.html`
2.  テーマフォルダー内に `parts` ディレクトリを作成し、テンプレートパーツを配置できます。テンプレートパーツ例は、
    *   `header.html`
    *   `footer.html`
    *   `sidebar.html`

<!-- 
[![](https://i0.wp.com/developer.wordpress.org/files/2022/11/my-first-fse-theme.png?resize=389%2C425&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2022/11/my-first-fse-theme.png?ssl=1)
 -->

[![](https://i0.wp.com/developer.wordpress.org/files/2022/11/my-first-fse-theme.png?resize=389%2C425&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2022/11/my-first-fse-theme.png?ssl=1)

<!-- 
As you know the required files for block themes, now let’s create your first block theme. 
 -->

ブロックテーマ用の必須ファイルについては、ご存じの通りですので、さっそくあなたの最初のブロックテーマを作成しましょう。

<!-- 
### Step 1 – Create a theme folder
 -->

### ステップ1 – テーマフォルダーの作成

<!-- 
First, create a new folder on your computer, and name it **my-first-theme**. This is where all of your theme’s files will go.
 -->

まず、自分のコンピューターに新しいフォルダーを作成し、**my-first-theme** と命名します。ここに、あなたのテーマのすべてのファイルが格納されます。

<!-- 
### Step 2 – Create a style.css file
 -->

### ステップ2 – `style.css` ファイルの作成

<!-- 
You can use any basic text editor on your computer to create a new file called **style.css**.
 -->

あなたのコンピューター上の任意のテキストエディターを使用して、**style.css** という名前の新規ファイルを作成します。

<!-- 
If you’re on a Windows-based machine use Notepad for now and if you’re using a Mac then use TextEdit.
 -->

Windows ベースのマシンを使用している場合は、当面は [Notepad](http://en.wikipedia.org/wiki/Notepad_\(software\)) を使用し、Mac を使用している場合は [TextEdit](http://en.wikipedia.org/wiki/TextEdit) を使用しましょう。

<!-- 
Copy and paste the following code into your newly created **style.css** file:
 -->

新しく作成した **style.css** ファイルに、下記コードをコピー & ペーストしましょう:

<!-- 
/\*  
Theme Name: My First WordPress Theme  
\*/
 -->

```css
/*  
Theme Name: My First WordPress Theme  
*/
```

<!-- 
### Step 3 – Create a theme.json file
 -->

### ステップ3 – `theme.json` ファイルの作成

<!-- 
Create the theme.json file in the root folder, and copy and paste the following code:
 -->

ルートフォルダーに `theme.json` ファイルを作成し、下記コードをコピー & ペーストしましょう:

<!-- 
{  
“version”: 2,  
“settings”: {  
“layout”: {  
“contentSize”: “840px”,  
“wideSize”: “1100px”  
}  
}  
}
 -->

```json
{  
    "version": 2,  
    "settings": {  
        "layout": {  
            "contentSize": "840px",  
            "wideSize": "1100px"  
        }  
    }  
}
```

<!-- 
### Step 4 – Add index.html inside the templates folder
 -->

### ステップ4 – テンプレートフォルダー内に `index.html` の追加

<!-- 
Inside your theme directory, create a templates folder. Inside the templates folder creates an **index.html** file. 
 -->

テーマディレクトリ内に `templates` フォルダーを作成しましょう。`templates` フォルダー内に **index.html** ファイルを作成しましょう。

<!-- 
Now, your theme structure should look like this,
 -->

さて、あなたのテーマ構造は、以下のような状態になっているはずです、

<!-- 
templates/

index.html

style.css

theme.json
 -->

```
templates/
index.html
style.css
theme.json
```

<!-- 
Your block theme is now ready. You can install and activate the theme. First, make the ZIP file of your theme directory. The ZIP file will be like, **my-first-theme.zip** 
 -->

あなたのブロックテーマの準備が整いました。テーマをインストールして有効化できます。まず、あなたのテーマディレクトリの zip ファイルを作成しましょう。zip ファイルは、**my-first-theme.zip** のようになります。

<!-- 
### Step 5 – Install and activate your theme
 -->

### ステップ5 – あなたのテーマのインストールと有効化

<!-- 
Now, go to your WordPress admin panel and **Appearance > Themes > Add New > Upload**. Upload the my-first-theme.zip and click on install and then activate.
 -->

では、あなたの WordPress 管理画面に移動し、**外観 > テーマ > 新規追加 > アップロード** を選択しましょう。`my-first-theme.zip` をアップロードし、インストールをクリックしてから有効化しましょう。

<!-- 
Congratulations – you’ve made your first WordPress block theme. 
 -->

おめでとうございます – あなたの最初の WordPress ブロックテーマが完成しました。

<!-- 
To know more about block themes, you can download the default Twenty Twenty-Three theme and use it as a reference. 
 -->

ブロックテーマについて詳しく知りたい場合は、デフォルトの `Twenty Twenty-Three` テーマをダウンロードし、リファレンスとして使用できます。

<!-- 
* * *
 -->

* * *

<!-- 
## Classic Theme
 -->

## クラシックテーマ

<!-- 
![getting-started-your-first-theme-01](https://i0.wp.com/developer.wordpress.org/files/2014/07/getting-started-your-first-theme-01.jpg?resize=1731%2C649&ssl=1)
 -->

![getting-started-your-first-theme-01](https://i0.wp.com/developer.wordpress.org/files/2014/07/getting-started-your-first-theme-01.jpg?resize=1731%2C649&ssl=1)

<!-- 
### Required Files
 -->

### 必須ファイル

<!-- 
As mentioned earlier in the “[What is a Theme](https://developer.wordpress.org/themes/getting-started/what-is-a-theme/)” section, the *only* files needed for a WordPress theme to work out of the box are an `index.php` file to display your list of posts and a `style.css` file to style the content.
 -->

「[テーマって ?](https://developer.wordpress.org/themes/getting-started/what-is-a-theme/)」セクションで前述したように、WordPress テーマがすぐに動作するために必要なファイルは、投稿一覧を表示する `index.php` ファイルと、コンテンツをスタイリングする `style.css` ファイル *のみ* です。

<!-- 
Once you get into more advanced development territory and your themes grow in size and complexity, you’ll find it easier to break your theme into many separate files (called [template files](https://developer.wordpress.org/themes/basics/template-files/ "Template Files")) instead. For example, most WordPress themes will also include:
 -->

より高度な開発領域に進み、あなたのテーマの規模と複雑さが増すにつれて、代わりにテーマを複数の ([テンプレートファイル](https://developer.wordpress.org/themes/basics/template-files/ "Template Files") と呼ばれる) 分離ファイルに分割するほうが容易であることに気付くでしょう。たとえば、ほとんどの WordPress テーマには、以下も含まれます:

<!-- 
*   `header.php`
*   `index.php`
*   `sidebar.php`
*   `footer.php`
 -->

*   `header.php`
*   `index.php`
*   `sidebar.php`
*   `footer.php`

<!-- 
We will cover creating separate files later in this handbook, but for now let’s get your first theme launched!
 -->

本ハンドブックの後半で、分離ファイルの作成について説明しますが、まずはあなたの最初のテーマをローンチしましょう !

<!-- 
(Note: The following steps assume you have already completed the “[Setting up a Development Environment](https://developer.wordpress.org/themes/getting-started/setting-up-a-development-environment/ "Setting up a Development Environment")” section.)
 -->

(注記: 下記手順は、「[開発環境のセットアップ](https://developer.wordpress.org/themes/getting-started/setting-up-a-development-environment/ "Setting up a Development Environment")」セクションをすでに完了していることを前提としています)

<!-- 
### Step 1 – Create a theme folder
 -->

### ステップ1 – テーマフォルダーの作成

<!-- 
First, create a new folder on your computer, and name it *my-first-theme*. This is where all of your theme’s files will go.
 -->

まず、自分のコンピューターに新しいフォルダーを作成し、**my-first-theme** と命名します。ここに、あなたのテーマのすべてのファイルが格納されます。

<!-- 
### Step 2 – Create a style.css file
 -->

### ステップ2 – `style.css` ファイルの作成

<!-- 
You can use any basic text editor on your computer to create a new file called style.css.
 -->

あなたのコンピューター上の任意の基本テキストエディターを使用して、**style.css** という名前の新規ファイルを作成できます。

<!-- 
If you’re on a Windows-based machine use [Notepad](http://en.wikipedia.org/wiki/Notepad_\(software\)) for now and if you’re using a Mac then use [TextEdit](http://en.wikipedia.org/wiki/TextEdit).
 -->

Windows ベースのマシンを使用している場合は、当面は [Notepad](http://en.wikipedia.org/wiki/Notepad_\(software\)) を使用し、Mac を使用している場合は [TextEdit](http://en.wikipedia.org/wiki/TextEdit) を使用しましょう。

<!-- 
Copy and paste the following code into your newly created `style.css` file:
 -->

新しく作成した **style.css** ファイルに、下記コードをコピー & ペーストしましょう:

```css
/*
Theme Name: My First WordPress Theme
*/

body {
    background: #21759b;
}
```

<!-- 
[Reference Gist](https://gist.github.com/philiparthurmoore/0496a9b659c12280666d)
 -->

[リファレンス Gist](https://gist.github.com/philiparthurmoore/0496a9b659c12280666d)

<!-- 
### Step 3 – Create an index.php file
 -->

### ステップ3 – `index.php` ファイルの作成

<!-- 
Now create a file named `index.php` and put it into your theme’s folder, adding the following code to it:
 -->

では、`index.php` と名付けたファイルを作成し、あなたのテーマフォルダーに配置し、それに下記コードを追加しましょう:

```php
<!DOCTYPE html>
<html>
<head>
<meta charset="<?php bloginfo( 'charset' ); ?>">
<title><?php wp_title( '|', true, 'right' ); ?></title>
<link rel="stylesheet" href="<?php echo esc_url( get_stylesheet_uri() ); ?>" type="text/css" />
<?php wp_head(); ?>
</head>
<body>
<h1><?php bloginfo( 'name' ); ?></h1>
<h2><?php bloginfo( 'description' ); ?></h2>

<?php if ( have_posts() ) : while ( have_posts() ) : the_post(); ?>

<h3><?php the_title(); ?></h3>

<?php the_content(); ?>
<?php wp_link_pages(); ?>
<?php edit_post_link(); ?>

<?php endwhile; ?>

<?php
if ( get_next_posts_link() ) {
next_posts_link();
}
?>
<?php
if ( get_previous_posts_link() ) {
previous_posts_link();
}
?>

<?php else: ?>

<p>No posts found. :(</p>

<?php endif; ?>
<?php wp_footer(); ?>
</body>
</html>
```

<!-- 
[Reference Gist](https://gist.github.com/philiparthurmoore/b1f47c15d3eb2c573924)
 -->

[リファレンス Gist](https://gist.github.com/philiparthurmoore/b1f47c15d3eb2c573924)

<!-- 
### Step 4 – Install Your Theme
 -->

### ステップ4 – あなたのテーマのインストール

<!-- 
Copy your new theme into the `wp-content/themes` folder on your development environment and activate it for review and testing.
 -->

あなたの新規テーマを、あなたの開発環境の `wp-content/themes` フォルダーにコピーし、レビューとテストのために有効化しましょう。

<!-- 
### Step 5 – Activate Your Theme
 -->

### ステップ5 – あなたのテーマの有効化

<!-- 
Now that you’ve installed your theme, go to **Admin > Appearance > Themes** to activate it.
 -->

さて、テーマをインストールしたら、**管理画面 > 外観 > テーマ** に移動して、有効化しましょう。

<!-- 
![getting-started-your-first-theme-02](https://i0.wp.com/developer.wordpress.org/files/2014/07/getting-started-your-first-theme-02.png?resize=1024%2C616&ssl=1)
 -->

![getting-started-your-first-theme-02](https://i0.wp.com/developer.wordpress.org/files/2014/07/getting-started-your-first-theme-02.png?resize=1024%2C616&ssl=1)

<!-- 
### Using Your First Theme
 -->

### あなたの最初テーマの使い方

<!-- 
**Congratulations – you’ve just made your first WordPress theme!**
 -->

**おめでとうございます – あなたの最初の WordPress テーマが完成しました !**

<!-- 
If you activate your new theme and view it within a browser, you should see something like this:
 -->

あなたの新規テーマを有効化し、ブラウザー内で表示すると、以下のような画面が表示されるはずです:

<!-- 
![Here's how Your First Theme looks on the front end.](https://i0.wp.com/developer.wordpress.org/files/2014/07/getting-started-your-first-theme-03.png?resize=908%2C321&ssl=1)
 -->

![フロントエンドでの「Your First Theme」の見た目。](https://i0.wp.com/developer.wordpress.org/files/2014/07/getting-started-your-first-theme-03.png?resize=908%2C321&ssl=1)

<!-- 
Here’s how Your First Theme looks on the front end.
 -->

フロントエンドでの「Your First Theme」の見た目。

<!-- 
Okay, so it’s not the *prettiest* theme yet, but it’s a terrific start!
 -->

たしかに、*最も素敵な* テーマとはまだ言えないけれど、すばらしいスタートです !

<!-- 
## What have we learned?
 -->

## 私たちは何を学んだの ?

<!-- 
Although your first theme may be missing the functionality and design elements that are found in other themes, the basic building blocks of a WordPress theme, as we have just created above, are all the same.
 -->

あなたの最初のテーマには、他のテーマに見られる機能やデザイン要素が不足しているかもしれませんが、先ほど作成したように、WordPress テーマの基本的な構築ブロックは、すべて同じです。

<!-- 
Remember that the key here is *not* to get caught up in how all those other things are done *now*, but to understand the guiding principles behind making WordPress themes that will stand the test of time, no matter how the code changes or the template file structure changes over time.
 -->

ここで重要なのは、他のテーマが *現在* どのように作られているかにとらわれることでは *なく*、コードがどのように変化しようとも、テンプレートファイルの構造が時とともに変わろうとも、時代を超えて通用する WordPress テーマ制作の指針となる原則を、理解することであることを覚えておいてください。

<!-- 
All websites, regardless of how they are created underneath the hood, need common elements: headers, primary content areas, menus, sidebars, footers, and the like. You’ll find that making WordPress themes is really just another way of crafting a website.
 -->

すべての Web サイトは、内部のしくみに関係なく、共通の要素を必要とします: ヘッダー、メインコンテンツエリア、メニュー、サイドバー、フッターなどです。WordPress テーマの作成は、Web サイトを構築するもう一つの方法に過ぎないことに気付くでしょう。

<!-- 
From this most basic theme, you’ll start learning about the building blocks that you put together to create a more complex theme.
 -->

この最も基本的なテーマから、より複雑なテーマを作成するために、組み合わせる構築ブロックについて学習を始めます。

<!-- 
## Up Next
 -->

## 次に

<!-- 
In [Chapter 2: Theme Basics](https://developer.wordpress.org/themes/basics/ "Chapter 2: Theme Basics"), we’ll dive further into themes and discuss the templates and other files that make up most themes, along with the PHP used to make dynamic themes, including:
 -->

[第2章: テーマの基本](https://developer.wordpress.org/themes/basics/ "Chapter 2: Theme Basics") では、テーマについてさらに掘り下げ、ほとんどのテーマを構成するテンプレートやその他のファイル、動的テーマ作成に使用される PHP について検討します。具体的には以下の内容を含みます:

<!-- 
*   Template Tags
*   The Loop
*   Theme Functions
*   Conditional Tags
*   and more
 -->

*   テンプレートタグ
*   ループ
*   テーマ関数
*   条件付きタグ
*   その他