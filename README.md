# Mapping Australia's Fire Lookouts

## Project Purpose

This project aims to create an interactive web map visualizing the locations of fire lookouts across Australia, including both currently operational sites and historical ones that may no longer be standing. The goal is to provide a geographic perspective on the data compiled by the Fire Lookouts Downunder website.

## Data Source and Attribution

**Important Note:** All lookout information presented on the map originates entirely from the excellent and comprehensive website:

**[Fire Lookouts Downunder](https://www.firelookoutsdownunder.com/)**

Full credit and ownership of the underlying data belong to the website owner. This project simply provides a visual representation of a subset of that data and claims no ownership over the information itself. Permission was kindly granted by the website owner to use the data for this mapping project. Please visit the original site for the most detailed and up-to-date information.

## Process

The map was created through the following steps:

1.  **Data Gathering:** Lookout data was scraped from [Fire Lookouts Downunder](https://www.firelookoutsdownunder.com/) using a Python script (with the owner's consent).
2.  **Coordinate Parsing & Cleaning:** The location information provided for each lookout was processed using Python (`pandas` library). This involved identifying various formats:
    *   Standard Latitude/Longitude (Decimal Degrees).
    *   MGA (Map Grid of Australia) Eastings and Northings.
    *   6-figure map grid references (common in Victoria).
    *   Missing or incomplete data.
3.  **Coordinate Conversion:** Where coordinates were provided as MGA Eastings/Northings (common in Queensland), they were converted to Latitude/Longitude using the `pyproj` library. MGA zones were estimated based on the 'Previous District' (town name) listed for each lookout to improve accuracy.
4.  **Data Aggregation:** Processed data from different state sheets was combined into a single dataset, aligning columns where necessary.
5.  **Map Generation:** An interactive HTML map was generated using the Python `folium` library. This map includes only those lookouts for which coordinates could be successfully processed into Latitude/Longitude (either directly available or converted). Popups for each marker display the available data fields and images sourced from the website.

## Current Status

The map currently displays lookouts where coordinates were provided in Decimal Degree format or could be converted from MGA Eastings/Northings.

Lookouts listed with 6-figure grid references (primarily in Victoria) have been identified but are **not yet included** on the map, as converting these requires manual lookup or more complex georeferencing.

## Viewing the Map

The current version of the interactive map can be viewed here:

**[>>> View the Fire Lookout Map <<<]([https://stertafed.github.io/fire-lookout-map/)**

## Future Enhancements

*   Manually converting or finding coordinates for lookouts currently listed with 6-figure grid references to add them to the map.
*   Regularly updating the data by re-running the scraping and processing scripts (respecting the source website's resources).
*   Potentially exploring alternative mapping libraries or UI designs for improved presentation.

## Acknowledgements

Huge thanks again to the creator and maintainer of [Fire Lookouts Downunder](https://www.firelookoutsdownunder.com/) for their incredible work compiling this information and for allowing its use in this project.

## License

The Python code used in this repository for scraping, processing, and mapping is made available under the MIT License.

Please note that this license applies **only** to the code itself and **not** to the underlying lookout data. The data remains the property of [Fire Lookouts Downunder](https://www.firelookoutsdownunder.com/).
