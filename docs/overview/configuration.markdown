---
layout: default
title: Configuration glossary
nav_order: 9
parent: Overview
permalink: docs/overview/configuration
---

# Configuration
{: .no_toc }

The custom Geant4 commands available in the molecularDNA application are listed here.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


## analysisDNA


<table ><thead><tr><th>command</th><th>description</th><th>parameters</th></tr></thead><tbody><tr><td>analysisDNA/saveStrands</td><td>Bool to set whether strands ought be saved
use /analysisDNA/strandDir to set location
</td><td><ol><li> (bool, Default: Not Set, Omittable: False)</li></ol></td></tr><tr><td>analysisDNA/strandDir</td><td>Directory to save DNA damage fragments
</td><td><ol><li>DNA fragments (str, Default: Not Set, Omittable: False)</li></ol></td></tr><tr><td>analysisDNA/fragmentGap</td><td>Gap between DNA fragments in base pairs.
Set to zero to score placement volumes independently
</td><td><ol><li>Base Pair gap (int, Default: Not Set, Omittable: False)</li></ol></td></tr><tr><td>analysisDNA/diagnosticChain</td><td>Save the position of hits histones only on one chain
</td><td><ol><li>Chain Index (int, Default: Not Set, Omittable: True)</li></ol></td></tr><tr><td>analysisDNA/dsbDistance</td><td>Max separation of DSBs. Must be less than 31.
</td><td><ol><li>Max. DSB distance. (int, Default: Not Set, Omittable: False)</li></ol></td></tr><tr><td>analysisDNA/testClassifier</td><td>Run unit test for break classification


</td><td></td></tr><tr><td>analysisDNA/fileName</td><td>ROOT output file name
</td><td><ol><li>ROOT output file name (str, Default: Not Set, Omittable: False)</li></ol></td></tr></tbody></table>



## cell


<table ><thead><tr><th>command</th><th>description</th><th>parameters</th></tr></thead><tbody><tr><td>cell/radiusSize</td><td>Set semi-major axes for cell (x, y, z) - unset, whole world is water
</td><td><ol><li>xradius (double, Default: Not Set, Omittable: False)</li><li>yradius (double, Default: Not Set, Omittable: False)</li><li>zradius (double, Default: Not Set, Omittable: False)</li><li>Unit (str, Default: Not Set, Omittable: False)</li></ol></td></tr></tbody></table>



## dnageom


<table ><thead><tr><th>command</th><th>description</th><th>parameters</th></tr></thead><tbody><tr><td>dnageom/placementVolume</td><td>Set a placement volume
format: name path
</td><td><ol><li>name path (str, Default: Not Set, Omittable: False)</li></ol></td></tr><tr><td>dnageom/definitionFile</td><td>Path to file that defines placement locations
</td><td><ol><li>path (str, Default: Not Set, Omittable: False)</li></ol></td></tr><tr><td>dnageom/placementSize</td><td>Side length for each placement (x, y, z)
</td><td><ol><li>xlength (double, Default: Not Set, Omittable: False)</li><li>ylength (double, Default: Not Set, Omittable: False)</li><li>zlength (double, Default: Not Set, Omittable: False)</li><li>Unit (str, Default: Not Set, Omittable: False)</li></ol></td></tr><tr><td>dnageom/fractalScaling</td><td>Scaling of XYZ in fractal definition file
</td><td><ol><li>xlength (double, Default: Not Set, Omittable: False)</li><li>ylength (double, Default: Not Set, Omittable: False)</li><li>zlength (double, Default: Not Set, Omittable: False)</li><li>Unit (str, Default: Not Set, Omittable: False)</li></ol></td></tr><tr><td>dnageom/checkOverlaps</td><td>Check overlaps in DNA geometry region
</td><td><ol><li>true/false check overlaps (bool, Default: Not Set, Omittable: False)</li></ol></td></tr><tr><td>dnageom/verbose</td><td>Verbosity for DNA geometry
</td><td><ol><li>int verbose level (int, Default: Not Set, Omittable: False)</li></ol></td></tr><tr><td>dnageom/setSmartVoxels</td><td>Optimisation value (int) for smart voxels
The G4 default is 2
</td><td><ol><li>Optimisation value (int, Default: Not Set, Omittable: False)</li></ol></td></tr><tr><td>dnageom/interactionDirectRange</td><td>Critical range to start recording SSBs from direct effects
</td><td><ol><li>Range (double, Default: Not Set, Omittable: False)</li><li>Unit (str, Default: Not Set, Omittable: False)</li></ol></td></tr><tr><td>dnageom/radicalKillDistance</td><td>Distance from base pairs at which to kill radicals
</td><td><ol><li>Range (double, Default: Not Set, Omittable: False)</li><li>Unit (str, Default: Not Set, Omittable: False)</li></ol></td></tr><tr><td>dnageom/activateHistoneScavenging</td><td>Activate Histone scavenging function
</td><td><ol><li>true/false Histone function (bool, Default: Not Set, Omittable: False)</li></ol></td></tr><tr><td>dnageom/drawCellVolumes</td><td>Draw cell/chromosome volumes rather than DNA (makes DNA invisible)
</td><td><ol><li>true/false draw cell volumes (bool, Default: Not Set, Omittable: False)</li></ol></td></tr></tbody></table>



## world


<table ><thead><tr><th>command</th><th>description</th><th>parameters</th></tr></thead><tbody><tr><td>world/worldSize</td><td>Side length for the world
</td><td><ol><li>Side length (double, Default: Not Set, Omittable: False)</li><li>Unit (str, Default: Not Set, Omittable: False)</li></ol></td></tr></tbody></table>
