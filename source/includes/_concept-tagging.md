## Concept Tagging

> Request example - `POST fromURL`...



```shell
curl --ssl-reqd --request POST -u YOUR_USERNAME:YOUR_PASSWORD --data url=http%3A%2F%2Fwww.theatlantic.com%2Finternational%2Farchive%2F2015%2F11%2Frussia-doping-2016-olympics%2F416604%2F "https://vm3.yonderlabs.com/1.0/text/concepttagging/fromURL?limit=8"
```


> ... and response body (200/JSON):

```json
{
  "url": "http://www.theatlantic.com/international/archive/2015/11/russia-doping-2016-olympics/416604/", 
  "text": "With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the World Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...].", 
  "limit": 8, 
  "tags": [
    "sports", 
    "wada", 
    "russian", 
    "olympics", 
    "vitaly mutko", 
    "world anti doping agency", 
    "russia", 
    "program"
  ]
}
```

> Request example  - `POST fromText`...


```shell
curl --ssl-reqd --request POST -u YOUR_USERNAME:YOUR_PASSWORD --data text="With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...]." "https://vm3.yonderlabs.com/1.0/text/concepttagging/fromText?limit=8"
```

> ... and response body (200/JSON):

```json
{
  "url": null, 
  "text": "With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...].", 
 "limit": 8, 
  "tags": [
    "sports", 
    "wada", 
    "russian", 
    "olympics", 
    "vitaly mutko", 
    "world anti doping agency", 
    "russia", 
    "program"
  ]
}
```








**Generate high-level semantic tags for your text document**

Concept tags are a limited and meaningful set of highly relevant named entities and important keywords related to facts, events, and relations found in your text.
Allowed input sources are: text content contained in an URL ("from URL") or just simple text ("from text").


### Concept Tagging - `POST fromURL`



Attribute | Type | Description | Values |
--------- | ------- | ----------- | ------ |
url | string, required | the URL of the text document | use [url-encoding](http://www.url-encode-decode.com/)|


Parameter | Type | Description | Value |
--------- | ------- | ----------- | ----- |
limit | number, optional | max # of relevant tags to be returned, in decreasing order of relevance | 1, 2, ..., 10 (default), etc. |
 

Examples of how-to-call the API and the related output are provided in the right panel.

### Concept Tagging - `POST fromText`


Attribute | Type | Description | Values |
--------- | ------- | ----------- | ------ |
text | string, required | the text to be classified | pass the text between "" (e.g. "This is an example") or use [url-encoded](http://www.url-encode-decode.com/) text|


Parameter | Type | Description | Value |
--------- | ------- | ----------- | ----- |
limit | number, optional | max # of relevant tags to be returned, in decreasing order of relevance | 1, 2, ..., 10 (default), etc. |

Examples of how-to-call the API and the related output are provided in the right panel.


<aside class="success">
Remember — insert your credentials for authentication!
</aside>





