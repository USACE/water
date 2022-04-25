# Baseline format
The base line of all interchange format is a follows below. The general intend is to
make it relatively easy to map to either a standard message queue (OpenWire,AQMP,STOMP,MQTT) components
or HTTP without a major shift in thinking.

## format

```ebnf
headers = source, content-type, on-behalf-of, type, {header}
data-start = '= start ='
data = {alphanumeric}
data-end = '= end ='

(* which component push this data into the system *)
source = 'Source', ':', [space], [alphanumeric], eol

(* what the data is. could be application/json text/plain or more specific. or url for larger data. *)
content-type = 'Content-Type', ':', [space], [alphanumeric]

(* USACE district office, project, command, etc *)
on-behalf-of: 'on-behalf-of',':', [space], [alphanumeric], eol

type = 'Type',':', [space], 'action' | 'data' | 'request', eol

header = alpha | '_' | '-', ':', [space], {alphanumeric}, eol

eol = '\n'
space = ' ' | '\t'
alphanumeric = alpha | digit
alpha = (* the letters *)
digit = (* the numbers *)
```


# Required Headers

The specifically named headers above can be used by various consumers to avoid processing data they don't care about or to sort out
where to put information.


# A URI

A URI should be defined in addition to this specification so that clients can request information without having to know which 
component will serve them.

## An example using CWMS timeseries IDs

```
Given the time series: Alder Springs.Precip-Inc.Inst.15Minutes.0.raw for SPK

cwms-timeseries://SPK/Alder Springs.Precip-Inc.Inst.15Minutes.0.raw?start=P-3D,end=P,units=mm

we have
scheme://<office>/<full identifier>?<start date>,<end date>, <units>

```

The principal behind the idea is to provide enough information in a human readable form the any given service can know what 
the requestor wants.