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

### Hilbert's fractal as a shadow effect

```python
"""
Recursively draw shapes, and shrink the objects on each recursion depth.
"""
def recursive_split(x, y, z, sx, sy, sz, k):
    
    cube(x, y, z, sx, sy, sz)
    active_object = bpy.context.active_object
    r, g, b = colorsys.hsv_to_rgb(0.075 * k, 0.85, 1)
    mat = new_material(r, g, b)
    active_object.data.materials.append(mat)
    
    if k > 0:
        for i in range(-1, 1+1, 2):
            for j in range(-1, 1+1, 2):
                recursive_split(
                    x+i*sx, y+j*sy, z + 3*sz,     # (x, y, z)
                    sx * 0.5, sy * 0.5, sz * 0.7, # (sx, sy, sz)
                    k-1
                )
    


"""
Run the algorithm.
"""
recursive_split(0, 0, 0, 1, 1, 0.2, 5)
```

In this case `k = 5`, so it will draw a total of `4^5 = 1024` cubes, so this might take a while. 

## Renders

See `/images` folder in this repository.

