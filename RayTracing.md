## Ray-casting
High-level view: to generate an image, for every pixel in the image, cast a ray from the screen space to the world space to get the color.

## Recursive Ray-tracing
when casting a ray, if the ray hits a specular surface, cast another ray from the hit point to the specular direction.