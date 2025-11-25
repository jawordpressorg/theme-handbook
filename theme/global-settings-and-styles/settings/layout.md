<!-- 
# Layout
 -->

# レイアウト

<!-- 
The `settings.layout` property in `theme.json` is an object that stores layout-related settings that you can configure. At the moment, it is used for setting “content” and “wide” widths, but it could also be used for other settings in the future.
 -->

`theme.json` 内の `settings.layout` プロパティは、あなたが構成できるレイアウト関連の設定を格納するオブジェクトです。現時点では「コンテンツ」幅と「幅広」幅の設定に使用されていますが、将来的には他の設定にも使用される可能性があります。

<!-- 
In this document, you will learn what the `layout` property is used for and how you can use it in your theme.
 -->

本ドキュメントでは、`layout` プロパティの用途と、あなたのテーマでどのように使用できるかを学びます。

<!-- 
## Layout settings
 -->

## レイアウトの設定

<!-- 
`layout` is an object that’s nested directly within the top-level `settings` property in `theme.json`. Within that object, you can define two settings:
 -->

`layout` は、`theme.json` のトップレベル `settings` プロパティ内に直接ネストされたオブジェクトです。このオブジェクト内では、次の2つの設定を定義できます:

<!-- 
*   `**contentSize**`: A valid CSS length value for defining the default width for content. It is typically used for controlling the width of the post content and related areas on the page.
*   **`wideSize`:** A valid CSS length value for defining the default wide alignment width, which is generally between the content size and full viewport width.
 -->

*   `**contentSize**`: コンテンツのデフォルト幅を定義するための、CSS の有効な長さの値で、通常、ページ上の投稿コンテンツや関連エリアの幅を制御するために使用されます。
*   **`wideSize`:** デフォルトの幅広の配置幅を定義するための、CSS の有効な長さの値で、通常、コンテンツ幅とビュー・ポートの全幅の間になります。

<!-- 
Take a look at the `layout` property in the context of a `theme.json` file with its default values:
 -->

`theme.json` ファイルのコンテキストにおける `layout` プロパティとそのデフォルト値をみてみましょう:

```json
{
	"version": 2,
	"settings": {
		"layout": {
			"contentSize": "",
			"wideSize": ""
		}
	}
}
```

<!-- 
### Content size
 -->

### コンテンツ幅

<!-- 
The `settings.layout.contentSize` property is primarily useful for defining the width of a site’s content area. Think of this as the default width of your site. You can break outside of this by applying the “wide” (below) or “full” width to a block. The content width is merely the foundation.
 -->

`settings.layout.contentSize` プロパティは、主にサイトのコンテンツ・エリアの幅を定義するために役立ちます。これはあなたのサイトのデフォルトの幅と考えてください。ブロックに「幅広」(下記) または「全幅」を適用することで、この幅を超えることができます。コンテンツの幅は、単なる基礎に過ぎません。

<!-- 
In almost any design, you will want to limit this width to something that is comfortable to read, especially if the content is going to include text. This is a value that you will need to determine for yourself, but a good rule of thumb is that you should have 45-75 characters of text per line (though some guidelines differ slightly on the number range). Of course, your default font-family and font-size are crucial pieces to figuring this out.
 -->

ほとんどのデザインにおいて、特にテキストを含むコンテンツの場合は、読みやすい範囲にこの幅を制限したいところでしょう。この値はあなたが自ら決定する必要がありますが、目安として1行あたり45～75文字のテキストを目安とすると良いでしょう (ただしガイドラインによって、数値範囲が若干異なる場合もある)。もちろん、あなたのデフォルトのフォント・ファミリーとフォント・サイズは、これを決定するうえで重要な要素となります。

<!-- 
Try configuring a content size in your `theme.json` file:
 -->

あなたの `theme.json` ファイルで、コンテンツ幅を指定してみましょう:

```json
{
	"version": 2,
	"settings": {
		"layout": {
			"contentSize": "40rem"
		}
	}
}
```

<!-- 
If you open a template in the **Site Editor**, you can use it to define the layout for various blocks. In the screenshot below, you can see that the Post Content block has the **Inner blocks use content width** option selected under the **Layout** tab:
 -->

**サイト・エディター** でテンプレートを開くと、さまざまなブロックのレイアウトを定義できます。以下のスクリーンショットでは、「投稿コンテンツ」ブロックの **レイアウト** タブで、**コンテンツ幅を使用するインナー・ブロック** オプションが選択されていることが確認できます:

<!-- 
[![WordPress post editor with a Post Content block selected, showing its inner content limited to the content width.](https://i0.wp.com/developer.wordpress.org/files/2023/10/content-size.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/content-size.jpg?ssl=1)
 -->

[![コンテンツ幅に制限された内部コンテンツを表示する、「投稿コンテンツ」ブロックが選択された WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/content-size.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/content-size.jpg?ssl=1)

<!-- 
What this setting does is tell WordPress that any nested blocks within the Post Content block should be set to the `40rem` value defined for `settings.layout.contentSize` in `theme.json`.
 -->

この設定は、「投稿コンテンツ」ブロック内のネストされたブロックはすべて、`theme.json` で `settings.layout.contentSize` に定義された `40rem` 値にセットされるよう WordPress に指示します。

<!-- 
### Wide Size
 -->

### 幅広

<!-- 
The `settings.layout.wideSize` property defines a width for “wide” blocks. To be useful, wide blocks must be nested within a block that is telling WordPress that its inner blocks should be limited to the “content” size. Wide-aligned blocks are meant to “break outside” of their parent block.
 -->

`settings.layout.wideSize` プロパティは、「ワイド」ブロックの幅を定義します。ワイドブロックが機能するためには、WordPress に内部ブロックを「コンテンツ」サイズに制限するよう指示するブロック内にネストされている必要があります。ワイド配置ブロックは、親ブロックの枠を「はみ出す」ように設計されています。

<!-- 
Not every theme will benefit by having a wide size. Depending on the design, a theme’s layout may simply not have additional room for blocks to break out of their container. In those cases, you do not need to set this value.
 -->

すべてのテーマが、幅広サイズでメリットを得るわけではありません。デザインによっては、テーマのレイアウト上、ブロックがコンテナから飛び出す余地が単純にない場合があります。そのような場合、この値を設定する必要はありません。

<!-- 
For theme designs that can accommodate wide blocks (typical of sidebar-less designs), you will want to set this to a value that is greater than `settings.layout.contentWidth`. But it shouldn’t stretch to the width of the full screen (e.g., `100vw`). WordPress has a separate full-width setting that you can use for that.
 -->

(サイドバーのないデザインに典型的な) 幅広のブロックに対応できるテーマデザインの場合、この値を `settings.layout.contentWidth` よりも大きく設定する必要があります。ただし、画面全体の幅 (例: `100vw`) まで拡大すべきではありません。WordPress には、その目的で使用できる別の全幅設定があります。

<!-- 
Try adding a custom `settings.layout.wideSize` to your `theme.json` file (remember, you need a set content size for this to be useful):
 -->

カスタム設定 `settings.layout.wideSize` を あなたの `theme.json` ファイルに追加してみましょう (この設定を活用するには、コンテンツ幅を設定する必要があることに注意):

```json
{
	"version": 2,
	"settings": {
		"layout": {
			"contentSize": "40rem",
			"wideSize": "64rem"
		}
	}
}
```

<!-- 
Now open your **Site Editor** in the WordPress admin and edit a template. First, add a **Group** block with the **Inner blocks use content width** option enabled. Then, stick another block within it and select the **Wide width** option.
 -->

では、あなたの WordPress 管理画面で **サイト・エディター** を開き、テンプレートを編集してみましょう。まず、**「グループ」**ブロックを追加し、**コンテンツ幅を使用するインナー・ブロック** オプションを有効にします。次に、その中に別のブロックを配置し、**幅広** オプションを選択します。

<!-- 
In the screenshot below, you can see the Post Featured Image block nested within a Group block. It breaks out of its parent container but the other post-related blocks are limited to the content width:
 -->

以下のスクリーンショットでは、「グループ」ブロック内にネストされた「アイキャッチ画像」ブロックを確認できます。このブロックは親コンテナから飛び出しますが、他の投稿関連ブロックは、コンテンツ幅に制限されます:

<!-- 
[![WordPress site editor with the Post Featured Image block selected and set to "wide width".](https://i0.wp.com/developer.wordpress.org/files/2023/10/wide-size.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/wide-size.jpg?ssl=1)
 -->

[![「投稿の注目画像」ブロックが選択され、「幅広」に設定された WordPress サイト・エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/wide-size.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/wide-size.jpg?ssl=1)