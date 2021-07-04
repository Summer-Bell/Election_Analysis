# Election_Analysis

## Overview of Election Audit
Tom an employee at the Colorado Board of Elections needs to certify the election results for a US Congressional precinct.
In order to certify the election results the vote count report needs to be audited.

### Purpose
To maintain election integrity the certification process requires that the audit be completed timely and accurately.
To achieve this Tom wants to automate the election results audit process.
By writing a script in Python he will be able to successfully complete the audit and automate the process for future election audits.
The vote count report used for the audit is [election_results.cvs](Resources/election_results.csv)
The Python script [PyPoll_Challenge.py](PyPoll_Challenge.py) will issue an output file [election_analysis.txt](Analysis/election_analysis.txt) that will summarize the election results.
It will instantly provide the total number of votes cast summarized by both candidate and county.
The election winner will be presented along with their vote count and winning percentage.

## Election-Audit Results
The election results are in [election_analysis.txt](Analysis/election_analysis.txt).
This output was generated using 'txt_file.write' code for the following variables: election_results, county_results, largest_turnout_county_summary and candidate_results.

### Election Outcomes are listed below:
- How many votes were cast in this congressional election?
	* The total votes cast were 369,711

To calculate the total votes a total_votes variable was inialized at 0.
Within a For loop the code 'total_votes = total_votes + 1' was utilized to calculate the total vote.

- Provide a breakdown of the number of votes and the percentage of total votes for each county in the precinct.
	* Jefferson: 10.5% (38,855)
	* Denver: 82.8% (306,055)
	* Arapahoe: 6.7% (24,801)

In the script a county list and county votes dictionary were created.
Within a For loop the county name from each row was extracted using 'county_name = row[1]'
The following if statement checks that the county does not match existing counties on the list and adds a county if they are not on the list.
In addition it compiles the number of votes for each county.

'''if county_name not in county_options:
	county_options.append(county_name)
	county_votes[county_name] = 0
	county_votes[county_name] += 1'''

- Which county had the largest number of votes?
	* Denver county had the largest number of votes with 306,055

An if statement was utilized to determine the winning county and get its vote count.
The following code was used.

'''if (votes > largest_turnout_county_count) and (vote_percentage > winning_percentage):
            largest_turnout_county_count = votes                
            largest_turnout_county = county_name'''

- Provide a breakdown of the number of votes and the percentage of the total votes each candidate received.
	* Charles Casper Stockham: 23.0% (85,213)
	* Diana DeGette: 73.8% (272,892)
	* Raymon Anthony Doane: 3.1% (11,606)

Determining the number of votes and the percentage of the total votes each candidate received used the same code structure that was used to determine these values for the county.
It utilized variables specific to candidates instead of the county.

- Which candidate won the election, what was their vote count, and what was their percentage of the total votes?
	* Winner: Diana DeGette
	* Winning Vote Count: 272,892
	* Winning Percentage: 73.8%


## Election-Audit Summary

### Business Proposal for Script Usage in Any Election
This script can be used for congressional, senatorial and local election audits.
It would not require any edits if they used a vote count report file that has the same column structure as [election_results.cvs](Resources/election_results.csv).
There are only three columns of data in that file.
If ballot type was added this script could be modified so the [election_analysis.txt](Analysis/election_analysis.txt) included a breakdown of voting methods.
This would help the election commission better understand how people are voting and focus resources accordingly.
The script could also be modified to provide a total below both the candidate and county vote so an auditor can easily verify that they equal the total votes.
This would help ensure no vote counts are missed during the analysis.



