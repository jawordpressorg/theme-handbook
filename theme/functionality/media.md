# Media

WordPress enables theme developers to customize the look, feel, and functionality of the platform’s core media capabilities.

## General

In WordPress you can upload, store, and display a variety of media such as image, video and audio files. Media can be uploaded via the **Media > Add New** in the [Administration Screen](https://codex.wordpress.org/Administration_Screens), or Add Media button on the Post/Page Editor. If a media file is uploaded within the edit screen, it will be automatically attached to the current post being created or edited. If it is uploaded via the Media’s Add New Screen or the Media Library Screen, it will be unattached, but may become attached to a post when it is inserted into a post later on.

### Retrieving attachment ID or image ID

To retrieve the attachment ID, use `[get_posts()](https://developer.wordpress.org/reference/functions/get_posts/)` or `[get_children()](https://developer.wordpress.org/reference/functions/get_children/)` function. This example retrieves the all attachments of the current post and getting all metadata of attachment by specifying the ID.

```php
// Insert into the Loop
$args = array(
    'post_parent'    => get_the_ID(),
    'post_type'      => 'attachment',
);
$attachments = get_posts( $args );
if ( $attachments ) {
    foreach ( $attachments as $attachment ) {
        $meta_data = wp_get_attachment_metadata( $attachment->ID, false );
    }
}
```

If you want to retrieve images from the post ID only, specify post\_mime\_type as image.

```php
$args = array(
    'post_parent'    => get_the_ID(),
    'post_type'      => 'attachment',
    'post_mime_type' => 'image',
);
```

#### References

*   `[get_posts()](https://developer.wordpress.org/reference/functions/get_posts/)`
*   `[get_children()](https://developer.wordpress.org/reference/functions/get_children/)`
*   `[wp_get_attachment_metadata()](https://developer.wordpress.org/reference/functions/wp_get_attachment_metadata/)`

## Special considerations

### Compatible media formats

In the Media Library, you can upload any file (with the network administrator’s unfiltered\_upload) and not just images or videos but text files, office documents or even binary files. Single site administrators do not have the unfiltered\_upload capability by default and requires that definition to be set for the capability to kick in. Audio and Video files are processed by the internal library `MediaElement.js`.

*   [Supported Audio format](https://developer.wordpress.org/?post_type=theme-handbook&p=25145#supported-audio-format)
*   [Supported Video format](https://developer.wordpress.org/themes/functionality/media/video/#supported-video-format)

### Troubleshooting:

#### Cannot retrieve attachment

When you cannot get your attached media by `[get_posts()](https://developer.wordpress.org/reference/functions/get_posts/)` or `[get_children()](https://developer.wordpress.org/reference/functions/get_children/)` function, confirm your media is really attached to the post. From the [Administration Screen](https://codex.wordpress.org/Administration_Screens), Click **Media > Library** to open the Media Library and confirm the value in “Uploaded to” column of the media.
