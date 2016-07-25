## Document Discovery 


> Request example to "Discover related documents" - `POST fromURL`...

```shell
curl --ssl-reqd --request POST --data url=https%3A%2F%2Fwww.theguardian.com%2Fworld%2F2016%2Fjul%2F22%2Fmissing-flight-mh370-hunt-for-debris-will-not-be-extended "https://vm3.yonderlabs.com/1.0/textcollection/documentdiscovery/fromURL?collection_name=scrooge&access_token=YOUR_ACCESS_TOKEN"
```

>... and response body (202 "ACCEPTED"):

```json
{
  "task_type": "DocumentDiscoveryAPI", 
  "task_id": "8292fd19-6c94-4570-90bf-c7d2f0afb9ed", 
  "url": "https://www.theguardian.com/world/2016/jul/22/missing-flight-mh370-hunt-for-debris-will-not-be-extended", 
  "collection_name": "scrooge", 
  "text": "The hunt for Malaysia Airlines flight MH370 is to be suspended if evidence of the missing jet is not found in the current search area. The transport ministers of Australia, Malaysia and China, representing the country leading the search, the airline and the home of the majority of its passengers, met to discuss the future of the search in the Malaysian federal administrative centre of Putrajaya on Friday. They announced that [...]", 
  "task_status": "PENDING"
}
```


> Request example to "Discover related documents" - `POST fromText`...

```shell
curl --ssl-reqd --request POST --data text="The hunt for Malaysia Airlines flight MH370 is to be suspended if evidence of the missing jet is not found in the current search area. The transport ministers of Australia, Malaysia and China, representing the country leading the search, the airline and the home of the majority of its passengers, met to discuss the future of the search in the Malaysian federal administrative centre of Putrajaya on Friday. They announced that [...]" "https://vm3.yonderlabs.com/1.0/textcollection/documentdiscovery/fromText?collection_name=scrooge&access_token=YOUR_ACCESS_TOKEN"
```

>... and response body (202 "ACCEPTED"):

```json
{
  "task_type": "DocumentDiscoveryAPI", 
  "task_id": "8292fd19-6c94-4570-90bf-c7d2f0afb9ed", 
  "url": null, 
  "collection_name": "scrooge", 
  "text": "The hunt for Malaysia Airlines flight MH370 is to be suspended if evidence of the missing jet is not found in the current search area. The transport ministers of Australia, Malaysia and China, representing the country leading the search, the airline and the home of the majority of its passengers, met to discuss the future of the search in the Malaysian federal administrative centre of Putrajaya on Friday. They announced that [...]", 
  "task_status": "PENDING"
}
```


> Request example to "Get related documents" - `GET`...

```shell
curl --ssl-reqd --request GET "https://vm3.yonderlabs.com/1.0/textcollection/documentdiscovery?task_id=8292fd19-6c94-4570-90bf-c7d2f0afb9ed&access_token=YOUR_ACCESS_TOKEN"
```

>... and response body, case 1) SUCCESS, i.e. the task is over:

```json
{
  "task_error": null, 
  "task_type": "DocumentDiscoveryAPI", 
  "task_id": "8292fd19-6c94-4570-90bf-c7d2f0afb9ed", 
  "url": "https://www.theguardian.com/world/2016/jul/22/missing-flight-mh370-hunt-for-debris-will-not-be-extended", 
  "collection_name": "scrooge", 
  "task_result": {
    "timestamp": "2015-12-29 16:28:06.517297", 
    "discovery_list": [
      {
        "score": 0.24134128928939388, 
        "id": "5661ce38b1f53961fbb5bb25"
      }, 
      {
        "score": 0.18162858119988462, 
        "id": "5661ce38b1f53961fbb5bb24"
      }, 
      {
        "score": 0.15711326735569822, 
        "id": "5661ce38b1f53961fbb5bb29"
      }
    ]
  }, 
  "text": "The hunt for Malaysia Airlines flight MH370 is to be suspended if evidence of the missing jet is not found in the current search area. The transport ministers of Australia, Malaysia and China, representing the country leading the search, the airline and the home of the majority of its passengers, met to discuss the future of the search in the Malaysian federal administrative centre of Putrajaya on Friday. They announced that [...]", 
  "task_status": "SUCCESS"
}
```

>... and response body, case 2) STARTED (the task has started, but it is not over):

```json
{
  "task_type": "DocumentDiscoveryAPI", 
  "task_id": "8292fd19-6c94-4570-90bf-c7d2f0afb9ed", 
  "task_status": "STARTED"
}
```

>... and response body, case 3) PENDING (the task is still pending):

```json
{
  "task_type": "DocumentDiscoveryAPI", 
  "task_id": "8292fd19-6c94-4570-90bf-c7d2f0afb9ed", 
  "task_status": "PENDING"
}
```


**Suggest other documents relevant to your text from a Text Collection**

Based on the provided text, this API suggests other contextually relevant documents by retrieving them from a Text Collection.

<aside class="notice">
Depending on the size of the Text Collection, this service might take up to few minutes to provide a full answer. 
</aside>


### Discover related documents in a Collection - `POST fromURL` 

Given an URL, this API allows you to discover other contextually relevant documents by retrieving them from a Text Collection.
As detailed in the right panel, as an immediate response to this API, you will get a `202` answer ("ACCEPTED") containing a task identifier `task_id` to be used later in the `GET` call. 

Parameter | Type | Description | Values |
--------- | ------- | ----------- | ------ |
collection_name | string, required | the name of the Text Collection  | - |
url | string, required |the url of the text | use [url-encoding](http://www.url-encode-decode.com/)|
access_token | string, required | your access token (40 digits) | - |

### Discover related documents in a Collection - `POST fromText` 

Given a text, this API allows you to discover other contextually relevant documents by retrieving them from a Text Collection.
As detailed in the right panel, as an immediate response to this API, you will get a `202` answer ("ACCEPTED") containing a task identifier `task_id` to be used later in the `GET` call.

Parameter | Type | Description | Values |
--------- | ------- | ----------- | ------ |
collection_name | string, required | the name of the Text Collection | - |
text | string, required |the text document | pass the text between "" (e.g. "This is an example") or use [url-encoded](http://www.url-encode-decode.com/) text|
access_token | string, required | your access token (40 digits) | - |

### Get results from Document Discovery - `GET` 

This API allows you to retrieve most related documents contained in a Text Collection.


Parameter | Type | Description | 
--------- | ------- | ----------- | 
task_id | string, required | the identifier of the created Document Discovery task| 
access_token | string, required | your access token (40 digits) | 

If results are ready (i.e. document similarities have been computed) you will get a `200` answer ("SUCCESS") and the resulting ouput, as detailed in the right panel.
If the process is still ongoing you will get an adequate status code answer ("STARTED" or "PENDING") meaning that you have to try again a bit later with another `GET` call. 

<aside class="notice">
In case of SUCCESS, results are promptly deleted afterwards, i.e. performing another GET on the same task_id will return no results.
</aside>
<aside class="success">
Remember — insert your credentials for authentication!
</aside>
