# Item 1 : use static factories instead of constructors
* Pros
 1. Can have multiple methods with identical parameters but different behaviour, which isn't true for constructors
 2. Useful for some singleton classes or where you already have a preconstructed object that can be passed to all callers

* Cons
 1. Difficult to make out as constructor role in docs
 2. need at least one non-private constructor in a class to inherit
 
 
# Item 2 : use builder pattern
* Pros 
 1. Useful when there are too many parameters to the constructor of the same type or its difficult to remember the ordering of args to constructor
 2. Serves as a default arg mechanism
 
* Cons
 1. More verbose
 2. Slight penalty in constructing a builder object in addition to the required class object
