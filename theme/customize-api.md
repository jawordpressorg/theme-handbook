<!-- 
# Theme Options &#8211; The Customize API
 -->

# テーマオプション &#8211; カスタマイズ API

<!-- 
The Customize API (Customizer) is a framework for live-previewing any change to WordPress. It provides a unified interface for users to customize various aspects of their theme and their site, from colors and layouts to widgets, menus, and more. Themes and plugins alike can add options to the Customizer. The Customizer is the canonical way to add options to your theme.
 -->

カスタマイズ (「カスタマイザー」) は、WordPress への任意の変更をライブプレビューするためのフレームワークです。ユーザーが、自身のテーマや自身のサイトの、色やレイアウトからウィジェット、メニュー、その他、といった、さまざまな側面をカスタマイズするための、統一されたインターフェースを提供します。テーマとプラグインの区別なく、「カスタマイザー」にオプションを追加できます。「カスタマイザー」は、あなたのテーマにオプションを追加するための標準的な方法です。

<!-- 
[![The customizer as it appears in WordPress 4.6 with the Twenty Fifteen theme.](https://i0.wp.com/developer.wordpress.org/files/2014/10/customize-4.6.png?resize=640%2C360&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2014/10/customize-4.6.png?ssl=1)
 -->

[![WordPress v4.6の Twenty Fifteen テーマにおける、「カスタマイザー」の画面表示。](https://i0.wp.com/developer.wordpress.org/files/2014/10/customize-4.6.png?resize=640%2C360&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2014/10/customize-4.6.png?ssl=1)

<!-- 
The customizer as it appears in WordPress 4.6 with the Twenty Fifteen theme.
 -->

WordPress v4.6の Twenty Fifteen テーマにおける、「カスタマイザー」の画面表示です。

<!-- 
Customizer options can be granted to users with different capabilities on a granular basis, so while most options are visible only to administrators by default, other users may access certain options if you want them to be able to. Different parts of the Customizer can also be contextual to whether they’re relevant to the front-end context that the user is previewing. For example, the core widgets functionality only shows widget areas that are displayed on the current page; other widget areas are shown when the user navigates to a page that includes them within the Customizer preview window.
 -->

「カスタマイザー」のオプションは、さまざまな権限を持つユーザーに対して細かく設定でき、デフォルトではほとんどのオプションは管理者だけに表示されますが、必要に応じて他のユーザーにも特定のオプションへのアクセスを許可できます。「カスタマイザー」のさまざまなパートは、ユーザーがプレビューしているフロントエンドのコンテンツに関連しているか否かというコンテキストに依存しています。たとえば、ウィジェット機能のコア部分が表示するのは、現在のページに表示されているウィジェットエリアのみです; その他のウィジェットエリアは、ユーザーがそれらを含むページに移動した際に、「カスタマイザー」のプレビューウィンドウ内に表示されます。

<!-- 
This section contains an overview of the Customize API, including code examples and discussion of best practices. For more details, it is strongly recommended that developers study the core customizer code (all core files containing “customize”). This is considered the canonical, official documentation for the Customize API outside of the inline documentation within the core code.
 -->

本セクションでは、カスタマイズ API の概要を説明し、コード例やベストプラクティスに関する議論を含みます。詳細については、開発者はコアカスタマイザーコード (「customize」を含む、すべてのコアファイル) を学ぶことを強く推奨します。これは、コアコード内のインラインドキュメントを除けば、カスタマイズ API に関する正式な公式ドキュメントと見なされます。