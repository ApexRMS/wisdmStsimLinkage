# Canada Thistle Demo

This project contains code for linking a WISDM library for modelling Canada Thistle distribution with a ST-Sim library for modelling Canada Thistle establishment relative to different management and disturbance regimes.

Below are the instructions to setup, configure, and run the code.

## Table of Contents

#### [Setup](#Setup-1)

#### [Configuration](#Configuration-1)

#### [Run Instructions](#Running)

## Setup

### Dependencies

These scripts require a working installations of R and SyncroSim, and were
developed on R v4.1.3 and SyncroSim v2.4.36. Additionally the following
R packages must be installed: `rsyncrosim`, `tidyverse`, `terra`, `yaml`. The ST-Sim package (v3.3.13) must also be installed in
SyncroSim. The instructions to run the script assume you will be using [RStudio](https://rstudio.com/),
however, this is not a strict requirement.

### Input Libraries

Two SyncroSim libraries are required that are not included on the GitHub repository due
to size constraints. These libraries have been saved as backup files that can
be downloaded from the the following links: 
- [Canada Thistle ST-Sim Library](https://s3.us-west-2.amazonaws.com/apexrms.com.public/USGS/A306/WISDM%20ST-Sim%20Linkage/Canada%20Thistle%20Demo/Input%20Libraries/CanadaThistleSTSimModel.ssim.backup.2023-08-25-at-11-28-04.ssimbak)
- [Canada Thistle WISDM Library](https://s3.us-west-2.amazonaws.com/apexrms.com.public/USGS/A306/WISDM%20ST-Sim%20Linkage/Canada%20Thistle%20Demo/Input%20Libraries/CanadaThistleWisdmModel.ssim.backup.2023-08-28-at-15-34-19.ssimbak)
Please note that the WISDM file is quite large (~5.7GB).

These backup files should be downloaded and saved into a folder named `library/` that should created in the same
folder as this README, not inside another folder (such as
`scripts/`). Once downloaded, both backup files must be opened, and saved as active libraries to the same `library/` folder.

## Configuration

The run can be configured by editing the `config/config.yaml` file. R Studio and
most modern text editors have syntax highlighting for YAML files that can help
with editing these files, but may not be associated with `*.yaml` files by
default. The YAML file syntax is fairly self-evident, but please see this short
[overview](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html)
for details.

## <a name="Running"></a>Run Instructions

Begin by opening the `demoWisdmStSimLinkage.Rproj` R project file to ensure the
correct working directory is set in RStudio. Next, open the `link-wisdm-and-stsim-libraries.R` 
script and either run line-by-line or press the `source` button in the top right
corner of the file editor pane of RStudio.

This script is responsible for extracting the probability of occurrence maps output by the pre-run WISDM library and preparing them for use as Spatial Transition Multipliers in the pre-configured ST-Sim library. The script then generates and runs forecast scenarios associated with different management and distribution forecsates for Canada Thistle.

Results can be viewed directly in the SyncroSim graphical user interface (GUI). Open the updated ST-Sim library and select the results scenarios from the `02 - Future Forecast` sub-folder of the `Full Scenarios` folder. Next select the Charts and Maps that you would like to view. You can also export tabular and map data to be viewed externally.

NOTE that using the GUI is optional and the scenario can also be run directly 
through the SyncroSim commandline or by using the rsyncrosim package for R.

