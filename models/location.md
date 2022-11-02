# Location

```mermaid
erDiagram

    location }o--|| datasource : ""
    location {
        UUID        id             PK "NOT NULL"
        UUID        datasource_id  FK "NOT NULL"
        VARCHAR     code              "NOT NULL"
        VARCHAR     slug              "UNIQUE NOT NULL"
        GEOMETRY    geometry          "NOT NULL"
        REAL        state_id
        JSONB       attributes        "NOT NULL DEFAULT '{}'::jsonb"
    }
    provider {
        UUID    id         PK "NOT NULL"
        VARCHAR slug          "NOT NULL"
        VARCHAR name          "NOT NULL"
        UUID    parent_id  FK "optionally support parent/child relationship"
    }
    datatype {
        UUID   id     PK "NOT NULL"
        VARCHAR slug     "NOT NULL"
        VARCHAR name     "NOT NULL"
        VARCHAR uri      "NOT NULL; (typically a top-level webservice url)"
    }
    datasource }o--|| provider : has
    datasource }o--|| datatype : has
    datasource {
        UUID id                  PK "NOT NULL"
        UUID provider_id         FK "NOT NULL"
        UUID datatype_id  FK "NOT NULL"
    }

```

## Location.code

This captures a semi-unique value for each location within the domain of its underlying "datasource". A few examples showing how the `code` field is used are shared below:

- datatype 'usgs-site': `code` is the USGS station number, e.g. "05091500"
- datatype 'cwms-location': `code` is the CWMS Name, unique within the context of a US Army Corps of Engineers office, e.g. "Adamsville"
- datatype 'nws-site': `code` is the national weather service location identifier (nwsli), often referred to as the "handbook 5 code". e.g. "ASTM5"

## Location.attributes

The location table has a field `attributes` which supports a flexibility. Keys are allowed/denied based on the `datatype` associated with the location. This is controlled at the API layer, not by database foreign key constraints. Allowed keys are determined by the `datatype`, which is determined for a location through the `datasource_id` field. Keys that are allowed in the `attributes` field for each datatype are listed below. Allowed keys may be extended and modified in the future.

### Datatype: cwms-location

- public_name
- kind

### Datatype: nws-site

- name

### Datatype: usgs-site

- station_name
- site_type
