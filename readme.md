<p align="center">
  <img src="https://github.com/user-attachments/assets/ac9abbc0-bed6-4807-b13b-a6112e12b81d" alt="Image" width="600">
</p>

# My first VisPy graph

## Table of Contents
1. [My first 2D graph](#my-first-2d-graph)
   - [Divide Canvas](#Divide-canvas)
3. [2D animation](#2d-animation)
4. [3D graph](#3d-graph)
5. [3D animation](#3d-animation)

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

### Divide canvas

## 2D animation

Tiro parabolico animación

```python
from vispy import scene, app
import numpy as np

# constants 

g  = 9.81
v  = 4
V  = np.array([v * np.cos(np.radians(45)), v * np.sin(np.radians(45))]) 
r  = np.array([0, 0])
t  = 0
dt = 0.01
position = []

canvas = scene.SceneCanvas(keys='interactive', size=(800, 600), show=True, bgcolor='#121212')
view   = canvas.central_widget.add_view()

view.camera = scene.PanZoomCamera(rect=(0, 2, 2, 2))

x_axis = scene.visuals.Line(pos=np.array([[0, 0], [2, 0]]), color='#ffffff', width=2)
y_axis = scene.visuals.Line(pos=np.array([[0, 0], [0, 2]]), color='#ffffff', width=2)
view.add(x_axis)
view.add(y_axis)

view.camera = 'panzoom'
view.camera.set_range(x=(0, 2), y=(0, 2))

projectil = scene.visuals.Markers()
projectil.set_data(np.array([[0, 0]]), face_color='#ffffff', size=20)
view.add(projectil)

trajectory = scene.visuals.Line(pos=np.array([[0, 0]]), color='#121212', width=2)
view.add(trajectory)

def update(ev):
    global t, position, V, r
    x = r[0] + V[0] * t
    y = r[1] + V[1] * t - 0.5 * g * t**2
    position.append([x, y])
    projectil.set_data(np.array([[x, y]]), face_color='#ffffff', size=20)
    trajectory.set_data(np.array(position), color='#ffffff', width=2)
    t += dt
    if y < 0:
        t = 0
        position.clear()


timer = app.Timer()
timer.connect(update)
timer.start(dt)

app.run()
```


## 3D graph
...

## 3D animation
...
