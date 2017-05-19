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

---

## Access modifiers for top-level classes

- public, (default)
- not private, protected!


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
- private constructors


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

## Overloading vs. Overriding

- Overriding checks
	- same signature
	- method in child class at least as accessible as method in parent class
	- can't throw new / broader checked exceptions
	- if returns a value, same type or sibclass of the method in parent class (covariant returns)

---

## Redeclaring private methods

- private methods can't be overridden

---

## Static method hiding

---
## Hiding instance variables

---

## Abstract classes

- create
- extend an abstract class

---

## Interfaces

- interface inheritance
- method signature inside interfaces: __public abstract__ always

---

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
