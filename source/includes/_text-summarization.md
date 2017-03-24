## Text Summarization 


> Request example - `POST fromURL`...



```shell
curl --ssl-reqd --request POST --data url=https%3A%2F%2Fwww.theguardian.com%2Fworld%2F2016%2Fjul%2F22%2Fmissing-flight-mh370-hunt-for-debris-will-not-be-extended "https://api.yonderlabs.com/1.0/text/textsummarization/fromURL?access_token=YOUR_ACCESS_TOKEN"

```

> ... and response body (200/JSON):

```json
{"message": "The Summarization API will be ready by 29-03-2017."}
```

> Request example - `POST fromText`...


```shell
curl --ssl-reqd --request POST --data text="The hunt for Malaysia Airlines flight MH370 is to be suspended if evidence of the missing jet is not found in the current search area. The transport ministers of Australia, Malaysia and China, representing the country leading the search, the airline and the home of the majority of its passengers, met to discuss the future of the search in the Malaysian federal administrative centre of Putrajaya on Friday. They announced that [...]" "https://api.yonderlabs.com/1.0/text/textsummarization/fromText?access_token=YOUR_ACCESS_TOKEN"
```


> ... and response body (200/JSON):

```json
{"message": "The Summarization API will be ready by 29-03-2017."}
```




**Produce a meaningful summary from your documents**

This API analyzes your text content and produces a short summary containing meaningful facts, events and relations.
If provided with more text inputs, the service distills content from multiple documents into a single summary.
Allowed input sources are: text content contained in an URL ("from URL") or just simple text ("from text").


### Text Summarization  - `POST fromURL`
 
The Text Summarization API will be ready by 29-03-2017. 
 

### Text Summarization - `POST fromText`


The Text Summarization API will be ready by 29-03-2017. 


<aside class="success">
Remember — insert your credentials for authentication!
</aside>

