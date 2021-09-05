# Video

## Video

The WordPress video feature allows you to embed video files and play them back using a simple shortcode **\[video\]**. Supported file types are mp4, m4v, webm, ogv, wmv and flv.

### Video shortcode

Following shortcode displays video player that loads pepper.mp4 file:

\[video src="pepper.mp4"\]

To use the shortcode in the template file, use the do\_shortcode() function. If the video file is stored in in your theme directory, get the file url directly using get\_template\_directory\_uri() or get\_stylesheet\_uri()

$video\_file = get\_template\_directory\_uri() . "/videos/pepper.mp4";
echo do\_shortcode('\[video mp4=' . $video\_file . '\]');

The following video player will be loaded.

### Loop and Autoplay

The shortcode video has the same option with audio. Refer to the related section for the [loop and autoplay](#loop-and-autoplay) options.

The following example starts playing the video immediately after the page load and loops.

echo do\_shortcode('\[video mp4=' . $video\_file . ' loop = "on" autoplay = 1\]');

### Initial image and Styling

The following basic options are supported:

#### Poster

Defines image to show as placeholder before the media plays.  
The following same code takes `album_cover.jpg` stored in `(theme directory)/images` folder as the initial image:

echo do\_shortcode('\[video mp4=' . $video\_file . ' poster = ' . get\_template\_directory\_uri() . '/images/album\_cover.jpg\]');

#### Height

Defines height of the media. Value is automatically detected on file upload. When you omit this option, the media file height is used.

#### Width

Defines width of the media. Value is automatically detected on file upload. When you omit this option, the media file width is used.  

Tip: The theme’s content\_width sets the maximum width.

  
The following example will load the audio player with 320 pixels width and 240 pixels height:

echo do\_shortcode('\[video mp4=' . $video\_file . ' width = 320 height = 240\]');

#### Styling

If you want to change look & feel of video player from stylesheet, you can target the class name of “wp-video-shortcode”. If you want to show the audio player like above in 320 x 240 size, insert following code into your stylesheet.

.wp-video-shortcode {
	width: 320px;
	height: 240px;
}

#### Supported Video format

*   mp4
*   m4v
*   webm
*   ogv
*   flv

### References

For more technical details such as internal library that enables this function, refer to

*   [https://make.wordpress.org/core/2013/04/08/audio-video-support-in-core/](https://make.wordpress.org/core/2013/04/08/audio-video-support-in-core/).
*   [Video Shortcode](https://codex.wordpress.org/Video_Shortcode)
*   [Function do\_shortcode()](https://developer.wordpress.org/reference/functions/do_shortcode/)