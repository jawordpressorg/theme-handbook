<!-- 
# Main Stylesheet (style.css)
 -->

# メイン・スタイルシート (style.css)

<!-- 
As described in [Theme Structure](https://developer.wordpress.org/themes/core-concepts/theme-structure/), WordPress requires that all themes include a `style.css` file. Its most important function is to “register” the theme with WordPress through configuration data at the top of the file. Many themes also use it to serve CSS to the front-end (and even the editor).
 -->

[テーマ構造](https://developer.wordpress.org/themes/core-concepts/theme-structure/) で説明したように、WordPress ではすべてのテーマに `style.css` ファイルを含める必要があります。その最も重要な機能は、ファイルの上部にある設定データを通じて、WordPress にテーマを「登録」することです。多くのテーマでは、フロントエンド (さらにはエディター) に CSS を提供するためにも、このファイルを使用しています。

<!-- 
In this document, you will learn how to configure your theme data via the `style.css` file header.
 -->

このドキュメントでは、`style.css` ファイルのヘッダーを使用してテーマデータを設定する方法について説明します。

<!-- 
## File Header
 -->

## ファイル・ヘッダー

<!-- 
The `style.css` file header is used to configure data about the theme. WordPress uses this information to determine how some features work and displays some of this data under the **Appearance > Themes** screen for users.
 -->

`style.css` ファイル・ヘッダーは、テーマに関するデータを設定するために使用されます。WordPress はこの情報を使用して、一部の機能の動作を決定し、そのデータの一部を **外観 > テーマ** 画面以下で、ユーザーに対して表示します。

<!-- 
Here is a look at what the theme details overlay looks like for the default Twenty Twenty-Three theme:
 -->

以下は、デフォルトの Twenty Twenty-Three テーマの「テーマ詳細」オーバーレイの表示例です:

<!-- 
[![WordPress themes screen with the Twenty Twenty-Three modal overlay over the screen. It shows the theme screenshot, description, and metadata.](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-theme-details.jpg?resize=2048%2C1002&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-theme-details.jpg?ssl=1)
 -->

[![WordPressのテーマ画面に、Twenty Twenty-Three のモーダル・オーバーレイが表示されている。テーマのスクリーンショット、説明、メタデータが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-theme-details.jpg?resize=2048%2C1002&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-theme-details.jpg?ssl=1)

<!-- 
Most of that information is pulled directly from the `style.css` file header. It is one of the most vital parts of creating a WordPress theme.
 -->

その情報のほとんどは、`style.css` ファイルのヘッダーから直接取得されています。これは、WordPress テーマを制作する際に、最も重要な要素のひとつです。

<!-- 
When determining which themes are available to activate, WordPress searches through each folder under `/wp-content/themes`, looking for a `style.css` file. If one is found, it pulls the first 8kb of data from the file and determines if there is a file header with standard fields defined.
 -->

有効化できるテーマを決定する際、WordPress は `/wp-content/themes` 以下の各フォルダーを調べて、`style.css` ファイルを探します。ファイルが見つかった場合、そのファイルから最初の8kb のデータを取得し、標準フィールドが定義されたファイルヘッダーがあるかどうかを判断します。

<!-- 
In themes, this is merely a CSS comment block with some standard keys and values defined.
 -->

テーマでは、これは単に CSS のコメント・ブロックであり、いくつかの標準的なキーと値が定義されています。

<!-- 
Suppose you were creating a theme with the folder name of `fabled-sunset`. WordPress would look for your theme’s `style.css` in the following location:
 -->

仮に、フォルダー名 `fabled-sunset` のテーマを制作しているとしましょう。WordPress は、以下の場所であなたのテーマの `style.css` を探します:

<!-- 
*   `wp-content/`
    *   `themes/`
        *   `fabled-sunset/`
            *   `style.css`
 -->

*   `wp-content/`
    *   `themes/`
        *   `fabled-sunset/`
            *   `style.css`

<!-- 
For WordPress to recognize your theme, you would at least need the `Theme Name` field defined at the top of `style.css` like so:
 -->

WordPress があなたのテーマを認識するためには、少なくとも `style.css` の最初にある、`Theme Name` フィールドを次のように定義する必要があります:

<!-- 
```css
/**
 * Theme Name: Fabled Sunset
 */
```
 -->

```css
/**
 * Theme Name: Fabled Sunset
 */
```

<!-- 
This is the minimum required header field for a valid theme. Of course, you’ll want to add much more information about your theme.
 -->

これは、有効なテーマに必要な、最小限のヘッダー項目です。もちろん、あなたのテーマに関するさらに多くの情報を追加したいでしょう。

<!-- 
### Header fields
 -->

### ヘッダー項目

<!-- 
There are many supported fields, and you will likely use most of them in your themes. Here is a quick look at a theme’s `style.css` file header with each of the fields configured:
 -->

サポートされている項目は数多くあり、そのほとんどをあなたのテーマで利用するでしょう。以下は、各項目が設定された、テーマの `style.css` ファイルヘッダーの簡単な例です:

<!-- 
```css
/**
 * Theme Name:        Fabled Sunset
 * Theme URI:         https://example.com/fabled-sunset
 * Description:       Custom theme description...
 * Version:           1.0.0
 * Author:            Your Name
 * Author URI:        https://example.com
 * Tags:              block-patterns, full-site-editing
 * Text Domain:       fabled-sunset
 * Domain Path:       /assets/lang
 * Tested up to:      6.4
 * Requires at least: 6.2
 * Requires PHP:      7.4
 * License:           GNU General Public License v2.0 or later
 * License URI:       https://www.gnu.org/licenses/gpl-2.0.html
 */
```
 -->

```css
/**
 * Theme Name:        Fabled Sunset
 * Theme URI:         https://example.com/fabled-sunset
 * Description:       カスタム・テーマの説明…
 * Version:           1.0.0
 * Author:            あなたの名前
 * Author URI:        https://example.com
 * Tags:              block-patterns, full-site-editing
 * Text Domain:       fabled-sunset
 * Domain Path:       /assets/lang
 * Tested up to:      6.4
 * Requires at least: 6.2
 * Requires PHP:      7.4
 * License:           GNU General Public License v2.0 or later
 * License URI:       https://www.gnu.org/licenses/gpl-2.0.html
 */
```

<!-- 
The following list outlines what each of these fields does.
 -->

以下のリストは、これらの各項目がどのような役割を果たすかを説明しています。

<!-- 
While the `Theme Name` is the only field required to work with WordPress, you must also include some other fields when submitting a theme to the WordPress theme directory. These fields are marked with **\*** below.
 -->

WordPress で動作するには `Theme Name` 項目のみが必要ですが、WordPress テーマ・ディレクトリにテーマを提出する際には、その他の項目も入力する必要があります。これらの項目は、以下で **\*** とマークされています。

<!-- 
*   **Theme Name\*:** A unique name for your theme.
*   **Theme URI:** The URL of a public web page where users can find more information about the theme.
*   **Description\*:** A description of the theme, which will be displayed when viewing a theme’s details in the WordPress admin and other places. It is also used for themes submitted to the WordPress theme directory.
*   **Version\*:** The version of the theme, written in `X.X` or `X.X.X` format.
*   **Author\*:**  Your name or the name of the organization who developed the theme. For themes submitted to the theme directory, it is recommended to use the WordPress.org username.
*   **Author URI:** The URL of the individual or organization who created the theme.
*   **Tags:** A comma-separated list of features the theme supports. The Theme Review Handbook has a [list of valid tags](https://make.wordpress.org/themes/handbook/review/required/theme-tags/) for submission to the theme directory, but third-party sites may use a different system.
*   **Text Domain\*:** The string used for the textdomain for translations.
*   **Domain Path:** A relative path to where theme translations are stored. WordPress uses this field when the theme is disabled to detect translations. Defaults to `/languages`.
*   **Tested up to\*:** The last WordPress version the theme has been tested up to, written in `X.X` format (e.g., `6.`4, `6.2.1`, etc.).
*   **Requires at least\*:** The oldest WordPress version the theme will work with, written in `X.X` format (e.g., `6.3`, `6.2.1`, etc.).
*   **Requires PHP\*:** The oldest PHP version the theme will work with, written in `X.X` format (e.g., `8.0`, `7.4`, etc.).
*   **License\*:** The license for the theme.
*   **License URI\*:** The URL of the theme’s license.
 -->

*   **Theme Name\*:** あなたのテーマ固有の名前です。
*   **Theme URI:** ユーザーがテーマに関する詳細情報を見ることができる、公開 Web ページの URL です。
*   **Description\*:** WordPress 管理画面やその他の場所で、テーマの詳細を表示する際に表示される、テーマの説明文です。WordPress テーマ・ディレクトリに提出されるテーマにも使用されます。
*   **Version\*:** `X.X` または `X.X.X` フォーマットで記述された、テーマのバージョンです。
*   **Author\*:** テーマを開発した、あなた個人または組織の名前です。テーマ・ディレクトリに提出するテーマの場合は、WordPress.org のユーザー名を使用することをおすすめします。
*   **Author URI:** テーマを制作した個人または組織の URL です。
*   **Tags:** テーマがサポートする機能の、カンマ区切りリストです。テーマレビュー・ハンドブックには、テーマ・ディレクトリへの提出用の [有効なタグのリスト](https://make.wordpress.org/themes/handbook/review/required/theme-tags/) がありますが、サードパーティのサイトでは異なるシステムを使用する場合があります。
*   **Text Domain\*:** 翻訳用テキストドメインに使用される、文字列です。
*   **Domain Path:** テーマの翻訳が保存されている場所への相対パスです。WordPress は、テーマが無効化されている場合に、この項目を使用して翻訳を検出します。デフォルトは `/languages` です。
*   **Tested up to\*:** `X.X` フォーマット (例: `6.4`、`6.2.1` など) で記述された、テーマがテストされた最新の WordPress バージョンです。
*   **Requires at least\*:** `X.X` フォーマット (例: `6.3`、`6.2.1` など) で記述された、テーマが動作する最古の WordPress バージョンです。
*   **Requires PHP\*:** `X.X` フォーマット (例: `8.0`、`7.4` など) で記述された、テーマが動作する最古の PHP バージョンです。
*   **License\*:** テーマのライセンスです。
*   **License URI\*:** テーマのライセンスの URL です。

<!-- 
### Child theme header fields
 -->

### 子テーマのヘッダー項目

<!-- 
When building a child theme, there is one additional supported field: **Template**. This is used to designate the parent theme’s folder.
 -->

子テーマを構築する際、追加で利用可能な項目が1つあります: **Template**。これは親テーマのフォルダーを指定するために使用されます。

<!-- 
If the fictional “Fabled Sunset” theme listed above was the parent of your child theme named “Grand Sunrise,” your `style.css` header fields would look similar to this:
 -->

あなたの子テーマ「Grand Sunrise」の親テーマが、上記の架空の「Fabled Sunset」テーマである場合、あなたの `style.css` ヘッダー項目は、次のようなものになります:

<!-- 
```css
/**
 * Theme Name: Grand Sunrise
 * Template:   fabled-sunset
 * ...other header fields
 */
```
 -->

```css
/**
 * Theme Name: Grand Sunrise
 * Template:   fabled-sunset
 * …その他のヘッダー項目
 */
```

<!-- 
The `Template` field must match the parent theme’s folder name exactly (relative to the `wp-content/themes` directory) for this to work. Otherwise, WordPress will not be able to appropriately match them.
 -->

この機能が動作するには、`Template` 項目が親テーマのフォルダー名 ( `wp-content/themes` ディレクトリを基準) と完全に一致している必要があります。一致していない場合、WordPress はそれらを適切に照合できません。

<!-- 
You can [learn more about child themes](https://developer.wordpress.org/themes/advanced-topics/child-themes/) in the Advanced Topics chapter.
 -->

「高度なトピック」章で、[子テーマについて詳しく学ぶ](https://developer.wordpress.org/themes/advanced-topics/child-themes/) ことができます。

<!-- 
### Custom header fields
 -->

### カスタム・ヘッダー項目

<!-- 
Some third-party marketplaces or systems may also make use of custom header fields. These are not officially supported by WordPress, but they are definitely allowed and should not negatively impact how the theme works within WordPress.
 -->

一部のサードパーティのマーケットプレイスやシステムも、カスタム・ヘッダー項目を利用している場合があります。これらは WordPress によって公式にサポートされているものではありませんが、使用は問題なく、WordPress でのテーマの動作に悪影響を与えることもありません。

<!-- 
## Custom CSS
 -->

## カスタム CSS

<!-- 
The `style.css` file is not merely a configuration file. You can also use it to write custom CSS code to alter the design of your theme, assuming the file is properly loaded.
 -->

`style.css` ファイルは、単なる設定ファイルではありません。このファイルが適切に読み込まれていれば、テーマのデザインを変更するためのカスタム CSS コードも記述できます。

<!-- 
With block themes, most or all of the design is ideally handled through the `theme.json` file, which you will learn about in the [Global Settings and Styles](https://developer.wordpress.org/themes/core-concepts/global-settings-and-styles/) documentation.
 -->

ブロックテーマでは、デザインのほとんどまたはすべては、理想的には、[グローバル設定とスタイル](https://developer.wordpress.org/themes/core-concepts/global-settings-and-styles/) ドキュメントで説明する、`theme.json` ファイルを通じて管理されます。

<!-- 
But there are times when you will want or need to add custom CSS. You can learn more about this in the [Including Assets](https://developer.wordpress.org/themes/core-concepts/including-assets/) documentation.
 -->

ただし、場合によっては、カスタム CSS を追加したい、または追加する必要がある場合があります。[アセットの読み込み](https://developer.wordpress.org/themes/core-concepts/including-assets/) ドキュメントで、これについて詳しく学ぶことができます。