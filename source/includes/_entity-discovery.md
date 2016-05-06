## Entity Discovery 

> Request example to "Discover related entities" - `POST fromURL`...


```shell
curl --ssl-reqd --request POST --data url=http%3A%2F%2Fwww.theatlantic.com%2Finternational%2Farchive%2F2015%2F11%2Frussia-doping-2016-olympics%2F416604%2F "https://vm3.yonderlabs.com/1.0/textcollection/entitydiscovery/fromURL?collection_name=scrooge&limit=5&access_token=YOUR_ACCESS_TOKEN"
```

>... and response body (202 "ACCEPTED"):

```json
{
  "task_type": "EntityDiscoveryAPI", 
  "task_id": "8292fd19-6c94-4570-90bf-c7d2f0afb9ed", 
  "url": "http://www.theatlantic.com/international/archive/2015/11/russia-doping-2016-olympics/416604/", 
  "collection_name": "scrooge", 
  "text": "With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...].", 
  "task_status": "PENDING"
}
```


> Request example to "Discover related entities" - `POST fromText`...

```shell
curl --ssl-reqd --request POST --data text="With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...]." "https://vm3.yonderlabs.com/1.0/textcollection/entitydiscovery/fromText?collection_name=scrooge&limit=5&access_token=YOUR_ACCESS_TOKEN"
```


>... and response body (202 "ACCEPTED"):

```json
{
  "task_type": "EntityDiscoveryAPI", 
  "task_id": "8292fd19-6c94-4570-90bf-c7d2f0afb9ed", 
  "url": null, 
  "collection_name": "scrooge", 
  "text": "With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...].", 
  "task_status": "PENDING"
}
```


> Request example to "Get related entities" - `GET`...

```shell
curl --ssl-reqd --request GET "https://vm3.yonderlabs.com/1.0/textcollection/entitydiscovery?task_id=8292fd19-6c94-4570-90bf-c7d2f0afb9ed&access_token=YOUR_ACCESS_TOKEN"
```

>... and response body, case 1) SUCCESS, i.e. the task is over:

```json
{
  "task_error": null,
  "task_type": "EntityDiscoveryAPI",
  "task_id": "8292fd19-6c94-4570-90bf-c7d2f0afb9ed",
  "url": "http://www.theatlantic.com/international/archive/2015/11/russia-doping-2016-olympics/416604/",
  "collection_name": "scrooge",
  "task_result": {
    "timestamp": "2016-05-06 09:58:00.787070",
    "limit": 5,
    "entities": [
      {
        "count": 1,
        "info": "Russia also officially known as the Russian Federation is a sovereign state in northern Eurasia [...]",
        "type": "WHERE",
        "name": "Russia",
        "graph": {
          "is_in_graph": true,
          "neighbors": [
            {
              "edge_weight": 0.02197802197802198,
              "id": 0,
              "edge_count": 2
            },
            {
              "edge_weight": 0.02197802197802198,
              "id": 2,
              "edge_count": 2
            },
            {
              "edge_weight": 0.01098901098901099,
              "id": 3,
              "edge_count": 1
            },
            {
              "edge_weight": 0.01098901098901099,
              "id": 4,
              "edge_count": 1
            },
            {
              "edge_weight": 0.01098901098901099,
              "id": 5,
              "edge_count": 1
            }
          ],
          "id": 1,
          "weight": 0.012578616352201259
        }
      }
    ],
    "graph": {
      "discovered_neighbors": [
        {
          "count": 2,
          "info": "Moscow is the capital and the largest city of Russia, with 12.2 million [...]",
          "name": "Moscow",
          "weight": 0.012578616352201259,
          "type": "WHERE",
          "id": 0
        },
        {
          "count": 15,
          "info": "Vladimir Vladimirovich Putin has been the President of Russia since [...]",
          "name": "Vladimir Putin",
          "weight": 0.09433962264150944,
          "type": "WHO",
          "id": 2
        },
        {
          "count": 1,
          "info": "The Moscow Kremlin, usually referred to as the Kremlin, is a fortified complex at the heart of [...]",
          "name": "Kremlin",
          "weight": 0.006289308176100629,
          "type": "WHERE",
          "id": 3
        },
        {
          "count": 1,
          "info": "Turkey is a parliamentary republic in Eurasia, largely located in [...]",
          "name": "Turkey",
          "weight": 0.006289308176100629,
          "type": "WHERE",
          "id": 4
        },
        {
          "count": 1,
          "info": "Ukraine is a sovereign country in Eastern Europe, bordered by Russia to the east and [...]",
          "name": "Ukraine",
          "weight": 0.006289308176100629,
          "type": "WHERE",
          "id": 5
        }
      ],
      "general_info": {
        "edge_type": "sentence",
        "number_of_nodes": 4458,
        "number_of_edges": 73867,
        "density": 0.007435287372392373
      }
    }
  },
  "text": "With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...].",
  "task_status": "SUCCESS"
}
```



>... and response body, case 2) STARTED (the task has started, but it is not over):

```json
{
  "task_type": "EntityDiscoveryAPI", 
  "task_id": "8292fd19-6c94-4570-90bf-c7d2f0afb9ed", 
  "task_status": "STARTED"
}
```

>... and response body, case 3) PENDING (the task is still pending):

```json
{
  "task_type": "EntityDiscoveryAPI", 
  "task_id": "8292fd19-6c94-4570-90bf-c7d2f0afb9ed", 
  "task_status": "PENDING"
}
```




**Find other relevant entities not in your text from a Text Collection**

Based on the submitted text, this API finds contextually relevant named entities originally not in your text, by mining them from a Text Collection.

<aside class="notice">
Depending on the size of the Text Collection, this service might take up to few seconds to provide a full answer. 
</aside>


### Discover related entities from a Collection - `POST fromURL` 

Given an URL, this API allows you to discover other contextually relevant named entities by retrieving them from a Text Collection.
As detailed in the right panel, as an immediate response to this API, you will get a `202` answer ("ACCEPTED") containing a task identifier `task_id` to be used later in the `GET` call. 

Parameter | Type | Description | Values |
--------- | ------- | ----------- | ------ |
collection_name | string, required | the name of the Text Collection  | - |
url | string, required |the url of the text | use [url-encoding](http://www.url-encode-decode.com/)|
limit | number, optional | the max # of relevant entities to be returned | If not specified, all results are returned |
access_token | string, required | your access token (40 digits) | - |



### Discover related entities in a Collection - `POST fromText` 

Given a text, this API allows you to discover other contextually relevant named entities by retrieving them from a Text Collection.
As detailed in the right panel, as an immediate response to this API, you will get a `202` answer ("ACCEPTED") containing a task identifier `task_id` to be used later in the `GET` call.

Parameter | Type | Description | Values |
--------- | ------- | ----------- | ------ |
collection_name | string, required | the name of the Text Collection | - |
text | string, required |the text document | pass the text between "" (e.g. "This is an example") or use [url-encoded](http://www.url-encode-decode.com/) text|
limit | number, optional | the max # of relevant entities to be returned | If not specified, all results are returned |
access_token | string, required | your access token (40 digits) | - |




### Get results from Entity Discovery - `GET` 

This API allows you to get results containing relevant named entities discovered in a Text Collection.


Parameter | Type | Description | 
--------- | ------- | ----------- | 
task_id | string, required | the identifier of the created Entity Discovery task| 
access_token | string, required | your access token (40 digits) | 

If results are ready (i.e. the graph-related entities have been computed) you will get a `200` answer ("SUCCESS") and the resulting ouput, as detailed in the right panel.
If the process is still ongoing you will get an adequate status code answer ("STARTED" or "PENDING") meaning that you have to try again a bit later with another `GET` call. 

<aside class="notice">
In case of SUCCESS, results are promptly deleted afterwards, i.e. performing another GET on the same task_id will return no results.
</aside>
<aside class="success">
Remember — insert your credentials for authentication!
</aside>
