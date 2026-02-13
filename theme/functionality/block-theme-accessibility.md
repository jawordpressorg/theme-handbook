<!-- 
# Block theme accessibility
 -->

# ブロック・テーマのアクセシビリティ

<!-- 
Block themes support accessibility and simplify the process for adding accessibility.
 -->

ブロックテーマは、アクセシビリティをサポートし、アクセシビリティ追加についてのプロセスを簡素化します。

<!-- 
## Landmark
 -->

## ランドマーク

<!-- 
Group, Template part, and Query blocks can become a landmark. There are two ways to create landmark.
 -->

「グループ」、「テンプレート・パーツ」そして「クエリー」ブロックは、ランドマークにできます。ランドマークを作成するには、2つの方法があります。

<!-- 
**Using block markup**  
 -->

**Using block markup**  

<!-- 
`”tagName":"header”` creates header landmark.
 -->

`”tagName":"header”` は、ヘッダー・ランドマークを作成します。

```
<!-- wp:group {"tagName":"header","layout":{"type":"constrained"}} -->
<header class="wp-block-group"><!-- wp:site-title /--></header>
<!-- /wp:group -->
```

<!-- 
**Using site editor**  
 -->

**サイト・エディターの使用**  

<!-- 
HTML element under Advanced section in the Block panel provides the following landmark options.  
 -->

「ブロック」パネルの「詳細」セクション下の HTML 要素には、以下のランドマーク・オプションが用意されています。

<!-- 
HTML element under Advanced section in the Block panel provides the following landmark options.  
 -->

「ブロック」パネルの「詳細」セクション下の HTML 要素には、以下のランドマーク・オプションが用意されています。

<!-- 
`<header>` `<main>` `<section>` `<article>` `<aside>` `<footer>`.
 -->

`<header>`、`<main>`、`<section>`、`<article>`、`<aside>`、`<footer>`。

<!-- 
## Skip to content
 -->

## コンテンツにスキップ

<!-- 
By selecting `<main>` landmark on Group, Template part, or Query block generates the Skip to Content link. Learn more about the [skip to content link here](https://make.wordpress.org/themes/handbook/review/required/#3-accessibility).
 -->

「グループ」、「テンプレート・パーツ」、または「クエリー」ブロックで `<main>` ランドマークを選択することで、「コンテンツにスキップ」リンクが生成されます。[コンテンツにスキップ・リンク](https://make.wordpress.org/themes/handbook/review/required/#3-accessibility) の詳細は、こちらをご覧ください。

```
<!-- wp:group {"tagName":"main","layout":{"type":"constrained"}} -->
<main class="wp-block-group"><!-- wp:heading -->
<h2 id="hello-world">Hello World</h2>
<p>Welcome to WordPress. This is your first post. </p>
<!-- /wp:heading -->
```

<!-- 
## Accessible navigation menu
 -->

## アクセス容易なナビゲーション・メニュー

<!-- 
Navigation block enables the following accessibility without additional code.
 -->

「ナビゲーション」ブロックは、追加のコードなしで、以下のアクセシビリティを実現します。

<!-- 
*   Support responsive view
*   Support keyboard navigation
*   Insert `<nav>` landmark role
*   Insert ARIA attributes `aria-label` `aria-hidden`
 -->

*   レスポンシブ表示のサポート
*   キーボード操作のサポート
*   `<nav>` ランドマーク・ロールの挿入
*   ARIA 属性 `aria-label`、`aria-hidden` の挿入

<!-- 
## Additional resources
 -->

## 追加リソース

<!-- 
*   [Accessibility](https://make.wordpress.org/themes/handbook/review/accessibility/)
 -->

*   [アクセシビリティ](https://make.wordpress.org/themes/handbook/review/accessibility/)

<!-- 
Changelog:
 -->

変更履歴:

<!-- 
*   **Updated** 2023-03-08 Updated code examples to reflect WordPress 6.1 block markup.
*   **Created** 2022-01-25
 -->

*   **更新** 2023-03-08: WordPress 6.1のブロック・マークアップを反映するため、コード例を更新。
*   **作成** 2022-01-25