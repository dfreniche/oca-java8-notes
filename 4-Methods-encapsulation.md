theme: Plain Jane
autoscale: true

# Methods / encapsulation

---

## Method signature

```java

public     final 	          void    	sayHello     (String message) throws RuntimeException

access	 | final  	     |   return   | method name | parameter list | throws Exception list
modifier | (optional)    | type name  |
````

- return type: check type
- method name: valid identifier

---

## Return type


```java
Void m1(String s) {
        return null;
}

void m1(String s) {
        // no return
}

String m1() {
	return "hello";
}	


```

---

## Varargs

- vargars __must__ be lastargument
- there can be only one

1. Exercise: create a method `calcMedian` that returns the median value of n `int` numbers. At least you must pass one value
1. Exercise: create a method `hodor` that given some Strings returns a single string with s1 + " Hodor! " + s2 + " Hodor! "

---

## Access modifiers for members

- 3 keywords, 4 levels: private, protected, (package), public

---

## Access modifiers: explain why are all wrong

```java

public void public m1() {}

public void m1 {
}

package void m1(String s) {
}

protected int m1(String s) {
}

protected void final m1(String s) {}

protected void m1(String s);


```

---

## Method modifiers

- static: class method
- abstract: method has no body, child class should override it
- final: can't override this method
- synchronized: thread safe
- strictfp (__not__ in OCA/OCP): floating point calculations IEEE 754 [^1]
- native (__not__ in OCA/OCP): to interact with native libraries (C, C++)

 
[^1]: Strictfp ensures that you get exactly the same results from your floating point calculations on every platform. If you don't use strictfp, the JVM implementation is free to use extra precision where available.  
http://docs.oracle.com/javase/specs/

---

## Static

- variables
- methods
- static imports

---

## Passing by value

- passing by value vs. passing by ref
	- in Java there's only pass by value
	- we pass a __copy__ of the reference
- simple types
- object types

---

## Overloading methods

---


## Lambdas

- use IntelliJ to learn how to write them :-D
- A Lambda is just a piece of code we can pass around. Think of it as a function pointer.
- Lambda that takes a string as param and doesn't return anything

```java
(String s) -> { ...statements; };
```

---

## Without lambdas...

```java
Runnable task1 = new Runnable() {
	@Override
	public void run() {
		System.out.println("Something!");
	}
};
task1.run();

```

### With Lambdas...

```java
Runnable task2 = () -> { System.out.println("Yeah!"); };
task2.run();
```


---

### We can omit {} if there's only one statement

```java
Runnable task2 = () -> System.out.println("Yeah!");
task2.run();
```

---

## Functional interface

- a functional interface has exactly one __abstract__ method
- default methods in an interface have an implementation, they are not abstract

```java

public class Main {
    public static void main(String[] args) {
        Downloadable d;

        d = uri -> { return uri + " Downloaded"; };
    }

}

interface Downloadable {
    String download(String uri);
}


```

---

## Pass something to the lambda, return something

```java


interface Eater {
	public String eat(int i);
}

Eater e = (int i) -> { return "Eaten i==" + i; };
System.out.println(e.eat(11));


```

---

## Functional programming

- focus on what, not in who
- "I want to convert all elements in this array to String", instead of "loop through..."
- Lambda expression
	- block of code
	- you can store it in a variable
	- you can pass it around
	- methods without a name
	
---

## Lambda expressions

```java
Stream<Person> f = people.stream().filter((Person p) -> {return p.isHappy() == true;});
f.forEach(p -> System.out.println(p.getName()));
```



---

## Classic First class functions: map 

- Not in OCA, but useful

```java
List<String> names = Arrays.asList("Grouch", "Chicc", "Harp");

// forEach to print
names.stream().forEach(e -> System.out.println(e ));

names.stream().map((e) -> e + "o").forEach(e -> System.out.printf(e + "\n"));
names.stream().map((e) -> e.toUpperCase()).forEach(e -> System.out.printf(e + "\n"));

```


---

## Predicates

- functional interface `Predicate`
- has a `test method`
```java
boolean test(T t);
```

```java
Predicate<String> p = s -> s.startsWith("G");

System.out.println(p.test("Manolo")); 		// --> false
System.out.println(p.test("Groucho"));		// --> true
```

---

## Predicates can be composed!

```
Predicate<String> startsWithG = s -> s.startsWith("G");
Predicate<String> correctSize = s -> s.length() == 7;
Predicate<String> correctName = startsWithG.and(correctSize);

System.out.println(correctName.test("Manolo"));
System.out.println(correctName.test("Groucho"));	// --> true
```

---

## Predicates for filtering streams

```java
List<String> names = Arrays.asList("Grouch", "Chicc", "Harp");

Predicate<String> p = s -> s.startsWith("G");
names.stream().filter(p).forEach(System.out::println);

```

---

## Optionals

```java
Optional<String> s = names.stream().reduce((s1, s2) -> { return s1+s2; });
		
if (s.isPresent()) {
	System.out.println(s.get());
}

```


---


## Fun with functions

```java
Interface Function<T,R>

- T: the type of the input to the function
- R: the type of the result of the function

```

```java

// m1() takes a String and returns a String, hence the <String, String>

static Function<String, String> m1() {
	return new Function<String, String>() {
		@Override
		public String apply(String s) {
			return s.concat(" and two boiled eggs!");
		}
	};
}

```

---

## Fun with functions

```java
static Function<String, String> m2() {
	return new Function<String, String>() {
		@Override
		public String apply(String s) {
			return s.concat(" yeah!");
		}
	};
}

// ....

Function<String, String> f;
f = m1();
System.out.println(f.apply("Hola"));

f = m2();
System.out.println(f.apply("Hola"));


```


---


