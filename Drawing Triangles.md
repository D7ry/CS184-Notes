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
Line tangent vector `T`of 2 points = P~1~ - P~0~ = (x~1~ - x~0~, y~1~ - y~0~) = (T~x~, T~y~)
Line normal vector `N` of 2 points = T~x~, -T~y~ = (N~x~, N~y~)
To calculate if dot V is on the plane, derive:
L~i~ = `dot(V,N)`
if L~i~ > 0  
then V is inside the half-plane
if L~i~ < 0  
then V is outside the half-plane
if L~i~ = 0  
then V is on the line


```cpp
bool triangle::inside(x, y) {
    // L0 = dot((x,y), N0)
    // L1 = dot((x,y), N1)
    // L2 = dot((x,y), N2)
    // if L0 > 0 && L1 > 0 && L2 > 0
    // then (x,y) is inside the triangle
    // else (x,y) is outside the triangle
}

frameBuffer_t fb

for (int x = 0; x < xmas; x++) {
    for (int y = 0; x < ymas, y++) {
        if (triangle.inside(x, y)) {
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

Triangles drawn are poorly approximated for smaller resolutions, this will be discussed in future notes.
![](https://cs184.eecs.berkeley.edu/public/sp23/lectures/lec-2-digital-drawing/slides/slide-62.jpg)