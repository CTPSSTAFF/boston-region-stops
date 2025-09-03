# Workflow

This section covers the primary workflows for using the model, from defining scenarios and applying it to a project, to understanding its calibration.

---

## Model Application

### Regional vs. Corridor Calibration
!!! warning "Important"
    **Regional calibration does not guarantee corridor-level accuracy.** Before forecasting, you **must** review model outputs for your specific corridor and adjust inputs as needed to better reflect observed local conditions. This review should be done with the STOPS group calibration setting turned **off** (`00-None Selected`).

### Modifying Inputs for a Project
* **Define Forecast Years**: In the STOPS menu, define new forecast years and link them to the appropriate population and employment fields in `MPO0000TAZPopEmp.shp`. You may also need to provide updated highway skims in `STOPS_PATH_Auto_skim.csv`.
    
* **Update Transit Network (GTFS)**: For new scenarios, duplicate and rename GTFS folders. Update the STOPS parameter file to point to the new folders. Ensure `route_type` values are consistent and code new Park-and-Ride lots in `pnr.txt`.
    
* **Update Station Shapefile (`STOPSStations.shp`)**: Add new project stations and set their `NEWSTATION` field to `1`. Apply consistent access penalties for new stations on existing lines (e.g., a 3-minute walk penalty for new Green Line stations).
* **Update Districts**: For corridor projects, refine the district file with smaller districts and update the **station group** definitions in `STOPSStations.shp` to match.

---

## Example Application: Blue Hill Avenue

This example adapted the model for the Blue Hill Avenue corridor, which has three fare-free bus routes.
1.  **Isolate Fare-Free Routes**: Routes #23, #28, and #29 were moved into a new, separate GTFS folder.
2.  **Update Parameter and Fare Files**: The new GTFS folder was registered with a unique suffix (`F`). The fare file was modified to set boarding fares to zero for `F` routes.
    
3.  **Refine District Definitions**: District boundaries were updated for more detailed resolution.
    

---

## Model Calibration Details

The model was calibrated by adjusting parameters and input files.

### Calibration Adjustments
* **Transfer Penalty**: Reduced to 3.0 minutes.
* **KNR Transit Setting**: Reduced to 0.20 to lower the share of Kiss-and-Ride trips.
* **Auto Time Adjustment**: A constant (+8.2 min) and factor (0.70) were applied to auto times.
* **Value of Time (VOT)**: Increased to $18/hour.
* **ACS Zones**: Large ACS zones were split to better represent walk access.
    
* **Station Penalties**: A 3-minute walk access penalty was added to Green Line branch stations and inner Commuter Rail stations to improve ridership distribution.