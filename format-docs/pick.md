## Description
This describes the possible parameters to describe a pick. 

Format: JSON 

Structure: Array of objects 

Response content: based on NEIC efforts see https://code.usgs.gov/ghsc/neic/utilities/earthquake-detection-formats/-/blob/master/format-docs/Pick.md 
```
    {
      "Type"      : "Pick",
      "ID"        : String,
      "Site"      :
      {
         "Station"   : String,
         "Channel"   : String,
         "Network"   : String,
         "Location"  : String
      },
      "Time"      : ISO8601,
      "Source"    :
      {
         "AgencyID"  : String,
         "Author"    : String
      },
      "Phase"     : String,
      "Polarity"  : ("up" | "down" | "no-result"),
      "Onset"     : ("impulsive" | "emergent" | "questionable"),
      "Picker"    : ("manual" | "raypicker" | "filterpicker" | "sta-lta" | "deep-learning" | "machine-learning" | "other"),
      "Filter"    : [ {
        "Type"     : String,
        "HighPass" : Number,
        "LowPass"  : Number,
        "Units"    : String
        }, ...]
      "Amplitude" :
      {
         "Amplitude" : Number,
         "Period"    : Number,
         "SNR"       : Number
      },
      "Beam" :
      {
        "BackAzimuth"      : Number,
        "BackAzimuthError" : Number,
        "Slowness"         : Number,
        "SlownessError"    : Number,
        "PowerRatio"       : Number,
        "PowerRatioError"  : Number,
      },
      "AssociationInfo" :
      {
         "Phase"    : String,
         "Distance" : Number,
         "Azimuth"  : Number,
         "Residual" : Number,
         "Sigma"    : Number
      },
      "ClassificationInfo" :
      {
        "Phase"                : String,
        "PhaseProbability"     : Number,
        "Distance"             : Number,
        "DistanceProbability"  : Number,
        "Backazimuth"              : Number,
        "BackazimuthProbability"   : Number,
        "Magnitude"            : Number,
        "MagnitudeType"        : String,
        "MagnitudeProbability" : Number,
        "Depth"                : Number,
        "DepthProbability"     : Number,
        "ClassifyingAlgorithm" : String
      },
      "Quality" : [ {
        "Standard"     : String,
        "Value"    : Number
        }, ...]
    }
```
## Glossary

**Required Values:**

These are the values **required** to define a pick.

* Type - A string that identifies this message as a pick.
* Site - An object containing the station the pick was made (no other validation then it must be populated)
* Source - An object containing the source of the pick, (no other validation then it must be populated).
* Time - A string containing the UTC arrival time of the phase that was picked, in the ISO8601 format `YYYY-MM-DDTHH:MM:SS.SSSZ`.
* Phase - A string that identifies the seismic phase that was picked. (optional in NEIC implementation)

**Optional Values:**

The following are supplementary values that **may or may not** be provided by
various picking algorithms.

* ID - A string containing an unique identifier for this pick. (mandatory at NEIC)
* Polarity - A string containing the phase polarity; "up", "down", "no-result". "no-result" indicates a calculation was attempted.
* Onset - A string containing the phase onset; "impulsive", "emergent", or "questionable" .
* Picker - A string describing the category of picker; "manual", "raypicker", "filterpicker", "sta-lta", "deep-learning", "machine-learning", or "other". Use "author" for the name of the process that created the picks.
* Filter - An array of objects containing the filter frequencies when the pick was made, (further defined at NEIC).
* Amplitude - An object containing the amplitude associated with the pick (further defined at NEIC).
* Beam - An object containing the waveform beam information associated with the pick, (further defined at NEIC).
* AssociationInfo - An object containing the association information if this pick is used as data (further defined at NEIC).
* ClassificationInfo - An object containing the classification information of this pick, (further defined at NEIC).
* Quality - An array of objects containing information about pick quality/score/weight ratings (added by CI).
