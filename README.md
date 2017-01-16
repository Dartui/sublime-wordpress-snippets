# Wordpress Snippets for Sublime Text 3
Simple snippets for Wordpress elements, such as meta boxes, pages, subpages, post types, taxonomies, etc...

# How to use
In PHP scope write `wp_` and find snippet you want to use. Each snippet is class-based, so it cannot be used outside of class (e.g. in functions.php).

# List of snippets
- wp_plugin_wrapper - class-based wrapper for plugin development
- wp_meta_box - adds meta box for post type with callback
- wp_menu_page - adds menu in admin dashboard with callback
- wp_submenu_page - adds submenu in admin dashboard with callback
- wp_enqueue_scripts - adds action and one line of script
- wp_enqueue_script - adds one line of script