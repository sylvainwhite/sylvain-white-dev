---
layout: misc
title: "REST principles"
author: "Sylvain White"
categories: subCategory
tags: [protocols,architecture]
# image: city-2.jpg
---
<br/>

## A brief introduction to REST

* In summary (from Stefan Tilkov [[web](https://www.infoq.com/articles/rest-introduction/){:target="_blank"}]), the five key principles are:
    * Give every “thing” an ID
    * Link things together
    * Use standard methods
    * Resources with multiple representations
    * Communicate statelessly

<br/>

## Relation between REST methods and CRUD operations 

* A summary table with REST methods and CRUD operations 
(CREATE, READ, UPDATE, DELETE) from Todd Fredrich [[web](https://www.restapitutorial.com/lessons/httpmethods.html){:target="_blank"}]

| HTTP&nbsp;methods | CRUD | Entire&nbsp;collection | Specific&nbsp;item |
|-------------------|------|------------------------|--------------------|
| POST           | CREATE         | 201 (Created), 'Location' header with link to /customers/{id} containing new ID. | 404 (Not Found), 409 (Conflict) if resource already exists.|
| GET            | READ           | 200 (OK), list of customers. Use pagination, sorting and filtering to navigate big lists. | 200 (OK), single customer. 404 (Not Found), if ID not found or invalid.|
| PUT            | UPDATE/REPLACE | 405 (Method Not Allowed), unless you want to update/replace every resource in the entire collection. |200 (OK) or 204 (No Content). 404 (Not Found), if ID not found or invalid.|
| PATCH          | UPDATE/MODIFY  | 405 (Method Not Allowed), unless you want to modify the collection itself. | 200 (OK) or 204 (No Content). 404 (Not Found), if ID not found or invalid.|
| DELETE         | DELETE         |  405 (Method Not Allowed), unless you want to delete the whole collection—not often desirable.| 200 (OK). 404 (Not Found), if ID not found or invalid.|

<br/>

## Web API - Crafting Interfaces that Developers Love

Excellent document on how to create a REST API with concrete world examples.

"Web API Design - Crafting interfaces that developers love" by Brian Mulloy
[[pdf]({{ site.github.url }}/resources/webApiDesign.pdf){:target="_blank"}]
[[web](https://pages.apigee.com/rs/apigee/images/api-design-ebook-2012-03.pdf){:target="_blank"}]