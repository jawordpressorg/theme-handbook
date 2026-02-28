<!-- 
# Media
 -->

# メディア

<!-- 
WordPress enables theme developers to customize the look, feel, and functionality of the platform’s core media capabilities.
 -->

WordPress は、テーマ開発者がプラットフォームのコアメディア機能のルック & フィールと機能を、カスタマイズできるようにします。

<!-- 
## General
 -->

## 総則

<!-- 
In WordPress you can upload, store, and display a variety of media such as image, video and audio files. Media can be uploaded via the **Media > Add New** in the [Administration Screen](https://codex.wordpress.org/Administration_Screens), or Add Media button on the Post/Page Editor.
 -->

WordPress では、画像、動画、音声ファイルなどさまざまなメディアをアップロード、保存、表示できます。メディアは、[管理画面](https://codex.wordpress.org/Administration_Screens) 内の **メディア > メディアファイルを追加**、または投稿エディター/ページエディター上の「メディア追加」ボタン経由でアップロードできます。

<!-- 
If a media file is uploaded within the edit screen, it will be automatically attached to the current post being created or edited. If it is uploaded via the Media’s Add New Screen or the Media Library Screen, it will be unattached, but may become attached to a post when it is inserted into a post later on.
 -->

メディアファイルを編集画面内でアップロードした場合、作成中または編集中の、現在の投稿に自動的に添付されます。メディアの「新規追加」画面または「メディアライブラリ」画面経由でアップロードした場合、添付はされず、後で投稿に挿入すると添付されます。

<!-- 
### Retrieving attachment ID or image ID
 -->

### 添付ファイル ID または画像 ID の取得

<!-- 
To retrieve the attachment ID, use `[get_posts()](https://developer.wordpress.org/reference/functions/get_posts/)` or `[get_children()](https://developer.wordpress.org/reference/functions/get_children/)` function. This example retrieves the all attachments of the current post and getting all metadata of attachment by specifying the ID.
 -->

添付ファイル ID を取得するには、[`get_posts()`](https://developer.wordpress.org/reference/functions/get_posts/) または [`get_children()`](https://developer.wordpress.org/reference/functions/get_children/) 関数を使用しましょう。本例では、現在の投稿のすべての添付ファイルを取得し、ID を指定することで、添付ファイルのすべてのメタデータを取得します。

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

<!-- 
If you want to retrieve images from the post ID only, specify post\_mime\_type as image.
 -->

投稿 ID のみから画像を取得したい場合は、`post_mime_type` を `image` として指定しましょう。

```php
$args = array(
    'post_parent'    => get_the_ID(),
    'post_type'      => 'attachment',
    'post_mime_type' => 'image',
);
```

<!-- 
#### References
 -->

#### リファレンス

<!-- 
*   `[get_posts()](https://developer.wordpress.org/reference/functions/get_posts/)`
*   `[get_children()](https://developer.wordpress.org/reference/functions/get_children/)`
*   `[wp_get_attachment_metadata()](https://developer.wordpress.org/reference/functions/wp_get_attachment_metadata/)`
 -->

*   [`get_posts()`](https://developer.wordpress.org/reference/functions/get_posts/)
*   [`get_children()`](https://developer.wordpress.org/reference/functions/get_children/)
*   [`wp_get_attachment_metadata()`](https://developer.wordpress.org/reference/functions/wp_get_attachment_metadata/)

<!-- 
## Special considerations
 -->

## 特別な考慮事項

<!-- 
### Compatible media formats
 -->

### 互換性のある、メディアフォーマット

<!-- 
In the Media Library, you can upload any file (with the network administrator’s unfiltered\_upload) and not just images or videos but text files, office documents or even binary files. Single site administrators do not have the unfiltered\_upload capability by default and requires that definition to be set for the capability to kick in. Audio and Video files are processed by the internal library `MediaElement.js`.
 -->

「メディアライブラリ」では、(ネットワーク管理者の `unfiltered_upload` 権限があれば) 画像や動画だけでなく、テキストファイル、オフィス文書、さらにはバイナリファイルなど、あらゆるファイルをアップロードできます。シングルサイト管理者は、デフォルトで `unfiltered_upload` 権限を持たず、その権限を発動させるために、定義の設定が必要です。音声ファイルと動画ファイルは、内部ライブラリ `MediaElement.js` によって処理されます。

<!-- 
*   [Supported Audio format](https://developer.wordpress.org/?post_type=theme-handbook&p=25145#supported-audio-format)
*   [Supported Video format](https://developer.wordpress.org/themes/functionality/media/video/#supported-video-format)
 -->

*   [サポートされている音声フォーマット](https://developer.wordpress.org/?post_type=theme-handbook&p=25145#supported-audio-format)
*   [サポートされている動画フォーマット](https://developer.wordpress.org/themes/functionality/media/video/#supported-video-format)

<!-- 
### Troubleshooting:
 -->

### トラブルシューティング:

<!-- 
#### Cannot retrieve attachment
 -->

#### 添付ファイルを取得できない

<!-- 
When you cannot get your attached media by `[get_posts()](https://developer.wordpress.org/reference/functions/get_posts/)` or `[get_children()](https://developer.wordpress.org/reference/functions/get_children/)` function, confirm your media is really attached to the post.  
From the [Administration Screen](https://codex.wordpress.org/Administration_Screens), Click **Media > Library** to open the Media Library and confirm the value in “Uploaded to” column of the media.
 -->

[`get_posts()`](https://developer.wordpress.org/reference/functions/get_posts/) または [`get_children()`](https://developer.wordpress.org/reference/functions/get_children/) 関数であなたの添付メディアを取得できない場合、あなたのメディアが投稿に実際に添付されているか確認しましょう。[管理画面](https://codex.wordpress.org/Administration_Screens) から、**メディア > ライブラリ** をクリックして「メディアライブラリ」を開き、メディアの「アップロード先」カラムの値を確認しましょう。