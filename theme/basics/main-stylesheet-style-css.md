<!-- 
# Main Stylesheet (style.css)
 -->

# メイン・スタイルシート (style.css)

<!-- 
The style.css is a stylesheet (CSS) file required for every WordPress theme. It controls the presentation (visual design and layout) of the website pages.
 -->

style.css とは、すべての WordPress テーマに必要なスタイルシート (CSS) ファイルです。このファイルは、Web サイトの表示方法 (視覚的なデザインとレイアウト) を制御します。

<!-- 
## Location
 -->

## ファイルの場所

<!-- 
In order for WordPress to recognize the set of theme template files as a valid theme, the style.css file needs to be located in the root directory of your theme, not a subdirectory.
 -->

WordPress がテーマ・テンプレート・ファイル群を有効なテーマとして認識するためには、style.css ファイルは、サブディレクトリではなく、あなたのテーマのルートディレクトリに配置する必要があります。

<!-- 
For more detailed explanation on how to include the style.css file in a theme, see the “Stylesheets” section of [Enqueuing Scripts and Styles](https://developer.wordpress.org/themes/basics/including-css-javascript/#stylesheets).
 -->

テーマに style.css ファイルを含める方法の詳細な説明については、[スクリプトとスタイルのエンキュー](https://developer.wordpress.org/themes/basics/including-css-javascript/#stylesheets) の「スタイルシート」セクションをご覧ください。

<!-- 
## Basic Structure
 -->

## 基本構造

<!-- 
WordPress uses the header comment section of a style.css to display information about the theme in the Appearance (Themes) dashboard panel.
 -->

WordPress は、style.css のヘッダーコメント・セクションを使用して、「外観」(テーマ) ダッシュボードパネルに、テーマに関する情報を表示します。

<!-- 
### Example
 -->

### 例

<!-- 
Here is an example of the header part of style.css.
 -->

以下は、style.css のヘッダー部分の例です。

```css
/*
Theme Name: Twenty Twenty
Theme URI: https://wordpress.org/themes/twentytwenty/
Author: the WordPress team
Author URI: https://wordpress.org/
Description: Our default theme for 2020 is designed to take full advantage of the flexibility of the block editor. Organizations and businesses have the ability to create dynamic landing pages with endless layouts using the group and column blocks. The centered content column and fine-tuned typography also makes it perfect for traditional blogs. Complete editor styles give you a good idea of what your content will look like, even before you publish. You can give your site a personal touch by changing the background colors and the accent color in the Customizer. The colors of all elements on your site are automatically calculated based on the colors you pick, ensuring a high, accessible color contrast for your visitors.
Tags: blog, one-column, custom-background, custom-colors, custom-logo, custom-menu, editor-style, featured-images, footer-widgets, full-width-template, rtl-language-support, sticky-post, theme-options, threaded-comments, translation-ready, block-styles, wide-blocks, accessibility-ready
Version: 1.3
Requires at least: 5.0
Tested up to: 5.4
Requires PHP: 7.0
License: GNU General Public License v2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html
Text Domain: twentytwenty
This theme, like WordPress, is licensed under the GPL.
Use it to make something cool, have fun, and share what you've learned with others.
*/
```

<!-- 
WordPress Theme Repository uses the number after “Version” in this file to determine if the theme has a new version available.
 -->

WordPress テーマ・リポジトリは、このファイル内の「Version」の後の数字を使用して、テーマが新しいバージョンを利用可能かどうかを判断します。

<!-- 
### Explanations
 -->

### 解説

<!-- 
Items indicated with (*\**) are required for a theme in the WordPress Theme Repository.
 -->

WordPress テーマ・リポジトリのテーマには、(*`*`*) で示された項目が必須です。

<!-- 
*   **Theme Name** (\*): Name of the theme.
*   **Theme URI**: The URL of a public web page where users can find more information about the theme.
*   **Author** (\*): The name of the individual or organization who developed the theme. Using the Theme Author’s wordpress.org username is recommended.
*   **Author URI**: The URL of the authoring individual or organization.
*   **Description** (\*): A short description of the theme.
*   **Version** (\*): The version of the theme, written in X.X or X.X.X format.
*   **Requires at least (\*)**: The oldest main WordPress version the theme will work with, written in X.X format. Themes are only required to support the three last versions.
*   **Tested up to (\*):** The last main WordPress version the theme has been tested up to, i.e. 5.4. Write only the number, in X.X format.
*   **Requires PHP (\*)**: The oldest PHP version supported, in X.X format, only the number
*   **License** (\*): The license of the theme.
*   **License URI** (\*): The URL of the theme license.
*   **Text Domain** (\*): The string used for textdomain for translation.
*   **Tags**: Words or phrases that allow users to find the theme using the tag filter. A full list of tags is in the [Theme Review Handbook](https://make.wordpress.org/themes/handbook/review/required/theme-tags/).
*   **Domain Path**: Used so that WordPress knows where to find the translation when the theme is disabled. Defaults to `/languages`.
 -->

*   **Theme Name** (\*): テーマの名称です。
*   **Theme URI**: テーマに関する詳細情報をユーザーが確認できる、公開 Web ページの URL です。
*   **Author** (\*): テーマを開発した個人または組織の名前です。テーマ作者の wordpress.org ユーザー名を使用することを推奨します。
*   **Author URI**: 作者個人または組織の URL です。
*   **Description** (\*): テーマの、簡単な説明です。
*   **Version** (\*): X.X または X.X.X 形式で記述された、テーマのバージョンです。
*   **Requires at least (\*)**: テーマが動作する、X.X 形式で表記された、最も古いメイン WordPress バージョンです。テーマは直近3バージョンへの対応のみが義務付けられています。
*   **Tested up to (\*):** テーマがテスト済みの、最新の WordPress メジャーバージョン、たとえば5.4です。数字のみを X.X 形式で記載します。
*   **Requires PHP (\*)**: 数字のみを X.X 形式で表記される、サポート対象の最も古い PHP バージョンです。
*   **License** (\*): テーマのライセンスです。
*   **License URI** (\*): テーマのライセンスの URL です。
*   **Text Domain** (\*): 翻訳用の textdomain に使用される文字列です。
*   **Tags**: ユーザーがタグフィルターを使用してテーマを検索できるようにする単語またはフレーズです。タグの完全なリストは [テーマ審査ハンドブック](https://make.wordpress.org/themes/handbook/review/required/theme-tags/) に記載されています。
*   **Domain Path**: テーマが無効化された際に、WordPress が翻訳ファイルの場所を認識できるように使用されます。デフォルトは `/languages` です。

<!-- 
After the required header section, style.css can contain anything a regular CSS file has.
 -->

必要なヘッダーセクションの後、style.css には通常の CSS ファイルが持つ、あらゆる内容を含めることができます。

<!-- 
## Style.css for a Child Theme
 -->

## 子テーマ用 style.css

<!-- 
If your theme is a Child Theme, the **Template** line is required in style.css header.
 -->

あなたのテーマが子テーマの場合、style.css のヘッダーに **Template** 行が必要です。

```css
/*
Theme Name: My Child Theme
Template: twentytwenty
*/
```

<!-- 
For more information on creating a Child Theme, visit the [Child Themes](/themes/advanced-topics/child-themes/) page.
 -->

子テーマの制作に関する詳細は、[子テーマ](/themes/advanced-topics/child-themes/) ページをご覧ください。