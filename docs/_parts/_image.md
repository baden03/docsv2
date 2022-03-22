To get the uploaded images, use the helper function [rwmb_meta()](/functions/rwmb-meta/):

```php
$images = rwmb_meta( 'info', array( 'size' => 'thumbnail' ) );
foreach ( $images as $image ) {
    echo '<a href="', $image['full_url'], '"><img src="', $image['url'], '"></a>';
}
```

This 2nd argument for `rwmb_meta` is an array of extra parameters and accepts the following parameters:

Name|Description
---|---
`size`|Image size returned. Optional. If missed, `thumbnail` will be used.
`link`|Set to `true` to show link to full-size images. Leave empty to not to.
`limit`|Limit the number of returned images.

This helper function returns an array of images, each image has the following information:

```php
array(
    'ID'   => 123,
    'name' => 'logo-150x80.png',
    'path' => '/var/www/wp-content/uploads/logo-150x80.png',
    'url' => 'https://example.com/wp-content/uploads/logo-150x80.png',
    'width' => 150,
    'height' => 80,
    'full_url' => 'https://example.com/wp-content/uploads/logo.png',
    'title' => 'Logo',
    'caption' => 'Logo caption',
    'description' => 'Used in the header',
    'alt' => 'Logo ALT text',
    'srcset' => 'large.jpg 1920w, medium.jpg 960w, small.jpg 480w' // List of responsive image src
    'sizes' => array(), // List of image sizes. See https://codex.wordpress.org/Function_Reference/wp_get_attachment_metadata
    'image_meta' => array(), // List of image meta. See https://codex.wordpress.org/Function_Reference/wp_get_attachment_metadata
);
```

In case you want to get only 1 image, use the `limit` parameter for the helper function:

```php
$images = rwmb_meta( 'info', array( 'limit' => 1 ) );
$image = reset( $images );
?>
<img src="<?php echo $image['url']; ?>">
```

If you only want to display uploaded images in an unordered list, you can just use the [rwmb_the_value()](/functions/rwmb-the-value/):

```php
rwmb_the_value( $field_id, array( 'size' => 'thumbnail' ) );
```

which outputs:

```html
<ul>
    <li><a href="link/to/full-size1"><img src="link/to/image1"></a></li>
    <li><a href="link/to/full-size2"><img src="link/to/image2"></a></li>
</ul>
```

Read more about [rwmb_meta()](/functions/rwmb-meta/) and [rwmb_the_value()](/functions/rwmb-the-value/).