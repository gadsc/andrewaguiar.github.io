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
df.parse("Friday 16 October 2015");
```

Same thing using Locales

```java
Locale.setDefault(Locale.FRENCH);

DateFormat df = new SimpleDateFormat("EEEE dd MMMM yyyy");
Date parse = df.parse("jeudi 15 octobre 2015");
```

Some pattern examples:
| Letter|Date or Time Component|Presentation|Examples |
|--|--------------|----|---|
| G|Era designator|Text|AD |
| y|Year|Year|1996; 96 |
| Y|Week year|Year|2009; 09 |
| M|Month in year|Month|July; Jul; 07 |
| w|Week in year|Number|27 |
| W|Week in month|Number|2 |
| D|Day in year|Number|189 |
| d|Day in month|Number|10 |
| F|Day of week in month|Number|2 |
| E|Day name in week|Text|Tuesday; Tue |
| u|Day number of week (1 = Monday, ..., 7 = Sunday)|Number|1 |
| a|Am/pm marker|Text|PM |
| H|Hour in day (0-23)|Number|0 |
| k|Hour in day (1-24)|Number|24 |
| K|Hour in am/pm (0-11)|Number|0 |
| h|Hour in am/pm (1-12)|Number|12 |
| m|Minute in hour|Number|30 |
| s|Second in minute|Number|55 |
| S|Millisecond|Number|978 |
| z|Time zone|General time zone|Pacific Standard Time; PST; GMT-08:00 |
| Z|Time zone|RFC 822 time zone|-0800 |
| X|Time zone|ISO 8601 time zone|-08; -0800; -08:00 |


