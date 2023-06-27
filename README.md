# About Me

The best way to describe myself is a CG hobbyist. My day job is mostly related to distributed systems and backend engineering, but in my evenings I like to tinker on small CG projects just for fun. I am generally interested in rendering beautiful images often using offline rendering. I like to understand how complex materials work and I tend to spend too much time profiling and optimizing the code I write.

Here are some of the projects I made over the past 6 years:

## Raytracing in a Weekend book series

Peter Shirley's [Raytracing in One Weekend](https://raytracing.github.io/) books was the starting point to my little adventure. I've always played around with ray tracers and computer graphics but these books allowed me to build a decent render while learning the basics along the way. Eventually I rewrote the renderers in CUDA (several times) increasing its performance along the way.

![Spheres scene](/images/RaytracingInAWeekend.jpg)

## Voxel Heightmaps

I got the inspiration of this project from [ephtracy](https://twitter.com/ephtracy)'s amazing [Aerialod](https://ephtracy.github.io/index.html?page=aerialod) path tracing renderer for heightmaps. I used CUDA again and what was new with this project is that I used a voxel representation for the scene and an optimized variant of the DDA algorithm.

![Colored heightmap](/images/VoxelHeightmap4.jpg)

## Point Clouds

For this project I wanted to focus on optimizing my CUDA renderer and was looking for an easy way to support very large scenes while sticking to the basic primitives (I didn't yet have support for triangle meshes at this point). I found [Michael Fogleman](https://www.michaelfogleman.com/) [DLA](https://www.michaelfogleman.com/projects/dlaf/) project which was perfect as it only required supporting points (which are basically small spheres in my renderer). Once I got that working it was straightforward rendering point clouds.

![DLA point cloud](/images/DLAGenerator2.jpg)

![Point cloud fountain scene](/images/PointClouds.jpg)

## Triangle Meshes

For this project I finally got the chance to add support for triangle meshes along with loading .obj files. Initial implementation didn't have a proper acceleration structure and that is why I only rendered low poly models. I compensated that by adding support for more Beer law absorption for glass.

![Glass model](/images/LowPolyTintedGlass3.jpg)

## Staircase Scene

For this project I wanted to render a proper trianglemesh scene. This particular scene if from Benedikt Bitterli's [rendering resources](https://benedikt-bitterli.me/resources/), with the actual obj scene nicely provided by [Asif](https://twitter.com/knightcrawler25) as part of his [GLSL-PathTracer](https://github.com/knightcrawler25/GLSL-PathTracer). Once I got the scene rendered properly, I focused on optimizing the renderer which led me to eventually implementing more advanced BVH build algorithms (specifically triangle splitting and SBVH).

![Staircase scene](/images/Staircase.png)

## Random Walk Subsurface Scattering

For this project I wanted to implement subsurface scattering, I used this great computergraphics.stackexchange [answer](https://computergraphics.stackexchange.com/questions/5214/a-recent-approach-for-subsurface-scattering) as a basis for my renderer, then I experiemented with various models.

![Monk model](/images/MonkSSS.jpg)

## San Miguel Scene

This was the scene that was on the cover of the 2nd edition of [Physically Based Rendering](https://pbrt.org/) book. For this particular project, I used [YoctoGL](https://github.com/xelatihy/yocto-gl) which is a nice C++ library which provides a lot of code that can greatly speedup rendering development. For this particular case I mostly used it to load .pbrt file and support some of the advanced materials I didn't yet implemented before.

![San Miguel scene](/images/SanMiguel.jpg)

## Back to basics

For this project I went back to [Raytracing in One Weekend](https://raytracing.github.io/) books' code and added support for triangle meshes. For this particular implementation I wanted to focus more on adding interesting features without worrying to much of low level optimizations. For now everything is on CPU, which makes it much easier to debug when things don't work as expected.
Eventually, I rewrote the path tracer from scratch based off the [Advanced Graphics course](https://www.cs.uu.nl/docs/vakken/magr/2022-2023/index.html) from Utrecht University. As part of that, I added support for multi-threading which made rendering so much faster allowing me to explore more complex materials, including Disney's principled BRDF and volumetric absorption with and without scattering (subsurface scattering).

![Gold Dragon](/images/GoldenDragon.png)
![Red Dragon with Disney BRDF](/images/RedDragon.png)
![Orange Bunny with Disney BRDF](/images/orange-bunny-rotated-backdrop-1kspp-600x600.png)
![Glass Dragon with volumetric absorption](/images/GlassDragonWithAbsorption.png)
![Glass Monk with volumetric absorption](/images/GlassMonkWithAbsorption.png)
![Baby Dragon with Subsurface Scattering](/images/BabyDragonSSS.png)
