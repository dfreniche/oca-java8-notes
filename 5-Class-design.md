theme: Plain Jane
autoscale: true

# Class Design

---

## Inheritance

- IS_A vs HAS_A
- single inheritance
- extends vs implements
- a class can´t extend an Interface
- can't implement a Class
- against inheritance: http://www.yegor256.com/2016/09/13/inheritance-is-procedural.html

---

## Access modifiers for top-level classes

- public, (default)
- not private nor protected!
	- we can have inner or nested classes with those modifiers (not in OCA)

---

```java

// not in the same file: each class in a differente .java file
// also: name the files

public class A {
}
```

- yay or nay?

```java
private class B {
}	
```

- yay or nay?

```java
public default class B {
}	
```

- yay or nay?



---

## Calling super members

- only public & protected

---

## Constructors

- default constructor: added by the compiler
- calling always super() or this()
- constructor chaining
- watch out! private constructors

---

## Constructors: private constructors!

```java
class A {
    private A() {
    }
}

class B extends A { // comp error: There's no default constructor available in A
   // we can't call super()!
}

```

---

## Constructors: private constructors!

```java
// problem solved

class A {
    private A() {
    }
    public A(String s) {
        
    }
}

class B extends A {
    public B() {
        super(null);
    }
}

```


---

## Init order

```java
public class Main {
	public static void main(String[] args) {		
		System.out.println("In main");
		
		Test t1 = new Test();
		Test t2 = new Test();
	}	
}

class Test {
	static int staticNumber = 1;

	static {
		System.out.println("static block 1 " + staticNumber);
		staticNumber = 10;
	}
	
	{
		System.out.println("instance block 1");
	}
	
	public Test() {
		System.out.println("Inside constructor");
	}
	
	{
		System.out.println("instance block 2");
	}
	
	static {
		System.out.println("static block 2 " + staticNumber);
	}
}

```

---

```

In main
static block 1 1
static block 2 10
instance block 1
instance block 2
Inside constructor
instance block 1
instance block 2
Inside constructor


```

---

## super() vs super

```java
class A {
    private int i1;
    int i2;
}

class B extends A {
    public B() {
        System.out.println(i2);
        i2 = 10; // OK, can see it
        System.out.println(i2);
        super.i2 = 11; // it's the same
        System.out.println(i2);
        this.i2 = 12; // same again
        System.out.println(i2);

    }
}
```

---

## Overloading vs. Overriding

- override a method: same method in child class
- overload a method: same method name, different parameters

---

## Overriding checks
- same signature
- method in child class at least as accessible as method in parent class
- can't throw new / broader checked exceptions
- if returns a value, same type or sibclass of the method in parent class (covariant returns) [^1]

[^1]: preserves the ordering of types 

---

## final methods

- can't be overridden

---

## Redeclaring private methods

- private methods can't be overridden

---

## Static method hiding

- no such thing as static method overridding exists

```java
class A {
    public static void m1() {
        System.out.println("In A");
    }
}

class B extends A {
    public static void m1() {	// not "overridding", just same name
        System.out.println("In B");
    }
}

A.m1();	// In A
B.m1(); // In B

A a = new B();
((B)a).m1(); // In B

```

---
## Hiding instance variables

- that's why getters/setters are nice!

```java
class A {
    private int i1;
    int i2;
}

class B extends A {
    int i1; // no problem, doesn't exist here
    String i2;  // hiding instance vars!

    public B() {
        System.out.println(i2);
        i2 = "b"; // OK, String var
        System.out.println(i2);
        super.i2 = 11; // OK, int var
        System.out.println(super.i2);
        this.i2 = "b2"; // sOK, String var
        System.out.println(i2);

    }
}

```


---

## Abstract classes

- a class that is marked as abstract
- can't instantiate objects from this class
- can have concrete & abstract methods

- exercise: create an abstract class
- excersise: extend an abstract class

---

## Interfaces

- method signature inside interfaces: __public abstract__ always
- marker interface: empty interface
- variables inside interfaces: __public static final__ always (static constants)

---

## Interface inheritance

- can inherit from multiple interfaces

```java
interface I {
	void m1();
}

interface II extends I {
	void m1();
	public abstract void m2();
}

class A implements II {
	@Override
	public void m1() {		
	}

	@Override
	public void m2() {		
	}
}
```

---

## Default methods in interfaces

```java
public interface Test {
	public default int getInt() {
		return 1;
	}
}

```

- can't be abstract, final, static
- problems with multiple inheritance?

---
 
## Static methods in interfaces

```java
interface I {
	void m1();
	
	static void sm1() {
		System.out.println("sm1");
	}
}
```

---
 
## Polymorphism

- we can "see" only the part of the object we're interested in
- at runtime, if we call a method, the __true__ one is the method from the instance clas, not the reference one
