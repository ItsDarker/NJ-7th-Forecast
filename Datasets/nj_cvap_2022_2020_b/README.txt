2022 Citizen Voting Age Population (CVAP) Data for New Jersey from the American Community Survey (ACS) 5-Year Estimates (2018-2022) Disaggregated to 2020 Census Blocks

## RDH Date Retrieval
06/17/2024

## Sources
CVAP data originally downloaded from this [link](https://www.census.gov/programs-surveys/decennial-census/about/voting-rights/cvap.2022.html).
PL data and CVAP data retrieved from U.S. Census via Redistricting Data Hub website.

## Fields:
Field Name Description                                                                        
GEOID20    Census Block GEOID                                                                                                            
C_TOT22    Citizen Estimate for Total                                                                
C_NHS22    Citizen Estimate for Not Hispanic or Latino                                               
C_AMI22    Citizen Estimate for American Indian or Alaska Native Alone                               
C_ASI22    Citizen Estimate for Asian Alone                                                          
C_BLA22    Citizen Estimate for Black or African American Alone                                      
C_NHP22    Citizen Estimate for Native Hawaiian or Other Pacific Islander Alone                      
C_WHT22    Citizen Estimate for White Alone                                                          
C_AIW22    Citizen Estimate for American Indian or Alaska Native and White                           
C_ASW22    Citizen Estimate for Asian and White                                                      
C_BLW22    Citizen Estimate for Black or African American and White                                  
C_AIB22    Citizen Estimate for American Indian or Alaska Native and Black or African American       
C_2OM22    Citizen Estimate for Remainder of Two or More Race Responses                              
C_HSP22    Citizen Estimate for Hispanic or Latino                                                   
C_AIA22    Citizen Estimate for American Indian or Alaska Native Alone or In Combination             
C_ASN22    Citizen Estimate for Asian Alone or In Combination                                        
C_BLK22    Citizen Estimate for Black or African American Alone or In Combination                    
CVAP_TOT22 CVAP Estimate for Total                                                                   
CVAP_NHS22 CVAP Estimate for Not Hispanic or Latino                                                  
CVAP_AMI22 CVAP Estimate for American Indian or Alaska Native Alone                                  
CVAP_ASI22 CVAP Estimate for Asian Alone                                                             
CVAP_BLA22 CVAP Estimate for Black or African American Alone                                         
CVAP_NHP22 CVAP Estimate for Native Hawaiian or Other Pacific Islander Alone                         
CVAP_WHT22 CVAP Estimate for White Alone                                                             
CVAP_AIW22 CVAP Estimate for American Indian or Alaska Native and White                              
CVAP_ASW22 CVAP Estimate for Asian and White                                                         
CVAP_BLW22 CVAP Estimate for Black or African American and White                                     
CVAP_AIB22 CVAP Estimate for American Indian or Alaska Native and Black or African American          
CVAP_2OM22 CVAP Estimate for Remainder of Two or More Race Responses                                 
CVAP_HSP22 CVAP Estimate for Hispanic or Latino                                                      
CVAP_AIA22 CVAP Estimate for American Indian or Alaska Native Alone or In Combination                
CVAP_ASN22 CVAP Estimate for Asian Alone or In Combination                                           
CVAP_BLK22 CVAP Estimate for Black or African American Alone or In Combination                       

## Processing Steps
The processing for this dataset was completed in multiple parts.

Part 1: Processing the 2022 Block Group CVAP data
CVAP data was retrieved at the block group level from link in "Sources" above.
The data was extracted from the national data to create a statewide dataset.
The data was pivoted from narrow to wide data based on GEOIDs so that one row is one block group, and each field represents a particular race/ethnicity. 
The fields were renamed to fit character length requirements. 
Processing was primarily completed using the pandas library.

To improve the usefulness of the data, we have add three categories to correspond with the Office of Management and Budget (OMB) racial categories. The "Alone or In Combinations" categories for American Indian or Alaska Native (fields with "AIA"), Asian (fields with "ASN"), and Black or African American (fields with "BLK") represent an encompassing racial category that is inclusive of all categories that include that race. For example, CVAP_AIA22 would be the sum of the "Alone" CVAP_AMI22, CVAP_AIB22, and CVAP_AIW22. For CVAP_BLK22, the field would be the sum of the "Alone" CVAP_BLA22, CVAP_AIB22, and CVAP_BLW22. For CVAP_ASN22, the field would be the sum of the "Alone" CVAP_ASI22 and CVAP_ASW22. These fields are also noted in the description as being "Alone or In Combination". No other estimate categories were modified.
All of the racial estimates provided are Non-Hispanic. Breakdowns for Hispanic/Non-Hispanic by race are not provided in the CVAP special tabulation.

Part 2: Disaggregating the 2022 Block Group CVAP data to 2020 Blocks
The 2022 CVAP data was disaggregated using 2020 PL 94-171 data. The following variables were created from block-level PL files retrieved on the RDH website (some were summed or subtracted, as indicated below, to better resemble the OMB categories):

CVAP Field Corresponding PL Field(s)

C_TOT22    P0020001                                            
C_NHS22    P0020003                                            
C_AMI22    P0020007
C_ASI22    P0020008
C_BLA22    P0020006           
C_NHP22    P0020009                                            
C_WHT22    P0020005                                            
C_AIW22    P0020014                                            
C_ASW22    P0020015                                            
C_BLW22    P0020013                                            
C_AIB22    P0020018                                            
C_2OM22    P0020011 - P0020018 - P0020014 - P0020013 - P0020015
C_HSP22    P0020002
C_AIA22    P0020007 + P0020018 + P0020014                      
C_ASN22    P0020008 + P0020015                                 
C_BLK22    P0020006 + P0020013 + P0020018                         
CVAP_TOT22 P0040001                                            
CVAP_NHS22 P0040003
CVAP_AMI22 P0040007
CVAP_ASI22 P0040008
CVAP_BLA22 P0040006                                                        
CVAP_NHP22 P0040009                                            
CVAP_WHT22 P0040005                                            
CVAP_AIW22 P0040014                                            
CVAP_ASW22 P0040015                                            
CVAP_BLW22 P0040013                                            
CVAP_AIB22 P0040018                                            
CVAP_2OM22 P0040011 - P0040018 - P0040014 - P0040013 - P0040015
CVAP_HSP22 P0040002
CVAP_AIA22 P0040007 + P0040018 + P0040014                      
CVAP_ASN22 P0040008 + P0040015                                 
CVAP_BLK22 P0040006 + P0040013 + P0040018        
                                                                                              

For each block in each column (e.g. CVAP_TOT22) the value for the 2020 block PL data was multiplied by the 2020 total for the block group.
The totals for the block group were retrieved by grouping the block data by block group ID. 
This provides a ratio of block to block group population for each individual racial category.
The ratios for each block in each column were multiplied by the 2022 CVAP total for the block's corresponding block group.
In the scenario where no blocks in a block group contain a value for a particular race/ethnicity combination in the 2020 PL data, but have a value in the 2022 estimates, total CVAP population or total citizen estimate population was used as a proxy, depending on the variable.
In the scenario where a block group does not contains a value in it's respective population or voting-age population field in the PL data, the 2022 population is divided evenly amongst all blocks in the block group.

A reproducible rounding method for CVAP was implemented for these files. Block-level CVAP values are rounded to integers in such a way to preserve block-group level counts for that particular population. CVAP was rounded based on share, taking the floor of each allocation using the method above, and then adding to blocks with the largest remainders. In the case of ties, blocks with larger whole parts were allocated an additional person, in the case of ties for those, blocks with higher census block GEOIDs were allocated the additional person.

## Additional Notes
For more information on the ACS CVAP documentation please refer to the ACS technical documentation included in this folder (also available at this [link](https://www2.census.gov/programs-surveys/decennial/rdo/technical-documentation/special-tabulation/CVAP_2018-2022_ACS_documentation_v1.pdf)).

For more information on OMB racial categories, please see this [link](https://obamawhitehouse.archives.gov/omb/bulletins_b00-02/#n_1_).

Please note that this dataset is derived from data collected in the five year range of 2018-2022. The Census recommends against using different datasets that contain overlapping years. For more information please see https://www.census.gov/newsroom/blogs/random-samplings/2022/03/period-estimates-american-community-survey.html

Visit the RDH GitHub and the processing script for this code [here](https://github.com/nonpartisan-redistricting-datahub/cvap-processing)

Please direct questions related to processing this dataset to info@redistrictingdatahub.org.