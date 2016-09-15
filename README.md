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
* Audio Analog Reel
* Video Cassette
* Video Optical Disc
* Video Reel

To Be Defined

* Audio Wire
* Film

## Usage
To validate a single json file against a version of the schema with [ajv](https://www.npmjs.com/package/ajv):
```
ajv validate -s versions/0.7/schema/digitized_audioreel.json -r versions/0.7/schema/fields.json -d /path/to/sample_digitized_audioreel.json
```

To validate all of the sample json files against their version of the schema with [ajv](https://www.npmjs.com/package/ajv):
```
ajv validate -s versions/0.7/schema/digitized.json -r "versions/0.7/schema/*.json" -d "versions/0.7/sample/*.json"
```
