---
layout: default
title: Carto
nav_order: 1
parent: Electroanatomic Mapping
grand_parent: Data Sources

---

# Carto (Biosense Webster)
{: .no_toc }

### Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Background

# Quickstart

# Detailed instructions
Carto exports password protected .zip files. Each password protected .zip file (for example, ```ExportData26_04_20 18_21_18.zip```) contains a further .zip file that contains the data (for example, ```Export_Study-1331-04_26_2020-17-59-21.zip```).

# Helper functions
A number of functions are provided to assist with interpretation of Carto data.

## cemrg2carto.m
*cemrg2carto* converts a CEMRG VTK file for use in CARTO.

The wrapper *doCemrg2Carto* is also provided which uses file dialogs to specify the in files and out files.

## drawMap.m
*drawMap* plots a Carto LAT map. Usage:
```matlab
    hSurf = drawMap(userdata)
    hSurf = drawMap(userdata, varargin);
```
Where:
* hSurf - is a handle to the surface
* userdata - is a Carto data structure

*drawMap* is essentially a wrapper function for colorShell.m.

*drawMap* accepts the following parameter-value pairs:
- parameter ```'type'```, values ```('act')```, ```'bip'```
  - Specifies type of map - activation, bipolar or unipolar voltage
- parameter ```'coloraxis'``` values ```[a b]```
  - Where a and b are real numbers. See help colorShell
- parameter ```'noLight'```, values ```(false)```, ```true```
  - If set to true no additional light will be drawn. Useful if overlaying maps.
- parameter ```'usrColorMap'```, values ```([])```, ```cMap```
  - If set, this colormap will be used instead of the defaults
- parameter ```'colorbarlocation'```, values ```'north'```, ```'south'```, ```'east'```, ```{'west'}```, ```'northoutside'```, ```'southoutside'```, ```'eastoutside'```, ```'westoutside'```
  - specifies position of the color bar

Usage example:
```matlab
  hSurf = drawMap(userdata, 'type', 'act')
  set(hSurf, 'facealpha', .5);
  hSphere = plot3dsphere(userdata.electric.egmSurfX, 'r', 3, 16, 'stepthrough', true)
```
# Troubleshooting

## HD Coloring

HD Coloring is a feature that was added to Carto in Carto 3 Version XXX. It's function is to XXX.

When a dataset is exported from Carto with HD Colouring turned on, the .mesh file is not included in the data output

There is a workaround which is to turn HD Coloring OFF as follows.

1. From the main menu select 'System'
2. Then select 'Tech Tools'. Contact Biosense Webster for the password for your machine.
3. From the menu click on the 'CAS Tools' tab.
4. Click on 'Feature Activation'
5. Untick the 'HD Coloring' feature

These steps are shown in the screenshots below
![](/assets/images/cas-tools-tab.png)
![](/assets/images/feature-activation.png)
![](/assets/images/hd-coloring-feature.png)

# Publications

This code has been used in the following publications.
