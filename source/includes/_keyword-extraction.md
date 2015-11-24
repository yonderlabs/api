## Keyword Extraction 


> Request example "fromURL"...



```shell
curl --ssl-reqd --request POST -u YOUR_USERNAME:YOUR_PASSWORD --data url=http%3A%2F%2Fwww.theatlantic.com%2Finternational%2Farchive%2F2015%2F11%2Frussia-doping-2016-olympics%2F416604%2F "https://vm3.yonderlabs.com/1.0/text/keywordextraction/fromURL?limit=12"
```

> ... and response body (200/JSON):

```json
{
  "url": "http://www.theatlantic.com/international/archive/2015/11/russia-doping-2016-olympics/416604/", 
  "text": "With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the World Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...].", 
  "limit": 12, 
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
    }, 
    {
      "score": 0.8, 
      "name": "months"
    }, 
    {
      "score": 0.8, 
      "name": "report"
    }, 
    {
      "score": 0.8, 
      "name": "team"
    }, 
    {
      "score": 0.8, 
      "name": "athletes"
    }, 
    {
      "score": 0.8, 
      "name": "country"
    }, 
    {
      "score": 0.8, 
      "name": "issues"
    }, 
    {
      "score": 0.2, 
      "name": "world"
    }, 
    {
      "score": 0.2, 
      "name": "record"
    }, 
    {
      "score": 0.2, 
      "name": "90-day sprint"
    }
  ]
}
```

> Request example "fromText"...


```shell
curl --ssl-reqd --request POST -u YOUR_USERNAME:YOUR_PASSWORD --data text="With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...]." "https://vm3.yonderlabs.com/1.0/text/keywordextraction/fromText?limit=12"
```

> ... and response body (200/JSON):

```json
{
  "url": null, 
  "text": "With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the world Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics [...].", 
"limit": 12, 
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
    }, 
    {
      "score": 0.8, 
      "name": "months"
    }, 
    {
      "score": 0.8, 
      "name": "report"
    }, 
    {
      "score": 0.8, 
      "name": "team"
    }, 
    {
      "score": 0.8, 
      "name": "athletes"
    }, 
    {
      "score": 0.8, 
      "name": "country"
    }, 
    {
      "score": 0.8, 
      "name": "issues"
    }, 
    {
      "score": 0.2, 
      "name": "world"
    }, 
    {
      "score": 0.2, 
      "name": "record"
    }, 
    {
      "score": 0.2, 
      "name": "90-day sprint"
    }
  ]
}
```





**Find meaningful keywords in your text document**

This API analyzes your text content (news articles, blog posts, e-mail, etc.) identifying all meaningful keywords related to important facts, events and relations.
Allowed input sources are: text content contained in an URL ("from URL") or just simple text ("from text").


### From URL: HTTPS request 

Attribute | Type | Description | Values |
--------- | ------- | ----------- | ------ |
url | string, required | the URL of the text document | use [url-encoding](http://www.url-encode-decode.com/)|


Parameter | Type | Description |
--------- | ------- | ----------- | 
limit | number, optional | max # of relevant keywords to be returned, in decreasing order of relevance (if not specified, all results are returned)

Examples of how-to-call the API and the related output are provided in the right panel.

### From text: HTTPS request


Attribute | Type | Description | Values |
--------- | ------- | ----------- | ------ |
text | string, required | the text to be classified | pass the text between "" (e.g. "This is an example") or use [url-encoded](http://www.url-encode-decode.com/) text|



Parameter | Type | Description | 
--------- | ------- | ----------- | 
limit | number, optional | max # of relevant keywords to be returned, in decreasing order of relevance (if not specified, all results are returned)

Examples of how-to-call the API and the related output are provided in the right panel.

<aside class="success">
Remember — insert your credentials for authentication!
</aside>

