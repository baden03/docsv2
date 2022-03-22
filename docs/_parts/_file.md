To get the uploaded files, use the helper function [rwmb_meta()](/functions/rwmb-meta/):

```php
$files = rwmb_meta( 'field_id' );
foreach ( $files as $file ) {
    ?>
    <a href="<?php echo $file['url']; ?>"><?php echo $file['name']; ?></a>
    <?php
}
```

This helper function returns an array of files, each file has the following information:

```php
array(
    'ID'    => 123,
    'name'  => 'intro.txt',
    'path'  => '/var/www/wp-content/uploads/intro.txt',
    'url'   => 'https://example.com/wp-content/uploads/intro.txt',
    'title' => 'Introduction',
);
```

In case you want to get only 1 file, use the `limit` parameter for the helper function:

```php
$files = rwmb_meta( 'field_id', array( 'limit' => 1 ) );
$file = reset( $files );
?>
<a href="<?php echo $file['url']; ?>">Download File</a>
```

If you only want to display uploaded files in an unordered list, you can just use the [rwmb_the_value()](/functions/rwmb-the-value/):

```php
rwmb_the_value( $field_id );
```

which outputs:

```html
<ul>
    <li><a href="link/to/file/">File 1</li>
    <li><a href="link/to/file/">File 2</li>
</ul>
```

Read more about [rwmb_meta()](/functions/rwmb-meta/) and [rwmb_the_value()](/functions/rwmb-the-value/).