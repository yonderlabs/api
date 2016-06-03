## Text Item



> Request example to "Create Text Item fromURL" - `POST fromURL`...

```shell
curl --ssl-reqd --request POST --data url=http%3A%2F%2Fwww.theatlantic.com%2Finternational%2Farchive%2F2015%2F11%2Frussia-doping-2016-olympics%2F416604%2F "https://vm3.yonderlabs.com/1.0/textcollection/textitem/fromURL?collection_name=donald_duck&access_token=YOUR_ACCESS_TOKEN"
```
>... and response body (200/JSON):

```json
{
  "url": "http://www.theatlantic.com/international/archive/2015/11/russia-doping-2016-olympics/416604/", 
  "collection_name": "donald_duck", 
  "text": "With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...].", 
  "timestamp": "2015-12-29 16:28:06.517297", 
  "inserted_id": "5665a1e8b1f5391201471f86"
}
```


> Request example to "Create Text Item fromText"  - `POST fromText`...

```shell
curl --ssl-reqd --request POST --data text="With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...]." "https://vm3.yonderlabs.com/1.0/textcollection/textitem/fromText?collection_name=donald_duck&access_token=YOUR_ACCESS_TOKEN"
```
>... and response body (200/JSON):

```json
{
  "url": null, 
  "collection_name": "donald_duck", 
  "text": "With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...].", 
  "timestamp": "2015-12-29 16:28:06.517297", 
  "inserted_id": "5665a1e8b1f5391201471f86"
}
```


> Request example to "Get info from Text Item"  - `GET`...

```shell
curl --ssl-reqd --request GET "https://vm3.yonderlabs.com/1.0/textcollection/textitem?collection_name=donald_duck&id=5665a1e8b1f5391201471f86&access_token=YOUR_ACCESS_TOKEN"
```
>... and response body (200/JSON):

```json
{
  "collection_name": "donald_duck", 
  "document": {
    "keywords": [
      {
        "score": 1.0, 
        "name": "program"
      }, 
      {
        "score": 1.0, 
        "name": "last week"
      }, 
      {
        "score": 1.0, 
        "name": "field"
      }
    ], 
    "entities": [
      {
        "info": {
          "wikipedia": "https://en.wikipedia.org/wiki/Russia", 
          "description": "Russia, also officially known as the Russian Federation, is a country in northern Eurasia. It is a federal semi-presidential republic [...]."
        }, 
        "score": 1.0, 
        "type": "Place", 
        "name": "Russia"
      }, 
      {
        "info": null, 
        "score": 1.0, 
        "type": "Organization", 
        "name": "WADA"
      }
    ], 
    "timestamp": "2015-12-29 16:28:06.517297", 
    "_id": "5665a1e8b1f5391201471f86"
  }, 
  "fetched_id": "5665a1e8b1f5391201471f86"
}
```




> Request example to "Modify Text Item fromURL"  - `PUT fromURL`...

```shell
curl --ssl-reqd --request PUT --data url=http%3A%2F%2Fwww.theguardian.com%2Fworld%2F2015%2Fnov%2F11%2Fgermany-spied-fbi-un-bodies-french-foreign-minister "https://vm3.yonderlabs.com/1.0/textcollection/textitem/fromText?collection_name=donald_duck&id=5665a1e8b1f5391201471f86&access_token=YOUR_ACCESS_TOKEN"
```
>... and response body (200/JSON):

```json
{
  "url": "http://www.theguardian.com/world/2015/nov/11/germany-spied-fbi-un-bodies-french-foreign-minister", 
  "collection_name": "donald_duck", 
  "modified_id": "5665a1e8b1f5391201471f86", 
  "timestamp": "2015-12-29 16:28:06.517297", 
  "text": "Germany's foreign intelligence service spied on targets including the French foreign minister, Laurent Fabius, the FBI and the UN Children's Fund, a media report said on Wednesday. The latest news report on the BND spy service fuels a debate in Germany about state surveillance kicked off by the revelations of the US whistleblower Edward Snowden [...]."
}
```


> Request example to "Modify Text Item fromText"  - `PUT fromText`...

```shell
curl --ssl-reqd --request PUT --data text="I want to change the text of the article about Russia and the 2016 Olympics in Rio de Janeiro." "https://vm3.yonderlabs.com/1.0/textcollection/textitem/fromText?collection_name=donald_duck&id=5665a1e8b1f5391201471f86&access_token=YOUR_ACCESS_TOKEN"
```
>... and response body (200/JSON):

```json
{
  "url": null, 
  "collection_name": "donald_duck", 
  "modified_id": "5665a1e8b1f5391201471f86",
  "timestamp": "2015-12-29 16:28:06.517297",  
  "text": "I want to change the text of the article about Russia and the 2016 Olympics in Rio de Janeiro."
}
```

> Request example to "Delete Text Item" - `DELETE`...

```shell
curl --ssl-reqd --request DELETE "https://vm3.yonderlabs.com/1.0/textcollection/textitem?collection_name=donald_duck&id=5665a1e8b1f5391201471f86&access_token=YOUR_ACCESS_TOKEN"
```
>... and response body (200/JSON):

```json
{
  "collection_name": "donald_duck", 
  "deleted_id": "5665a1e8b1f5391201471f86" 
 }
```






**Create, modify, delete, and retrieve info from Text Items in your Text Collections**

This API allows you to manage Text Items in your Text Collections. 


### Create Text Item - `POST fromURL` 

This API allows you to create a new Text Item from the text contained in a URL:

Parameter | Type | Description | Values |
--------- | ------- | ----------- | ------ |
collection_name | string, required | the name of the Text Collection where to insert the new Item | - |
url | string, required |the url of the text to be inserted as a new Item of the Text Collection | use [url-encoding](http://www.url-encode-decode.com/)|
access_token | string, required | your access token (40 digits) | - |


### Create Text Item - `POST fromText` 

This API allows you to create a new Text Item inserting simple text:


Parameter | Type | Description | Values |
--------- | ------- | ----------- | ------ |
collection_name | string, required | the name of the Text Collection where to insert the new Item | - |
text | string, required |the text to be inserted as a new Text Item | pass the text between "" (e.g. "This is an example") or use [url-encoded](http://www.url-encode-decode.com/) text|
access_token | string, required | your access token (40 digits) | - |


### Get info from Text Item - `GET`

This API allows you to retrieve all information from a Text Item:


Parameter | Type | Description | 
--------- | ------- | ----------- | 
collection_name | string, required | the name of the Text Collection which contains the Text Item| 
id | string, required |the ID of the text item|
access_token | string, required | your access token (40 digits) | 


### Change Text Item fromURL - `PUT fromURL`

This API allows you to change the text contained in a Text Item of a Text Collection:

Parameter | Type | Description |  Values |
--------- | ------- | ----------- | ------ |
collection_name | string, required | the name of the Text Collection where to change the item| - |
id | string, required |the ID of the text item| - |
url | string, required |the url of the text to be inserted | use [url-encoding](http://www.url-encode-decode.com/)|
access_token | string, required | your access token (40 digits) | - |



### Change Text Item fromText - `PUT fromText`

This API allows you to change the text contained in a Text Item of a Text Collection:


Parameter | Type | Description | Values |
--------- | ------- | ----------- | ------ |
collection_name | string, required | the name of the Text Collection where to change the item| - |
id | string, required |the ID of the text item| - |
text | string, required |the new text | pass the text between "" (e.g. "This is an example") or use [url-encoded](http://www.url-encode-decode.com/) text|
access_token | string, required | your access token (40 digits) | - |

### Delete a Text Item - `DELETE`

This API allows you to delete a Text Item from a Text Collection:


Parameter | Type | Description 
--------- | ------- | ----------- | 
collection_name | string, required | the name of the Text Collection where to delete the Item| 
id | string, required |the ID of the Text Item to be deleted|
access_token | string, required | your access token (40 digits) | 



<aside class="success">
Remember — insert your credentials for authentication!
</aside>


