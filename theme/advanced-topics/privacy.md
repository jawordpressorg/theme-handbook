<!-- 
# Privacy
 -->

# プライバシー

<!-- 
WordPress 4.9.6 introduced several tools to help sites meet the requirements of the European Union’s new GDPR (General Data Protection Regulation) and other potential laws across the world. This article details what theme authors need to know about compatibility with the features.
 -->

WordPress 4.9.6では、EU の新しい GDPR (General Data Protection Regulation。一般データ保護規則) や、世界中のその他の潜在的な法律の要件を満たすサイトを支援するツールがいくつか導入されました。本稿では、この機能との互換性について、テーマ作者が知っておくべきことを詳しく説明します。

<!-- 
For the most part, this should not directly impact themes, but you should make sure that nothing in your theme’s design or functionality conflicts with these features.
 -->

ほとんどの場合、これがテーマに直接影響することはありません。しかし、テーマのデザインや機能が、これらの機能と競合しないことは確認してください。

<!-- 
## Privacy Policy page
 -->

## 「個人情報保護方針」ページ

<!-- 
WordPress lets users select a privacy policy page via the **Settings > Privacy** screen in the admin. For newly-created WordPress installs (since version 4.9.6), a privacy policy page is automatically created with a draft status.
 -->

WordPress では、管理画面の **設定 > プライバシー** 画面経由で個人情報保護方針ページをユーザーが選択できるようになっています。(バージョン4.9.6以降) 新規に WordPress をインストールした場合、個人情報保護方針ページは下書き状態で自動的に作成されます。

<!-- 
### Linking to the Privacy Policy page
 -->

### 「個人情報保護方針」ページへのリンク

<!-- 
If you need to manually link to the Privacy Policy page on a site, WordPress provides a few functions for getting or outputting the URL or link:
 -->

サイトの「個人情報保護方針」ページに手動でリンクする必要がある場合、WordPress には、URL やリンクを取得したり出力したりするための関数がいくつか用意されています:

<!-- 
*   [**`get_privacy_policy_url()`**](https://developer.wordpress.org/reference/functions/get_privacy_policy_url/)**:** Retrieves the URL to the Privacy Policy page.
*   [**`the_privacy_policy_link()`**](https://developer.wordpress.org/reference/functions/the_privacy_policy_link/)**:** Displays the Privacy Policy page link with formatting, when applicable.
*   [**`get_the_privacy_policy_link()`**](https://developer.wordpress.org/reference/functions/get_the_privacy_policy_link/)**:** Returns the Privacy Policy page link with formatting, when applicable.
 -->

*   [**`get_privacy_policy_url()`**](https://developer.wordpress.org/reference/functions/get_privacy_policy_url/)**:**「個人情報保護方針」ページの URL を取得します。
*   [**`the_privacy_policy_link()`**](https://developer.wordpress.org/reference/functions/the_privacy_policy_link/)**:** 該当する場合、フォーマット付きの「個人情報保護方針」ページ・リンクを表示します。
*   [**`get_the_privacy_policy_link()`**](https://developer.wordpress.org/reference/functions/get_the_privacy_policy_link/)**:** 該当する場合、フォーマット付きの「個人情報保護方針」ページ・リンクを返します。

<!-- 
The following example will display the privacy policy link surrounded by a `<div>` element:
 -->

次の例では、個人情報保護方針リンクを `<div>` 要素で囲んで表示します:

```php
<?php the_privacy_policy_link( '<div>', '</div>' ); ?>
```

<!-- 
### Privacy Policy page template
 -->

### 「個人情報保護方針」ページ・テンプレート

<!-- 
While it is generally unnecessary for most themes, you can add a custom [Privacy Policy template](https://developer.wordpress.org/themes/templates/template-hierarchy/#privacy-policy-page-hierarchy) to customize the output of the page. This is an optional template:
 -->

ほとんどのテーマでは一般的に不要ですが、カスタム [「個人情報保護方針」テンプレート](https://developer.wordpress.org/themes/templates/template-hierarchy/#privacy-policy-page-hierarchy) を追加して、ページの出力をカスタマイズできます。これは任意のテンプレートです:

<!-- 
*   **Block Themes:** `templates/privacy-policy.html`
*   **Classic Themes:** `privacy-policy.php`
 -->

*   **ブロック・テーマ:** `templates/privacy-policy.html`
*   **クラシック・テーマ:** `privacy-policy.php`

<!-- 
If you decide to create a custom template, make sure that you output the page’s content using the appropriate block or function:
 -->

カスタム・テンプレートを制作する際には、適切なブロックや関数を使用して、ページのコンテンツを出力してください:

<!-- 
*   **Block Themes:** [Post Content block](https://wordpress.org/documentation/article/post-content-block/)
*   **Classic Themes:** [`the_content()` function](https://developer.wordpress.org/reference/functions/the_content/)
 -->

*   **ブロック・テーマ:** [「投稿コンテンツ」ブロック](https://wordpress.org/documentation/article/post-content-block/)
*   **クラシック・テーマ:** [`the_content()` function](https://developer.wordpress.org/reference/functions/the_content/)

<!-- 
This ensures that the user’s Privacy Policy content will be correctly displayed on the front end of the site.
 -->

これにより、ユーザーの「個人情報保護方針」コンテンツが、サイトのフロントエンドに正しく表示されます。

<!-- 
## Comment cookies
 -->

## コメント Cookie

<!-- 
When a logged out user comments on a post, they are asked for their name, email, and website. This information is stored locally in the commenter’s browser for two purposes:
 -->

ログアウトしたユーザーが投稿にコメントする際、名前、E メール、Web サイトの入力を求められます。この情報は、2つの目的でコメント投稿者のブラウザにローカルに保存されます:

<!-- 
1.  When they leave another comment on the site, their name, email, and website will be pre-populated into the respective fields.
2.  If their comment is held for moderation, they can return to that post and remove the comment before it is approved.
 -->

1.  彼らがサイトにコメントを残す際、氏名、E メール、Web サイトは、それぞれのフィールドに事前に入力されます。
2.  自分のコメントがモデレーションのために保留された場合、その投稿に戻り、承認される前にコメントを削除できます。

<!-- 
The information stored in this cookie is for convenience and is not essential. Therefore, the user needs to be given the choice to opt in or opt out of the storage of this data. For this reason, WordPress outputs a checkbox in the comment form that allows commenters to opt-in to storing this data in the cookie. This checkbox will be unchecked by default, as opt-in is an action the user must explicitly approve.
 -->

この Cookie に保存される情報は利便性のためのものであり、必須ではありません。したがって、このデータの保存をオプトインまたはオプトアウトする選択肢をユーザーに与える必要があります。このため、WordPress はコメントフォームにチェックボックスを出力し、コメント投稿者がこのデータを Cookie に保存することをオプトインできるようにしています。オプトインはユーザーが明示的に承認しなければならないアクションであるため、このチェックボックスはデフォルトではチェックされていません。

<!-- 
The new checkbox field is automatically added to comment forms displayed using the [Comment Form](https://wordpress.org/documentation/article/post-comments-form-block/) block (block themes) or the [`comment_form()`](https://developer.wordpress.org/reference/functions/comment_form/) function (classic themes).
 -->

新規チェックボックス・フィールドは、[「コメントフォーム」](https://wordpress.org/documentation/article/post-comments-form-block/) ブロック (ブロック・テーマ) または [`comment_form()`](https://developer.wordpress.org/reference/functions/comment_form/) 関数 (クラシック・テーマ) を使用して表示されるコメント・フォームに、自動的に追加されます。

<!-- 
While most themes will not require any action, it is recommended that you double check that the input and label does not require CSS adjustments in custom themes.
 -->

ほとんどのテーマでは何もする必要はありませんが、カスタム・テーマでは、入力とラベルに CSS の調整が必要ないか再確認することを推奨します。