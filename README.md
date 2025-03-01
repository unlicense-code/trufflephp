[![Build Status](https://travis-ci.com/abertschi/graalphp.svg?branch=master)](https://travis-ci.com/abertschi/graalphp)
[![codebeat badge](https://codebeat.co/badges/2fc3ffd8-52b2-493b-a7fd-7f0faebe8c78)](https://codebeat.co/projects/github-com-abertschi-graalphp-master)
[![CodeFactor](https://www.codefactor.io/repository/github/abertschi/graalphp/badge)](https://www.codefactor.io/repository/github/abertschi/graalphp)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/0f1a558135e241aeb94b650db93ff714)](https://www.codacy.com/manual/abertschi/graalphp?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=abertschi/graalphp&amp;utm_campaign=Badge_Grade)

# A PHP implementation built on GraalVM
> Graalphp is an experimental just-in-time (JIT) compiler and runtime
for PHP 7.4+ hosted on GraalVM.

### Abstract
  PHP is a popular, weakly typed, general purpose programming
  language. Originally designed for building dynamic web pages, the
  language has since gained wide adoption in server-side web
  development.  In this work, we describe the design and
  implementation of graalphp, an experimental compiler and
  runtime for PHP hosted on Truffle and GraalVM. GraalVM is a virtual
  machine that supports execution of multiple languages, which are
  implemented as Abstract Syntax Tree (AST) interpreters based on
  Truffle. GraalVM uses Graal as its JIT compiler to compile
  frequently executed code fragments to machine code.  We implement a
  subset of the PHP language to run synthetic benchmarks by
  The Computer Language Benchmarks Game. We compare peak
  performance of our implementation against PHP 7 as well as
  alternative implementations such as HHVM, JPHP and an early alpha
  version of PHP 8. Experimental results indicate that our runtime
  reaches competitive results with performance gains of up to 859%
  compared to PHP 7. These preliminary results
  suggest that a Truffle-hosted PHP implementation might be
  significantly faster than existing language implementations.

<p align="center">
    <img src="./benchmarks/evaluation/assets/report/image_2020-09-06_12-36-43.png" alt="design" width="600"/>
</p>

- Benchmarks: [./results.md/](./results.md/)
- [Download Report](https://abertschi.ch/default_public/ethz/graalphp/download.php)  
- Presentation: https://www.youtube.com/watch?v=Dzahabn8ojo

This project was launched as an undergraduate thesis at ETHZ.

### Build and Run
For a container image with development and benchmark dependencies see
[./docker/](./docker/).

```shell
# Build Dependencies: Linux environment, maven, ant, GraalVM
# download GraalVM from https://github.com/graalvm/graalvm-ce-builds/releases
$ export JAVA_HOME=/path/to/graalvm
$ mvn package
$ ./graalphp <php-file.php>
```

```sh
# build native image:
$ export JAVA_HOME=/path/to/graalvm
$ $JAVA_HOME/bin/gu install native-image
$ export GRAALPHP_BUILD_NATIVE="true"
$ mvn package
```

### Feature Set
High Level Overview of implemented features, current runtime code
base. ca. 4000 LOC. Implemented features are chosen to support execution of the Computer Language Benchmark Game.
https://github.com/abertschi/graalphp/tree/master/benchmarks/evaluation
  
Non exhaustive list of features:
+ Datatypes: int, float, boolean, arrays (sequences) of these types
+ Unconditionally defined functions
+ Variables in function scope, global scope
+ Binary, unary, operations
+ while, do while, for, if


### More Resources
- Graal Github Issue for PHP support :: https://github.com/oracle/graal/issues/361
- GraalVM :: https://graalvm.org

## License
 - Apache License Version 2.0, January 2004 http://www.apache.org/licenses/
  - All existing code authored by People Mentioned in AUTHORS
 - Everything else The Unlicense. or if it is a Dependencie its License stays valid for it self.
