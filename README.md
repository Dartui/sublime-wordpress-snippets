# Wordpress Snippets for Sublime Text 3
Simple snippets for Wordpress elements, such as meta boxes, pages, subpages, post types, taxonomies, etc...
##wp_create_plugin
Snippet for creating wrapper for plugins
```
/* Plugin Name: New plugin
 * Description: Description
 * Version: 1.0
 * Author: Me
 */

if (!class_exists('MyPluginClass')) {
	class MyPluginClass {
		public function __construct() {
			
		}
	}

	new MyPluginClass();
}
```
##wp_add_menu_page
Snippet for creating menu
```
// Put this into your __construct function
add_action('admin_menu', array($this, 'add_menu_slug_menu_page'));

public function add_menu_slug_menu_page() {
	add_menu_page('Page title', 'Menu title', 'manage_options', 'menu_slug', array($this, 'menu_slug_menu_callback'), 'dashicons-icon', 0);
}

public function menu_slug_menu_callback() {
	// Content goes here
	
}
```
##wp_add_submenu_page
Snippet for creating submenu
```
// Put this into your __construct function
add_action('admin_menu', array($this, 'add_submenu_slug_submenu_page'));

public function add_submenu_slug_submenu_page() {
	add_submenu_page('parent_slug', 'Page title', 'Menu title', 'manage_options', 'submenu_slug', array($this, 'submenu_slug_menu_callback'));
}

public function submenu_slug_submenu_callback() {
	// Content goes here
	
}
```
##wp_add_menu_with_submenu
Snippet for creating menu with one submenu
```
// Put this into your __construct function
add_action('admin_menu', array($this, 'add_menu_slug_menu_with_submenu_page'));

public function add_menu_slug_menu_with_submenu_page() {
	add_menu_page('Page title', 'Menu title', 'manage_options', 'menu_slug', array($this, 'menu_slug_menu_callback'), 'dashicons-icon', 0);
	add_submenu_page('menu_slug', 'Page title', 'Menu title', 'manage_options', 'menu_slug', array($this, 'menu_slug_menu_callback'));
	add_submenu_page('menu_slug', 'Page title', 'Submenu title', 'manage_options', 'submenu_slug', array($this, 'menu_slug_submenu_callback'));
}

public function menu_slug_menu_callback() {
	// Menu content goes here
	
}

public function menu_slug_submenu_callback() {
	// Submenu content goes here
}
```
##wp_add_meta_box
Snippet for creating metabox with callback and save function
```
// Put this into your __construct function
add_action('add_meta_boxes', array($this, 'add_mymetaboxname_metabox'));
add_action('save_post_post_type_slug', array($this, 'save_mymetaboxname_metabox_data'));

public function add_mymetaboxname_metabox {
	add_meta_box('mymetaboxname', 'Title', array($this, 'mymetaboxname_metabox_callback'), 'post_type_slug', 'normal', 'low');
}

public function mymetaboxname_metabox_callback($post) { ?>
	<label>Enter your first name:</label>
	<input type="text" name="mymetaboxname[first_name]" />
	<label>Enter your last name:</label>
	<input type="text" name="mymetaboxname[last_name]" />
<?php }

public function save_mymetaboxname_metabox_data($post_id) {
	if (!isset($_POST['mymetaboxname'])) {
		return $post_id;
	}

	foreach ($_POST['mymetaboxname'] as $key => $field) {
		update_post_meta($post_id, $key, $field);
	}
}
```
