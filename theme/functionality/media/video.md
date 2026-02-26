<!-- 
# Video
 -->

# 動画

<!-- 
## Video
 -->

## 動画

<!-- 
The WordPress video feature allows you to embed video files and play them back using a simple shortcode **\[video\]**. Supported file types are mp4, m4v, webm, ogv, wmv and flv.
 -->

WordPress の動画機能では、シンプルなショートコード **`[video]`** を使用して動画ファイルを埋め込み、再生できます。対応ファイル形式は、`mp4`、`m4v`、`webm`、`ogv`、`wmv`、`flv` です。

<!-- 
### Video shortcode
 -->

### 「動画」ショートコード

<!-- 
Following shortcode displays video player that loads pepper.mp4 file:
 -->

下記ショートコードは、`pepper.mp4` ファイルをロードする、ビデオプレイヤーを表示します:

```php
[video src="pepper.mp4"]
```

<!-- 
To use the shortcode in the template file, use the [do\_shortcode()](https://developer.wordpress.org/reference/functions/do_shortcode/) function. If the video file is stored in in your theme directory, get the file url directly using [get\_template\_directory\_uri()](https://developer.wordpress.org/reference/functions/get_template_directory_uri/) or [get\_stylesheet\_uri()](https://developer.wordpress.org/reference/functions/get_stylesheet_uri/) :
 -->

テンプレートファイルでショートコードを使用するには、[`do_shortcode()`](https://developer.wordpress.org/reference/functions/do_shortcode/) 関数を使用しましょう。動画ファイルがあなたのテーマディレクトリ内に保存されている場合、[`get_template_directory_uri()`](https://developer.wordpress.org/reference/functions/get_template_directory_uri/) または [`get_stylesheet_uri()`](https://developer.wordpress.org/reference/functions/get_stylesheet_uri/) を使用して、ファイル URL を直接取得しましょう:

```php
$video_file = get_template_directory_uri() . "/videos/pepper.mp4";
echo do_shortcode( '[video mp4=' . $video_file . ']' );
```

<!-- 
The following video player will be loaded.
 -->

下記のビデオプレイヤーがロードされます。

<!-- 
### Loop and Autoplay
 -->

### `loop` と `autoplay`

<!-- 
The shortcode video has the same option with audio. Refer to the related section for the [loop and autoplay](#loop-and-autoplay) options.
 -->

ショートコード `video` は、オーディオと同じオプションを持ちます。[`loop` と `autoplay`](#loop-and-autoplay) オプションについては、関連セクションを参照してください。

<!-- 
The following example starts playing the video immediately after the page load and loops:
 -->

下記の例は、ページロード直後から動画を再生し、ループします:

```php
echo do_shortcode( '[video mp4=' . $video_file . ' loop="on" autoplay=1]' );
```

<!-- 
### Initial image and Styling
 -->

### 初期画像とスタイリング

<!-- 
The following basic options are supported:
 -->

下記の基本オプションが、サポートされています:

<!-- 
#### Poster
 -->

#### `poster`

<!-- 
Defines image to show as placeholder before the media plays.  
The following same code takes `album_cover.jpg` stored in `(theme directory)/images` folder as the initial image:
 -->

メディア再生前のプレースホルダーとして表示する、画像を定義します。下記の同じコードは、`(theme_directory)/images` フォルダーに保存されている `album_cover.jpg` を、初期画像として使用します:

```php
echo do_shortcode( '[video mp4=' . $video_file . ' poster=' . get_template_directory_uri() . '/images/album_cover.jpg]' );
```

<!-- 
#### Height
 -->

#### `height`

<!-- 
Defines height of the media. Value is automatically detected on file upload. When you omit this option, the media file height is used.
 -->

メディアの高さを定義します。値は、ファイルアップロード時に、自動的に検出されます。本オプションを省略した場合、メディアファイルの高さが使用されます。

<!-- 
#### Width
 -->

#### `width`

<!-- 
Defines width of the media. Value is automatically detected on file upload. When you omit this option, the media file width is used.
 -->

メディアの幅を定義します。値は、ファイルアップロード時に、自動的に検出されます。本オプションを省略した場合、メディアファイルの幅が使用されます。

<!-- 
The theme’s content\_width sets the maximum width.
 -->

テーマの `content_width` は、最大幅をセットします。

<!-- 
The following example will load the audio player with 320 pixels width and 240 pixels height:
 -->

下記の例では、幅320ピクセル、高さ240ピクセルで、ビデオプレイヤーをロードします:

```php
echo do_shortcode( '[video mp4=' . $video_file . ' width=320 height=240]' );
```

<!-- 
#### Styling
 -->

#### スタイリング

<!-- 
If you want to change look & feel of video player from stylesheet, you can target the class name of “wp-video-shortcode”. If you want to show the audio player like above in 320 x 240 size, insert following code into your stylesheet:
 -->

ビデオプレイヤーのルック & フィールをスタイルシートから変更したい場合は、`wp-video-shortcode` のクラス名をターゲットにできます。上記のように320x240サイズでビデオプレイヤーを表示したい場合は、下記コードをあなたのスタイルシートに挿入しましょう:

```css
.wp-video-shortcode {
    height: 240px;
    width: 320px;
}
```

<!-- 
#### Supported Video format
 -->

#### サポートされている動画フォーマット

<!-- 
*   mp4
*   m4v
*   webm
*   ogv
*   flv
 -->

*   `mp4`
*   `m4v`
*   `webm`
*   `ogv`
*   `flv`

<!-- 
### References
 -->

### リファレンス

<!-- 
For more technical details such as internal library that enables this function, refer to
 -->

この関数を可能にする内部ライブラリなどの、技術的な詳細情報については、以下をご覧ください:

<!-- 
*   [https://make.wordpress.org/core/2013/04/08/audio-video-support-in-core/](https://make.wordpress.org/core/2013/04/08/audio-video-support-in-core/).
*   [Video Shortcode](https://codex.wordpress.org/Video_Shortcode)
*   [Function do\_shortcode()](https://developer.wordpress.org/reference/functions/do_shortcode/)
 -->

*   [コアでの、音声/動画サポート](https://make.wordpress.org/core/2013/04/08/audio-video-support-in-core/)
*   [「動画」ショートコード](https://codex.wordpress.org/Video_Shortcode)
*   [関数 `do_shortcode()`](https://developer.wordpress.org/reference/functions/do_shortcode/)