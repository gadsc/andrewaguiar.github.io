---
layout: post
title: "Java - How to format and parse dates"
---

Hi guys here comes a very quick and usefull guide of how to parse and format Dates in Java, I hope it helps.

## Using the java.text.DateFormat

### Formatting - from date to string

The simplest way to format a Date in java is to use the ``java.text.DateFormat``, it is an abstract class so we have to use an implementation of it. You can call DateFormat.getInstance methods to get a concrete class and start working.

```java
DateFormat df = DateFormat.getInstance();
System.out.println(df.format(new Date()));
// 10/16/15 3:15 PM
```

```java
DateFormat df = DateFormat.getTimeInstance();
System.out.println(df.format(new Date()));
// 3:15:03 PM
```

```java
DateFormat df = DateFormat.getDateInstance();
System.out.println(df.format(new Date()));
// Oct 16, 2015
```

```java
DateFormat df = DateFormat.getDateTimeInstance();
System.out.println(df.format(new Date()));
// Oct 16, 2015 3:15:03 PM
```

It works but it is not so usefull, most part of time we want to format a Date using some custom pattern like day month year. We can use ``java.text.SimpleDateFormat`` to customize our date pattern:

```java
DateFormat df = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss.SSS");
System.out.println(df.format(date));
//16/10/2015 15:03:17.396
```

We can also show week days and month names just changing the pattern:

```java
DateFormat df = new SimpleDateFormat("EEEE dd MMMM yyyy");
System.out.println(df.format(date));
System.out.println(Locale.getDefault());
// Friday 16 October 2015
// en_US
```

And finally we can change the default locale in order to change the month and week day name, ``java.util.Locale`` represents the Locale which will be considered. 

```java
Locale.setDefault(Locale.FRENCH);
```

Now we can show in French

```java
DateFormat df = new SimpleDateFormat("EEEE dd MMMM yyyy");
System.out.println(df.format(date));
System.out.println(Locale.getDefault());
// vendredi 16 octobre 2015
// fr
```

### Parsing - from string to date

To parse a Date to String we use the same Class DateFormat but now calling the ``parse`` method, if the String does not match with the pattern a ``java.text.ParseException`` will be thrown.

```java
DateFormat df = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss.SSS");
Date date = df.parse("16/10/2015 15:25:07.861");
```

```java
DateFormat df = new SimpleDateFormat("EEEE dd MMMM yyyy");
Date date = df.parse("Friday 16 October 2015");
```

Same thing using Locales

```java
Locale.setDefault(Locale.FRENCH);

DateFormat df = new SimpleDateFormat("EEEE dd MMMM yyyy");
Date date = df.parse("jeudi 15 octobre 2015");
```

### References
  - Java 7 SimpleDateFormat and patterns: [http://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html](http://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html).
  - Java 7 DateFormat: [http://docs.oracle.com/javase/7/docs/api/java/text/DateFormat.html](http://docs.oracle.com/javase/7/docs/api/java/text/DateFormat.html).
  - Java 7 Locale: [http://docs.oracle.com/javase/7/docs/api/java/util/Locale.html](http://docs.oracle.com/javase/7/docs/api/java/util/Locale.html).
