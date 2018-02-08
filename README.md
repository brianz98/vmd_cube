# vmd_cube
A Python script for rendering cube files generated by Psi4

## Adaptive isocontour values
If the cube files are generated with Psi4, vmd_cube will automatically use the adaptive isocontour values
reported in the comment section:
```
Psi4 Gaussian Cube File.
Property: Psi_a_1_1-Ag. Isocontour range for 85% of the density: (0.0535039,0)
```
These isocountour values capture 85% of the probability density using the least amount of grid points.

Alternatively, the isocontour range can be set with the `--iso` option. For example, `--iso 0.03 -0.03`.
If vmd_cube is not provided isocountour values, it will use the default ([0.05,-0.05]).

## Color schemes
The vmd_cube color scheme is customizable using the `--color1/--color2` options.
Alternatively the user can request one of the following color schemes (Emory is the default one).

![vmd_cube color schemes](/vmd_cube_color_schemes.png?raw=true "Color Schemes")

## Specifying arbitrary isosurface values/colors
vmd_cube can plot an arbitrary number of isosrufaces. This can be specified with the options `--isovalue` and `--isocolor`.
For example, to draw three surfaces with values [0.03,0.04,0.05] call vmd_cube with the following argument `--isovalue 0.03 0.04 0.05 --isocolor 3 23 12`.
Note that the number of arguments passed to `--isovalue` and `--isocolor` must be the same.

![vmd_cube color schemes](/vmd_cube_multiple_surfaces.png?raw=true "Color Schemes")


## vmd_cube options
```
>>> ./vmd_cube.py --help
usage: vmd_cube.py [-h] [--isovalue [<isovalue> [<isovalue> ...]]]
                   [--isocolor [<integer> [<integer> ...]]] [--rx [<angle>]]
                   [--ry [<angle>]] [--rz [<angle>]] [--tx [<length>]]
                   [--ty [<length>]] [--tz [<length>]] [--opacity [<opacity>]]
                   [--scale [<factor>]] [--no-montage] [--no-labels]
                   [--imagew [<integer>]] [--imageh [<integer>]]
                   [--fontsize [<integer>]] [--interactive] [--gzip]
                   [--national_scheme] [--silver_scheme] [--bright_scheme]
                   [--electron_scheme]
                   [<cubefile dir>]

vmd_cube is a script to render cube files with vmd. To generate cube files
with Psi4 add the command cubeprop() at the end of your input file.

positional arguments:
  <cubefile dir>        The directory containing the cube files.

optional arguments:
  -h, --help            show this help message and exit
  --isovalue [<isovalue> [<isovalue> ...]]
                        a list of isosurface values (a list of floats, default
                        = [0.05,-0.05])
  --isocolor [<integer> [<integer> ...]]
                        a list of isosurface color IDs (a list of integers,
                        default = [3,23])
  --rx [<angle>]        the x-axis rotation angle (float, default = 30.0)
  --ry [<angle>]        the y-axis rotation angle (float, default = 40.0)
  --rz [<angle>]        the z-axis rotation angle (float, default = 15.0)
  --tx [<length>]       the x-axis translation (float, default = 0.0)
  --ty [<length>]       the y-axis translation (float, default = 0.0)
  --tz [<length>]       the z-axis translation (float, default = 0.0)
  --opacity [<opacity>]
                        opacity of the isosurface (float, default = 1.0)
  --scale [<factor>]    the scaling factor (float, default = 1.0)
  --no-montage          call montage to combine images. (string, default =
                        false)
  --no-labels           do not add labels to images. (string, default = false)
  --imagew [<integer>]  the width of images (integer, default = 250)
  --imageh [<integer>]  the height of images (integer, default = 250)
  --fontsize [<integer>]
                        the font size (integer, default = 20)
  --interactive         run in interactive mode (default = false)
  --gzip                gzip cube files (default = false)
  --national_scheme     use a red/blue color scheme. (string, default = false)
  --silver_scheme       use a gray/white color scheme. (string, default =
                        false)
  --bright_scheme       use a soft yellow/blue color scheme. (string, default
                        = false)
  --electron_scheme     use a purple/green color scheme. (string, default =
                        false)
```
