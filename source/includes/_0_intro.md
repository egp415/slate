
#Welcome to the Wonolo API

Wonolo is an on demand staffing platform providing employers with a low cost option to find pre-screened workers to fill jobs quickly and reliably based on their particular needs.

The Wonolo API provides a mechanism to integrate customized applications and proprietary workflows with this platform.  Integration points could include automation for software responsible for scheduling and timekeeping or HR/CRM systems.  Individual systems can work directly with the API in a decentralized fashion through secure, standards based protocols.


The Wonolo API (V2.0) is a <a
href="https://en.wikipedia.org/wiki/Representational_state_transfer">RESTful</a>
API to perform <a
href="https://en.wikipedia.org/wiki/Create,_read,_update_and_delete">CRUD</a>
operations on Wonolo platform resources.

Currently, JSON is the only encoding format supported.

#Getting Started

##API Keys

Use of the Wonolo API requires keys. To obtain API keys, please <a
href="http://bit.ly/1Wk0ekp">apply here</a>.

##Test and Production Environments

You will be issued with two sets of API keys:

- **test** (starting with `pk_test` and `sk_test`) - for use with <a
href="https://test.wonolo.com/api_v2">test.wonolo.com/api_v2</a>

- **production** (starting with `pk_live` and `sk_live`) - for use with <a
href="https://api.wonolo.com/api_v2">api.wonolo.com/api_v2</a>


##Security
All API calls must be made over HTTPS.

With the exception of <code>/authenticate</code> and <code>/info</code>,
all API calls must use an authorization token (passed as the
`token` parameter).

##Webhooks

Webhooks allow your system to be notified of changes to certain Wonolo
resources via an HTTP call initiated from the Wonolo platform.

Currently, webhooks are available for state changes to
`JobRequest` and `Job` resources.

###Webhook Security

Webhooks are authenticated using a <code>X-Wonolo-Webhook-Token</code> HTTP
header.  This header is set to a SHA256 digest of the webhook&#39;s JSON
body concatenated with your secret API key.

###Configuring Webhooks

To enable webhooks, please first obtain your API keys and then <a
href="mailto:support@wonolo.com?subject=Webhooks">contact us</a>.

##Access Control / Privilege Level

Wonolo API keys will provide one of two different levels of access to
Wonolo resources:

- **Public Pool** access - if you are accessing Wonolo&#39;s
public pool of Wonoloers

- **Private Pool** access - if your company is managing its own
private pool of workers

With **Public Pool** access, you will only be able to access
those Wonoloers you have active Jobs with, and Job Requests and Jobs that
you have created. Also, write operations (`update/PATCH` and `create/POST`) are
forbidden in many cases.

For more details, consult the documentation of the individual endpoints.

##Obtaining a Token

Once you receive your API keys, the first step is to authenticate to obtain
a token for use with subsequent API calls. Please refer to the
<code>/api_v2/authenticate</code> endpoint documentation.

```shell
curl -X POST \
  'https://test.wonolo.com/api_v2/authenticate?api_key=pk_live_[your_key]&secret_key=sk_live_[your_key]'
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://test.wonolo.com/api_v2/authenticate?api_key=pk_live_[yourkey]&secret_key=sk_live_[yourkey]");
xhr.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");


xhr.send(data);

```

##Entities in the API

In order to understand the API and start working with it, it first helps to understand the core entities of the API and their relationship to the mobile apps and the Customer Portal.

**Users**
Users represent both Workers (or “Wonoloers” — those who are hired for a job) as well as Employers (sometimes also called Requesters) who post and manage jobs.

**Job Requests**
Job Requests represent some work to be done — e.g. “I need 10 people tomorrow to stack boxes for 8 hours, starting at 10am” 
 							
**Jobs**
Jobs represent the act of one Worker doing the work.  There is a 1-n relationship between Job Requests and Jobs.  When a Worker accepts a Job Request, a Job is created linking the Worker with the Job Request
			
Note that the word “job” is often used loosely to refer to both Job Requests and Jobs. In this document, the capitalized versions are used to specifically refer to Job Requests vs Jobs and the lowercase version is used in the more general sense. 

**Badges**						
Badges represent a skill, certification or experience that can be assigned to workers and required for jobs.
