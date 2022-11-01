# Modernization

## Vision

> Access to Water is not a website. Access to Water is not a database.

Access to Water _is_ a collection of activities and technical capabilities focused on sharing water resource data with the public. This includes support for geospatial (mapping) links to data, models, and analytic methods ([WRDA 2007](/legislation?id=wrda-2007-november-2007)). These activities are to be accomplished within current appropriations (funding).

Modern data sharing inherently employs a wide range of very tangible technical capabilities, including websites, data storage solutions, data aggregation pipelines (ETL), data services, automation, data visualization, etc. Effective data sharing also requires less tangible coordination and integration efforts to address administrative, organizational, and technical silos. Access to Water activities will necessarily include both categories.

Because the objective is data sharing, the end goal and marker of success of the modernization effort is likewise improved data sharing, not _a new website_. An updated website will, however, be a key technical component and the primary technical entrypoint for the public.

The original Access to Water website and API services focus primarily on sharing the [Corps Water Management System (CWMS)](https://www.hec.usace.army.mil/cwms/) dataset. This dataset contains the location of US Army Corps of Engineers dams across the United states, their physical characteristics, and associated timeseries information about current and past conditions (water level, flow, nearby weather). Updating the means of sharing the CWMS dataset will be the starting point for modernization efforts to ensure feature and data parity. The modernized architecture will support storing and serving a broader scope of datasets in a modular way. After modernization, Access to Water data storage and RESTful data services will not be tightly-coupled with the existing CWMS database or technical architecture, allowing flexibility to incorporate and integrate other water resource datasets in a modular way.

## FY23 Objectives

This list is a work in progress, more todo.

### APIs and Data Modeling

- [ ] Flexible, scalable API for locations
- [ ] Flexible, scalable API for timeseries
- [ ] Flexible, scalable API for documents (PDFs, etc.)
- [ ] Flexible, scalable API for paired data (rating curves, etc.)
- [ ] Design & Implement Auth Strategy
- [ ] Visualizations API (Dam Profile Chart, etc.)

### Quasi Real-Time Pipelines (ETL)

### Data Migration

### Public Website

- [ ] Site Map & Design
- [ ] Develop a strategy and direction for map canvas
- [ ] Design website landing page

### Admin Website

- [ ] Incrementally develop an admin website that will allow data managers to update and control information shared on the public website
