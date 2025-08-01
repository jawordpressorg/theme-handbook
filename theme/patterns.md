<!-- 
# Patterns
 -->

# パターン

<!-- 
Patterns are one of the most useful tools for theme development, allowing you to reuse groups of blocks across a wide variety of scenarios. Over time, you will likely use patterns more than any other theme feature available in WordPress.
 -->

パターンはテーマ開発において最も有用なツールのひとつであり、さまざまなシナリオにわたってブロックのグループを再利用できます。長期的には、WordPress の他のどのテーマ機能よりもパターンを使うことになるでしょう。

<!-- 
In this chapter, you will learn what patterns are and dive into the various use cases where you will apply them in your themes. This will include everything from providing insertable layouts to your theme users to running PHP for loading assets and even more.
 -->

本章では、パターンとは何かを学び、あなたのテーマでパターンを適用するさまざまなユースケースに踏み込みます。これには、あなたのテーマユーザーにインサート可能なレイアウトを提供することから、アセットをロードするための PHP の実行など、あらゆることが含まれます。

<!-- 
## Navigating this chapter
 -->

## 本章のナビゲーション

<!-- 
Use the following links to locate a specific topic within this chapter. It’s best to read them in order, but if you are already familiar with the basic tenets of pattern development, feel free to jump to the topic that you’re looking for.
 -->

本章の特定のトピックを探すには、以下のリンクをご利用ください。順番に読むのがベストですが、すでにパターン開発の基本的な考え方に慣れている人は、お探しのトピックに自由にジャンプしてください。

<!-- 
*   [**Introduction to Patterns**](https://developer.wordpress.org/themes/patterns/introduction-to-patterns/)**:** Provides an overview of what patterns are and how they work, giving you a foundation for later articles in the chapter.
*   [**Registering Patterns**](https://developer.wordpress.org/themes/patterns/registering-patterns/)**:** A guide on registering/unregistering patterns and pattern categories for your theme.
*   [**Using PHP in Patterns**](https://developer.wordpress.org/themes/patterns/using-php-in-patterns/)**:** How and why to use PHP in your themes, including practical applications like internationalizing text and including media.
*   [**Usage in Templates**](https://developer.wordpress.org/themes/patterns/usage-in-templates/)**:** How to include patterns in templates and why you should use them over templates in many cases.
*   [**Block Type Patterns**](https://developer.wordpress.org/themes/patterns/block-type-patterns/)**:** A walkthrough of creating block-specific patterns that offer a more elegant experience for your theme users.
*   [**Starter Patterns**](https://developer.wordpress.org/themes/patterns/starter-patterns/)**:** Building custom patterns as starting points for creating starting points for your theme users to build their pages and templates.
*   [**Patterns and Block Locking**](https://developer.wordpress.org/themes/patterns/patterns-and-block-locking/)**:** How to use the Block Locking API to curate the editing experience for your theme users.
 -->

*   [**パターン入門**](https://developer.wordpress.org/themes/patterns/introduction-to-patterns/)**:** パターンとは何か、パターンのしくみとは何かについて概説し、本章以降の記事の基礎とします。
*   [**パターンの登録**](https://developer.wordpress.org/themes/patterns/registering-patterns/)**:** あなたのテーマへのパターンとパターン・カテゴリーの登録/登録解除に関するガイドです。
*   [**パターンで PHP の利用**](https://developer.wordpress.org/themes/patterns/using-php-in-patterns/)**:** テキストの国際化やメディアのインクルードなどの実用的なアプリケーションを含む、あなたのテーマで PHP を使用する方法と理由です。
*   [**テンプレートでの使用法**](https://developer.wordpress.org/themes/patterns/usage-in-templates/)**:** テンプレートにパターンを含める方法と、多くのケースでテンプレートよりもパターンを使うべき理由です。
*   [**ブロック・タイプ・パターン**](https://developer.wordpress.org/themes/patterns/block-type-patterns/)**:** ブロックに特化したパターンを制作することで、あなたのテーマのユーザーに対して、よりエレガントな体験を提供するための手順です。
*   [**「スターター」パターン**](https://developer.wordpress.org/themes/patterns/starter-patterns/)**:** あなたのテーマユーザーがページやテンプレートを構築するための、出発点となるカスタムパターンを構築します。
*   [**パターンとブロックのロック機能**](https://developer.wordpress.org/themes/patterns/patterns-and-block-locking/)**:** Block Locking API を使用して、あなたのテーマユーザーの編集体験を魅力的なものにする方法です。