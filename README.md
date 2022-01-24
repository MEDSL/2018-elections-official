
# 2018-elections-official

This is the MEDSL repository for official precinct returns for 2018 General Election.

 Users can download data by the level of office returns (president, US senate, US house, state, or local levels). For each state that is complete, users can also download all of the precinct-level returns separately in the folders above.


States from this repository has been temporarily removed to investigate issues with duplicated rows and nearly duplicated rows. We are working to identify and correct the errors, which we have so far identified in the following states:

* ['Alabama', 'Arizona', 'Connecticut', 'Florida', 'Illinois', 'Iowa', 'Kansas', 'Maryland', 'Michigan', 'New Hampshire', 'New Jersey', 'Pennsylvania', 'Rhode Island', 'Vermont', 'Virginia', 'Wyoming']

We hope to provide corrected data shortly, and until we do so, data pulled from this repository prior to January 20, 2022 should be used with caution. Please contact us at sbaltz@mit.edu if you have any questions.


The returns are in progress, and will be updated periodically until completion. The following states and districts are included in the dataset:


## Alaska

Updated data added 01-24-2022. Local data not included at the moment.

## Arkansas

Updated data added 01-24-2022. Local data not included at the moment.

## California

Updated data added 01-24-2022. Local data not included at the moment.

## Colorado

Updated data added 01-24-2022.

## Delaware

Updated data added 01-24-2022.

## District of Columbia

Updated data added 01-24-2022.

## Georgia

Updated data added 01-24-2022. Local data not included at the moment.

## Hawaii

Updated data added 01-24-2022.

## Idaho

Updated data added 01-24-2022. Local data not included at the moment.

## Louisiana

Updated data added 01-24-2022.

## Maine

Updated data added 01-24-2022.

* Maine reports election results at the township level, rather at the precinct level. Township/municipality is treated as precinct in the cleaned data. 

* Certain rows contain county-fips info in place of jurisdiction-fips info for one of two reasons: (1) Maine reports state UOCAVA vote totals for each candidate aggregated at the county level. (2) Township information for certain towns could not be matched to our jurisdiction-fips merger file. 

## Massachusetts

Updated data added 01-24-2022. Local data not included at the moment.

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

## New Mexico

Updated data added 01-24-2022. Local data not included at the moment.

* New Mexico "masks" vote totals in precinct results for candidates with small vote tallies, to protect the privacy of voters. These masked votes are denoted as "-1" in the votes column.

## North Dakota

Updated data added 01-24-2022. Local data not included at the moment.

## Ohio

Updated data added 01-24-2022.

## Oklahoma

Updated data added 01-24-2022.

## Oregon

Updated data added 01-24-2022.

## South Carolina

Updated data added 01-24-2022. Local data not included at the moment.

## South Dakota

Updated data added 01-24-2022. Local data not included at the moment.

## Tennessee

Updated data added 01-24-2022. Local data not included at the moment.

## Washington

Updated data added 01-24-2022. Raw precinct data acquired from the Secretary of State wesbite at times have marginal discrepancies when aggregated and compared to statewide official totals.

## West Virginia

Updated data added 01-24-2022.

## Wisconsin

Updated data added 01-24-2022. Local data not included at the moment.

