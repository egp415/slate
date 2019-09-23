#Managing Workers
Workers (aka “Wonoloers”) are the people who hired for jobs and who use the Wonolo mobile app to search for and apply to job postings.  Employers (or “Requesters”) are the people posting jobs, primarily through the Customer Portal web application.   Both Workers and Employers are represented as Users within the API, and it is through that service that workers are managed.
 
##Privilege Level
If you have Public Pool access, you will only be able to access Wonoloers with whom you have “active” Jobs. Active jobs are those Jobs which:
* are in a state of filled, in_progress, paused, completed, or
* are in a state of approved and were approved in the past 24 hours.

##Creating / Updating Workers
>Creating a Worker

```shell
curl -X POST \
  'https://test.wonolo.com/api_v2/users/invite?token=[yourtoken]' \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
        "type": "Worker",
        "first_name": "InviteUserTestFName",
        "last_name": "InviteUserTestLName",
        "phone": "+1415-555-5555",
        "email": "wonolotest@wonolo.com",
        "external_id": "wonolotest2"
    }'
    
curl -X PATCH \
  'https://test.wonolo.com/api_v2/users/9012?token=VEzCnWyk1uFWEqyyuzhd' \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
    "user": {
    	"id": 9012,
        "external_id": wonolotest1,
        "type": "Worker",
        "first_name": "FName",
        "last_name": "LName",
        "avatar_url": null,
        "city": "San Francisco",
        "zip": "94111",
        "rating": null,
        "suspended": false,
        "suspended_until": null,
        "latitude": "37.7952",
        "longitude": "-122.4029",
        "workplace_image_url": null,
        "logo_url": null,
        "business_name": null,
        "email": "testworker01-wonolo@wonolo.com",
        "phone": "+1415-555-5551",
        "gender": null,
        "w2_employee_id": "",
        "w2_onboarding_status": "",
        "w2_onboarding_started": null,
        "dob": null,
        "ssn": "",
        "address": null,
        "address_state": "",
        "drug_tested": "",
        "updated_at": "2019-08-30T11:59:49.919-07:00",
        "w2_address_state": null,
        "w2_onboarding_completed": null,
        "lower_pool": null,
        "lower_pool_until": null,
        "home_latitude": "37.7952",
        "home_longitude": "-122.4029",
        "referred_by": "",
        "tracking_code": null,
        "onboarding_appt_time": null
        }
}'
```

```javascript
//first invite a worker
var data = JSON.stringify({
  "type": "Worker",
  "first_name": "InviteUserTestFName",
  "last_name": "InviteUserTestLName",
  "phone": "+1415-555-5551",
  "email": "wonolotest2@wonolo.com",
  "external_id": "wonolotest2"
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://test.wonolo.com/api_v2/users/invite?token=VEzCnWyk1uFWEqyyuzhd");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);

//then patch the user you created to add particular data
data = "{\n    \"user\": {\n    \t\"id\": 9012,\n        \"external_id\": wonolotest1,\n        \"type\": \"Worker\",\n        \"first_name\": \"Fname\",\n        \"last_name\": \"LastName\",\n        \"avatar_url\": null,\n        \"city\": \"San Francisco\",\n        \"zip\": \"94111\",\n        \"rating\": null,\n        \"suspended\": false,\n        \"suspended_until\": null,\n        \"latitude\": \"37.7952\",\n        \"longitude\": \"-122.4029\",\n        \"workplace_image_url\": null,\n        \"logo_url\": null,\n        \"business_name\": null,\n        \"email\": \"testworker01-wonolo@wonolo.com\",\n        \"phone\": \"+1415-555-5551\",\n        \"gender\": null,\n        \"w2_employee_id\": \"\",\n        \"w2_onboarding_status\": \"\",\n        \"w2_onboarding_started\": null,\n        \"dob\": null,\n        \"ssn\": \"\",\n        \"address\": null,\n        \"address_state\": \"\",\n        \"drug_tested\": \"\",\n        \"updated_at\": \"2019-08-30T11:59:49.919-07:00\",\n        \"w2_address_state\": null,\n        \"w2_onboarding_completed\": null,\n        \"lower_pool\": null,\n        \"lower_pool_until\": null,\n        \"home_latitude\": \"37.7952\",\n        \"home_longitude\": \"-122.4029\",\n        \"referred_by\": \"\",\n        \"tracking_code\": null,\n        \"onboarding_appt_time\": null\n}";

xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("PATCH", "https://test.wonolo.com/api_v2/users/9012?token=VEzCnWyk1uFWEqyyuzhd");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

Creating workers requires a variety of properties to be defined such as name, gender, and address information.  Particular properties important for assigning users to jobs are described below.

Workers are created by sending an initial post request to the <A href="#users-invite">invite</a> endpoint of the <A href="#users">Users</A> service.  Users are not created directly through posting the user service to avoid sending a password.  Calling the invite endpoint sends a link to the new user’s email.  Note that both the user’s email and the user’s phone number must be unique and the email must be formatted as a valid email address.
    
Subsequent updates to the user’s account may be done by making PATCH requests to the user service with the new identifier returned from calls to invite.

##Worker Location Info
Location information on users representing workers will be important when it comes to ranking workers for a job posting (see below).  This location information is represented as longitude and latitude coordinates for both here the worker resides as well as the worker’s current location [TODO: confirm home vs. current].  These values describe GPS coordinates as positive or negative decimal values.  These values can typically be obtained from an end user’s device.

##Assigning Badges to Workers
As described above, badges will be important in determining which jobs are visible and available to workers in the system.  It is therefore important to assign badges to users through the “badges” property, which is an array of badge objects.  To add a Badge, you just need to specify the ID of the Badge in `user[user_badges_attributes][badge_id]`.  Any number of badges may be added to a given worker object.

TODO: example code for assigning badges
Special Worker Properties

[TODO: this catch all for now things that might require particular explanation in relationship to the API or an explanation that goes beyond what can be provided in inline documentation]
		 	 	 								
external_id — You can associate your own ID as the external_id parameter and use that to retrieve the Worker in future. This can be any arbitrary string (it doesn’t have to be a number)  