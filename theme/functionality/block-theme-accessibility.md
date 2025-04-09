# Block theme accessibility

Block themes support accessibility and simplify the process for adding accessibility.

## Landmark

Group, Template part, and Query blocks can become a landmark. There are two ways to create landmark.

**Using block markup**  
`”tagName":"header”` creates header landmark.

```
<!-- wp:group {"tagName":"header","layout":{"type":"constrained"}} -->
<header class="wp-block-group"><!-- wp:site-title /--></header>
<!-- /wp:group -->
```

**Using site editor**  
HTML element under Advanced section in the Block panel provides the following landmark options.  

HTML element under Advanced section in the Block panel provides the following landmark options.  
`<header>` `<main>` `<section>` `<article>` `<aside>` `<footer>`.

## Skip to content

By selecting `<main>` landmark on Group, Template part, or Query block generates the Skip to Content link. Learn more about the [skip to content link here](https://make.wordpress.org/themes/handbook/review/required/#3-accessibility).

```
<!-- wp:group {"tagName":"main","layout":{"type":"constrained"}} -->
<main class="wp-block-group"><!-- wp:heading -->
<h2 id="hello-world">Hello World</h2>
<p>Welcome to WordPress. This is your first post. </p>
<!-- /wp:heading -->
```

## Accessible navigation menu

Navigation block enables the following accessibility without additional code.

*   Support responsive view
*   Support keyboard navigation
*   Insert `<nav>` landmark role
*   Insert ARIA attributes `aria-label` `aria-hidden`

## Additional resources

*   [Accessibility](https://make.wordpress.org/themes/handbook/review/accessibility/)

Changelog:

*   **Updated** 2023-03-08 Updated code examples to reflect WordPress 6.1 block markup.
*   **Created** 2022-01-25