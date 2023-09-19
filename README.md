# Quickstart for a Spring Boot project

This quickstart contains the following:
- CORS configuration
- OpenApi configuration
- JWT authentication
- Users handling
- Images handling
- Article entity as an example
- Generic utilities to bootstrap the DAO and Service creation

## Introduction

This is a quickstart for a REST API in a Spring Boot done in Spring boot version 3.1.3 and Java 17. It handles:
- Images as files to put into a database
- Authentication by using JWT token
- Issuing of the JWT tokens
- A data-rich entity as a blog article
- OpenApi documentation
- CORS configuration

The project is modularized monoloth that follows Domain Driven Design as much as possible. By default the three domains are:
- Article: entity mapped to the database with a large variety of data types
- Authentication: handler of Spring Security
- Image: can be used as a starting point for generic files too

The Authentication domain is further divided into:
- Token: handler of JWT tokens (creation and renewal)
- User: handler of a user as an entity mapped to Spring Security
The relation between these two subdomains is _One User has many Tokens_

## Local execution

This project comes boundled with a maven wrapper. The only needed thing is to have java set as path. Once done that run the following command from the uppermost folder:
```bash
./mvnw spring-boot:run
```
The project will be available by default on the port `8080`.
For the auto-generated documentation go to `http://localhost:8080/swagger-ui/index.html`

To install java it is recommended to use [sdkman](https://sdkman.io/)


## File structure

```bash
.
├── config            # The configuration files of the application
├── domain            # All the domains (modules) of the project
│  ├── Article        # Article domain
│  ├── Authentication # Authentication greater domain
│  │  ├── Token       # JWT token domain
│  │  └── User        # Spring Security user domain
│  └── Image          # Image domain
├── filter            # Filters
└── util              # Generic utilities to bootstrap a domain easier
```

## Dependencies

This project has no external dependencies as it uses just the following maven libraries available in the `pom.xml` file:
- lombok
- spring boot web starter
- spring boot jpa
- openapi documentation
- h2 database
- JWT api, implementation and jackson converter