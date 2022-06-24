# Physical Design training using OpenLane VSD

## Introduction to OpenLane
OpenLane is an automated RTL to GDSII flow based on several components including OpenROAD, Yosys, Magic, Netgen, CVC, SPEF-Extractor, CU-GR, Klayout and a number of custom scripts for design exploration and optimization. The flow performs full ASIC implementation steps from RTL all the way down to GDSII.

Installation, documentation and architecture of OpenLane can be found in following link

[OpenLane Github](https://github.com/The-OpenROAD-Project/OpenLane)

## Physical Design training using skywater 130 PDK

### OpenLane workflow 

![OpenLane workflow](Images/openlane.flow.1.png)

Invoke Openlane in interactive mode using flow.tcl

`./flow.tcl -interactive`
