---
layout: post
title:  "Exception handling- Best practices"
date:   2016-12-04 18:00:00 +0530
---


Well we all have been handling Exceptions in our programs for exception scenarios.
But are we doing it right?

Here are the following rules, which I definitely feel should be followed in process of handling any exception

<p>
    <h4>Dont generalize exceptions</h4>
    Do not create a single top level custom Exception which does the whole exception handling task. Learn from API designers of JAVA programming language.
</p>

<p>
    <h4>Identify exceptions at least granular level</h4>
    Try to identify exceptions at least meaningful level so that exceptions are clearly and precisely identified. 
    Do remember one thing, a granular thing can be coalesced but a coalesced thing cannot be granularized in programming.
</p>

<p>
    <h4>Give exceptions some codes while dealing at service layer</h4>
    Exceptions can be assigned codes similar to HTTP status codes, which eventually helps client to understand the error.
</p>

<p>
    <h4>Log exceptions beautifully</h4>
    Exceptions should be logged in a beautiful manner, so that maximum information can be extracted from logged information.
</p>