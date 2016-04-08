# AMI Metadata
Schema and samples of the metadata at each stage of the AMI digitization workflow.

All common fields are defined in fields.json. Schema for media types at a specific stage are defined in *stage*_*mediatype*.json. A rudimentary stage level schema is defined in *stage*.json.

### Stages

1. Shipped
2. Digitized
3. QC'ed

### Media Types

* Audio Analog Cassette
* Audio Digital Cassette
* Audio Optical Disc
* Audio Reel
* Video Cassette
* Video Optical Disc
* Video Reel

## Usage
To validate a single sample json file with [ajv](https://www.npmjs.com/package/ajv):
```
ajv validate -s schema/digitized_audioreel.json -r schema/fields.json -d sample/digitized_audioreel.json
```

To validate all of the sample json files with [ajv](https://www.npmjs.com/package/ajv):
```
ajv validate -s schema/digitized.json -r "schema/*.json" -d "sample/*.json"
```
