## Taxonomy Classification 

> Request example "fromURL"...


```shell
curl --ssl-reqd --request POST -u YOUR_USERNAME:YOUR_PASSWORD --data url=http%3A%2F%2Fwww.theatlantic.com%2Finternational%2Farchive%2F2015%2F11%2Frussia-doping-2016-olympics%2F416604%2F "https://vm3.yonderlabs.com/1.0/text/taxonomyclassification/fromURL?limit=2&taxonomy=news-en"
```

> ... and response body (200/JSON):


```json
{
  "url": "http://www.theatlantic.com/international/archive/2015/11/russia-doping-2016-olympics/416604/", 
  "text": "With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...].", 
  "topics": [
    {
      "category": "sports", 
      "score": 0.5645578680456448, 
      "level": 0
    }, 
    {
      "category": "domestic politics", 
      "score": 0.35036578139913005, 
      "level": 0
    }
  ], 
  "levels": 2, 
  "limit": 2, 
  "taxonomy": "news-en"
}
```


> Request example "fromText"...


```shell
curl --ssl-reqd --request POST -u YOUR_USERNAME:YOUR_PASSWORD --data text="With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...]." "https://vm3.yonderlabs.com/1.0/text/taxonomyclassification/fromText?limit=2&taxonomy=news-en"
```

> ... and response body (200/JSON):


```json
{
  "url": null, 
  "text": "With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...].", 
  "topics": [
    {
      "category": "sports", 
      "score": 0.5645578680456448, 
      "level": 0
    }, 
    {
      "category": "domestic politics", 
      "score": 0.35036578139913005, 
      "level": 0
    }
  ], 
  "levels": 2, 
  "limit": 2, 
  "taxonomy": "news-en"
}
```





**Categorize your text into a hierarchical taxonomy**

This service analyzes chunks of text (from single sentences to full documents) and classifies them into customizable hierarchical taxonomies (e.g. Reuters taxonomy for news, etc.). 
Allowed input sources are: text content contained in an URL ("from URL") or just simple text ("from text").


### From URL: HTTPS request 


Attribute | Type | Description | Values |
--------- | ------- | ----------- | ------ |
url | string, required | the URL of the text document | use [url-encoding](http://www.url-encode-decode.com/)|


Parameter | Type | Description | Values |
--------- | ------- | ----------- | ------ |
taxonomy | string, required |which taxonomy to use | "news-en", "news-it", "iab-it" |
levels | number, optional | # of hierarchical levels considered for classification | 1, 2 (default)|
limit | number, optional | max # of relevant categories returned per each level of the taxonomy | 1, 2, 3 (default) |


where:

+ "news-en" is the [Reuters taxonomy](http://www.ai.mit.edu/projects/jmlr/papers/volume5/lewis04a/a16-rbb-topic/topics.rbb) for news in English language;

+ "news-it" is one news taxonomy specific for Italian language;

+ "iab-it" is the [IAB (QAG) taxonomy](http://www.iab.com/guidelines/iab-quality-assurance-guidelines-qag-taxonomy/) in Italian language.

Examples of how-to-call the API and the related output are provided in the right panel.

### From text: HTTPS request


Attribute | Type | Description | Values |
--------- | ------- | ----------- | ------ |
text | string, required | the text to be classified | pass the text between "" (e.g. "This is an example") or use [url-encoded](http://www.url-encode-decode.com/) text|


Parameter | Type | Description | Values |
--------- | ------- | ----------- | ------ |
taxonomy | string, required |which taxonomy to use | "news-en", "news-it", "iab-it" |
levels | number, optional | # of hierarchical levels considered for classification | 1, 2 (default)|
limit | number, optional | max # of relevant categories returned per each level of the taxonomy | 1, 2, 3 (default) |


where:

+ "news-en" is the [Reuters taxonomy](http://www.ai.mit.edu/projects/jmlr/papers/volume5/lewis04a/a16-rbb-topic/topics.rbb) for news in English language;

+ "news-it" is one news taxonomy specific for Italian language;


+ "iab-it" is the [IAB (QAG) taxonomy](http://www.iab.com/guidelines/iab-quality-assurance-guidelines-qag-taxonomy/) in Italian language.


Examples of how-to-call the API and the related output are provided in the right panel.

<aside class="success">
Remember — insert your credentials for authentication! 
</aside>



