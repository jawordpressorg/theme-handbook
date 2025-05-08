# JavaScript Best Practices

Many themes use JavaScript to provide interactivity, animation or other enhancements. These best practices will help ensure your code works efficiently and does not cause conflicts with your content or plugins.

## Use Included Libraries

There are many useful JavaScript libraries you may want to include when building your theme. Did you know that WordPress comes bundled with dozens of popular libraries? Check out this [list of default scripts included with WordPress](https://developer.wordpress.org/themes/basics/including-css-javascript/#default-scripts-included-and-registered-by-wordpress).

A common mistake made by beginning theme and plugin developers is to bundle their theme or plugin with their own version of the library. This may conflict with other plugins that enqueue the version bundled with WordPress. As a best practice, make your theme compatible with the version of your favorite library included with WordPress.

Do not try to use your own version of a JavaScript library that is already [bundled](https://developer.wordpress.org/themes/basics/including-css-javascript/#default-scripts-included-and-registered-by-wordpress "Default Scripts Included with WordPress") with WordPress. Doing so may break core functionality and conflict with plugins.

If you feel you MUST replace the WordPress version with one of your own… well… the answer is still: don’t do it.  The versions of JavaScript libraries used by WordPress may include custom tweaks that WordPress needs to operate.  Any time you override these libraries, you risk breaking your WordPress instance. Moreover, plugins created by other authors should be written to be compatible with WordPress’s version of these libraries as well. Adding your own version may (and often does!) conflict with plugins.

## Standard JavaScript

Javascript is growing in popularity for web developers, and it’s being used to accomplish for a variety of tasks. Here are some best practices to use when writing your JavaScript

*   Avoid Global Variables
*   Keep your JavaScript unobtrusive
*   Use closures and the [module pattern](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
*   Stick to a coding style. Use The [WordPress Javascript Coding Standard](https://make.wordpress.org/core/handbook/coding-standards/javascript/).
*   Validate and Lint Your Code – [E](http://JSLint.com)[S](http://JSLint.com)[Lint.com](https://eslint.org/)
*   Ensure your site still works without JavaScript first – then add JavaScript to provide additional capabilities. This is a form of [Progressive Enhancement](http://en.wikipedia.org/wiki/Progressive_enhancement).
*   Lazy load assets that aren’t immediately required.
*   Don’t use jQuery *if you don’t need to* — There’s a great site that shows you how to do some common tasks with plain old JavaScript – [you might not need jQuery](http://youmightnotneedjquery.com)

## jQuery

### Including jQuery in your theme

[jQuery](http://www.jquery.com) is a popular JavaScript library to make working with JavaScript easier and more reliable across browsers. If you use jQuery, be sure to [follow the handbook guidelines on including JavaScript](https://developer.wordpress.org/themes/basics/including-css-javascript/). Giving your theme’s enqueued .js files a dependency array of `array( 'jquery' )` ensures that the jQuery script has been downloaded and loaded before your theme’s code.

#### Using $

Because the copy of jQuery included in WordPress loads in `[noConflict()](https://api.jquery.com/jQuery.noConflict/)` mode, use this wrapper code in your theme’s .js files to map “$” to “jQuery”:

```javascript
( function( $ ) {
// Your code goes here
} )( jQuery );
```

This wrapper (called an Immediately Invoked Function Expression, or IIFE) lets you pass in a variable—jQuery—on the bottom line, and give it the name “$” internally. Within this wrapper you may use `$` to select elements as normal.

### Selectors

Every time you select an element with jQuery, it performs a query through your document’s markup. These queries are very fast, but they do take time—you can make your site respond faster by re-using your jQuery objects instead of using a new query. So instead of repeating selectors:

```javascript
// Anti-pattern
$('.post img').addClass('theme-image');
$('.post img').on('click', function() { ... });
```

it is recommended to **cache your selectors** so you can re-use the returned element without having to repeat the lookup process:

```javascript
var $postImage = $('.post img');
// All image tags within posts can now be accessed through $postImage
$postImage.addClass('theme-image');
$postImage.on('click', function() { ... });
```

### Event Handling

When you use jQuery methods like `.bind` or `.click`, jQuery creates a new browser event object to handle processing the requested event. Each new event created takes a small amount of memory, but the amount of memory required goes up the more events you bind. If you have a page with a hundred anchor tags and wanted to fire a \`logClick\` event handler whenever a user clicked a link, it is very easy to write code like this:

```javascript
// Anti-pattern
$('a').click( logClick );
```

This works, but under the hood you have asked jQuery to create a new event handler for every link on your page.

**Event delegation** is a way to accomplish the same effect with less overhead. Because events in jQuery “bubble”—that is, a click event will fire on a link, then on the link’s surrounding `<p>` tag, then on the `div` container, and so on up to the `document` object itself—we can put a single event handler higher up in the page structure, and still catch the click events for all of those links:

```javascript
// Bind one handler at the document level, which is triggered
// whenever there is a "click" event originating from an "a" tag
$(document).on('click', 'a', logClick);
```