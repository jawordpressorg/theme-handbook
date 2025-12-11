<!-- 
# Categories, Tags, &amp; Custom Taxonomies
 -->

# カテゴリー、タグ、カスタム・タクソノミー

<!-- 
Categories, tags, and taxonomies are all related and can be easily confused.  
 -->

カテゴリー、タグ、タクソノミーは、すべて関連しており、混同されがちです。 

<!-- 
We’ll use the example of building a theme for a recipe website to help break down categories, tags, and taxonomies. 
 -->

レシピ・サイトのテーマ構築を例に、カテゴリー、タグ、タクソノミーを分解して説明します。

<!-- 
In our recipe website, the **categories** would be Breakfast, Lunch, Dinner, Appetizers, Soups, Salads, Sides, and Desserts. All recipes will fit within those categories, but users might want to search for something specific like chocolate desserts or ginger chicken dinners.  
 -->

当レシピ・サイトでは、**カテゴリー** として朝食、昼食、夕食、前菜、スープ、サラダ、副菜、デザートを設定します。すべてのレシピはこれらのカテゴリーに分類されますが、ユーザーはチョコレート・デザートや生姜チキン・ディナーなど、特定の料理を検索したい場合があります。

<!-- 
Chocolate, ginger, and chicken are all examples of **tags**.  They are another level of specificity that provides meaning to the user.
 -->

チョコレート、生姜、鶏肉はすべて **タグ** の例です。これらはユーザーに意味を提供する、もう一段階の詳細な分類です。

<!-- 
Lastly, there are taxonomies. In reality, categories and tags are examples of default taxonomies which simply are a way to organize content.  Taxonomies are the method of classifying content and data in WordPress. When you use a taxonomy you’re grouping similar things together. The taxonomy refers to the sum of those groups. As with Post Types, there are a number of default taxonomies, and you can also create your own.
 -->

最後に、タクソノミーがあります。実際には、カテゴリーとタグはデフォルト・タクソノミーの一例であり、単にコンテンツを整理する方法に過ぎません。タクソノミーとは、WordPress においてコンテンツやデータを分類する方法です。タクソノミーを使用すると、類似したものをまとめてグループ化できます。タクソノミーとは、それらのグループの総体を指します。投稿タイプと同様に、デフォルト・タクソノミーがいくつか用意されており、独自のものも作成できます。

<!-- 
Recipes are normally organized by category and tag, but there are some other helpful ways to break the recipes down to be more user friendly.  For example, the recipe website might want an easy way to display recipes by cook time. A custom taxonomy of cook time with 0-30 min, 30-min to an hour, 1 to 2 hours, 2+ hours would be a great breakdown.  Additionally, cook method such as grill, oven, stove, refrigerator, etc would be another example of a custom taxonomy that would be relevant for the site.  There could also be a custom taxonomy for how spicy the recipe is and then a rating from 1-5 on spiciness.
 -->

レシピは通常、カテゴリーとタグで整理されますが、ユーザーフレンドリーにするために、レシピを分類する他の便利な方法もあります。たとえば、レシピ・サイトでは、調理時間別にレシピを表示する、簡単な方法が必要かもしれません。調理時間のカスタム・タクソノミーとして、0～30分、30分～1時間、1～2時間、2時間以上といった区分が有用です。さらに、グリル、オーブン、コンロ、冷蔵庫など調理方法のカスタム・タクソノミーも、サイトに適切な例となります。レシピの辛さレベルを示すカスタム・タクソノミーを設け、辛さを1～5段階で評価する方式も考えられます。

<!-- 
## Default Taxonomies
 -->

## デフォルト・タクソノミー

<!-- 
The default taxonomies in WordPress are:
 -->

WordPress のデフォルト・タクソノミーは、次のとおりです:

<!-- 
*   categories: a hierarchical taxonomy that organizes content in the *post* Post Type
*   tags: a non-hierarchical taxonomy that organizes content in the *post* Post Type
*   post formats: a method for creating formats for your posts. You can learn more about these on the [Post Formats](https://developer.wordpress.org/themes/functionality/post-formats/ "Post Formats") page.
 -->

*   カテゴリー: *post* 投稿タイプ内のコンテンツを整理する、階層型タクソノミーです。
*   タグ: *post* 投稿タイプ内のコンテンツを整理する、非階層型タクソノミーです。
*   投稿フォーマット: あなたの投稿用にフォーマットを作成する方法です。これらについて詳しくは [投稿フォーマット](https://developer.wordpress.org/themes/functionality/post-formats/ "Post Formats") ページをご覧ください。

<!-- 
### Terms
 -->

### ターム

<!-- 
Terms are items within your taxonomy. So, for example, if you have the *Animal* taxonomy you would have the terms, dogs, cats, and sheep. Terms can be created via the WordPress admin, or you can use the [wp\_insert\_term()](https://developer.wordpress.org/reference/functions/wp_insert_term/ "wp_insert_term") function.
 -->

タームとは、あなたのタクソノミー内の項目です。たとえば、*動物* というタクソノミーを定義した場合、そのタームとして犬、猫、羊などが存在します。タームは WordPress 管理画面から作成できるし、[wp\_insert\_term()](https://developer.wordpress.org/reference/functions/wp_insert_term/ "wp_insert_term") 関数も使用できます。

<!-- 
## Database Schema
 -->

## データベース・スキーマ

<!-- 
Taxonomies and terms are stored in the following database tables:
 -->

タクソノミーとタームは、以下のデータベース・テーブルに保存されます:

<!-- 
*   wp\_terms – stores all of the terms
*   wp\_term\_taxonomy – places the term in a taxonomy
*   wp\_term\_relationships – relates the taxonomy to an object (for example, *category* to *post)*
 -->

*   wp\_terms – すべてのタームを格納します。
*   wp\_term\_taxonomy – タームをタクソノミーに配置します。
*   wp\_term\_relationships – タクソノミーをオブジェクトに関連付けます (たとえば、*category* を *post* に関連付ける)

<!-- 
[![taxonomy-schema](https://i0.wp.com/developer.wordpress.org/files/2014/10/taxonomy-schema.png?resize=311%2C452&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2014/10/taxonomy-schema.png?ssl=1)
 -->

[![タクソノミー・スキーマ](https://i0.wp.com/developer.wordpress.org/files/2014/10/taxonomy-schema.png?resize=311%2C452&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2014/10/taxonomy-schema.png?ssl=1)

<!-- 
## Templates
 -->

## テンプレート

<!-- 
WordPress offers several different hierarchies of templates for categories, tags, or custom taxonomies. More details on their structure and usage may be found on the [Taxonomy Templates](https://developer.wordpress.org/themes/functionality/taxonomy-templates/ "Taxonomy Templates") page.
 -->

WordPress は、カテゴリー、タグ、またはカスタム・タクソノミー向けに、いくつかの異なる階層構造のテンプレートを提供しています。その構造と使用方法の詳細については、[タクソノミー・テンプレート](https://developer.wordpress.org/themes/functionality/taxonomy-templates/ "Taxonomy Templates") ページをご覧ください。

<!-- 
## Custom Taxonomies
 -->

## カスタム・タクソノミー

<!-- 
It is possible to create new taxonomies in WordPress. You may, for example, want to create an *author* taxonomy on a book review website, or an *actor* taxonomy on a film site. As with custom post type **it is recommended that you put this functionality in a plugin**. This ensures that when the user changes their website’s design, their content is preserved in the plugin.
 -->

WordPress では、新規タクソノミーを作成できます。たとえば、書籍レビュー・サイトでは *著者* タクソノミーを、映画サイトでは *俳優* タクソノミーを、作成したい場合があるでしょう。カスタム投稿タイプと同様に、**この機能は、プラグインに実装することを推奨します**。これにより、ユーザーが Web サイトのデザインを変更しても、コンテンツはプラグイン内に保持されます。

<!-- 
You can read more about creating custom taxonomies in the [Plugin Developer Handbook.](https://developer.wordpress.org/plugins/taxonomy/working-with-custom-taxonomies/ "Working with Custom Taxonomies")
 -->

カスタム・タクソノミーの作成については、[プラグイン開発者ハンドブック](https://developer.wordpress.org/plugins/taxonomy/working-with-custom-taxonomies/ "Working with Custom Taxonomies") で詳しく説明されています。