# 2018 Election Returns

This is the MEDSL repository for official returns for the 2018 Midterm Elections.

The `senate_overall_2018` and `district_overall_2018` datasets, containing constituency level U.S. Senate and U.S. House election returns, respectively, are official and complete (except in a few cases where updates will be made at a later time).

The `state_overall_2018` and `county_2018` datasets contain constituency level state office election returns and county level election returns for all offices, respectively.

The `precinct_2018` dataset contains precinct level election returns for all offices. It is incomplete but will be updated weekly until completion. The following (34) states and districts are included in the dataset:

* Alabama
* Alaska
* Arkansas
* California
* Colorado
* Connecticut
* Delaware
* District of Columbia
* Florida
* Georgia
* Hawaii
* Idaho
* Illinois
* Louisiana
* Maryland
* Massachusetts
* Michigan
* Minnesota
* Missouri
* Montana
* Nevada
* New Jersey
* New Mexico
* North Carolina
* Oklahoma
* Oregon
* Rhode Island
* South Carolina
* Tennessee
* Texas
* Vermont
* Virginia
* Washington
* Wisconsin
* Wyoming

The precinct data are a work in progress, and we welcome feedback. Below are some notes for specific states:

- For data we obtained for New York, many counties are incomplete or missing entirely, so we have not posted data for the state.
- Data for Texas were retrieved given that it had the most complete precinct data. When cleaning the data, duplicate data were found by precinct within a small minority of counties. Additionally, these data contained different vote totals. For statewide races, these discrepancies amounted to approximately 0.1 percent of the total votes cast in an election. Given these minor discrepancies and that none of the different votes changed any election outcomes, we eliminated duplicated precincts by taking the minimum vote total whenever a unique precinct ID arose. This practice led to a small but systematic undercount of votes across affected races. Additionally, it does not appear that any party is systematically penalized votes over another. Therefore, when using these data, note that some discrepancies might arise from official results, but all vote percentages of the vote will be effectively indistinguishable from official results and should not in any way bias analyses conducted with these data.
- North Dakota data includes only major national and state offices; other offices will be added later.