https://msdn.microsoft.com/en-us/library/ff921087.aspx

#### Why use dependency injection?
- When a class uses multiple services (dependencies), but without DI I'll have to
  - test my classes with my dependencies
  - has repetitive code for creating, locating, and managing dependencies
  - change my class when I change my dependencies

So, I should instead use DI to decouple my dependencies from the dependent class.

This means selecting a concrete implementation type for class dependencies will be delegated to an external component, rather than the class.

Two different ways to do DI:
- constructor injection (use parameters of object constructor method to express dependencies, builder injects with dependencies. class uses dependent class' interface rather than class directly)
- setter injection (dependencies expressed thru setter properties, builder uses to pass dependencies during object initialization)

