---
layout: page
title: "Reporting"
category: ref
date: 2015-01-18 13:09:22
---

## Logging
The reporter in JMoribus uses slf4j and its Mapped Diagnostic Context.
So when you use the slf4j Logger you can format the output with extra information like so:

```
%d{yyyy-MM-dd HH:mm:ss} %-5p[%X{story}][%X{scenario}][%X{step}] %c{1}:%L - %m%n
```