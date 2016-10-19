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

#Item 3,4 : Use private constructor for singleton or to avoid instantiation
* Some classes are just a collection of static methods and it doesn't make much sense to instantiate them. If you don't include any constructor, the default constructor will be added to the class. To avoid, declare a private constructor.
* Singletons can be declared using a private constructor with a public static field /method. Method is more flexible since you can later change it to be non-singleton without changing any clients
* Easily the safest way to create singletons is to use enums. Will protect against serializabilty and reflection attacks

# Item 5 : don't construct objects unless absolutey needed
* Constucting a new object in a loop each time when a single declaration would do is expensive
* Similar examples include using  s = new String("xyz") instead of s = "xyz"
* Autoboxing/ unboxing is also another example of creating extra objects

# Item 6 : null a reference when object is no longer needed
* Its actually better to avoid this by declaring an object in the tightest possible scope, so it will automatically fall out of scope
* But sometimes a class may manage its own memory, for instance a stack allocates an array as its internal storage and expands or shrinks as needed. Now eventhough an object was popped out of the array, the array entry still maintains a reference and thsi can't be GC'd. Thsu you should always null it. 

# Item 7 : Avoid using finalize
* There is no guarantee when finalize is actually executed, so it is better to free important resources as soon as they are not required. Otherwise you might run out of resources. 
* Sometimes it may be necesarry to use finalize when working with native objects, but it should be used with care.
8 Instead it is better to provide explicit terminaiton methods in the resource class, and this can be called in the finally block. For e.g most streams and files have a close method.

# Ch2
* Mainly about overriding methods common in all objects - equals, hashCode, toString, clone, finalize

# Item 8 : override equals
* Only exception is if the class has a private constructor, or is non-instantiable, or the superclass override is sufficient, or all objects in the class are guaranteed to be unique, e.g thread class
* Important that the equals method follows contract of reflexivity, symmetry and transitivity
* Because of this it is often difficult to add a value member in the subclass, since it may violate symmetry
* The solution in this case is to prefer composition over inheritance
* Also its important that equals method should never throw any exception
* Always remember equals method takes as argument Object o and not Myclass o , otherwise it won't override the equals method in the object
* Typically 3 steps
** this == o return true
** if (! o instanceof Myclass) return false
** Myclass t = (Myclass) o
** custom equality comparison between value fields of o and t

# Item 9 : always override hashCode when you override equals
* Otherwise hashmap, hashset other such generics will not work as expected
* usually you may compose hashcodes of different value members, 
* Its important that if 2 objects are equal via equals, they have the same hashcode

# Item 10 : override toString
* Makes it easy for programmers when printing out debug info
* either specify the format, will make it easy to parse elsewhere but tie you in a particular format, or don't

# Item 11 : Never use clone
* clone() and Cloneable interface are bad.
* Prefer using copy constructor / static factory instead of clone.

# Item 12 : Not required but implement Comparable
* Comparable is a parametrized interface
* implement int compareTo(MyClass c){...}
* Will make it easier to take advantage of collections like TreeSet and other sorting capabilities.

