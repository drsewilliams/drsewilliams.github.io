---
layout: default
title: Contact Force Electrogram Morphology
parent: Processing
nav_order: 3
---

# Assess Contact Force Electrogram Morphology
{: .no_toc }

### Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Background
This page describes the approach for accessing the contact force data collected in [1].

## Dependencies
Carto data reader

## Process
```matlab
dataDirectory = '/Volumes/Extreme SSD/PigDataForAJ/data';
nPig = 2;
[userdata, egmSurfX, indRegion] = loadKCLContactForceData(dataDirectory, nPig);
[hSurf, hSphere] = drawKCLContactForceDataMap(userdata, indRegion, egmSurfX);
iRegion = 1;
plotKCLContactForceData(userdata, indRegion, iRegion);
```

## Output
<iframe width="100%" height="420" frameBorder="0"
src="https://youtube.com/embed/SQTjMQV5mcs?playlist=SQTjMQV5mcs&loop=1">
</iframe>

![](/assets/images/contact-force-egm-morphology.png)

## Publications
[1] Williams et al. JACC Clin Electrophysiol 2015; 1(5): 421:431. [http://dx.doi.org/10.1016/j.jacep.2015.06.003](http://dx.doi.org/10.1016/j.jacep.2015.06.003)
