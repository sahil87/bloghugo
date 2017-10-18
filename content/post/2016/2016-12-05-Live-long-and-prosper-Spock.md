---
title: Live long and prosper - Spock
author: Sahil Ahuja
categories: coding
tags: [java, testing, spock]
date: 2016-12-05 18:05:28
---
[Spock](http://spockframework.org/) is the new kid in town in the [crowded](https://en.wikipedia.org/wiki/Unit_testing) world of testing frameworks.

[Here](https://accu.org/index.php/journals/2203) is an article on Spock where the author tries to vent out years in frustration over JUnit in a very professionally demeanor.

_What he was really trying to say is:_
<!-- more -->
1. The way JUnits are written is laborious
1. With Spock you can do this: 
```Groovy
class Test_Factorial_Spock_Parameterized_Groovy extends Specification {
  @Unroll
  def 'iterative(#i) succeeds'() {
    expect:
    iterative(i) == r
    where:
    i | r
    0 | 1G
    1 | 1G
    7 | 5040G
    12 | 479001600G
    20 | 2432902008176640000G
    40 | 815915283247897734345611269596115894272000000000
  }
  @Unroll
  def 'iterative(#i) throws exception'() {
    when:
    iterative(i)
    then:
    thrown(IllegalArgumentException)
    where:
    i << [-1, -2, -5, -10, -20, -100]
  }
}
```
![Spock](/images/mr-spock.jpg)
And I was sold.

> The needs of the many outweigh the needs of the few ― Spock, Star Trek II: The Wrath of Khan

Good Spock Resourses:
http://jakubdziworski.github.io/java/groovy/spock/2016/05/14/spock-cheatsheet.html
http://codepipes.com/presentations/spock-vs-junit.pdf
https://github.com/spockframework/spock
