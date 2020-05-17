---
layout: default
title: Userdata
nav_order: 3
parent: Electroanatomic Mapping
grand_parent: Data Sources

---

# Userdata
{: .no_toc }

### Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Background
Electroanatomic mapping data is stored in a Matlab data structure called `userdata`. This page provides a description of the data types stored in userdata. Please see [here](/docs/data-sources/carto) for instructions on how to create `userdata`.

# Description

```
userdata
    |.cartoFolder
    |.surface
    |   |.triRep
    |   |.isVertexAtRim
    |   |.act_bip
    |   |.uni_imp_frc
    |.electric
    |   |.tags
    |   |.names
    |   |.egmX
    |   |.egmSurfX
    |   |.barDirection
    |   |.egm
    |   |.egmRef
    |   |.ecg
    |   |.annotations
    |   |   |.woi
    |   |   |.referenceAnnot
    |   |   |.mapAnnot
    |   |.voltages
    |   |   |.bipolar
    |   |   |.unipolar
    |   |.impedances
    |   |   |.time
    |   |   |.value
    |   |.force
    |   |   |.force
    |   |   |.axialAngle
    |   |   |.time_force
    |   |   |.time_axial
    |   |   |.time_lateral
    |.notes
```

#### userdata.cartoFolder
tbc

## userdata.surface

#### userdata.surface.triRep
tbc

#### userdata.surface.isVertexAtRim
tbc

#### userdata.surface.act_bip
An n x 2 matrix containing mapping data, where n is the number of points in userdata.surface.triRep. Each row contains the system-assigned local activation time in column 1 and the system-assigned bipolar voltage in column 2.

#### userdata.surface.uni_imp_frc
An n x 3 matrix containing mapping data, where n is the number of points in userdata.surface.triRep. Each row contains the system-assigned unipolar voltage in column 1, the system-assigned impedance value in column 2 and the system-assigned force value in column 3.

## userdata.electric

#### userdata.electric.tags
tbc

#### userdata.electric.names
tbc

#### userdata.electric.egmX
The 3D co-ordinates of each position in space where an electrogram was recorded.

#### userdata.electric.egmSurfX
The 3D co-ordinates of each position in space on the surface defined in userdata.surface.triRep corresponding to each recorded electrogram.

#### userdata.electric.barDirection
tbc

#### userdata.electric.egm
The electrograms recorded at each position given in userdata.electric.egmX

#### userdata.electric.egmRef
A reference electrogram, such as recorded from the coronary sinus corresponding to each electrogram recorded at the positions given in userdata.electric.egmX.

#### userdata.electric.ecg
A surface ECG, such as recorded from V1 corresponding to each electrogram recorded at the positions given in userdata.electric.egmX.

### userdata.electric.annotations

#### userdata.electric.annotations.woi
tbc

#### userdata.electric.annotations.referenceAnnot
tbc

#### userdata.electric.annotations.mapAnnot
The system-assigned local activation time assigned to each electrogram recorded at the positions given in userdata.electric.egmX.

### userdata.electric.votlages

#### userdata.electric.votlages.bipolar
tbc

#### userdata.electric.votlages.unipolar
tbc

### userdata.electric.impedances

#### userdata.electric.impedances.time
tbc

#### userdata.electric.impedances.value
tbc

### userdata.electric.force

#### userdata.electric.force.force
tbc

#### userdata.electric.force.axialAngle
tbc

#### userdata.electric.force.time_force
tbc

#### userdata.electric.force.time_axial
tbc

#### userdata.electric.force.time_lateral
tbc
