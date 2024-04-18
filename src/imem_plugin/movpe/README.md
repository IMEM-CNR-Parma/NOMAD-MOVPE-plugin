# MOVPE IKZ Plugin

See also:

[IMEM-NOMAD-plugins](https://github.com/IMEM-CNR-Parma/IMEM-NOMAD-plugins)

[NOMAD Materials Processing plugin](https://github.com/FAIRmat-NFDI/nomad-material-processing)

[NOMAD Measurement plugin](https://github.com/FAIRmat-NFDI/nomad-measurements)

[NOMAD Analysis plugin](https://github.com/FAIRmat-NFDI/nomad-analysis)

## Overview

This directory contains the MOVPE IMEM plugin for the NOMAD project.

The MOVPE IMEM plugin is used to parse and process data related to the MOVPE growth process at IMEM.

It is derived from the former yaml schema:[AreaA-data_modeling_and_schemas/movpe_CNR](https://github.com/FAIRmat-NFDI/AreaA-data_modeling_and_schemas/tree/main/movpe_CNR)

## Structure

The directory tree:

```bash
IKZ_plugin/
├── src
│   └── imem_plugin
│       ├── __init__.py
│       ├── movpe
│       │   ├── growth_excel
│       │   │   ├── nomad_plugin.yaml
│       │   │   └── parser.py
│       │   ├── nomad_plugin.yaml
│       │   └── schema.py
│       ├── nomad_plugin.yaml
│       └── utils.py
└── tests
    └── data
        └── movpe
            └── 013_example_dataset.xlsx
```

- `src/`: contains the source code of the plugin.
- `tests/`: contains the tests and template file to use with the plugin.
- `growth_excel/`: contains the source code to parse the excel file.
- `schema.py` defines the structure of the data after it has been parsed. It specifies the fields that the structured data will contain and the types of those fields.
- `parser.py` contains the logic for parsing the raw data from the MOVPE growth process. This includes reading the data from its original format, extracting the relevant information, and transforming it into a structured format.
- `nomad_plugin.yaml` defines the raw file matching rules of the parser. Check [NOMAD plugin official docs](https://nomad-lab.eu/prod/v1/staging/docs/howto/customization/plugins_dev.html#parser-plugin-metadata) for more info.

## Usage

- You need to copy and fill the excel files in `tests/data` folder, then drag and drop them into a new NOMAD upload.

- Follow the raw file matching rules in `nomad_plugin.yaml` of each parser. In general, a file must:
  - have specific extension.
  - contain specific column headers.

> [!CAUTION]
> The parser is built to match specific template files. If files extension is changed or they are missing regex matching in the column headers, they might not be recognized by the parsers.


## Installation

Check out the root folder [IMEM-NOMAD-plugins README file](https://github.com/IMEM-CNR-Parma/IMEM-NOMAD-plugins)