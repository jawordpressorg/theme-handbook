<!-- 
# Audio
 -->

# 音声

<!-- 
## Audio
 -->

## 音声

<!-- 
You can directly embed audio files and play them back using a simple shortcode **\[audio\]**. Supported file types are mp3, ogg, wma, m4a and wav.
 -->

音声ファイルを直接埋め込みしたり、シンプルなショートコード **`[audio]`** を使用して再生できます。対応ファイル形式は `mp3`、`ogg`、`wma`、`m4a`、`wav` です。

<!-- 
### Audio shortcode
 -->

### 「音声」ショートコード

<!-- 
Following shortcode displays audio player that loads music.mp3 file:
 -->

以下のショートコードは、`music.mp3` ファイルをロードする、オーディオプレイヤーを表示します:

```php
[[audio src="music.mp3"]]
```

<!-- 
To use the shortcode from template file, use do\_shortcode function. When music.mp3 file was stored in (theme\_directory)/sounds directory, insert following code into your template file:
 -->

テンプレートファイルからショートコードを使用するには、`do_shortcode` 関数を使用します。`music.mp3` ファイルが `(theme_directory)/sounds` ディレクトリに保存されている場合、あなたのテンプレートファイルに、以下のコードを挿入しましょう:

```php
$music_file = get_template_directory_uri() . "/sounds/music.mp3";
echo do_shortcode('[[audio mp3=' . $music_file . ']]');
```

<!-- 
The shortcode creates the audio player as shown in the screenshot below.
 -->

このショートコードは、以下のスクリーンショットに示すように、オーディオプレイヤーを作成します。

<!-- 
![Audio player](https://i0.wp.com/developer.wordpress.org/files/2014/10/audio_shortcode_basic.jpg?resize=558%2C66&ssl=1)
 -->

![オーディオプレイヤー](https://i0.wp.com/developer.wordpress.org/files/2014/10/audio_shortcode_basic.jpg?resize=558%2C66&ssl=1)

<!-- 
### Loop and Autoplay
 -->

### ループ再生と自動再生

<!-- 
The following basic options are supported:
 -->

下記の基本オプションが、サポートされています:

<!-- 
#### loop
 -->

#### `loop`

<!-- 
Allows for the looping of media.
 -->

メディアのループ再生を可能にします。

<!-- 
*   “off” – Do not loop the media. Default.
*   “on” – Media will loop to beginning when finished and automatically continue playing.
 -->

*   「off」– メディアをループ再生しません。デフォルトです。
*   「on」– メディアの再生が終了すると先頭からループ再生され、自動的に再生が継続されます。

<!-- 
#### autoplay
 -->

#### `autoplay`

<!-- 
Causes the media to automatically play as soon as the media file is ready.
 -->

メディアファイルの準備が整うとすぐに、メディアを自動的に再生します。

<!-- 
*   0 – Do not automatically play the media. Default.
*   1 – Media will play as soon as it is ready.
 -->

*   0 – メディアを自動再生しません。デフォルトです。
*   1 – メディアの準備が整い次第、再生を開始します。

<!-- 
The following example starts playing music immediately after the page load and loops.
 -->

下記の例は、ページロード直後から音楽を再生し、ループします。

```php
echo do_shortcode('[[audio mp3=' . $music_file . ' loop = "on" autoplay = 1]]');
```

<!-- 
### Styling
 -->

### スタイリング

<!-- 
If you want to change the look & feel of audio player, you can do so by targeting the default class name of “wp-audio-shortcode”. If you insert following code into your style.css, half width of audio player will be displayed.
 -->

オーディオプレイヤーのルック & フィールを変更したい場合は、デフォルトのクラス名 `wp-audio-shortcode` をターゲットに設定することで実現できます。下記コードをあなたの `style.css` に挿入すると、オーディオプレイヤーの幅が、半分のサイズで表示されます。

```css
.wp-audio-shortcode {
  width: 50%;
}
```

<!-- 
#### Supported Audio format
 -->

#### 対応音声フォーマット

<!-- 
*   mp3
*   ogg
*   wma
*   m4a
*   wav
 -->

*   mp3
*   ogg
*   wma
*   m4a
*   wav

<!-- 
### References
 -->

### リファレンス

<!-- 
For more technical details such as the internal library that enables this function, refer to
 -->

この関数を可能にする内部ライブラリなどの、技術的な詳細情報については、以下をご覧ください:

<!-- 
*   [https://make.wordpress.org/core/2013/04/08/audio-video-support-in-core/](https://make.wordpress.org/core/2013/04/08/audio-video-support-in-core/).
*   [Audio Shortcode](https://codex.wordpress.org/Audio_Shortcode)
*   [Function do\_shortcode()](https://developer.wordpress.org/reference/functions/do_shortcode/)
 -->

*   [コアでの、音声/動画サポート](https://make.wordpress.org/core/2013/04/08/audio-video-support-in-core/).
*   [「音声」ショートコード](https://codex.wordpress.org/Audio_Shortcode)
*   [関数 `do_shortcode()`](https://developer.wordpress.org/reference/functions/do_shortcode/)
