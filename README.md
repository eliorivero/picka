Picka
=====

Font Icon Picker plugin for jQuery

A lightweight font icon picker simple and straightforward. Created specially for WordPress admin environments but can be used anywhere.

Demo http://demo.queryloop.com/picka/

The demo uses icons from FontAwesome http://fontawesome.io/icons/ and Genericons http://genericons.com/ but can be extended to support any icon set.

Usage
---

*HTML*

```html
<!-- A wrapper for the icon picker launcher buttons, preview and field -->
<div class="icon-picker" data-pickerid="unique_id">
	<!-- A field to save the selected icon. -->
	<input type="hidden" value="" name="unique_id"/>
</div>

<div class="genericon-set icon-set">
	<ul>
		<!-- data code and class used when saving the icon -->
		<li data-code="f100" data-class="genericon genericon-standard" class="genericon genericon-standard"></li>
		<li data-code="f101" data-class="genericon genericon-aside" class="genericon genericon-aside"></li>
		<li data-code="f102" data-class="genericon genericon-image" class="genericon genericon-image"></li>
		
		<!-- ..the rest of the icon set using a similar markup... -->
	</ul>
</div>

<div class="fa-set icon-set">
	<ul>
		<li data-code="f042" data-class="fa fa-adjust" class="fa fa-adjust"></li>
		<li data-code="f170" data-class="fa fa-adn" class="fa fa-adn"></li>
		<li data-code="f037" data-class="fa fa-align-center" class="fa fa-align-center"></li>
		
		<!-- ..the rest of the icon set using a similar markup... -->
	</ul>
</div>
```

*JavaScript*
```js

jQuery(document).ready(function($){

	$('.icon-picker').qlIconPicker({
		'mode'       : 'dialog',// show overlay 'dialog' panel or slide down 'inline' panel
		'closeOnPick': true,    // whether to close panel after picking or 'no'
		'save'       : 'class', // save icon 'class' or 'code' in the input field
		'size'       : '',      // class to be added to icon panel, 'large' is supported.
		'classes'    : {        // extra classes:
			'launcher' : '',             // for launcher buttons. In WP Admin, use 'button'.
			'clear'    : 'remove-times', // for button that removes preview and clears field. In WP Admin, use 'dashicons dashicons-no-alt'.
			'highlight': '',             // when highlighting an icon. In WP Admin, use 'wp-ui-highlight'.
			'close'    : ''              // for close button. In WP Admin, use 'wp-ui-highlight'.
		},
		'iconSets' : {               // used to specify which launchers will be created
			'genericon' : 'Genericon', // create a launcher to pick genericon icons
			'fa' : 'FontAwesome'       // create a launcher to pick fontawesome icons
		}
	});
	
});
```

You can also specify the icon sets to use and the launcher buttons to create as JSON object in a HTML data attribute:

```html
<div class="icon-picker" data-pickerid="gi" data-iconsets='{"genericon":"Pick Genericon"}'>
	<input type="hidden" value="" name="unique_id"/>
</div>
```

this is useful for WordPress translation

```php
$picker = '<div class="icon-picker" data-pickerid="' . esc_attr( $field['id'] ) . '" data-iconsets=\'' . esc_attr('{"genericon":"' . __( 'Pick Genericon', 'yourtextdomain' ) . '"}') . '\'>';

	$picker  .= '<input type="hidden" value="' . $value . '" name="' . esc_attr( $field['id'] ) . '" />';

$picker .= '</div>';
```

but you can also use wp_localize_script() and pass the labels in an object when calling the plugin in JavaScript.

For more initialization and usage examples see the demo link.
