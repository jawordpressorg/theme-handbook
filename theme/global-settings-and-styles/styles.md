<!-- 
# Styles
 -->

# スタイル

<!-- 
The `styles` property in `theme.json` lets you configure settings at the global level, for individual elements, and individual blocks. WordPress supports a standard subset of the CSS specification, but also allows you to add custom CSS directly in your `theme.json` file.
 -->

`theme.json` 内の `styles` プロパティを使用すると、グローバル・レベル、個々の要素、個々のブロックごとに設定を構成できます。WordPress は CSS 仕様の標準的なサブセットをサポートしていますが、あなたの `theme.json` ファイルに直接カスタム CSS の追加も許可しています。

<!-- 
When possible, it is recommended to add your theme styles via the `styles` property, at least for standard WordPress features. This makes it possible for users to customize them via **Appearance > Editor > Styles** without CSS specificity issues.
 -->

可能な場合は、少なくとも標準的な WordPress 機能については、`styles` プロパティを介してあなたのテーマスタイルの追加を推奨します。これにより、ユーザーは CSS の詳細度の問題なしに、**外観 > エディター > スタイル** 経由でそれらをカスタマイズできます。

<!-- 
This document contains links for learning about the available style properties and how to apply styles to your theme via its `theme.json` file.
 -->

本ドキュメントには、利用可能なスタイル・プロパティについて学ぶためのリンクと、`theme.json` ファイルを介してあなたのテーマにスタイルを適用する方法についてのリンクが含まれています。

<!-- 
## The styles property
 -->

## スタイル・プロパティ

<!-- 
`styles` is a top-level property in `theme.json` and has multiple nested properties that you can define. And some of those nested properties have multiple levels of nesting of their own.
 -->

`styles` は `theme.json` のトップレベル・プロパティであり、定義可能な複数のネストされたプロパティを持ちます。また、それらのネストされたプロパティの一部は、それ自体で複数のネストレベルを持ちます。

<!-- 
The following is an overarching look at these properties in the context of a `theme.json` file:
 -->

以下は、`theme.json` ファイルの文脈におけるこれらのプロパティの包括的な概要です:

```json
{
	"version": 2,
	"styles": {
		"elements": {},
		"blocks": {}
	}
}
```

<!-- 
The following is an example of what the `styles` property could look like in a custom `theme.json` file. This should give you a feel for how it is structured, but you will dive into this more deeply as you read through this section of the handbook:
 -->

以下は、カスタム `theme.json` ファイル内で `styles` プロパティがどのように記述されるかの例です。これにより構造の概略が理解できるでしょうが、ハンドブックの本セクションを読み進める中で、さらに深く掘り下げていきます:

```json
{
	"version": 2,
	"styles": {
		"color": {
			"text": "#000000",
			"background": "#ffffff"
		},
		"elements": {
			"button": {
				"color": {
					"text": "#ffffff",
					"background": "#000000"
				}
			}
		},
		"blocks": {
			"core/code": {
				"color": {
					"text": "#ffffff",
					"background": "#000000"
				}
			}
		}
	}
}
```

<!-- 
## Styles documentation
 -->

## スタイル・ドキュメント

<!-- 
Use the following links to explore configuring styles via `theme.json` file:
 -->

以下のリンクを使用して、`theme.json` ファイルによるスタイル設定の方法をご覧ください:

<!-- 
*   **[Applying Styles](https://developer.wordpress.org/themes/global-settings-and-styles/styles/applying-styles/):** How to apply custom styles to your theme using the standard JSON syntax.
*   **[Using Presets](https://developer.wordpress.org/themes/global-settings-and-styles/styles/using-presets/):** How to use the presets that you’ve configured via the `settings` property in your styles.
*   **[Styles Reference](https://developer.wordpress.org/themes/global-settings-and-styles/styles/styles-reference/):** A reference guide for the available style properties that you can use in `theme.json`.
 -->

*   **[スタイルの適用](https://developer.wordpress.org/themes/global-settings-and-styles/styles/applying-styles/):** 標準の JSON 構文を使用して、あなたのテーマにカスタム・スタイルを適用する方法。
*   **[プリセットの使用](https://developer.wordpress.org/themes/global-settings-and-styles/styles/using-presets/):** `settings` プロパティで設定したプリセットを、あなたのスタイルで使用する方法。
*   **[スタイル・リファレンス](https://developer.wordpress.org/themes/global-settings-and-styles/styles/styles-reference/):** `theme.json` で使用可能なスタイル・プロパティのリファレンス・ガイド。