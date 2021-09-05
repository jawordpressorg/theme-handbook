# Theme Privacy

In WordPress 4.9.6, several tools were introduced to help sites meet the requirements of the new European Union’s new GDPR (General Data Protection Regulation) laws. This article details what theme authors need to know about compatibility with the features.

Theme authors should test their themes to confirm that there are no design conflicts between the features and their themes detailed below.

## Privacy Policy Pages

WordPress 4.9.6 introduced the ability to select a page as a privacy policy for a site in the Settings > Privacy section of the admin area. For new sites, a privacy policy template page will automatically be created in draft status.

To link to the selected page in plugins and themes, three template tags have been added:

*   [get\_privacy\_policy\_url()](https://developer.wordpress.org/reference/functions/get_privacy_policy_url/) – Retrieves the URL to the privacy policy page.
*   [the\_privacy\_policy\_link()](https://developer.wordpress.org/reference/functions/the_privacy_policy_link/) – Displays the privacy policy link with formatting, when applicable.
*   [get\_the\_privacy\_policy\_link()](https://developer.wordpress.org/reference/functions/get_the_privacy_policy_link/) – Returns the privacy policy link with formatting, when applicable.

### Example

The following example will display the privacy policy link surrounded by a `div` element

<br />
if ( function\_exists( 'the\_privacy\_policy\_link' ) ) {<br />
   the\_privacy\_policy\_link( '&lt;div>', '&lt;/div>' );<br />
}<br />

## Commenter Cookie Opt-Ins

When a logged out user comments on a post, they are asked for their name, email, and website. This information is stored locally in the commenter’s browser for two purposes:

1.  When they leave another comment on the site, their name, email, and website will be pre-populated into the respective fields.
2.  If their comment is held for moderation, they can return to that post and remove the comment before it is approved.

The information stored in this cookie is for convenience and is not essential. Therefore, the user needs to be given the choice to opt in or opt out of the storage of this data.

For this reason, a checkbox has been added to the comment form that allows commenters to opt-in to storing this data in the cookie. This checkbox will be unchecked by default, as opt-in is an action the user must explicitly approve.

The new checkbox field is automatically added to comment forms displayed using the [comment\_form()](https://developer.wordpress.org/reference/functions/comment_form/) function inside a p.comment-form-cookies-consent element.

While most themes will not require any action, it is recommended that you double check that the input and label does not require CSS adjustments in custom themes.

## Bundled Themes

All 8 currently supported bundled themes (Twenty Ten-Twenty Seventeen) have been updated to support these changes. Site footers will display a link to the site’s privacy policy when one has been selected, and the commenter cookie opt-in field has been styled.

Child themes built on top of bundled themes should be checked to see if any adjustments are necessary for the privacy policy link in the footer.