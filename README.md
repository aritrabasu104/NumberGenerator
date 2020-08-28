# Spring Boot "Microservice" Project - number generator

This is a sample Java / Spring Boot application with NIO file operations, Spring Caching,Exception Handling, Junit Test cases and Swagger. The api details can be found in http://localhost:8080/swagger-ui.html(or deployment-url/swagger-ui.html for cloud deployments)

## Problem
The API should write into a file /tmp/{TASK_ID}_output.txt in the descending order  ,a sequence of numbers in the decreasing order till 0 , with step and start number given  as input  ;The First API returns a task;When the status of the task is called, the second API , it has to return appropriate status SUCCESS if done or IN_PROGRESS if task is still running;
The third API when called with a completed task should return the list of numbers reading from the file;

## Solution
Writing files asynchronously with a custom thread pool whose configuration is provide in config file of app, using java nio for better performance

#### Solution type: back-end,.
Reasoning:
1. ThreadPool: Need asynchronous behaviour as opposed to synchonous in spring mvc.
2. Preconfigured custom instead of Cached: Because the deployment will have memory constraints.
3. Architecture: Standard MVC architecture used.
4. NIO: improves performance by sharing threads when parallel requests are coming.
5. Cahcing: Will improve read performance for large files when requested multiple times.

#### Trade-offs: The configuration might need to be tweaked according to performance / hardware constraints.
If you were to spend additional time on the project - externalize caching to use Redis and use a benchmarking tool to find the right setting for Threadpool

Link to your resume or public profile - can be found in swagger project description

## How to Run 

This application is packaged as a war which has Tomcat 8 embedded. No Tomcat or JBoss installation is necessary. You run it using the ```java -jar``` command.

* Clone this repository 
* Make sure you have JRE/JDK 1.8 or higher 
```
        java -jar  vmware-numbergenerator-1.0.jar
or
        mvnw spring-boot:run 
```