<!-- 
# Global Settings and Styles
 -->

# グローバル設定とスタイル

<!-- 
As you learned in [Theme Structure](https://developer.wordpress.org/themes/core-concepts/theme-structure/), `theme.json` is a standard file that WordPress looks for in your theme. While it is not technically required for a block theme, it is almost always necessary to configure various settings and styles for your theme.
 -->

[テーマ構造](https://developer.wordpress.org/themes/core-concepts/theme-structure/) で学んだように、`theme.json` は WordPress があなたのテーマ内で探す標準的なファイルです。ブロック・テーマでは技術的には必須ではありませんが、あなたのテーマのさまざまな設定やスタイルを構成するには、ほとんどの場合、このファイルが必要です。

<!-- 
This documentation is a quick introduction on what `theme.json` is and how it works. However, it is such a massive topic that there is a dedicated chapter that explores everything you can do with it: [Global Settings and Styles](https://developer.wordpress.org/themes/global-settings-and-styles/).
 -->

このドキュメントは、`theme.json` とは何か、そしてどのように機能するかを簡単に紹介するものです。ただし、このテーマは非常に広範なため、そのすべてを網羅した専用の章が用意されています: [グローバル設定とスタイル](https://developer.wordpress.org/themes/global-settings-and-styles/)。

<!-- 
## What is theme.json?
 -->

## theme.json とは ?

<!-- 
`theme.json` is a configuration file that tells WordPress what settings you want to enable, how to style specific elements and blocks, and which templates and template parts to register.
 -->

`theme.json` は、WordPress に、有効にする設定、特定の要素やブロックのスタイリング方法、登録するテンプレートやテンプレート・パーツを指示する設定ファイルです。

<!-- 
Some of the things you can do with `theme.json` are:
 -->

`theme.json` でできることの一部は、以下の通りです:

<!-- 
*   Enable or disable features like drop caps, padding, margin, and line-height.
*   Add a color palette, gradients, duotones, and shadows.
*   Configure typographical features like font families, sizes, and more.
*   Add CSS custom properties.
*   Register custom templates and assign parts to template part areas.
 -->

*   ドロップキャップ、パディング、マージン、行高などの機能を有効または無効にします。
*   カラーパレット、グラデーション、デュオトーン、シャドウを追加します。
*   フォント・ファミリー、サイズなどのタイポグラフィー設定を構成します。
*   CSS カスタム・プロパティを追加します。
*   カスタム・テンプレートを登録し、テンプレート・パーツをテンプレート領域に割り当てます。

<!-- 
Your `theme.json` configuration will be reflected in what you see in places like the post, template, and site editors in the WordPress admin. Custom styles, in particular, will be reflected in the **Styles** interface:
 -->

あなたの `theme.json` 設定は、WordPress の管理画面に表示される投稿、テンプレート、サイトエディターなどに反映されます。特にカスタム・スタイルは、**スタイル** インターフェースに反映されます:

<!-- 
[![WordPress Site Editor viewing a Single Post template. On the right, the Buttons block is highlighted in the Styles interface.](https://i0.wp.com/developer.wordpress.org/files/2023/11/global-styles-site-editor.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/global-styles-site-editor.jpg?ssl=1)
 -->

[![WordPress サイトエディターで「個別投稿」テンプレートを表示。右側では、「スタイル」インターフェースで「ボタン」ブロックが強調表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/11/global-styles-site-editor.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/global-styles-site-editor.jpg?ssl=1)

<!-- 
## theme.json structure
 -->

## theme.json 構造

<!-- 
A `theme.json` file can be as little as a few lines of code, such as this example that enables the appearance tools for blocks:
 -->

`theme.json` ファイルは、ブロックの表示ツールを有効にするこの例のように、わずか数行のコードで構成されることもあります:

```json
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2,
	"settings": {
		"appearanceTools": true
	}
}
```

<!-- 
Or it can be a massively complex file that spans 1,000s of lines of code. How many of the features you want to configure is entirely up to you.
 -->

または、1,000行超にわたるコードの、非常に複雑なファイルである可能性もあります。設定したい機能の数は、完全にあなたの判断に委ねられています。

<!-- 
The starting point is understanding the top-level properties that can be configured. Here is an outline of what this looks like:
 -->

最初のステップは、設定可能な上位レベルのプロパティを理解することです。以下にその概要を示します:

```json
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2,
	"settings": {},
	"styles": {},
	"customTemplates": {},
	"templateParts": {},
	"patterns": []
}
```

<!-- 
Here are what each of these properties define:
 -->

以下は、これらの各プロパティが定義する内容です:

<!-- 
*   **`$schema`:** Used for defining the supported JSON schema, which will integrate with many code editors to give you on-the-fly hints and error reporting.
*   **`version`:** The `theme.json` schema version you are building for. The latest version is 2 and can always be found in the [`theme.json` Living Reference](https://developer.wordpress.org/block-editor/reference-guides/theme-json-reference/theme-json-living/), a document that lists the most up-to-date properties you can set.
*   **`settings`:** Used to define your block controls and color palettes, font sizes, and more.
*   **`styles`:** Used to apply colors, font sizes, custom CSS, and more to the website and blocks.
*   **`customTemplates`:** Metadata for custom templates defined in your theme’s `/templates` folder.
*   **`templateParts`:** Metadata for template parts defined in your theme’s  `/parts` folder.
*   **`patterns`:** An array of pattern slugs to be registered from the [Pattern Directory](https://wordpress.org/patterns/).
 -->

*   **`$schema`:** サポートされる JSON スキーマを定義するために使用され、多くのコードエディターと統合され、リアルタイムのヒントとエラー報告を提供します。
*   **`version`:** 構築中の `theme.json` スキーマのバージョンです。最新のバージョンは2で、常に [`theme.json` ライブ・リファレンス](https://developer.wordpress.org/block-editor/reference-guides/theme-json-reference/theme-json-living/) というドキュメントに記載されており、設定可能な最新のプロパティが列挙されています。
*   **`settings`:** あなたのブロック・コントロールやカラーパレット、フォントサイズなどを定義するために使用されます。
*   **`styles`:** Web サイトとブロックにカラー、フォントサイズ、カスタム CSS などを適用するために使用されます。
*   **`customTemplates`:** あなたのテーマの `/templates` フォルダーで定義された、カスタム・テンプレート用のメタデータです。
*   **`templateParts`:** あなたのテーマの  `/parts` フォルダーで定義された、テンプレート・パーツ用のメタデータです。
*   **`patterns`:** [パターン・ディレクトリ](https://wordpress.org/patterns/) から登録するパターン・スラッグの配列です。

<!-- 
You will learn more about these properties and their sub-properties in the [Global Settings and Styles](https://developer.wordpress.org/themes/global-settings-and-styles/) chapter.
 -->

これらのプロパティとそのサブプロパティについては、[グローバル設定とスタイル](https://developer.wordpress.org/themes/global-settings-and-styles/) 章で詳しく学ぶことができます。

<!-- 
## Settings and styles hierarchy
 -->

## 設定とスタイルの階層構造

<!-- 
The `theme.json` file in your theme is only one level in a hierarchy of setting and style configurations for a website. This means it can be overridden under certain circumstances.
 -->

あなたのテーマ内の `theme.json` ファイルは、Web サイト用の設定とスタイルの構成階層における、一レベルに過ぎません。これは、特定の条件下で上書きされる可能性があることを意味します。

<!-- 
The order of this hierarchy from lowest to highest is:
 -->

この階層の優先順位は、最も低いものから最も高いものまで以下の通りです:

<!-- 
*   **WordPress `theme.json`:** WordPress has its own `theme.json` file that defines the default settings and styles.
*   **Theme `theme.json`:** Anything you define in your theme’s `theme.json` file overrides the WordPress defaults.
*   **Child theme `theme.json`:** If active, a child theme’s `theme.json` takes priority over the main or “parent” theme.
*   **User configuration:** Users can further customize how their site works under **Appearance > Editor** in the WordPress admin, and the JSON data is saved in their site’s database. Their choice takes priority over all other levels in the hierarchy.
 -->

*   **WordPress `theme.json`:** WordPress には、デフォルトの設定とスタイルを定義する独自の `theme.json` ファイルがあります。
*   **テーマ `theme.json`:** あなたのテーマの `theme.json` ファイルで定義した内容は、WordPress のデフォルト設定よりも優先されます。
*   **子テーマ `theme.json`:** 有効化されている場合、子テーマの `theme.json` がメインテーマまたは「親」テーマよりも優先されます。
*   **ユーザー設定:** ユーザーは、WordPress 管理画面の **外観 > エディター** で、サイトの動作をさらにカスタマイズでき、JSON データはサイトのデータベースに保存されます。ユーザーの選択は、階層内の他のすべてのレベルよりも優先されます。

<!-- 
There are also filter hooks available that let plugin and theme authors override the values dynamically. To learn more about these, check out [How to modify theme.json data using server-side filters](https://developer.wordpress.org/news/2023/07/how-to-modify-theme-json-data-using-server-side-filters/) from the WordPress Developer Blog.
 -->

プラグインやテーマの作成者が値を動的に上書きできるようなフィルター・フックも利用できます。これらの詳細については、WordPress 開発者ブログ [サーバーサイド・フィルターを使用して、theme.json データを修正する方法](https://developer.wordpress.org/news/2023/07/how-to-modify-theme-json-data-using-server-side-filters/) をご覧ください。

<!-- 
The important thing to remember is that anything configured in your `theme.json` file may not take priority in the hierarchy.
 -->

重要な点は、あなたの `theme.json` ファイルで設定された内容は、階層構造において優先されない場合がある、という点を覚えておくことです。