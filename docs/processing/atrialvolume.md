---
layout: default
title: Atrial Volume
parent: Processing
nav_order: 2
---

# Calculate Atrial Volume
{: .no_toc }

### Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Background
Segmentation tools, including [CEMRG](http://www.cemrg.com) often output cardiac chamber geometries as manifolds with holes representing anatomic structures. To calculate the volume of these structures, we first post-process these manifolds to close any existing holes. Subsequently, we calculate the volume contained within the structure.

## QuickStart

```matlab
system('source ~/.bash_profile'); % ensure relevant folders are on the path
hVtk = VTKReader('openfile');
system(['FillHoles ' hVtk.Filename ' 1000000']);
% if there are still holes, then
system(['FillHoles ~/Desktop/FillHolesOutput.vtk 1000000']);
hVtk = VTKReader('~/Desktop/FillHolesOutput.vtk');
hVtk.readAllData();
hVtk.writeStl();

/Applications/meshlab.app/Contents/MacOS/meshlabserver -i ~/Desktop/FillHolesOutput.stl -s ~/Documents/Dropbox/Matlab_Code/librarysteven/meshlabserver/untitled.mlx
```

## Dependencies
* VTK
* VTK FillHoles filter (see compilation instructions below)
* Paraview
* Meshlab

### Compiling fillholes
FillHoles is available from [here](https://lorensen.github.io/VTKExamples/site/Cxx/Meshes/FillHoles/). Alternatively, clone [this](https://github.com/drsewilliams/fillholes.git) version to allow the user to specify the size of holes.
```bash
git clone https://github.com/drsewilliams/fillholes.git ./fillholes
cd fillholes/build
cmake ..
make
```
For ease, copy the executable to a location on your path (`fillholes/build/FillHoles.app/Contents/MacOS/FillHoles`).

## Process

### Close holes with FileHoles
```bash
FillHoles input.vtk 1000000
```
A window will appear showing the original mesh and the ‘filled holes’ version. It may be there are still holes. In which case, the input parameter 100000 may need to be increased. The output will be saved to the desktop as FillHolesOutput.vtp.

![](/assets/images/fill-holes-example.png)

It is possible that you will have to run FillHoles on the mesh more than once. In which case:

```bash
Fileholes ~/Desktop/FileHolesOutput.vtp 1000000
```

### Convert the VTP file to a STL file
Using Paraview, open the new VTP file. Use Save Data to save the file as an STL file.

### Calculate the Volume in MeshLab
In MeshLab, import the STL mesh. Using the Compute Geometrics filter, calculate the volume. The volume will be displayed in the output console: e.g. “Mesh Volume 38297”. If you cannot see the output console, go to View > Show Layer Dialog

![](/assets/images/meshlab-instruction.png)


## Publications using this code
