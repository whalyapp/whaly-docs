# Using custom formatting

## Formatting numbers

Custom number format relies on [numeral.js](http://numeraljs.com/#format) in order to provide you with the ability to easily customise your metrics formatting.

The following table should be read this way:

* Number is an example number
* Format is the format you should type in the custom format input on Whaly
* Output show how your metric will display using the custom format

**Numbers formats**

| Number     | Format     | Output        |
| ---------- | ---------- | ------------- |
| 10000      | 0,0.0000   | 10,000.0000   |
| 10000.23   | 0,0        | 10,000        |
| 10000.23   | +0,0       | +10,000       |
| -10000     | 0,0.0      | -10,000.0     |
| 10000.1234 | 0.000      | 10000.123     |
| 100.1234   | 00000      | 00100         |
| 1000.1234  | 000000,0   | 001,000       |
| 10         | 000.00     | 010.00        |
| 10000.1234 | 0\[.]00000 | 10000.12340   |
| -10000     | (0,0.0000) | (10,000.0000) |
| -0.23      | .00        | -.23          |
| -0.23      | (.00)      | (.23)         |
| 0.23       | 0.00000    | 0.23000       |
| 0.23       | 0.0\[0000] | 0.23          |
| 1230974    | 0.0a       | 1.2m          |
| 1460       | 0 a        | 1 k           |
| -104000    | 0a         | -104k         |
| 1          | 0o         | 1st           |
| 100        | 0o         | 100th         |

**Currency formats**

| Number    | Format      | Output     |
| --------- | ----------- | ---------- |
| 1000.234  | $0,0.00     | $1,000.23  |
| 1000.2    | 0,0\[.]00 $ | 1,000.20 $ |
| 1001      | $ 0,0\[.]00 | $ 1,001    |
| -1000.234 | ($0,0)      | ($1,000)   |
| -1000.234 | $0.00       | -$1000.23  |
| 1230974   | ($ 0.00 a)  | $ 1.23 m   |

**Bytes formats**

| Number        | Format   | Output    |
| ------------- | -------- | --------- |
| 100           | 0b       | 100B      |
| 1024          | 0b       | 1KB       |
| 2048          | 0 ib     | 2 KiB     |
| 3072          | 0.0 b    | 3.1 KB    |
| 7884486213    | 0.00b    | 7.88GB    |
| 3467479682787 | 0.000 ib | 3.154 TiB |

**Percentages formats**

| Number      | Format    | Output   |
| ----------- | --------- | -------- |
| 1           | 0%        | 100%     |
| 0.974878234 | 0.000%    | 97.488%  |
| -0.43       | 0 %       | -43 %    |
| 0.43        | (0.000 %) | 43.000 % |

**Time formats**

| Number | Format   | Output   |
| ------ | -------- | -------- |
| 25     | 00:00:00 | 0:00:25  |
| 238    | 00:00:00 | 0:03:58  |
| 63846  | 00:00:00 | 17:44:06 |

**Exponential formats**

| Number       | Format   | Output   |
| ------------ | -------- | -------- |
| 1123456789   | 0,0e+0   | 1e+9     |
| 12398734.202 | 0.00e+0  | 1.24e+7  |
| 0.000123987  | 0.000e+0 | 1.240e-4 |

## Formatting durations

Custom duration format relies on [moment duration format](https://github.com/jsmreese/moment-duration-format) in order to provide you with the ability to easily customise your metrics formatting.

To format a duration you can use the following tokens :&#x20;

```
years:   Y or y
months:  M
weeks:   W or w
days:    D or d
hours:   H or h
minutes: m
seconds: s
ms:      S
```

Escape token characters within the template string using square brackets :&#x20;

For some time duration formats, a zero-padded value is required. Use multiple token characters together to create the correct amount of padding.

### Examples&#x20;

| Input (in seconds) | format               | output         |
| ------------------ | -------------------- | -------------- |
| 61                 | mm:ss                | 01:01          |
| 61                 | m \[min], s \[sec]   | 1 min, 1 sec   |
| 61                 | mm \[min], ss \[sec] | 01 min, 01 sec |
