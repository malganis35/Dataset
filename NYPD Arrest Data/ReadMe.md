# Description

### NYPD Arrest Data (Year To Date)

- This month we are analyzing NYPD Arrest Data!
- Can you explore the nature of police enforcement activity.
- [Acknowledgment : NYC Open Data](https://data.cityofnewyork.us/Public-Safety/NYPD-Arrest-Data-Year-to-Date-/uip8-fykc)





# Data Dictionnary



| Column Name              | Description                                                  | Type        |      |
| ------------------------ | ------------------------------------------------------------ | ----------- | ---- |
| ARREST_KEY               | Randomly generated persistent ID for each arrest             | Plain Text  |      |
| ARREST_DATE              | Exact date of arrest for the reported event                  | Date & Time |      |
| PD_CD                    | Three digit internal classification code (more granular than Key Code) | Number      |      |
| PD_DESC                  | Description of internal classification corresponding with PD code (more granular than Offense Description) | Plain Text  |      |
| KY_CD                    | Three digit internal classification code (more general category than PD code) | Number      |      |
| OFNS_DESC                | Description of internal classification corresponding with KY code (more general category than PD description) | Plain Text  |      |
| LAW_CODE                 | Law code charges corresponding to the NYS Penal Law, VTL and other various local laws | Plain Text  |      |
| LAW_CAT_CD               | Level of offense: felony, misdemeanor, violation             | Plain Text  |      |
| ARREST_BORO              | Borough of arrest. B(Bronx), S(Staten Island), K(Brooklyn), M(Manhattan), Q(Queens) | Plain Text  |      |
| ARREST_PRECINCT          | Precinct where the arrest occurred                           | Number      |      |
| JURISDICTION_CODE        | Jurisdiction responsible for arrest. Jurisdiction codes 0(Patrol), 1(Transit) and 2(Housing) represent NYPD whilst codes 3 and more represent non NYPD jurisdictions | Number      |      |
| AGE_GROUP                | Perpetrator’s age within a category                          | Plain Text  |      |
| PERP_SEX                 | Perpetrator’s sex description                                | Plain Text  |      |
| PERP_RACE                | Perpetrator’s race description                               | Plain Text  |      |
| X_COORD_CD               | Midblock X-coordinate for New York State Plane Coordinate System, Long Island Zone, NAD 83, units feet (FIPS 3104) | Number      |      |
| Y_COORD_CD               | Midblock Y-coordinate for New York State Plane Coordinate System, Long Island Zone, NAD 83, units feet (FIPS 3104) | Number      |      |
| Latitude                 | Latitude coordinate for Global Coordinate System, WGS 1984, decimal degrees (EPSG 4326) | Number      |      |
| Longitude                | Longitude coordinate for Global Coordinate System, WGS 1984, decimal degrees (EPSG 4326) | Number      |      |
| New Georeferenced Column |                                                              | Point       |      |
