<!-- 
# JavaScript/Underscore.js-Rendered Custom Controls
 -->

# JavaScript/Underscore.js でレンダリングされた、カスタムコントロール

<!-- 
WordPress 4.1 also added support for rendering JavaScript-heavy and/or high-quantity controls entirely with JavaScript. This allows for more dynamic behavior, especially related to dynamically-added controls. The core Color and Media controls currently leverage this API, and all core Controls will eventually use it in the future. The PHP-based control API is not going away, but in the future most controls will likely use the new API since it provides a faster experience for users and developers. Similar APIs for JS-templated Sections and Panels were introduced WordPress 4.3; however, there remain some gaps in the ease of dynamically-creating objects in JS as of WordPress 4.7, see [#30741](https://core.trac.wordpress.org/ticket/30741).
 -->

WordPress v4.1では、JavaScript を多用するコントロールや、大量のコントロールを完全に JavaScript でレンダリングする機能も、サポートされました。これにより、特に動的に追加されるコントロールに関連する、より動的な動作が可能になります。現在、コアのカラーコントロールとメディアコントロールがこの API を活用しており、将来的には、すべてのコアコントロールが、これを使用する予定です。PHP ベースのコントロール API は廃止されませんが、ユーザーと開発者にとって高速な体験を可能にするため、将来的にはほとんどのコントロールが新しい API を使用するようになるでしょう。JavaScript テンプレート化されたセクションおよびパネル向けの類似 API は、WordPress v4.3で導入されました; ただし、WordPress v4.7時点では、JavaScript における動的オブジェクト生成の容易さには、依然としていくつかのギャップが存在しており、詳細は [#30741](https://core.trac.wordpress.org/ticket/30741) をご覧ください。

<!-- 
## Registered Control Types
 -->

## 登録済みコントロールタイプ

<!-- 
In order to introduce a concept of having one template for multiple Customizer controls of the same type, we needed to introduce a way to register a type of control with the Customize Manager. Previously, custom control objects were only encountered when custom controls were added using `[WP_Customize_Manager::add_control()](https://developer.wordpress.org/reference/classes/wp_customize_manager/add_control/)`. But detecting added control types to render one template per type wouldn’t allow new controls to be created dynamically if no other instances of that type were loaded. `[WP_Customize_Manager::register_control_type()](https://developer.wordpress.org/reference/classes/wp_customize_manager/register_control_type/) solves this:`
 -->

同一タイプの複数の「カスタマイザー」コントロールに対して、1つのテンプレートを適用するしくみを導入するため、「カスタマイズマネージャー」にコントロールのタイプを登録する方法を、導入する必要がありました。従来、カスタムコントロールオブジェクトは、[`WP_Customize_Manager::add_control()`](https://developer.wordpress.org/reference/classes/wp_customize_manager/add_control/) を使用してカスタムコントロールが追加された場合にのみ、遭遇していました。しかし、追加されたコントロールタイプを検出してタイプごとにテンプレートをレンダリングする方式では、そのタイプの他のインスタンスがロードされていない場合、動的に新規コントロールを作成できません。[`WP_Customize_Manager::register_control_type()`](https://developer.wordpress.org/reference/classes/wp_customize_manager/register_control_type/) が、この問題を解決します:

```php
add_action( 'customize_register', 'prefix_customize_register' );
function prefix_customize_register( $wp_customize ) {
  // Define a custom control class, WP_Customize_Custom_Control.
  // Register the class so that its JS template is available in the Customizer.
  $wp_customize->register_control_type( 'WP_Customize_Custom_Control' );
}
```

<!-- 
All registered control types have their templates printed to the customizer by `WP_Customize_Manager::print_control_templates()`.
 -->

登録済みのすべてのコントロールタイプは、`WP_Customize_Manager::print_control_templates()` によって、そのテンプレートがカスタマイザーに出力されます。

<!-- 
## Sending PHP Control Data to JavaScript
 -->

## JavaScript に PHP コントロールデータの送信

<!-- 
While Customizer control data has always been passed to the control JS models, and this has always been able to be extended, you’re much more likely to need to send data down when working with JS templates. Anything that you would want access to in `render_content()` in PHP will need to be exported to JavaScript to be accessible in your control template. `WP_Customize_Control` exports the following control class variables by default:
 -->

「カスタマイザー」のコントロールデータは常にコントロールの JavaScript モデルに渡され、これは常に拡張可能でしたが、JavaScript テンプレートを扱う際には、データを下方向に送信する必要性が、はるかに高くなります。PHP の `render_content()` 内でアクセスしたいものはすべて、あなたのコントロールテンプレート内でアクセス可能にするために、JavaScript にエクスポートする必要があります。`WP_Customize_Control` は、デフォルトで、下記コントロールクラス変数をエクスポートします:

<!-- 
*   `type`
*   `label`
*   `description`
*   `active` (boolean state)
 -->

*   `type`
*   `label`
*   `description`
*   `active` (真偽値ステート)

<!-- 
You can add additional parameters specific to your custom control by overriding `[WP_Customize_Control::to_json()](https://developer.wordpress.org/reference/classes/wp_customize_control/to_json/)` in your custom control subclass. In most cases, you’ll want to call the parent class’ `to_json()` method also, to ensure that all core variables are exported as well. Here’s an example from the core color control:
 -->

あなたのカスタムコントロールのサブクラスで、[`WP_Customize_Control::to_json()`](https://developer.wordpress.org/reference/classes/wp_customize_control/to_json/) をオーバーライドすることで、あなたのカスタムコントロール固有の追加パラメータを追加できます。ほとんどのケースでは、親クラスの `to_json()` メソッドもコールして、すべてのコア変数がエクスポートされるようにする必要があります。以下は、コアのカラーコントロールからの例です:

```php
public function to_json() {
  parent::to_json();
  $this->json['statuses'] = $this->statuses;
  $this->json['defaultValue'] = $this->setting->default;
}
```

<!-- 
## JS/Underscore Templating
 -->

## JS/Underscore テンプレート機能

<!-- 
Once you’ve registered your custom control class as a control type and exported any custom class variables, you can create the template that will render the control UI. You’ll override `[WP_Customize_Control::content_template()](https://developer.wordpress.org/reference/classes/wp_customize_control/content_template/)` (empty by default) as a replacement for `[WP_Customize_Control::render_content()](https://developer.wordpress.org/reference/classes/wp_customize_control/render_content/)`. Render content is still called, so be sure to override it with an empty function in your subclass as well.
 -->

あなたのカスタムコントロールクラスをコントロールタイプとして登録し、任意のカスタムクラス変数をエクスポートしたら、コントロール UI をレンダリングするテンプレートを作成できます。[`WP_Customize_Control::render_content()`](https://developer.wordpress.org/reference/classes/wp_customize_control/render_content/) の代替として、[`WP_Customize_Control::content_template()`](https://developer.wordpress.org/reference/classes/wp_customize_control/content_template/) (デフォルトでは `empty`) をオーバーライドします。`render_content()` は引き続きコールされるため、サブクラスでも必ず `empty` 関数でオーバーライドしてあることを確認しましょう。

<!-- 
Underscore-style custom control templates are very similar to PHP. As more and more of WordPress core becomes JavaScript-driven, these templates are becoming increasingly more common. Some sample template code in core can be found in [media](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/media-template.php), [revisions](https://core.trac.wordpress.org/browser/trunk/src/wp-admin/includes/revision.php#L260), the [theme browser](https://core.trac.wordpress.org/browser/trunk/src/wp-admin/themes.php#L293), and even [in the Twenty Fifteen theme](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentyfifteen/inc/customizer.php#L266), where a JS template is used to both save the color scheme data and instantly preview color scheme changes in the Customizer. The best way to learn how these templates work is to study similar code in core and, accordingly, here is a brief example:
 -->

Underscore スタイルのカスタムコントロールテンプレートは、PHP と非常に似ています。WordPress のコアがますます JavaScript 駆動になるにつれ、これらのテンプレートはますます一般的になってきています。コア内のサンプルテンプレートコードは、[メディア](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/media-template.php)、[リビジョン](https://core.trac.wordpress.org/browser/trunk/src/wp-admin/includes/revision.php#L260)、[テーマブラウザー](https://core.trac.wordpress.org/browser/trunk/src/wp-admin/themes.php#L293)、さらには [Twenty Fifteen テーマ](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentyfifteen/inc/customizer.php#L266) 内でも確認でき、ここでは JavaScript テンプレートがカラースキームデータの保存と、「カスタマイザー」内でのカラースキーム変更の即時プレビューの両方に使用されています。これらのテンプレートのしくみを理解する最良の方法は、コア内の類似コードを学習することですので、以下に簡単な例を示します:

```php
class WP_Customize_Color_Control extends WP_Customize_Control {
  public $type = 'color';
// ...
  /**
   * Render a JS template for the content of the color picker control.
   */
  public function content_template() {
    ?>
    <# var defaultValue = '';
    if ( data.defaultValue ) {
      if ( '#' !== data.defaultValue.substring( 0, 1 ) ) {
        defaultValue = '#' + data.defaultValue;
      } else {
        defaultValue = data.defaultValue;
      }
      defaultValue = ' data-default-color=' + defaultValue; // Quotes added automatically.
    } #>
    <label>
      <# if ( data.label ) { #>
        <span class="customize-control-title">{{{ data.label }}}</span>
      <# } #>
      <# if ( data.description ) { #>
        <span class="description customize-control-description">{{{ data.description }}}</span>
      <# } #>
      <div class="customize-control-content">
        <input class="color-picker-hex" type="text" maxlength="7" placeholder="<?php esc_attr_e( 'Hex Value' ); ?>" {{ defaultValue }} />
      </div>
    </label>
    <?php
  }
}
```

<!-- 
In the above template for the core custom color control, you can see that after the closing PHP tag, we have a JS template. notation is used around statements to be evaluated – in most cases, this is used for conditionals. All of the control instance data that we exported to JS is stored in the \`data\` object, and we can print a variable using double (escaped) or triple (unescaped) brace notation `{{ }}`. As I said before, the best way to get the hang of writing controls like this is to read through existing examples. [`WP_Customize_Upload_Control`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/class-wp-customize-control.php#L639) was recently [updated to leverage this API](https://core.trac.wordpress.org/changeset/30309) as well, integrating nicely with the way the media manager is implemented, and squeezing a ton of functionality out of a minimal amount of code. If you want some really good practice, try converting some of the other core controls to use this API – and submit patches to core too, of course!
 -->

上記のカスタムカラーコントロール用コアテンプレートでは、PHP 終了タグの後に JavaScript テンプレートが記述されていることが確認できます。評価対象の文の周囲には、ノーテーションが使用されます – ほとんどのケースでは、これは条件式に使用されます。JavaScript にエクスポートしたすべてのコントロールインスタンスデータは、`data` オブジェクトに格納されており、変数は「二重波括弧」記法 (エスケープ) `{{ }}` または「三重波括」弧記法 (エスケープなし) `{{{ }}}` で出力できます。以前も述べたように、このようなコントロールの書き方を習得する最良の方法は、既存の例を読み通すことです。[`WP_Customize_Upload_Control`](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/class-wp-customize-control.php#L639) は、最近 [本 API を活かすよう更新](https://core.trac.wordpress.org/changeset/30309) され、メディアマネージャーの実装方法と非常にうまく統合されており、最小限のコードで膨大な機能を実現しています。本当に優れたグッドプラクティスをお求めなら、他のコアコントロールの一部をこの API を使用するように移行してみましょう – もちろん、コアへのパッチ提出も忘れずに !

<!-- 
## Putting the pieces together
 -->

## ピースのつなぎ合わせ

<!-- 
Here’s a summary of what’s needed to leverage the new API in a custom customizer control subclass:
 -->

カスタムカスタマイザーコントロールのサブクラスで新しい API を活用するために何が必要か、以下に要約します:

<!-- 
1.  Make your render\_content() function empty (but it does need to exist to override the default one).
2.  Create a new function, content\_template(), and put the old contents of render\_content() there.
3.  Add any custom class variables that are needed for the control to be exported to the JavaScript in the browser (the JSON data) by modifying the to\_json() function (see [WP\_Customize\_Color\_Control](https://developer.wordpress.org/reference/classes/wp_customize_color_control/) for an example).
4.  Convert the PHP from render\_content() into a JS template, using around JS statements to evaluate and {{ }} around variables to print. PHP class variables are available in the data object; for example, the label can be printed with {{ data.label }}.
5.  **Register the custom control class/type**. This critical step tells the Customizer to print the template for this control. This is distinct from just printing templates for all controls that were added because the ideas are that many instances of this control type could be rendered from one template, and that any registered control types would be available for dynamic control-creation in the future. Just do something like $wp\_customize->register\_control\_type( '[WP\_Customize\_Color\_Control](https://developer.wordpress.org/reference/classes/wp_customize_color_control/)' );.
 -->

1.  あなたの `render_content()` 関数を `empty` にします (ただし、デフォルトのものをオーバーライドするために、存在する必要がある)。
2.  新しい関数 `content_template()` を作成し、`render_content()` の旧内容を、そこに移します。
3.  `to_json()` 関数を修正することで、コントロールをブラウザーの JavaScript にエクスポートするために必要な、任意のカスタムクラス変数 (JSON データ) を追加します (たとえば、[`WP_Customize_Color_Control`](https://developer.wordpress.org/reference/classes/wp_customize_color_control/) を参照)。
4.  PHP の `render_content()` を JavaScript テンプレートに変換し、評価には JavaScript ステートメントを、変数の出力には `{{ }}` を使用しましょう。PHP のクラス変数は、データオブジェクト内で利用可能です; たとえば、ラベルは `{{data.label}}` で出力できます。
5.  **カスタムコントロールクラス/タイプを登録します**。この重要な手順により、「カスタマイザー」は、本コントロールのテンプレートを出力するよう通知されます。これは、追加されたすべてのコントロールに対して、単にテンプレートを出力するだけとは異なります。なぜなら、このコントロールタイプの多くのインスタンスが1つのテンプレートからレンダリングされる可能性があり、また登録済みのコントロールタイプは、将来の動的なコントロール作成に利用可能となる、という考え方にもとづいているからです。[`$wp_customize->register_control_type(WP_Customize_Color_Control);`](https://developer.wordpress.org/reference/classes/wp_customize_color_control/) のようなことを実行するだけです。

<!-- 
The PHP-only parts of the Customize API are still fully supported and perfectly fine to use. But given long term goals for making the customizer more flexible for doing things like switching themes in the customizer without a pageload, it is strongly encouraged to use JS/Underscore templates for all custom customizer objects where feasible.
 -->

「カスタマイズ API」の PHP 専用部分は、引き続き完全にサポートされており、問題なく使用できます。ただし、カスタマイザー内でページロードなしでテーマを切り替えるなど、カスタマイザーの柔軟性を高めるという長期的な目標を考慮すると、可能な限り、すべてのカスタムカスタマイザーオブジェクトに対して JavaScript/Underscore テンプレートを使用することが、強く推奨されます。