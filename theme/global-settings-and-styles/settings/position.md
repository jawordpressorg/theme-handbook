<!-- 
# Position
 -->

# 位置

<!-- 
The `settings.position` property in `theme.json` gives you control over the global positioning settings for blocks in WordPress. It’s important to note that this lets you configure the available settings in the user interface, not the position styles.
 -->

`theme.json` 内の `settings.position` プロパティを使用すると、WordPress でのブロックのグローバルな配置設定を制御できます。重要な注意点として、これは UI で利用可能な設定を構成するものであり、配置スタイルそのものを変更するものではありません。

<!-- 
## Position settings
 -->

## 位置の設定

<!-- 
`position` is an object that’s nested directly within the top-level `settings` property in `theme.json`. Currently, it only lets you set a single property: 
 -->

`position` は、`theme.json` のトップレベル `settings` プロパティ内に直接ネストされたオブジェクトです。現在、設定できるプロパティは1つだけです:

<!-- 
*   **`sticky`:** A boolean value for enabling block support for the **Position: Sticky** option.
 -->

*   **`sticky`:** **位置: 貼り付き** オプションのブロックサポートを有効にするための、真偽値です。

<!-- 
Take a look at the `position` property in the context of a `theme.json` file with its default values:
 -->

`theme.json` ファイルのコンテキストにおける `position` プロパティとそのデフォルト値を確認してみましょう:

```json
{
	"version": 2,
	"settings": {
		"position": {
			"sticky": false
		}
	}
}
```

<!-- 
### Enabling sticky positioning
 -->

### 貼り付き配置の有効化

<!-- 
Sticky positioning can be particularly useful in theme designs that feature a header that sticks to the top of the screen as the user scrolls down the page. This is one of the primary use cases, but it can also be useful in other scenarios.
 -->

貼り付き配置は、ユーザーがページを下にスクロールしても、ヘッダーが画面上部に固定されるようなテーマ・デザインにおいて特に有用です。これは主な使用例の一つですが、他のシナリオでも有用な場合があります。

<!-- 
Setting a block to the sticky position will stick the block to its most immediate parent when the user scrolls the page. Sticky positioning is only possible if enabled in `theme.json`.
 -->

ブロックを貼り付き配置に設定すると、ユーザーがページをスクロールした際に、そのブロックは最も近い親要素に固定されます。貼り付き配置は、`theme.json` で有効化されている場合にのみ利用可能です。

<!-- 
To enable sticky positioning for blocks that support it, set `settings.position.sticky` to `true`:
 -->

貼り付き配置をサポートするブロックで、貼り付き配置を有効にするには、`settings.position.sticky` を `true` に設定します:

```json
{
	"version": 2,
	"settings": {
		"position": {
			"sticky": true
		}
	}
}
```

<!-- 
This will enable a new **Position** tab in the block inspector controls (for blocks that support the position feature, such as Group). The control will show a dropdown select with the available position options: **Default** and **Sticky**:
 -->

これにより、(「グループ」など、位置機能をサポートするブロックの場合) ブロック・インスペクタ・コントロールに新しい **位置** タブが表示されます。コントロールには、利用可能な位置オプションのドロップダウンが表示されます: **デフォルト** と **貼り付き**:

<!-- 
[![WordPress site editor with the Header template part selected. In the right sidebar, the Sticky option is selected for the Position setting.](https://i0.wp.com/developer.wordpress.org/files/2023/10/position-sticky-header.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/position-sticky-header.jpg?ssl=1)
 -->

[![「ヘッダー」テンプレート・パーツが選択された、WordPress サイト・エディター。右サイドバーでは、「位置」設定の「貼り付き」オプションが選択されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/position-sticky-header.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/position-sticky-header.jpg?ssl=1)

<!-- 
If you want to create a sticky header, note that you cannot use positioning on the Header template part. You must wrap it with a containing Group block and apply the sticky positioning to the Group.
 -->

貼り付きヘッダーを作成する場合、「ヘッダー」テンプレート・パーツに配置設定を適用できない点に注意してください。「グループ」ブロックで必ず囲み、「グループ」に貼り付き配置を設定する必要があります。