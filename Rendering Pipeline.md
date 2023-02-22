# Rendering Pipeline

## Z-Buffer
Z-buffer serves as an indicator of depth, and is used to determine which pixel is in front of another. Whichever pixel has the smallest z-value is in front of the other.

Algorithm:
```C++
for (int i = 0; i < width; i++) {
    for (int j = 0; j < height; j++) {
        if (z_buffer[i][j] < z) {
            z_buffer[i][j] = z;
            //... update frame buffer
        }
    }
}
```

To deal with transparency, draw opaque polygons before transparent polygons in sorted order.