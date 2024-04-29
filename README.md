# Formats

This repo contains the formats as input and output of SCSN seismic processing services as well as overall description of the message structure for the services.

## Service Request and Response Structure

The message structure for both request calls and response outputs of this service is the http response structure in JSON
<pre>
{
    "status": // HTTP status code,
    "headers":{
        "Content-Type": "application/json",
        ...
        // other headers may be present
        },
    "body": {
        // Request or Response Parameters
        }
}
</pre>

### HTTP status codes
For a request that is not from a web service, use 200.

### Headers
Use headers to include any authentication information. No authentication information is provided in the body.

### Body
The body of the message structure will contain the retrieval parameters in a request or data points in a response specific to the service.

These are defined in [format-docs](https://scsngit.gps.caltech.edu/services/formats/-/tree/main/format-docs?ref_type=heads) .


## Example
This is an example message that describes a [time window](https://scsngit.gps.caltech.edu/services/formats/-/blob/main/format-docs/data-retrieval-request.md?ref_type=heads) that could be used in a data retrieval service later.

<pre>
{
    "status": 200,
    "headers":{
        "Content-Type": "application/json"
    },
    "body":{
        "RetrieveParameters": {
            "Method": "TriNet", 
            "Host": "waveserver", 
            "Port": "9999", 
            "SavePath": "/tmp/output"
            }, 
            "Windows": [
                {"Network": "AZ",
                 "Station": "TRO", 
                 "Channel": "HHZ", 
                 "Location": "--", 
                 "Starttime": "2024-03-15T00:30:05.047Z", 
                 "Endtime": "2024-03-15T00:31:05.047Z"
                 }
                ]
            }
}
                
</pre>

