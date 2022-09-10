# Spring

## Topics to cover

## Quiz

* Define a function which adds two numbers and returns the result after given time using promises

 <details>
 <summary>Solution</summary>

 function timer(n) {
   return new Promise((resolve) => setTimeout(resolve, n));
 }
 async function add(a, b) {
   await timer(500);
   return a+b;
 }
 (async function() {
 console.log(await add(2,3));
 })()
 </details>

<!-- tooltips -->
*[JVM]: Java Virtual Machine
<!-- tooltips end -->

## Documentation / Specification

[Book The introduction to algorithms](https://docs.google.com/viewer?a=v&pid=sites&srcid=ZGVmYXVsdGRvbWFpbnxhbGdvcml0aG1zaWNzMzUzfGd4OjI3ZjYxZjM3MmI1NGNhNmU)

## Notes

1️⃣🚩Reference
[Learn Spring: The certification class by Eugen Paraschlv](https://courses.baeldung.com/courses/)

📘 Module 0 - Before you start

### Course Introduction

📘 Module 1 - Getting Started with Spring 5
📃 Lesson 1 - Why Spring?

#### What is Spring?

* Spring is a backend technology with a very broad range of uses, commonly for developing web applications, but not limited to that.

Spring VS Java EE - initially was developed to overcome JEE implementation complexity. Now it covers so much over JEE.

#### Why Spring?

1. Core goal - remove complexity
2. Not an all or nothing decision
3. Plumbing for your system

#### Learning Spring

* A very long term investment
* Moving fast at the edges
* Stable core

📃 Lesson 2 - Understanding the full spring Ecosystem

#### The Spring Ecosystem

* Spring Ecosystem grew over time as the framework was successful, Not it is quite vast, but we can choose what is needed and implement it.

1. Spring Core
     * Core of the framework,
     * Contains the container with dependency injection, Spring Expression Language(SpEL), Aspect oriented programming(AOP), Testing framework and more advanced features.
2. Spring MVC
     * Web support,
     * REST support,
3. Spring Persistence
     * Data access
     * Transaction support
     * DAO support
     * JDBC
     * ORM support
     * SQL support
     * Hibernate
     * JPA
     * Spring Data projects
4. Spring security
     * is the security system in the Java Ecosystem
     * you can still use spring security on top of a non spring application as long as its running on a servlet environment
5. Spring Cloud
     * Support for Distributed systems
     * Support for micro services

6. Other spring projects - Spring Batch, Spring Integration, Spring HATEOAS, Spring Web Flow, Spring Web Services.

* Spring Roo, Groovy - are previous attempts to fix the large complexity of spring ecosystem
* Spring Boot is the latest one

📃 Lesson 3 - Introducing spring Boot

#### Spring Boot