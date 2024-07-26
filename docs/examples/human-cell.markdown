---
layout: default
title: Human cell
nav_order: 3
permalink: docs/examples/human-cell
parent: Available geometries
---
# Human cell (human_cell.mac)

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Overview
DNA damage induced in a simplified human fibroblast cell can be simulated using the provided macro files. A large amount of memory and computer performance will be required for this example. The parameters used in the macro human_cell.mac and shown in this page are further described in Phys. Med. 112 (2023) 102613 ([link]({{ "https://doi.org/10.1016/j.ejmp.2023.102613" | relative_url }}))

## Geometry
This geometry consists of a continuous chain defined by taking a basic Hilbert curve. This fractal is broken into cubic regions of straight and turned chromatin sections [DNA placement]({{"/docs/geometry-library/dna-placements" | relative_url}}). This chain is included in an ellipsoid with semi-dimensions 7.1x2.5x7.1 μm, which imitates a cell nucleus. Only cubes that are completely included in the ellipsoid are considered as parts of the chain, which length is 6.4 Gbp. Bp density of the produced cell corresponds to ~0.015 bp/nm3.
```
/world/worldSize 50 um
/cell/radiusSize 14 2.5 14 um
/scheduler/endTime 5.0 ns
/scheduler/maxNullTimeSteps 10000000
/dnageom/radicalKillDistance 9 nm
/dnageom/interactionDirectRange 2.0 angstrom

/dnageom/placementSize 75 75 75 nm
/dnageom/fractalScaling 75 75 75 nm
/dnageom/definitionFile geometries/cube-centred-X-8.txt
/dnageom/placementVolume turn geometries/turned_solenoid_750_withHistone.txt
/dnageom/placementVolume turntwist geometries/turned_twisted_solenoid_750_withHistone.txt true
/dnageom/placementVolume straight geometries/straight_solenoid_750_withHistone.txt
```
The DNA model in the simulation.

![human_Cell]({{"/assets/images/humanCell_irradiation.png" | relative_url}})
{: .text-right}

Left: The 3D geometry of the cell nucleus ( 14.2μm x 14.2μm x 5μm ) used in this macro file, showing the continuous fractal interior. Right: The beam geometry used in the simulation, showing the incident protons as a parallel beam.

The chromosome as region of interest for analysis is defined using:

```
/chromosome/add cell ellipse 7100 2500 7100 0 0 0 nm 0 0 0
```
## Particle source
A proton source plane with circle radius 7.1 um was located 3 μm from the cell center.
```
/gps/pos/type Plane
/gps/pos/shape Circle
/gps/pos/centre 0 3000 0 nm
/gps/pos/rot1 0 0 1
/gps/pos/rot2 1 0 0
/gps/pos/radius 7100 nm
/gps/direction 0 -1 0
/gps/particle  proton
/analysisDNA/fileName 400keV
/gps/energy 0.4 MeV
/run/beamOn 215
```
## Damage model
Direct damage model sets 5 eV for the lower break threshold and 37.5 eV for the upper break threshold. A probability of 40.5% is set for the production of strand break.
```
/dnadamage/directDamageLower 5 eV
/dnadamage/directDamageUpper 37.5 eV

/dnadamage/indirectOHBaseChance 1.0
/dnadamage/indirectOHStrandChance 0.405
/dnadamage/inductionOHChance 0.0

/dnadamage/indirectHBaseChance 1.0
/dnadamage/indirectHStrandChance 0.0
/dnadamage/inductionHChance 0.0

/dnadamage/indirectEaqBaseChance 1.0
/dnadamage/indirectEaqStrandChance 0.0
/dnadamage/inductionEaqChance 0.0
```
## Results
Output (see [analysis]({{"docs/overview/results-and-analysis"| relative_url}})) is analysed by using human_cell.C macro file.

![human_Cell]({{"/assets/images/human_cell_results.png" | relative_url}})
{: .text-left}

- **Species Hits (/Gy/Mbp)** is defined by radical + DNA reactions,
for example: EaqStrandHits is e_aq + DNA backbone


- **Damage yield (/Gy/Gbp)** is defined by DNA damage complexity (see [classification model]({{"/docs/overview/results-and-analysis" | relative_url}}))


- **Breaks yield (/Gy/Gbp)** is showed for each break type (direct SSB, indirect SSB, DSB,...).

![human_Cell]({{"/assets/images/human_cell_Fra.png" | relative_url}})
{: .text-left}

*Fragments distribution of DNA. A fragment is defined by a distance between two DSBs.*
