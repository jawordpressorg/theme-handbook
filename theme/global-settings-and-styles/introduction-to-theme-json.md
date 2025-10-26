<!-- 
# Introduction to theme.json
 -->

# theme.json の概要

<!-- 
`theme.json` is a configuration file that lets you define the global settings, styles, and more for your theme. The file works with both block and classic themes. 
 -->

`theme.json` は、あなたのテーマのグローバル設定やスタイルなどを定義できる設定ファイルです。このファイルはブロック・テーマとクラシック・テーマの両方で使用できます。

<!-- 
When building a block theme, `theme.json` may be the most important file in the entire theme. In a way, it is the foundational piece that trickles down to every other component. That’s why this chapter is one of the most extensive in the handbook.
 -->

ブロック・テーマを構築する際、`theme.json` は、テーマ全体で最も重要なファイルとなる可能性があります。ある意味では、これは他のすべてのコンポーネントに浸透する基盤となる要素です。そのため、本章はハンドブック中で最も詳細な章の一つとなっています。

<!-- 
Some of the things you can do with `theme.json` include (but are not limited to):
 -->

`theme.json` で実行可能な操作には、以下が含まれます (ただしこれらに限定されません):

<!-- 
*   Enabling block features in the user interface, such as color, typography, and spacing controls.
*   Configuring a custom color palette, duotone filters, and background gradients.
*   Defining typographical features like font families, bundling web fonts, and more.
*   Adding your own CSS custom properties.
*   Adjusting the overall design by working within the core styles system.
 -->

*   ユーザー・インターフェースにおける、色、タイポグラフィ、間隔調整などのブロック機能の有効化。
*   カスタム・カラーパレット、デュオトーン・フィルター、背景グラデーションの設定。
*   フォントファミリー、Web フォントのバンドルなど、タイポグラフィ機能の定義。
*   独自の CSS カスタム・プロパティの追加。
*   コアスタイルシステム内で作業し、デザイン全体の調整。

<!-- 
The settings and styles that you configure in `theme.json` are ultimately reflected on both the front end of the site and WordPress’ built-in editors. As shown in this screenshot, you can see that a variation of the default Twenty Twenty-Three theme as it’s looks in the **Appearance > Editor** screen in the admin:
 -->

`theme.json` で構成する設定とスタイルは、最終的にサイトのフロントエンドと WordPress の組込みディターの両方に反映されます。このスクリーンショットに示されているように、管理画面の **外観 > エディター** 画面で表示されるデフォルトの Twenty Twenty-Three テーマのバリエーションを確認できます:

<!-- 
[![WordPress Site Editor with the Styles panel open in the right sidebar.](https://i0.wp.com/developer.wordpress.org/files/2023/09/intro-styles-interface.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/intro-styles-interface.jpg?ssl=1)
 -->

[![右サイドバーにスタイルパネルが開いている、WordPress サイトエディター。](https://i0.wp.com/developer.wordpress.org/files/2023/09/intro-styles-interface.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/intro-styles-interface.jpg?ssl=1)

<!-- 
Each part of that design is handled directly in `theme.json`, and the user can further customize it through the built-in **Styles** interface.
 -->

そのデザインの各部分は `theme.json` で直接処理され、ユーザーは組込みの **スタイル** インターフェースを通じてさらにカスタマイズできます。

<!-- 
`theme.json` represents what you might call a “common language” that allows WordPress, your theme, plugins, and users to effectively communicate. Because it is built atop a standardized system, each component plays a role in bringing the overall site to life.
 -->

`theme.json` は、WordPress、あなたのテーマ、プラグイン、そしてユーザーが効果的にコミュニケーションを取ることを可能にする、いわば「共通言語」のようなものです。標準化されたシステムの上に構築されているため、各コンポーネントが役割を果たすことで、サイト全体が機能し、生き生きとしたものになります。

<!-- 
## theme.json structure
 -->

## theme.json の構造

<!-- 
The `theme.json` file can be broken down into several top-level sections as shown in this code snippet:
 -->

`theme.json` ファイルは、以下のコード・スニペットに示すように、いくつかの最上位セクションに分解できます:

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
Throughout this chapter, you will learn about each of these properties and how you can work with them to turn the design in your imagination into a working theme.
 -->

本章を通して、これらの各プロパティについて学び、それらを活用してあなたの想像上のデザインを、機能するテーマへと変換する方法について、理解を深めていきます。

<!-- 
Customizing the `theme.json` file directly in your theme requires that you have some familiarity with JSON code. You don’t need to be an expert (*copying and pasting can get you pretty far*), but having some foundational knowledge of how to format JSON will definitely help.
 -->

あなたのテーマ内で直接 `theme.json` ファイルをカスタマイズするには、JSON コードに関するある程度の知識が必要です。専門家である必要はありません (*コピー＆ペーストだけでもかなり進められます*) が、JSON のフォーマット方法に関する基礎的な知識があると確実に役立ちます。

<!-- 
You should also have a baseline understanding of CSS. While you do not need to directly write CSS code in `theme.json`, many of the features are mapped to CSS properties and values. Understanding the relationship between `theme.json` settings and styles and their CSS counterparts will help you in the long run.
 -->

CSS の基本的な理解も必要です。`theme.json` に直接 CSS コードを記述する必要はありませんが、多くの機能が CSS のプロパティや値に対応づけられます。`theme.json` の設定とスタイル、およびそれに対応する CSS の関連性を理解することは、長期的に見て役立ちます。

<!-- 
For more information on JSON and CSS, read:
 -->

JSON と CSS の詳細については、下記をご覧ください:

<!-- 
*   [MDN Web Docs: CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)
*   [MDN Web Docs: JSON](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON)
 -->

*   [MDN Web Docs: CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)
*   [MDN Web Docs: JSON](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON)

<!-- 
## theme.json properties
 -->

## theme.json のプロパティ

<!-- 
As you could see in the previous section, the `theme.json` file has several top-level properties. Some of these accept just a single value, but most have nested sub-properties with their own values.
 -->

前のセクションで見たように、`theme.json` ファイルには、いくつかの最上位プロパティがあります。これらのうちいくつかは単一の値のみを受け付けますが、ほとんどは独自の値を持つネストされたサブプロパティを持っています。

<!-- 
These are the current top-level properties that you can set in `theme.json`:
 -->

`theme.json` で設定可能な、現在の最上位プロパティは、以下の通りです:

<!-- 
*   **`version`:** The `theme.json` schema version you are building for. 
*   **`$schema`:** Used for defining the supported JSON schema, which will integrate with many code editors to give you on-the-fly hints and error reporting.
*   **`settings`:** Used to define which block controls appear, configure presets, and more.
*   **`styles`:** Used to apply colors, font sizes, custom CSS, and other styles  to the website and blocks.
*   **`customTemplates`:** Metadata for custom templates defined in your theme’s `/templates` folder.
*   **`templateParts`:** Metadata for template parts defined in your theme’s `/parts` folder.
*   **`patterns`:** An array of pattern slugs to be registered from the [Pattern Directory](https://wordpress.org/patterns/).
 -->

*   **`version`:** 構築対象の `theme.json` スキーマ・バージョンです。
*   **`$schema`:** サポートする JSON スキーマを定義するために使用されます。多くのコードエディターと連携し、リアルタイムのヒントやエラー報告を提供します。
*   **`settings`:** 表示するブロック・コントロールの定義、プリセットの設定などに使用されます。
*   **`styles`:** Web サイトやブロックに対して、色、フォントサイズ、カスタム CSS、その他のスタイルを適用するために使用されます。
*   **`customTemplates`:** あなたのテーマの `/templates` フォルダー内で定義された、カスタム・テンプレートのメタデータです。
*   **`templateParts`:** あなたのテーマの `/parts` フォルダー内で定義された、テンプレート・パーツのメタデータです。
*   **`patterns`:** [パターン・ディレクトリ](https://wordpress.org/patterns/) から登録されるパターンスラッグの配列です。

<!-- 
### Adding a version
 -->

### バージョンの追加

<!-- 
At the very least, you should set the `version` property in your `theme.json` file. This should be an integer that matches the API version used to read and understand your `theme.json` code.
 -->

少なくとも、あなたの `theme.json` ファイルで `version` プロパティを設定する必要があります。これは、あなたの `theme.json` コードを読み取り理解するために使用される、API バージョンと一致する整数であるべきです。

<!-- 
The API is currently at version `2`. You can always find the most up-to-date version via the [`theme.json` Living Reference](https://developer.wordpress.org/block-editor/reference-guides/theme-json-reference/theme-json-living/) document.
 -->

API は現在バージョン `2` です。最新バージョンは、常に [`theme.json` リビング・リファレンス](https://developer.wordpress.org/block-editor/reference-guides/theme-json-reference/theme-json-living/) ドキュメントで確認できます。

<!-- 
The bear minimum code that your `theme.json` file should have is:
 -->

あなたの `theme.json` ファイルに最低限必要となるコードは、以下の通りです:

```json
{
	"version": 2
}
```

<!-- 
All `theme.json` code examples in this handbook include the `version` property because it should always be set.
 -->

本ハンドブック内のすべての `theme.json` コード例には、`version` プロパティが含まれています。これは常に設定すべきプロパティだからです。

<!-- 
Technically, you can leave the version out, but WordPress will read your code as if it was on version `1` of the API. Using an outdated version may mean that your code will not be valid, at least as it is documented here in the handbook.
 -->

技術的にはバージョンを省略できるが、その場合、WordPress はあなたのコードを API バージョン `1` のものとして解釈します。古いバージョンを使用すると、少なくとも本ハンドブックに記載されている仕様では、あなたのコードが無効になってしまう可能性があります。

<!-- 
 You should always strive to keep up to date with the latest API version and make sure it is set in your `theme.json` file.
 -->

 常に最新の API バージョンを把握するよう努め、それがあなたの `theme.json` ファイルに設定されていることを確認してください。

<!-- 
### Adding a JSON schema
 -->

### JSON スキーマの追加

<!-- 
An optional property that you can add to your `theme.json` is a URL to the JSON schema. This can be particularly helpful when working with any modern code editor. Adding the `$schema` property will give you on-the-fly hints and error reporting in many code editors and is highly recommended.
 -->

あなたの `theme.json` に追加できる任意のプロパティは、JSON スキーマへの URL です。これは特に、モダンなコードエディターを使用する際に役立ちます。`$schema` プロパティを追加すると、多くのコードエディターでリアルタイムのヒントやエラー報告が得られ、強く推奨されます。

<!-- 
To add support for JSON schema, add this to your `theme.json` file:
 -->

JSON スキーマのサポートを追加するには、以下の内容をあなたの `theme.json` ファイルに追加してください:

```json
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2
}
```

<!-- 
Again, this is *technically* an optional property. But there is rarely a good reason to leave it out. It’s just good development practice to include it.
 -->

繰り返しますが、これは *技術的には* 任意のプロパティです。しかし、これを省略する正当な理由はほとんどありません。含めることが良い開発につながります。

<!-- 
### Adding settings, styles, and more
 -->

### 設定、スタイルなどの追加

<!-- 
The other properties available to you via `theme.json` require more in-depth documentation than what can be covered in this introduction. They each have their own pages (and some with multiple sub-pages) in this chapter of the handbook.
 -->

`theme.json` 経由で利用可能なその他のプロパティについては、この概要で網羅できる範囲を超える、詳細なドキュメントが必要です。このハンドブックの章には、それぞれ (複数サブページを持つものも含む) 専用のページが用意されています。

<!-- 
Now it’s time to really dive into learning more about `theme.json`. You can take these next documentation steps as you prefer, but these are listed in their recommended reading order:
 -->

それでは、`theme.json` についてさらに深く学ぶときが来ました。この後のドキュメントの手順は、好みの順序で進めていただいてかまいませんが、推奨される読み順は以下の通りです:

<!-- 
*   [**Settings**](https://developer.wordpress.org/themes/global-settings-and-styles/settings/)**:** Documentation for each of the standard and custom settings that you can configure via `theme.json`.
*   [**Styles**](https://developer.wordpress.org/themes/global-settings-and-styles/styles/)**:** Learn how to use the standard design system to apply styles through `theme.json`, which also integrate with the user interface.
*   [**Custom Templates**](https://developer.wordpress.org/themes/global-settings-and-styles/custom-templates/)**:** How to register custom post, page, and CPT (custom post type) templates for your theme.
*   [**Template Parts**](https://developer.wordpress.org/themes/global-settings-and-styles/template-parts/)**:** How to register custom template parts that can be reused across your theme.
*   [**Patterns**](https://developer.wordpress.org/themes/global-settings-and-styles/patterns/)**:** How to bundle patterns from the official patterns repository with your theme.
*   [**Style Variations**](https://developer.wordpress.org/themes/global-settings-and-styles/style-variations/)**:** Documentation on creating custom `theme.json` style variations, giving your users alternative designs to choose from.
 -->

*   [**設定**](https://developer.wordpress.org/themes/global-settings-and-styles/settings/): `theme.json` 経由で構成可能な、標準設定およびカスタム設定のドキュメントです。
*   [**スタイル**](https://developer.wordpress.org/themes/global-settings-and-styles/styles/): ユーザーインターフェースとも連携する `theme.json` を通じて、スタイルを適用する標準デザインシステムの使用方法を学びます。
*   [**カスタム・テンプレート**](https://developer.wordpress.org/themes/global-settings-and-styles/custom-templates/): あなたのテーマ用にカスタム投稿、ページ、および CPT (カスタム投稿タイプ) テンプレートを登録する方法です。
*   [**テンプレート・パーツ**](https://developer.wordpress.org/themes/global-settings-and-styles/template-parts/): あなたのテーマ全体で再利用可能な、カスタム・テンプレートパーツを登録する方法です。
*   [**パターン**](https://developer.wordpress.org/themes/global-settings-and-styles/patterns/): 公式パターン・リポジトリのパターンを、あなたのテーマにバンドルする方法です。
*   [**スタイル・バリエーション**](https://developer.wordpress.org/themes/global-settings-and-styles/style-variations/): カスタム `theme.json` スタイルバリエーションを作成し、あなたのユーザーが選択できる代替デザインを提供するドキュメントです。