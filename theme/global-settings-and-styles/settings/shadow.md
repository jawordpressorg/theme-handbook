<!-- 
# Shadow
 -->

# シャドウ

<!-- 
The `settings.shadow` property in `theme.json` currently lets you create custom shadow presets. As of WordPress 6.3, it contains no settings for enabling or disabling UI elements.
 -->

`theme.json` 内の `settings.shadow` プロパティは、現在、カスタム・シャドウ・プリセットの作成を可能にします。WordPress 6.3時点では、UI 要素の有効化または無効化に関する設定は含まれていません。

<!-- 
Shadow, in this case, refers specifically to the `box-shadow` CSS feature and is unrelated to `text-shadow`.
 -->

この場合、シャドウとは、特に `box-shadow` CSS 機能を指し、`text-shadow` とは無関係です。

<!-- 
## Shadow settings
 -->

## Shadow の設定

<!-- 
The `settings.shadow` property contains two settings that you can configure:
 -->

`settings.shadow` プロパティには、設定可能な2つの設定が含まれています:

<!-- 
*   **`defaultPresets`:** A boolean value for enabling or disabling the default WordPress shadow presets. Defaults to `true`.
*   `**presets**`: An array of objects for registering custom shadows for use in your theme or by users.
 -->

*   **`defaultPresets`:** WordPress のデフォルト・シャドウ・プリセットを、有効化または無効化するための、真偽値です。デフォルトは `true` です。
*   `**presets**`: あなたのテーマで使用するための、またはユーザーが使用するためのカスタム・シャドウを登録するための、オブジェクトの配列です。

<!-- 
Here is a look at the default shadow property in `theme.json`:
 -->

以下は `theme.json` 内のデフォルト・シャドウ・プロパティの概要です:

```json
{
	"version": 2,
	"settings": {
		"shadow": {
			"defaultPresets": true,
			"presets": [
				{
					"name": "Natural",
					"slug": "natural",
					"shadow": "6px 6px 9px rgba(0, 0, 0, 0.2)"
				},
				{
					"name": "Deep",
					"slug": "deep",
					"shadow": "12px 12px 50px rgba(0, 0, 0, 0.4)"
				},
				{
					"name": "Sharp",
					"slug": "sharp",
					"shadow": "6px 6px 0px rgba(0, 0, 0, 0.2)"
				},
				{
					"name": "Outlined",
					"slug": "outlined",
					"shadow": "6px 6px 0px -3px rgba(255, 255, 255, 1), 6px 6px rgba(0, 0, 0, 1)"
				},
				{
					"name": "Crisp",
					"slug": "crisp",
					"shadow": "6px 6px 0px rgba(0, 0, 0, 1)"
				}
			]
		}
	}
}
```

<!-- 
As you can see, WordPress registers several default presets that you can use directly in your block styles or that users can select from the interface:
 -->

ご覧の通り、WordPress ではいくつかのデフォルト・プリセットが登録されており、あなたのブロック・スタイルで直接使用できるほか、ユーザーがインターフェースから選択できます:

<!-- 
*   Natural
*   Deep
*   Sharp
*   Outline
*   Crisp
 -->

*   Natural
*   Deep
*   Sharp
*   Outline
*   Crisp

<!-- 
Like all presets, WordPress will generate a CSS custom property for each registered shadow. Shadow presets are named `--wp--preset--shadow--{$slug}`.
 -->

他のプリセットと同様に、WordPress は各登録シャドウに対して、CSS カスタム・プロパティを生成します。シャドウ・プリセットの名前は、`--wp--preset--shadow--{$slug}` になります。

<!-- 
Here is an example of the CSS generated for the default shadow presets:
 -->

以下は、デフォルト・シャドウ・プリセット用に生成された、CSS の例です:

```css
body {
	--wp--preset--shadow--natural: 6px 6px 9px rgba(0, 0, 0, 0.2);
	--wp--preset--shadow--deep: 12px 12px 50px rgba(0, 0, 0, 0.4);
	--wp--preset--shadow--sharp: 6px 6px 0px rgba(0, 0, 0, 0.2);
	--wp--preset--shadow--outlined: 6px 6px 0px -3px rgba(255, 255, 255, 1), 6px 6px rgba(0, 0, 0, 1);
	--wp--preset--shadow--crisp: 6px 6px 0px rgba(0, 0, 0, 1);
}
```

<!-- 
## Disabling core WordPress shadows
 -->

## WordPress のコア・シャドウの無効化

<!-- 
The default shadows available in core will not match the design of every theme. Typically, they will only work well for themes with a white or very light gray background. If your theme uses a different color, you will almost always want to remove these.
 -->

コアで利用可能なデフォルト・シャドウは、すべてのテーマのデザインに適合するわけではありません。通常、これらは背景が白または非常に薄いグレーのテーマでのみ適切に機能します。あなたのテーマが他の色を使用している場合、ほとんどの場合、これらを削除することをおすすめします。

<!-- 
But there may be other reasons to disable the defaults. Perhaps you want to limit users to only the shadows that you’ve specifically designed for your theme or simply not like their design.
 -->

ただし、デフォルト設定を無効にする理由は、他にもあるかもしれません。たとえば、あなたのテーマ用に特別にデザインしたシャドウのみをユーザーに使用させたい場合や、単にそのデザインが気に入らない場合などが考えられます。

<!-- 
Whatever the reason, you can remove them by setting `settings.shadow.defaultPresets` to `false` in `theme.json`:
 -->

理由が何であれ、`theme.json` で `settings.shadow.defaultPresets` を `false` に設定することで、削除できます:

```json
{
	"version": 2,
	"settings": {
		"shadow": {
			"defaultPresets": false
		}
	}
}
```

<!-- 
## Adding custom shadow presets
 -->

## カスタム・シャドウ・プリセットの追加

<!-- 
WordPress lets you register any number of custom shadows. You can add them via the `settings.shadow.presets` property, which is an array used for storing shadow objects. Each object in this array should contain three values:
 -->

WordPress では、任意の数だけカスタム・シャドウを登録できます。`settings.shadow.presets` プロパティを介してそれらを追加でき、本プロパティはシャドウ・オブジェクトを格納するための配列として使用されます。本配列内の各オブジェクトは、以下の3つの値を含む必要があります:

<!-- 
*   **`name`:** A human-readable name or label for the shadow that can be translated.
*   **`slug`:** A machine-readable slug for the shadow, which is used to build its associated CSS  custom property.
*   **`shadow`:** A valid CSS value for the `box-shadow` CSS property.
 -->

*   **`name`:** 翻訳可能で人間可読な、名前またはラベルです。
*   **`slug`:** 機械可読な、スラッグです。関連する CSS カスタム・プロパティの構築に使用されます。
*   **`shadow`:** `box-shadow` CSS プロパティの有効な CSS 値です。

<!-- 
Try your hand at registering a few shadows of your own. You can use this `theme.json` code to get started, which contains several shadow examples:
 -->

ご自身でいくつかのシャドウを登録してみましょう。この `theme.json` コードを使用して開始できます。これにはいくつかのシャドウの例が含まれています:

```json
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2,
	"settings": {
		"shadow": {
			"presets": [
				{
					"name": "Small",
					"slug": "sm",
					"shadow": "0 1px 2px 0 rgb(0 0 0 / 0.05)"
				},
				{
					"name": "Medium",
					"slug": "md",
					"shadow": "0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1)"
				},
				{
					"name": "Large",
					"slug": "lg",
					"shadow": "0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1)"
				},
				{
					"name": "XL",
					"slug": "xl",
					"shadow": "0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1)"
				},
				{
					"name": "2XL",
					"slug": "2-xl",
					"shadow": "0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1)"
				},
				{
					"name": "Inner",
					"slug": "inner",
					"shadow": "inset 0 2px 4px 0 rgb(0 0 0 / 0.05)"
				}
			]
		}
	}
}
```

<!-- 
Currently, this only shows a shadow option for the core Button block in the user interface. This control can be accessed via  **Appearance > Editor > Styles > Style Book** in the WordPress admin. From there, select the **Button** block and locate the **Shadow** option in the **Effects** tab, as shown here:
 -->

現在、これは、UI 内のコア「ボタン」ブロックに対して、シャドウ・オプションのみを表示するようになっています。この設定は、WordPress 管理画面の **外観 > エディター > スタイル > スタイル・ブック** からアクセスできます。そこから **「ボタン」** ブロックを選択し、**エフェクト** タブ内の **シャドウ** オプションを探してください。以下のように表示されます:

<!-- 
[![WordPress Style Book screen with the Button block highlighted. It has a gray drop-shadow.](https://i0.wp.com/developer.wordpress.org/files/2023/10/shadow-ui-buttons.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/shadow-ui-buttons.jpg?ssl=1)
 -->

[![「ボタン」ブロックが強調表示された、WordPress スタイル・ブック画面。灰色のドロップシャドウが付いている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/shadow-ui-buttons.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/shadow-ui-buttons.jpg?ssl=1)

<!-- 
It’s possible for third-party blocks to also utilize shadow presets and show them in the interface in the post, template, or site editors.
 -->

サードパーティ製ブロックもシャドウ・プリセットを利用し、投稿、テンプレート、サイトエディターのインターフェースに表示できます。

<!-- 
Like other presets, you can also use your custom shadows (or core WordPress shadows) in [`theme.json` Styles](https://developer.wordpress.org/themes/global-settings-and-styles/styles).
 -->

他のプリセットと同様に、あなたのカスタム・シャドウ (または WordPress のコア・シャドウ) も [`theme.json` スタイル](https://developer.wordpress.org/themes/global-settings-and-styles/styles) で使用できます。

<!-- 
For a deeper dive into this feature, read [Using the box-shadow feature for themes](https://developer.wordpress.org/news/2023/01/using-the-box-shadow-feature-for-themes/) on the WordPress Developer Blog.
 -->

この機能についてさらに詳しく知りたい場合は、WordPress 開発者ブログの [テーマにおけるボックス・シャドウ機能の使い方](https://developer.wordpress.org/news/2023/01/using-the-box-shadow-feature-for-themes/) をご覧ください。