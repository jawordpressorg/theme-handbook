<!-- 
# Debugging
 -->

# デバッグ

<!-- 
Debugging is the practice of finding and fixing errors in any software that you build. And it is an essential part of WordPress theme development, regardless of whether you are building a block or classic theme. 
 -->

デバッグとは、ビルドしたソフトウェアのエラーを見つけて修正するプロセスです。ブロック・テーマやクラシック・テーマの構築に関係なく、WordPress テーマ開発には欠かせない処理です。

<!-- 
WordPress provides some tools out of the box, but there are also plugins that you can use to enhance the experience. You’ll learn about some of these methods in this article, but you should also study the [Debugging in WordPress](https://wordpress.org/documentation/article/debugging-in-wordpress/) documentation in the Common APIs handbook.
 -->

WordPress はすぐに使えるツールをいくつか提供していますが、エクスペリエンスの向上に使えるプラグインもあります。本稿ではこれらの方法のいくつかを学びますが、共通 API ハンドブックにある [WordPress でのデバッグ](https://wordpress.org/documentation/article/debugging-in-wordpress/) ドキュメントも学習してください。

<!-- 
## Debugging constants
 -->

## デバッグ定数

<!-- 
When creating themes from within a development environment, you should always enable debugging to ensure that your theme is not creating notices or errors. WordPress offers several constants, which you can set in your installation’s `wp-config.php` file.
 -->

開発環境でテーマを制作する際には、テーマから通知やエラーが出ていないことを確認するために、常にデバッグを有効にしてください。WordPress はいくつかの定数を提供しており、インストール先の `wp-config.php` ファイルで設定できます。

<!-- 
If you open the `wp-config.php` file, scroll down until you locate this code:
 -->

`wp-config.php` ファイルを開いたら、このコードが見つかるまで下にスクロールしてください:

```php
/**
 * For developers: WordPress debugging mode.
 *
 * Change this to true to enable the display of notices during development.
 * It is strongly recommended that plugin and theme developers use WP_DEBUG
 * in their development environments.
 *
 * For information on other constants that can be used for debugging,
 * visit the documentation.
 *
 * @link https://wordpress.org/documentation/article/debugging-in-wordpress/
 */
define( 'WP_DEBUG', false );
```

<!-- 
This is where you will configure any debugging constants outlined in the sections below. 
 -->

ここで、以下のセクションで説明する、デバッグ定数を設定します。 

<!-- 
### WP\_DEBUG
 -->

### `WP_DEBUG`

<!-- 
The `WP_DEBUG` constant is the only one defined in a default WordPress installation’s `wp-config.php` file. In a standard install, it is set to `false`, but it is set to `true` if you are running a development copy of WordPress.
 -->

`WP_DEBUG` 定数は、デフォルトの WordPress インストールの `wp-config.php` ファイルで定義されている、唯一の定数です。標準的なインストールでは `false` に設定されていますが、開発用に WordPress を実行している場合は `true` に設定します。

<!-- 
The `WP_DEBUG` PHP constant is used to trigger the built-in “debug” mode on your WordPress installation. This allows you to view errors in your theme. It should be used in conjunction with all of the other debugging constants listed in the next sections.
 -->

`WP_DEBUG` PHP 定数は、WordPress に内蔵された「デバッグ」モードの起動に使用されます。この起動によりテーマ内のエラーを表示できます。この定数は次のセクションで挙げた他のすべてのデバッグ定数と組み合わせて使用する必要があります。

<!-- 
You should see this line in your `wp-config.php` file:
 -->

あなたの `wp-config.php` ファイルに、この行があるでしょう:

```php
define( 'WP_DEBUG', false );
```

<!-- 
To enable debugging, make sure it is set to `true`, as shown here:
 -->

デバグを有効にするには、ここに示すように、`true` に設定されていることを確認します:

```php
define( 'WP_DEBUG', true );
```

<!-- 
### WP\_DISABLE\_FATAL\_ERROR\_HANDLER
 -->

### `WP_DISABLE_FATAL_ERROR_HANDLER`

<!-- 
WordPress 5.2 [introduced a fatal error handler](https://make.wordpress.org/core/2019/04/16/fatal-error-recovery-mode-in-5-2/) to ensure that users do not get locked out of their site when a theme or plugin causes a fatal error. This is a great feature in production/live sites. But it can be problematic in development, preventing you from fully diagnosing errors.
 -->

テーマやプラグインが致命的エラーを引き起こした際には、ユーザーがサイトからロックアウトされないように、WordPress 5.2は、[致命的エラー・ハンドラを導入](https://make.wordpress.org/core/2019/04/16/fatal-error-recovery-mode-in-5-2/) しました。これは製品/本番サイトでは、すばらしい機能です。しかし、開発においては問題となる可能性があり、エラーを完全に診断できなくなります。

<!-- 
For this reason, in development, you should disable this to make sure things are broken until you can fix them. Define this constant in your `wp-config.php` file:
 -->

このため、開発段階では、修正できるまでは、壊れていることを明確にするために、この定数を無効にしておく必要があります。あなたの `wp-config.php` ファイルでこの定数を定義します:

```php
define( 'WP_DISABLE_FATAL_ERROR_HANDLER', true );
```

<!-- 
### WP\_DEBUG\_DISPLAY
 -->

### `WP_DEBUG_DISPLAY`

<!-- 
`WP_DEBUG_DISPLAY` is used to control whether debug messages display within the HTML of your WordPress site. By default, when `WP_DEBUG` is enabled, debugging messages will be shown on the screen. So, you can safely not define `WP_DEBUG_DISPLAY` during development.
 -->

`WP_DEBUG_DISPLAY` は、あなたの WordPress サイトの HTML 内にデバグ・メッセージを表示するかどうかを制御するために使用されます。デフォルトでは、`WP_DEBUG` を有効にすると、デバグ・メッセージが画面に表示されます。そのため、開発中は `WP_DEBUG_DISPLAY` を定義しないほうが安全です。

<!-- 
If you want to disable on-screen debugging messages, you can set `WP_DEBUG_DISPLAY` to `false` in your  `wp-config.php` file:
 -->

画面上のデバグ・メッセージを無効にしたい場合は、あなたの  `wp-config.php` ファイルで `WP_DEBUG_DISPLAY` を `false` に設定できます:

```php
define( 'WP_DEBUG_DISPLAY', false );
```

<!-- 
### WP\_DEBUG\_LOG
 -->

### `WP_DEBUG_LOG`

<!-- 
The `WP_DEBUG_LOG` constant is an optional feature that you can set to log errors to a `debug.log` file in your site’s `/wp-content` directory. By default, this is disabled.
 -->

`WP_DEBUG_LOG` 定数は、あなたのサイトの `/wp-content` ディレクトリにある `debug.log` ファイルにエラーを記録するように設定できる、任意機能です。デフォルトでは、無効になっています。

<!-- 
Generally, if you turn off on-screen debugging messages via `WP_DEBUG_DISPLAY`, then you will want to opt for storing these messages in the debug log.
 -->

一般的に、`WP_DEBUG_DISPLAY` 経由でオンスクリーン・デバグ・メッセージをオフにした際は、これらのメッセージをデバグログに保存することを選択したほうが良いでしょう。

<!-- 
To enable logging, define the `WP_DEBUG_LOG` constant as `true` in your `wp-config.php` file:
 -->

ロギングを有効にするには、あなたの `wp-config.php` ファイルで `WP_DEBUG_LOG` 定数を `true` と定義します:

```php
define( 'WP_DEBUG_LOG', true );
```

<!-- 
## Plugins
 -->

## プラグイン

<!-- 
There are several plugins that are helpful when debugging your theme. Each is hosted in the WordPress Plugin Directory:
 -->

あなたのテーマをデバグする際には、役立つプラグインがいくつかあります。各々は、「WordPress プラグイン・ディレクトリ」でホストされています:

<!-- 
*   [**Debug Bar**](https://wordpress.org/plugins/debug-bar/)**:** Provides a central location for debugging in your WordPress toolbar.
*   [**Query Monitor**](https://wordpress.org/plugins/query-monitor/)**:** Enables debugging of database queries, PHP errors, hooks and actions, block editor blocks, enqueued scripts and stylesheets, HTTP API calls, and more.
*   [**Log Deprecated Notices**](https://wordpress.org/plugins/log-deprecated-notices/)**:** Logs incorrect and deprecated function and file usages in your theme.
 -->

*   [**Debug Bar**](https://wordpress.org/plugins/debug-bar/)**:** あなたの WordPress ツールバーに、デバグ用の中心的な場所を提供します。
*   [**Query Monitor**](https://wordpress.org/plugins/query-monitor/)**:** データベース・クエリー、PHP エラー、フックとアクション、「ブロック・エディター」ブロック、エンキューされたスクリプトとスタイルシート、HTTP API コールなどのデバグを可能にします。
*   [**Log Deprecated Notices**](https://wordpress.org/plugins/log-deprecated-notices/)**:** あなたのテーマの、不正確で非推奨の関数やファイルの使用状況を、ログに記録します。