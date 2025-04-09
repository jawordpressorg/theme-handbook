# Privacy

WordPress 4.9.6 introduced several tools to help sites meet the requirements of the European Union’s new GDPR (General Data Protection Regulation) and other potential laws across the world. This article details what theme authors need to know about compatibility with the features.

For the most part, this should not directly impact themes, but you should make sure that nothing in your theme’s design or functionality conflicts with these features.

## Privacy Policy page

WordPress lets users select a privacy policy page via the **Settings > Privacy** screen in the admin. For newly-created WordPress installs (since version 4.9.6), a privacy policy page is automatically created with a draft status.

### Linking to the Privacy Policy page

If you need to manually link to the Privacy Policy page on a site, WordPress provides a few functions for getting or outputting the URL or link:

*   [**`get_privacy_policy_url()`**](https://developer.wordpress.org/reference/functions/get_privacy_policy_url/)**:** Retrieves the URL to the Privacy Policy page.
*   [**`the_privacy_policy_link()`**](https://developer.wordpress.org/reference/functions/the_privacy_policy_link/)**:** Displays the Privacy Policy page link with formatting, when applicable.
*   [**`get_the_privacy_policy_link()`**](https://developer.wordpress.org/reference/functions/get_the_privacy_policy_link/)**:** Returns the Privacy Policy page link with formatting, when applicable.

The following example will display the privacy policy link surrounded by a `<div>` element:

```php
<?php the_privacy_policy_link( '<div>', '</div>' ); ?>
```

### Privacy Policy page template

While it is generally unnecessary for most themes, you can add a custom [Privacy Policy template](https://developer.wordpress.org/themes/templates/template-hierarchy/#privacy-policy-page-hierarchy) to customize the output of the page. This is an optional template:

*   **Block Themes:** `templates/privacy-policy.html`
*   **Classic Themes:** `privacy-policy.php`

If you decide to create a custom template, make sure that you output the page’s content using the appropriate block or function:

*   **Block Themes:** [Post Content block](https://wordpress.org/documentation/article/post-content-block/)
*   **Classic Themes:** [`the_content()` function](https://developer.wordpress.org/reference/functions/the_content/)

This ensures that the user’s Privacy Policy content will be correctly displayed on the front end of the site.

## Comment cookies

When a logged out user comments on a post, they are asked for their name, email, and website. This information is stored locally in the commenter’s browser for two purposes:

1.  When they leave another comment on the site, their name, email, and website will be pre-populated into the respective fields.
2.  If their comment is held for moderation, they can return to that post and remove the comment before it is approved.

The information stored in this cookie is for convenience and is not essential. Therefore, the user needs to be given the choice to opt in or opt out of the storage of this data. For this reason, WordPress outputs a checkbox in the comment form that allows commenters to opt-in to storing this data in the cookie. This checkbox will be unchecked by default, as opt-in is an action the user must explicitly approve.

The new checkbox field is automatically added to comment forms displayed using the [Comment Form](https://wordpress.org/documentation/article/post-comments-form-block/) block (block themes) or the [`comment_form()`](https://developer.wordpress.org/reference/functions/comment_form/) function (classic themes).

While most themes will not require any action, it is recommended that you double check that the input and label does not require CSS adjustments in custom themes.