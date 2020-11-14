# RESTful
 Now, let's dwell on REST. This abbreviation stands for representational state transfer. The definition can be conveyed with simpler words: data presentation for a client in the format that is convenient for it. There is one of the main points that you need to understand and remember: REST is not a standard or protocol, this is an approach to or architectural style for writing API.

 A simple definition of RESTful API can easily explain the notion. REST is an architectural style, and RESTful is the interpretation of it. That is, if your back-end server has REST API and you make client-side requests (from a website/application) to this API, then your client is RESTful.
 
 ## How It Works
RESTful API best practices come down to four essential operations:

-  receiving data in a convenient format
- creating new data
-  updating data
- deleting data

 REST relies heavily on HTTP. We will not explain the features of this protocol, but it is worth mentioning its great advantage in this situation.
Each operation uses its own HTTP method:
* GET - getting
* POST - creation
* PUT - update (modification)
* DELETE - removal
All these methods (operations) are generally called CRUD. They manage data or as Wikipedia says, "create, read, update and delete" it.
The fact that REST contains a single common interface for requests and databases is its great advantage. This can be viewed in the table below.

![](https://d1xple9gxb4tux.cloudfront.net/assets/images/article_images/3549550fac75d816c27485b692dc2cf38af579e8.png?1553504752)

All requests you make have their HTTP status codes. There are a lot of them and they are divided into 5 classes. The first number indicates which of them a code belongs to:
*	1xx - informational
*	2xx - success
*	3xx - redirection
*	4xx - client error
*	5xx - server error

![](https://d1xple9gxb4tux.cloudfront.net/assets/images/article_images/bd4442aed16acafc54c7943d34abff0edadfa74c.png?1553504574)

