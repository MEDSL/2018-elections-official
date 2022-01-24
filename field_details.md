## Fields:
This markdown describes each field in the format "Datatype - [field description]".

* When reading in data in Python, utilize "dtype" parameter of the "pd.read_csv()" command to retain proper formatting of string padded fields. The "dtype" parameter can be set equal to the "official_datatypes" dictionary provided below for every precinct file except for the individual state file for Texas. Texas provides voter turnout percentage statistics which were retained in the "votes" column, so "votes" will need to be read as float dtype for this individual file.

* official_dtypes = {'precinct':str,'office':str, 'party_detailed':str, 
		'party_simplified':str,'mode':str,'votes':int, 'county_name':str,
		'county_fips':str, 'jurisdiction_name':str,'jurisdiction_fips':str,
		'candidate':str, 'district':str, 'dataverse':str,'year':int,
		'stage':str, 'state':str, 'special':str, 'writein':str, 'state_po':str,
		'state_fips':str, 'state_cen':str, 'state_ic':str, 'date':str, 
		'readme_check':str,'magnitude':int} 

### precinct: 
string - Identifier for the smallest election reporting unit of a state. 

### office: 
string - The field which contains the name of the elected position for the race.

### party_detailed:
string - The party name for the given entry. Propositions, amendments, and other referenda are left as blank "". 

### party_simplified:
string - The party name for the given entry simplified to one of the following: DEMOCRAT, REPUBLICAN, LIBERTARIAN, OTHER, and NONPARTISAN. Propositions, amendments, and other referenda are left as blank "". 

### mode:
string - The voting mode for how the election results are reported. For results that do not offer disaggregation by mode, it will be "TOTAL". For other states that do offer the distinction, then some common entries might include: ABSENTEE, ELECTRONIC, ELECTION DAY, PROVISIONAL, ONE-STOP, etc.

### votes:
int - The numeric value of votes for a given entry.

### county_name:
string - The name of the county. 

NOTE: Will be empty for AK

### county_fips: 
string - The Census 5-digit code for a given county. Structured such that the first two digits are the state fips, and the last three digits are the county part of the fips. Each component is string padded such that if a state's or county's fip is one digit, i.e. AL, then padded such that it might take the form of "01020". 

NOTE: Will be empty for AK

NOTE: Field will often be converted to an int when reading CSV, resulting in dropping of leading zeros. Specify datatype for this field when reading file to avoid.

### jurisdiction_name:
string - The name for the jurisdiction. With the exception of New England states, Wisconsin, and Alaska, these will be the same as the county_name. For the New England states, these will be the town names. 

NOTE: For AK, will be the state senate districts (1 - 40) for jurisdictions. 

### jurisdiction_fips: 
string - The fips code for the jurisdiction, which will be the same as the county fips for every state except New England states, Wisconsin, and Alaska. Just as with county fips, these varaibles are string padded, though the fips will be 10 digits.  

NOTE: For AK, will be the state senate districts (1 - 40) for jurisdictions, taking form of 020SD 

NOTE: Field will often be converted to an int when reading CSV, resulting in dropping of leading zeros. Specify datatype for this field when reading file to avoid.

### candidate:
string - The candidate name.

NOTE: Retention elections include the name of the candidate and the yes/no option 

### district: 
string - The district identifier for the race, given that it is substate. If the district is a state legislative or U.S. House race, then the district is string padded to be 3 digits long and with zeroes, i.e. State Senate district 3 would be equal to "003". Other substate units (wards, seats, etc) with multiple level are included if given, i.e. State District Court of the Sixth district and seat C, would be "006, seat C". For candidates with state wide jurisdictions, district is "STATEWIDE". For races without district info, the field is left blank "". 

## magnitude: 
int - The number of candidates voted for in a given office-district race. The default is 1 (i.e. a single member winner take all district), with multimember districts having a magnitude matching the number of candidates who can win a race. This will be more common in local races and a select few states for their state house (i.e. NH). 

NOTE: For entries for "REGISTERED VOTERS", "OVERVOTES" or similar stats, magnitude is coded as 0. When stats are related to a specific type of office, i.e. PRESIDENT - OVERVOTES, then the office's magnitude is used. 


### dataverse:
string - The dataverse that the data will be apart of given its office. These take the form of "PRESIDENT" for US Presidential races, "SENATE" for US Senate races, "HOUSE" for US House races, "STATE" for state level executive, legislative, and judicial races. All other races are part of the "LOCAL" dataverse.

### year:
int - The year of the election.

### stage:
string - The stage of the election, can be "PRI" for primary, "GEN" for general, or "RUNOFF" for a runoff election. 

NOTE: Info from states that report recounts (ie NH) is kept as "RECOUNT". 

### state: 
string - The name of the state. 

### special:
string - An indicator for whether the election was a special election, "TRUE" if special, "FALSE" for non-special.

### writein:
string - An indicator for whether the candidate was a write in, "True" if write in, "False" otherwise. 

NOTE: "Scattered" write in votes (aggregated totals accross multiple write in candidates) are kept when given and marked "True". 

### state_po:
string - The state postal abbreviation.

### state_fips:
string - The state's fips code, 2 digit string padded.

### state_cen: 
string - The state's census code, 2 digit string padded.

### state_ic:
string - Alternative state identity code, 2 digit string padded.

### date: 
string - The date of the election, formatted as %y-%m-%d.

### readme_check:
string - An indicator for whether an issue arose with the data, "TRUE" if so, and "FALSE" otherwise. Description of issues will be documented in the README.md file of the 2020-elections-official github.
