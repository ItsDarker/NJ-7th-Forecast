2021 General Election Results Disaggregated to 2020 Census Blocks for New Jersey

## RDH Date retrieval
11/16/2022

## Sources
Precinct shapefile with election results retrieved from the Redistricting Data Hub[https://redistrictingdatahub.org/]
Precinct shapefile with election results is originally from the Voting and Election Science Team (VEST)[https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/FDMI5F].
Block shapefiles and data are retrieved from the Redistricting Data Hub[https://redistrictingdatahub.org/dataset/new-jersey-block-pl-94171-2020-by-table/] and originally from the Census Bureau's Public Law 94-171 dataset and TIGER shapefiles.

## Fields metadata

Vote Column Label Format
------------------------
Columns reporting votes follow a standard label pattern. One example is:
G20PRERTRU
The first character is G for a general election, C for recount results, P for a primary, S for a special, and R for a runoff.
Characters 2 and 3 are the year of the election.
Characters 4-6 represent the office type (see list below).
Character 7 represents the party of the candidate.
Characters 8-10 are the first three letters of the candidate's last name.

Office Codes

ATG - Attorney General
GOV - Governor
LTG - Lieutenant Governor

Party Codes
D and R will always represent Democrat and Republican, respectively.
See the state-specific notes for the remaining codes used in a particular file; note that third-party candidates may appear on the ballot under different party labels in different states.

## Fields

GEOID20 - Block Unique ID
STATEFP - State FIPS Code
COUNTYFP - County FIPS Code
PRECINCTID - Unique Precinct Identifier
VAP_MOD - Modified Voting Age Population (VAP)

G21GOVDMUR - Philip Murphy (Democratic Party)
G21GOVRCIA - Jack Ciattarelli (Republican Party)
G21GOVLMEL - Gregg Mele (Libertarian Party)
G21GOVGHOF - Madelyn R. Hoffman (Green Party)
G21GOVSKUN - Joanne Kuniansky (Socialist Workers Party)

## Processing Steps

Precinct and block shapefiles were retrieved from the sources listed above. The primary libraries used in processing are geopandas, pandas, and maup[https://github.com/mggg/maup] in Python. 
The block data was prepared by creating the VAP_MOD field which is the total Voting Age Population (P0040001) minus Correctional Facility/Prison Population (P0050003) which will be used as the denominator in disaggregation.
The block file was queried out to include just the GEOID20, VAP_MOD, and geometry fields.
To assign blocks to precincts, the maup.assign function was used. Some blocks did not receive an assignment but nearly all of these had a VAP_MOD value of 0, meaning those blocks should not receive any votes during allocation anyway. In the rare instance where there was a block with a VAP_MOD > 0 and no precinct assignment, the L2 voter file was used to determine what precinct assignment was listed for residents of that block in 2020. If no results were returned, the block did not receive an assignment, otherwise the precinct assignment for the block was modified accordingly.
After the blocks have a received an assignment, they are grouped by their new assignment and summed to give a total VAP_MOD value for the precinct. A ratio is then calculated of VAP_MOD block / VAP_MOD precinct, which is applied to all candidate columns (those starting with "G21" and "S21").
In some instances, there are precincts that sum to 0 for VAP_MOD but do contain votes. In order to not lose votes in the disaggregation process, these blocks are modified to VAP_MOD=1, then summed again to get a non-zero value denominator for VAP_MOD at the precinct. Therefore all blocks in the precinct would have the same ratio applied and receive the same distribution of votes. All blocks that have a modified VAP_MOD value were returned to their original value of 0 before extraction to maintain accuracy.
A key assumption of maup is that a block receives one precinct as an assignment. The RDH checks for any precincts with votes which have not been assigned to any blocks. In these instances, the block file is clipped to each precinct geometry, and the block which has the largest area inside the precinct receives all of the votes from that precinct.

##Additional Information 
For more information please contact info@redistrictingdatahub.org or visit our GitHub[https://github.com/nonpartisan-redistricting-datahub/election-disag]