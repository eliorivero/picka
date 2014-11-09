Picka
=====

Font Icon Picker plugin for jQuery

A lightweight font icon picker simple and straightforward. Created specially for WordPress admin environments but can be used anywhere.

Demo http://demo.queryloop.com/picka/

The demo uses icons from FontAwesome
http://fontawesome.io/icons/

and Genericons
http://genericons.com/

but can be extended to support any icon set.

Usage
---

```html
<div class="icon-picker" data-pickerid="unique_id">
    <input type="hidden" value="" name="unique_id"/>
</div>
```

```js
$('.icon-picker').qlIconPicker({
		'mode'       : 'dialog',// show overlay 'dialog' panel or slide down 'inline' panel
		'closeOnPick': true,    // whether to close panel after picking or 'no'
		'save'       : 'class', // save icon 'class' or 'code'
		'size'       : '',      // class to be added to icon panel, 'large' is supported.
		'classes'    : {               // extra classes:
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
```

You can also specify the icon sets and labels for launcher buttons as JSON object in a HTML data attribute:

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
