## Document Discovery 


> Request example to "Discover related documents" - `POST fromURL`...

```shell
curl --ssl-reqd --include --request POST --data url=https%3A%2F%2Fwww.theguardian.com%2Fworld%2F2016%2Fjul%2F22%2Fmissing-flight-mh370-hunt-for-debris-will-not-be-extended "https://api.yonderlabs.com/1.0/textcollection/documentdiscovery/fromURL?collection_name=scrooge&access_token=YOUR_ACCESS_TOKEN"
```

>... and response header and body (202 "ACCEPTED"):

```
HTTP/1.1 202 ACCEPTED
Server: nginx/1.4.6 (Ubuntu)
Date: Thu, 26 Oct 2017 10:50:27 GMT
Content-Type: application/json
Content-Length: 157
Connection: keep-alive
API-instance: instance01
```
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
curl --ssl-reqd --include --request POST --data text="The hunt for Malaysia Airlines flight MH370 is to be suspended if evidence of the missing jet is not found in the current search area. The transport ministers of Australia, Malaysia and China, representing the country leading the search, the airline and the home of the majority of its passengers, met to discuss the future of the search in the Malaysian federal administrative centre of Putrajaya on Friday. They announced that [...]" "https://api.yonderlabs.com/1.0/textcollection/documentdiscovery/fromText?collection_name=scrooge&access_token=YOUR_ACCESS_TOKEN"
```

>... and response header and body (202 "ACCEPTED"):

```
HTTP/1.1 202 ACCEPTED
Server: nginx/1.4.6 (Ubuntu)
Date: Thu, 26 Oct 2017 10:50:27 GMT
Content-Type: application/json
Content-Length: 157
Connection: keep-alive
API-instance: instance01
```
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
curl --ssl-reqd --header "API-instance: instance01" --request GET "https://api.yonderlabs.com/1.0/textcollection/documentdiscovery?task_id=8292fd19-6c94-4570-90bf-c7d2f0afb9ed&access_token=YOUR_ACCESS_TOKEN"
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

Please notice that the `--include` in the `POST` call displays the response header, which includes the `API-instance` field. The value of `API-instance` field (e.g. `instance01`) must be included later in the following `GET` call.

Parameter | Type | Description | Values |
--------- | ------- | ----------- | ------ |
collection_name | string, required | the name of the Text Collection  | - |
url | string, required |the url of the text | use [url-encoding](http://www.url-encode-decode.com/)|
access_token | string, required | your access token (40 digits) | - |

### Discover related documents in a Collection - `POST fromText` 

Given a text, this API allows you to discover other contextually relevant documents by retrieving them from a Text Collection.
As detailed in the right panel, as an immediate response to this API, you will get a `202` answer ("ACCEPTED") containing a task identifier `task_id` to be used later in the `GET` call.

Please notice that the `--include` in the `POST` call displays the response header, which includes the `API-instance` field. The value of `API-instance` field (e.g. `instance01`) must be included later in the following `GET` call.

Parameter | Type | Description | Values |
--------- | ------- | ----------- | ------ |
collection_name | string, required | the name of the Text Collection | - |
text | string, required |the text document | pass the text between "" (e.g. "This is an example") or use [url-encoded](http://www.url-encode-decode.com/) text|
access_token | string, required | your access token (40 digits) | - |

### Get results from Document Discovery - `GET` 

This API allows you to retrieve most related documents contained in a Text Collection.
Please notice that the value of the `API-instance` field shown in the response header of the previous `POST` call (e.g. `instance01`) must be included in the `GET` call after the option `--header`, as detailed in the right panel.


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
