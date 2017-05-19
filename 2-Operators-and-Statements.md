theme: Plain Jane
autoscale: true

# Operators and statements

---

## Numeric promotion

- int + long == long
- int+ float == float
- byte, short, char --> promote to int always

---

## Byte woes

```java
byte b1 = 1;
byte b2 = 1 + b1;	// error

---

byte b1 = 1;
byte b2 = (byte)(1 + b1);

```
---

## Byte woes

```java

byte b3 = b1++;				// OK	
b1 = b1 += 1;				// OK
b1 = b1 + 1;				// error
System.out.println(b1 + 1);	// OK  ¯\_(ツ)_/¯

```


---


## Assignment

= no es ==

```java
int i = 10;
long l = 10;
double d = 10.9;
float f = 10.0;
```


---

## Binary arithmetic operators

---


## Unary operators

- +, -, ++, --
- postfix & prefix ++

---

## instanceof no entra en el examen

---

## Logical operators

- |, &, !: int / boolean
- ||, &&: short-circuit operators

---

## Ternary operator ?

---

## if-then-else

- curly braces not mandatory

```java
int x = 0;
if (x == 10) {
	x = 11;
} else {
	x == 10;
}
// value of x?
```

---

## if-then-else

```java
int x = 0;
if (x == 10)
	x = 11;
	x--;
	else 
	x = 10;

```


---

## switch

```java
int x = 0;
switch (x) {
	case 10:
	case 7:
	case 4:
		break;
	default:
		
}

```

---

## switch

```java
String name = "spongebob";
switch (name) {
	case "spongebob":
	case "7":
	case "PatrickStar":
		break;
	default:

}

```
---


el resto: a leer