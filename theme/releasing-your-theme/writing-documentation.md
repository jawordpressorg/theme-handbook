<!-- 
# Writing Documentation
 -->

# ドキュメントの作成

<!-- 
Documentation is important for themes as it provides a way for users to understand what a theme does and does not support. Likewise, documenting the code of your theme will make it easier for other theme developers to customize your theme, likely with a [child theme](https://developer.wordpress.org/themes/advanced-topics/child-themes/).
 -->

ドキュメントはテーマにとって重要です。ユーザーがテーマの機能範囲や非対応事項を理解する手段を提供するからです。同様に、あなたのテーマのコードを文書化することで、他のテーマ開発者が [子テーマ](https://developer.wordpress.org/themes/advanced-topics/child-themes/) を用いてあなたのテーマをカスタマイズし易くできます。

<!-- 
Here’s a list of **requirements** and **recommendations** for your theme’s documentation.
 -->

以下のリストは、あなたのテーマのドキュメントにおける **必須要件** と **推奨事項** です。

<!-- 
*   Themes are **required** to provide end-user documentation of any design limitations or extraordinary installation/setup instructions.
*   Themes are **required** to include a [readme.txt file](https://wordpress.org/plugins/about/readme.txt), using the plugin directory’s readme.txt markdown format. New themes need to follow this rule as of October 25th, 2018. Old themes have a 6 months grace time from this date. Since WordPress 5.8 theme [readme files are not parsed for requirements](https://core.trac.wordpress.org/ticket/48520). This means that headers `Requires PHP` and `Requires at least` are going to be parsed from theme’s `style.css` file.
 -->

*   テーマは、設計上の制限事項や、特別なインストール/セットアップ手順を、エンドユーザー向けに文書化することが **必須** です。
*   テーマは、プラグイン・ディレクトリの readme.txt マークダウン・フォーマットを用いた [readme.txt ファイル](https://wordpress.org/plugins/about/readme.txt) を含めることが **必須** です。2018/10/25以降、新規テーマは、この規則に従う必要があります。既存テーマには、この日付から6ヵ月の猶予期間が設けられています。WordPress 5.8以降、テーマ [readme ファイルは要件解析の対象外](https://core.trac.wordpress.org/ticket/48520) です。これは、ヘッダー `Requires PHP` および `Requires at least` がテーマの `style.css` ファイルから解析されることを意味します。