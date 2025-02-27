---
layout: single
classes: wide
author_profile: true
read_time: true
comments: true
share: true
related: true
title: "Engineering Design Framework"
description: "An engineering design framework for mechanical part and assembly design."
date: 2008-06-15
show_date: true
---

The effectiveness of software application frameworks such as [Ruby on Rails](https://rubyonrails.org/), automated build tools like [Maven](https://maven.apache.org/), and architectural design patterns like [Model-View-Controller](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller), demonstrate the value of a structured approach to development tasks. For me, the expression _"[convention over configuration](https://en.wikipedia.org/wiki/Convention_over_configuration)"_ really sums it up. When I'm developing an application I'm far more interested in the business logic rather than the inner workings of the framework or how I should structure an application.

Ruby on Rails achieves this goal by simplifying web application development and removing configuration decisions so that the developer can focus on solving the business problem. With this in mind I thought there may be value in exploring an equivalent framework for mechanical part and assembly design.


## The Basic Framework
The framework would be based on a file structure with names that follow the [Principle of Least Surprise](https://en.wikipedia.org/wiki/Principle_of_least_astonishment). The file structure would encourage engineers to organise their data and working files consistently across teams and projects. The default file structure would be generated and supported by scripts and file templates. Scripts would also be used to create new assemblies, parts, references, and generate reports. Additionally, the framework would leverage a number of established standards for engineering data – for example [MatML](https://www.nist.gov/publications/matml-version-30-schema) for material property data. The following is a first pass at how this might look.

At the first level the framework would contain directories for configuration, management, references, scripts, templates and work.

The configuration directory would contain vendor, supplier and project details together with specific framework configurations.

The management directory would contain typical project management documents including customer supplied data, reports and commercial and technical quality plans. Registers of the data would also be included as XML and could be potentially maintained automatically using scripts.

The reference directory would contain engineering reference data such as MIL Handbook or ASME data that is used across the project and is approved by the customer. In some instances this data may be public domain but the majority is likely to be proprietary to either the customer or the vendor and would be separated accordingly. An important assumption (convention) would be that all data would be current and approved for use. Ensuring this assumption holds true may be difficult, especially on larger projects, but this is something the framework could help maintain using automation. Reference data would be separated into design, analysis, manufacturing and materials. Ideally data and methods would be stored in neutral formats to maximise reuse opportunities.

The scripts and templates directories would contain standard scripts and templates together with any customised functionality. Templates would be defined in XML and styled using XSLT.

The work directory would contain the parts and assemblies structured according to the part hierarchy. An XML file would store these relationships for interrogation or reporting purposes. Part numbers would be used to uniquely identify part and assembly directories. For each component the design inputs and outputs would be separated. Inputs would be further separated into geometry, applied loads and materials and ideally stored as XML files. The outputs would be representative of the design lifecycle and resulting data formats, typically CAD, FEA, structural analysis reports and manufacturing plans. The maturity of the design could be captured in an XML file for each part according to a standard product lifecycle.

## Framework Infrastructure and Automation
A scripting language would be needed to support the framework and the obvious choice would be either Python or Ruby. Since the framework is intended for the engineering community, Python might seem like a prudent choice as it has always had a strong association with the scientific and technical computing community. However, the clean expressive nature of the Ruby language together with the Gem system for package management makes Ruby the preferred option.

Users would interact with the framework in the same way as they do with Ruby on Rails. For example from the command line:

Setting up a new project:
```
% engfwk project_name vendor_name client_name
```

Add a new assembly, part, material or load:
```
% ruby script/generate assembly assembly_name parent_assemby_name
% ruby script/generate part name parent_assembly_name
% ruby script/generate material source_filename.xml
% ruby script/generate load source_filename.xml
```

Create a progress report:
```
% rake report:progress
```

Clean the project file structure:
```
% rake verify:project
```

Generate project statistics:
```
% rake stats
```

## Benefits
In my experience, on large engineering design projects the approach that different engineers take when they design or analyse parts is largely dependent on how they did it last time, rather than best practice guidelines or company standards. The benefits of coercing the design and analysis activity into a standard structure is that users know exactly where to find and store data. While this may sound minor, on large projects this makes a huge difference to team productivity, ensuring the right reference data is used and the ease with which engineers can pickup another engineers work. Another benefit to structuring data in a consistent and predictable way is that engineers would be able to developer tools or pluggable extensions to the framework that could be reused across other projects.

## Concerns
The main concern with this idea is that the proposed framework could be considered just a simple, file-based PDM system. This is a valid concern, but the low costs and flexibility of the proposed framework probably negates this concern.

## Next Steps
The best way to explore the potential benefits of an engineering design framework would be to try applying it to a design problem. This will be my next step…
