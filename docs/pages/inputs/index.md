# Model Inputs

This section describes the data inputs used to build the Boston Regional STOPS model.

---

## Modeling Area and Approach

The model's geographic coverage includes Massachusetts, Rhode Island, and New Hampshire. STOPS only analyzes zones whose centroids fall within 25 miles of an active transit stop. The model reflects average weekday ridership in **Fall 2024**.



---

## Summary of Input Files

<html lang="en">
<body_mk_table>
<div class="table-title">Summary of Input Files</div>
<table class="table_autoWidth">
    <thead>
        <tr>
            <th>Input File/Folder Name</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><strong>Files in the "Districts" folder</strong></td>
            <td></td>
        </tr>
        <tr>
            <td>A2_DistrictZone.shp</td>
            <td>Contains the district definitions.</td>
        </tr>
        <tr>
            <td><strong>Files in the "Inputs" folder</strong></td>
            <td></td>
        </tr>
        <tr>
            <td>A225_D00.shp, A233_D00.shp, A244_D00.shp</td>
            <td>2012-2016 ACS zonal shape files for MA, NH, and RI.</td>
        </tr>
        <tr>
            <td>censusblocks_MA.shp, ..._NH.shp, ..._RI.shp</td>
            <td>Census block shape files for MA, NH, and RI.</td>
        </tr>
        <tr>
            <td>MA_ctpp1_t030_t046.ac2, etc.</td>
            <td>2012-2016 ACS Part 1, 2, and 3 files for MA, NH, and RI.</td>
        </tr>
        <tr>
            <td>MPO1126TAZPopEmp.shp</td>
            <td>TAZ shape file with population and employment for all analysis years.</td>
        </tr>
        <tr>
            <td>STOPS_PATH_Auto_skim.csv</td>
            <td>Zone-to-zone AM peak period auto travel times and distances.</td>
        </tr>
        <tr>
            <td>BATA, CATA, MBTA, MVRTA, MWRTA</td>
            <td>Folders containing the Fall 2024 GTFS files for each transit agency.</td>
        </tr>
        <tr>
            <td>MBTA50</td>
            <td>Folder containing the 2050 GTFS files for MBTA.</td>
        </tr>
        <tr>
            <td>AirPassengerTrips_Transit.csv</td>
            <td>Zone-to-zone linked transit trips for air passengers.</td>
        </tr>
        <tr>
            <td>STOPSStations.shp</td>
            <td>Station shape file with stop locations, boardings, and other attributes.</td>
        </tr>
        <tr>
            <td>route_counts.txt</td>
            <td>Route counts file with average weekday boardings by route.</td>
        </tr>
        <tr>
            <td>WalkLinks.shp</td>
            <td>Walk links shape file for the pedestrian network.</td>
        </tr>
        <tr>
            <td>STOPS_Fare_Structure.ctl</td>
            <td>Fare structure file defining boarding and transfer costs.</td>
        </tr>
        <tr>
            <td><strong>Control files in the root folder</strong></td>
            <td></td>
        </tr>
        <tr>
            <td>Boston_2024.ctl</td>
            <td>STOPS main control file for the 2024 calibration scenario.</td>
        </tr>
        <tr>
            <td>Boston_2050.ctl</td>
            <td>STOPS main control file for the 2050 horizon year scenario.</td>
        </tr>
    </tbody>
</table>
</body_mk_table>
</html>

---

## Existing Ridership Data

The model is calibrated to a regional weekday unlinked transit trip target of **887,322 boardings**. This data is based on Fall 2024 ridership information from the MBTA, National Transit Database (NTD), and other sources.

<html lang="en">
<body_mk_table>
<div class="table-title">Average Weekday Unlinked Transit Trips in Fall 2024</div>
<table class="table_autoWidth">
    <thead>
        <tr>
            <th>Agency</th>
            <th>Mode</th>
            <th>Average Weekday Boardings</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>MBTA</td>
            <td>Commuter Rail</td>
            <td>111,755</td>
        </tr>
        <tr>
            <td>MBTA</td>
            <td>Ferry</td>
            <td>5,411</td>
        </tr>
        <tr>
            <td>MBTA</td>
            <td>Heavy Rail</td>
            <td>296,977</td>
        </tr>
        <tr>
            <td>MBTA</td>
            <td>Light Rail (including Mattapan Line)</td>
            <td>117,899</td>
        </tr>
        <tr>
            <td>MBTA</td>
            <td>Bus</td>
            <td>332,671</td>
        </tr>
        <tr>
            <td>BATA</td>
            <td>Bus</td>
            <td>12,044</td>
        </tr>
        <tr>
            <td>CATA</td>
            <td>Bus</td>
            <td>633</td>
        </tr>
        <tr>
            <td>MVRTA</td>
            <td>Bus</td>
            <td>7,464</td>
        </tr>
        <tr>
            <td>MWRTA</td>
            <td>Bus</td>
            <td>2,470</td>
        </tr>
        <tr>
            <td><strong>Regional Total</strong></td>
            <td></td>
            <td><strong>887,322</strong></td>
        </tr>
    </tbody>
</table>
</body_mk_table>
</html>