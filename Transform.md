# Transform
Transform describes the position, rotation and scale of an objet in 3D space.

Transform can also describe relative position of connected body parts.

## Basic types of transforms
- Scale
- Translation
- Reflection
- Shear


## Linear Transforms
Linear transforms are usually achieved using a transform matrix.
Example:
`[x', y'] = M * [x, y]`

### w-coordinate
w-coordinate allows us to perform matrix translation.
With w = 1, matrix multiplication with t1 and t2 on the rhs of the matrix will result in a translation.

#### Homogenous coordinates
IF w is not 0 or 1, divide the whole vector by w to get the homogenous coordinates.


#### Affine Transformations
Affine map = linear map + translation:
(x' , y')<sup>T</sup> = M * (x, y)<sup>T</sup> + (t<sub>1</sub>, t<sub>2</sub>)<sup>T</sup>

Using w coordinates, we can represent affine transformations using only multiplication.

### Complex Transforms
- e.g. rotate on a point other than the origin.
  1. translate the point to the origin
  2. rotate
  3. translate back

- scale matrix that is not axis aligned
  1. rotate the point to the axis
  2. scale
  3. rotate back


## 3D transforms
```C++
class Transform
{

}
```

## Perspective Projection
a perspective projection consists of 3 parts:
1. view plane
2. front clipping plane
3. back clipping plane

The area between the front and back clipping planes is called the **view volume**. For efficiency, only the view volume is rendered.

### Linear Interpolation
