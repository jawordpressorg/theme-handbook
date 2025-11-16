<!-- 
# Custom
 -->

# カスタム

<!-- 
The `settings.custom` property is unique among other settings in `theme.json`. As its name implies, it is a custom property. This means that you get to decide how to use it. Essentially, it provides a method for creating CSS custom properties that you might need elsewhere in your theme.
 -->

`settings.custom` プロパティは、`theme.json` 内の他の設定とは一線を画すものです。その名が示すとおり、これはカスタム・プロパティです。つまり、その使用方法は、あなたが自由に決められます。要するに、あなたのテーマ内で必要となるかもしれない CSS カスタムプロパティを作成する手段を提供するものです。

<!-- 
In this document, you will learn what the `custom` property is for and how you can use it in your theme.
 -->

本ドキュメントでは、`custom` プロパティの目的と、あなたのテーマでどのように使用できるかを学びます。

<!-- 
## Overview of the custom setting
 -->

## カスタム設定の概要

<!-- 
The `settings.custom` property accepts a single object, and this object can be used to store other values. The individual object values must be valid CSS values or an object with nested key/value pairs.
 -->

`settings.custom` プロパティは単一のオブジェクトを受け付け、このオブジェクトは他の値を格納するために使用できます。個々のオブジェクト値は、有効な CSS 値、またはネストされたキー・値ペアを持つ、オブジェクトである必要があります。

<!-- 
Here is an example snippet from `theme.json` with no custom values set:
 -->

カスタム値が設定されていない `theme.json` のサンプル・スニペットは、以下の通りです:

```json
{
	"version": 2,
	"settings": {
		"custom": {}
	}
}
```

<!-- 
The great thing about the `settings.custom` object is that you can use it to create your own CSS custom properties. When you add a key and value to the object, WordPress will automatically generate the CSS custom property, assign the value, and load it for you.
 -->

`settings.custom` オブジェクトのすばらしい点は、独自の CSS カスタム・プロパティを作成できることです。オブジェクトにキーと値を追加すると、WordPress が自動的に CSS カスタム・プロパティを生成し、値を割り当て、あなたの代わりにロードします。

<!-- 
The generated CSS custom property will follow this pattern: `--wp--custom--{key}--{value}`.
 -->

生成される CSS カスタム・プロパティは次のパターンに従います: `--wp--custom--{key}--{value}`。

<!-- 
Suppose you wanted to use the key of `fruit` and give it a value of `apple`. Add this to your `theme.json` file:
 -->

`fruit` というキーを使用し、その値を `apple` に設定したい、としましょう。あなたの `theme.json` ファイルに、以下を追加してください:

```json
{
	"version": 2,
	"settings": {
		"custom": {
			"fruit": "apple"
		}
	}
}
```

<!-- 
WordPress will then generate this CSS:
 -->

すると、WordPress は、この CSS を生成します:

```css
body {
	--wp--custom--fruit: apple;
}
```

<!-- 
## How CSS custom properties are generated
 -->

## CSS カスタム・プロパティの生成方法

<!-- 
As you learned above, the `settings.custom.fruit` key name will generate the `--wp--custom--fruit` variable in CSS. But there are other cases too.
 -->

前述の通り、`settings.custom.fruit` というキー名は、CSS で `--wp--custom--fruit` という変数を生成します。ただし、その他のケースも存在します。

<!-- 
### Automatic hyphenation
 -->

### 自動ハイフネーション

<!-- 
WordPress will automatically hyphenate camel-cased names. For example, `lineHeight` in the following example will become `line-height`:
 -->

WordPress はキャメルケース表記の名称を自動的にハイフンで区切ります。たとえば、以下の例における `lineHeight` は、`line-height` となります:

```json
{
	"version": 2,
	"settings": {
		"custom": {
			"lineHeight": "1.4em"
		}
	}
}
```

<!-- 
This will create the following CSS:
 -->

これにより、以下の CSS が生成されます:

```css
body {
	--wp--custom--line-height: 1.4em;
}
```

<!-- 
Numbers are handled the same as uppercase letters when used as a key. For example, a key of `abc123` will become `abc-1-2-3` in the resulting CSS.
 -->

キーとして使用される場合、数字は大文字の文字と同様に扱われます。たとえば、`abc123` というキーは、結果の CSS では `abc-1-2-3` となります。

<!-- 
### Nested properties
 -->

### ネストされたプロパティ

<!-- 
Building off the above example, suppose you wanted to create several line-height CSS custom properties for use in your theme. For this, you might want to create an object under `settings.custom.lineHeight` instead of a single value.
 -->

上記の例をもとに、あなたのテーマで使用する、複数の行高 CSS カスタム・プロパティを作成したい場合を考えましょう。この場合、単一の値ではなく、`settings.custom.lineHeight` の下にオブジェクトを作成することをおすすめします。

<!-- 
Add the following to your `theme.json` file:
 -->

以下の内容を、あなたの `theme.json` ファイルに追加してください:

```json
{
	"version": 2,
	"settings": {
		"custom": {
			"lineHeight": {
				"xs": "1",
				"sm": "1.25",
				"md": "1.5",
				"lg": "1.75"
			}
		}
	}
}
```

<!-- 
WordPress will automatically use this nested structure when generating the CSS custom property names.
 -->

WordPress は、CSS カスタム・プロパティ名を生成する際に、このネスト構造を自動的に使用します。

<!-- 
This will generate this CSS:
 -->

これにより、以下の CSS が生成されます:

```css
body {
	--wp--custom--line-height--xs: 1;
	--wp--custom--line-height--sm: 1.25;
	--wp--custom--line-height--md: 1.5;
	--wp--custom--line-height--lg: 1.75;
}
```

<!-- 
There is no limit to the amount of nesting you can do, but keep in mind that the more you nest, the longer your CSS custom property names become.
 -->

ネストできる回数に制限はないが、ネストを重ねるほど、CSS カスタム・プロパティ名が長くなる点に留意してください。

<!-- 
## Practical usage
 -->

## 実用的な活用法

<!-- 
What you use the `settings.custom` property for is entirely up to you. At its core, all it really does is generate CSS custom properties, which don’t do anything on their own. Custom properties must also be used in CSS.
 -->

`settings.custom` プロパティの使用方法は、完全にあなたに任されてます。本質的には、CSS カスタム・プロパティを生成するだけで、それ自体は単独では何も働きません。カスタム・プロパティも CSS 内で使用する必要があります。

<!-- 
In the previous `theme.json` example above, you created a set of line-heights. There are a number of ways you can put these into practical use. 
 -->

上記の `theme.json` の例では、行高のセットを作成しました。これらを実用的に活用する方法は、いくつかあります。

<!-- 
### Use in theme.json styles
 -->

### theme.json スタイルでの使用

<!-- 
In the [Styles documentation](https://developer.wordpress.org/themes/global-settings-and-styles/styles), you will learn how to apply styles to the root element, elements, and blocks via `theme.json`. This will be one of the primary use cases for integrating with `settings.custom`.
 -->

[スタイル・ドキュメント](https://developer.wordpress.org/themes/global-settings-and-styles/styles) では、`theme.json` を介してルート要素、要素、ブロックにスタイルを適用する方法について学びます。これは `settings.custom` との連携における、主要なユースケースの一つとなります

<!-- 
Suppose you wanted to register the same set of line-heights from above and make use of them. Maybe you want to set the root element to the `md` line-height and Paragraph blocks to `lg`. You can access each line-height property via `var:custom|line-height|md` and `var:custom|line-height|lg`, respectively.
 -->

仮に、上記と同じ行高のセットを登録して、利用したい場合を考えてみましょう。ルート要素を `md` 行高に、段落ブロックを `lg` 行高に設定したいかもしれません。各行高プロパティは、それぞれ `var:custom|line-height|md` と `var:custom|line-height|lg` でアクセスできます。

<!-- 
Use this code in your `theme.json` file:
 -->

このコードを、あなたの `theme.json` ファイルで使用してください:

```json
{
	"version": 2,
	"settings": {
		"custom": {
			"lineHeight": {
				"xs": "1",
				"sm": "1.25",
				"md": "1.5",
				"lg": "1.75"
			}
		}
	},
	"styles": {
		"typography": {
			"lineHeight": "var:custom|line-height|md"
		}
		"blocks": {
			"core/paragraph": {
				"typography": {
					"lineHeight": "var:custom|line-height|lg"
				}
			}
		}
	}
}
```

<!-- 
You can also reference the values via their CSS custom properties. For example, instead of using `var:custom|line-height|md`, use `var( --wp--custom--line-height--md )`.
 -->

また、CSS カスタム・プロパティを介して値も参照できます。たとえば、`var:custom|line-height|md` の代わりに `var( --wp--custom--line-height--md )` を使用します。

<!-- 
Remember, you will learn more about styling via `theme.json` from the [Styles documentation](https://developer.wordpress.org/themes/global-settings-and-styles/styles/). You can use what you learn there to combine with the techniques outlined here.
 -->

`theme.json` によるスタイリングの詳細は、[スタイル・ドキュメント](https://developer.wordpress.org/themes/global-settings-and-styles/styles/) で学べることを、覚えておいてください。そこで学んだことを、ここで説明したテクニックと組み合わせて活用できます。

<!-- 
### Use in CSS
 -->

### CSS での使用

<!-- 
There are times when you might need to reference the generated CSS custom properties directly in CSS, such as your `style.css` file. To do this, you must use the CSS custom property name.
 -->

生成された CSS カスタム・プロパティを、あなたの `style.css` ファイルなどの CSS 内で直接参照する必要が、生じる場合があります。これを行うには、CSS カスタム・プロパティ名を使用する必要があります。

<!-- 
Suppose you needed to target a class with the name of `.example-class` and to give it the `sm` line-height that you’ve registered. Use this code in your CSS:
 -->

`.example-class` という名称のクラスを対象とし、登録済みの `sm` 行高を適用する必要があるとしましょう。あなたの CSS で、次のコードを使用してください:

```css
.example-class {
	line-height: var( --wp--custom--line-height--sm );
}
```