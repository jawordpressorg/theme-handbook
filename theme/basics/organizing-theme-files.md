<!-- 
# Organizing Theme Files
 -->

# テーマ・ファイルの編成

<!-- 
While WordPress themes technically only require two files (`index.php` in classic themes and `index.html` in block themes, and `style.css`), they usually are made up of many files. That means they can quickly become disorganized! This section will show you how to keep your files organized.
 -->

WordPress テーマは、技術的には2つのファイル (クラシック・テーマでは `index.php`、ブロック・テーマでは `index.html`、および `style.css`) のみで構成されますが、実際には多くのファイルで構成されることが一般的です。つまり、すぐに無秩序になってしまいがちです ! 本セクションでは、ファイルを系統だてた状態に保つ方法を紹介します。

<!-- 
## Theme folder and file structure
 -->

## テーマ・フォルダーとファイル構造

<!-- 
As mentioned previously, the default Twenty themes are some of the best examples of good theme development. For instance, here is how the [Twenty Seventeen Theme](https://wordpress.org/themes/twentyseventeen/) organizes its [file structure](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentyseventeen):
 -->

先述の通り、デフォルトの Twenty テーマは、優れたテーマ開発の好例です。たとえば、[Twenty Seventeen テーマ](https://wordpress.org/themes/twentyseventeen/) の [ファイル構造](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentyseventeen) は、以下のように構成されています:

```
.
├── assets (dir)/
│   ├── css (dir)
│   ├── images (dir)
│   └── js (dir)
├── inc (dir)
├── template-parts (dir)/
│   ├── footer (dir)
│   ├── header (dir)
│   ├── navigation (dir)
│   ├── page (dir)
│   └── post (dir)
├── 404.php
├── archive.php
├── comments.php
├── footer.php
├── front-page.php
├── functions.php
├── header.php
├── index.php
├── page.php
├── README.txt
├── rtl.css
├── screenshot.png
├── search.php
├── searchform.php
├── sidebar.php
├── single.php
└── style.css
```

<!-- 
You can see that the main theme template files are in the root directory, while JavaScript, CSS, images are placed in assets directory, template-parts are placed in under respective subdirectory of template-parts and collection of  functions related to core functionalities are placed in inc directory.
 -->

メインテーマのテンプレート・ファイルは、ルート・ディレクトリに配置されています。一方、JavaScript、CSS、画像は、assets ディレクトリに、テンプレート・パーツは、template-parts ディレクトリ内の各サブディレクトリに、コア機能に関連する関数のコレクションは、inc ディレクトリに配置されています。

<!-- 
There are no required folders in classic themes. In block themes, templates must be placed inside a folder called **templates**, and all template parts must be placed inside a folder called **parts**.
 -->

クラシック・テーマには、必須のフォルダーはありません。ブロック・テーマでは、テンプレートは **templates** というフォルダー内に配置する必要があり、すべてのテンプレート・パーツは **parts** というフォルダー内に配置する必要があります。

<!-- 
`style.css` should reside in the root directory of your theme not within the CSS directory.
 -->

`style.css` は、CSS ディレクトリ内ではなく、あなたのテーマのルートディレクトリに配置する必要があります。

<!-- 
### Languages folder
 -->

### Languages フォルダー

<!-- 
It’s best practice to [internationalize your theme](https://developer.wordpress.org/themes/functionality/internationalization/ "Internationalization") so it can be translated into other languages. Default themes include the `languages` folder, which contains a .pot file for translation and any translated .mo files. While `languages` is the default name of this folder, you can change the name. If you do so, you must update `[load_theme_textdomain()](https://developer.wordpress.org/reference/functions/load_theme_textdomain/)`.
 -->

他の言語に翻訳できるように [あなたのテーマの国際化](https://developer.wordpress.org/themes/functionality/internationalization/ "Internationalization") を行うことが、ベスト・プラクティスです。デフォルト・テーマには `languages` フォルダーが含まれており、翻訳用の .pot ファイルと翻訳済み .mo ファイルが格納されています。`languages` は、このフォルダーのデフォルト名ですが、名称変更は可能です。変更する場合は、`[load_theme_textdomain()](https://developer.wordpress.org/reference/functions/load_theme_textdomain/)` を修正する必要があります。