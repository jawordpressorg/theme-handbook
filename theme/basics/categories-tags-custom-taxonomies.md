# Categories, Tags, &amp; Custom Taxonomies

Categories, tags, and taxonomies are all related and can be easily confused.  

We’ll use the example of building a theme for a recipe website to help break down categories, tags, and taxonomies. 

In our recipe website, the **categories** would be Breakfast, Lunch, Dinner, Appetizers, Soups, Salads, Sides, and Desserts. All recipes will fit within those categories, but users might want to search for something specific like chocolate desserts or ginger chicken dinners.  

Chocolate, ginger, and chicken are all examples of **tags**.  They are another level of specificity that provides meaning to the user.

Lastly, there are taxonomies. In reality, categories and tags are examples of default taxonomies which simply are a way to organize content.  Taxonomies are the method of classifying content and data in WordPress. When you use a taxonomy you’re grouping similar things together. The taxonomy refers to the sum of those groups. As with Post Types, there are a number of default taxonomies, and you can also create your own.

Recipes are normally organized by category and tag, but there are some other helpful ways to break the recipes down to be more user friendly.  For example, the recipe website might want an easy way to display recipes by cook time. A custom taxonomy of cook time with 0-30 min, 30-min to an hour, 1 to 2 hours, 2+ hours would be a great breakdown.  Additionally, cook method such as grill, oven, stove, refrigerator, etc would be another example of a custom taxonomy that would be relevant for the site.  There could also be a custom taxonomy for how spicy the recipe is and then a rating from 1-5 on spiciness.

## Default Taxonomies

The default taxonomies in WordPress are:

*   categories: a hierarchical taxonomy that organizes content in the *post* Post Type
*   tags: a non-hierarchical taxonomy that organizes content in the *post* Post Type
*   post formats: a method for creating formats for your posts. You can learn more about these on the [Post Formats](https://developer.wordpress.org/themes/functionality/post-formats/ "Post Formats") page.

### Terms

Terms are items within your taxonomy. So, for example, if you have the *Animal* taxonomy you would have the terms, dogs, cats, and sheep. Terms can be created via the WordPress admin, or you can use the [wp\_insert\_term()](https://developer.wordpress.org/reference/functions/wp_insert_term/ "wp_insert_term") function.

## Database Schema

Taxonomies and terms are stored in the following database tables:

*   wp\_terms – stores all of the terms
*   wp\_term\_taxonomy – places the term in a taxonomy
*   wp\_term\_relationships – relates the taxonomy to an object (for example, *category* to *post)*

[![taxonomy-schema](https://i0.wp.com/developer.wordpress.org/files/2014/10/taxonomy-schema.png?resize=311%2C452&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2014/10/taxonomy-schema.png?ssl=1)

## Templates

WordPress offers several different hierarchies of templates for categories, tags, or custom taxonomies. More details on their structure and usage may be found on the [Taxonomy Templates](https://developer.wordpress.org/themes/functionality/taxonomy-templates/ "Taxonomy Templates") page.

## Custom Taxonomies

It is possible to create new taxonomies in WordPress. You may, for example, want to create an *author* taxonomy on a book review website, or an *actor* taxonomy on a film site. As with custom post type **it is recommended that you put this functionality in a plugin**. This ensures that when the user changes their website’s design, their content is preserved in the plugin.

You can read more about creating custom taxonomies in the [Plugin Developer Handbook.](https://developer.wordpress.org/plugins/taxonomy/working-with-custom-taxonomies/ "Working with Custom Taxonomies")