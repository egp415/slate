#Managing Badges

> Creating a Badge

```shell
curl -X POST \
  'https://test.wonolo.com/api_v2/badges?token=VEzCnWyk1uFWEqyyuzhd' \
  -H 'Content-Type: application/json' \
  -d '
{
            "name": "Example Badge",
            "description":"A badge created as an example",
            "icon_url": null,
            "is_soft": false
        }
'
```	

```javascript
var data = JSON.stringify({
  "name": "Example Badge",
  "description": "A badge created as an example",
  "icon_url": null,
  "is_soft": false
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://test.wonolo.com/api_v2/badges?token=VEzCnWyk1uFWEqyyuzhd");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.send(data);
```

A Badge represents a qualification, certification or skill that a worker can acquire and which can be specified as required for a particular job for which an employer is hiring.  Examples include a forklift driver certificate, basic first-aid, or license to sell insurance in a particular state.  Workers can have any number of badges (see Assigning Badges to Workers)

Unless a badge is considered a “soft requirement”, if the worker doesn’t have the Badge, they can’t accept the job and in most cases, if the worker doesn’t have a required Badge, they won’t even be able to see the job posting.
 										 			
Customers should define the set of Badges (and their hierarchy) that represents their business needs and this should be done earlier in developing their project plan. 	

See the reference documentation for <A HREF="#badges">Badges</A>					 		

[TODO:  ownership / hierarchy / security around badges ? ]