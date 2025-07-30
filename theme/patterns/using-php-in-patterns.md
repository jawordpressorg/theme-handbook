<!-- 
# Using PHP in Patterns
 -->

# パターンで PHP の利用

<!-- 
One of the biggest advantages of patterns over features like templates and template parts is that you can use PHP in them, which opens a world of possibilities for what you can accomplish. However, there are limits on what functionality is available to your patterns.
 -->

パターンはテンプレートやテンプレート・パーツなどの機能と比べて、最大の利点の一つは PHP を使用できる点であり、これにより、実現可能な可能性が大幅に広がります。ただし、あなたのパターンで利用可能な機能には制限があります。

<!-- 
In this article, you will learn the limitations of the patterns system, when and how you can use PHP, and some of the most common use cases for dynamic functionality.
 -->

この記事では、パターンシステムの制限事項、PHP をいつ、どのように使用できるか、および動的機能の最も一般的な使用例について学びます。

<!-- 
## Patterns are registered on init
 -->

## パターンは init 時に登録

<!-- 
When using PHP in patterns, it’s important to understand when the pattern’s block markup is actually compiled versus when it is rendered.
 -->

パターンで PHP を使用する際は、パターンのブロック・マークアップが実際にコンパイルされるタイミングとレンダリングされるタイミングを理解することが重要です。

<!-- 
Pattern registration happens on the [`init`](https://developer.wordpress.org/reference/hooks/init/) hook. At this point, WordPress compiles the content of the pattern and saves a copy of it as HTML-based block markup. This allows it to be used in both the editor and the front end. It’s during this registration process where the pattern can execute PHP code.
 -->

パターン登録は [`init`](https://developer.wordpress.org/reference/hooks/init/) フックで行われます。この時点で、WordPress はパターンのコンテンツをコンパイルし、そのコピーを HTML ベースのブロック・マークアップとして保存します。これにより、エディターとフロントエンドの両方で使用できます。この登録プロセス中に、パターンは PHP コードを実行できます。

<!-- 
A pattern’s block markup is not actually rendered until it is used either in the editor or on the front end. However, the block markup is plain HTML at the time it is rendered.
 -->

パターンのブロック・マークアップは、エディターまたはフロントエンドで使用されるまで実際にレンダリングされません。しかし、それがレンダリングされる時点では、ブロック・マークアップはプレーン HTML になります。

<!-- 
At a practical level, this means that a lot of data is unavailable during the registration process on `init`. Your patterns cannot access things like the global query or post. They also cannot use functions associated with that data. So this means that WordPress functions like `is_home()`, `is_single()`, `get_post()`, and others are simply not ready yet.
 -->

実践的なレベルでは、これは `init` の登録プロセス中に多くのデータが利用できないことを意味します。あなたのパターンは、グローバル・クエリーや投稿などにアクセスできません。また、そのデータに関連する関数も使用できません。したがって、これは、`is_home()`、`is_single()`、`get_post()` などの、WordPress 関数がまだ準備ができていないことを意味します。

<!-- 
For example, this PHP wouldn’t execute correctly in a pattern:
 -->

たとえば、この PHP は、パターンでは正しく実行されません:

```php
<?php if ( is_page() ) : ?>
	<!-- wp:paragraph -->
	<p><?php the_title(); ?></p>
	<!-- /wp:paragraph -->
<?php endif; ?>
```

<!-- 
Neither the `is_page()` nor the `the_title()` functions have the global data they need when a pattern is registered, so they won’t work.
 -->

`is_page()` 関数も `the_title()` 関数も、パターンが登録された時点では必要なグローバルデータを持っていないため、機能しません。

<!-- 
If you’re accustomed to building classic themes, this can feel very unintuitive, especially if you’ve been equating PHP-based patterns to classic, PHP-based template parts.
 -->

クラシック・テーマの構築に慣れている場合、特に、PHP ベースのパターン、PHP ベースのテンプレート・パーツを、クラシックと同一視していた場合、これは非常に直感に反する感覚になるかもしれません。

<!-- 
There are other methods for executing PHP at the time of render, such as using the [Block Bindings API](https://developer.wordpress.org/news/tag/block-bindings/). But those methods are outside the scope of pattern documentation.
 -->

レンダリング時に PHP を実行する他の方法として、[ブロック・バインディング API](https://developer.wordpress.org/news/tag/block-bindings/) を使用する方法があります。ただし、これらの方法は、パターン・ドキュメントの範囲外です。

<!-- 
You still have a wide and wonderful range of PHP functions and many WordPress functions available to you. And you’ll learn more about what you *can* use in the upcoming sections of this article.
 -->

PHP 関数や WordPress 関数には、依然として幅広くすばらしいものが数多く用意されています。本記事の今後のセクションでは、使用 *可能* なものについてさらに詳しく説明します。

<!-- 
## An example pattern
 -->

## パターン例

<!-- 
For the rest of this article, let’s use a single pattern that begins as mostly HTML. Then, you’ll walk through adding PHP to dynamically handle some portions of it. 
 -->

本記事の残りの部分では、主に HTML で構成される単一のパターンを使用します。その後、PHP を追加して、その一部を動的に処理する手順を説明します。

<!-- 
Create a new file named `patterns/hero.php` in your theme and put this code into it:
 -->

あなたのテーマに `patterns/hero.php` という名前の新規ファイルを作成し、以下のコードをその中に貼り付けてください:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */
?>
<!-- wp:cover {"overlayColor":"contrast","isUserOverlayColor":true,"align":"full"} -->
<div class="wp-block-cover alignfull">
	<span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim-100 has-background-dim"></span>
	<div class="wp-block-cover__inner-container">
		
		<!-- wp:heading {"textAlign":"center"} -->
		<h2 class="wp-block-heading has-text-align-center">Welcome to My Site</h2>
		<!-- /wp:heading -->

		<!-- wp:paragraph {"align":"center"} -->
		<p class="has-text-align-center">This is my little home away from home.</p>
		<!-- /wp:paragraph -->

		<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
		<div class="wp-block-buttons">
			<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
			<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button">Button A</a></div>
			<!-- /wp:button -->
			<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
			<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button">Button B</a></div>
			<!-- /wp:button -->
		</div>
		<!-- /wp:buttons -->

	</div>
</div>
<!-- /wp:cover -->
```

<!-- 
If you insert it the pattern into the editor, it should look like this:
 -->

パターンをエディターに挿入すると、次のように表示されるはずです:

<!-- 
[![WordPress post editor with a "Welcome to My Site" message in white text with a black background. It is wrapped in a Cover block.](https://i0.wp.com/developer.wordpress.org/files/2024/04/php-pattern-default.jpg?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/php-pattern-default.jpg?ssl=1)
 -->

[![WordPress 投稿エディターに、黒背景に白文字で「ようこそ私のサイトへ」メッセージが表示されている。これは「カバー」ブロックでラップされている。](https://i0.wp.com/developer.wordpress.org/files/2024/04/php-pattern-default.jpg?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/php-pattern-default.jpg?ssl=1)

<!-- 
## Internationalizing text in patterns
 -->

## パターン内テキストの国際化

<!-- 
One of the primary use cases for block patterns is [internationalizing text](https://developer.wordpress.org/themes/functionality/internationalization/) (making it ready for translation). For example, if you have text in a template or template part, the only way to internationalize that text is to move it into a pattern, where you have full access to PHP.
 -->

ブロック・パターンの主なユースケースの一つは [テキストの国際化](https://developer.wordpress.org/themes/functionality/internationalization/) (翻訳に対応できるようにすること) です。たとえば、テンプレートやテンプレート・パーツにテキストが存在する場合は、そのテキストを国際化するための唯一の方法は、PHP に完全なアクセス権限があるパターンに移動させることです。

<!-- 
Because pattern files are just PHP, you can use any of the internationalization functions within WordPress. In the below example, you’ll use [`esc_html_e()`](https://developer.wordpress.org/reference/functions/esc_html_e/) to both escape the text for security and make it ready for translators.
 -->

パターン・ファイルは単なる PHP ですので、WordPress 内の国際化関数を自由に使用できます。以下の例では、[`esc_html_e()`](https://developer.wordpress.org/reference/functions/esc_html_e/) を使用して、セキュリティのためにテキストをエスケープし、翻訳者が翻訳しやすいようにしています。

<!-- 
Let’s look at the Heading block from your Hero pattern:
 -->

「Hero」パターンの「見出し」ブロックを詳しく見てみましょう:

```markup
<!-- wp:heading {"textAlign":"center"} -->
<h2 class="wp-block-heading has-text-align-center">Welcome to My Site</h2>
<!-- /wp:heading -->
```

<!-- 
As you can see, the “Welcome to My Site” text in the Heading block is not internationalized. When shipping your theme to users all around the world who speak many different languages, it’s important to ensure this text can be translated.
 -->

ご覧の通り、「見出し」ブロック内の「Welcome to My Site」というテキストは、国際化されていません。あなたのテーマを世界中のユーザーに提供する際、彼らが話す多様な言語に対応するため、このテキストが翻訳可能であることを確認することが重要です。

<!-- 
To internationalize the Heading block’s text, you must wrap it in an internationalization function (`esc_html_e()` in this case). So you’d change the block markup to look like this:
 -->

「見出し」ブロックのテキストを国際化するには、そのテキストを国際化関数 (この場合は `esc_html_e()` ) でラップする必要があります。では、ブロックのマークアップを次のように変更します:

```php
<!-- wp:heading {"textAlign":"center"} -->
<h2 class="wp-block-heading has-text-align-center"><?php esc_html_e( 'Welcome to My Site', 'themeslug' ); ?></h2>
<!-- /wp:heading -->
```

<!-- 
There are three other places where you should also make these changes. The first is to the Paragraph block text, and then the two Button blocks. Your new `patterns/hero.php` file should look like this:
 -->

これらの変更を適用する必要がある場所は、他に3ヵ所あります。最初は「段落」ブロックのテキストで、次に2つの「ボタン」ブロックです。変更後の `patterns/hero.php` ファイルは次のように表示されるはずです:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */
?>
<!-- wp:cover {"overlayColor":"contrast","isUserOverlayColor":true,"align":"full"} -->
<div class="wp-block-cover alignfull">
	<span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim-100 has-background-dim"></span>
	<div class="wp-block-cover__inner-container">
		
		<!-- wp:heading {"textAlign":"center"} -->
		<h2 class="wp-block-heading has-text-align-center"><?php esc_html_e( 'Welcome to My Site', 'themeslug' ); ?></h2>
		<!-- /wp:heading -->

		<!-- wp:paragraph {"align":"center"} -->
		<p class="has-text-align-center"><?php esc_html_e( 'This is my little home away from home.', 'themeslug' ); ?></p>
		<!-- /wp:paragraph -->

		<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
		<div class="wp-block-buttons">
			<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
			<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Button A', 'themeslug' ); ?></a></div>
			<!-- /wp:button -->
			<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
			<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Button B', 'themeslug' ); ?></a></div>
			<!-- /wp:button -->
		</div>
		<!-- /wp:buttons -->

	</div>
</div>
<!-- /wp:cover -->
```

<!-- 
## Using images and other assets
 -->

## 画像やその他のアセットの利用

<!-- 
Adding dynamic URLs for images and other assets is another important feature of patterns. Because you have PHP access, you can use functions like [`get_theme_file_uri()`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/) to output an image URL that’s bundled with your theme, for example.
 -->

画像やその他のアセット用の動的 URL の追加は、パターンのもう一つの重要な機能です。PHP へのアクセス権限があるため、たとえばあなたのテーマにバンドルされた画像の URL を出力するために [`get_theme_file_uri()`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/) のような関数を使用できます。

<!-- 
Try adding an image background to your “hero” pattern’s Cover block. If you need an image, try grabbing one from the WordPress [Photo Directory](https://wordpress.org/photos/) (the example below uses this [Nepal night scene photo](https://wordpress.org/photos/photo/41664fab9b/)). 
 -->

あなたの「ヒーロー」パターンの「カバー」ブロックに、画像の背景を追加してみましょう。画像が必要な場合は、WordPress の [写真ディレクトリ](https://wordpress.org/photos/) から入手してみましょう (以下の例では、この [ネパールの夜景写真](https://wordpress.org/photos/photo/41664fab9b/) を使用しています)。

<!-- 
Download an image and save it to your theme’s `/assets/images` folder (or a folder of your choice) and name it `hero-background.jpg`.
 -->

画像をダウンロードし、あなたのテーマの `/assets/images` フォルダー (または任意のフォルダー) に保存し、`hero-background.jpg` と名付けます。

<!-- 
Then open your pattern in the editor and upload the image as the background for the Cover block in your Hero pattern, which should look like this:
 -->

次に、エディターであなたのパターンを開き、「ヒーロー」パターン内の「カバー」ブロックの背景として画像をアップロードすると、このように表示されます:

<!-- 
[![WordPress post editor with a Cover block that has a background image of a nighttime city. There is a welcome message and buttons overlaying the background.](https://i0.wp.com/developer.wordpress.org/files/2024/04/php-pattern-dynamic-background.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/php-pattern-dynamic-background.webp?ssl=1)
 -->

[![WordPress の投稿エディターに、夜間の都市の背景画像を使用した「カバー」ブロックがある。背景には、ウェルカム・メッセージとボタンがオーバーレイ表示されている。](https://i0.wp.com/developer.wordpress.org/files/2024/04/php-pattern-dynamic-background.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/php-pattern-dynamic-background.webp?ssl=1)

<!-- 
If you copy the blocks that make up the pattern, you’ll notice that you have two instances of the image URL in your pattern code. It will be a hardcoded URL similar to this:
 -->

パターンを構成するブロックをコピーすると、あなたのパターンコード内に、画像 URL のインスタンスが2つ存在することに気付くでしょう。これは次のようなハードコードされた URL です:

```markup
http://localhost/wp-content/uploads/2023/10/hero-background.jpg
```

<!-- 
You need to change both of those instances so that they point to the image that is located in your theme’s `/assets/images` folder. For this, you need do two things:
 -->

これらの2つのインスタンスを両方とも変更し、あなたのテーマの `/assets/images` フォルダー内に格納されている画像を指すようにする必要があります。これを行うには、次に示す2つの手順を実行する必要があります:

<!-- 
*   Get the correct URL using a function like [`get_theme_file_uri()`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/).
*   Escape the URL so that it’s safe for output with [`esc_url()`](https://developer.wordpress.org/reference/functions/esc_url/).
 -->

*   [`get_theme_file_uri()`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/) のような関数を使用して、正しい URL を取得します。
*   URL をエスケープするため、[`esc_url()`](https://developer.wordpress.org/reference/functions/esc_url/) で安全に出力できるようにします。

<!-- 
Change the hard coded image URLs to this:
 -->

ハードコードされた画像 URL を、次のように変更します:

```php
<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.jpg' ) ); ?>
```

<!-- 
Your final pattern code should look like this (note that this example includes internationalized text as explained in the previous section):
 -->

あなたの最終的なパターン・コードは、次のように見えるはずです (この例には、前のセクションで説明した国際化テキストを含むことに注意してください):

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */
?>
<!-- wp:cover {"url":"<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.jpg' ) ); ?>","id":3838,"dimRatio":50,"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull">
	<span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim"></span>
	<img class="wp-block-cover__image-background wp-image-3838" alt="" src="<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.jpg' ) ); ?>" data-object-fit="cover"/>
	<div class="wp-block-cover__inner-container">
		
		<!-- wp:heading {"textAlign":"center"} -->
		<h2 class="wp-block-heading has-text-align-center"><?php esc_html_e( 'Welcome to My Site', 'themeslug' ); ?></h2>
		<!-- /wp:heading -->

		<!-- wp:paragraph {"align":"center"} -->
		<p class="has-text-align-center"><?php esc_html_e( 'This is my little home away from home.', 'themeslug' ); ?></p>
		<!-- /wp:paragraph -->

		<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
		<div class="wp-block-buttons">
			<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
			<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Button A', 'themeslug' ); ?></a></div>
			<!-- /wp:button -->
			<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
			<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Button B', 'themeslug' ); ?></a></div>
			<!-- /wp:button -->
		</div>
		<!-- /wp:buttons -->

	</div>
</div>
<!-- /wp:cover -->
```

<!-- 
## foreach() loops
 -->

## `foreach()` ループ

<!-- 
You have access to nearly every PHP function and feature at your disposal, and many things will undoubtedly be useful to you as you build themes. But `foreach()` loops are likely one of the features that you will often reach for.
 -->

PHP のほぼすべての関数と機能にアクセス可能ですので、テーマを構築する際に、多くの機能が必ずや役立つことでしょう。中でも、`foreach()` ループは頻繁に利用する機能の一つとなるでしょう。

<!-- 
`foreach()` loops are particularly useful in patterns that have repeated blocks. For example, in your `patterns/hero.php` file, you have a set of two Button blocks:
 -->

`foreach()` ループは、繰り返しブロックを含むパターンにおいて、特に有用です。たとえば、あなたの `patterns/hero.php` ファイルには、「ボタン」ブロックのセットが2つあります:

```php
<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Button A', 'themeslug' ); ?></a></div>
<!-- /wp:button -->

<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Button B', 'themeslug' ); ?></a></div>
<!-- /wp:button -->
```

<!-- 
One of the foundational principles of development is DRY (Don’t Repeat Yourself). And this code breaks that principle. With a single `foreach()` loop, you can create the block markup once and loop through it.
 -->

開発の基礎原則の一つが DRY (Don't Repeat Yourself。繰り返しを避ける) 原則です。このコードはその原則に反しています。単一の `foreach()` ループを使用すれば、ブロック・マークアップを一度だけ作成し、ループで繰り返し使用できます。

<!-- 
First, you need an array of items to loop through, which is the Button content itself. At the top of your `patterns/hero.php` file before the closing `?>` tag, add an array of labels:
 -->

まず、ループ処理の対象となるアイテムの配列が必要で、それが「ボタン」コンテンツそのものです。`patterns/hero.php` ファイルの閉じタグ `?>` の前に、ラベルの配列を追加します:

```php
$buttons = array(
	__( 'Button A', 'themeslug' ),
	__( 'Button B', 'themeslug' )
);
```

<!-- 
Then replace the markup for your two Button blocks with this code:
 -->

次に、あなたの2つの「ボタン」ブロックのマークアップを、次のコードに差し替えます:

```php
<?php foreach ( $buttons as $button ) : ?>
	<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
	<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php echo esc_html( $button ); ?></a></div>
	<!-- /wp:button -->
<?php endforeach; ?>
```

<!-- 
Your full `patterns/hero.php` file should now look like the following (note this includes both the internationalized text and dynamic image example code from earlier):
 -->

あなたの `patterns/hero.php` ファイル全体は、現在以下のようになっているはずです (これには、以前の国際化テキストと動的画像のサンプルコードを両方含むことに注意してください):

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */

$buttons = array(
	__( 'Button A', 'themeslug' ),
	__( 'Button B', 'themeslug' )
);

?>
<!-- wp:cover {"url":"<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.jpg' ) ); ?>","id":3838,"dimRatio":50,"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull">
	<span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim"></span>
	<img class="wp-block-cover__image-background wp-image-3838" alt="" src="<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.jpg' ) ); ?>" data-object-fit="cover"/>
	<div class="wp-block-cover__inner-container">
		
		<!-- wp:heading {"textAlign":"center"} -->
		<h2 class="wp-block-heading has-text-align-center"><?php esc_html_e( 'Welcome to My Site', 'themeslug' ); ?></h2>
		<!-- /wp:heading -->

		<!-- wp:paragraph {"align":"center"} -->
		<p class="has-text-align-center"><?php esc_html_e( 'This is my little home away from home.', 'themslug' ); ?></p>
		<!-- /wp:paragraph -->

		<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
		<div class="wp-block-buttons">
			<?php foreach ( $buttons as $button ) : ?>
				<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
				<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php echo esc_html( $button ); ?></a></div>
				<!-- /wp:button -->
			<?php endforeach; ?>
		</div>
		<!-- /wp:buttons -->

	</div>
</div>
<!-- /wp:cover -->
```

<!-- 
At this point, your pattern is fully dynamic. As you dive deeper into pattern development, you’ll come up with even more use cases for using PHP. Think of this article as just the foundation that you’ll build from.
 -->

この時点で、あなたのパターンは完全に動的になっています。パターン開発にさらに深く取り組むにつれ、PHP を使用するさらなるユースケースが浮かんでくることでしょう。この記事を、これから構築するための基盤と考えてください。