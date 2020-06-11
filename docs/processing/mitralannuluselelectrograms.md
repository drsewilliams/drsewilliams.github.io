---
layout: default
title: Mitral Annulus Electrograms
parent: Processing
nav_order: 7
---

# Measure Relative Amplitudes of Electrogams at the Mitral Annulus
{: .no_toc }

### Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Background
This protocol was developed for a study measuring the relative amplitudes of the atrial and ventricular electrograms at the mitral valve annulus. It extends use of the [voltage calipers](/docs/processing/electrogram-amplitude/).

## Quickstart
Processing for this protocol is done entirely in Matlab.
```matlab
userdata = importcarto_mem;
CartoMeshToVTK_Mesh_translated;
partIDistances;
partIIvoltages;
partIIIAnalysis;
```

## Detailed Instructions

### Preparing and exporting Carto data
1.	Load case into the Carto system, and open the case for review.
2.	Click ‘Imaging’ and ‘Begin Carto Merge Study’ (it is now possible to see the segmented LA).
3.	Click ‘Study’ and ‘Export Study Data’. Select ‘Base’ and ‘CARTO VISITAG’ and click Export.
4.	Exit the study.
5.	Go to ‘System’ and ‘Export Data’; and move the file such as Export_Study-1-01_XXX into the USB drive labelling with the password Password1

### Load Carto data into Matlab

1. **Unzip** the Carto data using ‘The Unarchiver’
2. Use importcarto_mem to **read** in the Carto data, see [here](/docs/data-sources/carto/) for detailed instructions. _N.B. Use branch feature-feature-update_code_for_CartoV3.6.0.60.70_
```matlab
% Import the data into Matlab
userdata = importcarto_mem;
```

### Measure the annulus and electrograms
1. **Create a left atrial shell** from the rotational angiogram (and to store the file’s location in ```file3dra``` variable). This programme will ask you to select the mesh file (for example, ```LA.mesh```); and the Study XML file.
```matlab
% Create a left atrial shell
CartoMeshToVTK_Mesh_translated;
```
2. Identify the **mitral valve annulus plane** using ```partIDistances.m```. Select points around the mitral valve annulus using left click. Use the Matlab figure camera toolbar to rotate the shell. Once done, click 'q' on the keyboard.
```matlab
% Identify the plane of the MV annulus
partIDistances;
```
![](/assets/images/mitral-annulus-plane.png)
3. **Measure the voltages of the ventricular and atrial electrograms.** Run ```partIIVoltages.m``` and use this programme to measure the voltages of the ventricular and atrial electrograms. This will store the voltages in a cell array called voltages, since the number of measured voltages will depend on the number of electrograms present. As detailed [here](/docs/processing/electrogram-amplitude/) use left click+drag and ctrl left click+drag for atrial and ventricular electrograms, respectively.
```matlab
% Measure the electrogram voltages
partIIvoltages;
```
![](/assets/images/mitral-electrogram-voltage.png)

### Analyse the Data
1. Run ```partIIIAnalysis.m``` to analyse the data
```matlab
% Analyse the Data
partIIIAnalysis;
```
Two values are output - the difference in the A/V electrogram voltage at the mitral valve annulus (in mV) and the ratio of the A/V electrograms at the mitral valve annulus. By definition negative ratio indicates that the V electrogram is bigger than the A electrogram; whilst a positive ratio is given for A electrograms greater in amplitude than V electrograms.
![](/assets/images/ma-egm-analysis.png)

## Publications using this code
