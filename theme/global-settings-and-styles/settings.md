<!-- 
# Settings
 -->

# 設定

<!-- 
The `settings` property in `theme.json` lets you configure a wide range of settings for a WordPress install. It covers everything from color presets, to enabling typography design tools, to layout, and a little bit of everything in between.
 -->

`theme.json` 内の `settings` プロパティを使用すると、WordPress インストールに関する、幅広い設定を構成できます。色のプリセットからタイポグラフィ・デザイン・ツールの有効化、レイアウト設定まで、あらゆる設定項目を網羅しています。

<!-- 
This document contains links for learning about each of these settings, which have their own individual documentation pages.
 -->

本ドキュメントには、それぞれの設定について学ぶためのリンクが含まれており、各設定には個別のドキュメントページがあります。

<!-- 
## The settings property
 -->

## 設定プロパティ

<!-- 
`settings` is a top-level property in `theme.json` and has multiple nested properties that you can define. And some of those nested properties have multiple levels of nesting of their own.
 -->

`settings` は `theme.json` の最上位プロパティであり、定義可能な複数のネストされたプロパティを備えています。また、それらのネストされたプロパティの一部は、それ自体で複数のネストレベルを持っています。

<!-- 
The following is an overarching look at these properties in the context of a `theme.json` file:
 -->

以下は、`theme.json` ファイルの文脈における、これらのプロパティの包括的な概要です:

```json
{
	"version": 2,
	"settings": {
		"appearanceTools": false,
		"border": {},
		"color": {},
		"custom": {},
		"dimensions": {},
		"layout": {},
		"position": {},
		"shadow": {},
		"spacing": {},
		"typography": {},
		"useRootPaddingAwareAlignments": false,
		"blocks": {}
	}
}
```

<!-- 
## Settings documentation
 -->

## 設定ドキュメント

<!-- 
Use the following links to explore specific settings that you can configure in your `theme.json` file:
 -->

以下のリンクを使用して、あなたの `theme.json` ファイルで設定可能な特定の設定を、ご確認いただけます:

<!-- 
*   **[`appearanceTools`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/appearance-tools/):** A catchall setting for enabling multiple other settings.
*   **`[border](https://developer.wordpress.org/themes/global-settings-and-styles/settings/border/)`:** Used for controlling the border width, style, color, and radius.
*   **[`color`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/color/):** Lets you register a color palette, gradients, duotone and configure color-related settings.
*   [`**custom**`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/custom/): An object for adding custom settings, which are output as CSS custom properties.
*   **[`dimensions`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/dimensions/):** Lets you configure the minimum height setting.
*   **[`layout`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/layout/):** Used for setting layout properties like the content and wide widths.
*   **[`lightbox`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/lightbox/):** Lets you configure the image lightbox feature.
*   **[`position`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/position/):** Currently lets you define support for sticky positioning.
*   **[`shadow`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/shadow/):** Lets you configure box-shadow support and define custom shadow presets.
*   **[`spacing`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/spacing/):** Used for configuring spacing-related settings, such as margin and padding, 
*   **[`typography`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/typography/):** Used for configuring typography-related settings, defining custom font sizes, and registering font families.
*   **[`useRootPaddingAwareAlignments`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/use-root-padding-aware-alignments/):** A boolean setting for how padding on the root element should work.
*   **[`blocks`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/blocks/):** An object for configuring per-block settings.
 -->

*   **[`appearanceTools`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/appearance-tools/):** 複数の設定を有効にするための、包括的な設定です。
*   **`[border](https://developer.wordpress.org/themes/global-settings-and-styles/settings/border/)`:** 枠線の幅、スタイル、色、角丸を制御するために使用します。
*   **[`color`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/color/):** 色パレット、グラデーション、デュオトーンを登録し、色関連の設定を構成します。
*   **[`custom`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/custom/):** カスタム設定を追加するためのオブジェクトで、CSS カスタム・プロパティとして出力されます。
*   **[`dimensions`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/dimensions/):** 最小高の設定を構成します。
*   **[`layout`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/layout/):** コンテンツ幅や幅広などのレイアウト・プロパティを設定するために使用します。
*   **[`lightbox`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/lightbox/):** 画像ライトボックス機能を設定します。
*   **[`position`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/position/):** 現在、固定表示のサポートを定義します。
*   **[`shadow`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/shadow/):** ボックス・シャドウのサポートやカスタム・シャドウ・プリセットを設定します。
*   **[`spacing`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/spacing/):** マージンやパディングなど、間隔関連の設定を構成するために使用されます。
*   **[`typography`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/typography/):** タイポグラフィ関連の設定、カスタム・フォント・サイズの定義、フォント・ファミリーの登録に使用されます。
*   **[`useRootPaddingAwareAlignments`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/use-root-padding-aware-alignments/):** ルート要素のパディングの動作方法を指定する真偽値設定です。
*   **[`blocks`](https://developer.wordpress.org/themes/global-settings-and-styles/settings/blocks/):** ブロックごとの設定を構成するためのオブジェクトです。

<!-- 
The Theme Handbook also maintains a [reference for available settings](https://developer.wordpress.org/themes/global-settings-and-styles/settings/settings-reference/) based on the `theme.json` schema.
 -->

テーマ・ハンドブックは、`theme.json` スキーマにもとづく [利用可能な設定のリファレンス](https://developer.wordpress.org/themes/global-settings-and-styles/settings/settings-reference/) もメンテナンスしています。