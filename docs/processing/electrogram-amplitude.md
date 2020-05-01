---
layout: default
title: Electrogram amplitude
parent: Processing
nav_order: 3
---

# Measure Electrogram Amplitudes
{: .no_toc }

### Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Background
Electrogram voltage is a commonly-used metric in clinical (but less so in laboratory) electrophysiology. This simple program allows measurement of electrogram voltage in two categories (Va and Vb).

## Quickstart
```matlab
e = rand(1000,1); % simulate some data
voltagecalipers(e);
ud = get(gcf, 'userdata');
```
Use left click+drag to measure voltage of sections of the electrogram time series and store in Va. (ctrl click+drag to store in Vb).

## Description
Left click+drag highlights the section of voltage measurement in green. Ctrl click+drag highlights the section of voltage measurement in red.

![](/assets/images/electrogram-voltage.png)

Data is stored in a structure in the Figure's userdata.

Access the measured voltages with:
```matlab
ud = get(gcf, 'userdata')

ud =

  struct with fields:

    Va: [0 0.94338 0.99331]
    Vb: [0.96277 0.98433]
```



## Publications using this code
