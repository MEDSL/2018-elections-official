This README lists the dates that we finished cleaning each state's data, along with any relevant issues we encountered.

Note: When reading in data in Python, utilize "dtype" parameter of the "pd.read_csv()" command to retain proper formatting of string padded fields. The "dtype" parameter can be set equal to the "official_datatypes" dictionary provided below for every precinct file except for the individual state file for Texas. Texas provides voter turnout percentage statistics which were retained in the "votes" column, so "votes" will need to be read as float dtype for this individual file.

* official_dtypes = {'precinct':str,'office':str, 'party_detailed':str, 
		'party_simplified':str,'mode':str,'votes':int, 'county_name':str,
		'county_fips':str, 'jurisdiction_name':str,'jurisdiction_fips':str,
		'candidate':str, 'district':str, 'dataverse':str,'year':int,
		'stage':str, 'state':str, 'special':str, 'writein':str, 'state_po':str,
		'state_fips':str, 'state_cen':str, 'state_ic':str, 'date':str, 
		'readme_check':str,'magnitude':int} 

## Alabama

Updated data added 03-07-2022.

* Small, marginal discrepancies are present between the raw aggregated precinct data from the state and the official reports. These discrepancies originate only from three counties: Chilton, Dallas, and Russell, and thus only affect offices with votes from those counties. Here are the county level discrepancies for the office of governor (official vs. our precinct data):
* Ivey
	- Chilton:	11291   vs 10487
	- Dallas:	4917	vs 4542
	- Russell:	7168	vs 7166

* Maddox
	- Chilton:	2501    vs 2347
	- Dallas:	10295	vs 9968
	- Russell:	7864	vs 7861

## Alaska

Updated data added 01-24-2022. Local data not included at the moment.

## Arizona

Updated data added 03-07-2022.

## Arkansas

Updated data added 01-24-2022. Local data not included at the moment.

## California

Updated data added 01-24-2022. Local data not included at the moment.

## Colorado

Updated data added 01-24-2022.

## Connecticut

Updated data added 02-18-2022.

## Delaware

Updated data added 01-24-2022.

## District of Columbia

Updated data added 01-24-2022.

## Florida

Updated data added 03-07-2022.

* Raw data acquired from: https://www.dos.myflorida.com/elections/data-statistics/elections-data/precinct-level-election-results/

* The precinct field is a combination of the 'Precinct Polling Location' and 'Unique Precinct Identifier', separated by an underscore "_"

* Results for Miami-Dade were sourced separately, directly from the Miami-Dade county (official results contained anomolous duplicates). The format of the precinct field is therefore different from the other counties. 
* Very small, marginal discrepancies were discovered when comparing aggregate precinct results to the certified county results in the following offices: ['GOVERNOR', 'US SENATE', 'COMMISSIONER OF AGRICULTURE']. 


## Georgia

Updated data added 01-24-2022. Local data not included at the moment.

## Hawaii

Updated data added 01-24-2022.

## Idaho

Updated data added 01-24-2022. Local data not included at the moment.

## Illinois

Updated data added 02-18-2022.

## Indiana

Data added 11-01-2022.

* A precinct value of "Total" in the raw data has an inconsistent meaning, and no simple rule was successful in accounting for these rows. We have chosen to drop them, because aggregations of votes double-counts votes, and this was indeed the case in some counties. But in other cases, with no clear regularity, "Total" did not seem to refer to county-level aggregations. In particular,  when dropping these rows, US HOUSE races became substantially more accurate *except* district 6, which became much less accurate, while JOE DONNELLY's vote total in the US SENATE race went from being almost exactly correct to the discrepancy levels shown below. We choose to drop these rows because artifical aggregation precincts should in general not be retained, but users who wish to understand the problem better and potentially vary the decision are encouraged to access the replication code for this state.

* We find the following discrepancies in US HOUSE vote totals (in the format: [district]. [ours] vs. [official])\
&emsp;	2. JACKIE WALORSKI, 125097 vs. 125499\
&emsp;	2. MEL HALL, 103168 vs. 103363\
&emsp;	3. COURTNEY TRITCH, 82754 vs. 86610\
&emsp;	3. JIM BANKS, 158937 vs. 158927\
&emsp;	4. JIM BAIRD, 156591 vs. 156539\
&emsp;	5. DEE THORNTON, 137028 vs. 137142\
&emsp;	5. SUSAN W BROOKS, 179706 vs. 180035\
&emsp;	6. GREG PENCE, 134634 vs. 154260\
&emsp;	6. JEANNINE LEE LAKE, 70234 vs. 79430\
&emsp;	6. TOM FERKINHOFF, 7064 vs. 8030\
&emsp;	8. LARRY D BUCSHON, 154207 vs. 157396\
&emsp;	8. WILLIAM TANOOS, 83070 vs. 86895\
&emsp;	9. LIZ WATSON, 115073 vs. 118090\
&emsp;	9. TREY HOLLINGSWORTH, 146879 vs. 153271

* We were not able to perform county-level checks for US SENATE or state-level elections, because official county-level results are not available. For US SENATE we checked the aggregate candidate totals against the official statewide totals and find the following small statewide discrepancies:\
&emsp;	MIKE BRAUN, 1151904 vs. 1158000\
&emsp;	JOE DONNELLY, 1008030 vs. 1023553\
&emsp;	LUCY M BRENTON, 99732 vs. 100942

* Spot-checking suggests that state legislative races are largely accurate

* We do not conduct vote aggregation checks for write-in candidates. They should not be expected in general to match.

* In Tippecanoe county, four rows for state house have positive vote totals but no candidate name. We drop them.

* In one precinct there is a vote total of -79 attached to the candidate CAST VOTES. We retain this row because it is unclear whether this is a typo or some kind of adjustment row.

* 11 nearly duplicated rows, with all of the same information but different vote counts, were present in the original data. 10 of them are undervote totals for county council races in Johnson county, and lacking a canonical figure to compare them to, we cannot drop any of them. The remaining near-duplicate is MAURICE OAKEL FULLER's results in the state house race in one precinct in TIPPECANOE.

## Iowa

Updated data added 02-08-2022.

## Kansas

Updated data added 02-18-2022.

* Note that raw data reporting format leads to inclusion of precincts with 0 votes. Handle with care if computing aggregate statistics like average vote total by candidate.

## Kentucky

Updated data added 03-07-2022.

## Louisiana

Updated data added 01-24-2022.

## Maine

Updated data added 01-24-2022.

* Maine reports election results at the township level, rather at the precinct level. Township/municipality is treated as precinct in the cleaned data. 

* Certain rows contain county-fips info in place of jurisdiction-fips info for one of two reasons: (1) Maine reports state UOCAVA vote totals for each candidate aggregated at the county level. (2) Township information for certain towns could not be matched to our jurisdiction-fips merger file. 

## Maryland

Updated data added 02-18-2022.

## Massachusetts

Updated data added 01-24-2022. Local data not included at the moment.

## Michigan

Updated data added 02-08-2022.

* Precinct data are taken from https://miboecfr.nictusa.com/cgi-bin/cfr/precinct_srch.cgi?elect_year_type=2018GEN&county_code=00&Submit=Search

* Raw data includes rows with 0 votes even for locations where a race did not take place. For example, US House candidates will have the appropariate vote totals for precincts within the constituency and rows with 0 votes in precincts outside the constituency. Be sure to drop these rows if calcualting vote summary statistics like mean/median, othewise calculations will be biased.

* Precinct data contain precinct "9999", which are "statistical adjustments" rows that must be carefully considered when aggregating vote totals by office/county. Aggregating to state/county level including these 9999 precincts leads to the exact official SOS vote totals. 
* Vote totals aggregated by county that DO NOT include this 9999 precinct do not always match the official county totals for every race either. 
* All rows that have a discrepancy when aggregated by county (without the 9999 precinct rows) are marked readme_check == "TRUE". 
* More information about "9999" precincts and the nature of the discrepancies will be added to the README.md as we receive it.

## Minnesota

Updated data added 01-24-2022.

## Mississippi

Updated data added 01-24-2022.

## Missouri

Updated data added 01-24-2022. Local data not included at the moment.

## Montana

Updated data added 01-24-2022.

## Nebraska

Updated data added 01-24-2022. Local data not included at the moment.

## Nevada

Added 06-02-2021. Local data not included at the moment.

* From the official Nevada 2018 Election results spreadsheet: "Note: In cases where the cumulative turnout for a precinct for a race or ballot question is greater than 0 but less than 10, the numbers have been replaced with an asterisk in order to protect the secrecy of a voter's ballot, as required by Nevada Law. As a result, the total for a precinct may be different from what is reported on official documents." 
* We have included these cases in our cleaned results, replacing the asterisk with -1 to preserve the votes values as ints. These results should be dropped when aggregating results at the state/county level. Certain county aggregated results in affected races are marginally different from the official reported vote totals due to the masking of votes for privacy purposes.

## New Hampshire

Updated data added 02-08-2022.

## New Jersey

Updated data added 02-07-2022.

* Raw precinct data acquired from openelections (https://github.com/openelections/openelections-data-nj/tree/master/2018/counties). Marginal discrepancies identified in Essex, Hunterdon, and Salem counties when compared to official SOS aggregated results. Here are a list of discrepancies for US Senate candidate Robert Menendez (SOS vs our data):
- Essex: 		194,068 vs 193,796
- Hunterdon: 	24,823 vs 24,865
- Salem: 		9,060 vs 9,033

## New Mexico

Updated data added 01-24-2022. Local data not included at the moment.

* New Mexico "masks" vote totals in precinct results for candidates with small vote tallies, to protect the privacy of voters. These masked votes are denoted as "-1" in the votes column.

## New York

Added data 10-20-2022. The raw data were gathered by OpenElections: https://github.com/openelections/openelections-data-ny/tree/master/2018

Substantial portions of the state-supplied data had to be removed due to large and irreconcilable discrepancies between the reported precinct-level vote totals and the official county- or district-level vote totals. We believe that we have removed every race with severe discrepancies, but because of the magnitude of the errors in the original data, we urge users of this state's data to proceed with caution, and to independently check the vote totals for any races of interest. There are numerous discrepancies by office, and in many cases the discrepancies were so large that we simply omit any reporting from the race. We list those cases below.

US SENATE county-level issues:
* No results were reported from NIAGARA, results were insufficiently accurate in JEFFERSON
* Minor discrepancies in DUTCHESS, ERIE, LEWIS, MADISON, MONROE, NASSAU, SCHUYLER, WARREN, WYOMING

GOVERNOR county-level issues:
* No results reported from ALLEGANY, GENESEE, ORANGE, SCHUYLER, SUFFOLK
* Minor discrepancies in CORTLAND, DUTCHESS, JEFFERSON, LEWIS, NASSAU, OSWEGO, TIOGA, ULSTER, WYOMING

US HOUSE district-level issues:
* Results were insufficiently accurate in districts 18, 20, 21, 25 (just for candidate JOSEPH D MORELLE)
* Minor discrepancies in districts 4, 14, 19, 22, 23, 27

STATE SENATE district-level issues:
* Results were insufficiently accurate in districts 46, 48
* Minor discrepancies in districts 9, 19, 37, 40, 41, 42, 44, 45, 54, 55, 56, 57, 59, 63

STATE HOUSE district-level issues:
* No results were reported from districts 29, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 88, 89, 90, 91, 92, 93, 109, 123, 125, 141, 142, 143, 149, 150. Results were insufficiently accurate in districts 94, 95, 98, 99, 100, 101, 104, 108, 110, 111, 116, 117, 118, 119, 121, 122, 124, 130, 140, 144, 146, 147
* Minor discrepancies in districts 102, 103, 105, 107, 114, 120, 126, 132, 145

Users should also be aware of the following general issues:
* We have dropped contests in districts or counties where the precinct-level vote totals are extremely different from the official county-wide or district-wide totals. **This must be taken into account when computing descriptive statistics**, or when using New York's 2018 vote counts as a variable in any analysis. The available data are systematically incomplete in ways that prevent users from straightforwardly computing, for example, the average vote share of Democratic candidates in state house races.
* All meta-information, under/overvotes, and write-in numbers are retained as is. Because of the inconsistent structure of reporting, we were not able to verify the counts for this sort of information against certified results at the county or district level, and it should be assumed that there are discrepancies. Before including in any analysis the number of write-ins or the frequency of overvoting or undervoting, please independently verify the reported values
* OVERVOTES and UNDERVOTES appear to sometimes be reported as the net number of undervotes, perhaps by subtracting the number of undervotes from the number of overvotes
* The raw data contained 649 rows which were an exact duplicate of some other row in the dataset. By adding disambiguating information we were able to reduce the number of rows with a duplicate to 357, but those rows cannot be distinguished (and other rows are presumably being distinguished only by vote total when some other information should distinguish them as well)
* The reported candidate names are sometimes blank for non-write-in candidates in the raw data. We retain these rows because the vote totals may refer to real votes, so users can attempt to impute the missing candidate names based on the vote totals and locations
* RAYMOND W WALTER and KAREN M MCMAHON, opponents in a state house race, in some cases have their vote totals combined and reported together in one row
* Note that state house results are dramatically incomplete, and that the incompleteness correlates with district number (likely this means that quality and completeness of reporting varied by region within the state)

## North Carolina

Updated data added 03-07-2022.

## North Dakota

Updated data added 01-24-2022. Local data not included at the moment.

## Ohio

Updated data added 01-24-2022.

## Oklahoma

Updated data added 01-24-2022.

## Oregon

Updated data added 01-24-2022.

## Pennsylvania

Updated data added 02-08-2022.

* The raw precinct data is provided by the Pennsylvania Department of State.
* The precinct field is structured as:
	- ['precinct_code']_['cong_district']['senate_district']['house_district']_['vtd_code']
* The raw precinct data included a "Municipality Name" field, which has been stored in the "jurisdiction_name" field of our dataset. However, the "jurisdiction_fips" field is the same as the "county_fips" field, as there are no 10 digit jurisdiction FIPs codes associated with the provided municipalities. 
* There are marginal discrepancies between the aggregated precinct results and the results from the Secretary of State’s website. Precinct results are uncertified and uncorrected for later updates during the certification process, whereas the state website results reflect certified returns. Certified SOS results include “grace period” ballots (ballots postmarked and received by the Friday after election day), while the precinct results in many counties often do not. Counties with discrepancies are flagged readme_check = True.

* Here are the discrepancies by county for Governor (aggregated precinct data - official SOS results)
	- WESTMORELAND (WAGNER +287, WOLF +196)

## Rhode Island

Updated data added 02-07-2022.

## South Carolina

Updated data added 01-24-2022. Local data not included at the moment.

## South Dakota

Updated data added 01-24-2022. Local data not included at the moment.

## Tennessee

Updated data added 01-24-2022. Local data not included at the moment.

## Texas
Updated data added 02-07-2022.

* Raw data from Texas Legislative Council.

* precinct field is derived from taking 'CNTYVTD' and 'VTDKEY' and joining with the separator "_"

* 4 files failed to download, so the following results are excluded.
	- Dallas County J. P. Pct.3 Pl.1
	- Bexar County Court At Law No.12
	- Dallas County J. P. Pct.2 Pl.1
	- Harris County J. P. Pct.7 Pl.2

## Vermont

Updated data added 03-07-2022.

* Vermont provides the township level data broken down further by representative districts within township. The precinct field is thus a combination of the "Township" and "Rep District" fields, separated by an underscore "_".

* For State Senate races, Vermont has floating towns: towns that are physically located in one county but vote for senator in another county, so special care must be taken care off when aggregating votes.
	- Addison State Senate: Huntington is in Chittenden County and votes for Addison State Senator.
	- Bennington State Senate: Wilmington is in Windham County and votes for Bennington State Senator.
	- Caledonia State Senate: Bradford, Fairlee, West Fairlee, Newbury, Topsham are in Orange County and vote for Caledonia State Senator.
	- Essex-Orleans State Senate: Wolcott is in Lamoille County and votes for Essex-Orleans State Senator.
	- Franklin State Senate: Alburgh is in Grand Isle County and votes for Franklin State Senator.
	- Grand Isle State Senate: Colchester is in Chittenden County and votes for Grand Isle State Senator.
	- Windsor State Senate: Londonderry is in Windham County and votes for Windsor State Senator.

## Virginia

Updated data added 02-07-2022.

## Utah

Updated data added 02-07-2022.

* There are "supressed" votes in Weber county for certain small precincts to protect privacy. The county totals in Weber are therefore undercounted when compared to official county level results. The votes in these precincts are coded as -1, and should be dropped prior to any aggregation. 

* Other rows that are readme_checked == True are the result of PDF scraping errors. Major discrepancies with official results have been rectified, but some marginal discrepancies (off by no more than 5 votes with official results) remain. 

## Washington

Updated data added 01-24-2022. Raw precinct data acquired from the Secretary of State wesbite at times have marginal discrepancies when aggregated and compared to statewide official totals.

## West Virginia

Updated data added 01-24-2022.

## Wisconsin

Updated data added 10-13-2022. Local data not included at the moment. Votes that are reported at the county level as "scattered" were not reported at the precinct level, so our totals are smaller than the county-level totals for statewide or federal offices by exactly the number of scatted votes (the Wisconsin statute defines scattered votes as votes for "individuals whose names do not appear on the ballot and who receive a comparatively small number of votes" https://docs.legis.wisconsin.gov/statutes/statutes/7/ii/75)

## Wyoming

Updated data added 02-07-2022.


