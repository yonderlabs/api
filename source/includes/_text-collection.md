## Text Collection
> This is the code to "Create a Text Collection"...

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



> This is the code to "List Text Collections"...

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

> This is the code to "Retrieve text IDs from a Text Collection"...

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



> This is the code to "Delete a Text Collections"...

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



> This is the code to "Delete all Text Collections"...

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



**Create, retrieve, and remove Text Collections**

This API allows you to create/remove a Text Collection, list existing Text Collections, and retrieve text IDs from a Text Collection.


### Create a Text Collection 

This API allows you to create a new Text Collection:

`POST https://api.yonderlabs.com/1.0/textcollections/collection/?description=description`

Parameter | Type | Description | 
--------- | ------- | ----------- | 
collection | string, required | the name of the Text Collection to be created | 
description | string, optional | a textual description of the Text Collection | 



### List Text Collections 

This API allows you to list the names of all your Text Collections, their size, and descriptions:

`GET https://api.yonderlabs.com/1.0/textcollections/`


### Retrieve text IDs from a Text Collection

This API allows you to retrieve all the IDs of the documents contained in a Text Collection:

`GET https://api.yonderlabs.com/1.0/textcollections/collection`

Parameter | Type | Description | 
--------- | ------- | ----------- | 
collection | string, required | the name of the Text Collection from which to retrieve text IDs| 


### Delete a Text Collection

This API allows you to delete a Text Collection:


`DELETE https://api.yonderlabs.com/1.0/textcollections/collection`

Parameter | Type | Description | 
--------- | ------- | ----------- | 
collection | string, required | the name of the Text Collection to be deleted| 


### Delete all Text Collections

This API allows you to delete all your Text Collections:

`DELETE https://api.yonderlabs.com/1.0/textcollections`





<aside class="success">
Remember — insert your credentials for authentication!
</aside>



