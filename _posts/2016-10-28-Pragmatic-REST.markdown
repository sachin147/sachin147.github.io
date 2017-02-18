---
layout: post
title:  "Pragmatic REST"
date:   2016-10-23 18:00:00 +0530
---

<p>
In this post I'll be reflecting upon writing nice, clean, slick RESTful APIs.
Today in this web ecosystem, APIs have become a <u>language for communication</u>.
REST has become language of developers to understand, interprete and write a web API.
Writing RESTful API is a concept and hence a bit difficult to understand and implement.
Since its potrays, reflects a design of a system, the more clean, precise, expressive, the more easier it is to understand and use.
</p>

<p>
    APIs create a base for various business integrations.
    APIs reflect business model.
    APIs reflect 'UI of business'.
</p>

<p>
    RESTful web APIs work around resources in a system.
    You might probably need to go through understanding of 'what is REST'.
    For eg: A user can be identified as a resource, A vehicle is a resource.

    I will be considering a 'book' as a resource, around which the API will be designed.
</p>

<p>
<b>Following are the best practices for designing and writing a RESTful web API.</b>
</p>

<p>
    <h4>Keep the url simple.</h4>
    Two base urls for a resource is more than sufficient.
    For eg: 
    <li>/books</li>
    <li>/books/123</li>
    here in second url, 123 represents a specific book with id ( the resource id) in collection.
</p>

<p>
    <h4>Use nouns. No verbs in url</h4>
    <p>Do not use verb for operations on resource like</p>
    <p>/getBook, /getAllBooks, /findBookWithTwoAuthors</p>
</p>


<p>
    <h4>Use HTTP verbs</h4>
    Use HTTP verbs: GET, PUT, POST, DELETE.
    to operate on resource(s).
    For eg:
    <ul>
        <li>/books : To create(POST) book, To fetch(GET) books list, To update(PUT) books, To delete(DELETE) books </li>
        <li>/book/123 : To create(POST) book, To fetch(GET) book with id 123, To update(PUT) book with id 123,  To partially update(PATCH) book, To delete(DELETE) book with id 123 </li>
    </ul>
    
</p>

<p>
    <h4>/book or /books, plural or singular?</h4>
    Make sure to stick to one and dont mix both across API.
</p>

<p>
    <h4>Dont be abstract. Identify resources at most granular level.</h4>
    Dont generalize your resources, for example media resources like audio, video, book
    <li>/media is bad</li>
    <li>/audio , /video , /book is good</li>
</p>


<p>
    <h4>Stick to: /resource/id/resource</h4>
    Dont define more than 1 level of resource relationship hierarchy.
    <li>/book/1/author is good</li>
</p>


<p>
    <h4>Filter your resource(s) with ?</h4>
    To get books based on books attribute like totalpages, cover etc use ? and define the attributes as filters to fetch books.
    <li>/books?pages=2000&cover=hardback</li>
</p>


<p>
    <h4>Error handling</h4>
    Well not everything right happens in an API. So exceptions are equally important to be communicated. Do not generalize exceptions under one umbrella. Explicitly communicate the exception in the API response body as a message.
</p>

<p>
    <h4>Use HTTP status codes</h4>
    Error can be a client error or server error.
    Use HTTP codes to define them:
    <li>200 - success</li>
    <li>400 - Bad request</li>
    <li>500 - Internal server error</li>
    <li>404 - Not found</li>
    etc.
    These codes can help to properly communicate error and thereby making it useful for a developer to understand what type of error has occured and hence a correct error message can be communicated to client.
</p>

<p>
    <h4>JSON is in, XML is old</h4>
</p>

<p>
    <h4>Use camelCase for attributes in json response</h4>
</p>

<p>
    <h4>Versioning</h4>
    Specify version with a 'v'prefix and an integral number to the url base.
    <li>/v1/books</li>
</p>

<p>
    <h4>Pagination</h4>
    It is bad to fetch all records in one go. Therefore the best way to fetch records is in pages or chunks.
    There are many ways to define pagination. For eg: offset and limit, page and record per page, start and count.
    The best suit is possibly offset and limit as it is very well understood.
    <li>/books?offset=2&limit=10</li>
</p>

<p>
    <h4>Sorting</h4>
    Use a sort parameter. Put a '-' in front of sort parameter to indicate descending sort.
    <li>/books?sort=-rating</li>
</p>

<p>
    <h4>Searching</h4>
    A search value for global or local search can be indicated by 'q'
    <li>/book?q=searchparam</li>
</p>

<p>
    <h4>Partial Response</h4>
    Partial response is helpful when response is huge and you dont want each detail of a resource. It is helpful in utilizing bandwidth.
</p>

<p>
    <h4>GZIP - Compress your response</h4>
    This can help utilize bandwidth
</p>

<p>
    <h4>no resource situation</h4>
    In such situations there may not exist any resource around which api can be written. Use verbs in such situation
    For eg: translating a word from one language to another
    <li>/translate?from=ENG&to=HIN</li>
</p>

<p>
    <h4>Authentication</h4>
    OAuth2.0 to the rescue!
</p>

<p>
    <h4>Authorization</h4>
    Authorization cannot be handled by API. It can only be handled at service layer.
</p>
<p>
    <h4>Use HTTP headers wisely</h4>
    In case of overriding HTTP method, caching, CORS, rate limiting.
</p>
<p>
    <h4>Use HTTPS</h4>
</p>

<p>
    <h4>Validate input at server</h4>
</p>

<p>
    <h4>Using API key</h4>
    This is can perhaps be used to identify/authenticate origin of request. It is generally used for commercial APIs.
</p>

<p>
    <h4>Document your API</h4>
</p>

<p>
    <h4>My favourite API 10/10</h4>
    <li><a href="https://developer.github.com/v3/">Github API</a></li>    
</p>


