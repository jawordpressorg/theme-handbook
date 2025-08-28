<!-- 
# UI Best Practices
 -->

# UI のベスト・プラクティス

<!-- 
## Logo Homepage Link
 -->

## ロゴ・ホームページ・リンク

<!-- 
The logo at the top each page should send the user to the homepage of your site.  
If you are using the recommended function, [the\_custom\_logo()](https://developer.wordpress.org/reference/functions/the_custom_logo/) or the site logo block, the logo is linked to the homepage by default.
 -->

各ページ上部のロゴは、あなたのサイトのホームページに、ユーザーを誘導する必要があります。推奨関数 [`the_custom_logo()`](https://developer.wordpress.org/reference/functions/the_custom_logo/) または「サイト・ロゴ」ブロックを使用している場合、ロゴはデフォルトでホームページにリンクされます。

<!-- 
You can also add your logo manually. Assuming your logo is in your theme directory, this is how to display it in the `header.php` template file.
 -->

あなたのロゴを手動でも追加できます。あなたのロゴが、あなたのテーマ・ディレクトリにあると仮定して、 `header.php` テンプレート・ファイルでそれを表示する方法は、次のとおりです。

```php
<a href="<?php echo esc_url( home_url( '/' ) ); ?>"><img src="<?php echo get_stylesheet_directory_uri(); ?>/logo.png" alt="<?php esc_attr_e( 'Home Page', 'textdmomain' );?>" /></a>
```

<!-- 
## Descriptive Anchor Text
 -->

## 説明的アンカー・テキスト

<!-- 
The anchor text is the visible text for a hyperlink. Good link text should give the reader an idea of the action that will take place when clicking it.
 -->

アンカー・テキストとは、ハイパーリンクの表示されるテキストのことです。良いリンクテキストは、クリックした際に発生する操作を、読者に伝えるべきです。

<!-- 
A bad example:
 -->

悪例:

<!-- 
```
The best way to learn WordPress is to start using it. To Download WordPress, click here.
```
 -->

```
WordPress を学ぶ最良の方法は、実際に使い始めることです。WordPress をダウンロードするには、こちらをクリックしてください。
```

<!-- 
A better example:
 -->

良例:

<!-- 
```
Download WordPress and start using it. That's the best way to learn.
```
 -->

```
WordPress をダウンロードして使い始めましょう。それが学ぶ最善の方法です。
```

<!-- 
## Style Links with Underlines
 -->

## 下線付きスタイル・リンク

<!-- 
By default, browsers underline links to let the user know what is clickable. Some designers use CSS to turn off underlines for hyperlinks. This causes usability and accessibility problems, as it makes it more difficult to identify hyperlinks from the surrounding text.
 -->

デフォルトでは、ブラウザはリンクに下線を引いて、ユーザーにクリック可能な箇所を知らせます。一部のデザイナーは CSS を使用して、ハイパーリンクの下線を非表示にします。これにより、周囲のテキストからハイパーリンクを識別しにくくなるため、ユーザビリティーとアクセシビリティーの問題が生じます。

<!-- 
## Different Link Colors
 -->

## 別のリンク色

<!-- 
Color is another visual cue that text is clickable. Styling hyperlinks with a different color than the surrounding text makes them easier to distinguish.
 -->

色は、テキストがクリック可能であることを示す、もう一つの視覚的手がかりです。ハイパーリンクを、周囲のテキストとは異なる色でスタイル設定することで、見分けやすくなります。

<!-- 
Hyperlinks are one of the few HTML features that have state. The two most important states are *visited* and *unvisited*.
 -->

ハイパーリンクは、状態を持つ数少ない HTML 機能の一つです。最も重要な状態は *visited* と *unvisited* の2つです。

<!-- 
Having different colors for these two states helps users identify the pages they’ve visited before. A good trick for taking the guess work out of visited links is to color them 10%-20% darker than the unvisited links.
 -->

これらの2つの状態に別の色を割り当てることで、ユーザーは以前に閲覧したページを識別しやすくなります。訪問済みリンクの見分けを簡単にする良い方法は、未訪問リンクより10～20％暗い色で表示することです。

<!-- 
There are 3 other states that links can have:
 -->

リンクが持つ可能性のある他の状態は、3つあります:

<!-- 
*   hover, when a mouse is over an element
*   focus, similar to hover but for keyboard users
*   active, when a user is clicking on a link
 -->

*   hover: マウスが要素の上にあるとき
*   focus: hover と同様だが、キーボード・ユーザー向け
*   active: ユーザーがリンクをクリックしているとき

<!-- 
Since hover and focus have similar meanings, it is useful to give them the same styles.
 -->

hover と focus は類似した意味を持つため、同じスタイルを適用すると便利です。

<!-- 
Though hover and focus have similar meanings, they have different interaction patterns. If you choose a subtle hover state, you should have a more easily identifiable focus state. Hovering over a link is a directed activity, where the user knows where they are in the page and only needs to identify whether that spot is linked. Focus is an undirected activity, where the user needs to discover where their focus has moved to after shifting focus from the previous location.
 -->

hover と focus は類似した意味を持つものの、異なるインタラクション・パターンを有します。微妙な hover 状態を選択する場合、より識別しやすい focus 状態を設けるべきです。リンクの上に hover する行為は、ユーザーがページ内の現在位置を把握した上で、その箇所がリンクかどうかを確認するだけの、指向性のある操作なのです。Focus は、ユーザーはフォーカスを以前の位置から移動させた後、そのフォーカスがどこに移動したかを自ら発見する必要がある、非指向性のない操作なのです。

<!-- 
## Color Contrast
 -->

## 色コントラスト

<!-- 
Color contrast refers to the **difference between two colors**. Contrast is low between navy blue and black. Contrast is high between white and black. WebAIM, a non-profit web accessibility organization, provides a [color contrast calculator](https://webaim.org/resources/contrastchecker/) to help you determine the contrast in your website design. The WCAG 2.0 requires a ratio of 4.5:1 on normal text to be [AA compliant](http://www.w3.org/WAI/WCAG20/quickref/#qr-visual-audio-contrast-contrast).
 -->

色コントラストとは **2色間の違い** を意味します。濃紺と黒のコントラストは低く、白と黒のコントラストは高いです。非営利 Web アクセシビリティー団体 WebAIM は、あなたの Web サイトデザインのコントラストを判断するのに役立つ、[色コントラスト・カリキュレーター](https://webaim.org/resources/contrastchecker/) を提供しています。通常のテキストが [AA 準拠](http://www.w3.org/WAI/WCAG20/quickref/#qr-visual-audio-contrast-contrast) となるには、WCAG2.0では `4.5:1` の比率が要求されます。

<!-- 
## Sufficient Font Size
 -->

## 十分なフォント・サイズ

<!-- 
Make your text easy to read. By making your text large enough, you increase the usability of your site and make the content easier to understand. 14px is the smallest text should be.
 -->

あなたのテキストは、読み易いものにしましょう。あなたのテキストを十分に大きくすることで、あなたのサイトのユーザビリティーが向上し、コンテンツが理解しやすくなります。`14px` が最小のテキスト・サイズだと考えましょう。

<!-- 
## Associate Labels with Inputs
 -->

## 入力項目に関連付けたラベル

<!-- 
Labels inform the user what an input field is for. You can connect the label to the input by using the `for` attribute in the label. This will allow the user to click the label and focus on the input field.
 -->

ラベルは、入力フィールドの用途をユーザーに伝えるものです。ラベルに `for` 属性を使用することで、ラベルを入力フィールドに接続できます。これにより、ユーザーはラベルをクリックして、入力フィールドにフォーカスを移すことができます。

```
<label for="username">Username</label>
<input type="text" id="username" name="login" />
```

<!-- 
Labels work for radio buttons as well. Since it works using the **id** field *and not the name*, each input for the group gets its own label.
 -->

ラベルは、ラジオボタンにも適用されます。*name ではなく* **id** フィールドを使用して動作するため、グループの各入力項目には、固有のラベルが付与されます。

```
<input type="radio" id="user_group_blogger" name="user_group" value="blogger" />
<label for="user_group_blogger">Blogger</label>
 
<input type="radio" id="user_group_designer" name="user_group" value="designer" />
<label for="user_group_designer">Designer</label>
 
<input type="radio" id="user_group_developer" name="user_group" value="developer" />
<label for="user_group_developer">Developer</label>
```

<!-- 
## Placeholder Text in Forms
 -->

## フォーム内のプレースホルダー・テキスト

<!-- 
Placeholder text shows the user an example of what to type. When a user puts their cursor in the field, the placeholder text will disappear, while the label remains.
 -->

プレースホルダー・テキストは、ユーザーに入力例を示します。ユーザーがフィールドにカーソルを置くと、プレースホルダー・テキストは消え、ラベルは表示されたままになります。

```
<label for="name">Name</label>
<input type="text" id="name" name="name" placeholder="John Smith" />
```

<!-- 
Use placeholders to suggest the type of data a field requires, and not as a substitute for the field label.
 -->

プレースホルダーは、フィールドに必要なデータの種類を示すために使用し、フィールド・ラベルの代わりとして使用しないでください。

<!-- 
## Descriptive Buttons
 -->

## 説明的なボタン

<!-- 
The web is filled with buttons that have unclear meanings. Remember the last time you used ‘OK’ or ‘submit’ on your login form? Choosing better words to display on your buttons can make your website easier to use. Try the pattern *\[verb\] \[noun\]* — Create user, Delete File, Update Password, Send Message. Each describes what will happen when the user clicks the button.
 -->

Web には意味が不明なボタンが溢れています。あなたのログインフォームで最後に「OK」や「送信」を使ったのはいつか、覚えてます ? あなたのボタンに表示する言葉を選ぶことで、あなたの Web サイトはもっと使いやすくなります。*[名刺] [動詞]* パターンを試してみてください — ユーザー作成、ファイル削除、パスワード更新、メッセージ送信。各々は、ユーザーがボタンをクリックしたときに何が起こるかを説明しています。