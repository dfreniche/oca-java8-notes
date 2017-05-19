theme: Plain Jane
autoscale: true

# Dates and Times in Java 8

---

## Current Date


```java

LocalDate now = LocalDate.now();
System.out.println(now);

// 2015-11-08

```

- LocalDate: only date (not time)
- can't do `new LocalDate();`
- `import java.time.LocalDate;`


---

## Date with year, month, day

```java

LocalDate firstOfJanuary2015 = LocalDate.of(2015, Month.JANUARY, 1);
System.out.println(firstOfJanuary2015);
```

---

## LocalDate inmutable!

```java
LocalDate _12Oct1492_ = LocalDate.of(1492, Month.OCTOBER, 12);
_12Oct1492_.plusDays(800);
System.out.println(_12Oct1492_);								// 1492-10-12
LocalDate other = _12Oct1492_.plusDays(800);
System.out.println(other);										// 1494-12-21
```

---

## LocalTime

```java
LocalTime timeNow = LocalTime.now();
System.out.println(timeNow);									// 13:51:53.382
```

- LocalTime: sólo tiempo
- `LocalDateTime`: fecha y hora

---


## LocalTime inmutable!

```java
LocalTime timeNow = LocalTime.now();
System.out.println(timeNow);

timeNow.plusHours(1);
System.out.println(timeNow);

// 19:57:24.995
// 19:57:24.995

```

- plusMinutes / minusMinutes
- plusSeconds / minus

---

## Recorrer intervalos

```java
LocalDate start = LocalDate.of(2015, Month.APRIL, 10);
LocalDate end = LocalDate.of(2015, Month.APRIL, 20);
while (start.isBefore(end)) {
	System.out.println(start);
	start = start.plusDays(1);
}

2015-04-10
2015-04-11
2015-04-12
2015-04-13
2015-04-14
2015-04-15
2015-04-16
2015-04-17
2015-04-18
2015-04-19

```

---

## TimeZones [^1]

```java
System.out.println(LocalTime.now());
System.out.println(LocalTime.now(ZoneId.of("US/Pacific")));
System.out.println(LocalTime.now(ZoneId.of("Zulu")));

// console output

20:05:25.170
11:05:25.172
19:05:25.173

```


[^1]: no entra en el examen
https://garygregory.wordpress.com/2013/06/18/what-are-the-java-timezone-ids/

---


## Period

```java
// Create task every week

Period everyWeek = Period.ofWeeks(1);
start = LocalDate.now();
end = LocalDate.of(2016, Month.APRIL, 10);
while (start.isBefore(end)) {
	System.out.println(start);
	start = start.plus(everyWeek);
}

``` 
---

## Parse dates

```java

DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy/MM/dd");
LocalDate date = LocalDate.parse("2010/10/40", formatter);
System.out.println(date);

```
- can throw `java.time.format.DateTimeParseException` (Runtime)
