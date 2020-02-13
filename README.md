# Bulkhead and spring-boot

### Description

This project applies the bulkhead pattern in a spring-boot app.

The application should not fail if some parts of it don't work.
We will compartmentalize the application in such a way so that
failure is local to that area and it's not propagated to
other areas.

### Use cases

1. Static content is always displayed even in case
of database failure or failure to connect to a 
third-party web service
2. In case an integration with a third-party fails,
we should disable the appropriate functionality.
3. In case we fail to connect with the database,
we should disable the components that talk to the
database and handle it gracefully in the front-end.
4. The above errors can a) suddenly happen while
the application runs b) when the tomcat starts
because we released a new software. We should
handle both cases.
5. we should display the parts of the app that
we have disabled in the actuator.


#### Notes:

We have two options when it comes to failures

- retry until we recover
- disable the functionality until a new software 
release is deployed
- retry with a threshold and disable parts of the app
if the threshold is exceeded


#### How to build the project

    $ ./gradlew clean build
    
### How to run the server

    $ ./gradlew bootRun
    
Visit http://localhost:8080