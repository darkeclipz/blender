# Blender

This repository contains renderer images and code snippits for Blender.

![Hilbert](/images/hilbert_shadow_fractal.png)

## Code snippets

### Import `bpy`

To program Python in Blender, we always need to import `bpy` first.

```python
import bpy
```

### Create a cube

```python
"""
Create a new cube that sits at position (x, y, z) with a 
scale of (sx, sy, sz).
"""
def cube(x,y,z,sx,sy,sz):
    bpy.ops.mesh.primitive_cube_add(size=2, enter_editmode=False, align='WORLD', location=(x, y, z), scale=(sx, sy, sz))
```

### Create a plane & assign material

```python
plane = bpy.ops.mesh.primitive_plane_add(size=50, enter_editmode=False, align='WORLD', location=(0, 0, -0.2), scale=(100, 100, 100))
mat_plane = new_material(1, 1, 1)
active_object = bpy.context.active_object
active_object.data.materials.append(mat_plane)
```

### Create a material

```python
"""
Create a new cube that sits at position (x, y, z) with a 
scale of (sx, sy, sz).
"""
def cube(x,y,z,sx,sy,sz):
    bpy.ops.mesh.primitive_cube_add(size=2, enter_editmode=False, align='WORLD', location=(x, y, z), scale=(sx, sy, sz))
```

### Clear the scene

```python
"""
Create a new cube that sits at position (x, y, z) with a 
scale of (sx, sy, sz).
"""
def cube(x,y,z,sx,sy,sz):
    bpy.ops.mesh.primitive_cube_add(size=2, enter_editmode=False, align='WORLD', location=(x, y, z), scale=(sx, sy, sz))
```

### Add a sun

```python
sun = bpy.ops.object.light_add(type='SUN', align='WORLD', location=(0, 0, 0), scale=(1, 1, 1))
```

### Add a camera

```python
bpy.ops.object.camera_add(enter_editmode=False, align='VIEW', location=(7.5, -7.5, 6.5), rotation=(1.04, 3.60156e-07, 0.781907), scale=(1, 1, 1))
```

## Renders

See `/images` folder in this repository.

