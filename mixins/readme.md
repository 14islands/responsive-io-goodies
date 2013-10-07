
# Sass mixin

Mixins for Sass to simplify using CSS background images on responsive.io.  We might provide mixins for other CSS-preprocessor, anyone is also welcome to make pull requests to this repository.


## Background image mixin

Example:

```scss
@include responsive-bg("http://mydomain.com/myimage.jpg", 700)
```

The mixin automatically detects high density screens (Retina / HiDP) and provides double sized images. To disable high density detection, pass in **false** for the $detectRetina parameter.

Example:

```scss
@include responsive-bg("http://mydomain.com/myimage.jpg", 700, false)
```

The image is now always served in the specified size.  Following is the CSS output for this mixin call.

Output:

```css
background-image: url("http://src.responsive.io/w=700/http://mydomain.com/myimage.jpg");
```


## Media query mixin

A common user case in the real-world is to use CSS for full screen background images. Here is an example how that might work using the **if-wider-then** mixin.

Example:

```scss
$imageUrl = "http://mydomain.com/myimage.jpg"
@include responsive-bg($imageUrl, 700)

@include if-wider-than(400) {
	@include responsive-bg($imageUrl, 800)
}

@include if-wider-than(800) {
	@include responsive-bg($imageUrl, 1400)
}
```

// …and so it continues.


This will output:

```css
// Mobile first
background-image: url("http://src.responsive.io/w=400/http://mydomain.com/myimage.jpg");

// First breakpoint 
@media (min-width: pxToEm(400)) {
		background-image: url("http://src.responsive.io/w=800/http://mydomain.com/myimage.jpg");
}

// Second breakpoint
@media (min-width: pxToEm(800)) {
		background-image: url("http://src.responsive.io/w=1400/http://mydomain.com/myimage.jpg")
}

// …and so it continues.
```





