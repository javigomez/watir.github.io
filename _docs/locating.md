---
layout: page
title: Locating Elements
permalink: /docs/elements/
---

One of the biggest features of Watir is all of the ways it allows you to locate elements.

The Standard Selenium Locators:
* ID 
* Name 
* Link Text
* Partial Link Text
* Class Name
* Tag Name
* CSS
* XPath

Additional Watir Locators:
* Text
* Data attributes
* Aria attributes
* Any attribute in HTML5 spec for given element
* Presence/Absence/Multiple Attributes
* Presence/Absence/Multiple Classes
* Label
* Visible
* Adjacent (parent, child, previous sibling, following sibling)
* Index

Everything that can be located by String can use a Regular Expression to
allow partial matching on any locator.

All of these can be mixed and matched to provide as much specificity as you need to find 
what you are looking for.