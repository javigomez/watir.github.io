---
layout: page
title: Automation Pipeline
permalink: /docs/overview/
---

Watir is a user focused way to test your websites. It mostly uses Selenium for
browser automation, but it provides many more high level features that make
it easy to write stable, maintainable tests.

The ideal flow of information looks like this: 

Test Runner --> <br />
&nbsp; &nbsp; &nbsp; 
Test code --> <br /> 
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; 
PageObject code --> <br /> 
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp;&nbsp; &nbsp; 
Watir library-->  <br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;&nbsp; &nbsp; 
Selenium library -->  <br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;&nbsp; &nbsp; 
Selenium Server(s) (optional) --> <br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;&nbsp; &nbsp; 
Browser Driver -->  <br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;&nbsp; &nbsp;&nbsp; &nbsp; 
Browser
                        
1. **Test Runner.** In Ruby this can be MiniTest, RSpec or Cucumber. Most Watir users use RSpec
by default, but Cucumber is popular for teams that are working in a Behavior Driven Development
environment

2. **Test Code.** Whether Cucumber Steps or RSpec "it" blocks, the code here should be
focused on succinctly representing the business requirement for the test. This is the
higher level "what" code that references other objects (like page objects) for the actual implementation.
Ruby is more readable than most langauges, so name your page objects and methods well 
and a cursory inspection will allow you to easily understand the purpose of your test.

3. **Page Object.** This is where you put all of your implementation ("how") code. 
Page objects can represent an entire page, 
a modal, or a section of a page (like a sidebar or a footer). 
Page objects are where you store the locators of the elements you need to interact with, 
and the methods that represent the actions that a user can take on the page.
Most of this code will be references to Watir objects.

4. **Watir Code.** Watir takes the higher level code in your page object and translates
it into the series of applicable Selenium and Javascript calls to accomplish the desired
functionality. Watir attempts to understand the intention of the code you are writing
and tries to follow a "Do What I Mean" philosophy to accomplish it. Continue reading 
through the documentation to see how Watir makes writing tests fun and easy.

5. **Selenium Code.** Selenium focuses on the specific low level actions that can be taken 
on a browser. It implements a small number of locators and takes a "Do What I Say" approach.
It translates idiomatic Ruby code into serialized json blobs to send along for further processing.

6. **Selenium Server.** This isn't necessary if you are running locally on your own machine.
If you want to run code on a remote machine, however, the Selenium code needs
to be sent to a server. The server can be set to act in a standalone mode, or you can set up a 
grid and have a server on another machine that acts as a "hub", and a server on a third machine
that acts as a "node".

7. **Browser Drivers.** Because of the progress on the [W3C WebDriver Specification](https://w3c.github.io/webdriver/webdriver-spec.html), 
each major browser vendor (Google, Microsoft, Apple, and Mozilla) has committed to 
implementing their own driver for their respective browser. The driver is an executable
file that lives on the same machine as the browser you want to automate. Read the 
[Drivers documentation](../docs/drivers) to see how to download and store the driver so that
Selenium can find and use it. The driver accepts the standardized information from Selenium 
code and translates it into code needed by the particular browser to take the action specified.

8. **Browser.** The browser executes each command sent by the driver.
