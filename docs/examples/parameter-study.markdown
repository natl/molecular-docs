---
layout: default
title: Parameter study
nav_order: 1
permalink: docs/examples/parameter-study
parent: Available geometries
---

# Parameter study (cylinders.mac)

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Overview
The simulation geometry is based upon a past parameter study [1] of direct and indirect DNA damage yields in straight DNA fibres to study the impacts of the different parameters.
## Geometry
The geometry for parameter sweeps consists of a 3 μm sphere filled with 200.000 individual 216bp long straight DNA segments in a 100×30×30 nm placement volume. Radical kill distance [Damage model]( {{ "docs/overview/damage-model" | relative_url }} )  was set to 9 nm, as well as the range for direct interaction was set to 7 A.

```
/world/worldSize 10200 nm
/cell/radiusSize 3 3 3 um

/scheduler/endTime 1 us

/dnageom/setSmartVoxels 1
/dnageom/checkOverlaps false

/dnageom/radicalKillDistance 9 nm
/dnageom/interactionDirectRange 7 angstrom

/dnageom/placementSize 30 30 100 nm
/dnageom/fractalScaling 1 1 1 nm
/dnageom/definitionFile geometries/prisms200k_r3000.txt
/dnageom/placementVolume prism geometries/straight-216-0.txt

/dnageom/setVoxelPlacementAnglesAsMultiplesOfPi false
/dnageom/useCustomMoleculeSizes false
```

![cylinders]({{"/assets/images/cylinderImage.png" | relative_url}})
{: .text-center}

The chromosome as region of interest for analysis is defined using:

```
/chromosome/add cylinder sphere 3000 0 0 0 nm
```

## Particle source
Primary electrons are generated randomly, with a random direction in a smaller 500 nm sphere in the centre of the test region. The primary particles with energies no greater than 4.5 keV cannot escape the larger spherical region, and all primaries see an equivalently random region.
```
/gps/particle e-
/gps/ang/type iso
/gps/energy 4.5 keV
/gps/pos/type Volume
/gps/pos/shape Sphere
/gps/pos/radius 500 nm
/gps/pos/centre 0 0 0 nm
/run/beamOn 100000
```
## Damage model
Direct damage model uses the 17.5 eV for lower and upper break thresholds.
```
/dnadamage/directDamageLower 17.5 eV
/dnadamage/directDamageUpper 17.5 eV

/dnadamage/indirectOHBaseChance 1.0
/dnadamage/indirectOHStrandChance 0.65
/dnadamage/inductionOHChance 0.0

/dnadamage/indirectHBaseChance 1.0
/dnadamage/indirectHStrandChance 0.65
/dnadamage/inductionHChance 0.0

/dnadamage/indirectEaqBaseChance 1.0
/dnadamage/indirectEaqStrandChance 0.65
/dnadamage/inductionEaqChance 0.0
```
## Results
Output (see [analysis]({{"docs/overview/results-and-analysis"| relative_url}})) is analysed by using cylinders.C macro file.

![cylinders]({{"/assets/images/cylinders.png" | relative_url}})
{: .text-left}

Refer [classification model]({{"/docs/overview/results-and-analysis" | relative_url}}) for detail of source and complexity frequency.

## Visualization

For visualization, the following line can be used:
```
/control/execute vis.mac
```
More specifically, start moleculardna using the command:
```
./molecular
```
to open the Qt visualiser. Then use the mac file that you want, e.g.
```
/control/execute cylinders.mac
```
For such visualization, large amount of RAM is needed. For example using cylinders DNA geometries, to visualize 200 cylinders, ~2.5 Gb are needed. For 2000 cylinders, ~11 Gb are needed.

## Reference
1. Computational modelling of low-energy electron-induced DNA damage by early physical and chemical events, Nikjoo et al.,Int. J. Rad. Bio., 1997, 71, 467.
