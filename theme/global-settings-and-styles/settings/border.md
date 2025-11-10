<!-- 
# Border
 -->

# 枠線

<!-- 
The `settings.border` property in `theme.json` gives you control over the global border settings for blocks in WordPress. It’s important to note that this lets you configure the available settings in the user interface, not the border styles themselves.
 -->

`theme.json` 内の `settings.border` プロパティを使用すると、WordPress のブロックにおける、グローバルな枠線の設定を制御できます。重要な注意点として、これは UI で利用可能な設定を構成するものであり、枠線のスタイル自体を設定するものではありません。

<!-- 
Each of the border settings maps to a control at the individual block level and in the **Styles** interface for blocks, letting you curate which controls are available to your theme users:
 -->

各枠線の設定は、個々のブロック・レベルおよびブロックの **スタイル** インターフェース内のコントロールに対応し、あなたのテーマ・ユーザーが利用可能なコントロールを管理できるようにします:

<!-- 
[![WordPress post editor showing a Post Featured Image block with custom border settings.](https://i0.wp.com/developer.wordpress.org/files/2023/10/border-settings.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/border-settings.jpg?ssl=1)
 -->

[![カスタム枠線設定が適用された「投稿の注目画像」ブロックを表示している、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/border-settings.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/border-settings.jpg?ssl=1)

<!-- 
## Border settings
 -->

## 枠線設定

<!-- 
WordPress supports four border settings that you can configure via the `settings.border` property in `theme.json`. Each of them allows you to enable or disable a specific border feature and accepts a boolean (`true` or `false`) value:
 -->

WordPress は、`theme.json` 内の `settings.border` プロパティを通して設定可能な、4つの枠線設定をサポートしています。各設定では特定の枠線機能を有効化または無効化でき、真偽値 (`true` または `false`) を受け付けます:

<!-- 
*   **`color`:** Enables/Disables the border-color picker.
*   **`radius`:** Enables/Disables the border-radius control.
*   **`style`:** Enables/Disables the border-style selector (users have the option of `solid`, `dashed`, or `dotted`).
*   `**width**`: Enables/Disables the border-width input.
 -->

*   **`color`:** 枠線のカラー・ピッカーを有効/無効にします。
*   **`radius`:** 枠線の角丸コントロールを有効/無効にします。
*   **`style`:** 枠線のスタイル選択機能を有効/無効にします (ユーザーは `solid`、`dashed`、`dotted` から選択可能)。
*   **`width`:** 枠線の幅入力機能を有効/無効にします。

<!-- 
By default, all border properties are set to `false`, as shown in this example `theme.json` code:
 -->

この `theme.json` サンプルコードに示すように、デフォルトでは、すべての枠線プロパティは `false` に設定されています:

```json
{
	"version": 2,
	"settings": {
		"border": {
			"color": false,
			"radius": false,
			"style": false,
			"width": false
		}
	}
}
```

<!-- 
As of WordPress 6.3, `color`, `style`, and `width` are intertwined. If any one of them is set to `true`, the others will be available as options within the user interface.
 -->

WordPress 6.3 以降、`color`、`style`、`width` は相互に関連付けられています。いずれか一つが `true` に設定されている場合、他のオプションも UI 内で利用可能になります。

<!-- 
Also, setting the `radius` option to `false` does not work for the Button block. The border-radius control in the editor always appears.
 -->

また、`radius` オプションを `false` に設定しても、「ボタン」ブロックでは機能しません。エディター内の枠線の角丸制御は、常に表示されます。