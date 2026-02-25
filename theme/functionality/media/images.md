<!-- 
# Images
 -->

# 画像

<!-- 
## Images
 -->

## 画像

<!-- 
This section describes the handling of images in the Media Library. If you want to display the image file located within your theme directory, just specify the location with the img tag, and style it with CSS.
 -->

本セクションでは、「メディアライブラリ」における画像の取り扱いについて説明します。あなたのテーマディレクトリ内に配置された画像ファイルを表示したい場合は、`img` タグでその場所を指定し、CSS でスタイリングするだけです。

<!-- 
<img alt="" src="" />
 -->

```
<img alt="" src="" />
```

<!-- 
### Getting img code
 -->

### `img` コードの取得

<!-- 
To display the image in the Media Library, use `[wp_get_attachment_image()](https://developer.wordpress.org/reference/functions/wp_get_attachment_image/)` function.
 -->

「メディアライブラリ」内の画像を表示するには、[`wp_get_attachment_image()`](https://developer.wordpress.org/reference/functions/wp_get_attachment_image/) 関数を使用しましょう。

```php
echo wp_get_attachment_image( $attachment->ID, 'thumbnail' );
```

<!-- 
You will get the following HTML output with the selected thumbnail size
 -->

選択したサムネイルサイズで、下記の HTML 出力が得られます。

```markup
<img width="150" height="150" src="http://example.com/wordpress/wp-content/uploads/2016/11/sample-150x150.jpg" class="attachment-thumbnail size-thumbnail" ... />
```

<!-- 
You can specify other size such as ‘full’ for original image or ‘medium’ and ‘large’ for the sizes set at **Settings > Media** in the [Administration Screen](https://codex.wordpress.org/Administration_Screens), or any pair of width and height as array. You’re also free to set custom size strings with [add\_image\_size()](https://developer.wordpress.org/reference/functions/add_image_size/) ;
 -->

元画像の場合は `full`、[管理画面](https://codex.wordpress.org/Administration_Screens) 内の **設定 > メディア** で設定されたサイズの場合は `medium` や `large` といった、他のサイズを指定したり、幅と高さの任意のペアを配列として指定できます。[`add_image_size()`](https://developer.wordpress.org/reference/functions/add_image_size/) を使用してカスタムサイズ文字列も自由にセットできます;

```php
echo wp_get_attachment_image( $attachment->ID, array(640, 480) );
```

<!-- 
### Getting URL of image
 -->

### 画像の URL の取得

<!-- 
If you want to get the URL of the image, use `[wp_get_attachment_image_src()](https://developer.wordpress.org/reference/functions/wp_get_attachment_image_src/)`. It returns an array (URL, width, height, is\_intermediate), or `false`, if no image is available.
 -->

画像の URL を取得したい場合は、[`wp_get_attachment_image_src()`](https://developer.wordpress.org/reference/functions/wp_get_attachment_image_src/) を使用しましょう。この関数は、配列 (URL、幅、高さ、`is_intermediate`) を、あるいは、画像が存在しない場合は `false` を返します。

```php
<?php 
$image_attributes = wp_get_attachment_image_src( $attachment->ID );
if ( $image_attributes ) : ?>
    <img src="<?php echo $image_attributes[0]; ?>" width="<?php echo $image_attributes[1]; ?>" height="<?php echo $image_attributes[2]; ?>" />
<?php endif; ?>
```

<!-- 
### Alignments
 -->

### 位置合わせ

<!-- 
When adding the image in your site, you can specify the image alignment as right, left, center or none. WordPress core automatically adds CSS classes to align the image:
 -->

あなたのサイトに画像を追加する際、画像の位置合わせを右寄せ、左寄せ、中央寄せ、またはそろえなしとして指定できます。WordPress コアは、画像の位置合わせを行うために、自動的に CSS クラスを追加します:

<!-- 
*   alignright
*   alignleft
*   aligncenter
*   alignnone
 -->

*   `alignright`
*   `alignleft`
*   `aligncenter`
*   `alignnone`

<!-- 
This is the sample output when center align si chosen
 -->

中央寄せを指定した場合のサンプル出力は、以下の通りです:

```markup
<img class="aligncenter size-full wp-image-131" src= ... />
```

<!-- 
In order to take advantage of these CSS classes for alignment and text wrapping, your theme must include the styles in a stylesheet such as the [main stylesheet file](https://developer.wordpress.org/themes/basics/main-stylesheet-style-css/). You can use the `style.css` bundled with official themes such as Twenty Seventeen for reference.
 -->

これらの CSS クラスによる位置合わせやテキストの折り返しを活用するには、あなたのテーマが [メインスタイルシートファイル](https://developer.wordpress.org/themes/basics/main-stylesheet-style-css/) などのスタイルシートに、これらのスタイルを含んでいる必要があります。「Twenty Seventeen」などの公式テーマにバンドルされている `style.css` を、リファレンスとして使用できます。

<!-- 
### Caption
 -->

### キャプション

<!-- 
If a Caption was specified to image in the Media Library, HTML `img` element was enclosed by the shortcode \[caption\] and \[/caption\].
 -->

「メディアライブラリ」内の画像に「キャプション」が指定された場合、HTML `img` 要素は、ショートコード `[caption]` と `[/caption]` で囲まれます。

```markup
<div class="mceTemp">
  <dl id="attachment_133" class="wp-caption aligncenter" style="width: 1210px">
    <dt class="wp-caption-dt">
      <img class="size-full wp-image-133" src="http://example.com/wordpress/wp-content/uploads/2016/11/sample.jpg" alt="sun set" width="1200" height="400" />
    </dt>
    <dd class="wp-caption-dd">Sun set over the sea</dd>
  </dl>
</div>
```

<!-- 
And, it will be rendered as in HTML as the figure tag:
 -->

そして、HTML では、`figure` タグとしてレンダリングされます:

```markup
<figure id="attachment_133" style="width: 1200px" class="wp-caption aligncenter">
  <img class="size-full wp-image-133" src="http://example.com/wordpress/wp-content/uploads/2016/11/sample.jpg" alt="sun set" width="1200" height="400" srcset= ... />
  <figcaption class="wp-caption-text">Sun set over the sea</figcaption>
</figure>
```

<!-- 
Similar to alignments, your theme must include following styles.
 -->

位置合わせと同様に、あなたのテーマには、下記スタイルを含める必要があります。

<!-- 
*   `wp-caption`
*   `wp-caption-text`
 -->

*   `wp-caption`
*   `wp-caption-text`

<!-- 
## WebP support and default MIME type of sub size image output
 -->

## WebP サポートと、サブサイズ画像出力のデフォルト MIME タイプ

<!-- 
[WordPress 5.8](https://make.wordpress.org/core/2021/06/07/wordpress-5-8-adds-webp-support/) introduces support for [WebP](https://developers.google.com/speed/webp) image format which provides improved lossless and lossy compression for images on the web. WebP images are around 30% smaller on average than their JPEG or PNG equivalents, resulting in sites that are faster and use less bandwidth. WebP is supported in all modern browsers [according to caniuse](https://caniuse.com/webp).
 -->

[WordPress v5.8](https://make.wordpress.org/core/2021/06/07/wordpress-5-8-adds-webp-support/) では、Web 上の画像向けにロスレス圧縮とロス圧縮を改善した [WebP](https://developers.google.com/speed/webp) 画像フォーマットのサポートが導入されました。WebP 画像は、JPEG や PNG の同等画像と比較して平均で約30%小さいため、サイトの高速化と帯域幅の削減につながります。WebP は、[caniuse](https://caniuse.com/webp)によれば、すべての最新ブラウザーでサポートされています。

<!-- 
When images are uploaded, WordPress generates smaller sub sizes as defined using `add_image_size()`. By default, WordPress will generate these sub sizes in the same format as the original. Because of the performance benefits of the WebP format, it may be desirable for sub sizes to be generated in WebP instead of the original format.
 -->

画像がアップロードされると、WordPress は `add_image_size()` を使用して定義された、より小さな「サブサイズ」を生成します。デフォルトでは、WordPress は、これらのサブサイズを、元画像と同じフォーマットで生成します。WebP フォーマットのパフォーマンス上の利点から、元画像フォーマットではなく WebP で、サブサイズを生成することが望ましい場合があります。

<!-- 
`image_editor_output_format` filter hook can be used to change the file format used for image sub sizes. This can be used to switch all sub sizes to WebP, or any other desired format (JPEG, etc.).
 -->

`image_editor_output_format` フィルターフックを使用すると、画像のサブサイズ用ファイルフォーマットを変更できます。これにより、すべてのサブサイズを、WebP やその他の任意のフォーマット (JPEG 等) にスイッチさせることも可能です。

<!-- 
The following example shows how to generate all sub sizes for JPG images using WebP:
 -->

下記の例は、WebP を使用して、JPG 画像のすべてのサブサイズを生成する方法を示しています:

```php
<?php
function wporg_image_editor_output_format( $formats ) {
    $formats['image/jpg'] = 'image/webp';
 
    return $formats;
}
add_filter( 'image_editor_output_format', 'wporg_image_editor_output_format' );
```

<!-- 
**Note:** both the GD and ImageMagick libraries support the WebP format in both lossy and lossless. However, only ImageMagick supports animated images.
 -->

**注記:** GD ライブラリと ImageMagick ライブラリの双方が、WebP 形式のロス圧縮とロスレス圧縮の両方をサポートしています。ただし、アニメーション画像をサポートしているのは、ImageMagick のみです。

<!-- 
Setting the output format to WebP will verify if the web server supports it, and if not it will not change the format, i.e. won’t work.
 -->

出力フォーマットを WebP にセットすると、Web サーバーがそれをサポートしているか検証し、サポートしていない場合はフォーマットを変更されません (つまり適用されない)。

<!-- 
#### References
 -->

#### リファレンス

<!-- 
*   `[wp_get_attachment_image()](https://developer.wordpress.org/reference/functions/wp_get_attachment_image/)`
*   `[wp_get_attachment_image_src()](https://developer.wordpress.org/reference/functions/wp_get_attachment_image_src/)`
*   [Styling Images in Posts and Pages](https://codex.wordpress.org/Styling_Images_in_Posts_and_Pages)
*   [CSS (Codex)](https://codex.wordpress.org/CSS)
 -->

*   [`wp_get_attachment_image()`](https://developer.wordpress.org/reference/functions/wp_get_attachment_image/)
*   [`wp_get_attachment_image_src()`](https://developer.wordpress.org/reference/functions/wp_get_attachment_image_src/)
*   [投稿とページでの、画像のスタイリング](https://codex.wordpress.org/Styling_Images_in_Posts_and_Pages)
*   [CSS (Codex)](https://codex.wordpress.org/CSS)