## Text Extraction

> Request example ...



```shell
curl --ssl-reqd --request POST -u YOUR_USERNAME:YOUR_PASSWORD --data url=http%3A%2F%2Fwww.theatlantic.com%2Finternational%2Farchive%2F2015%2F11%2Frussia-doping-2016-olympics%2F416604%2F "https://vm3.yonderlabs.com/1.0/text/textextraction"
```

> ... and response body (200/JSON):

```json
{
  "url": "http://www.theatlantic.com/international/archive/2015/11/russia-doping-2016-olympics/416604/", 
  "text": "With less than nine months to go for the 2016 Olympics in Rio de Janeiro, Russia is trying to break a world record in the 90-day sprint. A little more than a week after a commission of the World Anti-Doping Agency (WADA) issued a report that accused Russia of essentially hosting a state-sponsored doping program, Russia launched a task force to rid itself of its doping infection so it may compete in the Olympics. In three months, we will once again go to the international federation to present ourselves as compliant with its standards, Vitaly Mutko, the Russian sports minister, said on Russian television. We hope our team will be reinstated. You may recall that Mutko was one of the many Russian officials to denounce the WADA report last week, calling it baseless and really fictional. But that changed Friday after Russia was provisionally banned from all international track and field competitions. But in an eyebrow-raising deal with the International Olympic Committee in Switzerland last week, Russia could compete in the Olympics if it agrees to punish past offenders, including coaches, officials, and athletes, fixes its program, and fields a clean team. There is skepticism about Russia's ability to clean up its program either by itself or in time for 2016. There have been calls for the investigation into the country's track and field program to expand. A full investigation should be carried out into the failed testing of Russian athletes from ALL sports, one athlete from the most recent Olympics in Sochi, Russia, wrote in a letter to WADA. Those issues as well as the question of whether more countries should be investigated\u2014which was one recommendation of last week's report\u2014are on the docket as WADA meets on Wednesday in Colorado."
}
```

**Extract text from a webpage removing all other undesired content**

This service extracts the main text from a webpage, discarding navigation links, advertisements and other undesired content.

### HTTPS request

Attribute | Type | Description | Values |
--------- | ------- | ----------- | ------ |
url | string, required | the URL of the text document | use [url-encoding](http://www.url-encode-decode.com/)|

Examples of how-to-call the API and the related output are provided in the right panel.

<aside class="success">
Remember — insert your credentials for authentication!
</aside>





