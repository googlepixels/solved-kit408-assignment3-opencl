Download Link: https://assignmentchef.com/product/solved-kit408-assignment3-opencl
<br>
The purpose of this assignment is to give you experience at writing a program using OpenCL programming techniques. This assignment will give you an opportunity to demonstrate your understanding of:

setting up OpenCL structures; passing memory from the CPU to the GPU;

creating memory formats that work across devices; and the translation of C/C++ code to OpenCL code.

Assignment Submission

Your assignment is to be submitted electronically via MyLO and should contain:

An assignment <a href="http://www.utas.edu.au/computing-information-systems/resources/assignment-cover-sheets">cover sheet</a>;

A .zip (or .rar) containing a Visual Studio Solution containing a project for each attempted stage of the assignment (labelled sensibly so it’s easy to determine what is Stage 1, Stage 2, Stage 3, and Stage 4). A document containing:

A table of timing information comparing the original provided base code times against the Stage 4 OpenCL implementation on each scene file.

An analysis of the above timing data.

<strong>You do not need to (and shouldn’t) submit executables, temporary object files, or images.</strong> In particular, you <strong>must</strong> delete the “.vs” diretory before submission as it just Visual Studio temporary files and 100s of MBs. Do not however delete the “Scenes” folder or the “Outputs” folder (but do delete the images within this one).

<h1>Marking</h1>

This assignment will be marked out of 100. The following is the breakdown of marks:

<table width="689">

 <tbody>

  <tr>

   <td width="603"><strong>Task/Topic</strong></td>

   <td width="86"><strong>Marks</strong></td>

  </tr>

  <tr>

   <td width="603"><strong>1. OpenCL Setup and Data Transfer</strong></td>

   <td width="86"><strong>60%</strong></td>

  </tr>

  <tr>

   <td width="603"><strong>CPU-side</strong></td>

   <td width="86"> </td>

  </tr>

  <tr>

   <td width="603">Correct OpenCL setup and kernel creation</td>

   <td width="86">10%</td>

  </tr>

  <tr>

   <td width="603">Well thought out and correct OpenCL buffers and kernel arguments for representing scene data</td>

   <td width="86">10%</td>

  </tr>

  <tr>

   <td width="603">Correct creation of two-dimensional kernel job</td>

   <td width="86">5%</td>

  </tr>

  <tr>

   <td width="603">Correct memory management (i.e. freeing resources)</td>

   <td width="86">5%</td>

  </tr>

  <tr>

   <td width="603">Inclusion of (helpful) error handling</td>

   <td width="86">5%</td>

  </tr>

  <tr>

   <td width="603">Correct alignment of datastructures</td>

   <td width="86">5%</td>

  </tr>

  <tr>

   <td width="603"><strong>GPU-side</strong></td>

   <td width="86"> </td>

  </tr>

  <tr>

   <td width="603">Correct declaration of equivalent OpenCL types and datastructures (for primitives, sceneobjects, etc.)</td>

   <td width="86">10%</td>

  </tr>

  <tr>

   <td width="603">Output (via printf) that verifies that the scene has been correctly transferred (for full marks, this information should only print once per execution)</td>

   <td width="86">5%</td>

  </tr>

  <tr>

   <td width="603">Correctly fills output buffer with colour</td>

   <td width="86">5%</td>

  </tr>

  <tr>

   <td width="603"><strong>2. Basic Rendering</strong></td>

   <td width="86"><strong>10%</strong></td>

  </tr>

  <tr>

   <td width="603">OpenCL implementation of renderer that colours spheres white and everything else black (i.e. no lighting, material application, reflection, refraction, or shadowing, etc.)</td>

   <td width="86">5%</td>

  </tr>

  <tr>

   <td width="603">Correctly handles all scenes</td>

   <td width="86">5%</td>

  </tr>

  <tr>

   <td width="603"><strong>3. Rendering with Lighting</strong></td>

   <td width="86"><strong>10%</strong></td>

  </tr>

  <tr>

   <td width="603">OpenCL implementation of renderer with correct lighting for spheres and triangles but no shadows or materials</td>

   <td width="86">5%</td>

  </tr>

  <tr>

   <td width="603">Correctly handles all scenes</td>

   <td width="86">5%</td>

  </tr>

  <tr>

   <td width="603"><strong>4. Full Rendering</strong></td>

   <td width="86"><strong>10%</strong></td>

  </tr>

  <tr>

   <td width="603">OpenCL implementation of renderer with correct lighting, shadowing, materials, reflection, and refraction</td>

   <td width="86">5%</td>

  </tr>

  <tr>

   <td width="603">Correctly handles all scenes</td>

   <td width="86">5%</td>

  </tr>

  <tr>

   <td width="603"><strong>Documentation</strong></td>

   <td width="86"><strong>10%</strong></td>

  </tr>

  <tr>

   <td width="603">Outputs showing timing information for Stage 4 on all applicable scene files</td>

   <td width="86">5%</td>

  </tr>

  <tr>

   <td width="603">Analysis of data (comparison between Stage 4 and the base code)</td>

   <td width="86">5%</td>

  </tr>

  <tr>

   <td width="603"><strong>Penalties</strong></td>

   <td width="86"> </td>

  </tr>

  <tr>

   <td width="603">Failure to comply with submission instructions (eg. no cover sheet, incorrect submission of files, abnormal solution/project structure, etc.)</td>

   <td width="86">-10%</td>

  </tr>

  <tr>

   <td width="603">Poor programming style (eg. insufficient / poor comments, poor variable names, poor indenting, obfuscated code without documentation, compiler warnings, etc.)</td>

   <td width="86">up to -20%</td>

  </tr>

  <tr>

   <td width="603">Lateness (-20% for up to 24 hours, -50% for up to 7 days, -100% after 7 days)</td>

   <td width="86">up to -100%</td>

  </tr>

 </tbody>

</table>




<h2>Programming Style</h2>

This assignment is not focussed on programming style (although it is concerned with efficient code), but you should endeavour to follow good programming practices. You should, for example:

comment your code; use sensible variables names; use correct and consistent indenting; and internally document (with comments) any notable design decisions.

[NOTE: any examples in the provided assignment materials that don’t live up to the above criteria, should be considered to be deliberate examples of what not to do and are provided to aid your learning ;P]

<h1>The Assignment Task</h1>

You are to heavily modify a slightly simplified implementation of our original single-threaded “simple” raytracer so that in runs as an OpenCL program. To fully complete this assignment you will need to convert everything from render onwards (i.e. every function that is called from render, and everything that is called from there, and so on) to be written in OpenCL.

The raytracer code has been simplified to be more C-like to make the translation to OpenCL easier (e.g. references converted to pointers, typedefs for structs, limited use of const, etc.).

From the provided single-threaded raytracer implementation, you will create multiple subsequent versions that convert various parts of the program to be implemented in OpenCL:

<ol>

 <li>Code to start an OpenCL Kernel and transfer the scene datastructure (no easy task).</li>

 <li>Basic rendering that just shows spheres as white and everything else as black (i.e. got traceRay working to to the point of objectIntersection working, but no lighting etc.).</li>

 <li>Rendering with support for triangles and basic lighting complete.</li>

 <li>Full rendering with all features of the base code in OpenCL.</li>

</ol>

<h1>Implementation</h1>

<h2>1. OpenCL Initialisation and Data Transfer</h2>

This stage involves initialising OpenCL (getting the platform, context, etc. etc.) as we’ve done in the tutorials. However, it requires careful thought when deciding how to pass through data to the OpenCL kernel as all the parameters to render (e.g. width, height, aaLevel) need to be available in the kernel and this includes the entire scene object.

You can’t simply pass a pointer to the scene, as any objects more complicated than scalars need to be allocated to a buffer (so that they can be available to the GPU). Even if you allocate the scene object to a buffer, the containers for the scene objects won’t transfer over automatically, so you’ll need to think about how to transfer them as well.

Additionally, to be able to use the scene in OpenCL, you’ll need an equivalent definition of the Scene struct which in turn means you’ll need definitions of scene objects and primitives. Some of these structs can be represented by built-in OpenCL types (e.g. Point, Vector, Colour, etc.) to greatly simplify your implementation (and gain access to a host of built-in functions).

Memory layout for structs on the CPU and GPU is not likely to be the same, and so you need to take great care to ensure that each struct has the same size on both devices. This means you need to either manually pad structs to get the memory alignment you want or make use of the _declspec(align(X)) command.

You also need to be explicit about what kind of memory different variables are. Many of your datastructures and pointers to datastructures will need to be declared __global.

In order to complete this step you will need to:

Have completely transferred a copy of the scene (including the scene object containers) to the GPU and verified this via outputting the whole structure.

Filled the entire output buffer with colour to ensure that your kernel is working over the correct range.

At the end of this stage the program should successfully transfer all scene information to the OpenCL kernel and be able to create a full image (just filled with pixels). Be thorough in your testing (i.e. test all the scenes) to ensure that everything works correctly before progressing.

<h2>Hints / Tips</h2>

Just make a basic kernel to begin with and transfer only the scene object. Verify that it has transferred correctly by using printf (this is available in OpenCL (huzzah!) at the cost of greatly reduced performance) on the CPU and on the GPU (use the work offset values to ensure you only print stuff once).

Rather than defining structs for many of the renderer types you can simply typedef <a href="https://www.khronos.org/registry/cl/sdk/2.0/docs/man/xhtml/dataTypes.html">OpenCL data types</a>. e.g. use “typedef well_chosen_type Point;” instead of a struct.

Memory alignment is a big issue. Never assume that something has transferred correctly to the OpenCL program — verify that it has via printf. Your kernel function will be a conversion of the render function, but at this stage it doesn’t need to do anything except get all of the same parameters, output the scene (via printf), and fill the image in with a colour. Refer to the introductory tutorials for help making a basic kernel. Rather than create one giant OpenCL source file, you would be wise to split your code across multiple files and use the clLoadSources function that takes an array of filenames. You’ll need to ensure that you define things in the correct order (sometimes prototypes can help here).

Pay attention to where in memory your datastructures are. You will need to use __global and __constant to avoid compiler errors/warnings.

NOTE: this is probably the hardest stage of the assignment.

<h2>2. Basic Rendering</h2>

This stage involves implementing some of the functionality of the traceRay function to at least detect whether a collision with an object has occured or not. As you only need to add colour when a collision with a sphere has been detected you can either check for collisions with all kinds of objects and be selective, or just not check for collisions with triangles at this stage.

<h2>Hints / Tips</h2>

Be really careful when converting * operations. Much of the original code overloads * to be dot-product and this will not automatically translate in the OpenCL program (it may compile, but instead just do a SIMD like multiplication) — there is a dot(X, Y) function that you can use. All of the stdlib math function need to be converted to OpenCL ones. Most of the time this is as simple as removing “f” from the end of the function name.

<ol start="3">

 <li><strong>Rendering with Triangles and Lighting</strong></li>

</ol>

This stage involves including the intersection tests with triangles and adding in the lighting calculations.

<ol start="4">

 <li><strong>Full Rendering</strong></li>

</ol>

This stage involves including the materials, shadowing, bump-mapping, reflection, refraction, etc.

<h2>Hints / Tips</h2>

The isInShadow function will likely need to be refactored (not having short-circuit evaluation) to be able to be translated to OpenCL.

<h1>Documentation</h1>

For the stage 4 (anything before a complete stage 4 solution is incomparable) of the assignment you should provide:

timing information for each scene file for the total time taken for a render. See a later section for an example format for this timing table; and an explanation of the results (e.g. why there’s no difference between the performance of stage 4 compared to the base code, or why a particular implementation works well (or poorly) on a particular scene, etc.).

<strong>NOTE: all debug </strong><strong>printf outputs for normal executions (including the output of Stage 1 of the assignment) should be removed before timing   you should NOT remove error </strong><strong>printfs that occur if something goes wrong in the OpenCL setup process.</strong>

<h2>Sample Timing Table Format</h2>

The following table is an example of how the timing information could be presented in an easily comparable fashion.

See the following sections for more information about the scene files / tests to be used.

<table width="689">

 <tbody>

  <tr>

   <td rowspan="2" width="188"><strong>Test</strong></td>

   <td colspan="3" width="376"><strong>Average Time (Over 5 Runs) (Milliseconds)</strong></td>

   <td width="125"> </td>

  </tr>

  <tr>

   <td width="125"><strong>Base Single-Threaded</strong><strong> </strong></td>

   <td width="125"><strong>Base Multi-Threaded (i.e. Ass1 Solution) </strong></td>

   <td width="125"><strong>Multi-Threaded SIMD (i.e. Ass2 Solution) </strong></td>

   <td width="125"><strong>Stage 4 OpenCL </strong></td>

  </tr>

  <tr>

   <td width="188">cornell1024x1024x1</td>

   <td width="125">1016ms</td>

   <td width="125">232ms</td>

   <td width="125">TODOms</td>

   <td width="125"> </td>

  </tr>

  <tr>

   <td width="188">cornell1024x1024x4</td>

   <td width="125">14426ms</td>

   <td width="125">3450ms</td>

   <td width="125">TODOms</td>

   <td width="125"> </td>

  </tr>

  <tr>

   <td width="188">cornell500x300x1</td>

   <td width="125">127ms</td>

   <td width="125">29ms</td>

   <td width="125">TODOms</td>

   <td width="125"> </td>

  </tr>

  <tr>

   <td width="188">cornell-256lights 512x512x1</td>

   <td width="125">23830ms</td>

   <td width="125">5625ms</td>

   <td width="125">TODOms</td>

   <td width="125"> </td>

  </tr>

  <tr>

   <td width="188">allmaterials1024x1024x1</td>

   <td width="125">303ms</td>

   <td width="125">96ms</td>

   <td width="125">TODOms</td>

   <td width="125"> </td>

  </tr>

  <tr>

   <td width="188">5000spheres 960x540x1</td>

   <td width="125">19857ms</td>

   <td width="125">4843ms</td>

   <td width="125">TODOms</td>

   <td width="125"> </td>

  </tr>

  <tr>

   <td width="188">bunny500.txt 1024x1024x1</td>

   <td width="125">23107ms</td>

   <td width="125">4118ms</td>

   <td width="125">TODOms</td>

   <td width="125"> </td>

  </tr>

  <tr>

   <td width="188">bunny10k.txt256x256x1</td>

   <td width="125">40931ms</td>

   <td width="125">7862ms</td>

   <td width="125">TODOms</td>

   <td width="125"> </td>

  </tr>

 </tbody>

</table>




<h1>Provided Materials</h1>

The materials provided with this assignment contain:

the source code of the base single-threaded version of the simplified raytracer; a set of scene files to be supplied to the program; and a set of textures that are referenced by the scene files.

<u>Download the materials as an ZIP file.</u>

<h2>Source Code</h2>

The provided code consists of 20 source files.

<strong>Raytracing logic:</strong>

<em>Raytrace.cpp</em>: this file contains the main function which reads the supplied scene file, begins the raytracing, and writes the output BMP file.

The main render loop, ray trace function, and handling of reflection and refraction is also in this file.

<em>Intersection.h</em> and <em>Intersection.cpp</em>: these files define a datastructure for capturing relevant information at the point of intersection between a ray and a scene object and functions for testing for individual ray-object collisions and ray-scene collisions.

<em>Lighting.h</em> and <em>Lighting.cpp</em>: these files provide functions to apply a lighting calculation at a single intersection point.

<em>Texturing.h</em> and <em>Texturing.cpp</em>: these files provide functions for the reading points from 3D procedural textures. <em>Constants.h</em>: this header provide constant definitions used in the raytracing.

<strong>Basic types</strong>:

<em>Primitives.h</em>: this header contains definitions for points, vector, and rays. It also provides functions and overloaded operators for performing calculations with vectors and points.

<em>PrimitivesSIMD.h</em>: this header contains operators for many common SIMD functions as well as a definition for Vector8 (as a representation for 8 vectors). It also provides functions and overloaded operators for performing calculations with Vector8s. <em>SceneObjects.h</em>: this header file provides definitions for scene objects (ie. materials, lights, spheres, and triangles).

<em>Colour.h</em>: this header defines a datastructure for representing colours (with each colour component represented as a float) and simple operations on colours, including conversions to/from the standard BGR pixel format.

<strong>Scene definition and I/O</strong>:

<em>Scene.h</em> and <em>Scene.cpp</em>: the header file contains the datastructure to represent a scene and a single function that initialises this datastructure from a file. The scene datastructure itself consists of properties of the scene and lists of the various scene objects as described above. The implementation file contains many functions to aide in the scene loading process. Scene loading relies upon the functionality provided by the Config class.

<em>Config.h</em> and <em>Config.cpp</em>: this class provide facilities for parsing the scene file. <em>SimpleString.h</em>: this is helper string class used by the Config class.

<strong>Image I/O</strong>:

<em>ImageIO.h</em> and <em>ImageIO.cpp</em>: these files contain the definitions of functions to read and write BMP files.

<strong>Miscellaneous</strong>:

<em>Timer.h</em>: this class provides a simple timer that makes use of different system functions depending on whether TARGET_WINDOWS, TARGET_PPU, or TARGET_SPU is defined (we don’t use the latter two, but I left this file unchanged in case anyone wanted to see how such cross-platform stuff can be handled).

<h3>Executing</h3>

The program has the following functionality:

By default it will attempt to load the scene “../Scenes/cornell.txt” and render it at 1024×1024 with 1×1 samples.

By default it will output a file named “../Outputs/[<em>scenefile-name</em>]_[<em>width</em>]x[<em>height</em>]x[<em>sample-level</em>]_[<em>executable-filename</em>].bmp” (e.g. with all the default options, “../Outputs/cornell.txt_1024x1024x1_RayTracerAss1.exe.bmp”)

It takes command line arguments that allow the user to specify the width and height, the anti-aliasing level (must be a power of two), the name of the source scene file, the name of the destination BMP file, and the number of times to perform the render (to improve the timing information).

Additionally it accepts some arguments (that are currently unused) for setting the number of threads, whether each thread will tint the area that it renders, and the size of the block to render (only applicable for stage 3).

It loads the specified scene.

It renders the scene (as many times as requested).

It produces timing information for the average time taken to produce a render ignoring all file IO. It outputs the rendered scene as a BMP file.

For example, running the program at the command line with no arguments would perform the first test (as described in the scene file section):

On execution this would produce output similar to the following (as well as writing the resultant BMP file to <em>../Outputs/cornell.txt_1024x1024x1_RayTracerAss1.exe.bmp</em>):     average time taken (1 run(s)): 890ms

<h1>Scene Files / Tests</h1>

Your testing should use the following scene files and parameters for the image size and anti-aliasing level:

<table width="689">

 <tbody>

  <tr>

   <td width="131"><strong>Scene File</strong></td>

   <td width="63"><strong>Width</strong></td>

   <td width="66"><strong>Height</strong></td>

   <td width="72"><strong>Anti-aliasing</strong></td>

   <td width="357"><strong>Image</strong></td>

  </tr>

  <tr>

   <td width="131">cornell.txt</td>

   <td width="63">1024</td>

   <td width="66">1024</td>

   <td width="72">1</td>

   <td width="357"></td>

  </tr>

  <tr>

   <td width="131">cornell.txt</td>

   <td width="63">1024</td>

   <td width="66">1024</td>

   <td width="72">4</td>

   <td width="357"></td>

  </tr>

  <tr>

   <td width="131">cornell.txt</td>

   <td width="63">500</td>

   <td width="66">300</td>

   <td width="72">1</td>

   <td width="357"></td>

  </tr>

  <tr>

   <td width="131">cornell-256lights.txt</td>

   <td width="63">512</td>

   <td width="66">512</td>

   <td width="72">1</td>

   <td width="357"></td>

  </tr>

  <tr>

   <td width="131">allmaterials.txt</td>

   <td width="63">1024</td>

   <td width="66">1024</td>

   <td width="72">1</td>

   <td width="357"></td>

  </tr>

  <tr>

   <td width="131">5000spheres.txt</td>

   <td width="63">960</td>

   <td width="66">540</td>

   <td width="72">1</td>

   <td width="357"></td>

  </tr>

  <tr>

   <td width="131">bunny500.txt</td>

   <td width="63">1024</td>

   <td width="66">1024</td>

   <td width="72">1</td>

   <td width="357"></td>

  </tr>

  <tr>

   <td width="131">bunny10k.txt</td>

   <td width="63">256</td>

   <td width="66">256</td>

   <td width="72">1</td>

   <td width="357"></td>

  </tr>

 </tbody>

</table>


