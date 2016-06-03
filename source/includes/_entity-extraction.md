## Entity Extraction


> Request example - `POST fromURL`...

```shell
curl --ssl-reqd --request POST --data url=http%3A%2F%2Fwww.theatlantic.com%2Finternational%2Farchive%2F2015%2F11%2Frussia-doping-2016-olympics%2F416604%2F "https://vm3.yonderlabs.com/1.0/text/entityextraction/fromURL?limit=10&access_token=YOUR_ACCESS_TOKEN"
```

> ... and response body (200/JSON):

```json
{
  "url": "http://www.theatlantic.com/international/archive/2015/11/russia-doping-2016-olympics/416604/", 
  "text": "With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the World Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...].", 
  "limit": 10, 
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
    }, 
    {
      "info": null, 
      "score": 1.0, 
      "type": "Misc", 
      "name": "Russian"
    }, 
    {
      "info": null, 
      "score": 0.9, 
      "type": "Organization", 
      "name": "Olympics"
    }, 
    {
      "info": {
        "wikipedia": "https://en.wikipedia.org/wiki/Vitaly_Mutko", 
        "description": "Vitaly Leontiyevich Mutko is a Russian politician. Since May 2008, he has been Minister of Sport, Tourism and Youth policy [...]."
      }, 
      "score": 0.8, 
      "type": "Person", 
      "name": "Vitaly Mutko"
    }, 
    {
      "info": {
        "wikipedia": "https://en.wikipedia.org/wiki/Rio_de_Janeiro", 
        "description": "Rio de Janeiro is the second-largest city in Brazil, the sixth-largest city in the Americas, and the world's thirty-ninth largest city by population [...]."
      }, 
      "score": 0.4, 
      "type": "Place", 
      "name": "Rio de Janeiro"
    }, 
    {
      "info": {
        "wikipedia": "https://en.wikipedia.org/wiki/Colorado", 
        "description": "Colorado is a U.S. state encompassing most of the Southern Rocky Mountains as well as the northeastern portion of the Colorado Plateau and the western edge of the Great Plains [...]."
      }, 
      "score": 0.4, 
      "type": "Place", 
      "name": "Colorado"
    }, 
    {
      "info": null, 
      "score": 0.4, 
      "type": "Organization", 
      "name": "World Anti-Doping Agency"
    }, 
    {
      "info": null, 
      "score": 0.4, 
      "type": "Organization", 
      "name": "International Olympic Committee"
    }, 
    {
       "info": {
        "wikipedia": "https://en.wikipedia.org/wiki/Switzerland", 
        "description": "Switzerland is a country in Europe. While still named the Swiss Confederation for historical reasons, modern Switzerland is a federal directorial republic [...]."
    },  
      "score": 0.4, 
      "type": "Place", 
      "name": "Switzerland"
    }
  ]
}
```


> Request example - `POST fromText`...



```shell
curl --ssl-reqd --request POST --data text="With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...]." "https://vm3.yonderlabs.com/1.0/text/entityextraction/fromText?limit=10&access_token=YOUR_ACCESS_TOKEN"
```

> ... and response body (200/JSON):

```json
{
  "url": null, 
  "text": "With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...].", 
  "limit": 10, 
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
    }, 
    {
      "info": null, 
      "score": 1.0, 
      "type": "Misc", 
      "name": "Russian"
    }, 
    {
      "info": null, 
      "score": 0.9, 
      "type": "Organization", 
      "name": "Olympics"
    }, 
    {
      "info": {
        "wikipedia": "https://en.wikipedia.org/wiki/Vitaly_Mutko", 
        "description": "Vitaly Leontiyevich Mutko is a Russian politician. Since May 2008, he has been Minister of Sport, Tourism and Youth policy [...]."
      }, 
      "score": 0.8, 
      "type": "Person", 
      "name": "Vitaly Mutko"
    }, 
    {
      "info": {
        "wikipedia": "https://en.wikipedia.org/wiki/Rio_de_Janeiro", 
        "description": "Rio de Janeiro is the second-largest city in Brazil, the sixth-largest city in the Americas, and the world's thirty-ninth largest city by population [...]."
      }, 
      "score": 0.4, 
      "type": "Place", 
      "name": "Rio de Janeiro"
    }, 
    {
      "info": {
        "wikipedia": "https://en.wikipedia.org/wiki/Colorado", 
        "description": "Colorado is a U.S. state encompassing most of the Southern Rocky Mountains as well as the northeastern portion of the Colorado Plateau and the western edge of the Great Plains [...]."
      }, 
      "score": 0.4, 
      "type": "Place", 
      "name": "Colorado"
    }, 
    {
      "info": null, 
      "score": 0.4, 
      "type": "Organization", 
      "name": "World Anti-Doping Agency"
    }, 
    {
      "info": null, 
      "score": 0.4, 
      "type": "Organization", 
      "name": "International Olympic Committee"
    }, 
    {
      "info": {
        "wikipedia": "https://en.wikipedia.org/wiki/Switzerland", 
        "description": "Switzerland is a country in Europe. While still named the Swiss Confederation for historical reasons, modern Switzerland is a federal directorial republic [...]."
    }, 
      "score": 0.4, 
      "type": "Place", 
      "name": "Switzerland"
    }
  ]
}
```






**Identify people, places, and organizations in your text**

This API detects named entities and classify them as `Person`, `Place`, `Organization` or `Misc`. The service also links them to knowledge base repositories (Wikipedia, DBpedia, etc.).
Allowed input sources are: text content contained in an URL ("from URL") or just simple text ("from text").


### Entity Extraction - `POST fromURL` 


Attribute | Type | Description | Values |
--------- | ------- | ----------- | ------ |
url | string, required | the URL of the text document | use [url-encoding](http://www.url-encode-decode.com/)|


Parameter | Type | Description |
--------- | ------- | ----------- | 
limit | number, optional | max # of relevant entities to be returned, in decreasing order of confidence (if not specified, all results are returned)
access_token | string, required | your access token (40 digits) | 

Examples of how-to-call the API and the related output are provided in the right panel.

### Entity Extraction - `POST fromText` 

Attribute | Type | Description | Values |
--------- | ------- | ----------- | ------ |
text | string, required | the text to be classified | pass the text between "" (e.g. "This is an example") or use [url-encoded](http://www.url-encode-decode.com/) text|



Parameter | Type | Description | 
--------- | ------- | ----------- | 
limit | number, optional | max # of relevant entities to be returned, in decreasing order of confidence (if not specified, all results are returned)
access_token | string, required | your access token (40 digits) | 

Examples of how-to-call the API and the related output are provided in the right panel.

<aside class="success">
Remember — insert your credentials for authentication!
</aside>
