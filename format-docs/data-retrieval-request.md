## Description
This describes the parameters that describe a waveform data retrieval request. 

### Method: Time Series Windows in JSON format 

1. POST method example: JSON dictionary  
*://data-retrieval/{method}/1/ --data@some.json* where some.json is the following JSON structure 

```
{
  "RetrieveParameters": {
    "Method": String,
    "Host": String,
    "Url": String,
    "Port": String,
    "Directory": String,
    "SavePath": String
  },
  "Windows":[
    {
    "Network": String,
    "Station": String, 
    "Location": String, 
    "Channel": String,
    "Starttime": ISO8601, 
    "Endtime": ISO8601"
    },...
  ],
  "Files": {
    "Filenames": [String array],
    "Suffix": String,
    "Format": String,
    ...
  }
}
```

## Glossary

### RetrieveParameters - information for the data source 
* Method - the retrieval method used (ex Winston, TriNet, FDSN, files)
* Host - host name or IP address
* Url - data source URL
* Port - specified port for connection
* Directory - directory name for where files are located
Adjust and add other options as needed/implemented

### Windows - SNCL and time information for data windows to retrieve
* Network - FDSN network code
* Station - FDSN station code
* Location - FSDN location code
* Channel - FDSN channel code
* Starttime - Start time of the time series in ISO 8601 format (YYYY-MM-DDTHH24:MI:SSZ)
* Endtime - Start time of the time series in ISO 8601 format (YYYY-MM-DDTHH24:MI:SSZ)

### Files - filenames or information to retrieve data from files
* Filenames - list of files to retrieve by name
* Suffix - suffix of files to retrieve
* Format - filename format to retrieve
Adjust as needed/implemented

## Requirements
These are the values **required** to define a time series request for each implemented method.

### Wave Select (? not sure what the name of our current one is)
* Protocols - Waveserver, Port
* Windows - Network, Station, Channel, Location, Starttime, Endtime

### FDSN Webservice
* Protocols - Url
* Windows - Network, Station, Channel, Location, Starttime, Endtime

Add others as implemented
