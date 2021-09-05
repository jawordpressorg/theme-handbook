# Test

<br />
&lt;?php add\_action( 'rest\_api\_init', function() { register\_rest\_field( 'comment', 'karma', array( 'get\_callback' => function( $comment\_arr ) {<br />
            $comment\_obj = get\_comment( $comment\_arr\['id'\] );<br />
            return (int) $comment\_obj->comment\_karma;<br />
        },<br />
        'update\_callback' => function( $karma, $comment\_obj ) {<br />
            $ret = wp\_update\_comment( array(<br />
                'comment\_ID'    => $comment\_obj->comment\_ID,<br />
                'comment\_karma' => $karma<br />
            ) );<br />
            if ( false === $ret ) {<br />
                return new WP\_Error( 'rest\_comment\_karma\_failed', \_\_( 'Failed to update comment karma.' ), array( 'status' => 500 ) );<br />
            }<br />
            return true;<br />
        },<br />
        'schema' => array(<br />
            'description' => \_\_( 'Comment karma.' ),<br />
            'type'        => 'integer'<br />
        ),<br />
    ) );<br />
} );<br />

[Expand full source code](#)[Collapse full source code](#)