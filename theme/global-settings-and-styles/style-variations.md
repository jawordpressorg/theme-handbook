<!-- 
# Style Variations
 -->

# スタイル・バリエーション

<!-- 
Unlike most things here in the Global Settings and Styles documentation, style variations are not things you define within `theme.json`. Instead, they are “variations” to your existing `theme.json` file that you can offer to users.
 -->

「グローバル設定とスタイル」ドキュメントのほとんどの項目とは異なり、スタイル・バリエーションは `theme.json` 内で定義するものではありません。代わりに、これらはあなたの既存の `theme.json` ファイルに対する「バリエーション」であり、ユーザーに提供できるものです。

<!-- 
A more accurate name for this feature might be *Global Settings and Styles Variations*. Or simply `theme.json` variations.
 -->

この機能のより正確な名称は、*グローバル設定とスタイル・バリエーション* とすべきかもしれません。あるいは単に `theme.json` のバリエーションかもしれません。

<!-- 
## What are style variations?
 -->

## スタイル・バリエーションって ?

<!-- 
Style variations are essentially alternative versions of `theme.json` that you can ship with your theme. They are custom-named JSON files that are stored in your theme’s `/styles` folder. Any [setting](https://developer.wordpress.org/themes/global-settings-and-styles/settings) or [style](https://developer.wordpress.org/themes/global-settings-and-styles/styles) that you can add to `theme.json` can also be added to your style variation JSON file.
 -->

スタイル・バリエーションは、基本的にあなたのテーマに同梱できる `theme.json` の代替バージョンです。これらはあなたのテーマの `/styles` フォルダーに保存される、カスタム名で命名された JSON ファイルです。`theme.json` に追加できる [設定](https://developer.wordpress.org/themes/global-settings-and-styles/settings) や [スタイル](https://developer.wordpress.org/themes/global-settings-and-styles/styles) は、あなたのスタイル・バリエーション JSON ファイルにも追加できます。

<!-- 
This lets your users pick and choose which variation they want to use on their site. In a way, they are “skins” for your theme.
 -->

これにより、あなたのユーザーは自身のサイトで使用したいバリエーションを選択できます。ある意味で、これらはあなたのテーマの「スキン」のようなものです。

<!-- 
For example, suppose you’ve created a restaurant theme and have kept the colors and typography pretty basic so that it covers a lot of different restaurant site designs. Further suppose that you wanted to offer more variety, variations on that initial design. You could create a style variation that caters more toward seafood restaurants with fun fonts and an ocean-oriented color palette. Or maybe you want to set the mood for coffee shops that might be running your theme.
 -->

たとえば、レストラン・テーマを制作し、色やタイポグラフィをかなりシンプルに保った場合、さまざまなレストラン・サイトのデザインに対応できます。さらに、その初期デザインにバリエーションを加え、より多くの選択肢を提供したいとしましょう。シーフード・レストラン向けに、遊び心のあるフォントと海を連想させるカラーパレットを用いたスタイル・バリエーションも制作できます。あるいは、あなたのテーマを採用する可能性のある、コーヒーショップの雰囲気を演出したい場合もあるでしょう。

<!-- 
That’s where style variations can really shine. You can bundle each of these alternative designs for your theme and let your users decide which is the best option for their site.
 -->

そこでスタイル・バリエーションが真価を発揮します。あなたのテーマ用に用意したこれらの代替デザインをそれぞれバンドルし、あなたのユーザーが自身のサイトに最適な選択肢を決められるようにできます。

<!-- 
Here is a look at the style variations that are bundled with the default Twenty Twenty-Three theme:
 -->

デフォルトの Twenty Twenty-Three テーマにバンドルされている、スタイル・バリエーションを紹介します:

<!-- 
[![WordPress Site Editor > Styles sub-screen, which is showing a grid of style variations with a red one in the preview panel.](https://i0.wp.com/developer.wordpress.org/files/2023/09/tt3-style-variations.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/tt3-style-variations.jpg?ssl=1)
 -->

[![プレビューパネルに赤いスタイルが表示されている、スタイル・バリエーションのグリッドが表示されている、WordPress サイトエディター > スタイル サブ画面。](https://i0.wp.com/developer.wordpress.org/files/2023/09/tt3-style-variations.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/tt3-style-variations.jpg?ssl=1)

<!-- 
When a user selects a style variation, the JSON data is migrated to the site’s database and stored as a user customization. This allows the data to overrule the theme’s primary `theme.json` settings and styles.
 -->

ユーザーがスタイル・バリエーションを選択すると、JSON データがサイトのデータベースに移行され、ユーザー・カスタマイズとして保存されます。これにより、データがテーマの主要な `theme.json` 設定やスタイルを上書きできます。

<!-- 
## Adding custom style variations
 -->

## カスタム・スタイル・バリエーションの追加

<!-- 
The style variations feature is relatively straightforward if you already understand how `theme.json` works, but there are a couple of differences.
 -->

スタイル・バリエーション機能は、`theme.json` のしくみを理解していれば比較的単純ですが、違いがいくつかあります。

<!-- 
The first difference between `theme.json` and style variations are their names and placement in your theme’s folder structure. `theme.json` lives in the root of your theme folder and is considered the default variation. But custom variations must have a unique filename and be placed in the `/styles` folder.
 -->

`theme.json` とスタイル・バリエーションの最初の違いは、それらの名称とあなたのテーマフォルダー構造内での配置です。`theme.json` はあなたのテーマフォルダーのルートに存在し、デフォルトのバリエーションとみなされます。しかしカスタム・バリエーションは一意のファイル名を持ち、`/styles` フォルダー内に必ず配置する必要があります。

<!-- 
Let’s assume you’ve built that restaurant theme mentioned earlier in this document. Now you want to add a couple of variations named Swashbuckler (for that seafood design) and Latte (for the coffee shop design). This is how your theme files would be organized:
 -->

本ドキュメントで前述したレストラン・テーマを、構築したと仮定しましょう。では、(シーフード・デザイン向け) Swashbuckler と、(コーヒーショップ・デザイン向け) Latte という2つのバリエーションを追加したいとします。あなたのテーマファイルは、以下のように構成されるでしょう:

```
/your-theme-folder
	/styles
		/latte.json
		/swashbuckler.json
	/theme.json
```

<!-- 
Style variations are simply variations of `theme.json`, so you have full access to everything in the `theme.json` specification at your fingertips. 
 -->

スタイル・バリエーションは単に `theme.json` のバリエーションであるため、`theme.json` 仕様のあらゆる要素を自由に操作できます。

<!-- 
The second difference between `theme.json` and style variations is the variation title. You can configure this by adding the `title` property to your custom JSON files.
 -->

`theme.json` とスタイル・バリエーションの2つ目の違いは、バリエーションのタイトルです。あなたのカスタム JSON ファイルに `title` プロパティを追加することで、これを設定できます。

<!-- 
Building off the Latte variation example above, you would open your `/styles/latte.json` file and add it, as shown in this code snippet:
 -->

上の Latte バリエーションの例をもとに、`/styles/latte.json` ファイルを開き、以下のコードスニペットのように追加します:

```json
{
	"version": 2,
	"title": "Latte",
	"settings": {},
	"styles": {}
}
```

<!-- 
The `title` field is used to represent your variation in the user interface. It is not a required field (WordPress will fall back to your variation), but it does make for a nicer user experience.
 -->

`title` フィールドは、UI 上であなたのバリエーションを表示するために使用されます。必須フィールドではありません (WordPress はあなたのバリエーションにフォールバックする) が、より良いユーザー体験を提供します。

<!-- 
## Style variations vs. child themes
 -->

## スタイル・バリエーション vs 子テーマ

<!-- 
If you are familiar with the concept of [child themes](https://developer.wordpress.org/themes/advanced-topics/child-themes/), which are covered in the [Advanced Topics](https://developer.wordpress.org/themes/advanced-topics/) documentation, you may be wondering what the differences between them and style variations are.
 -->

[高度なトピック](https://developer.wordpress.org/themes/advanced-topics/) ドキュメントで説明されている、[子テーマ](https://developer.wordpress.org/themes/advanced-topics/child-themes/) の概念を知っている人は、子テーマとスタイル・バリエーションの違いについて疑問に思われるかもしれません。

<!-- 
The most obvious difference is that a style variation is limited to a single JSON file that overrides the primary `theme.json`, whereas a child theme can override anything from its parent theme. So it’s probably better to look at the one area they are similar: the JSON file itself.
 -->

最も明らかな違いは、スタイル・バリエーションはプライマリ `theme.json` を上書きする個別 JSON ファイルに限定されるのに対し、子テーマは親テーマのあらゆる要素を上書きできる点です。したがって、両者が似ている点に注目するほうが適切でしょう: JSON ファイルそのものです。

<!-- 
In a child theme, the `theme.json` simply overrides its parent’s `theme.json` file. In a style variation—and this is where the major difference occurs—the variation’s JSON file overrides the `theme.json` file and **its data is saved to the database**.
 -->

子テーマでは、`theme.json` は親テーマの `theme.json` ファイルを上書きするだけです。スタイル・バリエーションでは — ここが主な違い — バリエーションの JSON ファイルが `theme.json` ファイルを上書きし、**そのデータはデータベースに保存** されます。

<!-- 
Once a user selects a style variation of a theme, everything in the variation’s JSON file is treated as a user customization. Essentially, WordPress stores that **initial** data in the same way as if the user had simply designed the colors, typography, spacing, etc. from the interface. This is an important distinction to make because it means that when you update a style variation in a future theme release, the user will not receive those changes if they have already saved the style variation.
 -->

ユーザーがテーマのスタイル・バリエーションを選択すると、そのバリエーションの JSON ファイル内のすべての設定は、ユーザー・カスタマイズとして扱われます。本質的に、WordPress はその **初期** データを、ユーザーがインターフェースから色、タイポグラフィ、間隔などを直接設定した場合と同様に保存します。これは重要な違いです。なぜなら、将来のテーマリリースでスタイル・バリエーションを更新しても、ユーザーがすでにそのバリエーションを保存している場合、変更は反映されないことを意味するからです。

<!-- 
It is possible for users to switch to a variation and switch back to the one they were using to get the update.
 -->

ユーザーはバリエーションに切り替えてから、更新を取得するために使用していた元のバリエーションに戻すことが可能です。

<!-- 
Style variations can be a great feature to add to your theme, but they have a specific use case. Sometimes child themes make more sense.
 -->

スタイル・バリエーションは、あなたのテーマに追加できる優れた機能ですが、特定の使用例に限定されます。場合によっては、子テーマの方が理に適っていることもあります。