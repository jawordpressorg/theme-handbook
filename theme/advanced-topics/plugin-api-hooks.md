<!-- 
# Plugin API Hooks
 -->

# プラグイン API フック

<!-- 
A theme should work well with WordPress plugins. Plugins add functionality by using actions and filters, which are collectively called hooks (see [Plugin API](https://codex.wordpress.org/Plugin_API "Plugin API") for more information).
 -->

テーマは、WordPress プラグインと良好に連携すべきです。プラグインは、フックと総称される、アクションとフィルターを使用して機能を追加します (詳細情報については [プラグイン API](https://codex.wordpress.org/Plugin_API "プラグイン API") をご覧あれ)。

<!-- 
Most hooks are executed internally by WordPress, so your theme does not need special tags for them to work. However, a few hooks need to be included in your theme templates. These hooks are fired by special Template Tags:
 -->

ほとんどのフックは WordPress 内部で実行されるため、あなたのテーマで特別なタグを用意する必要はありません。ただし、あなたのテーマ・テンプレートには、いくつかのフックを含める必要があります。これらのフックは、特別な「テンプレート・タグ」によって、発動されます:

<!-- 
**[wp\_head()](https://developer.wordpress.org/reference/functions/wp_head/ "Function Reference/wp head")**
 -->

**[`wp_head()`](https://developer.wordpress.org/reference/functions/wp_head/ "関数リファレンス/wp head")**

<!-- 
Goes at the end of the <head> element of a theme’s *header.php* template file.
 -->

テーマの *header.php* テンプレート・ファイルの `<head>` 要素の末尾に挿入されます。

<!-- 
**[wp\_body\_open()](https://developer.wordpress.org/reference/functions/wp_body_open/ "Function Reference/wp head")**
 -->

**[`wp_body_open()`](https://developer.wordpress.org/reference/functions/wp_body_open/ "関数リファレンス/wp head")**

<!-- 
Goes at the begining of the <body> element of a theme’s *header.php* template file.
 -->

テーマの *header.php* テンプレート・ファイルの `<body>` 要素の先頭に挿入されます。

<!-- 
**[wp\_footer()](https://developer.wordpress.org/reference/functions/wp_footer/ "Function Reference/wp footer")**
 -->

**[`wp_footer()`](https://developer.wordpress.org/reference/functions/wp_footer/ "関数リファレンス/wp footer")**

<!-- 
Goes in *footer.php*, just before the closing </body> tag.
 -->

*footer.php* の終了タグ `</body>` の直前に挿入されます。

<!-- 
**[wp\_meta()](https://developer.wordpress.org/reference/functions/wp_meta/ "Function Reference/wp meta")**
 -->

**[`wp_meta()`](https://developer.wordpress.org/reference/functions/wp_meta/ "関数リファレンス/wp meta")**

<!-- 
Typically goes in the <li>Meta</li> section of a Theme’s menu or sidebar.
 -->

通常、テーマのメニューまたはサイドバーの `<li>` Meta `</li>` セクションに挿入されます。

<!-- 
**[comment\_form()](https://developer.wordpress.org/reference/functions/comment_form/ "Function Reference/comment form")**
 -->

**[`comment_form()`](https://developer.wordpress.org/reference/functions/comment_form/ "関数リファレンス/comment form")**

<!-- 
Goes in *comments.php* directly before the file’s closing tag (</div>).
 -->

*comments.php* ファイルの終了タグ (`</div>`) の直前に挿入されます。

<!-- 
Take a look at a core theme’s templates for examples of how these hooks are used.
 -->

コア・テーマのテンプレートを参照し、これらのフックがどのように使用されているかの例を確認しましょう。