---
title: rwmb_set_meta
---

`rwmb_set_meta` is a helper function that helps you to set value for a field.


## Arguments

This function accepts 4 parameters as follows:

```php
rwmb_set_meta( $object_id, $field_id, $value, $args = [] );
```

Parameter|Description
---|---
`$object_id`|Object (post, term, user) ID. If you need to set value for an option (using MB Settings Page), object ID is the option name.
`$field_id`|Field ID.
`$value`|Value. Should be compatible with field value format. See [database](/database/).
`$args`|Extra arguments for some object types or storages. It works similarly in [rwmb_meta](/functions/rwmb-meta/) function. Can be array or a string in format param1=value1&param2=value2. Optional.

:::caution

This function works only when the field is already registered. In Meta Box, fields are registered at hook `init` with priority 20. So, you need to run this function after that:

```php
add_action( 'init', function() {
	rwmb_set_meta( 12, 'my_field', 'my_value' );
}, 99 );
```
:::

## Examples

**Setting a field value for a post:**

```php
add_action( 'init', function() {
	$post_id = 123;
	$field_id = 'my_field';
	$value = 'My custom value';
	rwmb_set_meta( $post_id, $field_id, $value );
}, 99 );
```

**Setting a cloneable group value for a post:**

```php
add_action( 'init', function() {
	$post_id = 123;
	$field_id = 'my_field';
	$value = [
		[
			'name' => 'Andy',
			'email' => 'andy@mail.com',
		],
		[
			'name' => 'Bruce',
			'email' => 'bruce@mail.com',
		],
	];
	rwmb_set_meta( $post_id, $field_id, $value );
}, 99 );
```

**Setting a field value for a term:**

```php
add_action( 'init', function() {
	$term_id = 123;
	$field_id = 'my_field';
	$value = 'My custom value';
	$args = [ 'object_type' => 'term' ];
	rwmb_set_meta( $term_id, $field_id, $value, $args );
}, 99 );
```

**Setting a field value for a user:**

```php
add_action( 'init', function() {
	$user_id = 123;
	$field_id = 'my_field';
	$value = 'My custom value';
	$args = [ 'object_type' => 'user' ];
	rwmb_set_meta( $user_id, $field_id, $value, $args );
}, 99 );
```

**Setting a field value for a settings page:**

```php
add_action( 'init', function() {
	$option_name = 'my_option';
	$field_id = 'my_field';
	$value = 'My custom value';
	$args = [ 'object_type' => 'setting' ];
	rwmb_set_meta( $option_name, $field_id, $value, $args );
}, 99 );
```

**Setting a field value with custom table:**

```php
add_action( 'init', function() {
	$table_name = 'my_table';
	$post_id = 123;
	$field_id = 'my_field';
	$value = 'My custom value';
	$args = [
		'storage_type' => 'custom_table',
		'table'        => $table_name,
	];
	rwmb_set_meta( $post_id, $field_id, $value, $args );
}, 99 );
```
