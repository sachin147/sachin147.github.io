---
layout: post
title:  "Quick Guide To Spock"
date:   2016-10-23 18:00:00 +0530
---

Hi folks, this is my post to get you ready with using Spock testing and specification framework as quickly as possible.

Spock is a great unit testing framework. You can find loads of appreciation for it, & mind you it is indeed worth appreciating.

There are certain prerequisites before using this beautiful framework.
<ul>
  <li>What is unit testing and purpose it serves</li>
  <li>A little bit of Groovy (it is happier Java, as simple), enough to get started with Spock testing</li>
  <li>Know what are Stubs and Mocks, trust me this one is surely needed</li>
</ul>

One must understand 'what is unit testing ?, why unit testing ?' and its importance in software development, before actually starting to write unit test, be it using any framework.


<b>Lets get started with Spock</b>

Spock was brought to life by Peter Niederwieser( an angel definitely ) as suggested by Wiki.

Spock is what a programming language should look like. It is simple, readable and most importantly understandable to any human.
It brings writing business like description to tests.
It helps to write specifications for 'class under test'.

Lets start with a very simple test with Spock

{% highlight groovy %}
class CalculatorSpec extends spock.lang.Specification {
    def "add must sum two numbers "() {
        when :"a new calculator is created"
            def calculator = new Calculator()
        then :"1 plus 1 is 2"
            calculator.add(1,1) == 2
    }
}
{% endhighlight %}
As you can from above spec where Calculator is the class under test, Spock has a very simple structure and speech wherein even a layman can understand what is being proposed.<br/>
The <i>'def'</i>part is what we are asserting. Here we are asserting ( literal meaning of assert is : to state a fact confidently) that the method 'add' should sum given two numbers.


In a standard Maven directory structure, Groovy source code is usually placed in the <i>src/test/groovy</i> folder so that the Groovy compiler plugin can find it. Spock tests can go into this directory without affecting your existing JUnit tests located in src/test/java.<br>

<u><i>The given,when,then flow</i></u>
{% highlight groovy %}
class CalculatorSpec extends spock.lang.Specification {
    def "add must sum two numbers "() {
        given :"a calculator"
            def calculator = new Calculator()
        when :"when 1 is added to 1"
            def sum = calculator.add(1,1)
        then :"sum is 2"
             sum == 2
    }
}
{% endhighlight %}
Here you can see,
in the <i>given</i> block(usually called as setup block), where a setup is done for the spec.<br>
<i>when</i> block is where a method under test is called
<i>then</i> block is where results are checked for truth.
<br/><br/>
<u><i>Blocks in a Spock test method</i></u>
<ul>
    <li>
        <u><i>given/setup</i></u>
        The given/setup(alias for given) block is where all the initialization (preparation) code for unit test resides.
    </li>
    <li>
        <u><i>when</i></u>
        The when block is where the call to our 'method under test' needs to be put. It should be small, and can be as simple as a single line. It is from where the call is triggered to our 'method under test' and its collaborators(stubs i mean to say).
    </li>
    <li>
        <u><i>then</i></u>
        The then block contains assertions ( can be multiple) to test for correctness of our method under test
    </li>
    <li>
        <u><i>and</i></u>
        It is basically to help writes tests in a distinct manner. It makes tests look eye pleasing and brings more natural speech to our tests .
    </li>
    <li>
        <u><i>cleanup</i></u>
        As the name suggests it does the cleanup part. It is similar to 'finally' in the exception handling blocks.
    </li>
</ul>
{% highlight groovy %}
class ListSpec extends spock.lang.Specification {
    def "add items to list "() {
        given :"a list"
            List list = new ArrayList<>()
        when :"when 1 is added to list"
            list.add(1)
        and :"when 2 is added to list" 
            list.add(2)
        then :"size of list is"
            list.size() == 2
        cleanup :"clear list"
            list.clear() 
    }
}
{% endhighlight %}
<br/>    
There are many annotations provided in Spock to make specs look more descriptive, but I won't be covering them as they are not really much needed now.
<br/><br/>

<u><i>@Shared</i></u>
This is used to indicate object which we want to 'live' across all tests.
{% highlight groovy %}
class CalculatorSpec extends spock.lang.Specification {
    
    @Shared
    Calculator calculator
    
    def "add numbers "() {        
        setup "give a calculator":
        calculator = new Calculator()
        ...
    }
}
{% endhighlight %}
<br/><br/>


<u><i>setup() and cleanup()</i></u>
setup() run before each test method. cleanup() run after each test method. They run as many times as test methods exist.

<u><i>setupSpec() and cleanupSpec()</i></u>
setupSpec() run once before all test methods. cleanupSpec() run once after all test methods. They work only with objects that are either static or marked with the @Shared annotation.


<u><i>Parameterized Tests</i></u>
Parameterized tests basically stops a developer from repeating their tests.
It is very easy to perform with the help of data tables. It basically helps to input for various permutations.


{% highlight groovy %}
class CalculatorSpec extends spock.lang.Specification {
    def "add must sum two numbers "() {
        when :
            sum = Calculator.add(number1, number2)
        then :
            assert sum
        where:
            number1 | number2   || sum
            1       | 3         || 4
            7       | 4         || 11
            0       | 0         || 0
    }
}
{% endhighlight %}

<br/><br/>

<u><i>Stubs</i></u>
A stub is a fake class that comes with preprogrammed ( hardcoded in simple terms) return values. It is 'injected' into the 'class under test' so that there can be a control over the input while the test case is being run.

<u><i>Mocks</i></u>
A mock is a fake class that can be examined after the test is finished for its 'interactions' with the 'class under test'. It can be used to  check how many times a method was called.

Here I would like you to go through the reference documentation of Spock [Interaction Based Testing][spock-interactiontesting] to understand it well as it is a very important topic.

Meanwhile, I would get ready with my added examples and update the post. :) . Adios

[spock-interactiontesting]: http://spockframework.org/spock/docs/1.1-rc-2/interaction_based_testing.html



