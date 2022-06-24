# Physical Design Workshop using OpenLane VSD

## Introduction to OpenLane
OpenLane is an automated RTL to GDSII flow based on several components including OpenROAD, Yosys, Magic, Netgen, CVC, SPEF-Extractor, CU-GR, Klayout and a number of custom scripts for design exploration and optimization. The flow performs full ASIC implementation steps from RTL all the way down to GDSII.

Installation, documentation and architecture of OpenLane can be found in following [OpenLane Github](https://github.com/The-OpenROAD-Project/OpenLane) link

### OpenLane detailed ASCI workflow 

OpenLane flow consists of several stages. All flow steps are to be run in sequence. Each stage may consist of multiple sub-stages.

![OpenLane workflow](Images/openlane.flow.1.png)

### Open-source eda tools in OpenLane

OpenLane integrated several key open source tools over the execution stages 

```
Synthesis
        yosys - Performs RTL synthesis
        abc - Performs technology mapping
        OpenSTA - Performs static timing analysis on the resulting netlist to generate timing reports
    Floorplan and PDN
        init_fp - Defines the core area for the macro as well as the rows (used for placement) and the tracks (used for routing)
        ioplacer - Places the macro input and output ports
        pdn - Generates the power distribution network
        tapcell - Inserts welltap and decap cells in the floorplan
    Placement
        RePLace - Performs global placement
        Resizer - Performs optional optimizations on the design
        OpenDP - Perfroms detailed placement to legalize the globally placed components
    CTS
        TritonCTS - Synthesizes the clock distribution network (the clock tree)
    Routing
        FastRoute - Performs global routing to generate a guide file for the detailed router
        CU-GR - Another option for performing global routing.
        TritonRoute - Performs detailed routing
        SPEF-Extractor - Performs SPEF extraction
    GDSII Generation
        Magic - Streams out the final GDSII layout file from the routed def
        Klayout - Streams out the final GDSII layout file from the routed def as a back-up
    Checks
        Magic - Performs DRC Checks & Antenna Checks
        Klayout - Performs DRC Checks
        Netgen - Performs LVS Checks
        CVC - Performs Circuit Validity Checks
```

### Directory structure

All output run data is placed by default under ./designs/design_name/runs. Each flow cycle will output a timestamp-marked folder containing the following file structure.

```
designs/<design_name>
├── config.tcl
├── runs
│   ├── <tag>
│   │   ├── config.tcl
│   │   ├── {logs, reports, tmp}
│   │   │   ├── cts
│   │   │   ├── signoff
│   │   │   ├── floorplan
│   │   │   ├── placement
│   │   │   ├── routing
│   │   │   └── synthesis
│   │   ├── results
│   │   │   ├── final
│   │   │   ├── cts
│   │   │   ├── signoff
│   │   │   ├── floorplan
│   │   │   ├── placement
│   │   │   ├── routing
│   │   │   └── synthesis

```


## ASIC design using OpenLane

### 1. Invoke OpenLane interactive and prepare design 

- `./flow.tcl -interactive` : invokes Openlane in interactive mode such that all flow steps can be run sequentially to see logs, results generated after each stage. 
 
- `package require openlane 0.9` : imports all OpenLane packages.

> ![OpenLane workflow](Images/import_packages_openlane_interactive.png )

- `prep -design <design_name>` : starts design preparation stage where tool creates merged LEF and configuration for OpenLane tools.

  Following are the outputs form design preparation stage
> ![OpenLane workflow](Images/op_dsgn_prep.png)



### 2. Synthesis








