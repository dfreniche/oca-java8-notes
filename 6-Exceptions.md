theme: Plain Jane
autoscale: true

# Exceptions

---

## An "Exceptional" 😩 family 

```
Object
|
class Throwable
|
|-- class Error
|-- class Exception
	|
	|- class RuntimeException
```	


---

## Types of exceptions

- all Exceptions are __created & injected__ by the Runtime
- __checked__ == "Compile-time" exceptions
    - handle-or-declare rule
- __non-checked__ == runtime exceptions


---

## Should I "catch" Errors? 🤔

- never, ever
- never
- really
- don't do it
- ever
- I'm serious
- don't

--- 
## Try-catch-finally

```java

try {
	// do something that can throw
} catch (Exception e) { 
    // do something if this exception is injected
} finally {
    // do this always
}

```
---

## Try-catch gotchas

### Error! Needs a block
```java
try
	int i = 0;
catch (Exception e) ;
```

### This is fine

```java

try {
	int i = 0;
} catch (Exception e) { }
```

---
## Try-catch gotchas

Just __one__ try, please

```java

try {
		
} try {
		
} catch (Exception e) {}
```


---

## Try-catch gotchas

```java
// we can have a try-catch with Throwable
try {
	int i = 0;
} catch (Throwable t) {
    //  Pokémon catch: Gotta catch'em all!
}

try {
	int i = 0;
} catch (Exception t) {
	// i++;               Error: i - local to try block
}

```

---

## Try-catch gotchas


```java 
// can have more than one catch
try {
	int i = 0;
} catch (Exception e) {

} catch (Throwable t) {

}

try {
	int i = 0;
} catch (Throwable t) {

} catch (Exception e) { // error: Exception has already been caught

}
```

---

## Creating your own exceptions


```java

// Runtime, non-checked Exception 
class NonCheckedException extends RuntimeException {

}

// Compile-time, checked exception, handle or declare rule
class CheckedException extends Exception {

}
```

---

## Catch-Or-Declare rule (Checked exceptions)

```java 
public class Main {
    public static void main(String[] args) {
        throwsNonChecked(); // no problem with non-checked
        try {
            throwsChecked();
        } catch (CheckedException e) {
            e.printStackTrace();
        }
    }

    static void throwsNonChecked() {
        throw new NonCheckedException();
    }

    static void throwsChecked() throws CheckedException {
        throw new CheckedException();
    }
}

```

--- 

## What does this prints? 😈

```java 
import java.io.IOException;

public class Main {
    public static void main(String[] args) {
        try {
            System.out.println("DogeBegin");
            new Main().saveToDisk();
        } catch (IOException e) {
            System.out.println(e.getMessage());
        } finally {
            System.out.println("DogeFinally");
        }
    }

    void saveToDisk() throws IOException{
        throw new IOException("Such litte space. Much files. Wow");
    }
}
```

---

## What does this prints?

```
DogeBegin
Such litte space. Much files. Wow
DogeFinally	
```

---
## What does this prints? 😈

```java 
import java.io.IOException;

public class Main {
    public static void main(String[] args) {
        try {
            System.out.println("DogeBegin");
            new Main().saveToDisk();
        } catch (IOException e) {
            System.out.println("IODoge" + e.getMessage());
        } catch (Exception e) {
            System.out.println("ExceptionDoge"+ e.getMessage());
        } finally {
            System.out.println("DogeFinally");
        }
    }

    void saveToDisk() throws IOException{
        throw new IOException("Such litte space. Much files. Wow");
    }
}
```

---

## What does this prints?

```
DogeBegin
IODogeSuch litte space. Much files. Wow
DogeFinally

```


---


## What does this prints? 😈

```java
import java.io.IOException;

public class Main {
    public static void main(String[] args) {
        new Main().run();
    }

    void run() {
        try {
            System.out.println("DogeBegin");
            saveToDisk();
        } catch (IOException e) {
            System.out.println("IODoge" + e.getMessage());
            return;
        } finally {
            System.out.println("DogeFinally");
        }
        System.out.println("DogeReturn");
    }

    void saveToDisk() throws IOException{
        throw new IOException("Such litte space. Much files. Wow");
    }
}
```
---

## What does this prints?

```

DogeBegin
IODogeSuch litte space. Much files. Wow
DogeFinally
```

---
## What does this prints? 😈

```java
import java.io.IOException;

public class Main {
    public static void main(String[] args) {
        new Main().run();
    }

    void run() {
        try {
            System.out.println("DogeBegin");
            saveToDisk();
        } catch (IOException e) {
            System.out.println("IODoge" + e.getMessage());
            return;
        } finally {
            System.out.println("DogeFinally");
        }
        System.out.println("DogeReturn");
    }

    void saveToDisk() throws IOException{
        throw new RuntimeException("Such litte space. Much files. Wow");
    }
}

```

---

```
Exception in thread "main" java.lang.RuntimeException: Such litte space. Much files. Wow
DogeBegin
	at Main.saveToDisk(Main.java:22)
DogeFinally
	at Main.run(Main.java:11)
	at Main.main(Main.java:5)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:497)
	at com.intellij.rt.execution.application.AppMain.main(AppMain.java:134)
```

