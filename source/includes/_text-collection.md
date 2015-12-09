## Text Collection
> Request example to "Create a Text Collection" - `POST`...

```shell
curl --ssl-reqd --request POST -u YOUR_USERNAME:YOUR_PASSWORD "https://vm3.yonderlabs.com/1.0/textcollection/textcollection?collection_name=donald-duck&description=this-is-my-first-collection"
```

>... and response body (200/JSON):

```json
{
  "type": "private", 
  "description": "this-is-my-first-collection", 
  "collection_name": "donald-duck", 
  "created": true
}
```



> Request example to "Get info from a Text Collection" - `GET`...


```shell
curl --ssl-reqd --request GET -u YOUR_USERNAME:YOUR_PASSWORD "https://vm3.yonderlabs.com/1.0/textcollection/textcollection?collection_name=donald-duck"
```

>... and response body (200/JSON):

```json
{
  "count": 0, 
  "type": "private", 
  "description": "this-is-my-first-collection", 
  "collection_name": "donald-duck"
}
```



> Request example to "Delete a Text Collection" - `DELETE`...


```shell
curl --ssl-reqd --request DELETE -u YOUR_USERNAME:YOUR_PASSWORD "https://vm3.yonderlabs.com/1.0/textcollection/textcollection?collection_name=donald-duck"
```

>... and response body (200/JSON):

```json
{
  "deleted": true, 
  "type": "private", 
  "description": "this-is-my-first-collection", 
  "collection_name": "donald-duck"
}
```




**Create, delete, and retrieve information from Text Collections**

This API allows you to create, delete, and get information from a Text Collection.


### Create a Text Collection - `POST`

This API allows you to create a new Text Collection:


Parameter | Type | Description | 
--------- | ------- | ----------- | 
collection_name | string, required | the name of the Text Collection to be created | 
description | string, optional | a textual description of the Text Collection | 




### Get info from a Text Collection - `GET`

This API allows you to retrieve all information from a Text Collection:


Parameter | Type | Description | 
--------- | ------- | ----------- | 
collection_name | string, required | the name of the Text Collection from which to retrieve information| 


### Delete a Text Collection - `DELETE`

This API allows you to delete a Text Collection:



Parameter | Type | Description | 
--------- | ------- | ----------- | 
collection_name | string, required | the name of the Text Collection to be deleted| 



<aside class="success">
Remember — insert your credentials for authentication!
</aside>



