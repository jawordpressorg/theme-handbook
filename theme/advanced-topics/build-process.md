<!-- 
# Build Process
 -->

# ビルド・プロセス

<!-- 
A build process is a method of converting source code files into a final build/production version that can be read by the computer. In particular, themes will most often be minifying or converting source code into CSS or JavaScript so that they can be read by the browser.
 -->

ビルド・プロセスとは、ソースコード・ファイルをコンピューターで読める最終的なビルド/製品版へと変換する方法です。特にテーマでは、ブラウザで読めるようにソースコードをミニファイしたり、CSS や JavaScript にトランスパイルしたりすることがほとんどです。

<!-- 
When creating a WordPress theme, you may find yourself in need of a build process to handle more complex projects. There are many systems to choose from, and you can use whatever you prefer. But WordPress also offers a standard package that you can be assured is continually updated and should cover most of your needs.
 -->

WordPress テーマを制作する際、より複雑なプロジェクトに対応するためのビルド・プロセスが必要だと感じることがあるかもしれません。多くのシステムから選ぶことができ、好きなものを使うことができます。しかし、WordPress も標準パッケージを提供しており、継続的に更新されているため、あなたのニーズのほとんどをカバーできるでしょう。

<!-- 
In this article, you will learn how to integrate with the [`@wordpress/scripts`](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/) package to handle your theme’s build process.
 -->

本稿では、あなたのテーマのビルド・プロセスを管理するために、[`@wordpress/scripts`](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/) パッケージと統合する方法を学びます。

<!-- 
## Prerequisites
 -->

## 必須要件

<!-- 
Most of WordPress theme development is pretty much plug and play. You just need a code editor and an install of WordPress in some type of development environment as outlined in [Tools and Setup](https://developer.wordpress.org/themes/getting-started/tools-and-setup/). But to work with a build process, there are some other requirements:
 -->

WordPress テーマ開発のほとんどは、プラグ＆プレイで可能です。[ツールとセットアップ](https://developer.wordpress.org/themes/getting-started/tools-and-setup/) で説明したように、コードエディターと WordPress を何らかの開発環境にインストールするだけです。しかし、ビルド・プロセスで扱うには、他にもいくつかの要件があります:

<!-- 
*   You need to have [Node.js and npm installed](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) on your local machine.
*   A basic [understanding of webpack](https://webpack.js.org/concepts/) is also highly recommended.
*   Some familiarity with the [`@wordpress/scripts`](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/) package (read [Getting started with wp-scripts](https://developer.wordpress.org/block-editor/getting-started/devenv/get-started-with-wp-scripts/) in the Block Editor Handbook).
 -->

*   あなたのローカルマシンに、[Node.js と npm がインストールされている](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) 必要があります。
*   基本的な [webpack の理解](https://webpack.js.org/concepts/) も強く推奨します。
*   [`@wordpress/scripts`](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/) パッケージについて、ある程度慣れている必要があります (ブロック・エディター・ハンドブックの [wp-scripts で始める](https://developer.wordpress.org/block-editor/getting-started/devenv/get-started-with-wp-scripts/) をご覧あれ)。

<!-- 
These are more advanced tools than what is normally required to build themes, but they are necessary if you want to work with the standard WordPress build process.
 -->

これらは、テーマを構築するために通常必要とされるものよりも高度なツールですが、標準的な WordPress ビルド・プロセスで作業したい場合、これらは必要です。

<!-- 
## Setting up your files and folders
 -->

## あなたのファイルとフォルダーのセットアップ

<!-- 
The `@wordpress/scripts` package was originally created for block development, but it evolved to also work with themes over time. By default, it expects that development files live in the `/src` folder and will output build files in the `/build` folder. Because most theme authors utilize a custom system for working with assets, this guide will show you how to do that.
 -->

`@wordpress/scripts` パッケージはもともとブロック開発用に制作されましたが、時間の経過とともにテーマでも動作するように進化しました。デフォルトでは、開発ファイルは `/src` フォルダーにあり、ビルドファイルは `/build` フォルダーに出力されます。ほとんどのテーマ作者は、アセットを扱うためのカスタムシステムを利用しているため、このガイドではその方法を紹介します。

<!-- 
For the examples that follow, you will use this structure within your theme folder:
 -->

この後の例では、あなたのテーマ・フォルダー内でこの構造を使用します:

*   `public/`
*   `resources/`
    *   `js/`
        *   `editor.js`
    *   `scss/`
        *   `editor.scss`
        *   `screen.scss`
*   `package.json`
*   `webpack.config.js`

<!-- 
## Installing the WordPress scripts package
 -->

## WordPress スクリプト・パッケージのインストール

<!-- 
Once you have your files and folders set up, you need to install the correct packages on your local machine.
 -->

あなたのファイルとフォルダーをセットアップしたら、正しいパッケージをローカルマシンにインストールする必要があります。

<!-- 
First, open your theme’s `package.json` file and add the following code:
 -->

まず、あなたのテーマの `package.json` ファイルを開き、以下のコードを追加しましょう:

```json
{
	"name": "your-project-name",
	"scripts": {
		"start": "wp-scripts start --webpack-src-dir=resources --output-path=public",
		"build": "wp-scripts build --webpack-src-dir=resources --output-path=public"
	}
}
```

<!-- 
The `@wordpress/scripts` package has several other [available scripts](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/#available-scripts) that you can add, but you will definitely need `start` and `build`.
 -->

`@wordpress/scripts` パッケージには、他にも追加できる [利用可能なスクリプト](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/#available-scripts) がいくつかありますが、`start` と `build` は絶対に必要なものです。

<!-- 
Now open your command line tool on your computer, navigate to your theme folder, and input the following command:
 -->

それでは、あなたのコンピューターであなたのコマンドライン・ツールを開き、あなたのテーマ・フォルダーに移動し、以下のコマンドを入力しましょう:

```bash
npm install @wordpress/scripts path webpack-remove-empty-scripts --save-dev
```

<!-- 
That command installs three packages:
 -->

このコマンドは、3つのパッケージをインストールします:

*   `@wordpress/scripts`
*   `path`
*   `webpack-remove-empty-scripts`

<!-- 
The latter two are third-party packages, but they are useful for integrating with webpack in the next step.
 -->

後者の2つはサードパーティー製のパッケージですが、次のステップで webpack と統合するのに便利です。

<!-- 
## Configuring webpack
 -->

## webpack の設定

<!-- 
The `@wordpress/scripts` package is built on top of webpack. If you were building a block, everything would already be in place for you. However, because you are building a theme, you need to overwrite some of the default configuration of the `@wordpress/scripts` package with your own.
 -->

`@wordpress/scripts` パッケージは、webpack 上に構築されています。ブロックを構築するのであれば、すべてがすでに用意されているはずです。しかし、あなたはテーマを構築しているので、`@wordpress/scripts` パッケージのデフォルト設定の一部を、あなた独自の設定で上書きする必要があります。

<!-- 
That’s where your theme’s custom `webpack.config.js` file comes in. There two primary things you need to configure:
 -->

そこで、あなたのテーマのカスタム `webpack.config.js` ファイルの出番です。設定する必要があるのは、主に2つです:

<!-- 
*   The entry points for your custom CSS and JavaScript files (those in the code below correspond to the file structure in this article).
*   The `webpack-remove-empty-scripts` plugin so that there are no leftover `.js` files mapped to your CSS.
 -->

*   カスタム CSS と JavaScript ファイルの、エントリーポイント (以下のコードにあるものは、本稿でのファイル構造に対応)。
*   あなたの CSS にマッピングされた `.js` ファイルが残らないようにするための、`webpack-remove-empty-scripts` プラグイン。 

<!-- 
Add the following code to your `webpack.config.js` file:
 -->

以下のコードを、あなたの `webpack.config.js` ファイルに追加します:

```javascript
// WordPress webpack config.
const defaultConfig = require( '@wordpress/scripts/config/webpack.config' );

// Plugins.
const RemoveEmptyScriptsPlugin = require( 'webpack-remove-empty-scripts' );

// Utilities.
const path = require( 'path' );

// Add any new entry points by extending the webpack config.
module.exports = {
	...defaultConfig,
	...{
		entry: {
			'js/editor':  path.resolve( process.cwd(), 'resources/js',   'editor.js'   ),
			'css/screen': path.resolve( process.cwd(), 'resources/scss', 'screen.scss' ),
			'css/editor': path.resolve( process.cwd(), 'resources/scss', 'editor.scss' ),
		},
		plugins: [
			// Include WP's plugin config.
			...defaultConfig.plugins,

			// Removes the empty `.js` files generated by webpack but
			// sets it after WP has generated its `*.asset.php` file.
			new RemoveEmptyScriptsPlugin( {
				stage: RemoveEmptyScriptsPlugin.STAGE_AFTER_PROCESS_PLUGINS
			} )
		]
	}
};
```

<!-- 
## Using the WordPress scripts package
 -->

## WordPress スクリプト・パッケージの使用

<!-- 
To use the WordPress scripts package to process your assets, you can run one of two commands in your command line tool:
 -->

あなたのコマンドライン・ツールで、以下の2つのコマンドのいずれかを実行することで、WordPress スクリプト・パッケージを使用してあなたのアセットを処理できます:

<!-- 
*   `start`: Builds the development version of your files and activates “watch” mode, which will process any code changes while enabled.
*   `build`: Builds the production version of your files.
 -->

*   `start`: あなたのファイルの開発版ファイルをビルドし、有効になっている間は、あらゆるコード変更が処理される、「ウォッチ」モードを有効にします。
*   `build`: あなたのファイルの製品版を、ビルドします。

<!-- 
Now open your command line tool and run the `start` command:
 -->

では、あなたのコマンドラインツールを開き、`start` コマンドを実行します:

```bash
npm run start
```

<!-- 
It should automatically process your files from the `/resources` folder and place them in the `/public` folder with this structure:
 -->

`/resources` フォルダーのあなたのファイルを自動的に処理し、この構造で `/public` フォルダーに配置するはずです:

*   `public/`
    *   `js/`
        *   `editor.js`
        *   `editor.asset.php`
    *   `scss/`
        *   `editor.scss`
        *   `editor.asset.php`
        *   `screen.scss`
        *   `screen.asset.php`

<!-- 
You’ll now see new `*.asset.php` files generated for each of your CSS and JavaScript files. These will contain metadata about each asset file that you can use when loading your files. This is covered in the “Loading scripts and styles” section below.
 -->

これで、あなたの CSS ファイルと JavaScript ファイルそれぞれに新規の `*.asset.php` ファイルが生成されます。これらのファイルには、各アセットファイルに関するメタデータが含まれており、あなたのファイルをロードする際に利用できます。これについては、以下の「スクリプトとスタイルのロード」セクションで説明します。

<!-- 
To disable the `start` command, type `Ctrl + C` (on either Windows or Mac) of your command line tool.
 -->

`start` コマンドを無効にするには、あなたのコマンドライン・ツールで、`Ctrl + C` (Windows でも Mac でも) をタイプします。

<!-- 
Once you’re ready to do a final production build of your files, run this command in your command line tool:
 -->

あなたのファイルの最終的な製品ビルドの準備ができたら、あなたのコマンドライン・ツールでこのコマンドを実行します:

```bash
npm run build
```

<!-- 
## Loading scripts and styles
 -->

## スクリプトとスタイルのロード

<!-- 
The methods for loading scripts and styles are already covered in depth in the [Including Assets](https://developer.wordpress.org/themes/core-concepts/including-assets/) documentation in this handbook. You should already be familiar with how to do this before proceeding with the next steps.
 -->

スクリプトとスタイルのロード方法については、このハンドブックの [アセットを含める](https://developer.wordpress.org/themes/core-concepts/including-assets/) ドキュメントですでに詳しく説明しています。次のステップに進む前に、この方法をすでに熟知している必要があります。

<!-- 
The documentation below is primarily geared towards teaching you how the `*.asset.php` file is generated for each asset. In each file, you will see an array that looks similar to the following snippet:
 -->

以下のドキュメントは、主に各アセットに対して `*.asset.php` ファイルがどのように生成されるかを説明するためのものです。各ファイルには、以下のスニペットのような配列が表示されているでしょう:

```php
<?php return array('dependencies' => array('wp-block-editor'), 'version' => '2eae4c519afeff2a8c77');
```

<!-- 
In particular, the array will have two pieces of metadata that you can use in any `wp_enqueue_*()` functions:
 -->

特に、配列は `wp_enqueue_*()` 関数で使用できる2つのメタデータを持ちます:

<!-- 
*   **`dependencies`:** An array of dependencies that your script/style rely on.
*   **`version`:** A version number that you can use for cache busting.
 -->

*   **`dependencies`:** あなたのスクリプト/スタイルが依存する、依存関係の配列です。
*   **`version`:** キャッシュ破棄に使用できる、バージョン番号です。

<!-- 
Because the file returns the array, you can use PHP’s `include` to assign the array to a variable in your code. The following example shows getting the array for the `screen.asset.php` file:
 -->

ファイルが配列を返すので、PHP の `include` を使用すると、配列をあなたのコード内の変数に代入できます。以下の例では、`screen.asset.php` ファイルの配列を取得しています:

```php
$asset = include get_theme_file_path( 'public/css/screen.asset.php' );
// Returns: array( 'dependencies' => array(), 'version' => '0000' );
```

<!-- 
When loading a script or style using either [`wp_enqueue_script()`](https://developer.wordpress.org/reference/functions/wp_enqueue_script/) or [`wp_enqueue_style()`](https://developer.wordpress.org/reference/functions/wp_enqueue_style/), you can pass `$asset['dependencies']` and `$asset['version']` to the corresponding parameters in the functions.
 -->

[`wp_enqueue_script()`](https://developer.wordpress.org/reference/functions/wp_enqueue_script/) または [`wp_enqueue_style()`](https://developer.wordpress.org/reference/functions/wp_enqueue_style/) を使用してスクリプトまたはスタイルをロードする際には、関数の対応するパラメータに `$asset['dependencies']` および `$asset['version']` を渡すことができます。

<!-- 
Try adding the following code to your theme’s `functions.php` file to load the assets that you’ve previously defined:
 -->

あなたのテーマの `functions.php` ファイルに以下のコードを追加して、以前に定義したアセットをロードしてみましょう:

```php
// Load front-end assets.
add_action( 'wp_enqueue_scripts', 'themeslug_assets' );

function themeslug_assets() {
	$asset = include get_theme_file_path( 'public/css/screen.asset.php' );

	wp_enqueue_style(
		'themeslug-style',
		get_theme_file_uri( 'public/css/screen.css' ),
		$asset['dependencies'],
		$asset['version']
	);
}

// Load editor stylesheets.
add_action( 'after_setup_theme', 'themeslug_editor_styles' );

function themeslug_editor_styles() {
	add_editor_style( [
		get_theme_file_uri( 'public/css/screen.css' )
	] );
}

// Load editor scripts.
add_action( 'enqueue_block_editor_assets', 'themeslug_editor_assets' );

function themeslug_editor_assets() {
	$script_asset = include get_theme_file_path( 'public/js/editor.asset.php'  );
	$style_asset  = include get_theme_file_path( 'public/css/editor.asset.php' );

	wp_enqueue_script(
		'themeslug-editor',
		get_theme_file_uri( 'public/js/editor.js' ),
		$script_asset['dependencies'],
		$script_asset['version'],
		true
	);

	wp_enqueue_style(
		'themeslug-editor',
		get_theme_file_uri( 'public/css/editor.css' ),
		$style_asset['dependencies'],
		$style_asset['version']
	);
}
```