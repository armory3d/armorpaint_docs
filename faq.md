# FAQ

#### Faces are missing on the imported mesh

The missing faces are likely caused by inverted normals &amp; backface culling. Reversing normals for the affected faces should resolve the issue.

There is also a way to disable backface culling in ArmorPaint at `Menu bar - Viewport - Cull Backfaces`, however it may cause issues with lighting due to normals pointing in the opposite direction.

If the issue persists, triangulating the mesh before importing it to ArmorPaint might help.

#### Mesh gets painted on multiple places at once

Make sure the UV map has no overlapping faces. It can be resolved by unwrapping the mesh so that each face occupies unique space on the UV map, or using multiple layers to paint objects with [multiple UV sets](https://www.youtube.com/watch?v=ocIPd6sgQBs&list=PLsoJIZPOq9_r2aciBXDB0VBo3Z0lTI2En&index=22).

Simple meshes can be unwrapped directly in ArmorPaint via the `uv_unwrap` plugin.

#### Black spots appear on the imported mesh

Make sure all mesh faces are present on the UV map.
