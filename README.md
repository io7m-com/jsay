jsay
===

[![Maven Central](https://img.shields.io/maven-central/v/com.io7m.jsay/com.io7m.jsay.svg?style=flat-square)](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22com.io7m.jsay%22)
[![Maven Central (snapshot)](https://img.shields.io/nexus/s/com.io7m.jsay/com.io7m.jsay?server=https%3A%2F%2Fs01.oss.sonatype.org&style=flat-square)](https://s01.oss.sonatype.org/content/repositories/snapshots/com/io7m/jsay/)
[![Codecov](https://img.shields.io/codecov/c/github/io7m-com/jsay.svg?style=flat-square)](https://codecov.io/gh/io7m-com/jsay)
![Java Version](https://img.shields.io/badge/21-java?label=java&color=e6c35c)

![com.io7m.jsay](./src/site/resources/jsay.jpg?raw=true)

| JVM | Platform | Status |
|-----|----------|--------|
| OpenJDK (Temurin) Current | Linux | [![Build (OpenJDK (Temurin) Current, Linux)](https://img.shields.io/github/actions/workflow/status/io7m-com/jsay/main.linux.temurin.current.yml)](https://www.github.com/io7m-com/jsay/actions?query=workflow%3Amain.linux.temurin.current)|
| OpenJDK (Temurin) LTS | Linux | [![Build (OpenJDK (Temurin) LTS, Linux)](https://img.shields.io/github/actions/workflow/status/io7m-com/jsay/main.linux.temurin.lts.yml)](https://www.github.com/io7m-com/jsay/actions?query=workflow%3Amain.linux.temurin.lts)|
| OpenJDK (Temurin) Current | Windows | [![Build (OpenJDK (Temurin) Current, Windows)](https://img.shields.io/github/actions/workflow/status/io7m-com/jsay/main.windows.temurin.current.yml)](https://www.github.com/io7m-com/jsay/actions?query=workflow%3Amain.windows.temurin.current)|
| OpenJDK (Temurin) LTS | Windows | [![Build (OpenJDK (Temurin) LTS, Windows)](https://img.shields.io/github/actions/workflow/status/io7m-com/jsay/main.windows.temurin.lts.yml)](https://www.github.com/io7m-com/jsay/actions?query=workflow%3Amain.windows.temurin.lts)|

## jsay

The `jsay` package provides a tiny command-line
[JMS](https://en.wikipedia.org/wiki/Java_Message_Service) sender.

## Features

* Tiny command-line JMS message sender.
* ISC license.

## Usage

The `jsay` command-line tool connects to a _message broker_, sends a single
text message, and then disconnects and exits.

```
INFO [main] com.io7m.jsay.Main: Usage: jsay [options]
  Options:
  * --address
      The message address
  * --broker-uri
      The message broker URI
    --expires
      The message expiry time
    --file
      The message file (if not specified, data is read from stdin)
      Default: /dev/stdin
    --password
      The message broker password
    --topic
      The destination is a topic, not a queue.
      Default: false
    --user
      The message broker user
    --verbose
      The level of logging verbosity
      Default: INFO
      Possible Values: [TRACE, DEBUG, INFO, WARN, ERROR]
```

The following invocation sends a `Hello world!` message to the JMS destination
named `announcements` on the given broker:

```
$ echo 'Hello world!' | java -jar jsay.jar \
  --address announcements \
  --broker-uri tcp://messaging.example.com:54663 \
  --expires 2024-01-01T00:00:00+00:00
```

