# Codebook for 2018 Election Offical Data

The data files `senate_overall_2018`, `district_overall_2018`, `state_overall_2018`, `senate_county_2018`, `district_county_2018`, and `state_county_2018` contain official returns for elections returns in 2018. Files that begin with senate_ contain data for U.S. Senate elections, files that begin with district_ contain data for U.S. House elections, and files that begin with state_ contain data for state office elections. Files for overall results show constituency-level returns, and where available, these are broken down into county level returns in the county files. The source of the data is each state's Secretary of State website or comparable elections division page on an official state website, except in a few cases where data comes from [The OpenElections Project](https://github.com/openelections) (see the [repository README file](https://github.com/MEDSL/2018-elections-official) for more details). For Kansas, returns come from Stephen Pettigrew and the Kansas Secretary of State office. Returns for some states are separated by mode of voting (e.g. election day, absentee, etc.), as indicated by the `mode` variable in the dataset.

## Variables
The variables are listed as they appear in the data file. 

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

### FIPS
 - **Description**: county FIPS code

-----------------

### office
- **Description**: office name

-----------------

### district
- **Description**: district number and/or name; statewide races labelled as "statewide"

-----------------

### stage
- **Description**: electoral stage; always general ("gen") here

-----------------

### special
- **Description**: special election TRUE/FALSE indicator (always FALSE here, no special elections data is included)

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
- **Description**: date when this dataset was finalize