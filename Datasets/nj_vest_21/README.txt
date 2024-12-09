2021 New Jersey precinct and election results shapefile.

## RDH Date retrieval
10/04/2022

## Sources
This file was retrieved from VEST at https://doi.org/10.7910/DVN/FDMI5F

Election results from individual county canvass reports or election reporting websites (https://nj.gov/state/elections/vote-county-election-officials.shtml).
Precinct shapefile from New Jersey Geographic Information Network (https://njogis-newjersey.opendata.arcgis.com/datasets/election-districts-for-new-jersey). Naval Weapons Station Earle in Monmouth County was added as an unassigned district.

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

G21GOVDMUR - Philip Murphy (Democratic Party)
G21GOVRCIA - Jack Ciattarelli (Republican Party)
G21GOVLMEL - Gregg Mele (Libertarian Party)
G21GOVGHOF - Madelyn R. Hoffman (Green Party)
G21GOVSKUN - Joanne Kuniansky (Socialist Workers Party)

## Processing Steps

All counties except Salem and Warren reported mail votes at the municipal and/or ward level. Hudson, Mercer, and Union also reported provisional votes at the municipal and/or ward level. The remaining counties reported all types of early votes at the municipal and/or ward level. Essex, Hudson, and Monmouth further subdivide these vote types by other districts on the same ballot. All votes were distributed by candidate to precincts based on their share of the precinct-level reported vote of the respective reporting unit.