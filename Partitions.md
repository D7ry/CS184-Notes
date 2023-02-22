**Spacial Hierarchies** gives us a tree-view where the leaf nodes give us the final partition.

Various types of spacial partitioning:
Oct-tree, Quad-tree, KD-tree, BSP-tree, etc.

## KD-Trees

### Internal Nodes
- Split axis: x, y, z // which axis to split on
- Split position: coordinate // where to split on the axis
- Children: left, right // left and right children

### Leaf Nodes
- Objects: list of objects // list of objects in the leaf node
- mailboxes: list of mailboxes // list of mailboxes in the leaf node

### Pre-Processing
Ideal split: choosing the split that minimizes the expected cost  of ray intersection.

#Spacial V. Object partitions

Spacial partition partitions space into non-overlapping regions.
Object partition partitions sets of objects into disjoint subsets.

Spacial partition may have one object in multiple regions.
Object partition may have the bounding box of one partition overlapping with another.

## Bounding Volume Hierarchy(BVH)

### Internal Nodes
- Bounding box
- Children

### Leaf Nodes
- Bounding box
- Objects


Like KD-tree, bounding boxes subdivides itselfs to avoid sampling all objects in large bounding boxes.

