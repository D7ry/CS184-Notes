# Drawing Triangles
<p> Learning how to draw triangles on the screen by sampling</p>

**Frame buffer**
Memory for a Raster Display

**Rasterization**
The process of converting a 3D scene into a frame buffer, which can be turned into an 2D image.

**Shape Primitives**
Shape primitives are basic units for drawing shapes on screen.  
Shape primitives + **vertexes**(xyz pos of each node) = shapes

## Triangles  

Triangles is a fundamental area primitive.  
All other polygons can be broken down into triangles.

### Properties of triangles:
- Guaranteed to be planar
- Well-defined method for interpolating values at vertices over triangle(?)

**Rasterization = drawing a triangle to the frame buffer**

## Triangle Rasterization

Input: Position of triangle verties projected on screen ->   
Output: Set of pixel values approximating the triangle


### Rasterization by SAMPLING
**Sampling is the core idea of Computer Graphics**  

 `func()` is a continuous function but has been discretized in the following code by sampling.
```cpp
for (int x = 0; x < xmas; x++) {
    output[x] = func(x);
}
```

### 2D Triangle sampling

Triangle = Intersection of 3 **Half Planes**  
Each line defines two half-planes.

#### Line equation Derivation
**Line Tangent Vector**
Line tangent vector of `P1, P0` = P1 - P0
Line normal vector of `p1, p0` = (P1 - P0) x (0, 0, 1)
Line equation L~i~ = `dot(v,n)`

if L(x,y) >= 0  
then (x,y) is inside the half-plane

```cpp
bool inside(triangle, x, y) {
    if (triangle.contains(x, y)) {
        return true;
    } 
    return false;
}

frameBuffer_t fb

for (int x = 0; x < xmas; x++) {
    for (int y = 0; x < ymas, y++) {
        if (inside(triangle, x, y)) {
            fb[x][y] = 1;
        } else {
            fb[x][y] = 0;
        }
    }
}
```

*OpenGl/D3D Edge convention:*
Edge Rule: 
When sample point falls on edge i.e. L~i~(x,y) = 0, the point is only on triangle if the edge is "top edge" or "left edge"

*Modern approach: Tiled Triangle Traversal*
Tests all samples in block in parallel, supported by all modern GPUs through SIMD instructions

## Signal Reconstruction on Real Displays
Assume each pixel emits a square of light that can be controlled independently.