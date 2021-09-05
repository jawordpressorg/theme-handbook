# Data Validation

Data validation is the process of analyzing the data against a predefined pattern (or patterns) with a definitive result: valid or invalid.

Usually this applies to data coming from external sources such as user input and calls to web services via API.

Simple examples of data validation:

*   Check that required fields have not been left blank
*   Check that an entered phone number only contains numbers and punctuation
*   Check that an entered postal code is a valid postal code
*   Check that a quantity field is greater than 0

**Data validation should be performed as early as possible.** That means validating the data before performing any actions.

Note:  
Validation can be performed by using JavaScript on the front end and by using PHP on the back end.

## Validating the Data

There are at least three ways: built-in PHP functions, core WordPress functions, and custom functions you write.

### Built-in PHP functions

Basic validation is doable using many built-in PHP functions, including these:

*   `[isset()](//secure.php.net/isset)` and `[empty()](//secure.php.net/empty)` for checking whether a variable exists and isn’t blank
*   `[mb_strlen()](//secure.php.net/mb_strlen)` or `[strlen()](//secure.php.net/strlen)` for checking that a string has the expected number of characters
*   `[preg_match()](//secure.php.net/preg_match)`, `[strpos()](//secure.php.net/strpos)` for checking for occurrences of certain strings in other strings
*   `[count()](//secure.php.net/count)` for checking how many items are in an array
*   `[in_array()](//secure.php.net/in_array)` for checking whether something exists in an array

### Core WordPress functions

WordPress provides many useful functions that help validate different kinds of data. Here are several examples:

*   `[is_email()](/reference/functions/is_email/)` will validate whether an email address is valid.
*   `[term_exists()](/reference/functions/term_exists/)` checks whether a tag, category, or other taxonomy term exists.
*   `[username_exists()](/reference/functions/username_exists/)` checks if username exists.
*   `[validate_file()](/reference/functions/validate_file/)` will validate that an entered file path is a real path (but not whether the file exists).

Check the the list of [conditional tags](https://developer.wordpress.org/themes/references/list-of-conditional-tags/) for more functions like these.  
Search for functions with names like these: `*_exists()`, `*_validate()`, and `is_*()`. Not all of these are validation functions, but many are helpful.

### Custom PHP and JavaScript functions

You can write your own PHP and JavaScript functions and include them in your plugin. When writing a validation function, you’ll want to name it like a question (examples: is\_phone, is\_available, is\_us\_zipcode).

The function should return a boolean, either true or false, depending on whether the data is valid or not. This will allow using the function as a condition.

## Example 1

Let’s say you have an U.S. zip code input field that a user submits.

<input id="wporg\_zip\_code" type="text" maxlength="10" name="wporg\_zip\_code">

The text field allows up to 10 characters of input with no limitations on the types of characters that can be used. Users could enter something valid like `1234567890` or something invalid (and evil) like `eval()`.

The `maxlength` attribute on our `input` field is only enforced by the browser, so you still need to validate the length of the input on the server. If you don’t, an attacker could alter the maxlength value.

By using validation we can ensure we’re accepting only valid zip codes.

First you need to write a function to validate a U.S. zip codes:

<?php function is\_us\_zip\_code($zip\_code) { // scenario 1: empty if (empty($zip\_code)) { return false; } // scenario 2: more than 10 characters if (strlen(trim($zip\_code)) > 10) {
        return false;
    }

    // scenario 3: incorrect format
    if (!preg\_match('/^\\d{5}(\\-?\\d{4})?$/', $zip\_code)) {
        return false;
    }

    // passed successfully
    return true;
}

When processing the form, your code should check the `wporg_zip_code` field and perform the action based on the result:

if ( isset( $\_POST\['wporg\_zip\_code'\] ) && is\_us\_zip\_code( $\_POST\['wporg\_zip\_code'\] ) ) {
    // your action
}

## Example 2

Say you’re going to query the database for some posts, and you want to give the user the ability to sort the query results.

This example code checks an incoming sort key (stored in the “orderby” input parameter) for validity by comparing it against an array of allowed sort keys using the built-in PHP function [`in_array`](//secure.php.net/in_array). This prevents the user from passing in malicious data and potentially compromising the website.

Before checking the incoming sort key against the array, the key is passed into the built-in WordPress function [`sanitize_key`](https://codex.wordpress.org/Function_Reference/sanitize_key). This function ensures, among other things, that the key is in lowercase ([`in_array`](//secure.php.net/in_array) performs a *case-sensitive* search).

Passing “true” into the third parameter of [`in_array`](//php.net/in_array) enables strict type checking, which tells the function to not only compare values but value *[types](http://php.net/manual/en/language.types.php)* as well. This allows the code to be certain that the incoming sort key is a string and not some other data type.

<?php
$allowed\_keys = \['author', 'post\_author', 'date', 'post\_date'\];

$orderby = sanitize\_key( $\_POST\['orderby'\] );

if ( in\_array( $orderby, $allowed\_keys, true ) ) {
    // modify the query to sort by the orderby key
}