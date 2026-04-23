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

TODO:
## Project Structure

| File | Role |
| ---- | ---- |
| **home.html** | Landing page. Introduces the application and links to the list view. |
| **index.html** | List view. Fetches car park data on load via the Bristol Open Data API. Displays results in a scrollable HTML table. Supports search by name/area and filtering by type and CCTV via checkboxes. |
| **map.html** | Map view. Fetches the same data and plots each car park as a Leaflet marker on an OpenStreetMap base. Supports the same search and filter logic by toggling marker visibility. |
| **stylesheet.css** | Shared stylesheet. Defines the header, heading layout, sidebar, search bar, table, loading spinner, map container, and View All Results button. |

## JSLint Warning Report

Each JavaScript module was run through JSLint to assess code quality. The results are shown below.

| Module | Warnings | Warning Types |
| ------ | -------- | ------------- |
| **index.html** | 14 | Unexpected 'for', Unexpected 'let', Line longer than 80 characters (×7), Unexpected trailing space (×4) |
| **map.html** | 16 | Unexpected 'for', Unexpected 'let', Use double quotes not single quotes (×3), Line longer than 80 characters (×3), Unexpected trailing space (×7), Expected ';' saw 'let', Expected property 'attribution' ordered before 'maxZoom' |

The warnings in both modules are predominantly stylistic — trailing whitespace from indentation, lines exceeding 80 characters due to the length of the API URL, and JSLint's preference for `while` loops over `for` loops with `let`. These do not affect the functionality of the application. The single/double quote warnings in `map.html` relate to Leaflet.js configuration strings. No logical or functional errors were reported.

## Version History

| Version | Changes |
| ------- | ------- |
| **v0.1** | Initial project structure. HTML skeleton with heading, sidebar, placeholder results. |
| **v0.2** | CSS layout implemented — sidebar, heading, search bar, horizontal rule divider. |
| **v0.3** | `query()` and `outputTable()` added to `index.html`. API fetch working, data rendered as table rows on page load using `window.onload`. |
| **v0.4** | `carsearchbar()` implemented. Search by name and area working on Search button click. |
| **v0.5** | Filter checkboxes added with `onchange`. Filters for Multi Storey, Surface, Underground, and CCTV. Combined search and filter logic using boolean flags. No-results row added. |
| **v0.6** | Loading spinner added. View All Results button implemented to reset search and filters. Map View link added to sidebar. |
| **v0.7** | `map.html` created. Leaflet.js integrated. Car parks plotted as markers with name popup. `markersearchbar()` implemented to toggle marker visibility based on search and filters. |
| **v0.8** | `home.html` created. Hero section, feature cards, about section, and footer. Navigation between all three pages via links and buttons. |
| **v1.0** | Final version submitted. All pages link correctly. Shared stylesheet applied across all pages. |


Bristol Open Data API
Endpoint
GET https://maps2.bristol.gov.uk/server2/rest/services/ext/ll_transport/MapServer/5/query

## Query Parameters

| Parameter | Value | Description |
| --------- | ----- | ----------- |
| `where` | `1=1` | Returns all records |
| `outFields` | `NAME,NUMBER_LEVELS,AREA_NAME,OPERATOR_NAME,SPACES,OPERATING_TIMES,TYPE_DESCRIPTION,CCTV` | Fields to include |
| `outSR` | `4326` | Spatial reference — WGS84 lat/lng |
| `f` | `json` | Response format |

## Software Architecture

The web application uses a three-page client-side architecture. All the pages share the same stylesheet. Index.html & Map.html separately fetch from the same Open data website. 

## Key JavaScript Functions

### index.html

| Function | Description |
| -------- | ----------- |
| **`query()`** | Called on page load via `window.onload`. Shows loading spinner, fetches API data using `fetch()`, passes result to `outputTable()`, hides spinner in `.finally()`. |
| **`outputTable(stuff)`** | Stores features in `CarparkData` array. Iterates through features and appends a `<tr>` row to `#resultstble` for each car park, displaying NAME, OPERATING_TIMES, TYPE_DESCRIPTION, SPACES, AREA_NAME. |
| **`carsearchbar()`** | Reads search input and checkbox states for multi, surface, onstreet, camera. Clears table and re-renders only rows matching both search and filter criteria. Shows "No results found" row if count is zero. Triggered by Search button and all checkbox `onchange` events. |

### map.html

| Function | Description |
| -------- | ----------- |
| **`query()`** | Same as index.html — called inside `window.onload` after map initialisation. Fetches API data and passes to `outputTable()`. |
| **`outputTable(stuff)`** | Stores features in `CarparkData`. For each feature, creates a Leaflet marker at coordinates from `geometry.x` and `geometry.y`, stores attributes as `marker.data`, adds to map, and binds a popup showing the car park name. |
| **`markersearchbar()`** | Reads search input and checkbox states. Removes all markers from the map then re-adds only those matching the search and filter criteria. Triggered by the Search button. |

{
  "features": [
    {
      "attributes": {
        "NAME": "Cabot Circus",
        "AREA_NAME": "City Centre",
        "TYPE_DESCRIPTION": "Multi Storey",
        "NUMBER_LEVELS": "MSCP",
        "SPACES": 2200,
        "OPERATOR_NAME": "Bristol City Council",
        "OPERATING_TIMES": "24 hours",
        "CCTV": "Yes"
      },
      "geometry": {
        "x": -2.5823,
        "y": 51.4567
      }
    }
  ]
}

![Insert your component Diagram here](images/component.png)

## Bristol Open Data API
TODO: Document each query to Bristol Open Data

![UML Class diagrams representing JSON query results](images/class1.png)
TODO: Repeat as necessary

# User guide
TODO: Explain how each use-case works by providing step-by-step screenshots for each use-case. This should be based on a tested scenario.
