<!-- 
# Dimensions
 -->

# 寸法

<!-- 
The `settings.dimensions` property in `theme.json` gives you control over the global dimensions settings for blocks. This property lets you decide which dimension controls are available in the user interface.
 -->

`theme.json` 内の `settings.dimensions` プロパティを使用すると、ブロックのグローバルな寸法の設定を制御できます。このプロパティにより、UI で利用可能な寸法コントロールを決定できます。

<!-- 
In this document, you will learn what the `dimensions` property is for and how you can use it in your theme.
 -->

本ドキュメントでは、`dimensions` プロパティの目的と、あなたのテーマでどのように使用できるかを学びます。

<!-- 
## Dimensions settings
 -->

## 寸法の設定

<!-- 
`dimensions` is an object that’s nested directly within the top-level `settings` property in `theme.json`. Currently, it only lets you set a single property: 
 -->

`dimensions` は、`theme.json` のトップレベル `settings` プロパティ内に直接ネストされたオブジェクトです。現在、設定できるプロパティは1つだけです:  

<!-- 
*   **`minHeight`:** A boolean value for enabling block support for the **Minimum Height** control.
 -->

*   **`minHeight`:** **最小の高さ** コントロールのブロック・サポートを有効にする真偽値。

<!-- 
Take a look at the `dimensions` property in the context of a `theme.json` file with its default values:
 -->

`theme.json` ファイルのコンテキストにおける `dimensions` プロパティとそのデフォルト値をみてみましょう:

```json
{
	"version": 2,
	"settings": {
		"dimensions": {
			"minHeight": false
		}
	}
}
```

<!-- 
### Minimum Height
 -->

### 最小の高さ

<!-- 
The `settings.dimensions.minHeight` property lets you control whether the **Minimum Height** field appears for blocks that have opted into support for the feature. As of WordPress 6.3, the only core WordPress blocks that do are Group and Post Content.
 -->

`settings.dimensions.minHeight` プロパティを使用すると、この機能のサポートを有効にしているブロックに対して、**最小の高さ** フィールドを表示するかどうかを制御できます。WordPress 6.3時点では、この機能をサポートしているコア WordPress ブロックは「グループ」と「投稿コンテンツ」のみです。

<!-- 
To enable support for the control, you must set the property’s value to `true` in `theme.json`:
 -->

コントロールのサポートを有効にするには、`theme.json` 内でプロパティの値を `true` に設定する必要があります:

```json
{
	"version": 2,
	"settings": {
		"dimensions": {
			"minHeight": true
		}
	}
}
```

<!-- 
This will enable the control in the interface. As shown in this screenshot, the **Minimum Height** field appears for the Group block (Stack variation):
 -->

これにより、インターフェース内のコントロールが有効になります。このスクリーンショットに示すように、「グループ」ブロック (スタック・バリエーション) に **最小の高さ** フィールドが表示されます:

<!-- 
[![WordPress post editor with a Stack block in the content canvas. Its minimum height is set in the sidebar.](https://i0.wp.com/developer.wordpress.org/files/2023/10/group-min-height.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/group-min-height.jpg?ssl=1)
 -->

[![コンテンツ・キャンバスに「スタック」ブロックが表示された、WordPress 投稿エディター。その最小の高さはサイドバーで設定される。](https://i0.wp.com/developer.wordpress.org/files/2023/10/group-min-height.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/group-min-height.jpg?ssl=1)