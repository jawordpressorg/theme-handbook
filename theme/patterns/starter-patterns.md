<!-- 
# Starter Patterns
 -->

# 「スターター」パターン

<!-- 
The WordPress block editor is powerful and can handle many different layouts and designs. However, when building a theme, you must remember that not all of your users will be skilled designers or even have much interest in piecing together their own layouts. This is where starter patterns can be beneficial to them.
 -->

WordPress のブロック・エディターは強力で、さまざまなレイアウトやデザインに対応しています。しかし、テーマを構築する際には、すべてのユーザーが熟練したデザイナーであるとは限らず、独自のレイアウトを組み立てることにあまり興味がないユーザーもいることを忘れてはなりません。そこで、「スターター」パターンが彼らにとって有益となるのです。

<!-- 
WordPress supports two types of starter patterns for pages (or any post type) and templates. This feature lets you create starting points for your theme users to build out their pages and templates with minimal skills.
 -->

WordPress は、ページ (または任意の投稿タイプ) とテンプレート向けに、2種類の「スターター」パターンをサポートしています。この機能により、あなたのテーマのユーザーが、自分たちのページやテンプレートを構築するための出発点を、最小限のスキルで作成できます。

<!-- 
## Starter page patterns
 -->

## 「スターター」ページ・パターン

<!-- 
Page patterns let you create custom patterns your theme users can access when adding a new page via **Pages > Add New** in their WordPress admin. From there, a modal will pop up and show them a selection of patterns if any are registered.
 -->

ページ・パターンを使用すると、WordPress 管理者画面で **固定ページ > 固定ページを追加** 経由で新規ページを追加する際に、あなたのテーマのユーザーがアクセスできるカスタム・パターンを作成できます。そこから、登録されているパターンがあれば、モーダル・ウィンドウがポップアップし、そのパターンの一覧が表示されます。

<!-- 
Here is what the screen looks like when creating a new page with the default Twenty Twenty-Four theme installed:
 -->

デフォルトの Twenty Twenty-Four テーマがインストールされた状態で、新規ページを作成する際の画面は、以下のようになります:

<!-- 
[![Modal overlaying the edit page screen, showing a grid of various page layouts.](https://i0.wp.com/developer.wordpress.org/files/2024/04/starter-page-pattern-tt4.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/starter-page-pattern-tt4.webp?ssl=1)
 -->

[![編集ページ画面にオーバーレイ表示されるモーダル・ウィンドウで、さまざまなページレイアウトのグリッドが表示される。](https://i0.wp.com/developer.wordpress.org/files/2024/04/starter-page-pattern-tt4.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/starter-page-pattern-tt4.webp?ssl=1)

<!-- 
This is a powerful feature because it means that you can provide well-designed starting points for your theme’s users or clients. And they don’t need to build from scratch. They only need to select a pattern, and it will automatically be inserted into the content area. From there, they can make any customizations they want.
 -->

これは強力な機能で、これにより、あなたのテーマのユーザーやクライアントに、よく設計された出発点を提供できます。彼らはゼロから構築する必要は、ありません。パターンを選択するだけで、それが自動的にコンテンツ・エリアに挿入されます。そこから、彼らは好きなようにカスタマイズできます。

<!-- 
### How to create a page pattern
 -->

### ページ・パターンの制作法

<!-- 
Technically, any pattern in your theme can be converted to a page pattern. All you need to do is define the correct parameters to mark it as such. As described in [Registering Patterns](https://developer.wordpress.org/themes/patterns/registering-patterns/), there are two available file header fields that you must set to make this happen:
 -->

技術的には、あなたのテーマ内の任意のパターンを、ページ・パターンに変換できます。やるべきことは、適切なパラメータを定義して、そのようにマークすることだけです。[パターンの登録](https://developer.wordpress.org/themes/patterns/registering-patterns/) で説明されているように、この機能を実現するために設定するべきファイル・ヘッダー・フィールドは、2つあります:

<!-- 
*   **`Block Types`:** Adding `core/post-content` as one of the block types for the pattern tells WordPress that the pattern should be used for the post content.
*   **`Post Types`:** You can add one or more post types (separated by commas) to connect the pattern.
 -->

*   **`Block Types`:** ブロック・タイプの一つとして、パターンに `core/post-content` を追加すると、そのパターンを投稿コンテンツに使用するように、WordPress に指示します。
*   **`Post Types`:** パターンを接続するために、(カンマで区切った) 1つ以上の投稿タイプを追加できます。

<!-- 
With these two fields combined, you create a starter page pattern. Here is what the file header looks like for a fictional `/patterns/example-page.php` pattern file:
 -->

これらの2つのフィールドを組み合わせることで、「スターター」ページ・パターンを制作します。以下は、架空の `/patterns/example-page.php` パターン・ファイルのファイル・ヘッダーの例です:

```php
<?php
/**
 * Title: Example Page
 * Slug: themeslug/example-page
 * Categories: page
 * Block Types: core/post-content
 * Post Types: page
 * Viewport width: 1376
 */
?>
<!-- Block code here. -->
```

<!-- 
And that’s literally all you must do. Define the pattern’s `Block Types` and `Post Types` parameters and you have a starter page pattern. 
 -->

そして、それがまさに、あなたがしなければならないことのすべてです。パターンの `Block Types` と `Post Types` パラメータを定義すると、「スターター」ページ・パターンが完成します。

<!-- 
This will work with any post type that has opted into the block editor, including both the default `post` and `page` post types.
 -->

これはデフォルトの `post` と `page` 投稿タイプを含む、ブロック・エディターに付属するすべての投稿タイプで機能します。

<!-- 
Because page patterns are actually tied to the content, you wouldn’t typically include something like a site header or footer here. The pattern is output as post content.
 -->

ページ・パターンは、実際にはコンテンツと密接に関連しているため、通常はサイト・ヘッダーやフッターのような要素をここに含めることはありません。パターンは、投稿コンテンツとして出力されます。

<!-- 
## Starter template patterns
 -->

## 「スターター」テンプレート・パターン

<!-- 
Like page patterns, template patterns give users a starting point when building a new template. The difference is that template patterns work from the Site Editor.
 -->

ページ・パターンと同様に、テンプレート・パターンは、新規テンプレートを構築する際の出発点を提供します。テンプレート・パターンは、サイト・エディターから操作する、という点が異なります。

<!-- 
If you visit **Appearance > Editor > Templates** in your WordPress admin and click the **+** icon button for creating a new template, you should see a new **Add template** modal:
 -->

WordPress 管理画面で **外観 > エディター > テンプレート** にアクセスし、新規テンプレートを制作するための **+** アイコン・ボタンをクリックすると、新規 **テンプレート追加** モーダルが表示されます:

<!-- 
[![WordPress site editing screen with a modal popup asking the user to add a new template.](https://i0.wp.com/developer.wordpress.org/files/2024/04/add-template.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/add-template.webp?ssl=1)
 -->

[![WordPress のサイト編集画面に、ユーザーに新規テンプレートの追加を求めるモーダル・ポップアップが表示される。](https://i0.wp.com/developer.wordpress.org/files/2024/04/add-template.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/add-template.webp?ssl=1)

<!-- 
From there, you can select the template that you want to create. If the template type has any patterns registered for it, a new **Choose a pattern** modal will appear, overlaying the template-editing interface.
 -->

そこから、作成したいテンプレートを選択できます。テンプレート・タイプにパターンが登録されている場合、テンプレート編集インターフェースの上に、新規 **パターン選択** モーダルが表示されます。

<!-- 
For example, when choosing the **Front Page** option with the default Twenty Twenty-Four theme, you will see this:
 -->

たとえば、デフォルトの Twenty Twenty-Four テーマで **フロントページ** オプションを選択すると、次のように表示されます:

<!-- 
[![A modal overlay showing four template options for the homepage from within the WordPress site editor.](https://i0.wp.com/developer.wordpress.org/files/2024/04/starter-template-patterns-tt4.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/starter-template-patterns-tt4.webp?ssl=1)
 -->

[![WordPress サイト・エディターから、ホームページの 4 つのテンプレート・オプションを表示するモーダル・オーバーレイ。](https://i0.wp.com/developer.wordpress.org/files/2024/04/starter-template-patterns-tt4.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/starter-template-patterns-tt4.webp?ssl=1)

<!-- 
This gives your theme users a really nice onramp for building templates. It means they don’t have to create everything from the ground up and can get started down the right path.
 -->

これにより、あなたのテーマのユーザーは、テンプレートを構築するための、非常に便利な出発点を手に入れることができます。つまり、彼らはすべてをゼロから構築する必要がなく、正しい道筋でスタートを切れ、すぐに作業を開始できます。

<!-- 
### How to create template type patterns
 -->

### テンプレートタイプ・パターンの制作法

<!-- 
Unlike page patterns, you will usually not make any of your patterns a template pattern. These are starting points for an entire template, so their use cases are much more limited and specific.
 -->

ページ・パターンとは異なり、通常はあなたのパターンを、テンプレート・パターンとして作成することはありません。これらはテンプレート全体の出発点となるため、ユースケースはもっと限定的で具体的です。

<!-- 
Because template patterns represent an entire template, you would typically include global elements like the header, footer, sidebar, and other sections that your theme’s templates display.
 -->

テンプレート・パターンはテンプレート全体を表すため、ヘッダー、フッター、サイドバー、およびあなたのテーマのテンプレートに表示される他のセクション、などのグローバル要素を含めるのが一般的です。

<!-- 
As noted in [Registering Patterns](https://developer.wordpress.org/themes/patterns/registering-patterns/), there is a single required header field needed for your template pattern (and one optional field):
 -->

[パターンの登録](https://developer.wordpress.org/themes/patterns/registering-patterns/) で説明されているように、あなたのテンプレート・パターンには、必須ヘッダー・フィールドが1つ (そして、任意のフィールドが1つ) 必要です:

<!-- 
*   **`Template Types`:** One or more template types, separated by comma, that the pattern should be associated with.
*   **`Inserter`:** *(Optional)* Often, you will not want template patterns to be available via the inserter. To disable this, set it to `no` or `false`.
 -->

*   **`Template Types`:** パターンが関連付けられるテンプレート・タイプを、1つ以上カンマで区切って指定します。
*   **`Inserter`:** *(任意)* しばしば、テンプレート・パターンをインサーター経由で利用可能にしたくない場合があります。これを無効にするには、`no` または `false` に設定します。

<!-- 
Suppose that you created a pattern that would work well for the Front Page or Home templates. Here is what a fictional `/patterns/home-template.php` file would look like:
 -->

仮に、「フロントページ」テンプレートまたは「ホーム」テンプレートに最適なパターンを制作したとします。以下は、架空の `/patterns/home-template.php` ファイルの例です:

```php
<?php
/**
 * Title: Home Template
 * Slug: themeslug/home-template
 * Template Types: front-page, home
 * Viewport width: 1376
 * Inserter: no
 */
?>
<!-- Block code here. -->
```

<!-- 
From that point, anytime a user attempted to create a new Front Page or Home template from the WordPress Site Editor, they would be presented with your template pattern as a starting point.
 -->

それ以降、ユーザーが WordPress サイト・エディターから新しい「フロントページ」テンプレートまたは「ホーム」テンプレートを制作しようとすると、あなたのテンプレート・パターンが出発点として提示されます。

<!-- 
### Supported template types
 -->

### 対応テンプレート・タイプ

<!-- 
The following list includes the templates that you can define via the `Template Types` field, but you can always reference the [Template Hierarchy](https://developer.wordpress.org/themes/templates/template-hierarchy/) documentation for a full overview of templates:
 -->

以下のリストには、`Template Types` フィールド経由で定義可能なテンプレートが含まれていますが、常に [テンプレート階層](https://developer.wordpress.org/themes/templates/template-hierarchy/) ドキュメントを参照することで、テンプレートの全体像を把握できます:

*   `index`
*   `home`
*   `front-page`
*   `singular`
*   `single`
*   `page`
*   `archive`
*   `author`
*   `category`
*   `taxonomy`
*   `date`
*   `tag`
*   `attachment`
*   `search`
*   `privacy-policy`
*   `404`

<!-- 
### Using template patterns in templates
 -->

### テンプレートでの、テンプレート・パターンの使用

<!-- 
When creating custom template patterns, it also makes sense to reuse those patterns within your templates. *Why rewrite code?*
 -->

カスタム・テンプレート・パターンを制作する際は、あなたのテンプレート内で、それらのパターンを再利用することも有効です。*なぜコードを再記述するのですか ?*

<!-- 
Imagine that you created a template pattern that would work as both a Home and Index template. It would look like this:
 -->

「ホーム」テンプレートと「インデックス」テンプレートの両方として機能する、テンプレート・パターンを制作したと想像してください。次のようなものになります:

```php
<?php
/**
 * Title: Index Template
 * Slug: themeslug/index-template
 * Template Types: home, index
 * Viewport width: 1376
 * Inserter: no
 */
?>
<!-- Block code here. -->
```

<!-- 
Now suppose that you included a `/templates/index.html` template in your theme. Instead of adding the code in two places, you can simply call the pattern from the template file:
 -->

では、あなたのテーマに `/templates/index.html` テンプレートを含めたと仮定しましょう。2ヵ所にコードを追加する代わりに、テンプレートファイルからそのパターンを呼び出すだけです:

```markup
<!-- wp:pattern {"slug":"themeslug/index-template"} /-->
```

<!-- 
To learn more about including patterns in templates, check out the [Usage in Templates](https://developer.wordpress.org/themes/patterns/usage-in-templates/) documentation.
 -->

テンプレートにパターンを含める方法について詳しく知りたい場合は、[テンプレートでの使用法](https://developer.wordpress.org/themes/patterns/usage-in-templates/) ドキュメントをご確認ください。