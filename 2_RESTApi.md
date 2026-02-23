# REST
Representation State Transfer.  
API : Application programming interface

Let's take netflix example

172.17.18.19 => Server  
:8080 => Port  
/endpoint

`172.17.18.19:8080/netflix/plan5` : URL

To talk server we need this URL + **HTTP Verb** which together is reffered as REST Api

###  HTTP Verbs

1. GET : To view
2. POST : Create
3. PUT : Modify
4. DELETE : To delete

---

### Controllers ?
Special components that handles http requests.

```java
@RestController
public class className{
    //We create endpoints as methods
}
```

`@RestController` converts everything that is being returned into json.  

---
### Path Variable vs Request Parameter

if we use `?` in URL,  