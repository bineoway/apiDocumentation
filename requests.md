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

[Extract Node Documentation](#https://github.com/neowaycx/extract_api_node)

[Extract QlikView Documentation](#https://github.com/neowaycx/extract_api_qlikview)


### DEVELOP AN EXTRACTOR

The BI API was developed to work fast and we choose to build a pagination function to provide *n* records per page. It means you have to tell us how many records you want to get per page and other parameters that we will list and explain here.

As we said before, it is a *RESTful API*, so first of all, you must open a rest connection to make your GET request and you have to iterate the pages.


### What kind of tools can I use to analyze these data?

You can use any tool that is able to read data from files, databases or data APIs. 
There are free options available such as Pentaho and Talend, but also there are paid options such as QlikView, Tableau and Power BI.


## Postman sample:

Postman sample here.