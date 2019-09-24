--- 

title: Wonolo (params in:formData) 

language_tabs: 
   - shell: cUrl
   - javascript 

toc_footers: 
   - <a href='#'>Sign Up for a Developer Key</a> 
   - <a href='https://github.com/lavkumarv'>Documentation Powered by lav</a> 

includes: 
   - 0_intro
   - 1_badges
   - 2_workers
   - 3_jobrequests
   - 4_finding_messaging_workers
   - 5_jobs

search: true 

--- 

2015-2017 Wonolo Inc. All rights reserved. 

**Version:** 2.0 

# /AUTHENTICATE
## ***POST*** 

**Summary:** Authenticate and obtain a token

**Description:** 
<p>Pass in your API publishable key and secret keys and obtain a token to use
for subsequent API calls. Tokens expire after 24 hours.</p>


### HTTP Request 
`***POST*** /authenticate` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| secret_key | formData | Your secret API key, e.g. +sk_test_rgyzxu6y_86FXE5YSMjN+ | Yes | string |
| api_key | formData | Your publishable API key, e.g. +pk_test_k4ttwB9bYVdmVyXgA7fD+ | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 401 | Your api_key or secret_key is invalid |
| 422 | You have not specified both api_key and secret_key |

# /BADGES
## ***GET*** 

**Summary:** List available Badges

**Description:** 
<p>Returns a list of available Badges, optionally paginated. Note: the maximum
number returned per page in any case is 50.</p>


### HTTP Request 
`***GET*** /badges` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | query | Token obtained from /authorize | Yes | string |
| page | query | The page number to start from | No | number |
| per | query | The size of the page | No | number |
| query | query | Filter by name of badge | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 401 | Unauthorized |

## ***POST*** 

**Summary:** Create a new Badge

**Description:** 

### HTTP Request 
`***POST*** /badges` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| badge[description] | formData | Description of Badge Detail | Yes | string |
| badge[name] | formData | Name of Badge | Yes | string |
| token | formData | Token obtained from /authorize | Yes | string |
| badge[info_url] | formData | External Url for more Information about Badge | No | string |
| badge[remote_icon_url] | formData | Remote URL of Icon Image | No | string |
| badge[is_soft] | formData | Allow Wonoloers to be ranked/notified about a job even though they do not have the badge | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | ok |

# /BADGES/{ID}
## ***GET*** 

**Summary:** Get a specific Badge

**Description:** 

### HTTP Request 
`***GET*** /badges/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | query | Token obtained from /authorize | Yes | string |
| id | path |  | Yes | number |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | ok |

## ***PATCH*** 

**Summary:** Update a Badge

**Description:** 

### HTTP Request 
`***PATCH*** /badges/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| badge[description] | formData | Description of Badge Detail | Yes | string |
| badge[name] | formData | Name of Badge | Yes | string |
| token | formData | Token obtained from /authorize | Yes | string |
| id | path |  | Yes | number |
| badge[info_url] | formData | External Url for more Information about Badge | No | string |
| badge[remote_icon_url] | formData | Remote URL of Icon Image | No | string |
| badge[is_soft] | formData | Allow Wonoloers to be ranked/notified about a job even though they do not have the badge | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | ok |

## ***DELETE*** 

**Summary:** Delete a Badge

**Description:** 

### HTTP Request 
`***DELETE*** /badges/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | formData | Token obtained from /authorize | Yes | string |
| id | path |  | Yes | number |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | ok |

# /CUSTOMERS
## ***POST*** 

**Summary:** Create a Customer

**Description:** 

### HTTP Request 
`***POST*** /customers` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| customer[name] | formData | Customer Name | Yes | string |
| token | formData | Token obtained from /authenticate | Yes | string |
| customer[account_owner] | formData | Account Owner | No | string |
| customer[account_manager] | formData | Account Manager | No | string |
| customer[address] | formData | Address | No | string |
| customer[city] | formData | City | No | string |
| customer[state] | formData | State | No | string |
| customer[zip] | formData | Zip | No | string |
| customer[phone] | formData | Phone | No | string |
| customer[contact_first_name] | formData | Contact First Name | No | string |
| customer[contact_last_name] | formData | Contact Last Name | No | string |
| customer[contact_email] | formData | Contact Email | No | string |
| customer[billing_first_name] | formData | Billing First Name - must be between 1 and 50 characters in length | No | string |
| customer[billing_last_name] | formData | Billing Last Name - must be between 1 and 50 characters in length | No | string |
| customer[billing_email] | formData | Billing Email - must be between 1 and 255 characters in length | No | string |
| customer[billing_phone] | formData | Billing Phone - must be between 1 and 50 characters in length | No | string |
| customer[fee_percentage] | formData | Fee Percentage - must be between 0.0 and 1.0 | No | number |
| customer[can_post_w2] | formData | True if this Customer can post w2 job requests. Default is False when not set | No | boolean |
| customer[can_post_1099] | formData | True if this Customer can post 1099 job request. Default is True when not set | No | boolean |
| customer[can_use_premier_features] | formData | True if this Customer can use premium features | No | boolean |
| customer[use_start_and_complete_pin] | formData | True if this Customer can use Start and Complete Pin. Default is False when left blank or not set | No | boolean |
| customer[strategic_pilot] | formData | True if this Customer is strategic pilot | No | boolean |
| customer[use_pending_state] | formData | True if this Customer can use Pending Workflow. Default is False when not set | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 422 | Could not save the Customer |

# /CUSTOMERS/{ID}
## ***GET*** 

**Summary:** Get a specific Customer

**Description:** 

### HTTP Request 
`***GET*** /customers/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | query | Token obtained from /authenticate | Yes | string |
| id | path | ID of Customer | Yes | number |

**Responses**

| Code | Description |
| ---- | ----------- |
| 404 | Not found. No Customer with the specified ID can be found |

## ***PATCH*** 

**Summary:** Update a Customer

**Description:** 

### HTTP Request 
`***PATCH*** /customers/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| customer[name] | formData | Customer Name | Yes | string |
| token | formData | Token obtained from /authenticate | Yes | string |
| id | path | ID of Customer | Yes | number |
| customer[account_owner] | formData | Account Owner | No | string |
| customer[account_manager] | formData | Account Manager | No | string |
| customer[address] | formData | Address | No | string |
| customer[city] | formData | City | No | string |
| customer[state] | formData | State | No | string |
| customer[zip] | formData | Zip | No | string |
| customer[phone] | formData | Phone | No | string |
| customer[contact_first_name] | formData | Contact First Name | No | string |
| customer[contact_last_name] | formData | Contact Last Name | No | string |
| customer[contact_email] | formData | Contact Email | No | string |
| customer[billing_first_name] | formData | Billing First Name - must be between 1 and 50 characters in length | No | string |
| customer[billing_last_name] | formData | Billing Last Name - must be between 1 and 50 characters in length | No | string |
| customer[billing_email] | formData | Billing Email - must be between 1 and 255 characters in length | No | string |
| customer[billing_phone] | formData | Billing Phone - must be between 1 and 50 characters in length | No | string |
| customer[fee_percentage] | formData | Fee Percentage - must be between 0.0 and 1.0 | No | number |
| customer[can_post_w2] | formData | True if this Customer can post w2 job requests. Default is False when not set | No | boolean |
| customer[can_post_1099] | formData | True if this Customer can post 1099 job request. Default is True when not set | No | boolean |
| customer[can_use_premier_features] | formData | True if this Customer can use premium features | No | boolean |
| customer[use_start_and_complete_pin] | formData | True if this Customer can use Start and Complete Pin. Default is False when left blank or not set | No | boolean |
| customer[strategic_pilot] | formData | True if this Customer is strategic pilot | No | boolean |
| customer[use_pending_state] | formData | True if this Customer can use Pending Workflow. Default is False when not set | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 404 | Not found. No Customer with the specified ID can be found |
| 422 | Could not save the Customer |

# /INFO
## ***GET*** 

**Summary:** Get API information

**Description:** 
<p>Returns information on the environment, API version, etc. No authentication
is required.</p>


### HTTP Request 
`***GET*** /info` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | ok |

# /JOB_REQUESTS
## ***GET*** 

**Summary:** List JobRequests

**Description:** 
<p>Returns a list of Job Requests, optionally paginated. Note: the maximum
number returned per page in any case is 50.</p>


### HTTP Request 
`***GET*** /job_requests` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | query | Token obtained from /authorize | Yes | string |
| page | query | The page number to start from | No | number |
| per | query | The size of the page | No | number |
| state | query | Filter Job Requests by state | No | string |
| company_id | query | Filter Job Requests by Company ID | No | string |
| multi_day_job_request_id | query | Filter Job Requests by the Multi-Day Job Request they relate to | No | number |
| classification | query | Filter Job Requests by their tax classification | No | string |
| w2_hourly_rate | query | Filter Job Requests by their W2 hourly rate | No | number |
| updated_before | query | Filter Job Requests by those that were last updated before provided DateTime | No | string |
| updated_after | query | Filter Job Requests by those that were last updated after provided DateTime | No | string |
| agent_code | query | Filter Job Requests by Company defined employee number. Enter 'Null' to get Job Requests with only empty value for the attribute | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 401 | Unauthorized |

## ***POST*** 

**Summary:** Create a JobRequest

**Description:** 

### HTTP Request 
`***POST*** /job_requests` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| job_request[request_name] | formData | A Requestor-visible name for this Job Request (not visible to Wonoloer) | Yes | string |
| job_request[zip] | formData | The zip of the work location | Yes | string |
| job_request[city] | formData | The city of the work location | Yes | string |
| job_request[address] | formData | The street address of the work location, e.g. '123 Fremont St' | Yes | string |
| job_request[slots] | formData | The number of Wonoloers required. | Yes | number |
| job_request[description_tasks] | formData | A detailed description of the work to be performed. Required unless +description+ is specified. | Yes | string |
| job_request[description] | formData | A detailed description of the work to be performed. Required unless +description_tasks+ is specified. If the below description_ fields are specified, +description+ will automatically be populated with a concatenation of those fields. | Yes | string |
| job_request[category] | formData | The category of the work to be performed, e.g. 'Customer Service'. Must be one of the pre-defined values defined for the API user's Company. | Yes | string |
| job_request[state] | formData | The Job Request's status. See the Job Request resource documentation for details. | Yes | string |
| token | formData | Token obtained from /authorize | Yes | string |
| job_request[description_company] | formData | A description of the company making this Job Request. | No | string |
| job_request[description_travel] | formData | Travel tips for the Wonoloer in performing this Job Request. | No | string |
| job_request[description_skills] | formData | Skills required to satisfy this Job Request. Multiple skills should be separated with the pipe character +|+ | No | string |
| job_request[description_contact] | formData | Who the Wonoloer should contact for any questions related to this Job Request. | No | string |
| job_request[description_arrival] | formData | Any arrival instructions for the Wonoloer. | No | string |
| job_request[start_time] | formData | The time to start work in 24-hour format. Example: 2018-08-18 19:30 | No | string |
| job_request[duration] | formData | The expected length of the Job in MINUTES. | No | number |
| job_request[venue] | formData | The name of the work location, e.g. 'Best Buy Store 321' | No | string |
| job_request[employer_id] | formData | The ID of the Requestor (Employer) requesting the work | No | number |
| job_request[wage] | formData | The wage to be paid. | No | number |
| job_request[preferred_candidate_ids] | formData | An array of Wonoloer IDs that are Preferred for this Job Request. Preferred Wonoloers are notified first and have a chance to accept before other ranked Wonoloers are notified. | No | array |
| job_request[open_request] | formData | True if this Job Request should open up to any eligible Wonoloer once all Preferred Wonoloers have been notified and a configurable time has passed | No | boolean |
| job_request[multi_day] | formData | True if this Job Request is part of a multi-day Job Request | No | boolean |
| job_request[multi_day_job_request_id] | formData | The id of the multi-day Job Request if multi-day | No | number |
| job_request[badge_requirements_attributes] | formData | Any Badges that are required to accept this Job Request | No | array |
| job_request[notification_distance] | formData | The maximum distance in MILES for notifications for this Job Request. Wonoloers whose current location is more than this distance from the Job Request location will not be notified. Overrides any default setting at the Company level. | No | number |
| job_request[ban_list] | formData | An array of Wonoloer IDs that are explicitly blocked from being notified or accepting this Job Request. | No | array |
| job_request[classification] | formData | The Job Request's tax classification. Default is 1099. | No | string |
| job_request[w2_hourly_rate] | formData | The hourly rate for W2 job requests — required with W2 classification | No | number |
| job_request[push_all_notifications_asap] | formData | Send all push notifications asap - use 'on' to set, 'off' to unset | No | string |
| job_request[can] | formData | Company defined job request number | No | string |
| job_request[agent_code] | formData | Company defined employee number - must be between 1 and 25 characters in length | No | string |
| job_request[organizational_path] | formData | Company defined notification tiers | No | string |
| job_request[use_pending_state] | formData | Enable Pending Workflow for this Job Request | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 403 | Forbidden - if you have Public Pool access only |

# /JOB_REQUESTS/{ID}
## ***PATCH*** 

**Summary:** Update a JobRequest

**Description:** 

### HTTP Request 
`***PATCH*** /job_requests/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| job_request[request_name] | formData | A Requestor-visible name for this Job Request (not visible to Wonoloer) | Yes | string |
| job_request[zip] | formData | The zip of the work location | Yes | string |
| job_request[city] | formData | The city of the work location | Yes | string |
| job_request[address] | formData | The street address of the work location, e.g. '123 Fremont St' | Yes | string |
| job_request[slots] | formData | The number of Wonoloers required. | Yes | number |
| job_request[description_tasks] | formData | A detailed description of the work to be performed. Required unless +description+ is specified. | Yes | string |
| job_request[description] | formData | A detailed description of the work to be performed. Required unless +description_tasks+ is specified. If the below description_ fields are specified, +description+ will automatically be populated with a concatenation of those fields. | Yes | string |
| job_request[category] | formData | The category of the work to be performed, e.g. 'Customer Service'. Must be one of the pre-defined values defined for the API user's Company. | Yes | string |
| job_request[state] | formData | The Job Request's status. See the Job Request resource documentation for details. | Yes | string |
| token | formData | Token obtained from /authorize | Yes | string |
| id | path | ID of the Job Request | Yes | number |
| state | formData | Use 'cancelled' if you want cancel a job request. | No | string |
| job_request[description_company] | formData | A description of the company making this Job Request. | No | string |
| job_request[description_travel] | formData | Travel tips for the Wonoloer in performing this Job Request. | No | string |
| job_request[description_skills] | formData | Skills required to satisfy this Job Request. Multiple skills should be separated with the pipe character +|+ | No | string |
| job_request[description_contact] | formData | Who the Wonoloer should contact for any questions related to this Job Request. | No | string |
| job_request[description_arrival] | formData | Any arrival instructions for the Wonoloer. | No | string |
| job_request[start_time] | formData | The time to start work in 24-hour format. Example: 2018-08-18 19:30 | No | string |
| job_request[duration] | formData | The expected length of the Job in MINUTES. | No | number |
| job_request[venue] | formData | The name of the work location, e.g. 'Best Buy Store 321' | No | string |
| job_request[employer_id] | formData | The ID of the Requestor (Employer) requesting the work | No | number |
| job_request[wage] | formData | The wage to be paid. | No | number |
| job_request[preferred_candidate_ids] | formData | An array of Wonoloer IDs that are Preferred for this Job Request. Preferred Wonoloers are notified first and have a chance to accept before other ranked Wonoloers are notified. | No | array |
| job_request[open_request] | formData | True if this Job Request should open up to any eligible Wonoloer once all Preferred Wonoloers have been notified and a configurable time has passed | No | boolean |
| job_request[multi_day] | formData | True if this Job Request is part of a multi-day Job Request | No | boolean |
| job_request[multi_day_job_request_id] | formData | The id of the multi-day Job Request if multi-day | No | number |
| job_request[badge_requirements_attributes] | formData | Any Badges that are required to accept this Job Request | No | array |
| job_request[notification_distance] | formData | The maximum distance in MILES for notifications for this Job Request. Wonoloers whose current location is more than this distance from the Job Request location will not be notified. Overrides any default setting at the Company level. | No | number |
| job_request[ban_list] | formData | An array of Wonoloer IDs that are explicitly blocked from being notified or accepting this Job Request. | No | array |
| job_request[classification] | formData | The Job Request's tax classification. Default is 1099. | No | string |
| job_request[w2_hourly_rate] | formData | The hourly rate for W2 job requests — required with W2 classification | No | number |
| job_request[push_all_notifications_asap] | formData | Send all push notifications asap - use 'on' to set, 'off' to unset | No | string |
| job_request[can] | formData | Company defined job request number | No | string |
| job_request[agent_code] | formData | Company defined employee number - must be between 1 and 25 characters in length | No | string |
| job_request[organizational_path] | formData | Company defined notification tiers | No | string |
| job_request[use_pending_state] | formData | Enable Pending Workflow for this Job Request | No | boolean |

**Responses**

| Code | Description |
| ---- | ----------- |
| 403 | Forbidden - if you have Public Pool access only |

## ***GET*** 

**Summary:** Get a specific JobRequest

**Description:** 

### HTTP Request 
`***GET*** /job_requests/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | query | Token obtained from /authorize | Yes | string |
| id | path | ID of Job Request | Yes | number |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | ok |

# /JOB_REQUESTS/{ID}/RANKINGS
## ***GET*** 

**Summary:** List the Wonoloers that are ranked for this JobRequest

**Description:** 
<p>Returns details of the Wonoloers that were ranked for this JobRequest, in
ranked order.</p>


### HTTP Request 
`***GET*** /job_requests/{id}/rankings` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | query | Token obtained from /authorize | Yes | string |
| id | path | ID of Job Request | Yes | number |

**Responses**

| Code | Description |
| ---- | ----------- |
| 403 | Forbidden - if you have Public Pool access only |

# /JOB_REQUESTS/{ID}/RE_RANK_WORKERS
## ***POST*** 

**Summary:** Re-rank workers for this JobRequest

**Description:** 

### HTTP Request 
`***POST*** /job_requests/{id}/re_rank_workers` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | formData | Token obtained from /authorize | Yes | string |
| id | path | ID of Job Request | Yes | number |

**Responses**

| Code | Description |
| ---- | ----------- |
| 403 | Forbidden - if you have Public Pool access only |

# /JOB_REQUESTS/{ID}/RESEND_NOTIFICATIONS
## ***POST*** 

**Summary:** Resend notifications for this JobRequest

**Description:** 
<p>If the JobRequest has Preferred Wonoloers, Preferred Notifications will
first be resent to those Preferred Wonoloers who have not already accepted
the JobRequest.</p>

<p>If the JobRequest does not have Preferred Wonoloers, the available Wonoloer
pool will be re-ranked and Wonoloers notified in resulting ranked order.</p>

<p>NB: in both cases, the Wonoloers notified will not necessarily be - and are
unlikely to be - exactly the same list as the prior time notifications were
sent.</p>
<hr>


### HTTP Request 
`***POST*** /job_requests/{id}/resend_notifications` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | formData | Token obtained from /authorize | Yes | string |
| id | path | ID of Job Request | Yes | number |
| push_all_notifications_asap | formData | Send all push notifications asap - use 'on' to set, 'off' to unset | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 403 | Forbidden - if you have Public Pool access only |

# /JOBS
## ***GET*** 

**Summary:** List Jobs

**Description:** 
<p>Returns a list of Jobs, optionally paginated. Note: the maximum number
returned per page in any case is 50.</p>


### HTTP Request 
`***GET*** /jobs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | query | Token obtained from /authorize | Yes | string |
| page | query | The page number to start from | No | number |
| per | query | The size of the page | No | number |
| state | query | Filter Jobs by state | No | string |
| job_request_id | query | List jobs for the specified Job Request | No | number |
| classification | query | Return jobs by a specific tax classification | No | string |
| w2_hourly_rate | query | Return jobs by a specific hourly rate | No | number |
| w2_pay_status | query | Return jobs by a specific pay status (not_started pending paid) | No | string |
| updated_before | query | Return jobs by those that were last updated before provided DateTime | No | string |
| updated_after | query | Return jobs by those that were last updated after provided DateTime | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 401 | Unauthorized |

## ***POST*** 

**Summary:** Create a Job

**Description:** 

### HTTP Request 
`***POST*** /jobs` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| job[job_request_id] | formData | ID of the Job Request being fulfilled by this Job | Yes | number |
| job[worker_id] | formData | ID of the Worker to perform the Job | Yes | number |
| token | formData | Token obtained from /authorize | Yes | string |
| job[requestor_notes] | formData | Arbitary text to be attached to this Job - not visible to Worker | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 403 | Forbidden - if you have Public Pool access only |

# /JOBS/ASSIGN
## ***POST*** 

**Summary:** Assign a Job

**Description:** 

### HTTP Request 
`***POST*** /jobs/assign` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| job[job_request_id] | formData | ID of the Job Request being fulfilled by this Job | Yes | number |
| job[worker_id] | formData | ID of the Worker to perform the Job | Yes | number |
| token | formData | Token obtained from /authorize | Yes | string |
| job[requestor_notes] | formData | Arbitary text to be attached to this Job - not visible to Worker | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 403 | Forbidden - if you have Public Pool access only |

# /JOBS/{ID}
## ***PATCH*** 

**Summary:** Update a Job

**Description:** 

### HTTP Request 
`***PATCH*** /jobs/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | formData | Token obtained from /authorize | Yes | string |
| id | path |  | Yes | number |
| state | formData | Use 'cancelled' if you want cancel a job. | No | string |
| actual_duration | formData | The actual duration of a job, in minutes | No | number |
| cancelled_reason | formData | Give a reason such as 'admin_cancelled', 'decided_to_cancel', or 'asked_to_cancel' so that the worker will not receive notifications for this job again | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 403 | Forbidden - if you have Public Pool access only |

## ***GET*** 

**Summary:** Get a specific Job

**Description:** 

### HTTP Request 
`***GET*** /jobs/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | query | Token obtained from /authorize | Yes | string |
| id | path |  | Yes | number |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | ok |

# /MESSAGES
## ***GET*** 

**Summary:** List Messages

**Description:** 
<p>Returns a list of Messages, optionally paginated. Note: the maximum number
returned per page in any case is 50.</p>


### HTTP Request 
`***GET*** /messages` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | query | Token obtained from /authorize | Yes | string |
| page | query | The page number to start from | No | number |
| per | query | The size of the page | No | number |
| job_id | query | Filter Messages by Job | No | number |
| sender_id | query | Filter Messages by Sender (User ID) | No | number |
| receiver_id | query | Filter Messages by Receiver (User ID) | No | number |

**Responses**

| Code | Description |
| ---- | ----------- |
| 401 | Unauthorized |

## ***POST*** 

**Summary:** Create a Message

**Description:** 

### HTTP Request 
`***POST*** /messages` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| message[body] | formData | The text content of this Message | Yes | string |
| message[job_id] | formData | ID of the Job to which this Message relates | Yes | number |
| message[receiver_id] | formData | User ID of recipient of this Message. Can be a Wonoloer or a Requestor | Yes | number |
| message[sender_id] | formData | User ID of sender of this Message. Can be a Wonoloer or a Requestor | Yes | number |
| token | formData | Token obtained from /authorize | Yes | string |
| message[image_url] | formData | The URL of an image to accompany this Message | No | string |
| message[read_at] | formData | If read, when this message was read | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 401 | Unauthorized |

# /MESSAGES/{ID}
## ***GET*** 

**Summary:** Get a specific Message

**Description:** 

### HTTP Request 
`***GET*** /messages/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | query | Token obtained from /authorize | Yes | string |
| id | path | ID of Message | Yes | number |

**Responses**

| Code | Description |
| ---- | ----------- |
| 401 | Unauthorized |

# /MULTI_DAY_JOB_REQUESTS
## ***POST*** 

**Summary:** Create a Multi-day Job Request

**Description:** 

### HTTP Request 
`***POST*** /multi_day_job_requests` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| multi_day_job_request[repeat_type] | formData | The repeat interval for this Job Request. Note that individual Job Requests can be removed from a Multi-Day Job Request after creation so this repeat may not match the actual days. | Yes | string |
| token | formData | Token obtained from /authorize | Yes | string |
| multi_day_job_request[same_workers] | formData | True if the Requestor wants the same Wonoloers each day | No | boolean |
| multi_day_job_request[repeat_number] | formData | How many days (occurences) this Multi-Day Job Request comprised when initially created. See prior note. | No | number |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | ok |

# /MULTI_DAY_JOB_REQUESTS/{ID}
## ***PATCH*** 

**Summary:** Update a Multi-day Job Request

**Description:** 

### HTTP Request 
`***PATCH*** /multi_day_job_requests/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| multi_day_job_request[repeat_type] | formData | The repeat interval for this Job Request. Note that individual Job Requests can be removed from a Multi-Day Job Request after creation so this repeat may not match the actual days. | Yes | string |
| token | formData | Token obtained from /authorize | Yes | string |
| id | path | ID of the Multi-day Job Request | Yes | number |
| multi_day_job_request[same_workers] | formData | True if the Requestor wants the same Wonoloers each day | No | boolean |
| multi_day_job_request[repeat_number] | formData | How many days (occurences) this Multi-Day Job Request comprised when initially created. See prior note. | No | number |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | ok |

## ***GET*** 

**Summary:** Get a specific Multi-day Job Request

**Description:** 

### HTTP Request 
`***GET*** /multi_day_job_requests/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | query | Token obtained from /authorize | Yes | string |
| id | path | ID of the Multi-day Job Request | Yes | number |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | ok |

# /SEARCH
## ***GET*** 

**Summary:** Search Wonolo

**Description:** 
<p>Searches common attributes of the most common Wonolo models</p>


### HTTP Request 
`***GET*** /search` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| q | query | The search parameter | Yes | string |
| token | query | Token obtained from /authorize | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | ok |

# /SYNC_AUTH_TOKEN
## ***POST*** 

**Summary:** sync auth_token for external user

**Description:** 
<p>Sync auth token from Wonolo server to external server</p>


### HTTP Request 
`***POST*** /sync_auth_token` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| created_at | formData | the created time of user session token | Yes | string |
| auth_token | formData | the auth token of user who need to be synced | Yes | string |
| synced_worker_id | formData | the id of user on the external server | Yes | number |
| token | formData | Token obtained from /authorize | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | ok |

# /USERS
## ***GET*** 

**Summary:** List users

**Description:** 
<p>Returns a list of Users, optionally paginated. Note: the maximum number
returned per page in any case is 50.</p>


### HTTP Request 
`***GET*** /users` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | query | Token obtained from /authorize | Yes | string |
| page | query | The page number to start from | No | number |
| per | query | The size of the page | No | number |
| type | query | Filter Users by type - either 'Worker' or 'Employer' | No | string |
| email | query | Filter Users by email | No | string |
| first_name | query | Filter Users by first name - should contain only letters, numbers, dash (-) and period (.) character | No | string |
| last_name | query | Filter Users by last name - should contain only letters, numbers, dash (-) and period (.) character | No | string |
| external_id | query | Filter Users by external id(s) - separate multiple external ids with commas | No | string |
| onboarding_last_state | query | Filter Users by onboarding state(s) - separate multiple states with commas | No | string |
| w2_onboarding_status | query | Filter users by W2 onboarding states(s) - separate multiple states with commas | No | string |
| w2_employee_id | query | Filter Users by their W2 employee ID | No | string |
| address_state | query | Filter Users by address state - separate multiple states with commas | No | string |
| drug_tested | query | Filter Users by drug test results - separate multiple states with commas | No | string |
| updated_before | query | Filter Users by those that were last updated before provided DateTime | No | string |
| updated_after | query | Filter Users by those that were last updated after provided DateTime | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 401 | Unauthorized - you did not pass a valid token |

## ***POST*** 

**Summary:** Create a user

**Description:** 

### HTTP Request 
`***POST*** /users` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| user[customer_id] | formData | Employer's customer ID. This attribute is used for Employers only. | Yes | number |
| user[role] | formData | Employer's role. This attribute is used for Employers only. | Yes | string |
| user[user_badges_attributes][badge_id] | formData | The ID of the Badge. This attribute is used for Workers only. | Yes | number |
| user[synced_worker_id] | formData | Worker's ID on an external server, used for syncing purposes. This attribute is used for Workers only. | Yes | number |
| user[last_name] | formData | User last name - should contain only letters, numbers, dash (-) and period (.) character | Yes | string |
| user[first_name] | formData | User first name - should contain only letters, numbers, dash (-) and period (.) character | Yes | string |
| user[password_confirmation] | formData | Must be specified and match password, if specified. | Yes | string |
| user[password] | formData | Password. Minimum 8 characters. Must be specified on creation. | Yes | string |
| user[email] | formData | User email - must be unique. | Yes | string |
| user[type] | formData | The type of User - Worker = Wonoloer, Employer = Requestor | Yes | string |
| token | formData | Token obtained from /authorize | Yes | string |
| user[gender] | formData | User's gender | No | string |
| user[avatar_url] | formData |  | No | string |
| user[address] | formData |  | No | string |
| user[city] | formData |  | No | string |
| user[address_state] | formData |  | No | string |
| user[zip] | formData |  | No | string |
| user[phone] | formData |  | No | string |
| user[suspended] | formData | True if the User is currently suspended | No | boolean |
| user[suspended_at] | formData |  | No | string |
| user[rating] | formData | User's current rating (out of 5.0) | No | number |
| user[agreed_to_terms] | formData | True if the User has agreed to terms | No | boolean |
| user[agreed_to_terms_date] | formData |  | No | string |
| user[external_id] | formData | An arbitrary value to be associated with this Worker. This attribute is used for Workers only. | No | string |
| user[onboarding_last_state] | formData | Worker's last onboarding state. This attribute is used for Workers only. | No | string |
| user[w2_employee_id] | formData | Worker's unique employee ID for W2 classified jobs. This attribute is used for Workers only. | No | string |
| user[drug_tested] | formData | Worker's drug test results. This attribute is used for Workers only. | No | string |
| user[verified_phone] | formData | Worker's verified phone. This attribute is used for Workers only. | No | string |
| user[phone_verified_at] | formData | This attribute is used for Workers only. | No | string |
| user[user_badges_attributes][id] | formData | The ID of the current User-Badge association between this Worker and a badge - required for the '_destroy' function below. This attribute is used for Workers only. | No | number |
| user[user_badges_attributes][_destroy] | formData | Set to remove this User-Badge association on updating a Worker (PATCH). This attribute is used for Workers only. | No | string |
| user[title] | formData | Employer's title. This attribute is used for Employers only. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 403 | Forbidden - if you have Public Pool access only |

# /USERS/INVITE
## ***POST*** 

**Summary:** Invite worker into our system

**Description:** 

### HTTP Request 
`***POST*** /users/invite` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| user[type] | formData | The type of User - Worker = Wonoloer | Yes | string |
| user[phone] | formData |  | Yes | string |
| user[last_name] | formData | Worker last name - should contain only letters, numbers, dash (-) and period (.) character | Yes | string |
| user[first_name] | formData | Worker first name - should contain only letters, numbers, dash (-) and period (.) character | Yes | string |
| token | formData | Token obtained from /authorize | Yes | string |
| user[email] | formData | Worker email | No | string |
| user[external_id] | formData | the id of user on the external server | No | number |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | ok |

# /USERS/{ID}
## ***PATCH*** 

**Summary:** Update a user

**Description:** 

### HTTP Request 
`***PATCH*** /users/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| user[customer_id] | formData | Employer's customer ID. This attribute is used for Employers only. | Yes | number |
| user[role] | formData | Employer's role. This attribute is used for Employers only. | Yes | string |
| user[user_badges_attributes][badge_id] | formData | The ID of the Badge. This attribute is used for Workers only. | Yes | number |
| user[synced_worker_id] | formData | Worker's ID on an external server, used for syncing purposes. This attribute is used for Workers only. | Yes | number |
| user[last_name] | formData | User last name - should contain only letters, numbers, dash (-) and period (.) character | Yes | string |
| user[first_name] | formData | User first name - should contain only letters, numbers, dash (-) and period (.) character | Yes | string |
| user[password_confirmation] | formData | Must be specified and match password, if specified. | Yes | string |
| user[password] | formData | Password. Minimum 8 characters. Must be specified on creation. | Yes | string |
| user[email] | formData | User email - must be unique. | Yes | string |
| user[type] | formData | The type of User - Worker = Wonoloer, Employer = Requestor | Yes | string |
| user[id] | formData | Unique ID of the User | Yes | number |
| token | formData | Token obtained from /authorize | Yes | string |
| id | path |  | Yes | number |
| user[gender] | formData | User's gender | No | string |
| user[avatar_url] | formData |  | No | string |
| user[address] | formData |  | No | string |
| user[city] | formData |  | No | string |
| user[address_state] | formData |  | No | string |
| user[zip] | formData |  | No | string |
| user[phone] | formData |  | No | string |
| user[suspended] | formData | True if the User is currently suspended | No | boolean |
| user[suspended_at] | formData |  | No | string |
| user[rating] | formData | User's current rating (out of 5.0) | No | number |
| user[agreed_to_terms] | formData | True if the User has agreed to terms | No | boolean |
| user[agreed_to_terms_date] | formData |  | No | string |
| user[external_id] | formData | An arbitrary value to be associated with this Worker. This attribute is used for Workers only. | No | string |
| user[onboarding_last_state] | formData | Worker's last onboarding state. This attribute is used for Workers only. | No | string |
| user[w2_employee_id] | formData | Worker's unique employee ID for W2 classified jobs. This attribute is used for Workers only. | No | string |
| user[drug_tested] | formData | Worker's drug test results. This attribute is used for Workers only. | No | string |
| user[verified_phone] | formData | Worker's verified phone. This attribute is used for Workers only. | No | string |
| user[phone_verified_at] | formData | This attribute is used for Workers only. | No | string |
| user[user_badges_attributes][id] | formData | The ID of the current User-Badge association between this Worker and a badge - required for the '_destroy' function below. This attribute is used for Workers only. | No | number |
| user[user_badges_attributes][_destroy] | formData | Set to remove this User-Badge association on updating a Worker (PATCH). This attribute is used for Workers only. | No | string |
| user[title] | formData | Employer's title. This attribute is used for Employers only. | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 403 | Forbidden - if you have Public Pool access only |

## ***GET*** 

**Summary:** Get a specific user

**Description:** 

### HTTP Request 
`***GET*** /users/{id}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | query | Token obtained from /authorize | Yes | string |
| id | path |  | Yes | number |

**Responses**

| Code | Description |
| ---- | ----------- |
| 401 | Unauthorized |
| 404 | Not found. No User with the specified ID can be found |

# /USERS/{ID}/TRACKING
## ***GET*** 

**Summary:** Get tracking data for a specific user

**Description:** 

### HTTP Request 
`***GET*** /users/{id}/tracking` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| token | query | Token obtained from /authorize | Yes | string |
| id | path |  | Yes | number |

**Responses**

| Code | Description |
| ---- | ----------- |
| 403 | Forbidden - if you have Public Pool access only |

<!-- Converted with the swagger-to-slate https://github.com/lavkumarv/swagger-to-slate -->
