CUDA Path Tracer
================

**University of Pennsylvania, CIS 565: GPU Programming and Architecture, Project 3**

* YAOYI BAI (pennkey: byaoyi)
* Tested on: Windows 10 Professional, i7-6700HQ  @2.60GHz 16GB, GTX 980M 8253MB (My own Dell Alienware R3)

### (TODO: Your README)

*DO NOT* leave the README to the last minute! It is a crucial part of the
project, and we will not be able to grade you without a good README.

### 1. Part 1 - Core Features
1. Basic BSDF Feature. 
The Cornell box are Lambert material, and the sphere at the center is a mixture of both Lambert and perfect specular material, therefore it has some reflectivity and also roughness. 

![enter image description here](https://lh3.googleusercontent.com/-tYVKqM7jvi4/Wc7LZJnGBBI/AAAAAAAAA5E/Skbteim31eQbtPE3FSw5uFR9KEzztZ5xgCLcBGAs/s0/cornell.2017-09-29_22-34-04z.617samp.png "cornell.2017-09-29_22-34-04z.617samp.png")

![enter image description here](https://lh3.googleusercontent.com/-YVjj1UlUcaA/Wc7Lpx1oxaI/AAAAAAAAA5M/8MFP7rN4P6AhjNNM2LNS44PKJwWUrbBhgCLcBGAs/s0/cornell.2017-09-29_22-33-18z.219samp.png "cornell.2017-09-29_22-33-18z.219samp.png")

2. Contiguous in memory by material type

### 2. Part 2 - Own Features
#### 1) Direct lighting


#### 2) Realistic Camera Effect

Uncomment

   

    thrust::default_random_engine rng = makeSeededRandomEngine(iter, index, 0);
    
    RealisticCamera(pathSegments[index], rng);

At the last of **generateRayFromCamera** kernel function, and rebuild the project, the result of the effect would be:

 Also, **lensRadius**  and **focalDistance** defined at the beginning of pathtrace.cu can be changed according to the translation of objects inside the scene. We can focus on the sphere in the Cornell box:



#### 3) Fresnel Dielectric
To test Fresnel effect, please use the **glass.txt** in scene files. 
This scene is basically the same as the Cornell box scene, however, the sphere at the center is a glass ball, which has reflection and refraction. The Fresnel implementation here is quite naive, it simply add up Fresnel specular 

![enter image description here](https://lh3.googleusercontent.com/-fBbqpyJxXKc/Wc7LwleBXdI/AAAAAAAAA5U/REzMMYDHyckmgMqQ8tRTFbVzL6LQwXYawCLcBGAs/s0/cornell.2017-09-29_22-36-07z.492samp.png "cornell.2017-09-29_22-36-07z.492samp.png")

![enter image description here](https://lh3.googleusercontent.com/-Kg-Vc9s4snk/Wc7L00K-0WI/AAAAAAAAA5c/OCckdHya2a00K9hYeM6i5oW2nBHxERUwwCLcBGAs/s0/cornell.2017-09-29_22-36-07z.346samp.png "cornell.2017-09-29_22-36-07z.346samp.png")

### 3. Performance Analysis 