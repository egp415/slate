#Finding and Communicating with Workers 

##Using Rankings
”Ranking” is the system used to decide which Workers should be notified of a Job Request and in what order

There are several aspects of Ranking which can be configured, such as the “Ranking Formula” that is used to calculate the rank for each Worker.  It can be as simple as notifying based on the Worker’s distance to the job but often is more complex

Additionally, the timing of sending Notifications can be configured to control how fast.  Notifications are sent  Notifications are sent by push notification by default but can optionally be sent by text message

NB: ranking does not necessarily determine which jobs the Worker can see in the Wonolo App – it just defines who gets notified

[TODO: rankings vs re_rank_workers]

##Using Notifications
[resend notifications]
If the Job Request has Preferred Wonoloers [TODO: define preferred wonoloers], Preferred Notifications [TODO: define preferred notifications] will first be resent to those Preferred Wonoloers who have not already accepted the JobRequest.

If the JobRequest does not have Preferred Wonoloers, the available Wonoloer pool will be re-ranked and Wonoloers notified in resulting ranked order.

NB: in both cases, the Wonoloers notified will not necessarily be - and are unlikely to be - exactly the same list as the prior time notifications were sent.

##Using Messaging
Wonolo's In-app Messages allow a Requestor and a Wonoloer to communicate about a Job.

##Using Tracking
