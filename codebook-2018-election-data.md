# Codebook for 2018 Election Offical Data

The data files `senate_overall_2018`, `district_overall_2018`, `state_overall_2018`, `county_2018`, and `precinct_2018` contain official returns for elections returns in 2018. The `precinct_2018` files are incomplete but will be updated weekly until completion. Files that begin with senate_ contain data for U.S. Senate elections, files that begin with district_ contain data for U.S. House elections, and files that begin with state_ contain data for state office elections. The county and precinct datasets contains all three. Files for overall results show constituency-level returns, and where available, these are broken down into county level returns in the county files. 

The source of the data is typically each state's Secretary of State website or comparable elections division page on an official state website. (The precinct-level returns for California are obtained from the statewide redistricting database, https://statewidedatabase.org/). For Michigan, Missouri, New Jersey, Oregon, South Carolina, and Vermont, we used precinct-level returns from the OpenElections project (https://github.com/openelections). 

Returns for some states are separated by mode of voting (e.g. election day, absentee, etc.), as indicated by the `mode` variable in the dataset. For Maine in the `county_2018` file, data was drawn from precinct results, some of which could not be linked to corresponding counties. These are listed as missing values in the county variable. The county-level data in the `county_2018` file for Maine is thus incomplete.

## Variables
The variables are listed as they appear in the data file. Not all variables appear in each data file.

### year
- **Description**: election year	

------------------

### state
- **Description**: state name 

-----------------

### state_po
- **Description**: U.S. postal code state abbreviation

----------------

### state_fips
 - **Description**: State FIPS code

----------------

### state_cen
 - **Description**: U.S. Census state code

 ---------------
 
### state_ic
 - **Description**: ICPSR state code

-----------------

### county
 - **Description**: county name

-----------------

### office
- **Description**: office name

-----------------

### district
- **Description**: district number and/or name; statewide races labelled as "statewide"

-----------------

### jurisdiction
 - **Description**: in precinct file, county name (except in Alaska, where results are reported by state legislative district)

-----------------

### county
 - **Description**: county name

-----------------

### stage
- **Description**: electoral stage; always general ("gen") here

-----------------

### special
- **Description**: special election TRUE/FALSE indicator (always FALSE here, no special elections data is included)

-----------------

### rank
- **Description**: candidate rank in ranked-choice voting (only applies for Maine US House District 2 data in the `county_2018` dataset)

-----------------

### candidate
- **Description**: name of the candidate; write-in candidates/totals represented as NA's
 
-----------------

### party
- **Description**: party of the candidate (always entirely lowercase); write-in candidates/totals represented as NA's

-----------------

### writein
- **Description**: TRUE/FALSE indicator for write-in candidates/totals

-----------------

### mode
- **Description**: mode of voting; states with data that doesn't break down returns by mode are marked as "total"; other states can have modes of "absentee," "machine," "absentee mail," "absentee walk-in," "election day," "polling," "early," "one stop," and "provisional" 

-----------------

### candidatevotes 
- **Description**: votes received by this candidate for this particular party

----------------

### totalvotes
- **Description**: total number of votes cast for this election

----------------

### unofficial
- **Description**: TRUE/FALSE indicator for unofficial result (to be updated later)

----------------

### version  
- **Description**: date when this dataset was finalized

----------------

### dataverse  
- **Description**: in precinct file, whether this election corresponds to elections in the Senate ("senate"), US House ("house"), or state ("state") files, or none of these ("local")

## Notes

There are several discrepancies between the data and official results. The precinct-level results for State Senate District 18 in Florida and for State House Districts 79 and 80 (Richland County portion only) in South Carolina are missing. We are working to obtain this data. In addition, there are discrepancies between the aggregate and precinct-level results in several counties in Alabama, Missouri (see https://github.com/openelections/openelections-data-mo/issues/11), New Jersey, and Washington. Finally, note that although OpenElections has precinct-level data on statewide referenda and constitutional amendments for Missouri, it is incomplete (https://github.com/openelections/openelections-data-mo/issues/12), and we are working on gathering more comprehensive data on these contests. Please let us know by filing an "issue" if you have information on how to resolve these discrepancies or if you find additional ones. 
