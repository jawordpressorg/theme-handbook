<!-- 
# Lightbox
 -->

# ライトボックス

<!-- 
`settings.lightbox` is a specific setting that you can enable for supported blocks. It enables a lightbox feature that expands an image when a site visitor clicks on an image.
 -->

`settings.lightbox` は、対応するブロックに対して有効にできる、特定の設定です。この設定を有効にすると、サイト訪問者が画像をクリックした際に画像を拡大表示するライトボックス機能が有効になります。

<!-- 
This setting is only available as of WordPress 6.4 and is specific to the core Image block (`core/image`).
 -->

この設定は WordPress 6.4以降でのみ利用可能であり、コアの「画像」ブロック (`core/image`) に固有のものです。

<!-- 
## Lightbox settings
 -->

## ライトボックスの設定

<!-- 
The `lightbox` setting is specific to the Image block, so the following examples will be shown in that context.
 -->

`lightbox` 設定は画像ブロック固有のものです。したがって、以下の例はその文脈で示されます。

<!-- 
The `lightbox` property is an object that has two nested properties that you can configure:
 -->

`lightbox` プロパティはオブジェクトで、設定可能な2つのネストされたプロパティを持ちます:

<!-- 
*   **`enabled`:** Whether to enable the lightbox feature for the Image block. The default value is `undefined` (the equivalent of being disabled).
*   **`allowEditing`:** Whether to show the **Expand on click** option in the interface, which allows the user to enable/disable lightbox for individual images. Defaults to `true`.
 -->

*   **`enabled`:** 「画像」ブロックのライトボックス機能を有効にするか否かです。デフォルト値は `undefined` (無効と同等) です。
*   **`allowEditing`:** インターフェースに **クリックで展開** オプションを表示するかどうかです。これにより、ユーザーは個々の画像に対してライトボックスを有効/無効にできます。デフォルトは `true` です。

<!-- 
Here is a look at the default `theme.json`:
 -->

デフォルトの `theme.json` は、以下の通りです:

```json
{
	"version": 2,
	"settings": {
		"blocks": {
			"core/image": {
				"lightbox": {
					"allowEditing": true
				}
			}
		}
	}
}
```

<!-- 
### Enabling lightbox for images
 -->

### 画像のライトボックスの有効化

<!-- 
To enable the lightbox feature for Image blocks used throughout the site, you must set `settings.blocks.core/image.lightbox.enabled` to true in `theme.json`:
 -->

サイト全体で使用される「画像」ブロックのライトボックス機能を有効にするには、`theme.json` 内で `settings.blocks.core/image.lightbox.enabled` を true に設定する必要があります:

```json
{
	"version": 2,
	"settings": {
		"blocks": {
			"core/image": {
				"lightbox": {
					"enabled": true
				}
			}
		}
	}
}
```

<!-- 
On the front-end of the site, visitors will be able to expand the image when clicking on it. The image will then overlay the entire screen (including an **x** button for closing the overlay), as shown below:
 -->

サイトのフロントエンドでは、訪問者が画像をクリックすると、その画像を拡大表示できます。拡大された画像は画面全体にオーバーレイ表示され (オーバーレイを閉じるための **x** ボタンを含む)、以下のように表示されます:

<!-- 
[![Image of palm trees expanded as an overlay modal.](https://i0.wp.com/developer.wordpress.org/files/2023/10/lightbox-expanded.jpg?resize=2048%2C959&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/lightbox-expanded.jpg?ssl=1)
 -->

[![ヤシの木の画像が、オーバーレイ・モーダルとして拡大表示された状態。](https://i0.wp.com/developer.wordpress.org/files/2023/10/lightbox-expanded.jpg?resize=2048%2C959&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/lightbox-expanded.jpg?ssl=1)

<!-- 
### Disabling user editing
 -->

### ユーザー編集の無効化

<!-- 
By default, WordPress will show an **Expand on Click** option under the **Settings** tab for the Image block:
 -->

デフォルトでは、WordPress は「画像」ブロックの **設定** タブに **クリックで展開** オプションを表示します:

<!-- 
[![WordPress post editor with an Image block showing the "expand on click" option selected.](https://i0.wp.com/developer.wordpress.org/files/2023/10/lightbox-allow-editing.jpg?resize=2048%2C1056&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/lightbox-allow-editing.jpg?ssl=1)
 -->

[![「画像」ブロックに「クリックで展開」オプションが選択されている、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/lightbox-allow-editing.jpg?resize=2048%2C1056&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/lightbox-allow-editing.jpg?ssl=1)

<!-- 
This control allows your theme’s users to enable or disable the lightbox feature on a per-block basis.
 -->

このコントロールにより、あなたのテーマのユーザーは、ブロック単位でライトボックス機能を有効化または無効化できます。

<!-- 
To disallow user editing, you must set `settings.blocks.core/image.lightbox.allowEditing` to `false` in `theme.json`:
 -->

ユーザー編集を無効化するには、`theme.json` 内で `settings.blocks.core/image.lightbox.allowEditing` を `false` に設定する必要があります:

```json
{
	"version": 2,
	"settings": {
		"blocks": {
			"core/image": {
				"lightbox": {
					"allowEditing": false
				}
			}
		}
	}
}
```