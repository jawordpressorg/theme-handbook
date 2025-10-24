<!-- 
# Required Theme Files
 -->

# 必須テーマファイル

<!-- 
**Block theme:** See [Create a Block Theme](https://developer.wordpress.org/block-editor/how-to-guides/themes/create-block-theme/) for building a block theme  
 -->

**ブロック・テーマ:** ブロック・テーマの構築については、[ブロック・テーマの制作](https://developer.wordpress.org/block-editor/how-to-guides/themes/create-block-theme/) をご覧ください。

<!-- 
Classic themes must  include the required theme files. These files must follow template file standards set by the themes team. For Classic themes, additional standard template files are recommended to use. Learn more about the [Organizing Theme Files](https://developer.wordpress.org/themes/basics/organizing-theme-files/).
 -->

クラシック・テーマには、必須テーマファイルを含める必要があります。これらのファイルは、テーマチームが定めたテンプレートファイル標準に準拠しなければなりません。クラシック・テーマでは、追加の標準テンプレート・ファイルの使用が推奨されます。詳細は、[テーマファイルの構成](https://developer.wordpress.org/themes/basics/organizing-theme-files/) をご覧ください。

<!-- 
## Classic Themes Required Theme Files
 -->

## クラシック・テーマの必須テーマファイル

<!-- 
1.  **style.css  
    **Your theme’s main [stylesheet](https://developer.wordpress.org/themes/basics/including-css-javascript/) file. This file will also include information about your theme, such as author name, version number, and plugin URL, in it’s header.
2.  **index.php  
    **The main [template](https://developer.wordpress.org/themes/basics/template-files/) file for your theme. This will be the template for the homepage on your site unless a static front page is specified. If you *only* include this template file, it must include all functionality of your theme. However, you can use as many relevant template files as you want in your theme.
3.  ****comments.php  
    ****The comment template which is included wherever comments are allowed. This file should provide support for threaded comments and trackbacks, and should style author comments differently then user comments. See the [Comments](https://developer.wordpress.org/themes/functionality/comments/) page for more information.
4.  **screenshot  
    **In the WordPress.org theme directory, the screenshot acts as a visual indicator of what your theme looks like. It is visible both in the web view and in the admin dashboard. The screenshot must not be bigger than 1200 x 900px. 
 -->

1.  **style.css**

    あなたのテーマのメイン [スタイルシート](https://developer.wordpress.org/themes/basics/including-css-javascript/) ファイルです。このファイルには、ヘッダー部分に、あなたのテーマに関する情報 (作者名、バージョン番号、プラグイン URL など) も含まれます。

2.  **index.php**

    あなたのテーマのメイン [テンプレート](https://developer.wordpress.org/themes/basics/template-files/) ファイルです。静的なフロントページが指定されていない限り、これがあなたのサイトのホームページのテンプレートとなります。このテンプレート・ファイルを *単独で* 使用する場合、あなたのテーマの全機能を含める必要があります。ただし、あなたのテーマでは、必要な数の関連テンプレート・ファイルをいくつでも使用できます。

3.  **comments.php**

    コメントが許可されている場所には必ず含まれる、コメント・テンプレートです。このファイルはスレッド化されたコメントとトラックバックの機能を実装し、投稿者コメントとユーザー・コメントを異なるスタイルで表示しなければなりません。詳細は [コメント](https://developer.wordpress.org/themes/functionality/comments/) ページをご覧ください。

4.  **screenshot**

    WordPress.org テーマ・ディレクトリでは、スクリーンショットは、あなたのテーマの外観を視覚的に示す役割を果たします。Web ビューと管理ダッシュボードの両方で表示されます。スクリーンショットのサイズは1200x900px を超えてはいけません。

<!-- 
While these files are the only files required by the theme review team for acceptance into the WordPress.org theme directory, you may use other template files. Of course, any file mentioned in the tutorial in this handbook may be used in your theme.
 -->

これらは、WordPress.org テーマ・ディレクトリへの承認のためにテーマ審査チームが要求するファイルだけですが、他のテンプレート・ファイルも使用できます。もちろん、本ハンドブックのチュートリアルで言及されているファイルは、あなたのテーマで使用できます。