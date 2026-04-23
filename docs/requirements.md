# Requirements

## User Needs

### User stories
- As a car driver, i would want to serach for car parks by name or location to find quick and secure parking in bristol.
- As a car driver, i want to find car parks in bristol by a type of filter so i can find the correct parking for my demands.
- As a car driver, i want to see how many avaliable spaces the car park has so that i can choose one with a good amount of parking spots.
- As a car driver, i want to locate a car park that minimises my walking to my actual destinanation.
- As a car driver, i want to locate the operating times of a car park so i can determine if the hours the car park is opened resonates with the times that the car is park.
- As a car driver, i want to know whether a car park has CCTV to ease any suspicions and help me feel secure in my car being kept safe.
- As a car driver, i want to see all car parks in bristol without filters so i can choose from all available options. 

### Actors
| Actor | Description |
| ----- | ----------- |
| User (Driver) | The main customer that uses the web application. A motorist driving in or around Bristol who needs to find a car park to leave their vehicle for an amount of time. They interact with the web interface via a desktop or mobile browser. |
| Bristol Open Data API | An outside platform that delivers car park data. Not a end user but interacts with the platform by responding to HTTP requests with JSON data. |
| Browser Geolocation API | An integrated browser service that retrives the user's live location when permission is granted.

### Use Cases

| UC1 | Search for a Car Park by Name or Area | 
| -------------------------------------- | ------------------- |
| **Description** | The users puts in a name or area into the search bar to filter the displayed car parks in real time.  |
| **Actors** | user |
| **Assumptions** | Car park information has been loaded from the API and loaded on the page. |
| **Steps** | 1. The user loads the web application. 2.The data from Bristol Open Data API. 3.User types a car park name (e.g "NCP") or area ("Clifton") into the search option. 4.The results list filters in actual time to display the right type of car park.  |
| **Variations** | If there are no matches to a car park, a "NO CAR PARKS FOUND" message is shown |
| **Non-functional** | Filtering search must update results within 100ms of each key stroke.  |
| **Issues** | None |

| UC2 | Filter Car Parks By Type | 
| -------------------------------------- | ------------------- |
| **Description** | The user chooses one or more checkboxes to filter the car parks by which type.|
| **Actors** | User |
| **Assumptions** | Car park data has loaded. The FACILITY_TYPE field is written in the API response. |
| **Steps** | 1. User choooses one or more  heckbozes out of the options. . 2. The results grid changes immediately to present only relavent car parks to that section. 3. Flters can be conjoined with the search bar.|
| **Variations** | If no checkboxes are selected, all car parks are shown. If no results fit the enquiry, a no results message is shown. |
| **Non-functional** | Filter must work ithout page reload.  |
| **Issues** | FACILITY_TYPE values in the API may not match filter labels: Partial string matching. |

| UC3 | Find Nearest Car Park | 
| -------------------------------------- | ------------------- |
| **Description** | The user selects "Find Nearest" button to order the car parks by proximity to their location.   |
| **Actors** | user & browser geoloaction API. |
| **Assumptions** | The users browser allows gelocation and the car park data loads.  |
| **Steps** | 1. User clicks the "Find Nearest" button. 2.Browser requests geolocation permission from the user. 3.User grants permission. 4. The web app gets the information(latitude & longitude) 5. Car parks are sorted by approximate distance from the users location. 6. Nearest car parks are displayed. |
| **Variations** | The user doesnt accept the location permission pop up and a message leyts the user know that their current location could not be retrieved. IF ghe dta hasnt loaded, the user would have to wait. |
| **Non-functional** | Geo,octaion requests must finish within the browsrers standard time out.   |
| **Issues** | The accuracy of the geolocation dpends on the users device and the browsre they might use. |

| UC4 | View All Carparks | 
| -------------------------------------- | ------------------- |
| **Description** | The users uses "VIEW ALL RESULTS" to reset any filters that are currently active and show a full display of the car park dataset.  |
| **Actors** | user |
| **Assumptions** | Car park has rendered |
| **Steps** | 1. User selects the "VIEW ALL RESULTS" button. 2. All active filyters and search terms are ignored. 3.The list of car parks is rendered into the grid of results. |
| **Variations** | NONE |
| **Non-functional** | All results must load within 500ms  |
| **Issues** | None |

| UC5 | View Car Park Details | 
| -------------------------------------- | ------------------- |
| **Description** | The user finds and looks at a car park to find information including spaces, hours of operation & CCTV ect. |
| **Actors** | user |
| **Assumptions** | Car park information has been loaded and the user can see results
| **Steps** | 1. Car Parks in Bristol are displayed as cards after seraching & filtering. 2. Each card shows the relevant information. |
| **Variations** | When fields are null the responses are not displayed. |
| **Non-functional** |  Cards have to be suitible to read on obile and desktop screens.  |
| **Issues** | Car paeks have incomplete data in the Open Data API. |

USER CASE DIAGRAM
<img width="1156" height="350" alt="Screenshot 2026-04-23 at 10 57 11" src="https://github.com/user-attachments/assets/d689656d-ae0e-4ad6-86dc-cab1a6474075" />

## Software Requirements Specification
### Functional requirements
### Functional Requirements

| ID | Requirement |
| -- | ----------- |
| **FR1** | The system shall fetch car park data from the Bristol Open Data REST API on page load. |
| **FR2** | The system shall display car park results as individual cards showing name, area, type, spaces, CCTV status, operator, operating hours, and number of levels. |
| **FR3** | The system shall allow the user to search car parks by name or area using a text input field. |
| **FR4** | The system shall filter results in real time as the user types in the search field. |
| **FR5** | The system shall allow the user to filter car parks by facility type using checkboxes (Multi Storey, Surface, On Street, Park & Ride). |
| **FR6** | The system shall allow multiple filters to be active simultaneously. |
| **FR7** | The system shall display a "no results" message when no car parks match the active search or filter criteria. |
| **FR8** | The system shall provide a "Find Nearest" function that uses the browser Geolocation API to sort car parks by proximity to the user's location. |
| **FR9** | The system shall display the top 10 nearest car parks when the Find Nearest function is used. |
| **FR10** | The system shall provide a "View All Results" button that resets all filters and displays the complete dataset. |
| **FR11** | The system shall display a loading or error status message to inform the user of the data fetch state. |

### Non-Functional Requirements
### Non-Functional Requirements

| ID | Requirement |
| -- | ----------- |
| **NFR1** | The application shall be written in valid HTML5, verified using the W3C HTML Validator. |
| **NFR2** | The application shall load and display car park data within 5 seconds on a standard broadband connection. |
| **NFR3** | Search and filter results shall update within 100ms of user input. |
| **NFR4** | The application shall be usable on both desktop and mobile screen sizes (responsive layout). |
| **NFR5** | The application shall not require any server-side code, backend, or database — all logic shall run client-side. |
| **NFR6** | The application shall handle API errors gracefully and display a user-friendly error message rather than crashing. |
| **NFR7** | Null or missing fields in the API response shall be handled silently — missing data shall not be displayed rather than showing "null" or "undefined". |
| **NFR8** | The codebase shall follow consistent naming conventions and be structured to a readable standard. |
