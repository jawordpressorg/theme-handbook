<!-- 
# Global Settings and Styles (theme.json)
 -->

# グローバル設定とスタイル (theme.json)

<!-- 
Welcome to the Global Settings and Styles documentation. In this chapter you will learn everything you need to know about configuring settings, styles, and more via your theme’s `theme.json` file.
 -->

「グローバル設定とスタイル」ドキュメントにようこそ。本章では、あなたのテーマの `theme.json` ファイルを介して設定、スタイルなどを構成するために必要なすべてを学びます。

<!-- 
`theme.json` is a foundational piece of block theming. While it is not a strictly required file, you will need to work with it for nearly any theme project. It is useful for everything from configuring colors to defining default typography settings to applying front-end styles to your theme.
 -->

`theme.json` は、ブロック・テーマの基盤となる重要な要素です。厳密には必須ファイルではありませんが、ほぼすべてのテーマ・プロジェクトで扱う必要があります。色の設定からデフォルトのタイポグラフィ設定の定義、あなたのテーマへのフロントエンド・スタイルの適用に至るまで、あらゆる場面で有用です。

<!-- 
## Navigating this chapter
 -->

## 本章の進め方

<!-- 
Use the below links to find the topic you are looking for in this chapter. Each section of the chapter is set up to offer a straightforward learning path toward learning the ins-and-outs of `theme.json` for first-time themers. But if you are already familiar with the foundational concepts, feel free to skip ahead to the topic you want to learn more about.
 -->

以下のリンクから、本章でお探しのトピックを見つけてください。各セクションは、初めてテーマを作成する人が `theme.json` の詳細を学ぶための、わかりやすい学習経路を提供するように、構成されています。ただし、基礎的な概念にすでに精通している場合は、さらに学びたいトピックに自由に進んでください。

<!-- 
*   [**Introduction to `theme.json`**](https://developer.wordpress.org/themes/global-settings-and-styles/introduction-to-theme-json/)**:** A walkthrough of setting up your `theme.json` file, introducing you to the foundational concepts for configuring global settings and styles for your theme.
*   [**Settings**](https://developer.wordpress.org/themes/global-settings-and-styles/settings/)**:** Documentation for each of the standard and custom settings that you can configure via `theme.json`. Sub-pages document every available setting.
*   [**Styles**](https://developer.wordpress.org/themes/global-settings-and-styles/styles/)**:** Learn how to use the standard design system to apply styles through `theme.json`, which also integrate with the user interface.
*   [**Custom Templates**](https://developer.wordpress.org/themes/global-settings-and-styles/custom-templates/)**:** How to register custom post, page, and CPT (custom post type) templates for your theme.
*   [**Template Parts**](https://developer.wordpress.org/themes/global-settings-and-styles/template-parts/)**:** How to register custom template parts that can be reused across your theme.
*   [**Patterns**](https://developer.wordpress.org/themes/global-settings-and-styles/patterns/)**:** How to bundle patterns from the official patterns repository with your theme.
*   [**Style Variations**](https://developer.wordpress.org/themes/global-settings-and-styles/style-variations/)**:** Documentation on creating custom `theme.json` style variations, giving your users alternative designs to choose from.
 -->

*   [**`theme.json` の紹介**](https://developer.wordpress.org/themes/global-settings-and-styles/introduction-to-theme-json/)**:** あなたの `theme.json` ファイルの設定手順を解説し、あなたのテーマに対してグローバル設定やスタイルを構成するための基礎概念を紹介します。
*   [**設定**](https://developer.wordpress.org/themes/global-settings-and-styles/settings/)**:** `theme.json` 経由で設定可能な、標準設定およびカスタム設定のドキュメントです。サブページでは、利用可能なすべての設定をドキュメント化しています。
*   [**スタイル**](https://developer.wordpress.org/themes/global-settings-and-styles/styles/)**:** 標準デザイン・システムを使用して、`theme.json` を通じてスタイルを適用する方法を学びます。これらは UI とも統合されます。
*   [**カスタム・テンプレート**](https://developer.wordpress.org/themes/global-settings-and-styles/custom-templates/)**:** あなたのテーマ用にカスタム投稿、ページ、および CPT (カスタム投稿タイプ) テンプレートを登録する方法です。
*   [**テンプレート・パーツ**](https://developer.wordpress.org/themes/global-settings-and-styles/template-parts/)**:** あなたのテーマ全体で再利用可能な、カスタム・テンプレート・パーツを登録する方法です。
*   [**パターン**](https://developer.wordpress.org/themes/global-settings-and-styles/patterns/)**:** 公式パターン・リポジトリのパターンを、あなたのテーマにバンドルする方法です。
*   [**スタイル・バリエーション**](https://developer.wordpress.org/themes/global-settings-and-styles/style-variations/)**:** カスタム `theme.json` スタイル・バリエーションの作成に関するドキュメントで、あなたのユーザーが選択できる、代替デザインを提供します。