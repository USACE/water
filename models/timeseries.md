# Timeseries Model

The goal of the timeseries data model a to provide a simple, flexible, multi-tenant capable storage solution atop the core provider/datasource model. A timeseries consists of summary metadata that applies to a collection of one or more `time`,`value` pairs. The `timeseries` entity does not actually contain the `time`,`value` pairs, only the name of the series and the latest time and value.

> Note: Most information can be represented as timeseries. As such, this model supports storage of static data, with the flexibility to capture changes over time if necessary.

```mermaid
erDiagram
    provider {
        UUID    id        PK "NOT NULL"
        VARCHAR slug         "NOT NULL"
        VARCHAR name         "NOT NULL"
        UUID    parent_id FK "optionally support parent/child relationship"
    }
    datasource_type {
        UUID   id    PK "NOT NULL"
        VARCHAR slug    "NOT NULL"
        VARCHAR name    "NOT NULL"
        VARCHAR uri     "NOT NULL; (typically a top-level webservice url)"
    }
    datasource }o--|| provider : has
    datasource }o--|| datasource_type : has
    datasource {
        UUID    id          PK "NOT NULL"
        UUID    provider_id FK "NOT NULL"
        VARCHAR type_id     FK "NOT NULL"
    }
    timeseries }o--|| datasource : ""
    timeseries {
        UUID        id             PK "NOT NULL"
        UUID        datasource_id  FK "NOT NULL"
        VARCHAR     datasource_key    "NOT NULL"
        DOUBLE      latest_value
        TIMESTAMPTZ latest_time
    }
```
