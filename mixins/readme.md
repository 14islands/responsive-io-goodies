
# Sass mixin

Sass mixinsto simplify using CSS background images on responsive.io.  We might provide mixins for other CSS-preprocessor later, but anyone is  welcome to make pull requests to this repository.


## Background image mixin

Useful mixin to use background images on responsive.io.

Example:

```scss
@include responsive-bg("http://mydomain.com/myimage.jpg", 700);
```

This mixin automatically detects high density screens (Retina / HiDP) to provide double size images. To disable high density detection, pass in **false** for the **$detectRetina** parameter.

Example:

```scss
@include responsive-bg("http://mydomain.com/myimage.jpg", 700, false)
```

The image is now always served in the specified size.  

CSS output:

```css
background-image: url("http://src.responsive.io/w=700/http://mydomain.com/myimage.jpg");
```


## Media query mixin

A common user case is to use CSS for full screen background images. Here is an example on how that might work using the **if-wider-then** mixin.

Example:

```scss
$imageUrl: "http://mydomain.com/myimage.jpg"

// Mobile first
@include responsive-bg($imageUrl, 700);

@include if-wider-than(400) {
	@include responsive-bg($imageUrl, 800);
}

@include if-wider-than(800) {
	@include responsive-bg($imageUrl, 1400);
}

// …and so it continues.
```

CSS output:

```css
background-image: url("http://src.responsive.io/w=400/http://mydomain.com/myimage.jpg");

@media (min-width: 400) {
		background-image: url("http://src.responsive.io/w=800/http://mydomain.com/myimage.jpg");
}

@media (min-width: 800) {
		background-image: url("http://src.responsive.io/w=1400/http://mydomain.com/myimage.jpg");
}

// …and so it continues.
```





