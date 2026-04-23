# Testing

# Testing

## Test Plan

### Testing Approach

The Car Park Finder application was tested manually using a structured test plan. Tests were conducted across all three pages: `home.html`, `index.html` (list view), and `map.html` (map view), in Google Chrome (v124) on macOS by opening the files locally in the browser.

### Test Environment

| Item | Detail |
|---|---|
| Browser | Google Chrome v124 |
| Operating System | macOS Sonoma |
| Screen Resolution | 1440 x 900 |
| Network | Standard broadband (50Mbps) |
| Entry points | `home.html`, `index.html`, `map.html` opened locally |

---

### Test Cases

#### TC1 — Home Page Loads

| Field | Detail |
|---|---|
| **Test ID** | TC1 |
| **Related Requirement** | FR1 |
| **Description** | Verify the home page loads with all sections visible. |
| **Test Steps** | 1. Open `home.html`. 2. Check title, feature cards, buttons, and footer are present. |
| **Expected Result** | All sections render correctly with no broken layout. |
| **Actual Result** | Home page rendered correctly with all content visible. |
| **Status** | ✅ Pass |

#### TC2 — Home Page Navigation to List View

| Field | Detail |
|---|---|
| **Test ID** | TC2 |
| **Related Requirement** | FR1 |
| **Description** | Verify the "Find Your Car Park" button navigates to index.html. |
| **Test Steps** | 1. Open `home.html`. 2. Click "Find Your Car Park". |
| **Expected Result** | Browser navigates to `index.html`. |
| **Actual Result** | Navigated to list view successfully. |
| **Status** | ✅ Pass |

#### TC3 — List View Loads and Table Populates

| Field | Detail |
|---|---|
| **Test ID** | TC3 |
| **Related Requirement** | FR2 |
| **Description** | Verify car park data is fetched from the API and displayed as table rows on page load. |
| **Test Steps** | 1. Open `index.html`. 2. Observe loading message. 3. Wait for table to populate. |
| **Expected Result** | Loading message disappears. Table rows appear with Name, Times, Type, Spaces, Area columns. |
| **Actual Result** | Table populated with all car parks within approximately 2 seconds. |
| **Status** | ✅ Pass |

#### TC4 — Search by Car Park Name

| Field | Detail |
|---|---|
| **Test ID** | TC4 |
| **Related Requirement** | FR3, FR4 |
| **Description** | Verify searching by car park name filters the table. |
| **Test Steps** | 1. Type "Cabot" in the search bar. 2. Click Search. |
| **Expected Result** | Only rows containing "Cabot" in the name are shown. |
| **Actual Result** | Table filtered correctly. |
| **Status** | ✅ Pass |

#### TC5 — Search by Area

| Field | Detail |
|---|---|
| **Test ID** | TC5 |
| **Related Requirement** | FR3, FR4 |
| **Description** | Verify searching by area name filters the table. |
| **Test Steps** | 1. Type "Clifton" in the search bar. 2. Click Search. |
| **Expected Result** | Only car parks in Clifton area shown. |
| **Actual Result** | Filtered correctly to Clifton area results. |
| **Status** | ✅ Pass |

#### TC6 — No Results Message

| Field | Detail |
|---|---|
| **Test ID** | TC6 |
| **Related Requirement** | FR7 |
| **Description** | Verify a no-results message is shown when nothing matches. |
| **Test Steps** | 1. Type "zzzzz" in search. 2. Click Search. |
| **Expected Result** | "No results found" row displayed spanning all columns. |
| **Actual Result** | No results row displayed correctly. |
| **Status** | ✅ Pass |

#### TC7 — Filter: Multi Storey

| Field | Detail |
|---|---|
| **Test ID** | TC7 |
| **Related Requirement** | FR5 |
| **Description** | Verify Multi Storey checkbox filters to MSCP car parks. |
| **Test Steps** | 1. Tick "Multi Storey" checkbox. |
| **Expected Result** | Only MSCP car parks shown. Table updates immediately. |
| **Actual Result** | Filtered correctly on checkbox change. |
| **Status** | ✅ Pass |

#### TC8 — Filter: Surface

| Field | Detail |
|---|---|
| **Test ID** | TC8 |
| **Related Requirement** | FR5 |
| **Description** | Verify Surface checkbox filters to surface car parks. |
| **Test Steps** | 1. Tick "Surface" checkbox. |
| **Expected Result** | Only surface car parks shown. |
| **Actual Result** | Filtered correctly. |
| **Status** | ✅ Pass |

#### TC9 — Filter: CCTV

| Field | Detail |
|---|---|
| **Test ID** | TC9 |
| **Related Requirement** | FR5 |
| **Description** | Verify camera checkbox filters to car parks with CCTV. |
| **Test Steps** | 1. Tick "camera" checkbox. |
| **Expected Result** | Only car parks with CCTV = "Yes" shown. |
| **Actual Result** | Filtered correctly. |
| **Status** | ✅ Pass |

#### TC10 — Combined Search and Filter

| Field | Detail |
|---|---|
| **Test ID** | TC10 |
| **Related Requirement** | FR3, FR5 |
| **Description** | Verify search and filter work simultaneously. |
| **Test Steps** | 1. Type "Bristol". 2. Tick "Surface". 3. Click Search. |
| **Expected Result** | Only Surface car parks matching "Bristol" shown. |
| **Actual Result** | Combined filtering worked correctly. |
| **Status** | ✅ Pass |

#### TC11 — View All Results (List View)

| Field | Detail |
|---|---|
| **Test ID** | TC11 |
| **Related Requirement** | FR10 |
| **Description** | Verify View All Results clears search and filters and shows all car parks. |
| **Test Steps** | 1. Apply a search and filter. 2. Click "View All Results". |
| **Expected Result** | Search cleared, checkboxes unchecked, all car parks shown. |
| **Actual Result** | Reset worked correctly. |
| **Status** | ✅ Pass |

#### TC12 — Map View Loads with Pins

| Field | Detail |
|---|---|
| **Test ID** | TC12 |
| **Related Requirement** | FR8 |
| **Description** | Verify map.html loads the Leaflet map and plots car park pins. |
| **Test Steps** | 1. Open `map.html`. 2. Wait for loading to complete. 3. Observe map. |
| **Expected Result** | OpenStreetMap renders centred on Bristol. Car park pins visible. |
| **Actual Result** | Map and pins loaded correctly. |
| **Status** | ✅ Pass |

#### TC13 — Map Popup on Pin Click

| Field | Detail |
|---|---|
| **Test ID** | TC13 |
| **Related Requirement** | FR8 |
| **Description** | Verify clicking a map pin shows the car park name in a popup. |
| **Test Steps** | 1. Click any pin on the map. |
| **Expected Result** | Popup appears showing the car park name. |
| **Actual Result** | Popup displayed correctly. |
| **Status** | ✅ Pass |

#### TC14 — Map Search by Name

| Field | Detail |
|---|---|
| **Test ID** | TC14 |
| **Related Requirement** | FR3, FR8 |
| **Description** | Verify searching by name on the map hides non-matching pins. |
| **Test Steps** | 1. Type "Cabot" in search. 2. Click Search. |
| **Expected Result** | Only pins for car parks matching "Cabot" remain on map. |
| **Actual Result** | Non-matching pins removed correctly. |
| **Status** | ✅ Pass |

#### TC15 — Navigation Between List and Map Views

| Field | Detail |
|---|---|
| **Test ID** | TC15 |
| **Related Requirement** | FR1 |
| **Description** | Verify the Map View / List View sidebar links navigate correctly. |
| **Test Steps** | 1. On index.html click "Map View". 2. On map.html click "List View". |
| **Expected Result** | Navigation works in both directions. |
| **Actual Result** | Both links navigated correctly. |
| **Status** | ✅ Pass |

---

## Requirements Traceability Matrix

| Use-Case ID | Requirement ID | Test Case ID | Description | Status |
|---|---|---|---|---|
| UC1 | FR1 | TC1, TC2 | Home page loads and navigates to list view | ✅ Pass |
| UC1 | FR2 | TC3 | API data fetched and rendered as table on load | ✅ Pass |
| UC1 | FR3 | TC4, TC5 | Search by name and area filters table | ✅ Pass |
| UC1 | FR4 | TC4, TC5 | Results update on Search button click | ✅ Pass |
| UC2 | FR5 | TC7, TC8, TC9 | Filter checkboxes filter by type and CCTV | ✅ Pass |
| UC2 | FR6 | TC10 | Search and multiple filters work simultaneously | ✅ Pass |
| UC1 | FR7 | TC6 | No results message shown when nothing matches | ✅ Pass |
| UC3 | FR8 | TC12, TC13, TC14 | Map loads, shows pins, filters by search | ✅ Pass |
| UC4 | FR10 | TC11 | View All Results resets search and filters | ✅ Pass |
| — | FR1 | TC15 | Navigation between list and map views works | ✅ Pass |













## Test Plan
TODO: Describe any manual and automated (unit) tests. Uniquely identify each test case. Include prerequisites and test data.

Test Runs
TODO: For each test described above, indicate the current status. 
Create a requirements traceability matrix to validate the completeness of the product.

| Use-Case ID | Requirement ID | Test Case | Status |
| ----------- | -------------- | --------- | ------ |

TODO: Add rows for each test, current status is eg. pass/fail
