<!-- 
# Internationalization
 -->

# 国際化

<!-- 
Internationalization is the process of developing your theme in such a way that its custom text can be translated into other languages. The term is often abbreviated as “i18n” because there are 18 letters between the “i” and “n,” the first and last letters.
 -->

国際化とは、テーマのカスタムテキストを他の言語に翻訳できるようにする、テーマ開発におけるプロセスのことです。この用語はしばしば「i18n」と略されますが、これは「i」と「n」、つまり最初と最後の文字の間に18文字があるためです。

<!-- 
In this article, you will learn how to internationalize your WordPress themes and why it is important. 
 -->

本稿では、あなたの WordPress テーマを国際化する方法と、それがなぜ重要なのかを学びます。

<!-- 
## Why internationalization is important
 -->

## 国際化が重要な理由

<!-- 
WordPress is used all over the world, in countries where your native language is not used. The strings in the WordPress themes need to be coded in a special way so that they can be easily translated into other languages. 
 -->

WordPress は、世界中で、あなたの母国語が使われていない国でも、使われています。WordPress テーマ内の文字列は、他の言語に簡単に翻訳できるように、特別な方法で記述する必要があります。

<!-- 
Even if you yourself do not know multiple languages, internationalization leaves the door open for translators to localize the text. Localization is the process of taking internationalized text and translating it for a specific language and locale. It is often abbreviated as “l10n.”
 -->

たとえあなた自身が多言語を知らなくても、国際化は、翻訳者がテキストをローカライズするための扉を開いておきます。ローカライゼーションとは、国際化されたテキストを特定の言語やロケール向けに翻訳するプロセスのことです。「l10n」と略記されることが多いです。

<!-- 
WordPress has a built-in translation system that allows localizing a theme without having to modify the source code of the theme itself. This is important because it means that users can keep up with theme updates while using their preferred translation.
 -->

WordPress には組込み翻訳システムがあり、テーマ自体のソースコードを変更することなくテーマをローカライズできます。これは、ユーザーが好みの翻訳を使用しながら、テーマのアップデートに追いつくことができることを意味するので、重要です。

<!-- 
You can certainly build a WordPress theme without internationalization, particularly if it’s for a site that you know will never be translated. But in most cases, it is considered standard practice to internationalize all of your theme’s text. For one, it means that it can be used by people in other languages, giving you a wider audience. And it [is also a requirement](https://make.wordpress.org/themes/handbook/review/required/#8-language-internationalization) when submitting a theme to the official [Theme Directory](https://wordpress.org/themes/).
 -->

翻訳されることがないとわかっているサイトのためであれば、特に国際化せずに WordPress テーマを構築できます。しかし、ほとんどの場合、あなたのテーマのすべてのテキストを国際化することが標準的な慣行と考えられています。ひとつは、他の言語の人たちにも使ってもらえるということで、より多くの人たちに使ってもらえるということです。また、公式 [テーマ・ディレクトリー](https://wordpress.org/themes/) にテーマを登録する際にも、[必須条件](https://make.wordpress.org/themes/handbook/review/required/#8-language-internationalization) となります。

<!-- 
## How to internationalize your theme
 -->

## あなたのテーマを国際化する方法

<!-- 
### Getting your text domain
 -->

### あなたのテキスト・ドメインの取得

<!-- 
The text domain is a unique identifier, allowing WordPress to distinguish between all of the loaded translations. That means that you need something unique for your theme so that WordPress will recognize translations that belong to it.
 -->

テキスト・ドメインは、WordPress がすべてのロードされた翻訳を区別できるようにする、一意の識別子です。つまり、WordPress がそのテーマに属する翻訳を認識できるように、あなたのテーマ特有の何かが必要なのです。

<!-- 
The text domain is used in three different places in your theme:
 -->

テキスト・ドメインは、あなたのテーマの3つの異なる場所で使用されます:

<!-- 
*   In the `style.css` file header.
*   As an argument in internationalization functions.
*   As an argument when loading translations (optional for themes submitted to the WordPress [Theme Directory](https://wordpress.org/themes/)).
 -->

*   `style.css` ファイル・ヘッダー内。
*   国際化関数の引数として。
*   翻訳をロードする際の引数として (WordPress [テーマ・ディレクトリー](https://wordpress.org/themes/) に登録されたテーマの場合は任意)。

<!-- 
Your theme’s text domain should always match your theme slug, as described in the [Reading this handbook](https://developer.wordpress.org/themes/getting-started/reading-this-handbook/#how-to-read-code-examples) documentation. This is a central component in making sure your theme is ready for translation.
 -->

[このハンドブックを読む](https://developer.wordpress.org/themes/getting-started/reading-this-handbook/#how-to-read-code-examples) ドキュメントで説明されているように、あなたのテーマのテキスト・ドメインは、常にあなたのテーマのスラッグと一致する必要があります。これは、あなたのテーマが翻訳に対応していることを確認するための中心的な要素です。

<!-- 
The *de facto* standard (and requirement if submitting your theme to the WordPress Theme Directory) is to use the [kebab-case](https://developer.mozilla.org/en-US/docs/Glossary/Kebab_case) version of your theme name. This means that it should:
 -->

*事実上の* 標準 (そして WordPress テーマ・ディレクトリに、あなたのテーマを登録する場合の必須条件) は、あなたのテーマ名の [ケバブ・ケース](https://developer.mozilla.org/en-US/docs/Glossary/Kebab_case) 版を使用することです。つまり、こうあるべきということです:

<!-- 
*   Use all lowercase letters.
*   Have no spaces.
*   Hyphenate when there are multiple words.
 -->

*   すべて小文字を使用しましょう。
*   空白は入れないでください。
*   複数の単語があるときは、ハイフンでつないでください。

<!-- 
So if your theme’s name is `Fabled Sunset`, your text domain should be `fabled-sunset`.
 -->

つまり、あなたのテーマ名が `Fabled Sunset` であれば、あなたのテキスト・ドメインは `fabled-sunset` でなくてはなりません。

<!-- 
### Defining your text domain
 -->

### あなたのテキスト・ドメインの定義

<!-- 
As described in the [Main Stylesheet](https://developer.wordpress.org/themes/core-concepts/main-stylesheet/) documentation, you can configure several important pieces of metadata about your theme via the `style.css` file header. In particular, there are two meta values you can define related to internationalization:
 -->

[メイン・スタイルシート](https://developer.wordpress.org/themes/core-concepts/main-stylesheet/) ドキュメントで説明されているように、`style.css` ファイル・ヘッダー経由で、あなたのテーマに関するいくつかの重要なメタデータを設定できます。特に、国際化に関連する2つのメタ値を定義できます:

<!-- 
*   **Text Domain:** The string used for the text domain for translations.
*   **Domain Path:** A relative path to where theme translations are stored. WordPress uses this field when the theme is disabled to detect translations. Defaults to `/languages` if not defined.
 -->

*   **`Text Domain`:** 翻訳用のテキスト・ドメインに使用される文字列です。
*   **`Domain Path`:** テーマの翻訳が保存されている場所への相対パスです。テーマが無効の場合、WordPress は翻訳を検出するために、このフィールドを使用します。定義されていない場合、デフォルトは `/languages` です。

<!-- 
For translations to work correctly, you must at least define the `Text Domain` field, which should be your theme’s slug.
 -->

翻訳が正しく機能するためには、あなたのテーマのスラッグとなる `Text Domain` フィールドを、少なくとも定義しなくてはなりません。

<!-- 
Let’s imagine your theme name is “Fabled Sunset” and you want translations stored in your theme’s `/assets/lang` folder. Your theme’s `style.css` should define these fields like so:
 -->

あなたのテーマ名が「Fabled Sunset」で、あなたのテーマの `/assets/lang` フォルダーに翻訳を保存したいとします。あなたのテーマの `style.css` は、これらのフィールドを次のように定義する必要があります:

```css
/**
 * Theme Name:        Fabled Sunset
 * ...
 * Text Domain:       fabled-sunset
 * Domain Path:       /assets/lang
 * ...
 */
```

<!-- 
It’s important to add this metadata to your `style.css` file because WordPress uses it even when the theme is not enabled (for example, when viewing all themes from the **Appearance > Themes** screen in the admin).
 -->

WordPress はテーマが有効になっていないときでも、このメタデータを使用するので、あなたの `style.css` ファイルにこのメタデータを追加することが重要です (たとえば、管理画面の **外観 > テーマ** 画面からすべてのテーマを表示する場合)。

<!-- 
### Wrapping text with internationalization functions
 -->

### 国際化関数による、テキストのラッピング

<!-- 
For text in your theme to be easily translated in your theme, it must be wrapped in an internationalization function instead of hardcoded. The available [internationalization functions](https://developer.wordpress.org/apis/internationalization/internationalization-functions/) are listed in the Common APIs handbook.
 -->

あなたのテーマのテキストを簡単に翻訳するためには、ハードコードする代わりに国際化関数でラップする必要があります。利用可能な [国際化関数](https://developer.wordpress.org/apis/internationalization/internationalization-functions/) は共通 API ハンドブックに記載されています。

<!-- 
In a typical HTML-based webpage, you would add plain text strings. For example, take a look at this example heading:
 -->

典型的な HTML ベースの Web ページでは、プレーンテキスト文字列を追加します。たとえば、この見出しの例を見てください:

```markup
<h2>Latest Posts</h2>
```

<!-- 
Because it is merely plain text, it cannot be translated into other languages without directly modifying the code.
 -->

単なるプレーンテキストですので、コードを直接修正しなければ他の言語に翻訳できません。

<!-- 
Let’s wrap that text in the [`_e()`](https://developer.wordpress.org/reference/functions/_e/) internationalization function, which tells WordPress that the text inside should be available for translation and echoed (printed to the screen):
 -->

WordPress に内側のテキストが翻訳可能であることと、エコー (画面に表示) されることを伝えるために、このテキストを [`_e()`](https://developer.wordpress.org/reference/functions/_e/) 国際化関数でラップしましょう:

```php
<h2><?php _e( 'Latest Posts', 'themeslug' ); ?></h2>
```

<!-- 
Now users can add translations for your theme without touching the code.
 -->

これで、ユーザーはコードに触れることなく、あなたのテーマに翻訳を追加できます。

<!-- 
As you may have noticed, the `_e()` function accepted a second parameter of `themeslug`. This should be replaced with your text domain.
 -->

お気付きかもしれませんが、`_e()` 関数は `themeslug` という2番目のパラメータを受け取っています。これは、あなたのテキスト・ドメインに置き換えてください。

<!-- 
There are many other internationalization functions that you will use, and you will learn about them later. For now, the idea is to introduce you to the basic concept.
 -->

あなたが使うことになる国際化関数は他にもたくさんありますが、それらについては後で学びます。今は、基本的なコンセプトを紹介するのが主旨です。

<!-- 
Because internationalized text is technically a PHP variable, it means that it can be exploited and become a security vulnerability. You should always use the [translate-and-escape functions](https://developer.wordpress.org/apis/internationalization/internationalization-functions/#translate-escape-functions) when possible. Otherwise, be sure to wrap them in an escaping function when outputting, as described in the [Security](https://developer.wordpress.org/themes/advanced-topics/security/) documentation.
 -->

国際化されたテキストは、技術的には PHP の変数ですので、これは悪用され、セキュリティの脆弱性になる可能性があります。可能であれば、常に [翻訳エスケープ関数](https://developer.wordpress.org/apis/internationalization/internationalization-functions/#translate-escape-functions) を使うべきです。そうでない場合は、[セキュリティ](https://developer.wordpress.org/themes/advanced-topics/security/) ドキュメントで説明されているように、出力する際には、必ずエスケープ関数でラップしてください。

<!-- 
### Loading translations
 -->

### 翻訳のロード

<!-- 
For themes hosted in the WordPress [Theme Directory](https://wordpress.org/themes/), you do not need to load translations. WordPress automatically checks the `wp-content/languages` directory in a user’s install and will download translations from the [Translating WordPress](https://translate.wordpress.org/) site. All translations can be handled there, and you don’t have to worry about storing or loading them from your theme.
 -->

WordPress [テーマ・ディレクトリー](https://wordpress.org/themes/) でホストされているテーマの場合、翻訳をロードする必要はありません。WordPress はインストールされたユーザーの `wp-content/languages` ディレクトリを自動的にチェックし、[WordPress の翻訳](https://translate.wordpress.org/) サイトから翻訳をダウンロードします。すべての翻訳はそこで処理でき、あなたのテーマからの保存やロードについて心配する必要もありません。

<!-- 
Translation in WordPress are saved in `.po` (human readable) and `.mo` (machine readable) files. The `.mo` files are the ones actually used by WordPress. 
 -->

WordPress における翻訳は、`.po` (人間可読) ファイルと `.mo` (機械可読) ファイルに保存されます。WordPress で実際に使用されるのは `.mo` ファイルです。

<!-- 
WordPress will look in two places for translation files based on the user’s locale defined for the site:
 -->

WordPress は、サイト用に定義されたユーザーのロケールにもとづいて、翻訳ファイル用に2つの場所を探します:

<!-- 
*   `wp-content/themes/your-theme/{domain-path}/{locale}.mo`
*   `wp-content/languages/themes/{textdomain}-{locale}.mo`
 -->

*   `wp-content/themes/あなたのテーマ/{ドメイン・パス}/{ロケール}.mo`
*   `wp-content/languages/themes/{テキスト・ドメイン}-{ロケール}.mo`

<!-- 
To load translation files from your theme, you must use one of two functions:
 -->

あなたのテーマから翻訳ファイルをロードするには、2つの関数のいずれかを使用する必要があります:

<!-- 
*   [`load_theme_textdomain()`](https://developer.wordpress.org/reference/functions/load_theme_textdomain/)
*   [`load_child_theme_textdomain()`](https://developer.wordpress.org/reference/functions/load_child_theme_textdomain/) (if building a [child theme](https://developer.wordpress.org/themes/advanced-topics/child-themes/))
 -->

*   [`load_theme_textdomain()`](https://developer.wordpress.org/reference/functions/load_theme_textdomain/)
*   [`load_child_theme_textdomain()`](https://developer.wordpress.org/reference/functions/load_child_theme_textdomain/) ([子テーマ](https://developer.wordpress.org/themes/advanced-topics/child-themes/) を構築する場合)

<!-- 
Let’s take a look at the `load_theme_textdomain()` function signature (it’s the same for both functions):
 -->

`load_theme_textdomain()` 関数のシグネチャを見てみましょう (どちらの関数も同じ):

```php
load_theme_textdomain(
	string $domain, 
	string|false $path = false 
): bool
```

<!-- 
The function accepts two parameters:
 -->

この関数は、2つのパラメータを受け取ります:

<!-- 
*   **`$domain`:** This should be the text domain for your theme as defined in `style.css`.
*   **`$path`:** This must be a full directory path to the location of translations in your theme. If left undefined, WordPress will fall back to your theme’s root folder.
 -->

*   **`$domain`:** これは、`style.css` 内で定義された、あなたのテーマのテキスト・ドメインでなくてはなりません。
*   **`$path`:** これは、あなたのテーマの翻訳の場所への、完全なディレクトリ・パスでなくてはなりません。未定義のままだと、WordPress はあなたのテーマのルート・フォルダーにフォールバックします。

<!-- 
Using the same example “Fabled Sunset” theme described earlier with translations stored in the `/assets/lang` folder, let’s try loading translations from the theme.
 -->

`/assets/lang` フォルダーに翻訳が保存されている、先ほどと同じ例の「Fabled Sunset」テーマを使って、テーマから翻訳をロードしてみましょう。

<!-- 
Add this code to your theme’s `functions.php` file:
 -->

このコードをあなたのテーマの `functions.php` ファイルに追加します:

```php
add_action( 'after_setup_theme', 'themeslug_load_textdomain' );

function themeslug_load_textdomain() {
	load_theme_textdomain(
		'fabled-sunset',
		get_parent_theme_file_path( 'assets/lang' )
	);
}
```

<!-- 
The above call to `load_theme_textdomain()` was executed on the [`after_setup_theme`](https://developer.wordpress.org/reference/hooks/after_setup_theme/) action hook, which fires immediately after the theme’s `functions.php` is loaded.
 -->

`load_theme_textdomain()` への上記コールは、テーマの `functions.php` がロードされた直後に実行される [`after_setup_theme`](https://developer.wordpress.org/reference/hooks/after_setup_theme/) アクションフックで実施されます。

<!-- 
If you were building a child theme, your `functions.php` code would instead look like this:
 -->

子テーマを構築する場合、あなたの `functions.php` コードは、次のようになります:

```php
add_action( 'after_setup_theme', 'themeslug_load_textdomain' );

function themeslug_load_textdomain() {
	load_child_theme_textdomain(
		'fabled-sunset',
		get_theme_file_path( 'assets/lang' )
	);
}
```

<!-- 
## Resources
 -->

## リソース

<!-- 
Internationalization is a large topic and is covered in full in the [Internationalization chapter](https://developer.wordpress.org/apis/internationalization/) of the Common APIs handbook. What you learn there will apply to both theme and plugin development.
 -->

国際化は大きなトピックであり、共通 API ハンドブックの [国際化の章](https://developer.wordpress.org/apis/internationalization/) で完全にカバーされています。そこで学んだことは、テーマ開発にもプラグイン開発にも適用できるでしょう。

<!-- 
WordPress has many [internationalization functions](https://developer.wordpress.org/apis/internationalization/internationalization-functions/) for you to use when wrapping text. Which one to use will be context-specific. Take the time to study each function so that you will know when to use it. The [Internationalization Guidelines](https://developer.wordpress.org/apis/internationalization/internationalization-guidelines/) will set you down the correct path.
 -->

テキストをラップする際、WordPress には使用可能な [国際化関数](https://developer.wordpress.org/apis/internationalization/internationalization-functions/) が多数用意されています。どれを使うかは文脈によって異なります。いつ使えばいいのか、それがわかるように、時間をかけて各機能を勉強しましょう。[国際化ガイドライン](https://developer.wordpress.org/apis/internationalization/internationalization-guidelines/) が正しい道を示してくれるでしょう。