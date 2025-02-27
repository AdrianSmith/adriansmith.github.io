---
layout: single
classes: wide
author_profile: true
read_time: true
comments: true
share: true
related: true
title: "Automated Acceptance Tests for Engineering Design"
description: "Apply automated acceptance tests to engineering design."
date: 2008-08-05
show_date: true
---

Acceptance tests define exactly what stake-holders expect of a system and are therefore a critical part of the system specification. Automation of these tests has gained popularity within the agile software community, following the success of [Test and Behaviour Driven Development](https://en.wikipedia.org/wiki/Test-driven_development), and are commonly referred to as [Executable Specifications](https://gojko.net/books/specification-by-example/). The popularity has given rise to the development of a number of software tools that support the definition and execution of acceptance tests. As you would expect, there are also a range of engineering tools that support automated design verification. However, there seems to be some fundamental differences in the two approaches.

## Executable Specifications: Approach, Tools and Benefits
Ideally, requirements would be written in a way that makes it easy for the development team to verify the system against them. Making them executable enables the team members to run them as often as necessary. Executable specifications can be based on stake-holder defined stories and are therefore a means for improving communication and clarifying interpretation.

The benefits to this approach are very compelling. Firstly, there is a much tighter link between the customer and the development team.  Secondly, it provides a tool that helps reduce the gap between what your customer wants the system to do, and what the system really does.

[RSpec](http://rspec.info/) is a Behaviour Driven Development a Ruby based framework describing behaviour at an object level and an application level. Similarly, [FitNesse](http://fitnesse.org/) is another tool that is based around a Wiki that enables the collaborative definition and execution of tests.

Both tools present the tests in a form that is more user-readable than your average unit test. This allows customers to see and understand the tests as well as seeing and understanding the test results. In theory it also allows stake-holders to write tests, but in practice this rarely happens.

## Engineering Design Verification
Numerous computational tools exist for verifying the structural integrity of an engineering design.  These tools are generally based on either finite-element or classical analysis methods. While these tools are very effective in verifying design conformance against specific engineering requirements, they do not provide an effective means of either representing or verifying the design against stake-holder defined requirements. There are, however, tools emerging that support automatic verification of 2D drawing and 3D model representations of a design. An example is the iCHECK product developed by INCAT. iCHECK can help organizations minimize the risks associated with poorly-produced CAD data by applying a series of automated checks.

The available checks include:
- Model meta-data (filename, properties, tags, associations, ...)
- Modeling practices (properly constrained sketches, allowed features, feature order, sizes...)
- Model annotations (dimension styles and overrides, line types, colors, ...)
- Model adaptively and visibility setting (render setting, part visibility, ...)

One of the benefits of a tool like iCHECK is that a stake-holder can define their own checks and share this directly with the engineering design team enabling them to automatically verify the design for themselves. Although this approach can be effective, it does not verify the design against the actual stake-holder requirements for the part or assembly. This is because the tests focus on verifying the model representing the design rather than the design itself.

Many CAD systems have attempted to integrate tools that capture engineering product knowledge and design rules directly into the model. An example is the [CATIA](https://www.3ds.com/products/catia) Knowledgeware suite of tools. These tools have focused on the capture and application of business knowledge in an attempt to automate or generatively create, CAD based design data. Unfortunately, the business knowledge required to make these tools effective is generally not available in a suitable form. Additionally, these tools have lacked the technical maturity to be used reliably and the captured knowledge is not in a form that can be persisted or repurposed separately from the tool.

There are two problems that these tools are trying to solve:
- Automated/generative design based on product knowledge; and
- Engineering design verification based on product knowledge.

For the solutions to these problems to be effective, there needs to be a recognition of the importance of stake-holder involvement in the capture and execution of the business knowledge (or requirements) that drive the engineering solution. It is often the case that as an organization attempts to capture engineering knowledge a number of recurring problems emerge. Some of these include:
- Staff generally resist documenting knowledge as part of normal working practices and are even less enthusiastic in supporting specific knowledge lead initiatives.
- Staff tasked with eliciting and documenting the engineering knowledge are too inexperienced to appreciate the significance and implied context.
- Lack of a commonly used and recognized standard for storing and persisting knowledge.
Lack of commonly available tools for automating the capture and persistence of engineering design knowledge.

Note: The last two points may be challenged by those with specialist skills or experience in knowledge management - but I would argue that the lack of industry acceptance suggests that there are still significant opportunities for improvement.

So how could these tools be improved? Could the Behaviour Driven Development approach used in the software industry be applied?

## Acceptance Tests as Engineering Design Requirements
As introduced earlier, acceptance testing frameworks support are gaining momentum and provide a medium for stake-holders and software developers to communicate a common understanding a how a system should behave. Therefore, one approach would be to facilitate the definition of stake-holder requirements using a structured software approach. This would enable the definition of acceptance criteria for various aspects including structural integrity (strength, stiffness, service life, ...), geometry (interfaces, fits, space-envelope, ...) etc to be captured. The output from this could be a series executable tests that could be shared by the stake-holders and the engineering designers to run automatically to verify the design as it progresses.

There are however a number of enabling technologies needed to make the suggested approach possible. These include:
1. A domain specific language or standard for defining engineering acceptance tests.
1. A testing framework enabling the execution of tests.
1. Closer integration and interoperability between CAD, FEA, CFD and other modeling or analysis tools.

As far as I am aware there are currently no initiatives that address items 1 and 2. Progress towards the last item is largely a commercial issue with different CAD vendors unwilling to trade competitive advantage for data interoperability. Standards for representing engineering data such as [ISO15926](https://en.wikipedia.org/wiki/ISO_15926) is of benefit, however vendor adoption is slow, especially for more advanced features.
