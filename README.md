

---

# Lewiston Recreation Mapping 

## Description
During this semester, our group worked on developing a tool that would give insights into the attendance and reach of the Kennedy Pool
programs. With basic data collected, we were able to develop a Python program that would make use of API in order to get geospatial data
based on the addressess provided for pool registration. With this data we were able to generate interactive maps and diagrams in order to 
show what areas and groups were being reached by the Kennedy Pool.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Functions](#functions)
- [Maps](#maps)
- [Graphs](#graphs)
- [Contributing](#contributing)


## Installation
- The project is mainly centered on the code available on the **function.ipynb** notebook. For some unkown reasons GitHub is unable to properly render the file. Doownload
  for propoer analysis of the code. 


- The project requires two shapefiles/directories in the repo: maine_census_tracts and maine_block_groups.zip
    - These files were obtained from [census.gov](https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html)
 
- The project utilizes Demographic data obstained from Social Explorer -  Social Explorer Dataset (SE), Census 2000 on 2010 Geographies, Social Explorer; U.S. Census Bureau.
  The demographic indicators used in the project include:
    - SE:T14. Race (SF3)![image](https://github.com/BatesDCS23-24/City_of_Lewiston_GroupB/assets/107200037/f1f7d35d-446c-4a70-b132-9d513f041686)
    - SE:T57. School Dropout Rate for Population 16 to 19 Years![image](https://github.com/BatesDCS23-24/City_of_Lewiston_GroupB/assets/107200037/b05c5959-4f43-4fc8-b556-2cdd3108943d)
    - SE:T67. Employment Status for Total Population 16 Years and Over![image](https://github.com/BatesDCS23-24/City_of_Lewiston_GroupB/assets/107200037/5a165279-8c6e-4335-b95c-eeedd735e99c)
    - SE:T90. Household Income in 1999 Dollars![image](https://github.com/BatesDCS23-24/City_of_Lewiston_GroupB/assets/107200037/25375717-55c1-4793-baba-36b34742b8f4)
    - SE:T1. Total Population![image](https://github.com/BatesDCS23-24/City_of_Lewiston_GroupB/assets/107200037/507cb6df-f679-4ded-a6f5-9cf0791ce862)
    - SE:T53. School Enrollment for the Population 3 Years and Over![image](https://github.com/BatesDCS23-24/City_of_Lewiston_GroupB/assets/107200037/98ab270e-f480-4d0a-bd78-174b4fe2df0f)


## Usage
The Jupyter Notebook "functions.ipynb" is organized by functions that carry out the required tasks in order to ouput the following: 
    - directory "event_name" which contains: census_tract_map, census_blockgroup_map, gender_visits.html, grade_visits.html

The function below was constructed in order to call all other functions and generate the report. 

### activityReport(event_name, event_file, user_agent, census_shapefile_path, demographic_data_path, census_blockg_shapefile_path):
    Function that runs alls the functions above, and generates complete activity report 

    Parameters:
        - event_name (str): name of the event for which the activity report is being done
        - event_file (str): Excel activity file path
        - user_agent (str): User agent for geocoding service .
        - census_shapefile_path (str): Path to the census BLOCK GROUP shapefile.
        - demographic_data_path (str): Specific demographic data filepath , available in GitHub
        - census_blockg_shapefile_path (str): Path to the census BLOCK GROUP shapefile.

    Returns:
        - directory "event_name" which contains: census_tract_map, census_blockgroup_map, gender_visits.html, grade_visits.html

The rest of function, a description of their parameters and their returns are detailed below. 

## Functions
### `clean_data(event_file)`
- Cleans data from an Excel file.
- Parameters:
  - `event_file`: Excel Filename.
- Returns:
  - `pd.DataFrame`: Cleaned event data used throughout the notebook.

### `geocode_addresses(df, user_agent)`
- Geocodes addresses in a DataFrame and adds latitude and longitude columns.
- Parameters:
  - `df (pd.DataFrame)`: DataFrame containing addresses.
  - `user_agent (str)`: User agent for geocoding service.
- Returns:
  - `pd.DataFrame`: DataFrame with added latitude and longitude columns.

### `census_tract_map(event_name, event_coords, census_shapefile_path, demographic_data_path)`
- Creates a Folium map with census tract boundaries.
- Parameters:
  - `event_name (str)`: Name of the event.
  - `event_coords (pd.DataFrame)`: DataFrame containing pool coordinates.
  - `census_shapefile_path (str)`: Path to census TRACT shapefile.
  - `demographic_data_path (str)`: Specific demographic data filepath.
- Returns:
  - `folium.Map`: Folium map.

### `census_blockgroup_map(event_name, event_coords, census_blockg_shapefile_path)`
- Creates a Folium map with census block group boundaries.
- Parameters:
  - Similar to `census_tract_map`.

### `demographs_graphs(event_data)`
- Generates graphs showing gender and grade distribution for the visitors.
- Parameters:
  - `event_data (pd.DataFrame)`: DataFrame containing event coordinates.
- Returns:
  - Tuple containing graphs for gender and grade (`go.Figure`).

## Maps
Two maps are returned from this project: 
- census_tract_map: An interactive Folium map that incorporates the demographic data detailed in earlier sections. Utilizes Maine Census Tract shapefile boundaries.
      - Further work can be done with this visualization. The Social Explorer demographic data and Shapefile GEOID are not the same versions so they are mismatched for many boundaries. Missing data in those areas is labeled as -99
- census_blockgroup_map: An interactive Folium map that utilizes Maine Census Block Group shapefile boundaries and details the number of visitors/registrations per 1000 residents. 

## Graphs
- gender_visits.html: Interactive Plotly pie chart that shows the distribution of the gender of visitors/participants. For missing Gender observations the observation was assigned a value of "Gender Not Disclosed"
- grade_visits.html: Interactive Plotly bar chart that shows the distribution of the grade of visitors/participants. For missing Gender observations the observation was assigned a value of "No Grade"

## Contributing
This project should serve as a blueprint on how demographic data and geospatial data can be used in a community engagement setting. I urge students
in future iterations of MATH 316 to continue the development and expansion of the project. 

###### READ.ME File by Carlos Gonzalez - For inquiries contact @cgonzala



---
