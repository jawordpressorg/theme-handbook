<!-- 
# Patterns and Block Locking
 -->

# パターンとブロックのロック機能

<!-- 
The [Block Locking API](https://developer.wordpress.org/block-editor/how-to-guides/curating-the-editor-experience/block-locking/) is a powerful set of features that lets you lock the behavior of blocks and how users interact with them. You can control whether users can remove, move, or customize blocks, which lets you further curate the editing experience of your themes.
 -->

[Block Locking API](https://developer.wordpress.org/block-editor/how-to-guides/curating-the-editor-experience/block-locking/) は、ブロックの挙動やブロックとのユーザー・インタラクションをロックできる、強力な機能セットです。ユーザーがブロックを削除、移動、カスタマイズできるかどうかをコントロールできるので、あなたのテーマの編集体験を、さらに魅力的なものにできます。

<!-- 
This article will explore some of the ways that you can utilize the API within your theme’s patterns. But for a deeper dive into the API, please refer to the [Block Locking documentation](https://developer.wordpress.org/block-editor/how-to-guides/curating-the-editor-experience/block-locking/) in the Block Editor Handbook.
 -->

本稿では、あなたのテーマのパターン内で、API を活用する方法のいくつかを探ります。その API をより深く掘り下げたい人は、ブロック・エディター・ハンドブックの、[「ブロック・ロック機能」ドキュメント](https://developer.wordpress.org/block-editor/how-to-guides/curating-the-editor-experience/block-locking/) をご覧ください。

<!-- 
You are not only limited to using Block Locking in patterns. You can also apply the methods in this article to [templates](https://developer.wordpress.org/themes/templates/).
 -->

「ブロック・ロック機能」の使い方は、パターンだけに限りません。本稿の方法を [テンプレート](https://developer.wordpress.org/themes/templates/) にも適用できます。

<!-- 
## What is Block Locking?
 -->

## 「ブロック・ロック機能」って ?

<!-- 
The Block Locking API lets you control how a user interacts with blocks on their site. The types of locking you can do are:
 -->

Block Locking API を使用すると、サイト上のブロックとのユーザー・インタラクションを制御できます。できるロックの種類は以下のとおりです:

<!-- 
*   Disabling block movement in the editor.
*   Preventing a block from being removed.
*   Preventing new blocks from being inserted.
*   Disabling editing block settings other than content and media.
 -->

*   エディターでの、ブロック移動の無効化。
*   ブロック削除の防止。
*   新規ブロック挿入の防止。
*   コンテンツとメディア以外の、ブロック設定編集の無効化。

<!-- 
This can be really useful depending on the scenario. For example, it often makes sense to lock a site header pattern, which can be complex, by disabling the deletion of its inner blocks by accident.
 -->

これはシナリオによっては、本当に便利なものです。たとえば、複雑になりがちなサイト・ヘッダー・パターンを、誤って内部ブロックを削除できないように、ロックすることは、しばしば意味があります。

<!-- 
There are also two types of locking the API offers: block and template. Locking at the block level means preventing the user from taking some actions for the individual block. Locking at the template level means preventing the user from some actions at a “group” level.
 -->

また、API が提供するロックには、2つのタイプ、ブロックとテンプレート、があります。ブロック・レベルでのロックとは、ユーザーが個々のブロックに対して、アクションを起こせないようにすることを意味します。テンプレート・レベルでのロックとは、ユーザーが「グループ」レベルでアクションを起こせないようにすることを意味します。

<!-- 
It’s important to note that “template” here refers to a section of blocks nested within a container block, such as Group, Cover, etc. It’s not referring specifically to template files.
 -->

ここで重要なのは、「テンプレート」とは、「グループ」「カバー」などのコンテナ・ブロック内で入れ子になったブロックのセクションを指すということです。テンプレート・ファイルを特に指しているわけではありません。

<!-- 
## Block locking
 -->

## ブロック・ロック機能

<!-- 
In this section, you will learn how to lock individual blocks. Namely, preventing a user from moving a block or removing it altogether.
 -->

本セクションでは、個々のブロックのロック法を学びます。つまり、ユーザーがブロックを移動したり、完全に削除したりできないようにします。

<!-- 
First, you should familiarize yourself with how to lock blocks from the UI. Let’s start by creating a custom “event” pattern to work for throughout the remainder of this article.
 -->

まず、UI からのブロックのロック法に慣れる必要があります。まずは、本稿の残りの部分で使用するカスタム「イベント」パターンの制作から始めましょう。

<!-- 
Create a new file in your theme named `/patterns/event.php` and place the following code into it:
 -->

あなたのテーマに `/patterns/event.php` という名前の新規ファイルを作成し、その中に以下のコードを配置しましょう:

```php
<?php
/**
 * Title: Event
 * Slug: themeslug/event
 * Categories: banner
 * Viewport Width: 1376
 */
?>
<!-- wp:group {"align":"wide","style":{"elements":{"link":{"color":{"text":"var:preset|color|base-2"}}},"spacing":{"padding":{"top":"var:preset|spacing|30","bottom":"var:preset|spacing|30","left":"var:preset|spacing|30","right":"var:preset|spacing|30"}}},"backgroundColor":"contrast","textColor":"base-2","layout":{"type":"default"}} -->
<div class="wp-block-group alignwide has-base-2-color has-contrast-background-color has-text-color has-background has-link-color" style="padding-top:var(--wp--preset--spacing--30);padding-right:var(--wp--preset--spacing--30);padding-bottom:var(--wp--preset--spacing--30);padding-left:var(--wp--preset--spacing--30)">

	<!-- wp:image {"sizeSlug":"full","linkDestination":"none"} -->
	<figure class="wp-block-image size-full"><img src="https://s.w.org/patterns/files/2021/06/Group-17-scaled.jpg" alt="Image of a woman being carried through the air by swans."/></figure>
	<!-- /wp:image -->

	<!-- wp:columns {"verticalAlignment":"center"} -->
	<div class="wp-block-columns are-vertically-aligned-center">
		
		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Location:', 'themeslug' ); ?></strong><br><?php esc_html_e( '82 Main St. Brooklyn, NY', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Date:', 'themeslug' ); ?></strong><br><?php esc_html_e( 'October 24, 2021', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:buttons -->
			<div class="wp-block-buttons">
				<!-- wp:button {"width":100,"className":"is-style-outline"} -->
				<div class="wp-block-button has-custom-width wp-block-button__width-100 is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Purchase Tickets' ); ?></a></div>
				<!-- /wp:button -->
			</div>
			<!-- /wp:buttons -->
		</div>
		<!-- /wp:column -->

	</div>
	<!-- /wp:columns -->

</div>
<!-- /wp:group -->
```

<!-- 
Then go to the post editor and insert your new pattern. Once you’ve done that, you should see the pattern in the content area.
 -->

続いて、投稿エディターに移動し、新規パターンを挿入します。そうすると、コンテンツ・エリアにパターンが表示されるはずです。

<!-- 
Now select the Image block (or any block) in the pattern. Then click the **Options** button in the block toolbar. You should see a **Lock** option:
 -->

続いて、パターン内の「画像」ブロック (または任意のブロック) を選択します。その後、ブロック・ツールバーの **オプション** ボタンをクリックします。**ロック** オプションが表示されるはずです:

<!-- 
[![WordPress post editor with an event pattern inserted into the content area. The outer Group block is selected and its Options dropdown menu is shown in the toolbar with the "Lock" option highlighted.](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-menu.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-menu.webp?ssl=1)
 -->

[![コンテンツ・エリアに挿入されたイベントパターンがある、WordPress 投稿エディター。外側の「グループ」ブロックが選択され、その「オプション」ドロップダウン・メニューが、「ロック」オプションが強調表示された状態で、ツールバーに表示される。](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-menu.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-menu.webp?ssl=1)

<!-- 
This will bring up a modal for various locking options, which you’ll learn about in the following sections.
 -->

これにより、次セクションで説明する、さまざまなロック・オプションのモーダルが表示されます。

<!-- 
This type of locking is shown in the UI, and a theme user will be able to override it from the UI. For publicly-distributed themes, this is a good thing. But for client work, this type of access may be undesirable. If you need to control permissions to the locking UI, see the instructions in the Locking API docs: [Change permissions to control locking ability](https://developer.wordpress.org/block-editor/how-to-guides/curating-the-editor-experience/block-locking/#change-permissions-to-control-locking-ability).
 -->

このロックのタイプは UI に表示され、テーマユーザーは UI から上書きできます。一般に配布されるテーマでは、これは良いことです。しかし顧客仕事では、このようなアクセスは望ましくないかもしれません。ロック UI に対するパーミッションを制御する必要がある場合は、ロック API ドキュメントの説明をご覧ください: [パーミッションを変更して、ロック機能のコントロール](https://developer.wordpress.org/block-editor/how-to-guides/curating-the-editor-experience/block-locking/#change-permissions-to-control-locking-ability)。

<!-- 
### Disable block movement
 -->

### ブロック移動の無効化

<!-- 
One of the primary use cases of the Block Locking API is to prevent users from accidentally moving blocks around within a pattern, altering the layout. In the **Lock** modal, you will see an option to **Disable movement**. Try selecting this option for the Image block from the event pattern:
 -->

Block Locking API の主なユースケースのひとつは、ユーザーが誤ってパターン内のブロックを動かして、レイアウトが変更されるのを防ぐことです。**ロック** モーダルで、**移動の無効化** というオプションが表示されます。イベントパターンから「画像」ブロックに対して、このオプションを選択してみましょう:

<!-- 
[![WordPress post editor with an event pattern inserted into the content area. A "Lock Image" modal overlays the screen with the "Disable movement" option selected.](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal-disable-movement.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal-disable-movement.webp?ssl=1)
 -->

[![イベントパターンをコンテンツ・エリアに挿入した、WordPress 投稿エディター。「移動の無効化」オプションを選択された画面が、オーバーレイ表示される「画像をロック」モーダル。](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal-disable-movement.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal-disable-movement.webp?ssl=1)

<!-- 
Under the hood, when you select this option, WordPress will add a new `lock` attribute to the block markup that looks like this:
 -->

裏側では、このオプションを選択すると、WordPress は、ブロック・マークアップに次のような新規 `lock` 属性を追加します:

```markup
<!-- wp:image {"lock":{"move":true,"remove":false}} -->
```

<!-- 
Because you’ve selected the **Disable movement** option, the `move` key will have a value of `true` (i.e., movement has been locked).
 -->

**移動の無効化** オプションを選択したため、`move` キーは `true` の値になります (つまり、移動がロックされました)。

<!-- 
Now try creating a new version of your pattern with the Image block’s movement disabled. Add a new `/patterns/event-disable-movement.php` file to your theme and paste this code in:
 -->

では、「画像」ブロックの移動を無効化して、あなたのパターンの新規バージョンを制作してみましょう。あなたのテーマに新規 `/patterns/event-disable-movement.php` ファイルを追加し、以下のコードをペーストしましょう:

```php
<?php
/**
 * Title: Event (Disable Movement)
 * Slug: themeslug/event-disable-movement
 * Categories: banner
 * Viewport Width: 1376
 */
?>
<!-- wp:group {"align":"wide","style":{"elements":{"link":{"color":{"text":"var:preset|color|base-2"}}},"spacing":{"padding":{"top":"var:preset|spacing|30","bottom":"var:preset|spacing|30","left":"var:preset|spacing|30","right":"var:preset|spacing|30"}}},"backgroundColor":"contrast","textColor":"base-2","layout":{"type":"default"}} -->
<div class="wp-block-group alignwide has-base-2-color has-contrast-background-color has-text-color has-background has-link-color" style="padding-top:var(--wp--preset--spacing--30);padding-right:var(--wp--preset--spacing--30);padding-bottom:var(--wp--preset--spacing--30);padding-left:var(--wp--preset--spacing--30)">

	<!-- wp:image {"sizeSlug":"full","linkDestination":"none","lock":{"move":true,"remove":false}} -->
	<figure class="wp-block-image size-full"><img src="https://s.w.org/patterns/files/2021/06/Group-17-scaled.jpg" alt="Image of a woman being carried through the air by swans."/></figure>
	<!-- /wp:image -->

	<!-- wp:columns {"verticalAlignment":"center"} -->
	<div class="wp-block-columns are-vertically-aligned-center">
		
		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Location:', 'themeslug' ); ?></strong><br><?php esc_html_e( '82 Main St. Brooklyn, NY', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Date:', 'themeslug' ); ?></strong><br><?php esc_html_e( 'October 24, 2021', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:buttons -->
			<div class="wp-block-buttons">
				<!-- wp:button {"width":100,"className":"is-style-outline"} -->
				<div class="wp-block-button has-custom-width wp-block-button__width-100 is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Purchase Tickets' ); ?></a></div>
				<!-- /wp:button -->
			</div>
			<!-- /wp:buttons -->
		</div>
		<!-- /wp:column -->

	</div>
	<!-- /wp:columns -->

</div>
<!-- /wp:group -->
```

<!-- 
Now, anytime a user adds this pattern to their content, they won’t be able to move the Image block within the pattern.
 -->

これで、ユーザーがコンテンツにこのパターンを追加すると、そのパターン内で画像ブロックの移動ができなくなります。

<!-- 
Just because the Image block’s movement has been disabled, it doesn’t affect other blocks within the pattern. For example, it’s still possible to move the Columns block. You would need to disable both blocks from being moved to stop the user from moving either.
 -->

「画像」ブロックの移動が無効化されたからといって、パターン内の他のブロックには影響しません。たとえば、「カラム」ブロックを移動することは、まだ可能です。ユーザーがどちらのブロックも移動できないようにするには、両方のブロックを無効化する必要があります。

<!-- 
### Prevent block removal
 -->

### ブロック削除の防止

<!-- 
For some patterns, you will want to keep a block from being deleted altogether. For example, in the event pattern, the Image block may be integral to the pattern’s design.
 -->

パターンによっては、ブロックが完全に削除されないようにしたいでしょう。たとえば、イベントパターンでは、「画像」ブロックはパターンの設計に不可欠かもしれません。

<!-- 
Starting from the original event pattern, repeat the process of opening the **Lock** modal. This time, select the **Prevent removal** option:
 -->

オリジナルのイベント・パターンから始めて、**ロック** モーダルを開くプロセスを繰り返します。今回は、**削除の防止** オプションを選択しましょう:

<!-- 
[![WordPress post editor with an event pattern inserted into the content area. A "Lock Image" modal overlays the screen with the "Prevent removal" option selected.](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal-prevent-removal.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal-prevent-removal.webp?ssl=1)
 -->

[![コンテンツ・エリアにイベント・パターンが挿入された、WordPress 投稿エディター。「削除の防止」オプションが選択された画面がオーバーレイされる、「画像をロック」モーダル。](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal-prevent-removal.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal-prevent-removal.webp?ssl=1)

<!-- 
Again, WordPress will automatically insert the `lock` attribute in the block markup, which will look like this:
 -->

再び、WordPress は自動的にブロック・マークアップに `lock` 属性を挿入し、次のようになります:

```markup
<!-- wp:image {"lock":{"move":false,"remove":true}} -->
```

<!-- 
This time, the `remove` option is set to `true` (i.e., removal has been locked).
 -->

今回は、`remove` オプションが `true` に設定されています (つまり、削除がロックされました)。

<!-- 
Now create an alternate version of your pattern with the Image block’s removal disabled. Add a new `/patterns/event-prevent-removal.php` file to your theme and paste this code in:
 -->

続いて、「画像」ブロックの削除を無効化して、あなたのパターンの代替バージョンを制作しましょう。あなたのテーマに新規 `/patterns/event-prevent-removal.php` ファイルを追加し、以下のコードをペーストしましょう:

```php
<?php
/**
 * Title: Event (Prevent Removal)
 * Slug: themeslug/event-prevent-removal
 * Categories: banner
 * Viewport Width: 1376
 */
?>
<!-- wp:group {"align":"wide","style":{"elements":{"link":{"color":{"text":"var:preset|color|base-2"}}},"spacing":{"padding":{"top":"var:preset|spacing|30","bottom":"var:preset|spacing|30","left":"var:preset|spacing|30","right":"var:preset|spacing|30"}}},"backgroundColor":"contrast","textColor":"base-2","layout":{"type":"default"}} -->
<div class="wp-block-group alignwide has-base-2-color has-contrast-background-color has-text-color has-background has-link-color" style="padding-top:var(--wp--preset--spacing--30);padding-right:var(--wp--preset--spacing--30);padding-bottom:var(--wp--preset--spacing--30);padding-left:var(--wp--preset--spacing--30)">

	<!-- wp:image {"sizeSlug":"full","linkDestination":"none","lock":{"move":false,"remove":true}} -->
	<figure class="wp-block-image size-full"><img src="https://s.w.org/patterns/files/2021/06/Group-17-scaled.jpg" alt="Image of a woman being carried through the air by swans."/></figure>
	<!-- /wp:image -->

	<!-- wp:columns {"verticalAlignment":"center"} -->
	<div class="wp-block-columns are-vertically-aligned-center">
		
		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Location:', 'themeslug' ); ?></strong><br><?php esc_html_e( '82 Main St. Brooklyn, NY', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Date:', 'themeslug' ); ?></strong><br><?php esc_html_e( 'October 24, 2021', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:buttons -->
			<div class="wp-block-buttons">
				<!-- wp:button {"width":100,"className":"is-style-outline"} -->
				<div class="wp-block-button has-custom-width wp-block-button__width-100 is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Purchase Tickets' ); ?></a></div>
				<!-- /wp:button -->
			</div>
			<!-- /wp:buttons -->
		</div>
		<!-- /wp:column -->

	</div>
	<!-- /wp:columns -->

</div>
<!-- /wp:group -->
```

<!-- 
Now, whenever a user inserts this pattern, they will not be able to remove the Image block. They’ll still be able to edit the image itself and any settings, though.
 -->

これで、ユーザーがこのパターンを挿入する際はいつでも、画像ブロックの削除ができません。ただし、画像自体の編集や設定はまだ可能です。

<!-- 
You can combine both of these techniques, locking movement and removal, depending on your use case. For some patterns, this is often needed to keep the design of the pattern intact.
 -->

あなたのユースケースに応じて、この2つのテクニック、移動のロックと削除のロック、も併用できます。パターンによっては、これは、パターンの設計を損なわないために必要なことが多いです。

<!-- 
## Template locking
 -->

## テンプレート・ロック機能

<!-- 
Template locking refers to locking all of the nested blocks within a container-type block. There are three types of locking that you can accomplish with template locking:
 -->

テンプレート・ロック機能とは、コンテナ型ブロック内の、入れ子ブロックすべてのロックを意味します。テンプレート・ロック機能で実現できるロックには、3種類あります:

<!-- 
*   **`all`:** Combined with the block locking methods covered earlier, lock all blocks within the container.
*   **`insert`:** Prevent users from inserting new blocks within the container.
*   **`contentOnly`:** Lock down all block settings within the container, only allowing the user to edit content (e.g., text and media).
 -->

*   **`all`:** 先に説明したブロック・ロック手法と組み合わせて、コンテナ内の全ブロックをロックします。
*   **`insert`:** ユーザーの、コンテナ内への新規ブロックの挿入を防止します。
*   **`contentOnly`:** コンテナ内のすべてのブロック設定をロックし、ユーザーにコンテンツ (テキストやメディア、など) の編集のみを許可します。

<!-- 
Template locking is only possible for a subset of container-type blocks in Core:
 -->

テンプレート・ロック機能は、「コア」のコンテナ型ブロックのサブセットでのみ、可能です:

*   Group
*   Cover
*   Columns
*   Column
*   Navigation

<!-- 
### Locking all nested blocks
 -->

### すべての入れ子ブロックのロック

<!-- 
With the built-in UI controls, you can lock all nested blocks within a pattern if it’s wrapped in one of the supported container-type blocks. 
 -->

組込み UI コントロールでは、対応するコンテナ型ブロックのひとつでラップされていれば、パターン内のすべての入れ子ブロックをロックできます。

<!-- 
This type of locking builds off the block locking covered earlier in this article. You can choose to disable movement, prevent removal, or both for all nested blocks.
 -->

このロックのタイプは、本稿で以前に取り上げたブロック・ロック機能の上に構築されます。すべての入れ子ブロックに対して、移動の無効化、削除の防止、またはその両方を選択できます。

<!-- 
When clicking on the wrapping Group block inside your event pattern and opening the **Lock** modal, select both the **Disable movement** and **Prevent removal** options. You should also see another option labeled **Apply to all blocks**, which will let you apply these rules to every block inside the Group:
 -->

イベント パターン内のラッピング「グループ」ブロックをクリックして **ロック** モーダルを開き、**移動の無効化** と **削除の防止** オプションの両方を選択します。また、「グループ」内のすべてのブロックにこれらのルールを適用させる、**すべてのブロックに適用** と書かれた別のオプションも表示されるはずです:

<!-- 
[![WordPress post editor with an event pattern inserted into the content area. A "Lock Group" modal overlays the screen with all locking options selected and applied to nested blocks.](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal.webp?ssl=1)
 -->

[![コンテンツ・エリアにイベントパターンを挿入した、WordPress 投稿エディター。すべてのロック・オプションが選択され、入れ子ブロックに適用された画面がオーバーレイされる、「グループのロック」モーダル。](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal.webp?ssl=1)

<!-- 
If you look at the underlying block markup, you will see a new `templateLock` attribute, which will be set to `all`. You will also see the `lock` attribute with both `move` and `remove` set to `true`:
 -->

内部のブロック・マークアップを見ると、新規の `templateLock` 属性があり、`all` に設定されています。また、`lock` 属性もあり、`move` と `remove` の両方が `true` に設定されています:

```markup
<!-- wp:group {"templateLock":"all","lock":{"move":true,"remove":true}} -->
```

<!-- 
Like with individual block locking, you can mix and match what you want to lock at the template level.
 -->

個々のブロック・ロック機能と同様に、テンプレート・レベルで、ロックしたいものをミックス & マッチできます。

<!-- 
Now create a new file named `/patterns/event-lock-all.php` in your theme and paste the following code into it:
 -->

では、あなたのテーマに `/patterns/event-lock-all.php` という新規ファイルを作成し、以下のコードをペーストしましょう:

```php
<?php
/**
 * Title: Event (Lock All)
 * Slug: themeslug/event-lock-all
 * Categories: banner
 * Viewport Width: 1376
 */
?>
<!-- wp:group {"templateLock":"all","lock":{"move":true,"remove":true},"align":"wide","style":{"elements":{"link":{"color":{"text":"var:preset|color|base-2"}}},"spacing":{"padding":{"top":"var:preset|spacing|30","bottom":"var:preset|spacing|30","left":"var:preset|spacing|30","right":"var:preset|spacing|30"}}},"backgroundColor":"contrast","textColor":"base-2","layout":{"type":"default"}} -->
<div class="wp-block-group alignwide has-base-2-color has-contrast-background-color has-text-color has-background has-link-color" style="padding-top:var(--wp--preset--spacing--30);padding-right:var(--wp--preset--spacing--30);padding-bottom:var(--wp--preset--spacing--30);padding-left:var(--wp--preset--spacing--30)">

	<!-- wp:image {"sizeSlug":"full","linkDestination":"none"} -->
	<figure class="wp-block-image size-full"><img src="https://s.w.org/patterns/files/2021/06/Group-17-scaled.jpg" alt="Image of a woman being carried through the air by swans."/></figure>
	<!-- /wp:image -->

	<!-- wp:columns {"verticalAlignment":"center"} -->
	<div class="wp-block-columns are-vertically-aligned-center">
		
		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Location:', 'themeslug' ); ?></strong><br><?php esc_html_e( '82 Main St. Brooklyn, NY', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Date:', 'themeslug' ); ?></strong><br><?php esc_html_e( 'October 24, 2021', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:buttons -->
			<div class="wp-block-buttons">
				<!-- wp:button {"width":100,"className":"is-style-outline"} -->
				<div class="wp-block-button has-custom-width wp-block-button__width-100 is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Purchase Tickets' ); ?></a></div>
				<!-- /wp:button -->
			</div>
			<!-- /wp:buttons -->
		</div>
		<!-- /wp:column -->

	</div>
	<!-- /wp:columns -->

</div>
<!-- /wp:group -->
```

<!-- 
Whenever a user inserts this new pattern into their content, they will not be able to move or remove any of the blocks within the pattern. But they can still edit each block’s content and settings.
 -->

ユーザーがコンテンツに、この新規パターンを挿入するたびに、パターン内のブロックを移動したり削除したりできません。しかし、各ブロックのコンテンツや 設定を編集することは、まだ可能です。

<!-- 
### Preventing new blocks from being inserted
 -->

### 新規ブロック挿入の防止

<!-- 
You can also lock your container-type blocks in patterns from having new blocks inserted into them. This is useful when you need to keep tight control over what is allowed within the design.
 -->

また、パターン内のコンテナ型ブロックに、新規ブロックが挿入されないように、ロックできます。これは、設計内で何が許可されているかを、厳密に管理する必要がある場合に便利です。

<!-- 
Unlock previous methods of locking blocks, this method has no UI controls associated with it. This means that you must edit the block markup directly by adding the `templateLock` value.
 -->

ブロックをロックする前述の方法とは異なり、この方法には UI コントロールが関連付けられていません。これは、`templateLock` 値を追加することで、ブロック・マークアップを直接編集しなければならないことを意味します。

<!-- 
Take a look at what this looks like when applied to a wrapping Group block:
 -->

これをラッピング「グループ」ブロックに適用するとどうなるか、見てみましょう:

```markup
<!-- wp:group {"templateLock":"insert"} -->
```

<!-- 
As you can see, the `templateLock` attribute is set to `insert` (i.e, the Group has locked inserting new blocks).
 -->

ご覧のように、`templateLock` 属性は `insert` に設定されています (つまり、グループは新規ブロックの挿入をロックしています)。

<!-- 
Now create a new file in your theme named `/patterns/event-prevent-insert.php` and paste the following code into it:
 -->

では、あなたのテーマに `/patterns/event-prevent-insert.php` という名前の新規ファイルを作成し、以下のコードをペーストしましょう:

```php
<?php
/**
 * Title: Event (Prevent Insert)
 * Slug: themeslug/event-prevent-insert
 * Categories: banner
 * Viewport Width: 1376
 */
?>
<!-- wp:group {"templateLock":"insert","align":"wide","style":{"elements":{"link":{"color":{"text":"var:preset|color|base-2"}}},"spacing":{"padding":{"top":"var:preset|spacing|30","bottom":"var:preset|spacing|30","left":"var:preset|spacing|30","right":"var:preset|spacing|30"}}},"backgroundColor":"contrast","textColor":"base-2","layout":{"type":"default"}} -->
<div class="wp-block-group alignwide has-base-2-color has-contrast-background-color has-text-color has-background has-link-color" style="padding-top:var(--wp--preset--spacing--30);padding-right:var(--wp--preset--spacing--30);padding-bottom:var(--wp--preset--spacing--30);padding-left:var(--wp--preset--spacing--30)">

	<!-- wp:image {"sizeSlug":"full","linkDestination":"none"} -->
	<figure class="wp-block-image size-full"><img src="https://s.w.org/patterns/files/2021/06/Group-17-scaled.jpg" alt="Image of a woman being carried through the air by swans."/></figure>
	<!-- /wp:image -->

	<!-- wp:columns {"verticalAlignment":"center"} -->
	<div class="wp-block-columns are-vertically-aligned-center">
		
		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Location:', 'themeslug' ); ?></strong><br><?php esc_html_e( '82 Main St. Brooklyn, NY', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Date:', 'themeslug' ); ?></strong><br><?php esc_html_e( 'October 24, 2021', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:buttons -->
			<div class="wp-block-buttons">
				<!-- wp:button {"width":100,"className":"is-style-outline"} -->
				<div class="wp-block-button has-custom-width wp-block-button__width-100 is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Purchase Tickets' ); ?></a></div>
				<!-- /wp:button -->
			</div>
			<!-- /wp:buttons -->
		</div>
		<!-- /wp:column -->

	</div>
	<!-- /wp:columns -->

</div>
<!-- /wp:group -->
```

<!-- 
When a user adds this pattern into their post or page content, they will be able to customize the blocks within the pattern. But they will not be able to add any new blocks from within the UI.
 -->

ユーザーがこのパターンを投稿やページのコンテンツに追加すると、パターン内のブロックをカスタマイズできます。しかし、UI 内から新規ブロックを追加できません。

<!-- 
### Applying content-only editing
 -->

### コンテンツ専用編集の適用

<!-- 
One of the most useful features for patterns is to use template locking to only allow the user to customize the content of a pattern. This can be useful when you need full control over the design but need to allow user input.
 -->

パターンの最も便利な機能のひとつは、テンプレート・ロック機能を使用して、ユーザーがパターンのコンテンツだけをカスタマイズできるようにすることです。これは、設計を完全に制御する必要があるが、ユーザー入力を許可する必要もある場合に便利です。

<!-- 
When this type of locking is applied to a container-type block, users will see a new **Content** panel when inspecting any block instead of the usual block settings:
 -->

コンテナ型ブロックにこのタイプのロックを適用すると、任意のブロックでの作業時、ユーザーには通常のブロック設定の代わりに、新規 **コンテンツ** パネルが表示されます:

<!-- 
[![WordPress post editor with an event pattern shown. The outer Group block is selected. In the sidebar, instead of the normal design and setting controls, it has a "Content" panel that shows the nested blocks.](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-locking-content-only.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-locking-content-only.webp?ssl=1)
 -->

[![イベントパターンが表示された、WordPress 投稿エディター。外側の「グループ」ブロックが選択されている。サイドバーには、通常の設計と設定のコントロールの代わりに、入れ子ブロックを表示する、「コンテンツ」パネルがある。](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-locking-content-only.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-locking-content-only.webp?ssl=1)

<!-- 
This is also a type of locking that has no UI controls and must be manually applied to the block markup. If applied to the outer Group block of your pattern, it will look like this:
 -->

これも UI コントロールのないタイプのロックで、ブロック・マークアップに手動で適用する必要があります。あなたのパターンの外側「グループ」ブロックに適用すると、次のようになります:

```markup
<!-- wp:group {"templateLock":"contentOnly"} -->
```

<!-- 
Note that the `templateLock` attribute is set to `contentOnly`, which means that everything but content editing is locked.
 -->

`templateLock` 属性が、コンテンツ編集以外のすべてがロックされていることを意味する、`contentOnly` に設定されていることに注意してください。

<!-- 
Now let’s apply this to the event pattern. Create a new file in your theme named `/patterns/event-content-only.php` and paste the following code into it:
 -->

では、これをイベント・パターンに適用してみましょう。あなたのテーマに `/patterns/event-content-only.php` という名前の新規ファイルを作成し、以下のコードをペーストしましょう:

```php
<?php
/**
 * Title: Event (Content Only)
 * Slug: themeslug/event-content-only
 * Categories: banner
 * Viewport Width: 1376
 */
?>
<!-- wp:group {"templateLock":"contentOnly","align":"wide","style":{"elements":{"link":{"color":{"text":"var:preset|color|base-2"}}},"spacing":{"padding":{"top":"var:preset|spacing|30","bottom":"var:preset|spacing|30","left":"var:preset|spacing|30","right":"var:preset|spacing|30"}}},"backgroundColor":"contrast","textColor":"base-2","layout":{"type":"default"}} -->
<div class="wp-block-group alignwide has-base-2-color has-contrast-background-color has-text-color has-background has-link-color" style="padding-top:var(--wp--preset--spacing--30);padding-right:var(--wp--preset--spacing--30);padding-bottom:var(--wp--preset--spacing--30);padding-left:var(--wp--preset--spacing--30)">

	<!-- wp:image {"sizeSlug":"full","linkDestination":"none"} -->
	<figure class="wp-block-image size-full"><img src="https://s.w.org/patterns/files/2021/06/Group-17-scaled.jpg" alt="Image of a woman being carried through the air by swans."/></figure>
	<!-- /wp:image -->

	<!-- wp:columns {"verticalAlignment":"center"} -->
	<div class="wp-block-columns are-vertically-aligned-center">
		
		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Location:', 'themeslug' ); ?></strong><br><?php esc_html_e( '82 Main St. Brooklyn, NY', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Date:', 'themeslug' ); ?></strong><br><?php esc_html_e( 'October 24, 2021', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:buttons -->
			<div class="wp-block-buttons">
				<!-- wp:button {"width":100,"className":"is-style-outline"} -->
				<div class="wp-block-button has-custom-width wp-block-button__width-100 is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Purchase Tickets' ); ?></a></div>
				<!-- /wp:button -->
			</div>
			<!-- /wp:buttons -->
		</div>
		<!-- /wp:column -->

	</div>
	<!-- /wp:columns -->

</div>
<!-- /wp:group -->
```

<!-- 
With this setting in place, the user will be able to edit the Image block’s media and the content of the individual Paragraph and Button blocks. But they won’t be able to make any design changes directly inside of the pattern.
 -->

この設定にすると、ユーザーは、「画像」ブロックのメディアと、個々の「段落」ブロックと「ボタン」ブロックのコンテンツを編集できます。しかし、パターンの内側で直接、設計を変更できません。