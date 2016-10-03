# AMI Metadata
Schema and samples of the metadata at each stage of the AMI digitization workflow.

All common fields are defined in fields.json. Schema for media types at a specific stage are defined in *stage*_*mediatype*.json. A rudimentary stage level schema is defined in *stage*.json.

## Stages

1. Shipped (in process)
2. Digitized
3. QC'ed (in process)

## Media Types

* Audio Cassette Analog
* Audio Cassette Digital
* Audio Grooved Cylinder
* Audio Grooved Disc
* Audio Optical Disc
* Audio Reel Analog
* Audio Reel Digital
* Video Cassette Analog
* Video Cassette DV
* Video Optical Disc
* Video Reel

To Be Defined

* Audio Magnetic Cylinder
* Audio Wire
* Film

## Usage
There are a number of tools that can validate data against JSON schema. We recommend [ajv](https://www.npmjs.com/package/ajv). To use ajv from a terminal window as in the following examples, you will also need [ajv-cli](https://www.npmjs.com/package/ajv-cli)

To validate a single sample json file against a version of the schema with ajv:
```
cd path/to/schema/base/directory
ajv validate -s versions/1.1/schema/digitized_audioreel.json -r versions/1.1/schema/fields.json -d /path/to/sample_digitized_audioreel.json
```

To validate all of the sample json files against their version of the schema with ajv:
```
cd path/to/schema/base/directory
ajv validate -s versions/1.1/schema/digitized.json -r "versions/0.7/schema/*.json" -d "versions/1.1/sample/*.json"
```

To validate all json files in a set of bags with ajv:
```
ajv validate -s path/to/version/and/schema/digitized.json -r "path/to/version/and/schema/*.json" -d "path/to/directory/of/bags/*/data/*/*.json"
```
