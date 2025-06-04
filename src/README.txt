# A0 Submission
Compilation:
A windows system with cmake-gui and visual studio code was utilized. 
It may be sufficient to open in visual studio and use 'Local Windows Debugger'
to build and run the solution.

Specification: 
No special specifications for A0 besides modifying main.cpp to generate
an image other than noise. 
Image produced is multicolored concentric circles with changing colors based
on GlobalFrameCount.

# A1 Submission

Tasks:
* Ray trace triangle
* Shadow rays and Lambertian shading
* Specular reflection
* Specular refraction
* Environment mapping
* (Extra) SAH BVH

## Specifications for Build/Run project

To run the project from build directory:
* First argument is the render object file
* (Optional) second argument is environment_map file

```shell
.\CS488.exe ..\..\..\media\testObj-glass.obj
```

```shell
.\CS488.exe ..\..\..\media\testObj-glass.obj ..\..\..\media\uffizi_probe.hdr
```

There are 2 `#define` statements to set options for render:

```shell
#define LAMBERTIAN_SHADOW
```
LAMBERTIAN_SHADOW macro sets whether shadow rays are rendered, which is required for
all tasks except for Task 1. Comment out this define if running task 1

```shell
#define SAHBVH
```
SAHBVH macro allows for surface area heuristic BVH splitting to accelerate ray tracing.


## (Extra) SAH BVH Implementation
SAH-BVH is implemented to speed up ray tracing. Overall, there is between a 1.5-2.3 times
speed up depending on the render .obj file loaded in the scene. We do notice a significantly
larger overhead when building the SAH-BVH compared to the non SAH-BVH methods. 

| Render Object | Average non SAH-BVH time (ms) | Average SAH-BVH time (ms) | Speed Up |
| --- | --- | --- | --- |
| cornellbox | 1133 | 509 | 2.23 |
| cornellbox-metal | 1193 | 581 | 2.05 |
| cornellbox-glass | 1598 | 821 | 1.95 |
| teapot | 397 | 259 | 1.53 |
| teapot-metal | 429 | 267 | 1.61 |
| teapot-glass | 959 | 559 | 1.72 |
| testObj | 2699 | 1167 | 2.31 |
| testObj-metal | 3060 | 1372 | 2.23 |
| testObj-glass | 3956 | 2045 | 1.93 |


