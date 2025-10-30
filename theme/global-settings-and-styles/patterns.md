<!-- 
# Patterns
 -->

# パターン

<!-- 
The `patterns` property in `theme.json` lets you bundle patterns from the WordPress [Pattern Directory](https://wordpress.org/patterns/) with your theme. This is a neat system that lets you provide a wide variety of patterns that you’ve personally selected without having to design and build them yourself. Any pattern in the directory is available to you.
 -->

`theme.json` 内の `patterns` プロパティを使用すると、WordPress の [パターン・ディレクトリ](https://wordpress.org/patterns/) からあなたのテーマにパターンをバンドルできます。これは便利なシステムで、自分でデザインや構築をしなくても、個人的に選んだ多種多様なパターンを提供できます。ディレクトリ内のあらゆるパターンが利用可能です。

<!-- 
[![Screenshot of the WordPress.org Pattern Directory, which displays a grid of block pattern demos.](https://i0.wp.com/developer.wordpress.org/files/2023/09/patterns-directory.jpg?resize=2048%2C1458&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/patterns-directory.jpg?ssl=1)
 -->

[![ブロック・パターンのデモがグリッド状に表示されて いる、WordPress.org パターン・ディレクトリのスクリーンショット。](https://i0.wp.com/developer.wordpress.org/files/2023/09/patterns-directory.jpg?resize=2048%2C1458&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/patterns-directory.jpg?ssl=1)

<!-- 
And if you’re feeling adventurous, you can even submit your custom-designed patterns to the directory. This will let you both bundle them with your theme and let other theme creators and users use your patterns, even when your theme is not installed.
 -->

冒険心のある人は、独自にデザインしたパターンをディレクトリに申請できます。これにより、あなたのテーマにパターンをバンドルできるだけでなく、他のテーマ作者やユーザーがあなたのパターンを利用できるようになり、たとえあなたのテーマがインストールされていなくても使用可能になります。

<!-- 
In this document, you will learn how to include directory patterns for your theme’s users with just a few lines of code in `theme.json`.
 -->

本ドキュメントでは、`theme.json` に数行のコードを追加するだけで、あなたのテーマのユーザー向けにディレクトリ・パターンを組み込む方法を学びます。

<!-- 
## Adding patterns from the directory
 -->

## ディレクトリからパターンの追加

<!-- 
`patterns` is an optional property that lets you bundle as many or as few patterns as you’d like with your theme. The property accepts an array of pattern slugs, and as long as those patterns exist in the Patterns Directory, they will appear in the **Patterns** inserter in the WordPress editors.
 -->

`patterns` は任意のプロパティで、あなたのテーマに好きなだけパターンをバンドルできます。このプロパティはパターン・スラッグの配列を受け付け、それらのパターンがパターン・ディレクトリに存在している限り、WordPress エディターの **パターン** インサーターに表示されます。

<!-- 
Here is a look at the `patterns` property in the default `theme.json`:
 -->

デフォルトの `theme.json` における `patterns` プロパティの概要は、以下の通りです:

```json
{
	"version": 2,
	"patterns": []
}
```

<!-- 
Let’s take a look at one of the patterns from the Pattern Directory: [Hero banner with overlap images](https://wordpress.org/patterns/pattern/hero-banner-with-overlap-images/). To find the slug for the pattern, you need to look in the address bar of your browser, which should give you this URL:
 -->

パターン・ディレクトリから、1つのパターンを見てみましょう: [Hero banner with overlap images](https://wordpress.org/patterns/pattern/hero-banner-with-overlap-images/)。このパターンのスラッグを見つけるには、あなたのブラウザのアドレスバーを確認してください。そこには以下の URL が表示されているはずです:

```markup
https://wordpress.org/patterns/pattern/hero-banner-with-overlap-images/
```

<!-- 
The slug is the part of the URL that comes after `https://wordpress.org/patterns/pattern/`. In this case, the slug is `hero-banner-with-overlap-images` (note that the final slash is not included).
 -->

スラッグとは、URL の `https://wordpress.org/patterns/pattern/` の後に続く部分です。この場合、スラッグは `hero-banner-with-overlap-images` です (末尾のスラッシュは含まれないことに注意)。

<!-- 
To include this pattern with your theme, you need to pass only the slug to the `patterns` array in `theme.json`:
 -->

このパターンをあなたのテーマに組み込むには、`theme.json` 内の `patterns` 配列に、スラッグのみを渡す必要があります:

```json
{
	"version": 2,
	"patterns": [
		"hero-banner-with-overlap-images"
	]
}
```

<!-- 
Now that you’ve got the basics down, pick out a couple of other patterns and add them to your `patterns` array in `theme.json`:
 -->

基本を理解したところで、他のパターンをいくつか選び、`theme.json` 内のあなたの `patterns` 配列に追加しましょう:

```json
{
	"version": 2,
	"patterns": [
		"fullscreen-cover-image-gallery",
		"hero-banner-with-overlap-images",
		"mixed-shape-gallery"
	]
}
```

<!-- 
Now you should see your chosen patterns in the **Patterns** inserter in the UI:
 -->

これで、UI の **パターン** インサーターに、選択したパターンが表示されるはずです:

<!-- 
[![Patterns inserter from the page-editing screen showing a list of Gallery-based patterns.](https://i0.wp.com/developer.wordpress.org/files/2023/09/patterns-dotorg.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/patterns-dotorg.jpg?ssl=1)
 -->

[![ギャラリーベースのパターン一覧を表示する、ページ編集画面からのパターン・インサーター。](https://i0.wp.com/developer.wordpress.org/files/2023/09/patterns-dotorg.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/patterns-dotorg.jpg?ssl=1)

<!-- 
The patterns you include will automatically appear under the categories they are assigned to in the Pattern Directory. These are mapped to the existing patterns registered within WordPress. The patterns from the above example code all have the `gallery` pattern category, so they appear under the **Patterns > Gallery** tab in the inserter.
 -->

あなたが組み込んだパターンは、パターン・ディレクトリ内で割り当てられたカテゴリー下に自動的に表示されます。これらは WordPress 内に登録済みの、既存パターンにマッピングされます。上記のコード例にあるパターンはすべて `gallery` パターン・カテゴリーに属するため、インサーター内の **パターン > ギャラリー** タブ下に表示されます。