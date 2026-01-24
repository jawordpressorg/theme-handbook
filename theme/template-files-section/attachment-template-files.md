<!-- 
# Attachment Template Files
 -->

# 添付テンプレート・ファイル

<!-- 
Attachments are a special post type that holds information about a file uploaded through the WordPress media upload system, such as its description and name, which can display through several **post type – attachment** template files.
 -->

添付ファイルは、WordPress のメディア・アップロード・システムを通じてアップロードされたファイルに関する情報 (説明や名称など) を保持する、特別な投稿タイプであり、複数の **投稿タイプ – 添付ファイル** テンプレート・ファイルを通じて表示できます。

<!-- 
For images, as an example, the attachment post type links to metadata information, about the size of the images, the thumbnails generated, the location of the image files, the HTML alt text, and even information obtained from EXIF data embedded in the images.
 -->

画像の場合、たとえば投稿タイプ `attachment` は、画像のサイズ、生成されたサムネイル、画像ファイルの保存場所、HTML 代替テキスト、さらには画像に埋め込まれた EXIF データから取得した情報といった、メタデータ情報にリンクします。

<!-- 
Utilizing attachment templates to gain additional metadata information for uploads, help with SEO efforts.
 -->

アップロード用の添付テンプレートを活用し、追加のメタデータ情報を取得することで、SEO 対策を支援します。

<!-- 
As shown in the [template hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/#visual-overview), you are able to display your attachments through several template files in order of fallback:
 -->

[テンプレート階層](https://developer.wordpress.org/themes/basics/template-hierarchy/#visual-overview) に示されているように、フォールバック順に、複数のテンプレート・ファイルを通じて、添付ファイルを表示できます:

<!-- 
1.  `MIME_type.php` and a `subtype.php`  
    It can be any MIME type (For example: `image.php`, `video.php`, `application.php`). For text/plain, the following path is used (in order):
    1.  `text_plain.php`
    2.  `plain.php`
    3.  `text.php`
2.  `attachment.php`
3.  `single-attachment.php`
4.  `single.php`
5.  `singular.php`
6.  `index.php`
 -->

1.  `MIME_type.php` と `subtype.php`
   任意の MIME タイプが可能です (例: `image.php`、`video.php`、`application.php`)。`text/plain` の場合、以下のパスが順に使用されます: 
   1.  `text_plain.php`
   2.  `plain.php`
   3.  `text.php`
2.  `attachment.php`
3.  `single-attachment.php`
4.  `single.php`
5.  `singular.php`
6.  `index.php`

<!-- 
## MIME\_type.php
 -->

## `MIME_type.php`

<!-- 
Attachments are served by template files based on their mime-type. As an example, if your attachment is an image, your can customize how they display through the creation of an `image.php` template file. All images with the `post_mime_type` of image/\* will render though your `image.php` template file.
 -->

添付ファイルは、その MIME タイプにもとづいてテンプレート・ファイルによって提供されます。たとえば、添付ファイルが画像の場合、`image.php` テンプレート・ファイルを作成することで、表示方法をカスタマイズできます。`post_mime_type` が `image/*` であるすべての画像は、`image.php` テンプレート・ファイルを通じてレンダリングされます。

<!-- 
Attachments also support the use of a mime `subtype.php` file. To continue with the image example, you can further customize your theme to support not only an `image.php` file but a `jpg.php` subtype file.
 -->

添付ファイルは、MIME `subtype.php` ファイルの使用も、サポートしています。画像の例を続けると、あなたのテーマをさらにカスタマイズして、`image.php` ファイルだけでなく、`jpg.php` サブタイプ・ファイルも、サポートできるようにできます。

<!-- 
## Attachment.php
 -->

## `attachment.php`

<!-- 
An attachment page (`attachment.php`) is a single post page with the post type of attachment, generated through the creation of an attachment.php. Just like a [single post page](https://developer.wordpress.org/themes/template-files-section/post-template-files/#single-php), which is dedicated to your article, the attachment page provides a dedicated page in attachments in your theme.
 -->

添付ファイル・ページ (`attachment.php`) は、投稿タイプ `attachment` の個別投稿ページであり、`attachment.php` の作成を通じて生成されます。[個別投稿ページ](https://developer.wordpress.org/themes/template-files-section/post-template-files/#single-php) があなたの記事専用のページであるように、添付ファイル・ページは、あなたのテーマ内の添付ファイルに、専用のページを提供します。

<!-- 
Creation of attachment page is as simple as creating an attachment.php file. The attachment.php file then contains code similar to the single.php post page.
 -->

添付ファイル・ページの作成は、`attachment.php` ファイルを作成するのと同じくらい簡単です。`attachment.php` ファイルには、投稿ページ用の `single.php` と同様のコードが含まれます。

```php
<div class="entry-attachment">
	<?php
	$image_size = apply_filters( 'wporg_attachment_size', 'large' );
	echo wp_get_attachment_image( get_the_ID(), $image_size );
	?>

	<?php if ( has_excerpt() ) : ?>
		<div class="entry-caption">
			<?php the_excerpt(); ?>
		</div><!-- .entry-caption -->
	<?php endif; ?>
</div><!-- .entry-attachment -->
```

<!-- 
## Function Reference
 -->

## 関数リファレンス

<!-- 
*   [get\_attachment\_template()](https://developer.wordpress.org/reference/functions/get_attachment_template/) : Retrieve path of attachment template in current or parent template.
 -->

*   [`get_attachment_template()`](https://developer.wordpress.org/reference/functions/get_attachment_template/): 現在のテンプレートまたは親テンプレート内の、添付ファイル用テンプレートのパスを取得します。