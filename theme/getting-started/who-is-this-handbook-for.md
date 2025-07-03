<!-- 
# Who Is This Handbook For?
 -->

# このハンドブックの対象者は ?

<!-- 
The Theme Developer Handbook is a self-contained resource to help you learn the fundamental principles of creating a WordPress theme. It covers a range of topics that span the basics to advanced development.
 -->

テーマ開発者ハンドブックは、WordPress テーマ制作の基本原則を学ぶのに役立つ、自己完結型の参考資料です。このハンドブックでは、基礎から高度な開発まで、幅広いトピックをカバーしています。

<!-- 
You should read this handbook if you want to:
 -->

下記に該当する人は、このハンドブックを読むべきでしょう:

<!-- 
*   Create a theme based on nothing but your imagination
*   Build a new theme based on an existing one
*   Extend another theme by creating a child theme
*   Understand how themes work 
 -->

*   想像力のみにもとづいて、テーマを制作したい
*   既存のテーマをベースに、新しいテーマを構築したい
*   子テーマを制作することで、別のテーマを拡張したい
*   テーマのしくみを理解したい

<!-- 
Regardless of your reasons for starting down this adventure, this handbook will help you take the next steps toward building a WordPress theme of your own.
 -->

どのような理由でこの冒険を始めたにせよ、独自の WordPress テーマを構築するための次のステップを踏み出すのに、このハンドブックは役立つでしょう。

<!-- 
## Your skill level
 -->

## あなたのスキルレベル

<!-- 
While not a strict requirement, you will get the most out of this handbook if you have a baseline understanding and some experience with web technologies, such as HTML, CSS, and PHP. JavaScript knowledge would be a bonus if you plan to add interactivity to the front end.
 -->

厳密な要件ではありませんが、HTML、CSS、PHP などの Web 技術に関する基本的な理解とある程度の経験があれば、このハンドブックを最大限に活用できるでしょう。フロントエンドにインタラクティブ性を追加するつもりなら、JavaScript の知識はボーナスになるでしょう。

<!-- 
Present-day WordPress and its block theme system allow you to customize and export a theme directly from the Site Editor interface:
 -->

現在、WordPress とそのブロック・テーマシステムでは、サイトエディターのインターフェースから、直接テーマをカスタマイズしてエクスポートできます:

<!-- 
[![WordPress Site Editor with the options menu dropdown open on the right. The Export option is highlighted.](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-three-export.jpg?resize=2400%2C1250&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-three-export.jpg?ssl=1)
 -->

[![WordPress サイトエディターの右側で、オプションメニューのドロップダウンを開く。エクスポートオプションがハイライトされている。](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-three-export.jpg?resize=2400%2C1250&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-three-export.jpg?ssl=1)

<!-- 
Exporting a variation of the core Twenty Twenty-Three theme.
 -->

コアの Twenty Twenty-Three テーマのバリエーションをエクスポートする。

<!-- 
With each major WordPress update, its visual building tools become even more robust. Still, having some basic HTML, CSS, and PHP knowledge will help you move along faster.
 -->

WordPress のメジャーアップデートごとに、そのビジュアル構築ツールはさらに強力になってきています。それでも、基本的な HTML、CSS、PHP の知識があれば、より迅速に作業を進めることができるでしょう。

<!-- 
Unlike block themes, [classic themes](https://developer.wordpress.org/themes/classic-themes/) are built entirely from code. This requires that you be comfortable enough to edit one or more of those languages to some degree.
 -->

ブロック・テーマとは異なり、[クラシック・テーマ](https://developer.wordpress.org/themes/classic-themes/) は完全にコードから構築されます。そのため、1つ以上のこれらの言語をある程度編集できるくらいの慣れが必要です。

<!-- 
The [Reading this handbook](https://developer.wordpress.org/themes/getting-started/reading-this-handbook/) page has more information on the prerequisite knowledge you need to build themes.
 -->

[このハンドブックを読む](https://developer.wordpress.org/themes/getting-started/reading-this-handbook/) ページには、テーマを構築するために必要な前提知識についての詳細情報が記載されています。

<!-- 
At the very least, you must be able to set up and configure a website using WordPress. Otherwise, you won’t be able to test or use the theme that you are building. You can learn more about getting things running in the [Tools and setup](https://developer.wordpress.org/themes/getting-started/tools-and-setup/) documentation.
 -->

最低限、WordPress を使って Web サイトのセットアップおよび構成できる必要があります。そうしないと、構築中のテーマをテストしたり使用したりできません。[ツールとセットアップ](https://developer.wordpress.org/themes/getting-started/tools-and-setup/) のドキュメントで、より詳しく学ぶことができます。

<!-- 
## What this handbook covers
 -->

## このハンドブックがカバーするもの

<!-- 
This handbook provides the basic information you need to build both block and classic WordPress themes. This includes in-depth coverage of the essential features and APIs that you should know, such as the topics in the [Core Concepts](https://developer.wordpress.org/themes/core-concepts/) chapter. It also dives into tools and techniques for building more advanced themes in the [Advanced Topics](https://developer.wordpress.org/themes/advanced-topics/) chapter.
 -->

このハンドブックでは、ブロックとクラシックの WordPress テーマの両方を構築するために必要な基本情報を提供します。これには、[コア・コンセプト](https://developer.wordpress.org/themes/core-concepts/) 章で取り上げているトピックなど、知っておくべき重要な機能や API が詳しく網羅されています。また、[上級者向けトピック](https://developer.wordpress.org/themes/advanced-topics/) 章では、より高度なテーマを構築するためのツールやテクニックについても踏み込んでいます。

<!-- 
WordPress is a vast subject. HTML, CSS, PHP, accessibility, and other web technologies are even larger. It’d be impossible to cover every aspect of building a website in this handbook alone. Therefore, it is highly-focused on the fundamentals of theme building.
 -->

WordPress は広大な主題です。HTML、CSS、PHP、アクセシビリティ、その他の Web 技術はさらに膨大です。このハンドブックだけで、Web サイト構築のあらゆる側面のカバーは不可能でしょう。そのため、このハンドブックはテーマ構築の基礎に焦点を当てています。

<!-- 
The goal of this handbook is to give you a solid foundation for WordPress theme creation by providing step-by-step instructions for building basic themes and providing resources to further your skills.
 -->

このハンドブックのゴールは、基本的なテーマの構築方法をステップ・バイ・ステップで説明し、さらにスキル向上に役立つ参考資料を提供することで、WordPress テーマ制作の確固たる基礎を築くことです。

<!-- 
If this sounds like something you’d be interested in, come along. You’re in for a journey.
 -->

少しでも興味が湧いたら、この度にぜひ参加してください。旅の始まりです。