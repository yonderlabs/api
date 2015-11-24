## Text Item
> This is the code to "Insert item from text"...

```python

from urllib2 import Request, urlopen

request = Request('https://api.yonderlabs.com/1.0/text/taxonomyclassification/fromURL?url=url&taxonomy=taxonomy&levels=2&limit=3')

response_body = urlopen(request).read()
print response_body
```
```shell
curl --include \
     --request POST \
'https://api.yonderlabs.com/1.0/text/taxonomyclassification/fromURL?url=url&taxonomy=taxonomy&levels=2&limit=3'
```



>... which returns a json structured like this (response 201):

```json
{
    "text": "A wonderful tennis match took place yesterday at Wimbledon between Djokovic and Federer"
    "taxonomy": "iab"
    "levels": 2
    "limit": 3
    "topic":
        [
            {
                "level": 0
                "category": "sports"
                "score": 0.8
                "sublevels":
                    [
                        {
                            "level": 1
                            "category": "tennis"
                            "score": 1.0
                        }
                    ]
            },
            {
                "level": 0
                "category": "arts&entertainment"
                "score": 0.2
                "sublevels":
                    [
                        {
                            "level": 1
                            "category": "television"
                            "score": 0.9
                        },
                        {
                            "level": 1
                            "category": "celebrity fun/gossip"
                            "score": 0.1
                        }
                    ]
            },
        ]
}
```



> This is the code to "Insert item from URL"...

```python

from urllib2 import Request, urlopen

request = Request('https://api.yonderlabs.com/1.0/text/taxonomyclassification/fromText?text=text&taxonomy=taxonomy&levels=2&limit=3')

response_body = urlopen(request).read()
print response_body
```


```shell
curl --include \
     --request POST \
'https://api.yonderlabs.com/1.0/text/taxonomyclassification/fromText?text=text&taxonomy=taxonomy&levels=2&limit=3'
```

>... which returns a json structured like this (response 200):

```json
{
  "levels": 2,
  "limit": 1,
  "taxonomy": "iab-it",
  "text": "Contemporaneamente a Juncker, anche la Cancelliera Merkel parla di emergenza immigrazione, in un discorso al Bundestag. E lo fa, al solito, con i suoi toni pragmatici: « Coloro che cercano asilo e che vedono riconosciuto il diritto d’asilo hanno bisogno del nostro aiuto. E bisogna integrarli velocemente. E altrettanto velocemente devono imparare velocemente il tedesco e avere velocemente un lavoro. Diventeranno cittadini tedeschi», ha aggiunto. «Un Paese che dice “benvenuti” a tante persone deve anche dire quali sono le regole - ha aggiunto -. Anche questo fa parte di una società aperta. Non ci sarà nessuna tolleranza per la società parallela». Temi e concetti che si ritrovano anche nel discorso di Juncker.",
  "topics": [
    {
      "category": "leggi_governo_e_politica",
      "level": 0,
      "score": 0.7233245447210793,
      "sublevels": [
        {
          "category": "politica",
          "level": 1,
          "score": 0.5251832068430112
        }
      ]
    }
  ]
}
```

> This is the code to "Change item text"...

```python

from urllib2 import Request, urlopen

request = Request('https://api.yonderlabs.com/1.0/text/taxonomyclassification/fromText?text=text&taxonomy=taxonomy&levels=2&limit=3')

response_body = urlopen(request).read()
print response_body
```


```shell
curl --include \
     --request POST \
'https://api.yonderlabs.com/1.0/text/taxonomyclassification/fromText?text=text&taxonomy=taxonomy&levels=2&limit=3'
```

>... which returns a json structured like this (response 200):

```json
{
  "levels": 2,
  "limit": 1,
  "taxonomy": "iab-it",
  "text": "Contemporaneamente a Juncker, anche la Cancelliera Merkel parla di emergenza immigrazione, in un discorso al Bundestag. E lo fa, al solito, con i suoi toni pragmatici: « Coloro che cercano asilo e che vedono riconosciuto il diritto d’asilo hanno bisogno del nostro aiuto. E bisogna integrarli velocemente. E altrettanto velocemente devono imparare velocemente il tedesco e avere velocemente un lavoro. Diventeranno cittadini tedeschi», ha aggiunto. «Un Paese che dice “benvenuti” a tante persone deve anche dire quali sono le regole - ha aggiunto -. Anche questo fa parte di una società aperta. Non ci sarà nessuna tolleranza per la società parallela». Temi e concetti che si ritrovano anche nel discorso di Juncker.",
  "topics": [
    {
      "category": "leggi_governo_e_politica",
      "level": 0,
      "score": 0.7233245447210793,
      "sublevels": [
        {
          "category": "politica",
          "level": 1,
          "score": 0.5251832068430112
        }
      ]
    }
  ]
}
```



> This is the code to "Delete item"...

```python

from urllib2 import Request, urlopen

request = Request('https://api.yonderlabs.com/1.0/text/taxonomyclassification/fromText?text=text&taxonomy=taxonomy&levels=2&limit=3')

response_body = urlopen(request).read()
print response_body
```


```shell
curl --include \
     --request POST \
'https://api.yonderlabs.com/1.0/text/taxonomyclassification/fromText?text=text&taxonomy=taxonomy&levels=2&limit=3'
```

>... which returns No Content (response 204)





**Create, modify, and delete items in your Text Collections**

This API allows you to manage text items in your collections. 


### Insert item from text 

This API allows you to create a new item just inserting simple text:

`POST https://api.yonderlabs.com/1.0/textcollections/collection/item/fromText -d "text=text"`

Parameter | Type | Description | 
--------- | ------- | ----------- | 
collection | string, required | the name of the Text Collection where to insert the new Item | 
text | string, required |the text to be inserted as a new item of the Text Collection |


### Insert item from URL 

This API allows you to create a new item from the text contained in a URL:

`POST https://api.yonderlabs.com/1.0/textcollections/collection/item/fromURL -d "url=url"`

Parameter | Type | Description | 
--------- | ------- | ----------- | 
collection | string, required | the name of the Text Collection where to insert the new item | 
url | string, required |the url of the text to be inserted as a new item of the Text Collection |



### Change item text

This API allows you to change the text contained in an item of a Text Collection:

`PUT https://api.yonderlabs.com/1.0/textcollections/collection/item/fromText -d "text=text"?id=id`

Parameter | Type | Description 
--------- | ------- | ----------- | 
collection | string, required | the name of the Text Collection where to change the item| 
id | number, required |the ID of the text item|
text | string, required |the new text |




### Delete a Text Item

This API allows you to delete an Item from a Text Collection:


`DELETE https://api.yonderlabs.com/1.0/textcollections/collection/item/?id=id`

Parameter | Type | Description 
--------- | ------- | ----------- | 
collection | string, required | the name of the Text Collection where to delete the Item| 
id | number, required |the ID of the text Item to be deleted|




<aside class="success">
Remember — insert your credentials for authentication!
</aside>



