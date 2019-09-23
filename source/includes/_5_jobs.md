#Hiring Workers and Monitoring Job Progress (Jobs)
A Job represents an individual Wonoloer (Worker) performing a Job Request.

##Onboarding Workers
Workers are “hired” by posting to the assign endpoint of the Jobs service, using the worker’s User id and the Job Request id. 

##Job States
As with Job Requests, one of the most important attributes of the Job entity is its state, which can be used to monitor the job’s progress, based on how the worker and employer are interacting with the job.

<img src="images/JobStates.png">

The following job states exist:

**filled** – the Worker has accepted a Job but has not started it yet – i.e. they pressed “Accept” in the app.

**withdrawn** – the Worker withdrew from the Job (NB: if the Worker accepts the Job again, the same Job will return to the filled state)

**cancelled** – the Job has been cancelled by the Requestor

**in_progress** – the Worker has pressed “Start” in the Wonolo app

**paused** – the Worker has paused the job to take a break

**completed** – the Worker has pressed “Complete” in the Wonolo app

**approved** – the Requestor has approved the job as done

**no_show** – the Requestor has marked that the Worker did not show up for the Job

##Webhooks for Job State Transitions

###Time and Attendance
Each Job includes an array of “transitions” which record the datetime of each change in the Job’s state.  These transitions can be used to monitor a worker’s status with a transition to in_progress equating to “clocking in” and a transition to paused or completed equating to “clocking out.” 
Ending Jobs

Jobs may be cancelled by posting a PATCH request to the Jobs service with a reason for the cancellation (canclled_reason)
