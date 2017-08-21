# Write a Passthrough Service

Now that you have [written your first program](../first-program.md) and [written a main program](../main-program.md) for an integration scenario, it is time to work with services.

> This tutorial provides instructions on how to write a REST service that uses the Google Books API to get books about a given topic. This scenario is demonstrated by querying books on WSO2.

This tutorial consists of the following main sections.

- [Add a service](add-a-service)

> **Prerequisites**: Download Ballerina and set it up. For instructions on how to do this, see the [Quick Tour](../quick-tour.md). it is also recommended to try to [write your first program](../first-program.md) and [write a main program](../main-program.md) as some concepts are explored in detail in those tutorials.

## Set up a service for integration

When defining a Ballerina program as a service instead of an executable program, the `service` construct acts as the top-level container that holds all the integration logic and can interact with the rest of the world. Its base path is the context part of the URL that clients use when sending requests to the service. You create one service per Ballerina program file.

A service is a container of `resources`, each of which defines the logic for handling one type of request. Services are singletons, so all variables defined within a service scope are shared across all resource invocations. A service can have state for as long as it's active.

### About service URLs

In this tutorial, the service and the resource are also represented by the URL that you are calling. For example, the base path for a resource can be as follows: 

> http://localhost:9090/

The following is the URL for the `books` service:

> http://localhost:9090/books

If you are accessing a different service, like `magazines` for example, you can have magazines instead of books in the above URL.

If you are accessing a resource within this service, like book titles for example, the URL is as follows:

> http://localhost:9090/books/title

This is how resources and services can equate to the URL that you are calling.

### Add a service

1. To define a service in the Composer, drag the service from the tool palette to the canvas. You can then set the base path annotation using the `Annotations` button in the upper right corner of the service, and define any variables the service needs by clicking the `Variables` button in the upper left corner. 

    ![alt text](../images/AddService.gif)
    A new resource is added automatically with the service. This happens because a resource is required if you need to invoke something or get something back from the service. 
1. You can rename the service by providing an appropriate name.
    ![alt text](../images/ServiceName.png)
    You can start adding your integration logic.

### Add integration logic to your service

Now that you have added a service, you must set up this service so that it can be used in your integration scenario.

1. Select an HTTP identifier from the dropdown available. In this case, you can use GET as the HTTP verb, since you are aiming to get the information using a URL. If you use both a GET and a POST, you need to add a new resource. You can add more resources by dragging them from the tool palette and adding them to the service.
    ![alt text](../images/IdentifierHTTP.png)
1. As mentioned in [About service URLs](#about-service-URLs), the path for the books service is `http://localhost:9090/books`. Add an annotation by clicking on the label in the service and selecting `ballerina.net.http` from the dropdown.
    ![alt text](../images/AddAnnotation.png)
