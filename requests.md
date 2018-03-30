---
layout: page
title: API Requests
---


<div class="message">
  Well, it's time to understand how the Neoway BI API works.
</div>

You do not have to worry about this step. We are here to make it works well.

First, you have to decide if you are going to use one of our extractors or if you prefer to build your own extractor. We really recommend you to use one of our extractors for some reasons as follows:

- It is the easier way for you to interact with the Neoway BI API.
- Considering that we developed the BI API we know exactly the best way to interact with it.
- Our extractors are optimized.


### Pick one method:
1. [Use Neoway BI API extractors.](#bi-api-extractors)
2. [Develop an extractor.](#develop-an-extractor)


### BI API EXTRACTORS

Thinking how to make this process easier we developed two extractor options. One written in **QlikView Language** and another one written in **JavaScript**, based on **Node.JS**.

When you contract BI API the BI Team will contact you and provide access to both Git repositories where you will find the instructions to use each one extractor on **"README"** file.

1. [Extract Node and Documentations](https://github.com/neowaycx/extract_api_node)
2. [Extract QlikView and Documentations](https://github.com/neowaycx/extract_api_qlikview)


### DEVELOP AN EXTRACTOR

The BI API was developed to work fast and we choose to build a pagination function to provide *n* records per page. It means you have to tell us how many records you want to get per page and other parameters that we will list and explain here.

As we said before, it is a *RESTful API*, so first of all, you must open a rest connection to make your GET request and you have to iterate the pages.

To get the request permissions, you'll first need to get an access token. You can make a post request for `https://api.neoway.com.br/auth/token`

*Example of curl request on linux or macOs X*
> `curl -X POST https://api.neoway.com.br/auth/token -d '{ "application" : "your-application-name", "application_secret" : "your-secret" }'`

*Example of curl request on Windows*
> `curl -X POST https://api.neoway.com.br/auth/token -d "{ \"application\": \"your-application-name\", \"application_secret\": \"your-secret\" }"`

> **Important!** - *The access toke is valid for 30 minutes*

After POST request, you will receive an access token to initiate the data request process.

*For data requests, you will do a curl this way*
> `curl -X GET https://api.neoway.com.br/services/bi/sumOfClients -H 'limit: 1' -H 'skip: 0' -H 'authorization: Bearer <yourAccessToken>'`

> **Important!** - *The threshold parameter will accept up to 10,000 records per page. Above this the request will be denied.*

The request response is structured in json format. In this way, we have in this answer all fact data at a json level called results and terms the number of records at the count level.

Following this proposal, we suggest that the extraction logic continue to observe the values of the limit parameter that was informed, with the value of the count level coming from each request. So when count is less than limit it indicates that we have reached the end of the data.


### What kind of tools can I use to analyze these data?

You can use any tool that is able to read data from files, databases or data APIs. 
There are free options available such as Pentaho and Talend, but also there are paid options such as QlikView, Tableau and Power BI.


## Postman sample:

We have prepared a json file, where you can import this file into Postman.
[Postman sample here.](https://github.com/neowaycx/BIApiDocumentation/blob/gh-pages/postmanRequests.json)