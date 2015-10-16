---
layout: post
title: "Java - How to format and parse dates"
---

Hi guys here comes a very quick and usefull guide of how to parse and format Dates in Java, I hope it helps.

## Using the java.text.DateFormat

The simplest way to format a Date in java is to use the ``java.text.DateFormat``, it is an abstract class so we have to use an implementation of it. You can call DateFormat.getInstance methods to get a concrete class and start working.

```java
DateFormat dateFormatInstance = DateFormat.getInstance();
System.out.println(dateFormatInstance.format(new Date()));
// 10/16/15 3:15 PM

DateFormat dateFormatTimeInstance = DateFormat.getTimeInstance();
System.out.println(dateFormatTimeInstance.format(new Date()));
// 3:15:03 PM

DateFormat dateFormatDateInstance = DateFormat.getDateInstance();
System.out.println(dateFormatDateInstance.format(new Date()));
// Oct 16, 2015

DateFormat dateFormatDateAndTimeInstance = DateFormat.getDateTimeInstance();
System.out.println(dateFormatDateAndTimeInstance.format(new Date()));
// Oct 16, 2015 3:15:03 PM
```

It works but it is not so usefull, most part of time we want to format a Date using some custom pattern like day month year. We can use ``java.text.SimpleDateFormat`` to customize our date pattern:

```java
DateFormat simpleDateFormat = new SimpleDateFormat("dd/MM/yyyy HH:mm:ss.SSS");
System.out.println(simpleDateFormat.format(date));
//16/10/2015 15:03:17.396
```

We can also show week days and month names just changing the pattern:

```java
DateFormat simpleDateFormatEN = new SimpleDateFormat("EEEE dd MMMM yyyy");
System.out.println(simpleDateFormatEN.format(date));
System.out.println(Locale.getDefault());
// Friday 16 October 2015
// en_US
```

And finally we can change the default locale in order to change the month and week day name, ``java.util.Locale`` represents the Locale which will be considered. 

```java
Locale.setDefault(Locale.FRANCE);
```

Now we can show in French

```java
DateFormat simpleDateFormatEN = new SimpleDateFormat("EEEE dd MMMM yyyy");
System.out.println(simpleDateFormatEN.format(date));
System.out.println(Locale.getDefault());
// vendredi 16 octobre 2015
// fr
```
