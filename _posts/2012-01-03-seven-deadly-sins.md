---
layout: single
classes: wide
author_profile: true
read_time: true
comments: true
share: true
related: true
title: "Seven Deadly Sins of Automated Testing"
description: "Seven common pitfalls of automated testing."
date: 2012-01-03
show_date: true
---

When [Craig Smith](https://craigsmith.id.au) and I were planning our presentation for Agile 2011 – we toyed with the idea of listing 7 anti-patterns for automated testing. I’ve taken these patterns and loosely matched them to the classic seven-deadly-sins. This metaphor also allowed me to include a linocut that my uncle Errol Smith made – pictured here.

![Seven Deadly Sins]({{ site.baseurl }}/assets/images/sins/seven-deadly-sins.png){: .align-right width="300px" alt="Seven Deadly Sins"}

Senior management often view automated testing as a silver bullet in reducing testing effort/costs and increasing delivery speed. While it is true that automated tests can provide rapid feedback on health of the system, all approaches to automated testing are not created equal and there are some gotchas that should be avoided.

## 1. Envy
![Envy]({{ site.baseurl }}/assets/images/sins/envy.png){: .align-right width="300px" alt="Envy"}

Flawed comparison between manual testing and automation

Automated tests are not a replacement for manual exploratory testing. A mixture of testing types and levels is needed to achieve the desired quality mitigate the risk associated with defects. This is because testing is not merely a sequence of repeatable actions. The automated testing triangle originally described by Mike Cohn explains the investment profile in tests should focus at the unit level and then reduce up through the application layers.

## 2. Gluttony
![Gluttony]({{ site.baseurl }}/assets/images/sins/gluttony.png){: .align-right width="300px" alt="Gluttony"}

#### _Over indulging on commercial testing tools_

Many commercial testing tools provide simple features for automating the capture and replay of manual test cases. While this approach seems sound, it encourages testing through the user-interface and results in inherently brittle and difficult to maintain tests. Additionally, the cost and restrictions that licensed tools place on who can access the test cases is an overhead that tends to prevent collaboration and team work. Furthermore, storing test cases outside the version control system creates unnecessary complexity. As an alternative, open source test tools can usually solve most automated testing problems and the test cases can be easily included in the version control system.

## 3. Lust
![Lust]({{ site.baseurl }}/assets/images/sins/lust.png){: .align-right width="300px" alt="Lust"}

Loving the UI so much that all tests are executed through the UI

Although automated UI tests provide a high level of confidence, they are expensive to build, slow to execute and fragile to maintain. Testing at the lowest possible level is a practice that encourages collaboration between developers and testers, increases the execution speed for tests and reduces the test implementation costs. Automated unit tests should be doing a majority of the test effort followed by integration, functional, system and acceptance tests. UI based tests should only be used when the UI is actually being tested or there is no practical alternative.

## 4. Pride
![Pride]({{ site.baseurl }}/assets/images/sins/pride.png){: .align-right width="300px" alt="Pride"}

#### _Too proud to collaborate when creating tests_

Test driven development is an approach to development that is as much a design activity as it is a testing practice. The process of defining test cases (or executable specifications) is an excellent way ensuring that there is a shared understanding between all involved as to the actual requirement being developed and tested. The practice is often associated with unit testing but can be equally applied to other test types including acceptance testing.

## 5. Sloth
![Sloth]({{ site.baseurl }}/assets/images/sins/sloth.png){: .align-right width="300px" alt="Sloth"}

#### _Too lazy to maintain automated tests_

The cost and rapid feedback benefits of automated tests are best realised when the tests are regularly executed. This has the effect of highlighting failures and providing continuous feedback about the health of the system. If your automated tests are initiated manually rather than through the CI continuous integration system then there is significant risk that they are not being run regularly and therefore may in fact be failing. Make the effort to ensure automated tests are executed through the CI system.

## 6. Rage
![Rage]({{ site.baseurl }}/assets/images/sins/rage.png){: .align-right width="300px" alt="Rage"}

#### _Frustration with slow, brittle or unreliable tests_

Unreliable tests are a major cause for teams ignoring or losing confidence in automated tests. Once confidence is lost the value initially invested in automated tests is dramatically reduced. Fixing failing tests and resolving issues associated with brittle tests should be a priority to eliminate false positives.

## 7. Avarice (Greed)
![Avarice]({{ site.baseurl }}/assets/images/sins/greed.png){: .align-right width="300px" alt="Avarice"}

#### _Trying to cut costs through automation_

Testing tool vendors often try to calculate a Return-on-Investment based purely on labour savings. This analysis is unreliable and under values the importance of testing, the investment required to adopt automation practices and the ongoing maintenance costs.

## Summary

Automated testing is not without pitfalls and some of these are identified here. There are of course many other anti-patterns for automated testing that justify further discussion.
