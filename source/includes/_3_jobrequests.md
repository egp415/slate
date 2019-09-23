#Posting Jobs (Creating Job Requests)

A Job Request represent some work to be done (e.g. “I need 10 people tomorrow to stack boxes for 8 hours, starting at 10am”), so the first step in hiring Wonoloers will be to post to the Job Request service. 							

##Job Request States, State Transitions
One of the most important aspects of a Job Request is its “state” which determines how workers may interact with it and indicate where in its lifecycle the job request is at. 

<img src="images/JobRequestStates.png">

The following are valid job states:

**posted** – available to any eligible Worker and will show on the map in the Wonolo app.  When a Job Request is posted, Workers are ranked and notified. Create a Job Request with a state of posted if you want ranking and notifying to begin immediately 

**unassigned** – invisible to Workers unless they are preferred [TODO: explanation regarding preferred]

**unfilled** – no slots were filled at the start time of the Job Request

**filled** – all slots are filled but the start time is still in the future

**in_progress** – at least one Job is in progress

**completed** – all of the Jobs for this Job Request are completed

**approved** – all of the Jobs for this Job Request are approved [TODO: define approved] 

**cancelled** – the Requestor cancelled the Job Request

##Category and Descriptive Information
Certain descriptive information is required to create a job — for a complete listing see the API documentation, but some critical properties to be mindful of include:

**category** — a set of values predefined for a given company

**venue** — The name of the work location, e.g. 'Best Buy Store 321'

**start_time** — The time to start work in 24-hour format. Example: 2018-08-18 19:30

**duration** — The expected length of the Job in MINUTES.

##Wages
As part of defining a job request you will need to specify whether it is a 1099 or w2 job, and if applicable, what the wage is.
Location Information (Longitude and Latitude)
As with workers defined through the user service, job requests will be created with longitude and latitude coordinates defined as decimals.  These values will be used to help rank workers for the purpose of placement in a given job as well as display the job posting on a map.

##Badge Requirements					
Badge requirements are sub-attributes of the Job Request and will be used to filter workers when they are not a soft requirement for the job.		
Preferred Candidates and Ban Lists
In order to further filter workers for a particular job request, it is possible to specify a list of candidates you would prefer to use if they are available and a list of user ids you specifically do not want assigned to the Job Request.

##Multi Day Jobs
Jobs that span multiple days are managed through the Multi Day Jobs service.   A Multi Day Job joins multiple Job Requests together though a given Job Request’s multi_day_job_request_id property.  

This entity specifies frequency (daily or weekly) and the number of repetitions/iteration as you would on a calendar entry.

Additionally, a Requestor may specify that a Wonoloer must accept all days of a Multi-day Job Request through the same_workers property. Otherwise, a Wonoloer is free to pick and choose those days they wish.

##Webhooks for Job Request State Transitions