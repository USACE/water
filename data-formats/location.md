# Location message

Relevant information about a location so systems can update internal information if required.

```ebnf
headers = source, content-type, on-behalf-of, type, name, {header}
data-start = '= start ='
data = json | url
data-end = '= end ='

(* which component push this data into the system *)
source = 'Source', ':', [space], [alphanumeric], eol

(* what the data is. could be application/json text/plain or more specific. or url for larger data.)
content-type = 'Content-Type', ':', [space], [alphanumeric]

(* USACE district office, project, command, etc)
on-behalf-of: 'on-behalf-of',':', [space], [alphanumeric], eol

type = 'Type',':', [space], 'action' | 'data' | 'request', eol

name = (* TODO: define valid name *)

header = alpha | '_' | '-', ':', [space], {alphanumeric}, eol

json = (* valid json data *)
url = (* URL to other data source, like say an S3 bucket containing the JSON data*)
eol = '\n'
space = ' ' | '\t'
alphanumeric = alpha | digit
alpha = (* the letters *)
digit = (* the numbers *)
```

# JSON data 
```json
{
    name: 
    office:
    lat:
    long:
    elevation:
    datum info:
    /*
        other meta data I don't feel like typing out in the intitial example
    */
}


```