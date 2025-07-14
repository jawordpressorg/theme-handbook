<!-- 
# Custom Functionality (functions.php)
 -->

# カスタム機能 (functions.php)

<!-- 
This document will introduce you to the `functions.php` file. It is one of the optional standard files you first learned about in [Theme Structure](https://developer.wordpress.org/themes/core-concepts/theme-structure/). Both block and classic themes can utilize it.
 -->

このドキュメントでは、`functions.php` ファイルについて説明します。これは、[テーマ構造](https://developer.wordpress.org/themes/core-concepts/theme-structure/) で最初に学んだオプショナルな標準ファイルの一つです。ブロック・テーマとクラシック・テーマの両方で利用可能です。

<!-- 
The following will introduce you to the core concepts around using PHP within `functions.php`, but it will not teach you the PHP programming language itself. You can visit the official [PHP documentation](https://www.php.net/) for more information on how to write your own PHP code.
 -->

以下では、`functions.php` 内で PHP を使用する際の、核心的な概念について紹介しますが、PHP プログラミング言語そのものを教えるものではありません。あなた独自の PHP コードを書く方法に関する詳細な情報は、公式 [PHP ドキュメント](https://www.php.net/) をご参照ください。

<!-- 
Throughout the handbook, you will encounter more examples where you will add custom functionality, so getting the basics down is important. You can jump into more advanced PHP examples in the [Features](https://developer.wordpress.org/themes/features/), [Advanced Topics](https://developer.wordpress.org/themes/advanced-topics/), and [Classic Themes](https://developer.wordpress.org/themes/classic-themes/) chapters.
 -->

ハンドブック全体を通じて、カスタム機能を追加するさらなる例に遭遇するでしょうから、基本的な部分をしっかり理解することが重要です。[機能](https://developer.wordpress.org/themes/features/)、[高度なトピック](https://developer.wordpress.org/themes/advanced-topics/)、[クラシック・テーマ](https://developer.wordpress.org/themes/classic-themes/) の各章では、より高度な PHP の例に飛び込むことができます。

<!-- 
## What is functions.php?
 -->

## functions.php とは ?

<!-- 
The `functions.php` essentially acts like a WordPress plugin, letting you add custom PHP functions, classes, interfaces, and more. It opens up the entirety of the PHP programming language to your theme.
 -->

`functions.php` は本質的に WordPress プラグインのように機能し、カスタム PHP 関数、クラス、インターフェースなどを追加する機能を提供します。これにより、あなたのテーマに対して PHP プログラミング言語の全機能を解放します。

<!-- 
WordPress automatically loads the `functions.php` file (if it exists) as soon as it loads the theme on all page views on both the admin and front-end of the website. So it provides you with a lot of power to build unique features around WordPress.
 -->

WordPress は、Web サイトの管理画面とフロントエンドの両方で、すべてのページの表示時にテーマをロードすると、(存在する場合) `functions.php` ファイルを自動的にロードします。そのため、WordPress に独自の機能を構築するための強力なパワーを提供します。

<!-- 
Just because you *can* build plugin-like features in a theme doesn’t mean you always should, particularly if you are distributing your theme to others to use. If you are creating features that should be available regardless of the site’s design, **it is best practice to put the code in a plugin**. The rule of thumb is that themes should only deal with the site’s design.
 -->

特に、あなたのテーマを他者に配布して使用してもらう場合、テーマ内でプラグインのような機能を構築 **できる** からといって、必ずしもそうすべきとは限りません。サイトのデザインにかかわらずに利用可能な機能を制作する場合、**そのコードをプラグインに配置することが、ベスト・プラクティスです**。基本的なルールとして、テーマはサイトのデザインのみを扱うべきです。

<!-- 
While all themes can have a custom `functions.php` file, WordPress will only load the currently active theme’s.
 -->

すべてのテーマはカスタム `functions.php` ファイルを保持できますが、WordPress は現在有効化されているテーマのファイルのみをロードします。

<!-- 
The only caveat to that rule is when a child theme is active. In that case, WordPress loads the child theme’s `functions.php` just before loading the parent theme’s `functions.php`. You can learn more about [child themes](https://developer.wordpress.org/themes/advanced-topics/child-themes/) in the Advanced Topics chapter.
 -->

そのルールの唯一の例外は、子テーマが有効化されている場合です。その場合、WordPress は子テーマの `functions.php` を、親テーマの `functions.php` をロードする直前に、ロードします。高度なトピック章で、[子テーマ](https://developer.wordpress.org/themes/advanced-topics/child-themes/) について詳しく学ぶことができます。

<!-- 
## Common uses for functions.php
 -->

## functions.php の一般的な用途

<!-- 
Because the `functions.php` file lets you write any PHP, you will often see themes with wildly different code, organizational systems, naming conventions, and more. The deeper your understanding of PHP, the easier it will be to follow the code from other themes.
 -->

`functions.php` ファイルは任意の PHP コードを記述できるため、テーマごとにコードの構造、構成システム、命名規則などが大きく異なる場合があります。PHP の理解が深ければ深いほど、他のテーマのコードを追跡するのが容易になります。

<!-- 
The following are some uses you will often find in a theme’s `functions.php` file. 
 -->

以下は、テーマの `functions.php` ファイルでよく見られる使用例です。

<!-- 
### Adding actions or filters to hooks
 -->

### フックに対する、アクションやフィルターの追加

<!-- 
Hooks are the entry point to extending WordPress’ functionality, providing you with a way to inject custom code or filter data. Think of them as a way for themes (and plugins) to communicate directly with WordPress.
 -->

フックは、WordPress の機能を拡張するためのエントリー・ポイントであり、カスタムコードを挿入したり、データをフィルタリングしたりする方法を提供します。フックは、テーマ (およびプラグイン) が WordPress と直接通信するための手段と考えてください。

<!-- 
WordPress’ hooks system offers two different methods for executing your code during the page loading process:
 -->

WordPress のフック・システムは、ページのロード・プロセス中にコードを実行するための、2つの異なる方法を提供しています:

<!-- 
*   [**Action hooks**](https://developer.wordpress.org/plugins/hooks/actions/) allow you to run a custom action callback and “act on” the information that it receives.
*   [**Filter hooks**](https://developer.wordpress.org/plugins/hooks/filters/) let you filter data via a custom filter callback and manipulate it.
 -->

*   [**アクション・フック**](https://developer.wordpress.org/plugins/hooks/actions/) を使用すると、カスタム・アクション・コールバックを実行し、受け取った情報にもとづいて、アクションを実行できます。

ここは原文に従わず、カッコを外した方が自然かなと思いました。
*   [**フィルター・フック**](https://developer.wordpress.org/plugins/hooks/filters/) を使用すると、カスタム・フィルター・コールバックを介してデータをフィルタリングし、操作できます。

<!-- 
Technically, hooks are a part of the Plugin API, and you can [read the documentation](https://developer.wordpress.org/plugins/hooks/) on them in the Plugin Handbook.
 -->

技術的には、フックは「プラグイン API」の一部であり、プラグイン・ハンドブックでそれらに関する [ドキュメントを確認](https://developer.wordpress.org/plugins/hooks/) できます。

<!-- 
Despite being in the Plugin API, hooks are also extremely useful in the context of themes. Like plugins, you should always run your code on a hook so that it performs its functionality at the appropriate point in the load process.
 -->

プラグイン API の一部であるにもかかわらず、フックはテーマの文脈においても、非常に有用です。プラグインと同様に、フック上で常にコードを実行するようにすることで、ロードプロセスにおける適切なタイミングで、その機能を果たすことができます。

<!-- 
Throughout this handbook, you will see examples of adding features or functionality from `functions.php`, and these examples will always use a hook. Familiarizing yourself with their documentation will make it easier to understand PHP code in the handbook.
 -->

ハンドブック全体を通じて、`functions.php` から機能を追加する例が複数登場しますが、これらの例では必ずフックが使用されます。それらのドキュメントに慣れることで、ハンドブック内の PHP コードを理解しやすくなります。

<!-- 
### Theme setup function
 -->

### テーマのセットアップ機能

<!-- 
One common use case for many themes is adding a setup function, which is generally used to register theme-supported features with WordPress. This is almost always executed on the `after_setup_theme` action hook, which is the first hook available after a theme’s `functions.php` file has been loaded.
 -->

多くのテーマでよく使用されるユースケースのひとつは、セットアップ関数の追加で、通常、WordPress にテーマがサポートする機能を登録するために使用されます。これはほとんどの場合、これは、テーマの `functions.php` ファイルがロードされた後に最初に利用可能なフックである、`after_setup_theme` アクションフックで実行されます。

<!-- 
To test this, open your theme’s `functions.php` file (create one if it doesn’t exist), and add the following PHP code:
 -->

これをテストするには、テーマの `functions.php` ファイルを (存在しない場合は作成して) 開き、以下の PHP コードを追加してください:

<!-- 
```php
<?php
add_action( 'after_setup_theme', 'theme_slug_setup' );

function theme_slug_setup() {
	add_theme_support( 'wp-block-styles' );
}
```
 -->

```php
<?php
add_action( 'after_setup_theme', 'theme_slug_setup' );

function theme_slug_setup() {
	add_theme_support( 'wp-block-styles' );
}
```

<!-- 
This code adds support for WordPress’ more-opinionated block styles to your theme. You do not have to use this; it is merely serving as an example of what a setup function might look like.
 -->

このコードは、あなたのテーマに対して、WordPress のより個性的なブロック・スタイルへのサポートを追加します。これを使用する必要はありません; これは、セットアップ関数の例としてのみ機能します。

<!-- 
Setup functions are more common in classic themes. When using a block theme, the theme is often automatically opted into the features needed. You can find a list of theme-supported features here:
 -->

クラシック・テーマでは、セットアップ関数がより一般的に使用されています。ブロック・テーマを使用する場合、テーマは通常、必要な機能が自動的に有効化されます。テーマがサポートする機能のリストは、以下から確認できます:

<!-- 
*   [Function Reference: `add_theme_support()`](https://developer.wordpress.org/reference/functions/add_theme_support/)
*   [Block Editor Handbook: Theme Support](https://developer.wordpress.org/block-editor/how-to-guides/themes/theme-support/)
 -->

*   [関数リファレンス: `add_theme_support()`](https://developer.wordpress.org/reference/functions/add_theme_support/)
*   [ブロックエディター・ハンドブック: テーマ・サポート](https://developer.wordpress.org/block-editor/how-to-guides/themes/theme-support/)

<!-- 
### Loading scripts and styles
 -->

### スクリプトとスタイルのロード

<!-- 
If you are familiar with HTML, you will likely have come across adding JavaScript via the `<script>` tag or stylesheets via the `<link rel=”stylesheet”/>` or `<style>`  tags.
 -->

HTML に馴染みがある人なら、`<script>` タグを使用して JavaScript を追加したり、`<link rel=”stylesheet”/>` や `<style>`  タグを使用してスタイルシートを追加したりした経験があるかもしれません。

<!-- 
WordPress provides helper functions and specific action hooks for loading scripts and styles. This ensures that they are injected at the appropriate place in the document output. WordPress creates the appropriate HTML markup for you.
 -->

WordPress は、スクリプトとスタイルのロードのための、ヘルパー関数と特定のアクションフックを提供しています。これにより、それらがドキュメント出力の適切な場所に挿入されることが保証されます。WordPress は、適切な HTML マークアップを自動的に作成します。

<!-- 
You can learn more about loading scripts and styles in the [Including Assets](https://developer.wordpress.org/themes/core-conepts/including-assets/) documentation.
 -->

スクリプトとスタイルのロードに関する詳細については、[アセットを含める](https://developer.wordpress.org/themes/core-conepts/including-assets/) ドキュメントをご覧ください。

<!-- 
It is not uncommon when building block themes to have no need of including additional scripts/styles. Some themes rely entirely on [Global Settings and Styles](https://developer.wordpress.org/themes/core-concepts/global-settings-and-styles/) for the front-end design.
 -->

ブロック・テーマを作成する際、追加のスクリプトやスタイルを組み込む必要がないことは珍しくありません。一部のテーマは、フロントエンドの設計において [グローバル設定とスタイル](https://developer.wordpress.org/themes/core-concepts/global-settings-and-styles/) に完全に依存しています。

<!-- 
## Including other PHP files
 -->

## 他 PHP ファイルのインクルード

<!-- 
WordPress will automatically load your theme’s `functions.php` for you, but you are not limited to only adding custom PHP code in that file. You can load other files with PHP interfaces, classes, traits, and functions from elsewhere in your theme.
 -->

WordPress は、あなたのテーマの `functions.php` を自動的にロードしますが、そのファイルにカスタム PHP コードを追加するだけにとどめる必要はありません。あなたのテーマ内のどこからでも、PHP インターフェース、クラス、特性、関数を含む他のファイルをロードできます。

<!-- 
As you learned in [Theme Structure](https://developer.wordpress.org/themes/core-concepts/theme-structure/), some themes include a custom folder named `/inc` (or any custom folder) to store custom PHP files. Let’s assume you had an `/inc/helpers.php` file for custom helper functions, you could load it via `functions.php` using the `get_parent_theme_file_path()` function:
 -->

[テーマ構造](https://developer.wordpress.org/themes/core-concepts/theme-structure/) で学んだように、一部のテーマには、カスタム PHP ファイルを格納するための `/inc` という (または任意の) 名前のカスタムフォルダーが含まれています。仮にカスタムヘルパー関数用の `/inc/helpers.php` ファイルがあった場合、`get_parent_theme_file_path()` 関数を使用して、`functions.php` 経由でロードできます:

<!-- 
```php
include get_parent_theme_file_path( 'inc/helpers.php' );
```
 -->

```php
include get_parent_theme_file_path( 'inc/helpers.php' );
```

<!-- 
Generally speaking, you should use this function to get the correct directory path to any PHP file you need to load.
 -->

一般的に言えば、ロードする必要がある PHP ファイルの正しいディレクトリパスを取得するには、この関数を使用すべきです。

<!-- 
Alternatively, if you wanted to allow a child theme to override the file with a fallback to the parent theme, you could use `get_theme_file_path()` instead:
 -->

代わりに、子テーマがファイルを上書きできるようにし、親テーマへのフォールバックを許可したい場合は、代わりに `get_theme_file_path()` を使用できます:

<!-- 
```php
include get_theme_file_path( 'inc/helpers.php' );
```
 -->

```php
include get_theme_file_path( 'inc/helpers.php' );
```

<!-- 
It’s not standard practice to let child theme’s override files with PHP functions or classes, but there are use cases where it’s needed.
 -->

子テーマが PHP 関数やクラスを使用してファイルを上書きすることは標準的な慣行ではありませんが、必要となるユースケースは存在します。

<!-- 
## Avoid closing ?> tags at the end of files
 -->

## ファイル末尾での `?>` タグの回避

<!-- 
This section could otherwise be titled “How to avoid the dreaded WordPress *white screen of death*.”
 -->

このセクションは、代わりに「WordPress の *死の白い画面* の回避」という見出しでもよいでしょう。

<!-- 
There are various reasons that you might see a broken site with nothing but a white screen. One of those reasons is when the `functions.php` file (or any PHP file) has whitespace following its closing `?>` tag like this:
 -->

Web サイトが白一色の画面しか表示されない理由はさまざまです。その理由の一つは、`functions.php` ファイル (または任意の PHP ファイル) の終了タグ `?>` の後に、このように、空白行が挿入されている場合です:

<!-- 
```php
<?php
// some code...
?>
 
```
 -->

```php
<?php
// 何らかのコード…
?>
 
```

<!-- 
Many editor configurations will automatically add an extra line at the end of files (a common development practice). When you add a closing `?>` tag at the end of the file, it can be easy to miss this extra whitespace, which may cause the “white screen of death” in some environments.
 -->

多くのエディター設定では、ファイルの末尾に自動的に追加の行が挿入されます (一般的な開発慣行)。ファイルの末尾に終了タグ `?>` を追加する際、この追加の空白を簡単に見逃してしまい、一部の環境では「死の白い画面」と呼ばれるエラーが発生する可能性があります。

<!-- 
The easiest way to avoid this issue is to leave the closing `?>` tag out altogether, which is perfectly valid PHP and standard practice. The above code should be written as:
 -->

この問題を回避する最も簡単な方法は、終了タグ `?>` を完全に省略することで、これは完全に有効な PHP であり、標準的な慣行です。上記のコードは次のように記述する必要があります:

<!-- 
```php
<?php
// some code...
 
```
 -->

```php
<?php
// 何らかのコード…
 
```