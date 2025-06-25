<p align="center">
  <img src="https://github.com/user-attachments/assets/ac9abbc0-bed6-4807-b13b-a6112e12b81d" alt="Image" width="600">
</p>

# My first VisPy graph

## Table of Contents
1. [My first 2D graph](#my-first-2d-graph)
2. [2D animation](#2d-animation)
3. [3D graph](#3d-graph)
4. [3D animation](#3d-animation)

## My first 2D graph

```python
import numpy as np
from vispy import scene, app

canvas = scene.SceneCanvas(keys='interactive', size=(800, 600), show=True, bgcolor='#121212')
view = canvas.central_widget.add_view()

# rect=(x0, y0,, width, height)
view.camera = scene.PanZoomCamera(rect=(0, -1.5, 3 * np.pi, 3))

x = np.linspace(0, 3 * np.pi, 100)
cos = scene.visuals.Line(pos=np.column_stack((x, np.cos(x))), color='#0fffff', width=2)
sin = scene.visuals.Line(pos=np.column_stack((x, np.sin(x))), color='#ffffff', width=2)

view.add(cos)
view.add(sin)


app.run()
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/1778cea7-5cae-4d06-b060-384107546534" alt="Image" width="600">
</p>



## 2D animation
...

## 3D graph
...

## 3D animation
...
