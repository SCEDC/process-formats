## Description
This describes the parameters that describe waveforms.

Format: JSON

Structure: Array of objects

Content:  This shall be a format used by the SCSN Pick Service https://scsngit.gps.caltech.edu/services/picker-spec/-/blob/main/pick-request.md

``` 
[
  {'channel': 'HNN', 
   'data': [16683, 16680, 16681, 16685, ....],
   'delta': 0.01, 
   'endtime': '2024-02-14T08:48:01.953Z', 
   'filename': 'CYP.CI.HNN..D.2024.045.084641', 
   'location': '', 
   'network': 'CI', 
   'sampling_rate': 100.0, 
   'starttime': '2024-02-14T08:46:35.103Z', 
   'station': 'CYP'},
  ....
  }
]
```

