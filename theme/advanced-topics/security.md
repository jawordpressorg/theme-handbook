<!-- 
# Security
 -->

# セキュリティ

<!-- 
When releasing any code out into the world, whether it will only exist on your own site or hundreds of thousands of sites, it’s important to strive to make it as secure as possible. Responsible coding means being vigilant about all the ways your theme can be exploited.
 -->

世の中にリリースする際には、自身のサイトだけに存在するものであれ、何十万ものサイトに存在するものであれ、可能な限りセキュアにするよう努力することが重要です。責任あるコーディングとは、あなたのテーマが悪用される可能性のあるあらゆる方法を警戒することです。

<!-- 
Your primary source for learning about security in the [Security chapter](https://developer.wordpress.org/apis/security/) in the Common APIs Handbook. This article should be considered a supplement to what you will learn there and is not an all-encompassing guide on security itself. 
 -->

セキュリティについて学ぶためのあなたの主な情報源は、共通 API ハンドブックの [セキュリティ章](https://developer.wordpress.org/apis/security/) です。本稿は、そこで学ぶことを補足するものであり、セキュリティそのものを網羅するガイドではありません。

<!-- 
Below, you will find a list of common vulnerabilities to consider, but please use the Resources section for a more comprehensive overview of how to secure your themes.
 -->

以下に、考慮すべき一般的な脆弱性のリストがありますが、あなたのテーマをセキュアにする方法についてのより包括的な概要は、「リソース」セクションをご利用ください。

<!-- 
## Common vulnerabilities
 -->

## 一般的な脆弱性

<!-- 
Security is an ever-changing landscape, and vulnerabilities evolve over time. The following is an overview of common vulnerabilities you should protect against and the techniques for protecting your theme from exploitation.
 -->

セキュリティは常に変化するものであり、脆弱性は時間とともに進化します。以下は、防御すべき一般的な脆弱性の概要と、あなたのテーマを悪用から守るためのテクニックです。

<!-- 
### Cross-Site Scripting (XSS)
 -->

### クロスサイト・スクリプティング (XSS)

<!-- 
Cross-Site Scripting (XSS) happens when a nefarious party injects JavaScript into a web page.
 -->

悪意のある者が Web ページに JavaScript を注入すると、クロスサイト・スクリプティング (XSS) が起こります。

<!-- 
To avoid XSS vulnerabilities, any output should be escaped. Since it’s the theme’s primary responsibility to output content, you should always [escape dynamic content](https://developer.wordpress.org/apis/security/sanitizing/) with the proper function based on the data type.
 -->

XSS 脆弱性を避けるため、出力はすべてエスケープする必要があります。コンテンツを出力するのはテーマの第一の責任ですので、データタイプにもとづいた適切な関数を使用して、常に [動的コンテンツをエスケープ](https://developer.wordpress.org/apis/security/sanitizing/) する必要があります。

<!-- 
This example shows how to escape an image URL to avoid XSS vulnerabilities:
 -->

この例では、XSS 脆弱性を回避するために画像 URL をエスケープする方法を示します:

```php
<img src="<?php echo esc_url( $great_user_picture_url ); ?>" />
```

<!-- 
Content that has HTML entities within can be sanitized to allow only specified HTML elements:
 -->

HTML エンティティを含むコンテンツは、特定の HTML 要素のみを許可するように、サニタイズできます:

```php
$allowed_html = array(
	'a' => array(
		'href' => array()
	),
	'br'     => array(),
	'em'     => array(),
	'strong' => array()
);

echo wp_kses( $custom_content, $allowed_html );
```

<!-- 
### SQL Injection
 -->

### SQL インジェクション

<!-- 
SQL Injection happens when values being input are not properly sanitized, allowing for any SQL commands in the data to potentially be executed. To prevent this, the WordPress API is extensive. For example, it offers functions like [`add_post_meta()`](https://developer.wordpress.org/reference/functions/add_post_meta/) so that you don’t need to manually insert metadata via SQL.
 -->

SQL インジェクションは、入力される値が適切にサニタイズされていない場合に発生し、データ中の SQL コマンドを可能な限り実行できるようにします。これを防ぐために、WordPress の API は充実しています。たとえば、[`add_post_meta()`](https://developer.wordpress.org/reference/functions/add_post_meta/) のような関数が用意されているので、SQL 経由で手動でメタデータを挿入する必要はありません。

<!-- 
The first rule for hardening your theme against SQL Injection is: **when there’s a WordPress function, use it.**
 -->

SQL インジェクションに対して、あなたのテーマを強化するための最初のルールは: **WordPress 関数があるなら、それを使いましょう。**

<!-- 
While it is rare to do so in themes, sometimes you need to do complex queries that have not been accounted for in the API. If this is the case, always use the [`$wpdb` functions](https://developer.wordpress.org/reference/classes/wpdb/). These were built specifically to protect your database.
 -->

テーマでそのようなことをするのはまれですが、API では考慮されていない複雑なクエリーを行う必要がある場合もあります。そのような場合は、常に [`$wpdb` 関数](https://developer.wordpress.org/reference/classes/wpdb/) を使用してください。これらは、あなたのデータベースを保護するために特別に作られました。

<!-- 
All data in SQL queries must be SQL-escaped before the SQL query is executed to prevent SQL injection attacks. The best function to use for SQL-escaping is `$wpdb->prepare()` which supports both a [`sprintf()`](http://secure.php.net/sprintf)\-like and [`vsprintf()`](http://secure.php.net/vsprintf)\-like syntax:
 -->

SQL クエリーが実行される前に、SQL インジェクション攻撃を防ぐため、SQL クエリー内のデータはすべて SQL エスケープする必要があります。SQL エスケープに最適な関数は、[`sprintf()`](http://secure.php.net/sprintf) 風と [`vsprintf()`](http://secure.php.net/vsprintf) 風構文の両方をサポートする、`$wpdb->prepare()` です:

```php
$wpdb->get_var( $wpdb->prepare(
	"SELECT something FROM table WHERE foo = %s and status = %d",
	$name, // an unescaped string (function will do the sanitization for you)
	$status // an untrusted integer (function will do the sanitization for you)
) );
```

<!-- 
### Cross-Site Request Forgery (CSRF)
 -->

### クロスサイト・リクエスト偽造 (CSRF)

<!-- 
Cross-site request forgery or CSRF (pronounced *sea-surf*) is when a nefarious party tricks a user into performing an unwanted action within a web application they are authenticated in. For example, a phishing email might contain a link to a page that would delete a user’s account in the WordPress admin.
 -->

クロスサイト・リクエスト偽造、または CSRF (*sea-surf* と発音) とは、悪意のある第三者がユーザーを騙して、認証された Web アプリケーション内で、望ましくないアクションを実行させることです。たとえば、フィッシングメールには、WordPress の管理画面からユーザーのアカウントを削除するページへのリンクが、含まれている可能性があります。

<!-- 
This is more common in plugins than themes. But if your theme includes any HTML or HTTP-based form submissions, use a [nonce](https://developer.wordpress.org/apis/security/nonces/) to guarantee a user intends to perform an action:
 -->

これはテーマよりもプラグインで、より一般的です。しかし、もしあなたのテーマが HTML や HTTP ベースのフォーム送信を含む場合には、[nonce](https://developer.wordpress.org/apis/security/nonces/) を使って、ユーザーがアクションを実行する意思があることを保証しましょう:

```php
<form method="post">
	<!-- some inputs here ... -->
	<?php wp_nonce_field( 'name_of_my_action', 'name_of_nonce_field' ); ?>
</form>
```

<!-- 
## Resources
 -->

## 資料

<!-- 
Use the resources listed below to dive more deeply into securing your themes, plugins, and anything else you build on top of WordPress:
 -->

あなたのテーマ、プラグイン、そして WordPress 上に構築するその他のものの安全性をより深く追求するために、以下にリストされている資料を使用しましょう:

<!-- 
*   [Common APIs Handbook: Security](https://developer.wordpress.org/apis/security/)
    *   [Escaping Data](https://developer.wordpress.org/apis/security/escaping/)
    *   [Sanitizing Data](https://developer.wordpress.org/apis/security/sanitizing/)
    *   [Validating Data](https://developer.wordpress.org/apis/security/data-validation/)
    *   [Nonces](https://developer.wordpress.org/apis/security/nonces/)
*   Make Themes: A Guide To Writing Secure Themes:
    *   [Part 1: Introduction](https://make.wordpress.org/themes/2015/05/19/a-guide-to-writing-secure-themes-part-1-introduction/)
    *   [Part 2: Validation](https://make.wordpress.org/themes/2015/05/26/a-guide-to-writing-secure-themes-part-2-validation/)
    *   [Part 3: Sanitization](https://make.wordpress.org/themes/2015/06/02/a-guide-to-writing-secure-themes-part-3-sanitization/)
    *   [Part 4: Securing Post Meta](https://make.wordpress.org/themes/2015/06/09/a-guide-to-writing-secure-themes-part-4-securing-post-meta/)
 -->

*   [共通 API ハンドブック: セキュリティ](https://developer.wordpress.org/apis/security/)
    *   [データのエスケープ](https://developer.wordpress.org/apis/security/escaping/)
    *   [データのサニタイズ](https://developer.wordpress.org/apis/security/sanitizing/)
    *   [データの検証](https://developer.wordpress.org/apis/security/data-validation/)
    *   [nonce](https://developer.wordpress.org/apis/security/nonces/)
*   テーマの作成: 安全なテーマを書くためのガイド:
    *   [パート 1: はじめに](https://make.wordpress.org/themes/2015/05/19/a-guide-to-writing-secure-themes-part-1-introduction/)
    *   [パート 2: 検証](https://make.wordpress.org/themes/2015/05/26/a-guide-to-writing-secure-themes-part-2-validation/)
    *   [パート 3: サニタイズ](https://make.wordpress.org/themes/2015/06/02/a-guide-to-writing-secure-themes-part-3-sanitization/)
    *   [パート 4: ポストメタの保護](https://make.wordpress.org/themes/2015/06/09/a-guide-to-writing-secure-themes-part-4-securing-post-meta/)

<!-- 
### Staying current
 -->

### 現状の把握

<!-- 
It is important to stay current on potential security holes. The following resources provide a good starting point:
 -->

潜在的なセキュリティ・ホールについては、現状を常に把握しておくことが重要です。以下の資料が、良い出発点となるでしょう:

<!-- 
*   [WordPress Security Whitepaper](https://wordpress.org/about/security/)
*   [WordPress Security Release](https://wordpress.org/news/category/security/)
*   [Open Web Application Security Project (OWASP) Top 10](https://www.owasp.org/index.php/OWASP_Top_Ten_Cheat_Sheet)
 -->

*   [WordPress セキュリティ白書](https://wordpress.org/about/security/)
*   [WordPress セキュリティ・リリース](https://wordpress.org/news/category/security/)
*   [オープン Web アプリケーション・セキュリティ・プロジェクト (OWASP) トップ 10](https://www.owasp.org/index.php/OWASP_Top_Ten_Cheat_Sheet)