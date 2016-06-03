## Entity Graph 

> Request example to "Create an Entity Graph" - `POST`...


```shell
curl --ssl-reqd --request POST "https://vm3.yonderlabs.com/1.0/textcollection/entitygraph?collection_name=scrooge&limit=5&access_token=YOUR_ACCESS_TOKEN"
```


>... and response body (202 "ACCEPTED"):

```json
{
  "task_type": "EntityGraphAPI", 
  "collection-name": "scrooge", 
  "task_id": "a4e31278-4432-43da-8fbf-1b21562d02f9", 
  "task_status": "PENDING"
}
```

> Request example to "Get results from Entity Graph" - `GET`...


```shell
curl --ssl-reqd --request GET "https://vm3.yonderlabs.com/1.0/textcollection/entitygraph?task_id=a4e31278-4432-43da-8fbf-1b21562d02f9&access_token=YOUR_ACCESS_TOKEN"
```


>... and response body, case 1) SUCCESS, i.e. the task is over:

```json
{
  "task_error": null,
  "task_type": "EntityGraphAPI",
  "task_id": "a4e31278-4432-43da-8fbf-1b21562d02f9",
  "collection_name": "scrooge",
  "task_result": {
    "timestamp": "2016-05-06 09:31:44.987771",
    "nodes": [
      {
        "count": 2,
        "info": "Russia also officially known as the Russian Federation is a sovereign state in northern Eurasia [...]",
        "name": "Russia",
        "neighbors": [
          {
            "edge_weight": 0.02197802197802198,
            "id": 1,
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
        "weight": 0.012578616352201259,
        "type": "Place",
        "id": 0
      },
      {
        "count": 2,
        "info": "Ukraine is a sovereign country in Eastern Europe, bordered by Russia to the east and [...]",
        "name": "Ukraine",
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
        "weight": 0.012578616352201259,
        "type": "Place",
        "id": 1
      }
    ],
      "general_info": {
      "edge_type": "sentence",
      "number_of_nodes": 4458,
      "number_of_edges": 73867,
      "density": 0.007435287372392373
    },
    "limit": 5
  },
  "task_status": "SUCCESS"
}      
```




>... and response body, case 2) STARTED (the task has started, but it is not over):

```json
{
  "task_type": "EntityGraphAPI", 
  "task_id": "a4e31278-4432-43da-8fbf-1b21562d02f9", 
  "task_status": "STARTED"
}
```

>... and response body, case 3) PENDING (the task is still pending):

```json
{
  "task_type": "EntityGraphAPI", 
  "task_id": "a4e31278-4432-43da-8fbf-1b21562d02f9", 
  "task_status": "PENDING"
}
```


**Identify a graph of entities from your Text Collection**

This API analyzes a collection of texts and extracts a graph with most related named entities, highlighting hidden interactions between people, places and organizations.



<aside class="notice">
Depending on the size of the Text Collection, this service might take up to few seconds to provide a full answer.  
</aside>

### Create an Entity Graph - `POST`

This API allows you to launch the task which computes a co-occurrence graph on all named entities contained in a Text Collection.
Co-occurrency is here evaluated at 'sentence' level.
As detailed in the right panel, as an immediate response to this API, you will get a `202` answer ("ACCEPTED") containing a task identifier `task_id` to be used later in the `GET` call. 


Parameter | Type | Description | 
--------- | ------- | ----------- | 
collection_name | string, required | the name of the Text Collection from which to build an Entity Graph | 
limit	| number, optional	| max # of relevant entities to be returned, in decreasing order of edge weight (if not specified, all results are returned)
access_token | string, required | your access token (40 digits) |



### Get results from Entity Graph - `GET`

This API allows you to retrieve the computed co-occurrence graph on all named entities contained in a Text Collection, where co-occurrency is evaluated at 'sentence' level.

Parameter | Type | Description | 
--------- | ------- | ----------- | 
task_id | string, required | the identifier of the created Entity Graph task| 
access_token | string, required | your access token (40 digits) |

If results are ready (i.e. the entity graph has been computed) you will get a `200` answer ("SUCCESS") and the resulting ouput, as detailed in the right panel.
If the process is still ongoing you will get an adequate status code answer ("STARTED" or "PENDING") meaning that you have to try again a bit later with another `GET` call. 

<aside class="notice">
In case of SUCCESS, results are promptly deleted afterwards, i.e. performing another GET on the same task_id will return no results.
</aside>

<aside class="success">
Remember — insert your credentials for authentication!
</aside>