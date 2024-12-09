2020 New Jersey precinct and election results shapefile.

## RDH Date retrieval
10/04/2022

## Sources
This file was retrieved from VEST at https://doi.org/10.7910/DVN/K7760H

Election results from individual county canvass reports or election reporting websites (https://nj.gov/state/elections/vote-county-election-officials.shtml). Precinct shapefile from New Jersey Geographic Information Network (https://njogis-newjersey.opendata.arcgis.com/datasets/election-districts-for-new-jersey).

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
AUD - Auditor
COC - Corporation Commissioner
COU - City Council Member
DEL - Delegate to the U.S. House
GOV - Governor
H## - U.S. House, where ## is the district number. AL: at large.
INS - Insurance Commissioner
LTG - Lieutenant Governor
PRE - President
PSC - Public Service Commissioner
SAC - State Appeals Court (in AL: Civil Appeals)
SCC - State Court of Criminal Appeals
SOS - Secretary of State
SPI - Superintendent of Public Instruction
USS - U.S. Senate

Party Codes
D and R will always represent Democrat and Republican, respectively.
See the state-specific notes for the remaining codes used in a particular file; note that third-party candidates may appear on the ballot under different party labels in different states.

## Fields

G20PREDBID - Joseph R. Biden (Democratic Party)
G20PRERTRU - Donald J. Trump (Republican Party)
G20PRELJOR - Jo Jorgensen (Libertarian Party)
G20PREGHAW - Howie Hawkins (Green Party)
G20PRECBLA - Don Blankenship (Constitution Party)
G20PRESLAR - Gloria Estela La Riva (Socialism and Liberation)
G20PREOHAM - Bill Hammons (Unity Party America)
G20PREOFUE - Roque "Rocky" De La Fuente (Alliance Party)

G20USSDBOO - Cory Booker (Democratic Party)
G20USSRMEH - Rikin "Rik" Mehta (Republican Party)
G20USSGHOF - Madelyn R. Hoffman (Green Party)
G20USSOFER - Veronica Fernandez (Of, By, For!)
G20USSOBUR - Daniel Burke (LaRouche Was Right)

## Processing Steps

For the nj_2020 shapefile precincts have been merged and labeled to match the units by which election results were reported by the respective counties. 
Overseas federal ballots were reported at the county level by Burlington, Cape May, Gloucester, Monmouth, Morris, and Sussex. Provisional ballots were reported at the municipal/district level by Essex. These were distributed by candidate to reporting units based on their share of the municipal or ward/district reported vote.
For the nj_2020_vtd_estimates shapefile the 2020 election results have been further apportioned to individual precincts based on the average of the vote from the 2016 election results for President and the 2018 election results for US Senate. Votes for each candidate on the 2020 ballot were distributed from 2020 reporting units to the precincts that comprise those reporting units based on the share of the average 2016/2018 vote from each precinct that was cast for that party's candidate or for the most ideologically similar minor party candidate.