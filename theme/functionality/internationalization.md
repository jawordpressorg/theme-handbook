<!-- 
# Internationalization
 -->

# 国際化

<!-- 
## What is internationalization?
 -->

## 国際化って ?

<!-- 
Internationalization is the process of developing your theme, so it can easily be translated into other languages. Internationalization is often abbreviated as `i18n` (because there are 18 letters between the letters i and n).
 -->

国際化とは、あなたのテーマを開発するプロセスであり、他の言語へ容易に翻訳できるようにします。国際化は、(i と n の間に18文字あるため) しばしば `i18n` と略されます。

<!-- 
## Why is internationalization important?
 -->

## なぜ国際化は、重要なの ?

<!-- 
WordPress is used all over the world, in countries where English is not the main language. The strings in the WordPress plugins need to be coded in a special way so that can be easily translated into other languages. As a developer, you may not be able to provide localizations for all your users; however, a translator can successfully localize the theme without needing to modify the source code itself.
 -->

WordPress は、英語が主要言語ではない国々を含む、世界中で利用されています。WordPress プラグイン内の文字列は、他の言語へ容易に翻訳できるよう、特別な方法でコーディングする必要があります。開発者として、すべてのあなたのユーザー向けにローカライズを提供できない場合もあるでしょう; しかし翻訳者は、ソースコード自体を変更することなく、テーマのローカライズを成功させることができます。

<!-- 
## How to internationalize your theme?
 -->

## あなたのテーマを国際化するには ?

<!-- 
For the text in the theme to be able to be translated easily the text should not be hardcoded in the theme but be passed as an argument through one of the localization functions in WordPress.
 -->

テーマ内のテキストを容易に翻訳可能にするためには、テキストはテーマにハードコードすべきではなく、WordPress の国際化関数を通じて引数として渡されるべきです。

<!-- 
The following example could not be translated unless the translator modified the source code which is not very efficient.
 -->

以下の例は、翻訳者がソースコードを変更しない限り翻訳できず、効率的とまでは言えません。

```php
<h1>Settings Page</h1>
```

<!-- 
By passing the string through a localization function it can it can be easily parsed to be translated.
 -->

文字列をローカライズ関数に通すことで、翻訳のために簡単に解析できます。

```php
<h1><?php _e( 'Settings Page' ); ?></h1>
```

<!-- 
WordPress uses [gettext](http://www.gnu.org/software/gettext/) libraries to be able to add the translations in PHP. In WordPress you should use the WordPress localization functions instead of the native PHP gettext-compliant translation functions.
 -->

WordPress は、PHP 内で翻訳を追加できるようにするため、[`gettext`](http://www.gnu.org/software/gettext/) ライブラリを使用しています。WordPress では、ネイティブの PHP gettext 準拠の翻訳関数ではなく、WordPress のローカライズ関数を使用する必要があります。

<!-- 
### Text Domain
 -->

### テキスト・ドメイン

<!-- 
The text domain is the second argument that is used in the internationalization functions. The text domain is a unique identifier, allowing WordPress to distinguish between all of the loaded translations. The text domain is only needed to be defined for themes and plugins.
 -->

テキスト・ドメインは、国際化関数で使用される2番目の引数です。テキスト・ドメインは、一意の識別子であり、ロードされたすべての翻訳を、WordPress が区別できるようにします。テキスト・ドメインは、テーマとプラグインに対してのみ、定義する必要があります。

<!-- 
Themes that are hosted on WordPress.org the text domain must match the slug of your theme URL (`wordpress.org/themes/<slug>`). This is needed so that the translations from [translate.wordpress.org](https://translate.wordpress.org/) work correctly.
 -->

WordPress.org でホストされているテーマでは、テキスト・ドメインは、あなたのテーマ URL のスラッグ (`wordpress.org/themes/<slug>`) と一致している必要があります。これは、[`translate.wordpress.org`](https://translate.wordpress.org/) からの翻訳が、正しく機能するために必要です。

<!-- 
The text domain name must use dashes and not underscores and be lowercase. For example, if the theme’s name `My Theme` is defined in the `style.css` or it is contained in a folder called `my-theme` the text domain should be `my-theme`.
 -->

テキスト・ドメイン名は、アンダースコアではなくダッシュを使用し、小文字で記述する必要があります。たとえば、テーマ名が `My Theme` として `style.css` で定義されている場合、または `my-theme` というフォルダーに含まれている場合、テキスト・ドメインは `my-theme` にする必要があります。

<!-- 
The text domain is used in three different places:
 -->

テキスト・ドメインは、3つの異なる場所で使用されます:

<!-- 
1.  In the `style.css` theme header
2.  As an argument in the localization functions
3.  As an argument when loading the translations using `load_theme_textdomain()` or  `load_child_theme_textdomain()`
 -->

1.  `style.css` テーマ・ヘッダー内
2.  ローカライズ関数内での、引数として
3.  `load_theme_textdomain()` または `load_child_theme_textdomain()` を使用して翻訳をロードする際の、引数として

<!-- 
#### style.css theme header
 -->

#### `style.css` テーマ・ヘッダー

<!-- 
The text domain is added to the `style.css` header so that the theme meta-data like the description can be translated even when the theme is not enabled. The text domain should be same as the one used when [loading the text domain](#loading-text-domain).
 -->

テキスト・ドメインは、`style.css` ヘッダーに追加されるため、テーマが有効化されていない場合でも、説明などのテーマ・メタデータが翻訳可能となります。テキスト・ドメインは、[テキスト・ドメインのロード](#loading-text-domain) 時に使用されるものと同一である必要があります。

<!-- 
**Example:**
 -->

**例:**

```php
/*
* Theme Name: My Theme
* Author: Theme Author
* Text Domain: my-theme
*/
```

<!-- 
##### Domain Path
 -->

##### ドメイン・パス

<!-- 
The domain path is needed when the translations are saved in a directory other than `languages` . This is so that WordPress knows where to find the translation when the theme is not activated. For example, if .mo files are located in the languages folder then Domain Path will be `/languages` and must be written with the first slash. Defaults to the `languages` folder in the theme.
 -->

翻訳が `languages` 以外のディレクトリに保存されている場合、ドメイン・パスが必要です。これは、テーマが有効化されていない状態で WordPress が翻訳ファイルの場所を特定できるようにするためです。たとえば、`.mo` ファイルが `languages` フォルダーにある場合、ドメイン・パスは `/languages` となり、スラッシュ始まりで記述する必要があります。デフォルトでは、テーマ内の `languages` フォルダーが使用されます。

<!-- 
**Example:**
 -->

**例:**

```php
/*
* Theme Name: My Theme
* Author: Theme Author
* Text Domain: my-theme
* Domain Path: /languages
*/
```

<!-- 
#### Add text domain to strings
 -->

#### 文字列にテキスト・ドメインの追加

<!-- 
The text domain should be added as an argument to all of the localization functions for the translations to work correctly.
 -->

翻訳が正しく機能するためには、テキスト・ドメインを、すべてのローカライズ関数の引数として追加する必要があります。

<!-- 
**Example 1**:
 -->

**例1**:

```php
__( 'Post' )
```

<!-- 
should become
 -->

は、以下のようにすべきです。

```php
__( 'Post', 'my-theme' )
```

<!-- 
**Example 2**:
 -->

**例2**:

```php
_e( 'Post' )
```

<!-- 
should become
 -->

は、以下のようにすべきです。

```php
_e( 'Post', 'my-theme' )
```

<!-- 
**Example 3**:
 -->

**例3**:

```php
_n( '%s post', '%s posts', $count )
```

<!-- 
should become
 -->

は、以下のようにすべきです。

```php
_n( '%s post', '%s posts', $count, 'my-theme' )
```

<!-- 
The text domain should be passed as a string to the localization functions instead of a variable. It allows parsing tools to differentiate between text domains. Example of what not to do:  
 -->

テキスト・ドメインは、変数ではなく、文字列としてローカライゼーション関数に渡す必要があります。これにより、解析ツールが、テキスト・ドメインを区別できます。以下の例は、避けるべきものです:  

```php
__( 'Translate me.' , $text_domain );
```

<!-- 
#### Loading Translations
 -->

#### 翻訳のロード

<!-- 
The translations in WordPress are saved in `.po` and `.mo` files which need to be loaded. They can be loaded by using the functions `[load_theme_textdomain()](https://developer.wordpress.org/reference/functions/load_theme_textdomain/)` or `[load_child_theme_textdomain()](https://developer.wordpress.org/reference/functions/load_child_theme_textdomain/)`. This loads `{locale}.mo` from your theme’s base directory or `{text-domain}-{locale}.mo` from the WordPress theme language folder in `/wp-content/languages/themes/`.
 -->

WordPress における翻訳は `.po` および `.mo` ファイルに保存され、ロードする必要があります。これらは、[`load_theme_textdomain()`](https://developer.wordpress.org/reference/functions/load_theme_textdomain/) または [`load_child_theme_textdomain()`](https://developer.wordpress.org/reference/functions/load_child_theme_textdomain/) 関数を使用して、ロードできます。これは、あなたのテーマのベース・ディレクトリから `{locale}.mo` を、または `/wp-content/languages/themes/` 内の WordPress テーマ言語フォルダーから `{text-domain}-{locale}.mo` を、ロードします。

<!-- 
As of version 4.6 WordPress automatically checks the language directory in `wp-content` for translations from [translate.wordpress.org](https://translate.wordpress.org/). This means that plugins that are translated via translate.wordpress.org do not require `load_plugin_textdomain()` anymore.  
If you don’t want to add a `load_plugin_textdomain()` call to your plugin you should set the `Requires at least:` field in your readme.txt to 4.6.  
 -->

v4.6以降、WordPress は [`translate.wordpress.org`](https://translate.wordpress.org/) からの翻訳を `wp-content` 内の言語ディレクトリで、自動的にチェックします。これは、`translate.wordpress.org` 経由で翻訳されたプラグインが、もはや `load_plugin_textdomain()` を必要としないことを意味します。
あなたのプラグインに `load_plugin_textdomain()` コールを追加したくない場合は、`readme.txt` 内の `Requires at least:` フィールドを `4.6` に設定してください。

<!-- 
To find out more about the different language and country codes, see [the list of languages](https://make.wordpress.org/polyglots/teams/ "https://codex.wordpress.org/WordPress_in_Your_Language").
 -->

さまざまな言語と国コードの詳細については、[言語のリスト](https://make.wordpress.org/polyglots/teams/ "https://codex.wordpress.org/WordPress_in_Your_Language") をご覧ください。

<!-- 
**Watch Out**
 -->

**くれぐれも注意**

<!-- 
*   Name your MO file as `{locale}.mo` (e.g. de\_DE.po & de\_DE.mo) if adding the translation to the theme folder.
*   Name your MO file as `{text-domain}-{locale}.mo` (e.g my-theme-de\_DE.po & my-theme-de\_DE.mo) if you are adding the translation to the WordPress theme language folder.
 -->

*   テーマ・フォルダーに翻訳を追加する場合、MO ファイルの名称は `{locale}.mo` の形式にします (たとえば `de_DE.po` と `de_DE.mo`)。
*   WordPress テーマ言語フォルダーに翻訳を追加する場合、MO ファイルの名称は `{text-domain}-{locale}.mo` の形式にします (たとえば `my-theme-de_DE.po` と `my-theme-de_DE.mo`)。

<!-- 
**Example:**
 -->

**例:**

```php
function my_theme_load_theme_textdomain() {
    load_theme_textdomain( 'my-theme', get_template_directory() . '/languages' );
}
add_action( 'after_setup_theme', 'my_theme_load_theme_textdomain' );
```

<!-- 
This function should ideally be run within the theme’s `function.php`.
 -->

本関数は、理想的には、テーマの `function.php` 内で実行されるべきです。

<!-- 
##### Language Packs
 -->

##### 言語パック

<!-- 
If you’re interested in language packs and how the import to [translate.wordpress.org](https://translate.wordpress.org/) is working, please read the [Meta Handbook page about Translations](https://make.wordpress.org/meta/handbook/documentation/translations/).
 -->

言語パックや [`translate.wordpress.org`](https://translate.wordpress.org/) へのインポートのしくみに興味がある場合は、[翻訳に関する、メタ・ハンドブックのページ](https://make.wordpress.org/meta/handbook/documentation/translations/) をご覧ください。

<!-- 
## Internationalizing your theme
 -->

## あなたのテーマの国際化

<!-- 
Now that your translations are loaded, you can start writing every string in your theme with Internationalization functions.
 -->

さて、あなたの翻訳がロードされたので、あなたのテーマ内のすべての文字列を、国際化関数を使って書き始めることができます。

<!-- 
Check the [Internationalization](https://developer.wordpress.org/apis/handbook/internationalization/) page on the [Common APIs Handbook](https://developer.wordpress.org/apis/) for more information and best practices.
 -->

詳細およびベスト・プラクティスについては、[共通 API ハンドブック](https://developer.wordpress.org/apis/) の、[国際化](https://developer.wordpress.org/apis/handbook/internationalization/) ページをチェックしてください。