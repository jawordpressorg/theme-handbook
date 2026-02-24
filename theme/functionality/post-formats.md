<!-- 
# Post Formats
 -->

# 投稿フォーマット

<!-- 
A Post Format is used by a theme for presenting posts in a certain format and style. The Post Formats feature provides a standardized list of formats available to all themes that support the feature. A theme may not support every format on the list; in such a case, it is good form to make this known to users.
 -->

投稿フォーマットは、テーマが特定のフォーマットやスタイルで投稿を表示するために使用されます。投稿フォーマット機能は、この機能をサポートするすべてのテーマで利用可能なフォーマットの、標準化されたリストを提供します。テーマは、リスト上のすべてのフォーマットを、必ずしもサポートするとは限りません; そのような場合、ユーザーにその旨を知らせるのが望ましい対応です。

<!-- 
A theme cannot introduce formats not on the standardized list, even through plugins. This standardization ensures compatibility between themes and a way for external tools to use the feature in a consistent fashion.
 -->

テーマは、標準化されたリストにないフォーマットを、プラグインを通じてであっても導入できません。この標準化により、テーマ間の互換性が確保され、外部ツールが機能を一貫した方法で利用できます。

<!-- 
In short, with a theme that supports Post Formats, a blogger can change how a post looks by choosing a Post Format.
 -->

要するに、「投稿フォーマット」をサポートするテーマを使用すれば、ブロガーは「投稿フォーマット」を選択することで、投稿の見た目を変更できます。

<!-- 
Using **Asides** as an example, in the past, a category called Asides was created, and posts were assigned that category, and then displayed differently based on styling rules from [post\_class()](https://developer.wordpress.org/reference/functions/post_class/) or from [in\_category(‘asides’)](https://developer.wordpress.org/reference/functions/in_category/).
 -->

**「Asides」** を例に挙げると、以前は、「Asides」というカテゴリーが作成され、投稿にそのカテゴリーが割り当てられ、その後、[`post_class()`](https://developer.wordpress.org/reference/functions/post_class/) や [`in_category('asides')`](https://developer.wordpress.org/reference/functions/in_category/) に由来するスタイリングルールにもとづいて、さまざまな表示がなされます。

<!-- 
With **Post Formats**, the new approach allows a theme to add support for a Post Format (e.g. [add\_theme\_support(‘post-formats’, array(‘aside’))](https://developer.wordpress.org/reference/functions/add_theme_support/)), and then the post format can be selected in the Publish meta box when saving the post. A function call of [get\_post\_format($post->ID)](https://developer.wordpress.org/reference/functions/get_post_format/) can be used to determine the format, and [post\_class()](https://developer.wordpress.org/reference/functions/post_class/) will also create the “format-asides” class, for pure-css styling.
 -->

**「投稿フォーマット」** では、新しいアプローチにより、テーマが「投稿フォーマット」(例: [`add_theme_support('post-formats', array('aside'))`](https://developer.wordpress.org/reference/functions/add_theme_support/)) のサポートを追加できるようになり、投稿を保存する際、投稿フォーマットは「公開」メタボックスで選択できます。[`get_post_format($post->ID)`](https://developer.wordpress.org/reference/functions/get_post_format/) の関数コールをフォーマット決定に利用でき、[`post_class()`](https://developer.wordpress.org/reference/functions/post_class/) は、純粋な CSS によるスタイリングのために `format-asides` クラスも作成します。

<!-- 
## Supported Formats
 -->

## 対応フォーマット

<!-- 
The following Post Formats are available, if supported by the theme.
 -->

テーマがサポートしている場合、以下の「投稿フォーマット」が利用可能です。

<!-- 
Note that while actual post content won’t change, the theme can display a post differently based on the format chosen. How posts are displayed is entirely up to the theme, but here are some general guidelines on typical uses for the different Post Formats.
 -->

実際の投稿内容は変更されませんが、テーマは、選択されたフォーマットにもとづいて、投稿を異なる方法で表示できることに注意してください。投稿の表示方法は完全にテーマ次第ですが、以下は、さまざまな「投稿フォーマット」の典型的な使用法に関する、一般的なガイドラインです。

<!-- 
*   **aside** – Typically styled without a title. Similar to a Facebook note update.
*   **gallery** – A gallery of images. Post will likely contain a gallery shortcode and will have image attachments.
*   **link** – A link to another site. Themes may wish to use the first <a href=””> tag in the post content as the external link for that post. An alternative approach could be if the post consists only of a URL, then that will be the URL and the title (post\_title) will be the name attached to the anchor for it.
*   **image** – A single image. The first <img /> tag in the post could be considered the image. Alternatively, if the post consists only of a URL, that will be the image URL and the title of the post (post\_title) will be the title attribute for the image.
*   **quote** – A quotation. Probably will contain a blockquote holding the quote content. Alternatively, the quote may be just the content, with the source/author being the title.
*   **status** – A short status update, similar to a Twitter status update.
*   **video** – A single video. The first <video /> tag or object/embed in the post content could be considered the video. Alternatively, if the post consists only of a URL, that will be the video URL. May also contain the video as an attachment to the post, if video support is enabled on the blog (like via a plugin).
*   **audio** – An audio file. Could be used for Podcasting.
*   **chat** – A chat transcript, like so:
 -->

*   **aside** – 通常、タイトルなしでスタイリングされます。Facebook のノート更新に類似しています。
*   **gallery** – 画像のギャラリーです。投稿にはギャラリーショートコードが含まれ、画像添付がある可能性があります。
*   **link** – 他のサイトへのリンクです。テーマでは、投稿コンテンツ内の最初の `<a href="">` タグを、その投稿の外部リンクとして使用する場合があります。別アプローチとして、投稿内容が URL のみで構成されている場合、その URL がリンク先となり、タイトル (`post_title`) がそのアンカーに紐づく名称になります。
*   **image** – 個別の画像です。投稿内の最初の `<img />` タグが画像と見なされます。あるいは、投稿内容が URL のみで構成されている場合、その URL が画像 URL となり、投稿タイトル (`post_title`) が画像の `title` 属性となります。
*   **quote** – 引用です。引用内容を保持するであろうブロッククオートが含まれます。あるいは、引用文自体が内容であり、`source`/`author` がタイトルとなる場合もあります。
*   **status** – 簡潔なステータス更新で、Twitter のステータス更新に類似しています。
*   **video** – 個別の動画です。投稿コンテンツ内の最初の `<video />` タグ、または `object`/`embed` が動画と見なされます。あるいは、投稿が URL のみで構成されている場合、その URL が動画 URL となります。ブログで動画サポートが有効化されている場合 (プラグイン経由など)、投稿への添付ファイルとして動画が含まれることもあります。
*   **audio** – 音声ファイルです。ポッドキャスティングに使用できます。
*   **chat** – 以下のような、チャットの文字起こしです:

```bash
John: foo
Mary: bar
John: foo 2
```

<!-- 
When writing or editing a Post, “Standard” designates that no Post Format is specified. Also if an invalid format is specified, “Standard” (no format) is applied by default.
 -->

「投稿」の作成または編集時に「標準」と表示される場合、「投稿フォーマット」が指定されていないことを示します。また、無効なフォーマットが指定された場合、デフォルトで「標準」(フォーマットなし) が適用されます。

<!-- 
## Function Reference
 -->

## 関数リファレンス

<!-- 
### Main Functions
 -->

### 主要関数

<!-- 
*   [set\_post\_format()](https://developer.wordpress.org/reference/functions/set_post_format/)
*   [get\_post\_format()](https://developer.wordpress.org/reference/functions/get_post_format/)
*   [has\_post\_format()](https://developer.wordpress.org/reference/functions/has_post_format/)
 -->

*   [`set_post_format()`](https://developer.wordpress.org/reference/functions/set_post_format/)
*   [`get_post_format()`](https://developer.wordpress.org/reference/functions/get_post_format/)
*   [`has_post_format()`](https://developer.wordpress.org/reference/functions/has_post_format/)

<!-- 
### Other Functions
 -->

### その他の関数

<!-- 
*   [get\_post\_format\_link()](https://developer.wordpress.org/reference/functions/get_post_format_link/)
*   [get\_post\_format\_string()](https://developer.wordpress.org/reference/functions/get_post_format_string/)
 -->

*   [`get_post_format_link()`](https://developer.wordpress.org/reference/functions/get_post_format_link/)
*   [`get_post_format_string()`](https://developer.wordpress.org/reference/functions/get_post_format_string/)

<!-- 
## Adding Theme Support
 -->

## テーマサポートの追加

<!-- 
Themes need to use [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) in the *functions.php* file to tell WordPress which post formats to support by passing an array of formats like so:
 -->

テーマは、*functions.php* ファイル内で [`add_theme_support()`](https://developer.wordpress.org/reference/functions/add_theme_support/) を使用し、以下のようにフォーマットの配列を渡すことで、WordPress にサポートする投稿フォーマットを通知する必要があります:

```php
<?php
function themename_post_formats_setup() {
	add_theme_support( 'post-formats', array( 'aside', 'gallery' ) );
}
add_action( 'after_setup_theme', 'themename_post_formats_setup' );
```

<!-- 
The [after\_setup\_theme](https://developer.wordpress.org/reference/hooks/after_setup_theme/) hook is used so that the post formats support is registered after the theme has loaded.
 -->

[`after_setup_theme`](https://developer.wordpress.org/reference/hooks/after_setup_theme/) フックを使用することで、投稿フォーマットサポートがテーマロード後に登録されるようにしています。

<!-- 
## Adding Post Type Support
 -->

## 投稿タイプサポートの追加

<!-- 
Post Types need to use [add\_post\_type\_support()](https://developer.wordpress.org/reference/functions/add_post_type_support/) in the *functions.php* file to tell WordPress which post formats to support:
 -->

投稿タイプは、WordPress にサポートする投稿フォーマットを通知するために、*functions.php* ファイル内で [`add_post_type_support()`](https://developer.wordpress.org/reference/functions/add_post_type_support/) を使用する必要があります:

```php
<?php
function themename_custom_post_formats_setup() {
	// add post-formats to post_type 'page'
	add_post_type_support( 'page', 'post-formats' );
	// add post-formats to post_type 'my_custom_post_type'
	add_post_type_support( 'my_custom_post_type', 'post-formats' );
}
add_action( 'init', 'themename_custom_post_formats_setup' );
```

<!-- 
Or in the function [register\_post\_type()](https://developer.wordpress.org/reference/functions/register_post_type/), add ‘post-formats’, in ‘supports’ parameter array:
 -->

あるいは関数 [`register_post_type()`](https://developer.wordpress.org/reference/functions/register_post_type/) 内で、`supports` パラメータ配列に `post-formats` を追加します:

```php
<?php
$args = array(
	'supports' => array( 'title', 'editor', 'author', 'post-formats' ),
);
register_post_type( 'book', $args );
```

<!-- 
[add\_post\_type\_support](https://developer.wordpress.org/reference/functions/add_post_type_support/) should be hooked to [init](https://developer.wordpress.org/reference/hooks/init/) hook, as custom post types may not have been registered at [after\_setup\_theme](https://developer.wordpress.org/reference/hooks/after_setup_theme/).
 -->

カスタム投稿タイプは [`after_setup_theme`](https://developer.wordpress.org/reference/hooks/after_setup_theme/) 時点では登録されていない可能性があるため、[`add_post_type_support`](https://developer.wordpress.org/reference/functions/add_post_type_support/) は [`init`](https://developer.wordpress.org/reference/hooks/init/) フックに接続する必要があります。

<!-- 
## Using Formats
 -->

## フォーマットの使用

<!-- 
In the theme, use [get\_post\_format()](https://developer.wordpress.org/reference/functions/get_post_format/) to check the format for a post, and change its presentation accordingly. Note that posts with the default format will return a value of FALSE. Alternatively, use the [has\_post\_format()](https://developer.wordpress.org/reference/functions/has_post_format/) [conditional tag](https://developer.wordpress.org/themes/basics/conditional-tags/):
 -->

テーマでは、[`get_post_format()`](https://developer.wordpress.org/reference/functions/get_post_format/) を使用して投稿のフォーマットを確認し、それに応じて視覚表現を変更します。デフォルトのフォーマットを持つ投稿は、`FALSE` を返すことに注意してください。あるいは、[条件タグ](https://developer.wordpress.org/themes/basics/conditional-tags/) である [`has_post_format()`](https://developer.wordpress.org/reference/functions/has_post_format/) も使用できます:

```php
<?php
if ( has_post_format( 'video' ) ) {
	echo 'This is the video format.';
}
```

<!-- 
### Suggested Styling
 -->

### おすすめスタイリング

<!-- 
An alternate approach to formats is through styling rules. Themes should use the [post\_class()](https://developer.wordpress.org/reference/functions/post_class/) function in the wrapper code that surrounds the post to add dynamic styling classes. Post formats will cause extra classes to be added in this manner, using the “format-foo” name.
 -->

フォーマットに代わるアプローチとして、スタイリングルールがあります。テーマでは、投稿を囲むラッパーコード内で [`post_class()`](https://developer.wordpress.org/reference/functions/post_class/) 関数を使用し、動的なスタイリングクラスを追加する必要があります。投稿フォーマットは、この方法で「format-foo」という名称の追加クラスを生成します。

<!-- 
For example, one could hide post titles from status format posts by putting this in your theme’s stylesheet:
 -->

たとえば、テーマのスタイルシートに以下を記述することで、`status` フォーマット投稿に於ける投稿タイトルを非表示にできます:

```css
.format-status .post-title {
     display: none;
}
```

<!-- 
Each of the formats lend themselves to a certain type of “style”, as dictated by modern usage. It is well to keep in mind the intended usage for each format when applying styles.
 -->

各フォーマットは、現代の使用法によって規定される、ある種の「スタイル」に適しています。スタイルを適用する際には、各フォーマットの意図された用途を念頭に置くとよいでしょう。

<!-- 
For example, the aside, link, and status formats are simple, short, and minor. These will typically be displayed without title or author information. The aside could contain perhaps a paragraph or two, while the link would be only a sentence with a link to a URL in it. Both the link and aside might have a link to the single post page (using [the\_permalink()](https://developer.wordpress.org/reference/functions/the_permalink/)) and would thus allow comments, but the status format very likely would not have such a link.
 -->

たとえば、`aside`、`link`、`status` フォーマットはシンプルで短く、付随的なものです。これらは通常、`title` や `author` 情報なしで表示されます。`aside` には1～2段落が含まれる可能性がありますが、`link` は URL へのリンクを含む一文のみとなります。`link` と `aside` の両方には個別投稿ページへのリンク ([`the_permalink()`](https://developer.wordpress.org/reference/functions/the_permalink/) を使用) が含まれる可能性があり、コメントが許可されますが、`status` フォーマットにはそのようなリンクが含まれない可能性が高くなります。

<!-- 
An image post, on the other hand, would typically just contain a single image, with or without a caption/text to go along with it. An audio/video post would be the same but with audio/video added in. Any of these three could use either plugins or standard [Embeds](https://codex.wordpress.org/Embeds) to display their content. Titles and authorship might not be displayed for them either, as the content could be self-explanatory.
 -->

一方、画像投稿は通常、キャプションやテキストの有無にかかわらず、個別画像のみを含みます。音声/動画投稿は同様ですが、音声/動画が追加されます。これら3つのいずれにおいても、コンテンツの表示にはプラグインまたは標準の [埋め込み](https://codex.wordpress.org/Embeds) が使用可能です。また、コンテンツ自体が説明を必要としない場合、タイトルや著者情報が表示されないこともあります。

<!-- 
The quote format is especially well suited to posting a simple quote from a person with no extra information. If you were to put the quote into the post content alone, and put the quoted person’s name into the title of the post, then you could style the post so as to display [the\_content()](https://developer.wordpress.org/reference/functions/the_content/) by itself but restyled into a blockquote format, and use [the\_title()](https://developer.wordpress.org/reference/functions/the_title/) to display the quoted person’s name as the byline.
 -->

`quote` フォーマットは、追加情報なしで人物の単純な引用を投稿するのに、特に適しています。引用文だけを投稿本文に配置し、引用元の人物の名前を投稿タイトルに配置する場合、投稿をスタイリングして [`the_content()`](https://developer.wordpress.org/reference/functions/the_content/) をそれ自体で表示しつつ、`blockquote` フォーマットにスタイリングし直すこともでき、[`the_title()`](https://developer.wordpress.org/reference/functions/the_title/) を使用して引用された人物の名前を著者情報として表示できるようにします。

<!-- 
A chat in particular will probably tend towards a monospaced type display, in many cases. With some styling on the .format-chat, you can make it display the content of the post using a monospaced font, perhaps inside a gray background div or similar, thus distinguishing it visually as a chat session.
 -->

特にチャットは、多くの場合、等幅フォントでの表示になる傾向があります。`.format-chat` に若干のスタイリングを施すことで、投稿のコンテンツを等幅フォントで表示させることができ、たとえば、灰色の背景の `div` 要素などの内部に配置することで、視覚的にチャットセッションとして区別できます。

<!-- 
### Formats in a Child Theme
 -->

### 子テーマでのフォーマット

<!-- 
[Child Themes](https://developer.wordpress.org/themes/advanced-topics/child-themes/) inherit the post formats defined by the parent theme. Calling [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) for post formats in a child theme must be done at a later priority than that of the parent theme and will **override** the existing list, not add to it.
 -->

[子テーマ](https://developer.wordpress.org/themes/advanced-topics/child-themes/) は、親テーマで定義された投稿フォーマットを継承します。子テーマ内で投稿フォーマットに対して [`add_theme_support()`](https://developer.wordpress.org/reference/functions/add_theme_support/) をコールする場合、親テーマよりも低い優先度で行う必要があり、既存のリストに追加するのではなく **オーバーライド** します。

```php
<?php
add_action( 'after_setup_theme', 'childtheme_formats', 11 );
function childtheme_formats() {
	 add_theme_support( 'post-formats', array( 'aside', 'gallery', 'link' ) );
}
```

<!-- 
Calling [remove\_theme\_support(‘post-formats’)](https://developer.wordpress.org/reference/functions/remove_theme_support/) will remove it all together.
 -->

[`remove_theme_support('post-formats')`](https://developer.wordpress.org/reference/functions/remove_theme_support/) をコールすると、完全に削除されます。