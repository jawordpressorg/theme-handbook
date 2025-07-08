<!-- 
# Quick-Start Guide
 -->

# クイック・スタートガイド

<!-- 
The first step is always the hardest to take. Now that you’ve made it this far into the Getting Started chapter, you’ve already taken several steps. Congratulations on getting through all of the necessary setup.
 -->

最初のステップが最も難しいものです。この「はじめに」章までたどり着いたあなたは、すでにいくつかのステップを踏み出しています。必要なセットアップをすべて完了させたこと、おめでとうございます。

<!-- 
In a way, actually building your first theme can feel like another first step, but you are ready to trek out into the wilderness and beyond. Don’t worry—this guide will walk with you as you set out on this journey.
 -->

ある意味では、あなたの最初のテーマを構築することは、また別の最初のステップのように感じられるかもしれませんが、あなたはすでに、未知の領域へと踏み出す準備ができています。心配しないでください — このガイドは、あなたがこの旅に出発する際に、あなたとともに歩んでいきます。

<!-- 
## Activating your first theme
 -->

## あなたの最初のテーマを有効化する

<!-- 
One of the best ways to understand how to build themes is to look at and study existing themes. 
 -->

テーマを構築する方法を理解する最も良い方法の一つは、既存のテーマを観察し、研究することです。

<!-- 
Even in advanced development circles, one of the cornerstones of sound development is to reuse code. This is because developers understand that this is the most efficient way to get things done, and many try to abide by the “don’t reinvent the wheel” mantra.
 -->

先進的な開発サークルにおいても、健全な開発の基盤の一つはコードの再利用です。これは、開発者が最も効率的な方法であると理解しているためであり、多くの開発者が「車輪の再発明を避ける」原則に従おうとしています。

<!-- 
Regardless of whether you are a developer, this is sound advice. You don’t need to build everything from scratch. There’s a good chance that most of what you want to do has already been created by someone else.
 -->

あなたが開発者かどうかにかかわらず、これは有益なアドバイスです。すべてをゼロから作る必要はありません。あなたがやりたいことのほとんどは、すでに誰かが作成している可能性が高いです。

<!-- 
So, your next step is to activate an existing theme.
 -->

では、次のステップは、既存テーマの有効化です。

<!-- 
### Choosing a theme to learn from
 -->

### 学習するテーマを選ぶ

<!-- 
Packaged in every version of WordPress since version 3.0 (and named after the year they were released in), the default themes are some of the best to study how themes are built. This is because they are designed with broad use in mind and fully adhere to WordPress coding standards.
 -->

WordPress バージョン3.0以降、すべてのバージョンに標準で同梱されている (リリース年を名前に冠する) デフォルトテーマは、テーマの構築方法を学ぶうえで最も優れた例の一つです。これは、これらのテーマが幅広い用途を想定して設計されており、WordPress のコーディング標準に完全に準拠しているためです。

<!-- 
Because this handbook primarily focuses on modern, block theming, you should choose one of the newest default themes:
 -->

このハンドブックは主にモダンなブロック・テーマに焦点を当てているため、最新のデフォルトテーマのいずれかを選択する必要があります:

<!-- 
*   [Twenty Twenty-Four](https://wordpress.org/themes/twentytwentyfour/)
*   [Twenty Twenty-Three](https://wordpress.org/themes/twentytwentythree/)
*   [Twenty Twenty-Two](https://wordpress.org/themes/twentytwentytwo/) 
 -->

*   [Twenty Twenty-Four](https://wordpress.org/themes/twentytwentyfour/)
*   [Twenty Twenty-Three](https://wordpress.org/themes/twentytwentythree/)
*   [Twenty Twenty-Two](https://wordpress.org/themes/twentytwentytwo/) 

<!-- 
It’s typically best to use the latest default theme. This is because it will be built with the most up-to-date features in mind. Plus, it should already be activated if you’ve recently installed WordPress:
 -->

通常、最新のデフォルトテーマを使用するのが最も適切です。これは、最新の機能に対応して設計されているためです。さらに、最近 WordPress をインストールした場合は、すでに有効化されているはずです:

<!-- 
[![WordPress Appearance > Theme admin screen, showing the Twenty Twenty-Four theme activated.](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-activated.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-activated.jpg?ssl=1)
 -->

[![WordPress「外観 > テーマ」管理画面、Twenty Twenty-Four テーマが有効化されていることが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-activated.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-activated.jpg?ssl=1)

<!-- 
You can also choose any theme from the official [Theme Directory](https://wordpress.org/themes/) to learn from, but for the purposes of this guide, it should be a [block theme](https://wordpress.org/themes/tags/full-site-editing/). For more information on installing and activating themes, read the [Work with themes](https://wordpress.org/documentation/article/work-with-themes/) documentation.
 -->

また、公式 [テーマ・ディレクトリ](https://wordpress.org/themes/) から任意のテーマを選択して学習できますが、このガイドの目的上は [ブロック・テーマ](https://wordpress.org/themes/tags/full-site-editing/) を選択する必要があります。テーマのインストールと有効化に関する詳細は、[テーマの取り扱い](https://wordpress.org/documentation/article/work-with-themes/) ドキュメントをご確認ください。

<!-- 
If your interests lie in classic WordPress, you should jump forward to the [Classic Themes](https://developer.wordpress.org/themes/classic-themes/) chapter for more details on building classic themes.
 -->

クラシック WordPress に興味がある場合は、[クラシック・テーマ](https://developer.wordpress.org/themes/classic-themes/) 章に進んで、クラシック・テーマの構築に関する詳細をご覧ください。

<!-- 
## Customizing your theme
 -->

## テーマをカスタマイズする

<!-- 
Once you’ve activated a block theme, take some time to simply have fun exploring and tinkering with the available options in the [Site Editor](https://wordpress.org/documentation/article/site-editor/). Essentially, this is an editable, visual representation of your theme in the WordPress admin.
 -->

ブロック・テーマを有効化したら、まずは [サイトエディター](https://wordpress.org/documentation/article/site-editor/) で利用可能なオプションを自由に探検し、試行錯誤しながら楽しんでみてください。要するに、これは WordPress の管理画面内であなたのテーマを視覚的に編集できる機能です。

<!-- 
And, as promised earlier in the Getting Started chapter, you can build your theme entirely from this interface without touching a single line of code.
 -->

そして、「はじめに」章で約束したように、コードを一行も触れることなく、このインターフェースからあなたのテーマを完全に構築できます。

<!-- 
You can locate the Site Editor via **Appearance > Editor** in the WordPress admin menu. Once opened, your screen should look similar to this:
 -->

サイトエディターは、WordPress 管理者メニューの **外観 > エディター** からアクセスできます。エディターを開くと、画面は次のような表示になります:

<!-- 
[![WordPress Site Editor with the Design menu shown in the left panel. In the preview panel is the homepage of the Twenty Twenty-Four theme.](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-editor.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-editor.jpg?ssl=1)
 -->

[![WordPress サイトエディターの左パネルに「デザイン」メニューが表示されている。プレビューパネルには、Twenty Twenty-Four テーマのホームページが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-editor.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-editor.jpg?ssl=1)

<!-- 
There are a lot of pieces to this, and you can find yourself lost for hours just tinkering around in the Site Editor. It can be fun, and you’ll learn more about how this integrates with your theme as you read through this handbook. For now, let’s get to the basics of “creating” a theme.
 -->

この作業には多くの要素が含まれており、サイトエディターで試行錯誤して過ごすだけで、何時間も時間を費やしてしまうことがあります。これは楽しい作業であり、このハンドブックを読み進めることで、あなたのテーマとの統合方法についてより深く理解できます。では、まずはテーマの「制作」の基本から始めましょう。

<!-- 
This part of the journey can be entirely self-directed, so feel free to do this at your own pace and in your own way. But most people will want to begin by adjusting their design. 
 -->

旅のこの部分は、完全に自分のペースで進めることができるので、ご自身のペースとやり方で進めてください。ただし、ほとんどの人はまずデザインを調整することから始めるでしょう。

<!-- 
You can do this by first selecting the **Styles** item in the menu panel:
 -->

これを行うには、まずメニューパネルの **スタイル** を選択します:

<!-- 
[![WordPress Styles screen under the Site Editor in the admin. The left panel shows several style variation options.](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-styles.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-styles.jpg?ssl=1)
 -->

[![管理画面のサイトエディター以下にある、「WordPress スタイル」画面。左側パネルには、スタイルのバリエーションのオプションがいくつか表示される。](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-styles.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-styles.jpg?ssl=1)

<!-- 
The Twenty Twenty-Four theme (and many other block themes) include pre-designed style variations, which you can see in the sidebar in the above screenshot. You will learn more about these variations in the [Global Settings and Styles](https://developer.wordpress.org/themes/global-settings-and-styles/) chapter, but feel free to use one as a starting point for your own customizations.
 -->

Twenty Twenty-Four テーマ (および多くの他のブロック・テーマ) には、事前に設計されたスタイルのバリエーションが含まれており、上記のスクリーンショットのサイドバーで確認できます。これらのバリエーションについては、[グローバル設定とスタイル](https://developer.wordpress.org/themes/global-settings-and-styles/) 章で詳しく説明されますが、独自のカスタマイズを始める際の出発点として、自由に利用してください。

<!-- 
The next step is to select the **Style Book** icon (it looks like an eye). Opening this screen will give you full access to modifying the global styles of the site:
 -->

次のステップは、**スタイルブック** アイコン (目の形をしたアイコン) を選択することです。この画面を開くと、サイトのグローバルスタイルを編集するすべての機能にアクセスできます:

<!-- 
[![Style Book screen under the WordPress Site Editor in the admin. It shows a tabbed overlay with various blocks.](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-style-book.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-style-book.jpg?ssl=1)
 -->

[![管理画面の WordPress サイトエディター以下にあるスタイルブック画面。さまざまなブロックがタブで表示される。](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-style-book.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-style-book.jpg?ssl=1)

<!-- 
At this point, *the world is your oyster*—in other words, feel free to let your creativity run wild. But most importantly, get a feel for what settings and styles are available in the interface. This familiarity will come in hand as you dive into more advanced sections of the handbook.
 -->

この段階では、*世界はあなたの掌に* — つまり、創造性を存分に発揮してください。しかし最も重要なのは、インターフェースで利用可能な設定やスタイルに慣れることです。この経験は、ハンドブックのより高度なセクションに取り組む際に役立ちます。

<!-- 
For a deeper dive into using the Style Book, read this guide from the WordPress Developer Blog: [The Style Book: a one-stop shop for styling block themes](https://developer.wordpress.org/news/2023/06/the-style-book-a-one-stop-shop-for-styling-block-themes/).
 -->

スタイルブックの使用についてさらに詳しく知りたい人は、WordPress 開発者ブログに掲載されているこのガイドをご覧ください: [スタイルブック: ブロック・テーマのスタイリングに関する総合ガイド](https://developer.wordpress.org/news/2023/06/the-style-book-a-one-stop-shop-for-styling-block-themes/).

<!-- 
## Exporting your theme
 -->

## テーマをエクスポートする

<!-- 
Once you’ve customized the theme to your liking, be sure to hit the **Save** button. When you’re ready, you will “create” your first theme.
 -->

テーマを好みの設定にカスタマイズしたら、必ず **保存** ボタンをクリックしてください。準備が整ったら、あなたの最初のテーマを“生成”します。

<!-- 
You have two options for doing this. The first is to use the built-in exporter from the Site Editor in WordPress. The second is to use the [Create Block Theme](https://wordpress.org/plugins/create-block-theme/) plugin, which has more extensive options available. There are instructions for both methods below.
 -->

これを行うには、2つのオプションがあります。1つ目のオプションは、WordPress のサイトエディターに備わっているエクスポーターを使用することです。2つ目のオプションは、より幅広いオプションが利用できる [Create Block Theme](https://wordpress.org/plugins/create-block-theme/) プラグインを使用することです。以下、両方の方法を説明します。

<!-- 
### Exporting from the Styles interface
 -->

### スタイル・インターフェースから、エクスポートする

<!-- 
To export your theme from the Site Editor interface, click the **⋮ (Options)** button in the header area. You will see a dropdown of available options. Click the **Export** option, as shown below:
 -->

サイトエディターのインターフェースからテーマをエクスポートするには、ヘッダーエリアの **⋮ (オプション)** ボタンをクリックします。利用可能なオプションのドロップダウン・メニューが表示されます。以下の図のように **エクスポート** オプションをクリックします:

<!-- 
[![WordPress Site Editor with the Options menu dropdown open. The Export option is highlighted.](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-export.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-export.jpg?ssl=1)
 -->

[![WordPress サイトエディターで、オプションメニューのドロップダウンが開いた状態。エクスポート・オプションがハイライト表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-export.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-export.jpg?ssl=1)

<!-- 
This will give you a ZIP file with your complete theme in it. The filename will match that of the theme you were working from. In the case of the default Twenty Twenty-Four theme, it will be `twentytwentyfour.zip`.
 -->

これにより、あなたのテーマの全ファイルが含まれた、ZIP ファイルが作成されます。ファイル名は、作業元のテーマ名と一致します。デフォルトの Twenty Twenty-Four テーマの場合、ファイル名は `twentytwentyfour.zip` となります。

<!-- 
***Congratulations!*** You have now successfully created your first WordPress theme.
 -->

***おめでとうございます !*** これで、あなたの最初の WordPress テーマの制作が完了しました。

<!-- 
You were assured that you could create a theme without touching code. That was the truth. You have built a theme that can be uploaded to any WordPress website just like any other theme.
 -->

あなたは、「コードを触らずにテーマを制作できる」と約束されました。それは事実でした。あなたは、他のテーマと同じように、あらゆる WordPress Web サイトにアップロードできるテーマを制作したことになります。

<!-- 
But there was a *fib*—a harmless white lie—mixed in with that truth about there being no code involved. 
 -->

しかし、その「コードを触らずに」という事実の中に *虚偽* — 無害な白々しい嘘 — が混じってました。

<!-- 
The theme you downloaded is still named “Twenty Twenty-Four,” and it’s best to rename it so that it’s representative of what you’ve created. To do this, unzip the `twentytwentyfour.zip` folder and rename it to `your-theme-name`. 
 -->

ダウンロードしたテーマは現在「Twenty Twenty-Four」という名前のままですので、ご自身が制作した内容にふさわしい名前に変更することをおすすめします。これを行うには、`twentytwentyfour.zip` フォルダーを解凍し、`your-theme-name` に名前を変更してください。

<!-- 
Then, open the `style.css` file within that folder. You should see something like this at the top of the file:
 -->

その後、そのフォルダー内の `style.css` ファイルを開きます。ファイルの上部には、次のような内容が表示されているはずです:

<!-- 
```css
/*
Theme Name: Twenty Twenty-Four
Theme URI: https://wordpress.org/themes/twentytwentyfour/
Author: the WordPress team
Author URI: https://wordpress.org
...
```
 -->

```css
/*
Theme Name: Twenty Twenty-Four
Theme URI: https://wordpress.org/themes/twentytwentyfour/
Author: the WordPress team
Author URI: https://wordpress.org
...
```

<!-- 
At the very least, you should adjust those first four lines, particularly the `Theme Name` value. And that’s all the code you *really* have to touch.
 -->

少なくとも、最初の4行を調整する必要があり、特に、`Theme Name` の値に注意してください。そして、それがあなたが *本当に* 変更する必要があるコードのすべてです。

<!-- 
As a final step, zip the file again with whatever utility program you have on your computer for creating ZIP files.
 -->

最終ステップとして、コンピューターにインストールされている ZIP ファイルを生成する任意のユーティリティ・プログラムで、ファイルを再び圧縮してください。

<!-- 
### Using the Create Block Theme plugin
 -->

### Create Block Theme プラグインを使用する

<!-- 
The [Create Block Theme](https://wordpress.org/plugins/create-block-theme/) plugin is an official, first-party plugin that WordPress contributors maintain. Often, you will see new ideas for exporting themes tried and tested here before they land in WordPress.
 -->

[Create Block Theme](https://wordpress.org/plugins/create-block-theme/) プラグインは、WordPress の公式プラグインであり、WordPress の貢献者によってメンテナンスされています。WordPress に導入される前に、テーマのエクスポートに関する新しいアイデアがここで試され、テストされることがよくあります。

<!-- 
The plugin is more robust than what you will find in core WordPress, meaning that it has many more options for exporting your theme. This guide will only cover the basics of exporting your theme, but feel free to explore the plugin’s features in more detail.
 -->

このプラグインは WordPress のコア機能よりもはるかに堅牢で、あなたのテーマのエクスポートに関するオプションがさらに豊富に用意されています。このガイドでは、あなたのテーマのエクスポートの基本についてのみ説明しますが、プラグインの機能をさらに詳しく確認したい人は、ぜひご自由にお試しください。

<!-- 
Once you’ve activated Create Block Theme, you should see a new button in the Site Editor that is displayed as a wrench icon. Click this button to open the **Create Block Theme** menu.
 -->

Create Block Theme を有効にすると、サイトエディターにレンチのアイコンで表示される新しいボタンが表示されます。このボタンをクリックすると、**Create Block Theme** メニューが開きます。

<!-- 
You will see several options for saving changes, exporting a ZIP, editing theme info, and creating a new theme:
 -->

変更を保存する、ZIP ファイルをエクスポートする、テーマ情報を編集する、新しいテーマを制作するなどのオプションが表示されます:

<!-- 
[![WordPress Site Editor with a "tool" icon in the top right. A menu is open titled "Create Block Theme" and has several options.](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-create-block-theme-menu.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-create-block-theme-menu.jpg?ssl=1)
 -->

[![WordPress サイトエディターの上部右側に「ツール」アイコンがある。「Create Block Theme」というタイトルのメニューが開いており、複数のオプションが用意されている。](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-create-block-theme-menu.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-create-block-theme-menu.jpg?ssl=1)

<!-- 
You can use the **Export ZIP** option to export the theme as you did earlier.
 -->

**ZIP をエクスポート** オプションを使用すると、先程と同様にテーマをエクスポートできます。

<!-- 
But Create Block Theme offers more customization options that you’ll want to use for truly creating a custom theme. Click on the **Create Theme** option:
 -->

ですが、Create Block Theme には、本当にカスタムテーマを制作するために活用したい、より多くのカスタマイズ・オプションが用意されています。**テーマを制作** オプションをクリックしてください:

<!-- 
[![WordPress Site Editor with the Create Block Theme > Create Theme menu open. Several fields are shown within the menu panel.](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-create-block-theme-customize.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-create-block-theme-customize.jpg?ssl=1)
 -->

[![「Create Block Theme > テーマを制作」メニューを開いた WordPress サイトエディター。メニューパネルには、いくつかのフィールドが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-create-block-theme-customize.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt4-create-block-theme-customize.jpg?ssl=1)

<!-- 
From there, you’ll be able to customize all of the information about your theme to make it unique. Once finished, click the **Export Theme** button for your new theme.
 -->

そこから、あなたのテーマに関するすべての情報をカスタマイズして、独自のテーマを作成できます。完了したら、あなたの新しいテーマの **テーマをエクスポート** ボタンをクリックしてください。

<!-- 
The one thing that Create Block Theme does not yet do is let you upload a custom screenshot. You’ll still need to add a unique `screenshot.[png|jpg]` file in your theme if you intend to distribute to others.
 -->

Create Block Theme がまだ対応していない唯一の機能は、カスタムスクリーンショットのアップロードです。他者に配布する予定の場合、テーマ内に一意の `screenshot.[png|jpg]` ファイルを追加する必要があります。