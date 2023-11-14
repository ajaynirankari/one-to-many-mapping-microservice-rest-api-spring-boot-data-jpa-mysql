# one-to-many-mapping-microservice-rest-api-spring-boot-data-jpa-mysql

MySQL Database setup
--------------------
1. Login MySQL
2. Create the Database from below commands
```
DROP DATABASE IF EXISTS onetomanymapping;
CREATE DATABASE onetomanymapping;
CREATE USER 'dbUser'@'%' IDENTIFIED BY 'dbUser';
GRANT ALL ON onetomanymapping.* TO 'dbUser'@'%';
```

File - src/main/resources/application.properties
-------------------------------------------------
```
spring.datasource.url=jdbc:mysql://localhost:3306/onetomanymapping
spring.datasource.username=dbUser
spring.datasource.password=dbUser
spring.jpa.hibernate.ddl-auto=update
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.show-sql=true
```

Steps to Run Application
------------------------
1. Open Git Bash
2. git clone https://github.com/ajaynirankari/one-to-many-mapping-microservice-rest-api-spring-boot-data-jpa-mysql.git
3. cd one-to-many-mapping-microservice-rest-api-spring-boot-data-jpa-mysql/
4. ./mvnw clean spring-boot:run

Steps to Test Application
-------------------------
1. Open Git Bash
2. curl -v http://localhost:8080/authors | jq

```
$ curl -v http://localhost:8080/authors | jq
*   Trying 127.0.0.1:8080...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to localhost (127.0.0.1) port 8080 (#0)
> GET /authors HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.78.0
> Accept: */*
>
* Mark bundle as not supporting multiuse
< HTTP/1.1 200
< Content-Type: application/json
< Transfer-Encoding: chunked
< Date: Tue, 14 Nov 2023 08:07:15 GMT
<
{ [260 bytes data]
100   254    0   254    0     0   1089      0 --:--:-- --:--:-- --:--:--  1094
* Connection #0 to host localhost left intact
[
  {
    "id": 2,
    "name": "Johm",
    "books": [
      {
        "id": 4,
        "name": "Match",
        "type": "General"
      },
      {
        "id": 5,
        "name": "Physic",
        "type": "Science"
      }
    ]
  },
  {
    "id": 1,
    "name": "Smith",
    "books": [
      {
        "id": 1,
        "name": "Java",
        "type": "CS"
      },
      {
        "id": 2,
        "name": "C++",
        "type": "CS"
      },
      {
        "id": 3,
        "name": "SQL",
        "type": "CS"
      }
    ]
  }
]

```

Test REST API via Swagger
-------------------------
URL: http://localhost:8080/swagger-ui/index.html
![image](https://github.com/ajaynirankari/one-to-many-mapping-microservice-rest-api-spring-boot-data-jpa-mysql/assets/26870634/d340b39d-435b-4107-875f-0b9fff0a9bfa)

Configure for the Swagger-UI
-----------------------------
Reference Link: https://springdoc.org/

Add below dependency in pom.xml
```
   <dependency>
      <groupId>org.springdoc</groupId>
      <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
      <version>2.2.0</version>
   </dependency>
```


