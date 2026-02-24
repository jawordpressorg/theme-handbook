<!-- 
# Galleries
 -->

# ギャラリー

<!-- 
## Galleries
 -->

## ギャラリー

<!-- 
[![](https://i0.wp.com/developer.wordpress.org/files/2014/10/Capture.png?resize=711%2C583&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2014/10/Capture.png?ssl=1)
 -->

[![](https://i0.wp.com/developer.wordpress.org/files/2014/10/Capture.png?resize=711%2C583&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2014/10/Capture.png?ssl=1)

<!-- 
Image galleries are the best way to showcase your pictures on your WordPress sites. WordPress bundles the **Create Gallery** feature by default in the media uploader which allows you to create a simple gallery.  
 -->

画像ギャラリーは、あなたの WordPress サイトであなたの画像を展示する、最良の方法です。WordPress はデフォルトで、シンプルなギャラリーを作成できる **ギャラリー作成** 機能をメディアアップローダーにバンドルしています。

<!-- 
Note: Before adding a gallery, you must have images in your media library. Otherwise, you need to upload the images into the library and can proceed on gallery creation.
 -->

注記: ギャラリーを追加する前に、あなたのメディアライブラリに画像が存在している必要があります。そうでない場合は、画像をライブラリにアップロードしてからギャラリー作成を進めてください。

<!-- 
### Gallery shortcode
 -->

### 「ギャラリー」ショートコード

<!-- 
The **Gallery** feature allows you to add one or more image galleries to your posts and pages using a simple Shortcode.
 -->

**ギャラリー** 機能は、シンプルな「ショートコード」を使用して、あなたの投稿やページに1つ以上の画像ギャラリーを追加できます。

<!-- 
The basic form of gallery shortcode is:
 -->

「ギャラリー」ショートコードの基本形式は、以下の通りです:

```php
[gallery]
```

<!-- 
If you use the \[gallery\] shortcode without using the `ids` argument in your post or page, only images that are “attached” to that post or page will be displayed.  
 -->

あなたの投稿やページで、`ids` 引数を使用せずに `[gallery]` ショートコードを使用する場合、その投稿やページに「添付」されている画像のみが表示されます。 

<!-- 
If you need to add multiple images with ID’s, use the following sample shortcode
 -->

ID 付きの画像を複数追加する必要がある場合は、下記のサンプルショートコードを使用しましょう。

```php
//Note: 10, 205, 552 and 607 are the IDs of respected image.
[gallery ids="10, 205, 552, 607"]
```

<!-- 
NOTE: find the proper IDs of the images for the gallery. Go to Media library and click on the respected image and ID will appear on the URL.  
 -->

注記: ギャラリー用の画像の適切な ID を確認してください。「メディアライブラリ」に移動し、該当する画像をクリックすると、URL 上に ID が表示されます。

<!-- 
To use the shortcode from the template file, use the [do\_shortcode()](https://developer.wordpress.org/reference/functions/do_shortcode/) function. Insert the following code into your template file:
 -->

テンプレートファイルからショートコードを使用するには、[`do_shortcode()`](https://developer.wordpress.org/reference/functions/do_shortcode/) 関数を使用しましょう。下記コードをあなたのテンプレートファイルに挿入しましょう:

```php
<?php echo do_shortcode( [gallery] ); ?>
```

<!-- 
If you need to use the shortcode with IDs, insert the following code in your template file:
 -->

ID 付きショートコードを使用する必要がある場合は、下記コードをあなたのテンプレートファイルに挿入しましょう:

```php
<?php echo do_shortcode( [gallery ids="10, 205, 552, 607"] ); ?>
```

<!-- 
### Usage
 -->

### 使用方法

<!-- 
There are may options that may be specified using the below syntax:
 -->

以下の構文を使用して指定できるオプションは、多数あります:

```php
[gallery option1="value1" option2="value2"]
```

<!-- 
If you want to print the gallery directly on the template file, use \`[do\_shortcode()](https://developer.wordpress.org/reference/functions/do_shortcode/) \` function like below:
 -->

テンプレートファイル上にギャラリーを直接出力したい場合は、以下のように [`do_shortcode()`](https://developer.wordpress.org/reference/functions/do_shortcode/) 関数を使用しましょう:

```php
<?php echo do_shortcode( '[gallery option1="value1"]' ); ?>
```

<!-- 
If you need to filter the shortcodes, the following example gives you some tips
 -->

ショートコードをフィルタリングする必要がある場合、下記の例が参考になります。

```php
// Note: 'the_content' filter is used to filter the content of the
// post after it is retrieved from the database and before it is 
// printed to the screen.
<?php
$gallery_shortcode = '[gallery id="' . intval( $post->post_parent ) . '"]';
print apply_filters( 'the_content', $gallery_shortcode );
?>
```

<!-- 
### Supported Options
 -->

### サポートされるオプション

<!-- 
Gallery Shortcodes supports the basic options which are listed below:
 -->

「ギャラリー」ショートコードは、以下の基本オプションをサポートしています:

<!-- 
#### Orderby
 -->

#### `orderby`

<!-- 
‘orderby’ specifies the order the thumbnails show up. The default order is ‘menu\_order’.
 -->

`orderby` は、サムネイルの表示順序を指定します。デフォルトの順序は `menu_order` です。

<!-- 
*   menu\_order: You can reorder the images in the Gallery tab of the Add Media popup
*   title: Order by the title of the image in the Media Library
*   post\_date: Sort by date/time
*   rand: Order randomly
*   ID: Specify the post ID
 -->

*   `menu_order` -「メディア追加」ポップアップの「ギャラリー」タブで、画像の順序を変更できます。
*   `title` -「メディアライブラリ」内の画像タイトル順に、並べ替えます。
*   `post_date` - 日付/時刻順に並べ替えます。
*   `rand` - ランダムな順番です。
*   `ID` - 投稿 ID を指定します。

<!-- 
#### Order
 -->

#### `order`

<!-- 
order specify the sort order used to display thumbnail; ASC or DESC. For Example, to sort by ID and DESC:
 -->

`order` は、サムネイル表示に使用する、並べ替え順序を指定します; `ASC` または `DESC` です。たとえば、`ID` で `DESC` 順に並べ替えるには、以下のようにします:

```php
[gallery order="DESC" orderby="ID"]
```

<!-- 
If you need to print it on template file, use the [do\_shortcode()](https://developer.wordpress.org/reference/functions/do_shortcode/) function;
 -->

テンプレートファイルに出力する必要があれば、[`do_shortcode()`](https://developer.wordpress.org/reference/functions/do_shortcode/) 関数を使用しましょう;

```php
<?php echo do_shortcode( '[gallery]' ); ?>
```

<!-- 
#### columns
 -->

#### `columns`

<!-- 
The Columns options specify the number of columns in the gallery. The default value is 3.  
If you want to increase the number of column in the galley, use the following shortcode.
 -->

`columns` オプションは、ギャラリーのカラム数を指定します。デフォルト値は `3` です。ギャラリーのカラム数を増やしたい場合は、下記ショートコードを使用しましょう。

```php
[gallery columns="4"]
```

<!-- 
If you need to print it on your template file, use the [do\_shortcode()](https://developer.wordpress.org/reference/functions/do_shortcode/) function;
 -->

あなたのテンプレートファイルに出力する必要がある場合は、[`do_shortcode()`](https://developer.wordpress.org/reference/functions/do_shortcode/) 関数を使用しましょう;

```php
<?php echo do_shortcode(' [gallery columns="4"] '); ?>
```

<!-- 
#### IDs
 -->

#### `id`

<!-- 
The IDs option on the gallery shortcode loads images with specific post IDs.
 -->

ギャラリーショートコード上の `id` オプションは、特定の投稿 ID を持つ画像をロードします。

<!-- 
If you want to display the attached image with the specific post ID, follow the following code example.
 -->

特定の投稿 ID を持つ添付画像を表示したい場合は、下記コード例に倣いましょう。

```php
// Note: remove each space between brackets and 'gallery' and brackets and `123"`.
//Here "123" stands for the post IDs. If you want to display more than
//one ID, separate the IDs by a comma `,`.
[ gallery id="123" ]
```

<!-- 
Use ‘do\_shortcode’ function to print the gallery with IDs on template files like below:
 -->

テンプレートファイル上で ID 付きギャラリーを出力するには、以下のように `do_shortcode` 関数を使用しましょう:

```php
// Note: remove each space between brackets and 'gallery' and brackets and `123"`.
<?php echo do_shortcode(' [ gallery id="123" ] '); ?>
```

<!-- 
#### Size
 -->

#### `size`

<!-- 
Size determines the image size to use for the thumbnail display. Valid values include “thumbnail”, “medium”, “large”, “full” and any other additional image size that was registered with [add\_image\_size()](https://developer.wordpress.org/reference/functions/add_image_size/). The default value is “thumbnail”. The size of the images for “thumbnail”, “medium” and “large” can be configured in WordPress admin panel under Settings > Media.
 -->

`size` は、サムネイル表示に使用する、画像サイズを決定します。有効な値には `thumbnail`、`medium`、`large`、`full`、および [`add_image_size()`](https://developer.wordpress.org/reference/functions/add_image_size/) で登録された、任意のその他の追加画像サイズが含まれます。デフォルト値は `thumbnail` です。`thumbnail`、`medium`、`large` 用の画像サイズについては、WordPress 管理パネルの **設定 > メディア** で設定できます。

<!-- 
For example, to display a gallery of medium sized images:
 -->

たとえば、`medium` サイズの画像ギャラリーを表示するには、以下のようにします:

```php
[gallery size="medium"]
```

<!-- 
Some advanced options are also available on Gallery shortcodes.
 -->

「ギャラリー」ショートコードには、いくつかの高度なオプションも利用可能です。

<!-- 
#### itemtag
 -->

#### `itemtag`

<!-- 
The name of the HTML tag used to enclose each item in the gallery. The default is “dl”.
 -->

ギャラリー内の各項目を囲むために使用される、HTML タグの名称です。デフォルトは、`dl` です。

<!-- 
#### icontag
 -->

#### `icontag`

<!-- 
The name of the HTMLtag used to enclose each thumbnail icon in the gallery. The default is “dt”.
 -->

ギャラリー内の各サムネイルアイコンを囲むために使用される、HTML タグの名称です。デフォルトは `dt` です。

<!-- 
#### captiontag
 -->

#### `captiontag`

<!-- 
The name of the HTML tag used to enclose each caption. The default is “dd”.
 -->

各キャプションを囲むために使用される、HTML タグの名称です。デフォルトは `dd` です。

<!-- 
You are allowed to change the defaults.
 -->

デフォルトの変更は、可能です。

```php
[gallery itemtag="div" icontag="span" captiontag="p"]
```

<!-- 
#### Link
 -->

#### `link`

<!-- 
Specify where you want the image to link. The default value links to the attachment’s [permalink](https://codex.wordpress.org/Using_Permalinks). Options:
 -->

リンクしたい画像を指定してください。デフォルト値は、添付ファイルの [パーマリンク](https://codex.wordpress.org/Using_Permalinks) にリンクします。選択肢は、以下になります:

<!-- 
*   file – Link directly to image file
*   none – No link
 -->

*   `file` – 画像ファイルへの、直接リンクです。
*   `none` – リンクは、ありません。

<!-- 
Example:
 -->

例:

```php
[gallery link="file"]
```

<!-- 
#### Include
 -->

#### `include`

<!-- 
Include allows you to insert an “array” of comma separated attachment IDs to show only the images from these attachments.
 -->

`include` を使用すると、カンマ区切りの添付ファイル ID の「配列」を挿入することで、これら添付ファイルの画像のみを表示できます。

```php
[gallery include="23,39,45"]
```

<!-- 
#### Exclude
 -->

#### `exclude`

<!-- 
Exclude callows you to insert an “array” of comma separated attachment IDs to not show the images from these attachments. Please note that include and exclude cannot be used together.
 -->

`exclude` を使用すると、カンマ区切りの添付ファイル ID の「配列」を挿入することで、これら添付ファイルの画像を表示しないようにできます。`include` と `exclude` は、同時に使用できないことに注意しましょう。

```markup
[gallery exclude="21,32,43"]
```

<!-- 
### References
 -->

### リファレンス

<!-- 
For more technical details take a reference from below links
 -->

技術的な詳細情報については、以下のリファレンスをご覧ください:

<!-- 
*   [Gallery Shortcode](https://codex.wordpress.org/Gallery_Shortcode)
*   [Function do\_shortcode()](https://developer.wordpress.org/reference/functions/do_shortcode/)
 -->

*   [「ギャラリー」ショートコード](https://codex.wordpress.org/Gallery_Shortcode)
*   [関数 `do_shortcode()`](https://developer.wordpress.org/reference/functions/do_shortcode/)