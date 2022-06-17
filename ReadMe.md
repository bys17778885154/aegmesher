![](https://github.com/flintoftid/aegmesher/blob/master/doc/blade.jpg "AEG Blade Antenna")

# AEG Mesher: An Open Source Structured Mesh Generator for FDTD Simulations

The Applied Electromagnetics Group ([AEG][]) mesh generator, *aegmesher*, is an 
[Open Source][] structured mesh generator for creating uniform and non-uniform 
cuboid meshes. It was primarily developed in the [Department of Electronic Engineering][] 
at the [University of York][] for generating meshes for finite-difference 
time-domain ([FDTD][]) and similar electromagnetic solvers.

- - - -
**Note**: The non-uniform mesh line generation presented in the IEEE Antennas 
and Propagation Magazine article ([Berens2016]) is not yet fully integrated and 
is currently disabled. See doc/[ToDo.md][] for details.
- - - -

## Code Features

The mesh generator takes a description of a physical structure in the form of an 
unstructured mesh and then, using options provided by the user, creates a 
structured mesh representation of the structure. The mesh generator and 
associated utilities are able to read unstructured meshes in [Gmsh][] and 
[AMELET-HDF][] format. The target structured mesh can be cubic, uniform or 
non-uniform. The input unstructured mesh can contain any number of physical 
objects defined by groups of mesh elements. These groups can define point-like, 
linear, surface or volumetric objects.

The software is script-driven using the GNU [Octave][] language which allows it 
to be easily extended and combined with other phases of an overall simulation 
work-flow. The meshing is performed in two stages:

1. The input unstructured mesh is first analysed together with the user provided 
   options and a set of mesh lines generated that optimally satisfy the meshing 
   constraints. The key constraints are the maximum and minimum cell size each 
   object in the mesh. 

2. Each object in the unstructured mesh is then mapped onto the structured mesh.

Currently *aegmesher* can export the structured meshes in the [AEG][] [Vulture][] 
FDTD Code format. Other formats can easily be added.

The package also has some limited support for transforming unstructured meshes 
into formats suitable for use in the [CONCEPT-II][] method-of-moments code.

## Requirements

The code is written in a portable subset of GNU [Octave][] and [MATLAB][]. 
Additional requirements are:

1. (Mandatory for use with GNU [Octave][]) The 
   [optim](http://octave.sourceforge.net/optim/index.html) package from [OctaveForge][].

2. (Recommended) The [Gmsh][] unstructured mesh generator is highly recommended 
   for creating and viewing meshes. It also enables importing meshes in many other 
   formats such as [STL](http://en.wikipedia.org/wiki/STL_%28file_format%29).
   Note that AEG Mesher currently only support Gmsh version 2.x meshes.

3. (Optional) The [nlopt][] package provides enhanced optimisation capability.

4. (Optional) For [AMELET-HDF][] format support the command line tools from the 
   [HDF5][] package are required.

5. (Optional) To run the test-suite automatically the [CMake][] software build tool is 
   needed.

6. (Optional) To help with development or as an alternative way to download the source 
   a client for the [git][] Version Control System is required.

The code has been primarily developed using GNU [Octave][] on Linux platforms, 
but should run under both GNU [Octave][] and [MATLAB][] on Linux and Windows 
systems.

## Documentation

Installation instructions are contained in the file [Install.md][] in the 
source distribution. The best place to start after installing the software is 
with the detailed  example in the tutorial directory of the software 
package: tutorial/[tutorial.md][]. There is also a user manual in the file 
doc/[UserManual.md][].

Details of the mesher algorithms, particularly the non-uniform mesh line 
generation can be found in the article ([Berens2016]).

## Bugs and support

The code is still under development and no doubt will contain many bugs. Known 
significant bugs are listed in the file doc/[Bugs.md][]  in the source code. 

Please report bugs using the issue tracker at
<https://github.com/flintoftid/aegmesher/issues> or by email to <ian.flintoft@googlemail.com>.

For general guidance on how to write a good bug report see, for example:

* <http://www.chiark.greenend.org.uk/~sgtatham/bugs.html>
* <http://noverse.com/blog/2012/06/how-to-write-a-good-bug-report>
* <http://www.softwaretestinghelp.com/how-to-write-good-bug-report>

Some of the tips in <http://www.catb.org/esr/faqs/smart-questions.html> are also 
relevant to reporting bugs.

## How to contribute

We welcome any contributions to the development of the mesher, including:

* Fixing bugs.

* Interesting examples that can be used for test-cases.

* Improving the user documentation.

* Working on importers and exporters for other formats and codes.

* Improving the quality of the meshes generated and the general robustness of the mesher.

* Speeding up the mesh mapping phase, maybe by reimplementing keys parts as low level 
  code in another language.
  
* Items in the to-do list in the file doc/[ToDo.md][].

Please contact [Dr Ian Flintoft], <ian.flintoft@googlemail.com>, if you are interested in helping 
with these or any other aspect of development.

## Licence

The code is licensed under the [GNU Public Licence, version 3](http://www.gnu.org/copyleft/gpl.html). 
For details see the file [Licence.md][].

If you use AEG Mesher please cite ([Berens2016]).

## Developers

[Dr Ian Flintoft][], <ian.flintoft@googlemail.com>

Mr Michael Berens, <michael-berens1@web.de>

[Dr John Dawson][], <john.dawson@york.ac.uk>

## Contacts

[Dr Ian Flintoft][], <ian.flintoft@googlemail.com>

[Dr John Dawson][], <john.dawson@york.ac.uk>

## Credits

The mesher originated as the project of [Erasmus Programme][] student Mr Michael 
Berens from the [Leibnitz Universität Hannover][] during his internship at the 
[University of York][] in 2013, under the supervision of Dr John Dawson and 
Prof Heyno Garbe.

The mesh formats are largely based on the [AMELET-HDF][] specification.

Many thanks to the [Gmsh][] developers for creating an excellent [Open Source][] mesh 
generator.

## Publications using AEG Mesher

[Flintoft2018]: http://dx.doi.org/10.1109/TMTT.2017.2778059

([Flintoft2018]) I. D. Flintoft, S. A. Bourke, J. Alvarez, J. F. Dawson, M. R. Cabello, 
M. P. Robinson and S. G. Garcia, “Face centered anisotropic surface impedance boundary 
conditions in FDTD”, IEEE Transactions on Microwave Theory and Techniques, vol. 66, 2018.

[Bourke2017]: http://dx.doi.org/10.1109/EMCEurope.2017.8094791

([Bourke2017]) S. A. Bourke, J. F. Dawson, I. D. Flintoft, M. P. Robinson, “Errors in 
the shielding effectiveness of cavities due to stair-cased meshing in FDTD: Application 
of empirical correction factors”, EMC Europe 2017, International Symposium and Exhibition 
on Electromagnetic Compatibility, Angers, France, paper no. 52, 4-8 Sep. 2017.

[Berens2016]: http://dx.doi.org/10.1109/MAP.2016.2541606

([Berens2016]) M. K. Berens, I. D. Flintoft and J. F. Dawson, “Open source 
automatic non-uniform mesh generation for FDTD simulation”, IEEE Antennas and 
Propagation Magazine, vol. 58, no. 3, pp. 45-55, June 2016.

[Marvin2013b]: http://incompliancemag.com/article/a-wide-band-hybrid-antenna-for-use-in-reverberation-chambers

([Marvin2013b]) A. C. Marvin, L. Dawson, J. K. A. Everard, J. F. Dawson, G. C. R. 
Melia, I. D. Flintoft and G. Esposito, “A wide-band hybrid antenna for use in 
reverberation chambers”, In Compliance Magazine, pp. 44-50, December 2013, 

[Flintoft2013]:  http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6653358&isnumber=6653179

([Flintoft2013]) I. D. Flintoft, G. Eposito, A. C. Marvin, L. Dawson, M. P. 
Robinson and J. F. Dawson, ”Numerical evaluation of a dual-mode antenna for use 
in reverberation chambers”, EMC Europe 2013, 12th International Symposium on 
EMC, Brugge, Belgium, 2-6 September 2013, pp. 520-525.

[Marvin2013]: http://dx.doi.org/10.1109/ISEMC.2013.6670413

([Marvin2013]) A. C. Marvin, L. Dawson, J. K. A. Everard, J. F. Dawson, G. C. R. 
Melia, I. D. Flintoft and G. Esposito, “A wide-band hybrid antenna for use in 
reverberation chambers”, 2013 IEEE International Symposium on Electromagnetic 
Compatibility, Denver, Colorado, 5-9 August, 2013, pp. 222-226.

## Related links

* Robert Schneiders' [list of free and commercial mesh generation software](http://www.robertschneiders.de/meshgeneration//software.html).



[Leibnitz Universität Hannover]: http://www.uni-hannover.de/en
[University of York]: http://www.york.ac.uk
[Department of Electronic Engineering]: https://www.york.ac.uk/electronic-engineering
[AEG]: https://www.york.ac.uk/electronic-engineering/research/communication-technologies/applied-electromagnetics-devices
[Dr Ian Flintoft]: https://flintoftid.github.io
[Dr John Dawson]: https://www.york.ac.uk/electronic-engineering/staff/john_dawson
[Gmsh]: http://geuz.org/gmsh
[AMELET-HDF]: https://code.google.com/p/amelet-hdf
[Octave]: http://www.gnu.org/software/octave
[MATLAB]: http://www.mathworks.co.uk/products/matlab
[git]: https://git-scm.com
[Vulture]: https://github.com/flintoftid/vulture
[FDTD]: http://en.wikipedia.org/wiki/Finite-difference_time-domain_method
[OctaveForge]: http://octave.sourceforge.net
[HDF5]: http://www.hdfgroup.org/HDF5
[CMake]: http://www.cmake.org
[nlopt]: http://ab-initio.mit.edu/wiki/index.php/NLopt
[CONCEPT-II]: http://www.tet.tuhh.de/concept/?lang=en
[Open Source]: http://opensource.org
[Erasmus Programme]: http://en.wikipedia.org/wiki/Erasmus_Programme
[Install.md]: https://github.com/flintoftid/aegmesher/blob/master/Install.md
[tutorial.md]: https://github.com/flintoftid/aegmesher/blob/master/tutorial/tutorial.md
[UserManual.md]: https://github.com/flintoftid/aegmesher/blob/master/doc/UserManual.md
[Bugs.md]: https://github.com/flintoftid/aegmesher/blob/master/doc/Bugs.md
[ToDo.md]: https://github.com/flintoftid/aegmesher/blob/master/doc/ToDo.md
[Licence.md]: https://github.com/flintoftid/aegmesher/blob/master/Licence.md


You'd better not forget to download this paper:A Three-Dimension Cartesian Mesh Generation Algorithm Based on the GPU Parallel Ray Casting Method.
