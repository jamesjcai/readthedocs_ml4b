Using MATLAB to Visualize Scientific Data
=========================================

Introduction 
------------

MATLAB is a high-performance language for technical computing. It
integrates computation, visualization, and programming in an easy-to-use
environment where problems and solutions are expressed in common
mathematical notation. MATLAB is an interactive system whose basic data
type is the array or matrix.

MATLAB has extensive facilities for displaying vectors and matrices as
graphs, as well as annotating and printing these graphs. It includes
high-level functions for two-dimensional and three-dimensional data
visualization, image processing, animation, and presentation graphics.
There are two basic ways to create graphs in MATLAB. You can either use
the MATLAB GUI plotting tools to interactively create graphs (see `Some
Ways to Use Plotting
Tools <http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/learn_matlab/f3-25097.html>`__
for more information) or you can use the command interface by entering
MATLAB graphics commands in the Command Window.

In this tutorial we will use the command interface to show how to
visualize scientific data using MATLAB graphics commands. We will cover
major visualization techniques such as slicing, color mapping,
contouring, oriented glyphs, and streamlines. It is assumed that the
student is familiar with the basics of using MATLAB.

For an introductory tutorial on using MATLAB, see the SCV tutorial an
`Introduction to
MATLAB <http://www.bu.edu/tech/support/research/training-consulting/online-tutorials/matlab/>`__.
`MathWorks <http://www.mathworks.com/>`__, the developer of MATLAB, also
has extensive `MATLAB
documentation <http://www.mathworks.com/access/helpdesk/help/techdoc/matlab.html>`__
including video tutorials on its website. And there is a full set of
documentation available from within MATLAB itself which can be viewed by
selecting **Product Help** from the **Help** menu.

--------------

Getting started 
---------------

The most effective way for you to go through this tutorial is to run the
listed example code in a MATLAB session as you proceed through the
tutorial. This can be accomplished by copying and pasting the listed
example code into the MATLAB *Command* *Window*. It will also be helpful
for you to browse the MATLAB documentation for the specific functions as
we discuss them (links are provided). After browsing the documentation,
you should then experiment with the example code by varying some of the
arguments and watching the effect this has on the output. By playing
with the example code, you will gain a deeper understanding of how the
various graphic functions work.

Boston University SCV users, please go to the `SCV MATLAB Help
Page <http://www.bu.edu/tech/support/research/software-and-programming/software-and-applications/rcs-software-packages/matlab/>`__
for information specific to the installation at this site. This will
tell you on what machines MATLAB is available, how to set up your
environment, how to set your display, and where the documentation is.

--------------

Graphics Model 
--------------

MATLAB has an abstract graphics layer above the local host's graphic
software interface. This insures cross-platform portability and creates
a device independent graphics layer. In MATLAB graphics objects are used
to create visual representations of data. There are two basic types of
graphics objects in the MATLAB graphics model: *Core graphics objects*
and *Composite graphics objects*. Core graphics objects include basic
drawing primitives such as line, text, rectangles, patches (filled
polygons), surfaces (3D grid of vertices), images (2D matrix
representation of an image), light sources, and axes (define the
coordinate system). Composite graphics objects are composed of core
graphics objects that have been grouped together to provide a more
convenient interface.

**Creating a Graphics Window** ┬á

In order to visualize your data, you will need a graphics window which
contains a *figure*, an *axes*, and a *view*.

Figure
~~~~~~

All MATLAB graphical output is directed to a window that is separate
from the Command Window. This window is referred to as a *figure*.
Figures can contain menus, toolbars, user-interface objects, context
menus, axes, or any other type of graphics object. MATLAB functions that
generate graphics output such as *plot,* *surf, slice,* etc. will create
a figure if none already exists. If a figure does exist, then these
functions will display their graphics output in the current figure
window (the last figure window used or clicked in). By default this will
be done without clearing or resetting the current figure properties.

To create a new figure, use the
`figure <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/figure.html>`__
function. Here is example code to create a simple graphics window:

.. code:: code-block

   figure

.. image:: http://www.bu.edu/tech/files/images/figure1.jpg
   :alt: figure1

Every graphics object has a set of properties associated with it. These
properties define the different attributes of an object, such as its
color, size, position, etc. Properties are usually specified by
name/property pairs e.g. **figure**\ (
``'PropertyName', propertyvalue, ...`` ). These properties can be set
either at the time of creation by specifying property name and property
value pairs or after the graphics object has been created by using the
`set <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/set.html>`__
function.

When creating a new figure, MATLAB creates a window whose
characteristics are specified by your computer's windowing system, by
the default MATLAB figure properties, and by the properties specified as
arguments to the function. Any property not specified as an argument
will use the default values. See the `Figure
Properties <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/figure_props.html>`__
for a list of properties that can be set for a figure.

Here is an example of setting figure properties to create a new window
named 'Test Window' with no menus and with a screen position of [left
100, bottom 500, width 250, height 250]:

.. code:: code-block

   figure('Name','Test Window','Position',[100 500 350 350],'MenuBar','none')

.. image:: http://www.bu.edu/tech/files/images/figure2.jpg
   :alt: figure2

You can use
`clf <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/clf.html>`__
(clear figure) to clear the contents of the current figure and reset all
of its properties to their default values.

.. code:: code-block

   clf reset

Axes
~~~~

Axes define a frame of reference for the display objects in the figure
window. This frame of reference is the coordinate system which defines
where each data point is placed on the graph. Axes orient and scale
graphical output to produce the view of the data that you see on screen.
By default, the size of the axes MATLAB creates is normalized to the
size of the figure window. All functions that draw graphics create an
axes object if one does not already exist.

As with figure properties, axes properties are used to specify the
characteristics of the axes. The `Axes
Properties <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/axes_props.html>`__
list all axes properties and provide an overview of the characteristics
that are affected by each property. For example camera properties such
as the camera position, camera target, up vector, and view angle can all
be directly set with axes properties. The
`axes <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/axes.html>`__
function, however, is a low-level function. Though you can specify
values for these properties directly, it is much easier to use the
*view* function (covered in the next section) to set up the axes using
default property values and to define a reasonable view.

View
~~~~

The *view* is the particular orientation you set to display the
visualization. The term *viewing* refers to the process of displaying a
graphical scene from various directions by adjusting the camera
position, changing the perspective, changing the aspect ratio, etc.

MATLAB viewing is composed of two basic areas:

-  Positioning the viewpoint to orient the scene
-  Setting the aspect ratio and relative axis scaling to control the
   shape of the objects being displayed

**Positioning the viewpoint**: The
`view <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/view.html>`__
function specifies the viewpoint by defining azimuth and elevation with
respect to the axis origin. Azimuth is a polar angle in the *x-y* plane,
with positive angles indicating counterclockwise rotation of the
viewpoint. Elevation is the angle above (positive angle) or below
(negative angle) the *x-y* plane.

.. image:: http://www.bu.edu/tech/files/images/coordinate.jpg
   :alt: coordinates

MATLAB automatically selects a viewpoint that is determined by whether
the plot is 2-D or 3-D:

-  For 2-D plots, the default is azimuth = 0┬░ and elevation = 90┬░.
-  For 3-D plots, the default is azimuth = -37.5┬░ and elevation = 30┬░.

| ``view(2)`` sets the default two-dimensional view, with az = 0, el =
  90.
| ``view(3)`` sets the default three-dimensional view, with az = ΓÇô37.5,
  el = 30.
| ``view(az,el)`` or ``view([az,el])`` set the viewing angle for a
  three-dimensional plot.

The azimuth, az, is the horizontal rotation about the *z*-axis as
measured in degrees from the negative *y*-axis. Positive values indicate
counterclockwise rotation of the viewpoint. el is the vertical elevation
of the viewpoint in degrees. Positive values of elevation correspond to
moving above the object; negative values correspond to moving below the
object.

Here is example code that creates a simple graphics window with a
default axes, a view, and a surface:

::

   Z = peaks(20);
   figure;
   h = surf(Z);
   view([-20,25]);

.. image:: http://www.bu.edu/tech/files/images/figure3.jpg
   :alt: figur33

**Setting the aspect ratio and axis scale**: The
`axis <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/axis.html>`__
command enables you to adjust the aspect ratio of graphs. The axis
command also enables you to adjust the scaling of graphs. Normally
MATLAB stretches the axes to fill the window and chooses appropriate
axes ranges based on the maxima and minima of the plotted data. If you
will be interactively rotating the visualization in the figure window
you should use the *vis3d* option.

| ``axis([xmin xmax ymin ymax zmin zmax])`` sets the limits for the
  *x*-axis, *y*-axis and *z*-axis of the current axes.
| axis vis3d freezes aspect ratio properties to enable rotation of 3-D
  objects and overrides stretch-to-fill.

Here is the same code but with a different axes:

.. code:: code-block

   Z = peaks(20);
   figure;
   h = surf(Z);
   view([-20,25]);
   axis([0 30 0 30 -15 15]);

.. image:: http://www.bu.edu/tech/files/images/figure4.jpg
   :alt: figure4

Labels
~~~~~~

The
`xlabel <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/xlabel.html>`__,
`ylabel <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/ylabel.html>`__,
and
`zlabel <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/zlabel.html>`__
commands add *x*-, *y*-, and *z*-axis labels. The
`title <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/title.html>`__
command adds a title at the top of the figure and the
`text <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/text.html>`__
function inserts text anywhere in the figure.

Here is example code that creates a simple graphics window with a
default axes, a default view, a surface, and labels:

.. code:: code-block

   Z = peaks(20);
   figure;
   h = surf(Z);
   view(3);
   axis on;
   xlabel('Longitude');
   ylabel('Latitude');
   zlabel('Altitude');
   title('Surface of Peaks');

.. image:: http://www.bu.edu/tech/files/images/figure5.jpg
   :alt: figure5

**The Camera Toolbar**

Once you have established the initial view for your visualization, you
can then use the Camera toolbar to interactively control the camera. To
enable the Camera toolbar, select **Camera Toolbar** from the figure
window's **View** menu. Your figure window should now look like this:

.. image:: http://www.bu.edu/tech/files/images/figure6.jpg
   :alt: figure6

This camera toolbar contains the following parts:

.. image:: http://www.bu.edu/tech/files/images/cameratoolbar.jpg
   :alt: camera toolbar

See `View Control with the Camera
Toolbar <http://www.mathworks.com/help/matlab/visualize/view-control-with-the-camera-toolbar.html>`__
for information on how to use the camera toolbar.

**Lighting**

Lighting is an effective means to enhance the visibility of surface
shape and to provide a three-dimensional perspective to your
visualization. MATLAB provides several commands that enable you to
position light sources and adjust the characteristics of lit objects.
These commands include the following:

`light <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/light.html>`__
- Creates a light object

`lighting <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/lighting.html>`__
- Selects a lighting method

`material <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/material.html>`__
- Sets the reflectance properties of lit objects

`camlight <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/camlight.html>`__
- Creates or moves a light with respect to the camera position

`shading <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/shading.html>`__
- Controls the color shading of surface and patch graphic objects

Here is example code that creates a simple graphics window with a
default axes, a default view, a surface, and a camera light with phong
shading:

.. code:: code-block

   Z = peaks(20);
   figure;
   h = surf(Z);
   view(3);
   axis on;
   light;
   lighting phong;
   camlight('left');
   shading interp;

.. image:: http://www.bu.edu/tech/files/images/figure7.jpg
   :alt: img

--------------

MATLAB Data Types 
-----------------

**Matrix**

The fundamental data type of MATLAB is the matrix or array. A matrix is
an n row by m column array of numbers or objects corresponding to
numbers:

.. code:: code-block

   >> a = [ 1 2 3 ; 4 5 6 ; 7 8 9]
    a = 

     1   2   3 
     4   5   6 
     7   8   9

When n is 1 the matrix is a row vector:

.. code:: code-block

   >> b = [1 2 3]
   b =

     1   2   3

When m is 1 the matrix is a column vector:

.. code:: code-block

   >> c = [1; 2; 3]
   c =

     1
     2
     3

and when both n and m are 1 the 1 x 1 matrix corresponds to a scalar.

.. code:: code-block

   >> d = [1]
   d =

     1

MATLAB uses graphics objects to create visual representations of data.
Arrays of numbers can be used not only to store scalar and vector data
but also the coordinate data of graphics objects. For example a
two-dimensional array of numbers could be used to represent a surface by
constructing a grid of rectangles whose vertices are defined by using
the row and column indices of each element as the *x*- and
*y*-coordinates and the value of each element as the *z*-coordinate.

| **Volume Data**
| MATLAB uses the term ΓÇ£Volume VisualizationΓÇ¥ to refer to the graphical
  representation of data sets that are defined on three-dimensional
  grids. These data sets are characterized by multidimensional arrays of
  scalar or vector data and are typically defined on lattice structures
  representing values sampled in 3-D space.
| MATLAB has two basic types of volume data:

-  **Scalar volume data**
-  single values for each point
-  examples: temperature, pressure, density, elevation

-  **Vector volume data**
-  two or three values for each point, defining the components of a
   vector
-  magnitude and direction
-  examples: velocity, momentum

As an example of scalar volume data, we will be using the the *flow*
M-file (M-files are text files containing MATLAB code). The flow dataset
represents the speed profile of a submerged jet within an infinite tank.

.. code:: code-block

   >> [x,y,z,v] = flow;

| The flow dataset contains four 3-D arrays: *x*, *y*, and *z* are
  coordinate arrays which specify the coordinates of each point in the
  volume and *v* specifies the scalar value for each point in the
  volume.
| As an example of vector volume data, we will be using the *wind*
  dataset. The wind dataset represents air currents over North America
  and is stored as a binary file. The
  `load <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/load.html>`__
  function imports variables containing numeric data from binary files
  or text files to the workspace.

.. code:: code-block

   >> load wind

| The wind dataset contains six 3-D arrays: *x*, *y*, and *z* are
  coordinate arrays which specify the coordinates of each point in the
  volume and *u*, *v*, and *w* are the vector components for each point
  in the volume.
| *Both the flow and wind datasets are part of the example data included
  in the MATLAB installation.*

--------------

Modeling Visualization Algorithms 
---------------------------------

Modeling algorithms are often used to reveal internal details of a data
set in order to discover where interesting regions exist.

| **Matrix to Surface**
| In MATLAB a surface is defined by the *z*-coordinates of points above
  a rectangular grid in the *x*-*y* plane. The surface is formed by
  joining adjacent points with straight lines. Surface plots are useful
  for visualizing large matrices and for graphing functions of two
  variables. In MATLAB there are two different types of surface plots:
  mesh plots and surface plots. Mesh plots are colored wire-frame
  surfaces. Surface plots are colored faceted surfaces.
| The
  `mesh <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/mesh.html>`__
  and
  `surf <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/surf.html>`__
  functions create 3-D surface plots of matrix data. For the matrix Z
  the elements Z(i,j) define the height of a surface over an underlying
  (i,j) grid.
| `Surface
  properties <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/surface_props.html>`__
  provide additional control over the visual appearance of the surface.
  You can specify line styles, face coloring, lighting characteristics,
  etc.
| The
  `meshgrid <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/meshgrid.html>`__
  function generates X and Y arrays for 3-D plots.
| The
  `peaks <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/peaks.html>`__
  function is a function of two variables, obtained by translating and
  scaling Gaussian distributions.

.. code:: code-block

   [X,Y] = meshgrid(-3:0.25:3);
   Z = peaks(X,Y);
   figure;
   mesh(X,Y,Z);
   view(3);
   axis([-3 3 -3 3 -10 10]);
   grid on;

.. image:: http://www.bu.edu/tech/files/images/mesh.jpg
   :alt: mesh

.. code:: code-block

   [X,Y] = meshgrid(-3:0.25:3);
   Z = peaks(X,Y);
   figure;
   surf(X,Y,Z);
   view(3);
   axis([-3 3 -3 3 -10 10]);
   grid on;
   light;
   lighting phong;
   camlight('left');

.. image:: http://www.bu.edu/tech/files/images/surface.jpg
   :alt: surface

| **Slicing**
| Slicing entails creating a "cross-section" of the dataset. Any kind of
  surface can be used to slice the volume, but the simplest technique is
  to use a plane to define the cutting surface thereby creating a planar
  cut. The color at each point is determined by 3-D interpolation into
  the volume. The cutting surface interpolates the data as it cuts in
  order to color the surface with values in the volume data where the
  slice is positioned. To create a planar cut we will use the
  `slice <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/slice.html>`__
  function to do the actual cutting.

.. code:: code-block

   [x,y,z,v] = flow;
   figure;
   xslice = 5;
   yslice = 0;
   zslice = 0;
   slice(x,y,z,v,xslice,yslice,zslice);
   view(3);
   axis on;
   grid on;
   light;
   lighting phong;
   camlight('left');
   shading interp;

.. image:: http://www.bu.edu/tech/files/images/slice.jpg
   :alt: slice

--------------

Scalar Visualization Algorithms 
-------------------------------

Scalars are single data values associated with each point in the
dataset. There are several different algorithms to visualize scalar
data. Two common algorithms are Color Mapping and Contouring.

| **Color Mapping**
| Color can be quite effective at conveying data values, both constant
  and varying. Color mapping is a visualization technique in which each
  scalar value in the data set is mapped through a lookup table to a
  specific color. The scalar values are used as an index into the color
  lookup table. In MATLAB the color lookup table is called the
  *colormap*. Each MATLAB figure window has a colormap associated with
  it. The colormap is a three-column 2-D matrix whose length is equal to
  the number of colors that are defined. Each row of the matrix defines
  a single color by specifying three values in the range of zero to one.
  These values define the RGB components (i.e., the intensities of the
  red, green, and blue video components) of each color.
| The primary MATLAB function used for color mapping is
  `colormap <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/colormap.html>`__.
  Colormaps can be created with either MATLAB array operations or with
  one of the several color table generating functions (*jet*, *hsv*,
  *hot*, *cool*, *summer*, and *gray*). Each of the color table
  generating functions has an optional parameter that specifies the
  number of colors or rows in the resulting colormap. The
  `colorbar <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/colorbar.html>`__
  function displays the current color scalar mapping, either vertically
  or horizontally, in the figure window. Here is example code which
  shows the mapping of the entire scalar range of the data into the jet
  color table:

.. code:: code-block

   [x,y,z,v] = flow;
   figure;
   xslice = 5;
   yslice = 0;
   zslice = 0;
   slice(x,y,z,v,xslice,yslice,zslice);
   view(3);
   axis([0 10 -4 4 -3 3]);
   grid on;
   colormap(jet(64));
   colorbar('vertical');
   shading interp;

.. image:: http://www.bu.edu/tech/files/images/colormap11.jpg
   :alt: colormap

If instead of mapping the lower scalar values to blues and the higher
values to reds, we wish to map the lower values to reds and higher
values to blues we can use the
`flipud <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/flipud.html>`__
function. Here is example code which shows the technique:

.. code:: code-block

   [x,y,z,v] = flow;
   figure;
   xslice = 5;
   yslice = 0;
   zslice = 0;
   slice(x,y,z,v,xslice,yslice,zslice);
   view(3);
   axis([0 10 -4 4 -3 3]);
   grid on;
   colormap(flipud(jet(64)));
   colorbar('vertical');
   shading interp;

.. image:: http://www.bu.edu/tech/files/images/colormap21.jpg
   :alt: colormap2

And if instead of mapping the entire scalar range of the data into the
color table, we wish to set a specific range (in terms of minimum and
maximum) of the data that is mapped, we can adjust the color limits.
Adjusting the color limits with the
`caxis <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/caxis.html>`__
function enables us to emphasize a particular range of interest in the
data. Here is example code which shows the result of limiting the color
range from -5.0 to 2.0 so that any scalar value lower than -5.0 are
mapped to the same color as -5.0 and any scalar value greater than 2.0
are mapped to the same color as 2.0:

.. code:: code-block

   [x,y,z,v] = flow;
   figure;
   xslice = 5;
   yslice = 0;
   zslice = 0;
   slice(x,y,z,v,xslice,yslice,zslice);
   view(3);
   axis([0 10 -4 4 -3 3]);
   grid on;
   colormap(flipud(jet(64)));
   caxis([-5.0,2.0]);
   colorbar('vertical');
   shading interp;

.. image:: http://www.bu.edu/tech/files/images/colormap31.jpg
   :alt: colormap3

If you want even more control over the color mapping, you can use the
`colormap
editor <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/colormapeditor.html>`__.
You open the colormap editor by selecting **Colormap** from the **Edit**
menu of the figure whose colormap you wish to modify.

.. image:: http://www.bu.edu/tech/files/images/colormapeditor1.jpg
   :alt: color map editor

| The colormap editor displays the current figure's colormap as a strip
  of colored cells. Node pointers are located below the colormap strip
  and indicate points in the colormap where the rate of the variation of
  R, G, and B values changes. You can select and move the node pointers
  to change the range of colors in the colormap. The color of a node
  pointer remains constant as you move it, but the colormap changes by
  linearly interpolating the RGB values between nodes. You can also add
  a node pointer by clicking below the corresponding cell in the
  colormap strip.
| Here is an example of using the color map editor:
| |color map editor 2|

.. image:: http://www.bu.edu/tech/files/images/colormap41.jpg
   :alt: colormap4

| **Contours / Isosurfaces**
| Contouring is a technique where one constructs a boundary between
  distinct regions in the data. Contours are lines or surfaces of
  constant scalar value. This is a natural extension from color mapping
  as our eyes instinctively separate similarly colored areas into
  distinct regions. The first step in contouring is to explore the data
  space to find points near a contour or region of interest. Once found
  these points are then connected into either contour lines
  (**isolines**) for two-dimensional data or into surfaces
  (**isosurfaces**) for three-dimensional data. The lines or surfaces
  can also be color mapped using the scalar data. The primary MATLAB
  functions used for creating contour lines are
  `contour <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/contour.html>`__
  and
  `contour3 <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/contour3.html>`__
  and
  `contourslice <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/contourslice.html>`__.
| ``contour(X,Y,Z,v)`` draws a contour plot of matrix Z with contour
  lines at the data values specified in the vector *v*.
| ``contour3(X,Y,Z,v)`` draws a contour plot of matrix Z in a 3-D view
  using X and Y to determine the x- and y-axis limits.
| ``contourslice(X,Y,Z,V,Sx,Sy,Sz,v)`` draws contour plots in the x-,
  y-, and z-axis aligned planes at the points in the vectors Sx, Sy, Sz.

Here are some examples which shows how to generate contours for
two-dimensional data:

.. code:: code-block

   [X,Y] = meshgrid(-3:0.25:3);
   Z = peaks(X,Y);
   figure;
   isovalues = (-3.0:0.5:3.0);
   contour(X,Y,Z,isovalues);
   view(2);
   axis on;
   grid on;

.. image:: http://www.bu.edu/tech/files/images/contour12.jpg
   :alt: contour1

.. code:: code-block

   [X,Y] = meshgrid(-3:0.25:3);
   Z = peaks(X,Y);
   figure;
   isovalues = (-3.0:0.5:3.0);
   contour3(X,Y,Z,isovalues);
   view(3);
   axis on;
   grid on;

.. image:: http://www.bu.edu/tech/files/images/contour22.jpg
   :alt: contour2

.. code:: code-block

   [x,y,z,v] = flow;
   figure;
   xslice = (1:3:9);
   yslice = 0;
   zslice = 0;
   isovalues = (-3.0:0.25:3.0);
   contourslice(x,y,z,v,xslice,yslice,zslice,isovalues);
   view([-10 40]);
   axis on;
   grid on;

.. image:: http://www.bu.edu/tech/files/images/contour32.jpg
   :alt: contour3

| For three-dimensional data we can generate an isosurface. Through
  exploration of the volume data, we can determine isovalues that reveal
  useful information about the data. To start select an isovalue within
  the range of values in the volume data. The primary MATLAB functions
  used for creating isosurfaces are
  `isosurface <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/isosurface.html>`__,
  `isonormals <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/isonormals.html>`__,
  and
  `patch <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/patch.html>`__.
| ``isosurface(X,Y,Z,V,isovalue)`` computes isosurface data from the
  volume data V at the isosurface value specified in *isovalue*. The
  isosurface function connects points that have the specified value the
  same way contour lines connect points of equal elevation.
| ``isosurface(X,Y,Z,V,isovalue,colors)`` computes isosurface data and
  also interpolates the array *colors* onto the scalar field and colors
  the isosurface appropriately.
| ``isonormals(X,Y,Z,V,vertices)`` computes the normals of the
  isosurface vertices from the vertex list necessary for lighting.
| ``patch`` is the low-level graphics function that creates patch
  graphics objects. A patch object is one or more polygons defined by
  the coordinates of its vertices.

In this example we show how to create a single colored isosurface:

.. code:: code-block

   [x,y,z,v] = flow;
   isovalue = -1;
   purple = [1.0 0.5 1.0];
   figure;
   p = patch(isosurface(x,y,z,v,isovalue));
   isonormals(x,y,z,v,p);
   set(p,'FaceColor',purple,'EdgeColor','none');
   view([-10 40]);
   axis on;
   grid on;
   light;
   lighting phong;
   camlight('left');

.. image:: http://www.bu.edu/tech/files/images/isosurface1.jpg
   :alt: isosurface1

In this next example we create two isosurfaces and color each of them by
using the *v* scalar data of the flow dataset and the current colormap.
The *fcolors* variable is a vector containing scalar values for each of
the vertices in the isosurface.

.. code:: code-block

   [x,y,z,v] = flow;
   isovalue = -1;
   colors = v;
   figure;
   [faces,verts,fcolors] = isosurface(x,y,z,v,isovalue,colors);
   p = patch('Vertices',verts,'Faces',faces,'FaceVertexCData',fcolors, ...
   'FaceColor','interp','EdgeColor','none');
   isonormals(x,y,z,v,p);
   isovalue2 = 0;
   [faces,verts,fcolors] = isosurface(x,y,z,v,isovalue2,colors);
   p2 = patch('Vertices',verts,'Faces',faces,'FaceVertexCData',fcolors, ...
   'FaceColor','interp','EdgeColor','none');
   isonormals(x,y,z,v,p2);
   view([-10 40]);
   axis on;
   grid on;
   colormap(jet(64));
   light;
   lighting phong;
   camlight('left');

.. image:: http://www.bu.edu/tech/files/images/isosurface2.jpg
   :alt: isosurface2

--------------

Vector Visualization Algorithms 
-------------------------------

Vector data is a three-dimensional representation of direction and
magnitude associated with each point in the dataset. Vector data is
often used to describe rate of change of some quantity. Vectors can also
be used to describe fluid flow. There are several algorithms that can be
used to visualize vector data.

| **Oriented Glyphs**
| One visualization technique for vector data is to draw an oriented,
  scaled glyph for each vector. The orientation and scale of the glyph
  can indicate the direction and magnitude of the vector. The glyph may
  also be colored according to vector magnitude or some other scalar
  quantity (e.g. temperature or pressure). Glyphs are polygonal objects
  such as a cone or an arrow. In MATLAB there are currently two types of
  glyph available: the cone or the arrow. The primary MATLAB function
  for creating oriented glyph visualizations is
  `coneplot <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/coneplot.html>`__.
| ``coneplot(X,Y,Z,U,V,W,Cx,Cy,Cz)`` plots vectors as cones pointing in
  the direction of the vector, having a length proportional to the
  magnitude of the vector.
| X, Y, Z define the coordinates for the vector field
| U, V, W define the vector field
| Cx, Cy, Cz define the location of the cones in the vector field
| See `Specifying Starting Points for Stream
  Plots <http://www.mathworks.com/help/matlab/visualize/visualizing-vector-volume-data.html#f5-7374>`__
  for tips on how to select starting locations.
| ``coneplot(...,s)`` automatically scales the cones to fit the graph
  and then stretches them by the scale factors. If you do not specify a
  value for s, a value of 1 is used. Use s = 0 to plot the cones without
  automatic scaling.
| ``coneplot(...,color)`` interpolates the array color onto the vector
  field and then colors the cones according to the interpolated values.
  The size of the color array must be the same size as the U, V, W
  arrays. This option only works with cones.
| ``coneplot(...,'quiver')`` draws arrows instead of cones.

This example uses arrow glyphs to visualize the vector data. The arrows
are scaled (proportional to the magnitude of the vectors) and are
located over the entire volume.

.. code:: code-block

   load wind;
   xmin = min(x(:));
   xmax = max(x(:));
   ymin = min(y(:));
   ymax = max(y(:));
   zmin = min(z(:));
   zmax = max(z(:));
   scale = 4;
   figure;
   [cx cy cz] = meshgrid(xmin:5:xmax,ymin:5:ymax,zmin:2:zmax);
   coneplot(x,y,z,u,v,w,cx,cy,cz,scale,'quiver');
   view([-35 60]);
   camproj perspective;
   camzoom(3.0);
   axis on;
   grid off;
   box on;

.. image:: http://www.bu.edu/tech/files/images/glyph11.jpg
   :alt: glyph1

This example uses cone glyphs to visualize the vector data. The cones
are colored by wind speed.

.. code:: code-block

   load wind;
   xmin = min(x(:));
   xmax = max(x(:));
   ymin = min(y(:));
   ymax = max(y(:));
   zmin = min(z(:));
   zmax = max(z(:));
   wind_speed = sqrt(u.^2 + v.^2 + w.^2);
   colors = wind_speed;
   scale = 4;
   figure;
   [cx cy cz] = meshgrid(xmin:5:xmax,ymin:5:ymax,zmin:2:zmax);
   c = coneplot(x,y,z,u,v,w,cx,cy,cz,scale,colors);
   set(c,'EdgeColor','none');
   view([-35 60]);
   camproj perspective;
   camzoom(3.0);
   axis on;
   grid off;
   box on;
   light;
   lighting flat;

.. image:: http://www.bu.edu/tech/files/images/glyph21.jpg
   :alt: glyph2

| **Streamlines**
| A streamline can be thought of as the path a massless particle takes
  flowing through a velocity field (i.e. vector field). Streamlines can
  be used to convey the structure of a vector field by providing a
  snapshot of the flow at a given instant in time. Multiple streamlines
  can be created to explore interesting features in the field.
  Streamlines are computed via numerical integration (integrating the
  product of velocity times delta T). The primary MATLAB functions used
  for creating streamline visualizations are
  `streamline <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/streamline.html>`__,
  `streamribbon <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/streamribbon.html>`__,
  and
  `streamtube <http://www.mathworks.com/access/helpdesk/help/techdoc/ref/streamtube.html>`__.
| ``streamline(X,Y,Z,U,V,W,startx,starty,startz)`` draws stream lines
  from the vector volume data.
| ``streamribbon(X,Y,Z,U,V,W,startx,starty,startz)`` draws stream
  ribbons from the vector volume data.
| ``streamtube(X,Y,Z,U,V,W,startx,starty,startz)`` draws stream tubes
  from the vector volume data.
| X, Y, Z define the coordinates for the vector field
| U, V, W define the vector field
| startx, starty, startz define the starting positions of the streams
| See `Specifying Starting Points for Stream
  Plots <http://www.mathworks.com/help/matlab/visualize/visualizing-vector-volume-data.html#f5-7374>`__
  for tips on how to select starting locations.

This example uses stream lines to visualize the vector data.

.. code:: code-block

   load wind;
   xmin = min(x(:));
   xmax = max(x(:));
   ymin = min(y(:));
   ymax = max(y(:));
   zmin = min(z(:));
   zmax = max(z(:));
   purple = [1.0 0.5 1.0];
   figure;
   [sx sy sz] = meshgrid(xmin,ymin:10:ymax,zmin:2:zmax);
   h = streamline(x,y,z,u,v,w,sx,sy,sz);
   set(h,'LineWidth',1,'Color',purple);
   view([-40 50]);
   axis on;
   grid off;
   box on;

.. image:: http://www.bu.edu/tech/files/images/stream1.jpg
   :alt: stream1

This example uses stream ribbons to visualize the vector data. The
ribbons are colored by the magnitude of the vectors.

::

   load wind;
   xmin = min(x(:));
   xmax = max(x(:));
   ymin = min(y(:));
   ymax = max(y(:));
   zmin = min(z(:));
   zmax = max(z(:));
   figure;
   [sx sy sz] = meshgrid(xmin,ymin:10:ymax,zmin:2:zmax)
   h = streamribbon(x,y,z,u,v,w,sx,sy,sz);
   set(h,'EdgeColor','none');
   view([-40 50]);
   axis on;
   grid off;
   box on;
   light;
   lighting flat;
   camlight('left');

.. image:: http://www.bu.edu/tech/files/images/stream2.jpg
   :alt: stream2

This example uses stream tubes to visualize the vector data. The width
of the tubes are proportional to the normalized divergence of the vector
field.

.. code:: code-block

   load wind;
   xmin = min(x(:));
   xmax = max(x(:));
   ymin = min(y(:));
   ymax = max(y(:));
   zmin = min(z(:));
   zmax = max(z(:));
   figure;
   [sx sy sz] = meshgrid(xmin,ymin:10:ymax,zmin:2:zmax);
   h = streamtube(x,y,z,u,v,w,sx,sy,sz);
   set(h,'EdgeColor','none');
   view([-40 50]);
   axis on;
   grid off;
   box on;
   light;
   lighting flat;
   camlight('left');

.. image:: http://www.bu.edu/tech/files/images/stream3.jpg
   :alt: stream3

--------------

Additional Help 
---------------

| For an introductory tutorial on using MATLAB, see the SCV tutorial an
  `Introduction to
  MATLAB <http://www.bu.edu/tech/support/research/training-consulting/online-tutorials/matlab/>`__.
| `MathWorks <http://www.mathworks.com/>`__, the developer of MATLAB,
  has extensive `MATLAB Technical Documentation and
  Support <http://www.mathworks.com/access/helpdesk/help/techdoc/matlab.html>`__
  including user guides, video tutorials, and demos on its website.
| There is a full set of documentation available from within MATLAB
  itself which can be viewed by selecting **Product Help** from the
  **Help** menu.
| For specifics on running MATLAB on SCV systems, see our `MATLAB Help
  Page <http://www.bu.edu/tech/support/research/software-and-programming/software-and-applications/rcs-software-packages/matlab/>`__.
| For more information on MATLAB, visit the `MATLAB
  website <http://www.mathworks.com/products/matlab/>`__ or the `MATLAB
  Wiki <http://matlabwiki.mathworks.com/>`__.
| There are also several other MATLAB tutorials available on the web:
  `MATLAB
  Tutorials <http://www.mathworks.com/academia/student_center/tutorials/launchpad.html>`__.

--------------

References 
----------

| All of the information covered in this tutorial was taken either from
  the standard MATLAB documentation or from the MathWorks website. Our
  goal was to simplify and reduce the amount of information you need to
  understand in order to start visualizing your data.
| *Getting Started with MATLAB*, version 7, The MathWorks, Inc.

*Using MATLAB*, version 7, The MathWorks, Inc.

*Using MATLAB Graphics*, version 7, The MathWorks, Inc.

MathWorks: `MATLAB Technical Documentation and
Support <http://www.mathworks.com/access/helpdesk/help/techdoc/matlab.html>`__

.. |color map editor 2| image:: http://www.bu.edu/tech/files/images/colormapeditor2.jpg


