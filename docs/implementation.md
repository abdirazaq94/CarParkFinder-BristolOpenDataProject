# Implementation

## Introduction
The car park finder is a client side web application made using HTML, CSS and JavaScript by using bristols open data api to find car parks locations in the City of Bristol. The application istelf is made up of a home page, a list view and a interactive map view. All logic runs client side with no backend, server or exxternal JavaScript libraries besides the maps use of leaflet.js.

The dataset used is the Bristol Car Parks layer from the Bristol City Council transport MapServer:

https://maps2.bristol.gov.uk/server2/rest/services/ext/ll_transport/MapServer/5

Fields retrieved: NAME, NUMBER_LEVELS, AREA_NAME, OPERATOR_NAME, SPACES, OPERATING_TIMES, TYPE_DESCRIPTION, CCTV
Notes on the data:

NUMBER_LEVELS is used for type-based filtering. Values in the dataset include mscp (multi-storey), surface, and u/ground (underground).
TYPE_DESCRIPTION is displayed in the results table as the human-readable type label.
The map view uses Leaflet.js loaded from a CDN (unpkg.com) and requires an internet connection.

## Project Structure

CarParkFinder-BristolOpenDataProject/
├── html/
│   ├── home.html           # Landing page — introduction and navigation
│   ├── index.html          # List view — search, filter, scrollable results table
│   ├── map.html            # Map view — interactive Leaflet map with car park pins
│   └── stylesheet.css      # Shared stylesheet used by all three pages
├── docs/
│   ├── planning.md         # Planning: business case, scope, context diagram
│   ├── requirements.md     # Requirements: user stories, use cases, SRS
│   ├── design.md           # Design: wireframes, high-fidelity mockup
│   ├── implementation.md   # Implementation: architecture, API docs, user guide
│   └── testing.md          # Testing: test plan, traceability matrix
└── readme.md               # Project overview and links to docs

TODO: Provide an outline of the project folder structure and the role of each file within it.
provide a table listing the number of jslint warnings/reports for each module.

## Software Architecture
TODO: Describe the major components of your architecture. Are any particular architectural styles being used?

![Insert your component Diagram here](images/component.png)

## Bristol Open Data API
TODO: Document each query to Bristol Open Data

![UML Class diagrams representing JSON query results](images/class1.png)
TODO: Repeat as necessary

# User guide
TODO: Explain how each use-case works by providing step-by-step screenshots for each use-case. This should be based on a tested scenario.
