# Widgets

A widget adds content and features to a widget area (also called a [sidebar](https://developer.wordpress.org/themes/functionality/sidebars/ "Sidebars")). Widget areas provide a way for users to customize their site. A widget area can appear on multiple pages or on only one page. Your theme might have just one widget area or many of them.

Some examples of ways you can use widget areas are:

*   Lay out a homepage using widgets. This allows site owners to decide what should appear in each section of their homepage.
*   Create a footer that users can customize with their own content.
*   Add a customizable sidebar to a blog.

A widget is a PHP object that outputs some HTML. The same kind of widget can be used multiple times on the same page (e.g. the Text Widget). Widgets can save data in the database (in the options table).

When you create a new kind of widget, it will appear in the user’s Administration Screens at **Appearance > Widgets**. The user can add the widget to a widget area and customize the widget settings from the WordPress admin.

## Built-in versus stand-alone widgets

A set of widgets is included with the default WordPress installation. In addition to these standard widgets, extra widgets can be included by themes or plugins. An advantage of widgets built into themes or plugins is to provide extra features and increase the number of widgets.

A disadvantage is that if a theme is changed or a plugin is deactivated, the plugin or theme widget’s functionality will be lost. However, the data and preferences from the widget will be saved to the options table and restored if the theme or plugin is reactivated.

If you include a widget with your theme, it can only be used if that theme is active. If the user decides to change their theme they will lose access to that widget. However, if the widget is included with a plugin, the user can change their theme without losing access to the widget functionality.

## Anatomy of a Widget

Visually, a widget comprises two areas:

1.  Title Area
2.  Widget Options

For example, here is the layout of the built-in text widget in the admin and on the front-end:

![Sample Editable Widget](https://make.wordpress.org/docs/files/2013/06/widget_visual.png)

A widget form in the admin area.

![A widget as it appars to a site visitor.](https://make.wordpress.org/docs/files/2013/06/Widget-front-end.png)

A widget as it appears to a site visitor.

HTML output for this widget looks like this:

<div id="text-7" class="widget widget\_text">
<!-- Widget Container -->
    <div class="widget-wrap">
        <h4 class="widgettitle">This is a text widget</h4>
        <!-- Title -->
        <div class="textwidget">
        <!-- Content of Widget -->
            I can put HTML in here. <a href="http://google.com/">Search me!</a>
        </div>
    </div>
</div>

Each widget has its own way of outputting HTML that is relevant to the data being displayed. The wrapper tags for the widget are defined by the widget area in which it is being displayed.

The PHP code necessary to create a widget like the built-in text widget looks like this:

<?php

class My\_Widget extends WP\_Widget {

	function \_\_construct() {

		parent::\_\_construct(
			'my-text',  // Base ID
			'My Text'   // Name
		);

		add\_action( 'widgets\_init', function() {
			register\_widget( 'My\_Widget' );
		});

	}

	public $args = array(
		'before\_title'  => '<h4 class="widgettitle">',
		'after\_title'   => '</h4>',
		'before\_widget' => '<div class="widget-wrap">',
		'after\_widget'  => '</div></div>'
	);

	public function widget( $args, $instance ) {

		echo $args\['before\_widget'\];

		if ( ! empty( $instance\['title'\] ) ) {
			echo $args\['before\_title'\] . apply\_filters( 'widget\_title', $instance\['title'\] ) . $args\['after\_title'\];
		}

		echo '<div class="textwidget">';

		echo esc\_html\_\_( $instance\['text'\], 'text\_domain' );

		echo '</div>';

		echo $args\['after\_widget'\];

	}

	public function form( $instance ) {

		$title = ! empty( $instance\['title'\] ) ? $instance\['title'\] : esc\_html\_\_( '', 'text\_domain' );
		$text = ! empty( $instance\['text'\] ) ? $instance\['text'\] : esc\_html\_\_( '', 'text\_domain' );
		?>
		<p>
		<label for="<?php echo esc\_attr( $this->get\_field\_id( 'title' ) ); ?>"><?php echo esc\_html\_\_( 'Title:', 'text\_domain' ); ?></label>
			<input class="widefat" id="<?php echo esc\_attr( $this->get\_field\_id( 'title' ) ); ?>" name="<?php echo esc\_attr( $this->get\_field\_name( 'title' ) ); ?>" type="text" value="<?php echo esc\_attr( $title ); ?>">
		</p>
		<p>
			<label for="<?php echo esc\_attr( $this->get\_field\_id( 'Text' ) ); ?>"><?php echo esc\_html\_\_( 'Text:', 'text\_domain' ); ?></label>
			<textarea class="widefat" id="<?php echo esc\_attr( $this->get\_field\_id( 'text' ) ); ?>" name="<?php echo esc\_attr( $this->get\_field\_name( 'text' ) ); ?>" type="text" cols="30" rows="10"><?php echo esc\_attr( $text ); ?></textarea>
		</p>
		<?php

	}

	public function update( $new\_instance, $old\_instance ) {

		$instance = array();

		$instance\['title'\] = ( !empty( $new\_instance\['title'\] ) ) ? strip\_tags( $new\_instance\['title'\] ) : '';
		$instance\['text'\] = ( !empty( $new\_instance\['text'\] ) ) ? $new\_instance\['text'\] : '';

		return $instance;
	}

}
$my\_widget = new My\_Widget();
?>

[Expand full source code](#)[Collapse full source code](#)

The code above will be explained in detail later in the article.

## Developing Widgets

To create and display a widget, you need to do the following:

1.  Create your widget’s class by extending the standard [WP\_Widget](https://developer.wordpress.org/reference/classes/wp_widget/) class and some of its functions.
2.  Register your widget so that it’s made available in the **Widgets** screen.
3.  Make sure that your theme has at least one [widget area](https://make.wordpress.org/docs/theme-developer-handbook/theme-functionality/sidebars/ "Sidebars") in which to add the widgets.

### Your Widget Class

The [WP\_Widget](https://developer.wordpress.org/reference/classes/wp_widget/) class is located in [wp-includes/class-wp-widget.php](https://core.trac.wordpress.org/browser/tags/4.8/src/wp-includes/class-wp-widget.php)

<?php

class My\_Widget extends WP\_Widget {

	public function \_\_construct() {
		// actual widget processes
	}

	public function widget( $args, $instance ) {
		// outputs the content of the widget
	}

	public function form( $instance ) {
		// outputs the options form in the admin
	}

	public function update( $new\_instance, $old\_instance ) {
		// processes widget options to be saved
	}
}

?>

[Expand full source code](#)[Collapse full source code](#)

The documentation for each of these functions can be found in the widget class code:

1.  `[construct](https://core.trac.wordpress.org/browser/tags/4.8/src/wp-includes/class-wp-widget.php#L175)`: Set up your widget with a description, name, and display width in your admin.
2.  `[widget](https://core.trac.wordpress.org/browser/tags/4.8/src/wp-includes/class-wp-widget.php#L122)`: Process the widget options and display the HTML on your page. The `$args` parameter provides the HTML you can use to display the widget title class and widget content class.
3.  `[form](https://core.trac.wordpress.org/browser/tags/4.8/src/wp-includes/class-wp-widget.php#L154)`: Display the form that will be used to set the options for your widget. If your widget doesn’t have any options, you can skip this function (although it is still best practice to include it even if it’s empty).
4.  `[update](https://core.trac.wordpress.org/browser/tags/4.8/src/wp-includes/class-wp-widget.php#L141)`: Save the widget options to the database. If your widget doesn’t have any options, you can skip this function (although it is still best practice to include it even if it’s empty).

### Registering a Widget

The [register\_widget()](https://developer.wordpress.org/reference/functions/register_widget/) function is used to register a widget.

Call this function using the widgets\_init hook:

<?php
add\_action( 'widgets\_init', 'wpdocs\_register\_widgets' );

function wpdocs\_register\_widgets() {
	register\_widget( 'My\_Widget' );
}
?>

The HTML that wraps the widget, as well as the class for the title and widget content, is specified at the time you register the widget area using [register\_sidebar()](https://developer.wordpress.org/reference/functions/register_sidebar/).

## Examples

### Example Text Widget

To build the text widget from the example at the beginning of this article. You will start by setting up a widget class that extends the [WP\_Widget](https://developer.wordpress.org/reference/classes/wp_widget/) class.

In the class constructor you will call the parent constructor and pass it your widget’s base ID and name. Also in the class constructor you will hook into the `[widgets_init](https://developer.wordpress.org/reference/hooks/widgets_init/)` action to register your widget.

Next you will declare the arguments you will use when creating your widget. There are four arguments you must define, `before_title`, `after_title`, `before_widget`, and `after_widget`. These arguments will define the code that wraps your widgets title and the widget itself.

After defining your arguments, you will define the widgets function. This function takes two parameters, the `$args` array from before, and the `$instance` of the widget, and is the function that will process options from the form and display the HTML for the widget on the front-end of your site. In the example above the widget function simply outputs the widget title, while passing it through the `[widget_title](https://developer.wordpress.org/reference/hooks/widget_title/)` filter. It then out puts a simple widget wrapper and the content of the widget’s text field. As outlined in the example, you can access the options from the widget that are stored in the `$instance`.

Next you will define the form function. This function takes one parameter, `$instance`, and outputs the form that the user uses to create the widget in the Widgets admin screen. In the example above, the function starts by defining the `$title` and `$text` variables and setting them to the previously entered values, if those values exist. Then it outputs a simple form with a text field for the title and a textarea for the text content.

Lastly you will define the update function. This function takes two parameters, `$new_instance` and `$old_instance`, and is responsible for updating your widgets with new options when they are submitted. Here you simply define `$instance` as an empty array. You then set the title and text keys to the `$new_instance` values if they exist. You then return `$instance`.

Finally, when all of the above is defined, you instantiate your new widget class and test your work.

### Sample Widget

<?php

/\*\*
 \* Adds Foo\_Widget widget.
 \*/
class Foo\_Widget extends WP\_Widget {

	/\*\*
	 \* Register widget with WordPress.
	 \*/
	public function \_\_construct() {
		parent::\_\_construct(
			'foo\_widget', // Base ID
			'Foo\_Widget', // Name
			array( 'description' => \_\_( 'A Foo Widget', 'text\_domain' ), ) // Args
        );
    }

	/\*\*
	 \* Front-end display of widget.
	 \*
	 \* @see WP\_Widget::widget()
	 \*
	 \* @param array $args     Widget arguments.
	 \* @param array $instance Saved values from database.
	 \*/
	public function widget( $args, $instance ) {
		extract( $args );
		$title = apply\_filters( 'widget\_title', $instance\['title'\] );

		echo $before\_widget;
		if ( ! empty( $title ) ) {
			echo $before\_title . $title . $after\_title;
		}
		echo \_\_( 'Hello, World!', 'text\_domain' );
		echo $after\_widget;
	}

	/\*\*
	 \* Back-end widget form.
	 \*
	 \* @see WP\_Widget::form()
	 \*
	 \* @param array $instance Previously saved values from database.
	 \*/
	public function form( $instance ) {
		if ( isset( $instance\[ 'title' \] ) ) {
			$title = $instance\[ 'title' \];
		}
		else {
			$title = \_\_( 'New title', 'text\_domain' );
		}
		?>
		<p>
		    <label for="<?php echo $this->get\_field\_name( 'title' ); ?>"><?php \_e( 'Title:' ); ?></label>
            <input class="widefat" id="<?php echo $this->get\_field\_id( 'title' ); ?>" name="<?php echo $this->get\_field\_name( 'title' ); ?>" type="text" value="<?php echo esc\_attr( $title ); ?>" />
         </p>
    <?php
    }

	/\*\*
	 \* Sanitize widget form values as they are saved.
	 \*
	 \* @see WP\_Widget::update()
	 \*
	 \* @param array $new\_instance Values just sent to be saved.
	 \* @param array $old\_instance Previously saved values from database.
	 \*
	 \* @return array Updated safe values to be saved.
	 \*/
	public function update( $new\_instance, $old\_instance ) {
		$instance = array();
		$instance\['title'\] = ( !empty( $new\_instance\['title'\] ) ) ? strip\_tags( $new\_instance\['title'\] ) : '';

		return $instance;
	}

} // class Foo\_Widget

?>

[Expand full source code](#)[Collapse full source code](#)

This sample widget can then be registered in the widgets\_init hook:

<?php
// Register Foo\_Widget widget
add\_action( 'widgets\_init', 'register\_foo' );
    
function register\_foo() { 
    register\_widget( 'Foo\_Widget' ); 
}
?>

### Example with a Namespace

If you use PHP 5.3 with namespaces you should call the constructor directly as in the following example:

<?php
namespace a\\b\\c;

class My\_Widget\_Class extends \\WP\_Widget {
	function \_\_construct() {
		parent::\_\_construct( 'baseID', 'name' );
	}
	// ... rest of the functions
}
?>

and call the register widget with:

<?php
// Register Foo\_Widget widget
add\_action( 'widgets\_init', 'register\_my\_widget' );

function register\_my\_widget() {
    register\_widget( 'a\\b\\c\\My\_Widget\_Class' );
}
?>

See [this answer at stack exchange](http://stackoverflow.com/questions/5247302/php-namespace-5-3-and-wordpress-widget/5247436#5247436) for more detail.

## Special considerations

If you want to use a widget inside another template file, rather than in a sidebar, you can use `[the_widget()](https://developer.wordpress.org/reference/functions/the_widget/)` to display it programmatically. The function accepts widget class names. You pass the widget class name to the function like this:

<?php the\_title(); ?>

<div class="content">
    <?php the\_content(); ?>
</div>

<div class="widget-section">
    <?php the\_widget( 'My\_Widget\_Class' ); ?>
</div>

You may want to use this approach if you need to use a widget in a specific area on a page, such as displaying a list of events next to a form in a section on the front page of your site or displaying an email capture form on a mega-menu alongside your navigation.