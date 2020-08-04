---
layout: default
title: Omnipole Mapping
parent: Processing
nav_order: 10
---

# Perform Omnipole Voltage Mapping
{: .no_toc }

### Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Background
Omnipole mapping refers to ...
This page describes how to create an omnipole voltage map

## Dependencies
This process depends on unipole data from Carto. Specifically, the following fields must be present in the userdata structure:
tbc
In addition the following functions are required:
```matlab
RBFConductionVelocity.m % for interpolation
connectaxes % for visualisation
drawMap % for visualisation
carto2vtk % for saving data
```

## Quickstart
```matlab
[interpOtmax, interpBip, interpUni] = run_maxOmnipoleVoltage(userdata);
```

## Process
### Create omnipole dataset
```matlab
datapath = '/Users/Steven/Documents/Dropbox/Matlab_Code/workingdir/OmnipoleMapping/data/485LAiain.mat';
load(datapath)
[interpOtmax, interpBip, interpUni] = run_maxOmnipoleVoltage(userdata);
```
Each of the above output variables has numel() equal to size(userdata.surface.triRep.X,2). In other words, this represents point data, which can be used directly with [carto2vtk](/docs/processing/carto2vtk).

### Visualise the data
```matlab
ax(1) = subplot(1,3,1);
drawMap(userdata, 'data', interpBip', 'coloraxis', [0.05 0.5]); title('Bipolar');
ax(2)= subplot(1,3,2);
drawMap(userdata, 'data', interpUni', 'coloraxis', [0.5 5]); title('Unipolar');
ax(3) = subplot(1,3,3);
drawMap(userdata, 'data', interpOtmax', 'coloraxis', [0.5 5]); title('Omnipolar');
connectaxes(ax)
```
![](/assets/images/bipuniomni.png)
### Convert the data to VTK Format
See [carto2vtk](/docs/processing/carto2vtk)
```matlab
datapath = '/Users/Steven/Documents/Dropbox/Matlab_Code/workingdir/OmnipoleMapping/data/485LAiain.mat';
[d,f] = fileparts(datapath);
carto2vtk(userdata, [d filesep() f 'omni.vtk'], 'manual', 'pointdata', interpOtmax);
```

## Publications using this code
tbc
