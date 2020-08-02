# Software Architecture Study

This repository is a deep study about different kind of software architectures applied by the most famous companies.

## Wildlife Studios

### Bibliographic Reference

- [How I Write Backend Systems at Wildlife Studios](https://medium.com/tech-at-wildlife-studios/write-backend-systems-50aae8db849e)

### Introduction

They usually divide their system into three meaningful layers:

**Delivery Layer ➡️ Business layer ➡️ Data Access Layer**

It is done in order to define a single data flow direction, what helps avoiding future problems like *Cyclic Dependency and High Coupling*. Each layer is responsible for a subset of operations for each known entity.

### Boilerplate organization

- API (Delivery Layer)
  - Often there's a server listening for HTTP or gRPC external requests.
  - That's the layer closest to clients, it receives inputs, knows how to format them and passes it to the *Business Logic Layer*.
  - So, basically it means that layer receives a raw input, formats it and passes it to some entity or model on the *Data Access Layer* with help of some function from the *Business Logic Layer*.

	*Ex: A HTTP Server.*

- CMD (Distribution)
  - All the main packages that handles initialization for executables, parses configurations, etc.
	
	*Ex: A Compiler can be here.*

- Models (Data Access Layer)
  - Holds business objects that are frequently used. Not only knows about business members but also has methods to apply transformations and access their internal structures.
	
	*Ex: A Customer Repository.*

- Storage (Data Access Layer)
  - Define interfaces to run data operations on storage engines. 
	
	*Ex: Postgres, S3, RAM, Redis*

- UseCases (Business Logic Layer)
  - Define interfaces for operations over entities (the features on the software).
  - Interfaces are used both in storage and here in order to help mocking on unit tests and to reuse it if you need a wrapper over and existing use-case.

	*Ex: CreateUserUseCase*