# 🪄 Formulas

#### IF(condition; expression\_if\_true; expression\_if\_false)

Takes three arguments, the first one must be a boolean and the second and third must return the same type.

In the `expression_if_true` and `expression_if_false` part, you can use **comparators** and **mathematical operations** such as: `+` ,`-` ,`/` ,`*` ,`>` ,`<` ,`=` ,`>=` ,`<=` ,`like`

Examples:

```
IF(column_a > column_b; "column_a is bigger than column_b"; "column_b is bigger than column_a")
IF(column_a + column_b <= 10; "Bigger than 10"; "less than 10")
IF(column_a like "%toto%"; "Toto detected"; "Toto is not here")
```

**Like operator**

The like operator is used to compare strings together and can be used to do "begins with", "ends with", "contains".

Begins with "toto": `column_a like "toto%"`

Ends with "toto": `column_a like "%toto"`

Contains "toto": `column_a like "%toto%"`

## URLs operators

#### UTM\_SOURCE(expression)

Takes an url as an input and return the utm source url parameter if exists or null.

```
UTM_SOURCE("https://whaly.io?utm_source=linkedin") => "linkedin"
```

#### UTM\_CAMPAIGN(expression)

Takes an url as an input and return the utm campaign url parameter if exists or null.

```
UTM_CAMPAIGN("https://whaly.io?utm_campaign=yc-announcement") => "yc-announcement"
```

#### UTM\_MEDIUM(expression)

Takes an url as an input and return the utm medium url parameter if exists or null.

```
UTM_MEDIUM("https://whaly.io?utm_medium=social") => "social"
```

#### UTM\_TERM(expression)

Takes an url as an input and return the utm term url parameter if exists or null.

```
UTM_TERM("https://whaly.io?utm_term=startup") => "startup"
```

#### UTM\_CONTENT(expression)

Takes an url as an input and return the utm content url parameter if exists or null.

```
UTM_CONTENT("https://whaly.io?utm_content=flavor_a") => "flavor_a"
```

#### DOMAIN(expression)

Takes an url as an input and return the domain of the url parameter if exists or null

```
DOMAIN("https://whaly.io?utm_content=flavor_a") => "whaly.io"
```

#### IS\_NULL(expression)

Takes a column as an input and returns a boolean. Return true if null or false if not null.

```
IS_NULL(null) => true
IS_NULL("ycombinator") => false
IS_NULL(0) => false
```

#### IS\_NOT\_NULL(expression)

Takes a column as an input and returns a boolean. Return true if not null or false if null.

```
IS_NOT_NULL(null) => false
IS_NOT_NULL("ycombinator") => true
IS_NOT_NULL(0) => true
```

**URL(url, label)**

Takes two column as an input and returns an html element that can be clicked on

```
URL("https://google.com", "click me !")
```

## Date operators

#### NOW

Return the current time.

```
NOW => "2022-09-02"
```

#### DATEVALUE(expression)

Takes a number representing the number of milliseconds since the 1st January 1970 as an input and returns the associated date.

```
DATEVALUE(1630598507000) => "2021-09-02"
```

#### **DATEDIF(date1; date2; resultDateType)**

Returns the duration between date1 and date2 (date1 - date2), in Day, Month or Week.

```
DATEDIF("2021-02-01"; "2021-01-01"; "MONTH") => 1
DATEDIF("2021-02-01"; "2021-01-01"; "DAY") => 30
```

**resultDateType** can be: `MILLISECOND`, `SECOND`, `MINUTE`, `HOUR`, `DAY`, `WEEK`, `MONTH`.

#### **PARSE\_GOOGLESHEET\_TIMESTAMP(timestampColumn)**

Convert a Google Sheet timestamp (number of days since the 31th december 1899) into a proper date.

```
PARSE_GOOGLESHEET_TIMESTAMP(1) => "1899-12-31"
```

#### **COHORT(expression, Type)**

Returns a cohort when inputed a date. Type can be: `DAY`, `WEEK` ,`MONTH` or `YEAR.`

```
COHORT("2018-12-19T12:00:00", "DAY") => "2018-12-19T00:00:00"
COHORT("2018-12-19T12:00:00", "WEEK") => "2018-12-17T00:00:00"
COHORT("2018-12-19T12:00:00", "MONTH") => "2018-12-01T00:00:00"
COHORT("2018-12-19T12:00:00", "YEAR") => "2018-01-01T00:00:00"
```

#### DATEADD(Date; Interval; Part)

Add period to a date. Part can be: `SECOND`, `MINUTE`, `HOUR`, `DAY`, `WEEK`, `MONTH`, `QUARTER`, `YEAR`

```
DATE_ADD("2018-12-19"; 1; "DAY") => "2018-12-20"
DATE_ADD("2018-12-19"; 1; "YEAR") => "2019-12-19"
```

#### DATETIME\_FORMAT(expression; format)

Format a date into string. Supported format are described below.

```
DATETIME_FORMAT("2018-12-19"; "%A, %B %e, %Y") => "Wednesday, December 19, 2018"
DATETIME_FORMAT("2018-12-19"; "%B") => "December"
```

#### **DATETIME\_PARSE(expression; format)**

Parse a string that match the format and turn it into a Date. Supported format are described below.

```
DATETIME_PARSE("Wednesday, December 19, 2018"; "%A, %B %e, %Y") => "2018-12-19"
```

## Text operators

#### CONCAT(...expressions)

Takes several columns separated by "`;`" and returns a concatenated string. Ex:

```
CONCAT("Hello"; " "; "World") => "Hello World"
```

#### LEFT(string; howMany)

Extract howMany characters from the beginning of the string.

```
LEFT("quick brown fox"; 5) => "quick"
```

#### RIGHT(string; howMany)

Extract howMany characters from the end of the string.

```
RIGHT("quick brown fox"; 3) => "fox"
```

#### MID(string; whereToStart; count)

Extract a substring of count characters starting at whereToStart.

```
MID("quick brown fox"; 7; 5) => "brown"
```

#### LENGTH(string)

Count the number of characters in the String.

```
LENGTH("whaly") => 5
```

#### SPLIT(columnToBeSplitted; splitSeparator; indexToGet)

Split a column content according to a separator and then return the value at the given index in the splitted array.

```
SPLIT("CatA > CatB > CatC"; ">"; 1) => "CatB"
```

## **Logical operators**

#### **AND(expressionA; expressionB)**

Return true if expressionA _**and**_ expressionB are true.

```
AND(true, true) => true
AND(true, false) => false
AND(false, false) => false
```

#### **OR(expressionA; expressionB)**

Return true if expressionA _**or**_ expressionB are true.

```
OR(true, true) => true
OR(true, false) => true
OR(false, false) => false
```

## Number operators

#### **ROUND(expression; precision)**

Round a number with a precision.

```
ROUND(3.14; 0) => 3
ROUND(3.14; 1) => 3.1
ROUND(4.65; 1) => 4.7
```

#### FLOOR(expression)

Floor a number, get rid of the decimals.

```
FLOOR(3.14) => 3
FLOOR(3.1) => 3
FLOOR(3) => 3
```

#### VALUE(expression)

Convert a text into an integer number.

```
VALUE("3") => 3
VALUE("3.2") => 3
VALUE("Invalid") => null
```

## DATETIME formula format

Unless otherwise noted, `DATETIME` functions that use format strings support the following elements:

| Format element | Description                                                                                                                                                                                                                                                                                                                                 | Example                  |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------ |
| %A             | The full weekday name.                                                                                                                                                                                                                                                                                                                      | Wednesday                |
| %a             | The abbreviated weekday name.                                                                                                                                                                                                                                                                                                               | Wed                      |
| %B             | The full month name.                                                                                                                                                                                                                                                                                                                        | January                  |
| %b or %h       | The abbreviated month name.                                                                                                                                                                                                                                                                                                                 | Jan                      |
| %C             | The century (a year divided by 100 and truncated to an integer) as a decimal number (00-99).                                                                                                                                                                                                                                                | 20                       |
| %c             | The date and time representation.                                                                                                                                                                                                                                                                                                           | Wed Jan 20 21:47:00 2021 |
| %D             | The date in the format %m/%d/%y.                                                                                                                                                                                                                                                                                                            | 01/20/21                 |
| %d             | The day of the month as a decimal number (01-31).                                                                                                                                                                                                                                                                                           | 20                       |
| %e             | The day of month as a decimal number (1-31); single digits are preceded by a space.                                                                                                                                                                                                                                                         | 20                       |
| %F             | The date in the format %Y-%m-%d.                                                                                                                                                                                                                                                                                                            | 2021-01-20               |
| %G             | The [ISO 8601](https://en.wikipedia.org/wiki/ISO\_8601) year with century as a decimal number. Each ISO year begins on the Monday before the first Thursday of the Gregorian calendar year. Note that %G and %Y may produce different results near Gregorian year boundaries, where the Gregorian year and ISO year can diverge.            | 2021                     |
| %g             | The [ISO 8601](https://en.wikipedia.org/wiki/ISO\_8601) year without century as a decimal number (00-99). Each ISO year begins on the Monday before the first Thursday of the Gregorian calendar year. Note that %g and %y may produce different results near Gregorian year boundaries, where the Gregorian year and ISO year can diverge. | 21                       |
| %H             | The hour (24-hour clock) as a decimal number (00-23).                                                                                                                                                                                                                                                                                       | 21                       |
| %I             | The hour (12-hour clock) as a decimal number (01-12).                                                                                                                                                                                                                                                                                       | 09                       |
| %j             | The day of the year as a decimal number (001-366).                                                                                                                                                                                                                                                                                          | 020                      |
| %k             | The hour (24-hour clock) as a decimal number (0-23); single digits are preceded by a space.                                                                                                                                                                                                                                                 | 21                       |
| %l             | The hour (12-hour clock) as a decimal number (1-12); single digits are preceded by a space.                                                                                                                                                                                                                                                 | 9                        |
| %M             | The minute as a decimal number (00-59).                                                                                                                                                                                                                                                                                                     |                          |
| %m             | The month as a decimal number (01-12).                                                                                                                                                                                                                                                                                                      | 01                       |
| %n             | A newline character.                                                                                                                                                                                                                                                                                                                        |                          |
| %P             | Either am or pm.                                                                                                                                                                                                                                                                                                                            | pm                       |
| %p             | Either AM or PM.                                                                                                                                                                                                                                                                                                                            | PM                       |
| %Q             | The quarter as a decimal number (1-4).                                                                                                                                                                                                                                                                                                      | 1                        |
| %R             | The time in the format %H:%M.                                                                                                                                                                                                                                                                                                               | 21:47                    |
| %r             | The 12-hour clock time using AM/PM notation.                                                                                                                                                                                                                                                                                                | 09:47:00 PM              |
| %S             | The second as a decimal number (00-60).                                                                                                                                                                                                                                                                                                     | 00                       |
| %s             | The number of seconds since 1970-01-01 00:00:00. Always overrides all other format elements, independent of where %s appears in the string. If multiple %s elements appear, then the last one takes precedence.                                                                                                                             | 1611179220               |
| %T             | The time in the format %H:%M:%S.                                                                                                                                                                                                                                                                                                            | 21:47:00                 |
| %t             | A tab character.                                                                                                                                                                                                                                                                                                                            |                          |
| %U             | The week number of the year (Sunday as the first day of the week) as a decimal number (00-53).                                                                                                                                                                                                                                              | 03                       |
| %u             | The weekday (Monday as the first day of the week) as a decimal number (1-7).                                                                                                                                                                                                                                                                | 3                        |
| %V             | The [ISO 8601](https://en.wikipedia.org/wiki/ISO\_week\_date) week number of the year (Monday as the first day of the week) as a decimal number (01-53). If the week containing January 1 has four or more days in the new year, then it is week 1; otherwise it is week 53 of the previous year, and the next week is week 1.              | 03                       |
| %W             | The week number of the year (Monday as the first day of the week) as a decimal number (00-53).                                                                                                                                                                                                                                              | 03                       |
| %w             | The weekday (Sunday as the first day of the week) as a decimal number (0-6).                                                                                                                                                                                                                                                                | 3                        |
| %X             | The time representation in HH:MM:SS format.                                                                                                                                                                                                                                                                                                 | 21:47:00                 |
| %x             | The date representation in MM/DD/YY format.                                                                                                                                                                                                                                                                                                 | 01/20/21                 |
| %Y             | The year with century as a decimal number.                                                                                                                                                                                                                                                                                                  | 2021                     |
| %y             | The year without century as a decimal number (00-99), with an optional leading zero. Can be mixed with %C. If %C is not specified, years 00-68 are 2000s, while years 69-99 are 1900s.                                                                                                                                                      | 21                       |
| %%             | A single % character.                                                                                                                                                                                                                                                                                                                       | %                        |
| %E\<number>S   | Seconds with \<number> digits of fractional precision.                                                                                                                                                                                                                                                                                      | 00.000 for %E3S          |
| %E\*S          | Seconds with full fractional precision (a literal '\*').                                                                                                                                                                                                                                                                                    | 00.123456                |
| %E4Y           | Four-character years (0001 ... 9999). Note that %Y produces as many characters as it takes to fully render the year.                                                                                                                                                                                                                        | 2021                     |
