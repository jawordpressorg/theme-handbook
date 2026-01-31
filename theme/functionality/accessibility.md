<!-- 
# Accessibility
 -->

# アクセシビリティ

<!-- 
A WordPress theme should generate pages everyone can use, including those who cannot see or use a mouse.
 -->

WordPress テーマは、視覚障害のある人やマウス操作ができない人を含む、あらゆるユーザーが利用可能なページを生成すべきです。

<!-- 
To create an accessible theme, you need to have knowledge of web standards for HTML, CSS, and JavaScript.  
You also need to be aware of best practices for web accessibility and have basic knowledge of the [Web Content Accessibility Guidelines](https://www.w3.org/WAI/WCAG21/quickref/), WCAG.
 -->

アクセシブルなテーマを作成するには、HTML、CSS、JavaScript の Web 標準に関する知識が必要です。
また、Web アクセシビリティのベスト・プラクティスを理解し、WCAG ([Web コンテンツ・アクセシビリティ・ガイドライン](https://www.w3.org/WAI/WCAG21/quickref/) ) の基本的な知識も必要です。

<!-- 
To succeed in making your theme accessible, accessibility should be considered from the start of your project as part of your project specification. By making the right decisions from the beginning, you can avoid making last-minute adjustments that can be costly, time-consuming, and of low quality.
 -->

あなたのテーマをアクセシブルにするには、あなたのプロジェクトの仕様の一部として、あなたのプロジェクトの開始時点からアクセシビリティを考慮する必要があります。最初から適切な判断を下すことで、高コストで時間が掛かり品質も低い、最終段階での調整を回避できます。

<!-- 
The [Accessibility Team](https://make.wordpress.org/accessibility/) have documented many of the best practices and resources for development, design, and content in their handbook. In the handbook, you can also learn about testing for accessibility.
 -->

[アクセシビリティ・チーム](https://make.wordpress.org/accessibility/) は、設計、開発、コンテンツに関するベスト・プラクティスやリソースの多くを、そのハンドブックにまとめています。同ハンドブックでは、アクセシビリティのテスト方法についても学ぶことができます。

<!-- 
The [Themes Team](https://make.wordpress.org/themes/) has two sets of accessibility requirements for themes submitted to the WordPress.org theme directory:
 -->

[テーマ・チーム](https://make.wordpress.org/themes/) は、WordPress.org テーマ・ディレクトリに提出されるテーマに対して、2種類のアクセシビリティ要件を設けています:

<!-- 
*   [Requirements for all themes](https://make.wordpress.org/themes/handbook/review/required/#3-accessibility)
*   [Requirements for using the “‘accessibility-ready” tag](https://make.wordpress.org/themes/handbook/review/accessibility/)
 -->

*   [全テーマに対する、要件](https://make.wordpress.org/themes/handbook/review/required/#3-accessibility)
*   [「アクセシビリティ対応済み」タグ使用に対する、要件](https://make.wordpress.org/themes/handbook/review/accessibility/)

<!-- 
The accessibility-ready requirements are based on WCAG but adapted for WordPress themes.
 -->

アクセシビリティ対応要件は WCAG にもとづきますが、WordPress テーマ向けに調整されています。

<!-- 
“Accessibility Ready” does **not** mean that the theme meets the WCAG guidelines [AA-level](https://make.wordpress.org/accessibility/handbook/make/which-questions-should-you-ask/#levels-of-accessibility). It means that the theme reaches the minimum standards that the theme review team has set.
 -->

「アクセシビリティ対応」は、テーマが WCAG ガイドラインの [AA レベル](https://make.wordpress.org/accessibility/handbook/make/which-questions-should-you-ask/#levels-of-accessibility) を満たしていることを意味するものでは、**ありません**。これは、当該テーマが、テーマ審査チームの設定した、最低基準に達していることを意味します。

<!-- 
## The four principles of web accessibility
 -->

## Web アクセシビリティの四大原則

<!-- 
Although web accessibility can be a complex subject, it boils down to only four principles. The content must be:
 -->

Web アクセシビリティは複雑なテーマですが、その本質は4つの原則に集約されます。コンテンツは、次の条件を満たす必要があります:

<!-- 
### Perceivable
 -->

### 知覚可能

<!-- 
Content must be available to all. It should not depend on a specific device or browser or require a specific physical sense, such as sight or sound.
 -->

コンテンツは、すべての人に利用可能でなければ、なりません。特定のデバイスやブラウザーに依存したり、視覚や聴覚といった特定の身体的感覚を必要としたりしては、なりません。

<!-- 
### Operable
 -->

### 操作可能

<!-- 
Users must be able to move around and operate the final site effectively, whether they’re using a keyboard, a mouse, or assistive technology.
 -->

ユーザーは、キーボード、マウス、または支援技術を使用している場合でも、最終サイトを効果的に移動し操作できる必要があります。

<!-- 
### Understandable
 -->

### 理解可能

<!-- 
The content should be presented in a manner that supports understanding, including supporting the construction of a mental model of the site for screen reader users. Similarly, the site’s operation (navigation menus, links, forms, etc.) should be easily understandable. Building a theme that incorporates known user behaviors (such as underlining links within the main content area) helps in this respect.
 -->

コンテンツは、理解を助ける形で提示されるべきであり、スクリーン・リーダー利用者に対して、サイトについてのメンタル・モデル構築の支援を伴わなければ、なりません。同様に、サイトの操作性 (ナビゲーション・メニュー、リンク、フォーム、等) も、容易に理解できるものであるべきです。既知のユーザー挙動 (メイン・コンテンツ領域内のリンクに下線を引く、など) を組み込んだテーマを構築することは、この点において有益です。

<!-- 
### Robust
 -->

### 堅牢

<!-- 
Content must be equally available across a wide range of user agents. Disabled users may employ a range of hardware and software solutions (commonly referred to as “assistive technology”) to allow them to access the Web—including screen reading & voice recognition software, braille readers, and switches (single input devices).
 -->

コンテンツは、幅広いユーザー・エージェントで、均等に利用可能でなければ、なりません。障害を抱えるユーザーは、Web にアクセスするために、さまざまなハードウェアおよびソフトウェア・ソリューション (一般に「支援技術」と呼ばれる) を必要とする場合が、少なくありません — これには、スクリーン・リーダーや音声認識ソフトウェア、点字リーダー、スイッチ (単一入力デバイス) などが含まれます。

<!-- 
A theme designed with these four principles in mind eases the creation of an accessible website.
 -->

これらの4つの原則を念頭に置いて設計されたテーマは、アクセシブルな Web サイトの作成を容易にします。

<!-- 
* * *
 -->

* * *

<!-- 
## Perceivable and understandable
 -->

## 知覚可能かつ理解可能

<!-- 
### Color and color contrast
 -->

### 色と、色コントラスト

<!-- 
Having a high enough color contrast between background and foreground colors makes content easier to read. Theme authors must ensure that all background/foreground color contrasts for plain content text are within the level AA contrast ratio (4.5:1) specified in the Web Content Accessibility Guidelines (WCAG) 2.0 for color luminosity.
 -->

背景色と前景色とのコントラストを十分に高く設定することで、コンテンツの可読性が向上します。テーマ作者は、プレーン・テキスト・コンテンツの背景色と前景色とのコントラストが、Web コンテンツ・アクセシビリティ・ガイドライン (WCAG) 2.0で規定されている、レベル AA のコントラスト比 (`4.5:1`) の範囲内にあることを、保証しなければなりません。

<!-- 
*   Color may not be the only way to identify controls, links in text content, or error messages.
*   If there is no text decoration on linked text, there must be a 3:1 color contrast between the link text color and the surrounding non-link text color, in addition to the other color contrast requirements.
 -->

*   コントロール、テキスト・コンテンツ内のリンク、またはエラー・メッセージを識別する方法は、色だけではない場合があります。
*   リンク・テキストにテキスト装飾がない場合、リンク・テキストの色と、周囲の非リンク・テキストの色との間に、他の色コントラスト要件に加えて、`3:1` の色コントラストが必要です。

<!-- 
There are separate requirements for links in content (links surrounded by other text) and links that are grouped together in navigation menus. Groups of links do not need to be underlined if it is obvious from the context that they are links.
 -->

コンテンツ内のリンク (他のテキストに囲まれたリンク) と、ナビゲーション・メニューにまとめられたリンクとでは、要件が異なります。文脈からリンクであることが明らかな場合、リンク群に下線を引く必要はありません。

<!-- 
[Best practices for the use of color](https://make.wordpress.org/accessibility/handbook/design/use-of-color/)
 -->

[色の使用における、ベスト・プラクティス](https://make.wordpress.org/accessibility/handbook/design/use-of-color/)

<!-- 
[Accessibility-ready requirements for contrast](https://make.wordpress.org/themes/handbook/review/accessibility/required/#contrasts)
 -->

[コントラストにおける、アクセシビリティ対応要件](https://make.wordpress.org/themes/handbook/review/accessibility/required/#contrasts)

<!-- 
### Resizable text
 -->

### サイズ変更可能な、テキスト

<!-- 
Users have many means to resize text, including browser settings. All content and functionality must remain available if the user resizes the text up to 200% of the original size.
 -->

ユーザーは、ブラウザー設定を含め、さまざまな方法を用いてテキストのサイズを変更できます。ユーザーがテキストを元のサイズの最大200%まで拡大した場合でも、すべてのコンテンツと機能が、利用可能な状態を維持しなければなりません。

<!-- 
*   Resizing text must not trigger multi-dimensional scrolling
*   Enlarged texts must not cause overflows or overlaps
 -->

*   テキストのサイズ変更によって、多次元スクロールが発生しては、なりません
*   拡大されたテキストによって、オーバーフローや被りが発生しては、なりません

<!-- 
To avoid these issues, it is recommended to:
 -->

これらの課題を回避するために、以下が推奨されます:

<!-- 
*   Use a relative unit for font sizes and line heights
*   Test your theme in different browsers and screen widths
 -->

*   フォント・サイズと行高には、相対単位を使用しましょう
*   あなたのテーマを、さまざまなブラウザーと画面幅でテストしましょう

<!-- 
[Best practices for font sizes and resized text](https://make.wordpress.org/accessibility/handbook/design/font-sizes-and-resize-text/)
 -->

[フォント・サイズおよびにおけるリサイズされたテキスト、ベスト・プラクティス](https://make.wordpress.org/accessibility/handbook/design/font-sizes-and-resize-text/)

<!-- 
### Images
 -->

### 画像

<!-- 
#### Non-decorative images
 -->

#### 装飾用ではない画像

<!-- 
Example:
 -->

例:

<!-- 
*   A header image that replaces header text
*   Images used in place of text for navigation
 -->

*   ヘッダー・テキストの代わりに表示される、ヘッダー画像
*   ナビゲーション用のテキストの代わりに使用される、画像

<!-- 
Non-decorative images included with `img` elements should have an `alt` attribute.
 -->

`img` 要素に含まれる、装飾用ではない画像には、`alt` 属性を付けるべきです。

<!-- 
#### Decorative images
 -->

#### 装飾用の画像

<!-- 
Example:
 -->

例:

<!-- 
*   A header image used alongside header text
*   Images and icons accompanying navigation text links
 -->

*   ヘッダー・テキストとともに使用される、ヘッダー画像
*   ナビゲーション・テキスト・リンクに付随する、画像とアイコン

<!-- 
When possible, decorative images should be included using CSS.
 -->

可能な場合は、装飾用の画像も CSS を使用して含めるべきです。

<!-- 
*   Decorative images included with `img` elements should have an empty `alt` attribute: `alt=""`.
*   Decorative images that are displayed together with text should be hidden from screen readers using `aria-hidden`.
 -->

*   `img` 要素に含まれる装飾用の画像は、空の `alt` 属性を持つべきです: `alt=""`。
*   テキストとともに表示される装飾用の画像は、`aria-hidden` を使用して、スクリーン・リーダーに対して非表示にするべきです。

<!-- 
#### Featured images
 -->

#### アイキャッチ画像

<!-- 
The alt attribute for featured images is defined in the media library.
 -->

アイキャッチ画像の alt 属性は、メディア・ライブラリで定義されます。

<!-- 
*   If the featured image is unlinked, the alt attribute should describe the image
*   If the featured image is linked to a post, the alt text should use the post title
 -->

*   アイキャッチ画像がリンクされていない場合、alt 属性で、画像の説明を記述しましょう
*   アイキャッチ画像が投稿にリンクされている場合、alt 属性には、投稿タイトルを使用しましょう

<!-- 
[Best practices for alt texts](https://make.wordpress.org/accessibility/handbook/content/alternative-text-for-images/)
 -->

[alt 属性における、ベスト・プラクティス](https://make.wordpress.org/accessibility/handbook/content/alternative-text-for-images/)

<!-- 
[Accessibility-ready requirement for images](https://make.wordpress.org/themes/handbook/review/accessibility/required/#images)
 -->

[画像における、アクセシビリティ対応要件](https://make.wordpress.org/themes/handbook/review/accessibility/required/#images)

<!-- 
## Operable
 -->

## 操作可能

<!-- 
### Controls
 -->

### コントロール

<!-- 
All controls must be usable with the keyboard on all screen sizes, including but not limited to buttons for opening and closing menus, submenus, any type of dialog, modal, and popup.
 -->

すべての画面サイズにおいて、メニュー、サブメニュー、あらゆる種類のダイアログ、モーダル、ポップアップを開閉するボタンを含む (ただし、これらに限定されない) すべての操作要素は、キーボードで操作可能でなければなりません。

<!-- 
[Best practices for dialog modals](https://make.wordpress.org/accessibility/handbook/markup/dialog-modal/)
 -->

[ダイアログモーダルにおける、ベスト・プラクティス](https://make.wordpress.org/accessibility/handbook/markup/dialog-modal/)

<!-- 
[Accessibility-ready requirements for controls](https://make.wordpress.org/themes/handbook/review/accessibility/required/#controls)
 -->

[コントロールにおける、アクセシビリティ対応要件](https://make.wordpress.org/themes/handbook/review/accessibility/required/#controls)

<!-- 
### Headings
 -->

### 見出し

<!-- 
Headings are an essential way of breaking content down into logical sub-sections. Heading levels indicate the importance of the content. Screen reader users can scan the contents of a page by reading the headings, and navigating to a section via its heading. That is why it is important that headings are used logically and not for presentational purposes.
 -->

見出しは、コンテンツを論理的なサブセクションに分割する、重要な手段です。見出しレベルは、コンテンツの重要性を示します。スクリーン・リーダー利用者は、見出しを読み取ることでページのコンテンツをスキャンし、見出しを通じて特定のセクションに移動します。こうした理由から、見出しは表示目的ではなく、論理的に使用することが重要です。

<!-- 
[Best practices for Heading structure in theme development](https://make.wordpress.org/accessibility/handbook/markup/heading-structure-in-theme-development/)
 -->

[テーマ開発での見出し構造における、ベスト・プラクティス](https://make.wordpress.org/accessibility/handbook/markup/heading-structure-in-theme-development/)

<!-- 
[Accessibility-ready requirements for headings](https://make.wordpress.org/themes/handbook/review/accessibility/required/#headings)
 -->

[見出しにおける、アクセシビリティ対応要件](https://make.wordpress.org/themes/handbook/review/accessibility/required/#headings)

<!-- 
### Links
 -->

### リンク

<!-- 
#### Link text
 -->

#### リンク・テキスト

<!-- 
Link text should describe the resource that it links to, even when the text is read out of context. Some assistive software scans a page for links and presents them to the user as a simple list. In these situations, all the links will be read out of context. So it is important the text used in a link is descriptive. Bare URLs should never be used as links.
 -->

リンク・テキストは、文脈から切り離されて読み上げられた場合でも、リンク先のリソースを説明できるものでなければ、なりません。一部の支援ソフトウェアは、ページ内のリンクをスキャンし、単純なリストとしてユーザーに提示します。このような状況では、すべてのリンクが文脈から切り離されて、読み上げられます。したがって、リンクに使用するテキストが、説明的であることが重要です。素の URL は、リンクとして決して使用すべきではありません。

<!-- 
[Good link texts](https://make.wordpress.org/accessibility/handbook/content/good-link-texts/)
 -->

[適切な、リンク・テキスト](https://make.wordpress.org/accessibility/handbook/content/good-link-texts/)

<!-- 
[Accessibility-ready requirements: Avoiding repetitive Read More or Continue reading texts.](https://make.wordpress.org/themes/handbook/review/accessibility/required/#repetitive-link-text)
 -->

[アクセシビリティ対応要件: 「続きを読む」といったテキストの繰り返しを避けること。](https://make.wordpress.org/themes/handbook/review/accessibility/required/#repetitive-link-text)

<!-- 
#### Link underlining and styling link states
 -->

#### リンクのアンダーライン設定と、リンク状態のスタイル設定

<!-- 
Generally speaking, links should be underlined if they are outside navigation menus and lists. Using color alone to distinguish links is insufficient as not everyone can perceive color.
 -->

一般的に、リンクはナビゲーション・メニューやリストの範囲外にある場合、下線を引くべきです。誰もが色を認識できるわけではないので、リンクを識別するために色のみを使用することは不十分です。

<!-- 
Users must be able to tell if a text is linked if they are hovering over a link, if they are focusing on a link, and if they have already visited a link. The default browser style for the focus state should not be removed unless replaced with a more visible focus style.
 -->

ユーザーは、テキストがリンクされているかどうか、リンクの上にカーソルを合わせているかどうか、リンクにフォーカスしているかどうか、そしてリンクをすでに訪問したかどうかを判別できる必要があります。フォーカス状態のデフォルトのブラウザー・スタイルは、より視認性の高いフォーカス・スタイルに置き換えない限り、削除すべきではありません。

<!-- 
[Accessibility-ready requirements for underlining links in the content](https://make.wordpress.org/themes/handbook/review/accessibility/required/#content-links)
 -->

[コンテンツ内リンクのアンダーライン表示における、アクセシビリティ対応要件](https://make.wordpress.org/themes/handbook/review/accessibility/required/#content-links)

<!-- 
#### Skip Links
 -->

#### スキップ・リンク

<!-- 
Skip links provide a mechanism that enables users to navigate directly to content or navigation on entering any given page. For example, a skip to content link might allow a user to skip a header area and go directly to the main content.
 -->

スキップ・リンクは、ユーザーが任意のページにアクセスした際に、コンテンツやナビゲーションに直接移動できるしくみを提供します。たとえば、「コンテンツにスキップ」リンクを使用すると、ユーザーはヘッダー・エリアをスキップしてメイン・コンテンツに直接移動できます。

<!-- 
In designs with multiple menus and content areas, multiple skip links can be used:
 -->

複数のメニューや複数のコンテンツ・エリアを伴うデザインでは、複数のスキップ・リンクを使用できます:

<!-- 
*   Skip to the main navigation
*   Skip to content
*   Skip to footer
 -->

*   メイン・ナビゲーションにスキップ
*   コンテンツにスキップ
*   フッターにスキップ

<!-- 
These links may be positioned off-screen initially using an appropriate CSS technique but should remain available to screen reader users and be visible on focus for sighted keyboard navigators.
 -->

これらのリンクは、適切な CSS 技術を用いて、初期状態では画面外に配置される場合がありますが、スクリーン・リーダー利用者が利用可能な状態を維持し、視覚障害者のキーボード・ナビゲーターがフォーカス時に視認できる状態である必要があります。

<!-- 
[Best practices for Skip Links](https://make.wordpress.org/accessibility/handbook/markup/skip-links/)
 -->

[スキップ・リンクにおける、ベスト・プラクティス](https://make.wordpress.org/accessibility/handbook/markup/skip-links/)

<!-- 
[Accessibility-ready requirements for Skip Links](https://make.wordpress.org/themes/handbook/review/accessibility/required/#skip-links)
 -->

[スキップ・リンクにおける、アクセシビリティ対応要件](https://make.wordpress.org/themes/handbook/review/accessibility/required/#skip-links)

<!-- 
### Forms
 -->

### フォーム

<!-- 
*   Provide enough information for the user to be able to complete the form.
*   All input fields must have a label. A placeholder text is not a replacement for the label. Input fields must also have a visible focus style.
*   Group controls that belong together, for example, a set of related checkboxes, with a `fieldset` and `legend`.
*   Make sure that the tab order in the form matches the visual order of the input fields: Do not move focus unexpectedly or skip past input fields.
 -->

*   ユーザーがフォーム入力を完了できる、十分な情報を提供しましょう。
*   すべての入力フィールドには、ラベルが必要です。プレースホルダー・テキストは、ラベルの代わりにはなりません。入力フィールドには、視覚的なフォーカス・スタイルも必要です。
*   関連するグループ・コントロール、たとえば、関連するチェックボックスのセットを、`fieldset` と `legend` でまとめます。
*   フォーム内のタブ順序が、入力フィールドの視覚的な順序と一致していることを確認してください: フォーカスが予期せず移動したり、入力フィールドをスキップしたりしないようにしましょう。

<!-- 
#### On Form Submission
 -->

#### フォーム送信時

<!-- 
Post-submission responses—including any error messages—should always be perceivable. If possible, error messages should be generated at the top of the post-submission page so the user is immediately aware of any issues. Error messages should also make sense when read out of context.
 -->

投稿後の応答 — エラー・メッセージを含む — は、常に認識可能であるべきです。可能であれば、エラー・メッセージは、投稿後のページの上部に表示され、ユーザーがただちに問題を認識できるようにすべきです。エラー・メッセージは、文脈から切り離して読んでも、意味が通じるものでなければなりません。

<!-- 
[Best practices for forms](https://make.wordpress.org/accessibility/handbook/markup/web-forms/)
 -->

[フォームにおける、ベスト・プラクティス](https://make.wordpress.org/accessibility/handbook/markup/web-forms/)

<!-- 
[Accessibility-ready requirements for forms](https://make.wordpress.org/themes/handbook/review/accessibility/required/#forms)
 -->

[フォームにおける、アクセシビリティ対応要件](https://make.wordpress.org/themes/handbook/review/accessibility/required/#forms)

<!-- 
## Robust
 -->

## 堅牢

<!-- 
Use the HTML element that is the best match for the content. Use buttons when performing an action, and links when navigating to a part of a page or a new page.
 -->

コンテンツにふさわしい、HTML 要素を使用しましょう。アクションを実行するときはボタンを、ページ内の一部や新しいページへ移動するときはリンクを、使用しましょう。

<!-- 
*   The content of the website should be available even if the user disables both JavaScript and CSS
*   Establish which [browsers](https://make.wordpress.org/core/handbook/best-practices/browser-support/) your theme supports and test your theme with these browsers on different screen sizes
 -->

*   ユーザーが JavaScript と CSS の両方を無効にした場合でも、Web サイトのコンテンツは利用可能であるべきです
*   あなたのテーマがサポートする [ブラウザー](https://make.wordpress.org/core/handbook/best-practices/browser-support/) を特定し、それらのブラウザーを用いて異なる画面サイズであなたのテーマをテストしましょう

<!-- 
## Resources
 -->

## リソース

<!-- 
[Make WordPress Accessible](https://make.wordpress.org/accessibility/) is the official blog for the WordPress Accessibility Team, dedicated to making WordPress accessible to as many people as possible. Anyone can join in the discussions, bug scrubs, and meetings. You can also follow discussions via email or subscribe to feeds for posts and comments.
 -->

[Make WordPress Accessible](https://make.wordpress.org/accessibility/) は、可能な限り多くの人々が WordPress を利用できるようにすることを目的とした、WordPress アクセシビリティ・チームの公式ブログです。議論、バグの修正作業、ミーティングには誰でも参加できます。また、メールで議論をフォローしたり、投稿やコメントに関するフィードも購読したりできます。

<!-- 
*   [Test for web accessibility](https://make.wordpress.org/accessibility/handbook/test-for-web-accessibility/)
*   [Development tools](https://make.wordpress.org/accessibility/handbook/which-tools-can-i-use/useful-tools/)
*   [WCAG 2 (external link)](https://www.w3.org/WAI/standards-guidelines/wcag/)
 -->

*   [Web アクセシビリティに関するテスト](https://make.wordpress.org/accessibility/handbook/test-for-web-accessibility/)
*   [開発ツール](https://make.wordpress.org/accessibility/handbook/which-tools-can-i-use/useful-tools/)
*   [WCAG 2 (外部リンク)](https://www.w3.org/WAI/standards-guidelines/wcag/)

<!-- 
Changelog:
 -->

変更履歴:

<!-- 
*   **Rewritten and published** 2023-02-16
 -->

*   **改訂・公開** 2023-02-16