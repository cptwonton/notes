#### What is Spring?
- open source Java platform, provides infrastructure support for developing robust Java apps quickly
- written by Rod Johnson, released in June 2003 under Apache 2.0 license
- most popular app development framework for enterprise Java 
- very lightweight, basic version is only 2MB
- goal is to make J2EE development easier to use
- promotes good programming practices by using POJO-based programming model

#### Benefits of Spring?
- allows developers to develop enterprise-class apps using POJOs (plain-old java objects)
  - do not need an EJB container product, like app server
  - can instead use robust servlet container like Tomcat
- modular, so pick and chose what I want
- reuses existing technologies like logging frameworks, timers, etc...
- testing is very easy using depedency injection and bc environment-dependent code is moved into the framework
- Spring's web framework is MVC
- convenient API to translate technology specific exceptions into consistent, unchecked exceptions
- IoC containers are more lightweight compared to EJB containers
- Dependency Injection, one form of Inversion of Control (IoC), makes things more modular and allows for good testing practices
- Aspect Oriented Programming (AOP), i.e., logging and caching and security are separate from business logic
  - key unit in OOP is a class, key unit in AOP is aspect
  
#### IoC Containers
- core of Spring framework
  - creates objects
  - wires objects together
  - configure objects
  - manage complete life cycle of objects from creation till destruction
- uses DI to manage components that make up an app
- objects are called Spring Beans
- input POJOs + config metadata (XML, java annotations, java code), output bean
- two types of containers:
  - Spring BeanFactory Container
    - simplest container
    - provides basic support for DI
    - defined by org.springframework.beans.factory.BeanFactory interface
  - Spring ApplicationContext Container
    - enterprise-specific functionality like resolving textual messages from properties file
    - publish application events to event listeners
    - defined by org.springframework.context.ApplicationContext interface
- ApplicationContext does everything BeanFactory does, so applicationcontext > beanfactory except when we care about being lightweight for speed or data volume

#### Beans
- objects that form the backbone of app, managed by Spring IoC containers
- created with config metadata, which defines for the container:
  - how to create a bean
  - bean lifecycle
  - dependencies

###### Bean Scopes
- specified when defining a bean
- `prototype` forces Spring to create new bean instance every time one is needed. use for stateful beans
- `singleton` forces Spring to reuse the same bean instance (default). use for stateless beans
- `request`, `session`, `global-session` only available to web-aware ApplicationContext container

###### Bean Lifecycle
- simple. when starts up, does `init-method` to get bean into usable state. when no longer required and removed from container, `destroy-method` is run
- can be done either in xml config metadata xml, OR by implementing InitializingBean interface's `afterPropertiesSet()` method and/or DisposableBean interface's `destroy()` method.

