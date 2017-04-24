# AMI Metadata
This repository contains schema and sample files of the required metadata for NYPL AMI digitization. All metadata included in AMI bags should validate against one of the defined schema.

## Repository organization
Major release versions are maintained in `versions/x.x`. Each version directory contains a directory a `sample` and `schema` sub-directory. Within `schema` common metadata elements are defined in `fields.json` and schema for media types are defined in `digitized_*mediatype*.json`. Each version also includes a `digitized.json` schema, which can test a single json metadata file against every media type schema in that version.

## Media Types

* Audio Cassette Analog
* Audio Cassette Digital
* Audio Grooved Cylinder
* Audio Grooved Disc
* Audio Optical Disc
* Audio Reel Analog
* Audio Reel Digital
* Audio Wire
* Video Cassette Analog
* Video Cassette Digital
* Video Optical Disc
* Video Reel

To Be Defined

* Audio Magnetic Cylinder
* Film

## Usage
There are a number of tools that can validate JSON data against JSON schema. We recommend [ajv](https://www.npmjs.com/package/ajv). To use ajv from a terminal window as in the following examples, you will also need [ajv-cli](https://www.npmjs.com/package/ajv-cli)

To validate a single sample json file against a version of the schema with ajv:
```
cd path/to/schema/base/directory
ajv validate -s versions/2.0/schema/digitized_audioreel.json -r versions/2.0/schema/fields.json -d /path/to/sample_digitized_audioreel.json
```

To validate all of the sample json files against their version of the schema with ajv:
```
cd path/to/schema/base/directory
ajv validate -s versions/2.0/schema/digitized.json -r "versions/2.0/schema/*.json" -d "versions/2.0/sample/*.json"
```

To validate all json files in a set of bags with ajv:
```
ajv validate -s path/to/schema/version/digitized.json -r "path/to/schema/version/*.json" -d "path/to/directory/of/bags/*/data/*/*.json"
```
