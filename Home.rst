====
Home
====

Free and open source Java reporting tool
----------------------------------------
DynamicReports is based on JasperReports. It allows to create dynamic report designs and it doesn't need a visual report designer. You can very quickly create reports and produce documents that can be displayed, printed or exported into many popular formats such as PDF, Excel, Word and others.

Why should I use DynamicReports?
--------------------------------
You can get a lot of benefits while using this library, such as

Easy to use
^^^^^^^^^^^
Very easy to use, which not only saves a lot of your time and money but also increases reporting productivity and decreases training time. Only a very small amount of code is needed to create a report and even more complex reports will be very clear, easy to maintain and understandable.

Dynamic report design
^^^^^^^^^^^^^^^^^^^^^
A design is created by a pure simple Java code. While it is generated at runtime, you can implement any logic in your code which decides how the report will look like, unlike the static reports (jrxml JasperReports templates) where the defined design cannot be changed at runtime.
It's ideal for ad hoc reporting where it is needed to create reports dynamically.

Inherited report design
^^^^^^^^^^^^^^^^^^^^^^^
A design can even be inherited from another design. This is impossible in static report designs designed in visual designers.

No need for a visual designer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
As mentioned above, a design is defined by a java code and hence you don't have to use a visual report designer. Visual designers are quite robust and require more effort and time for report creation.
This library enables you to create reports in your favorite IDE at the same speed as you write a java code.

Ability to mix dynamic designs with static designs (jasper jrxml templates)
You are able to design a part of the report in e.g. iReport and another part in DynamicReports.
There are two ways how they can work together:

  - static designs can be embedded in a dynamic design through subreports and placed into any band and any numbers of them
  - static design as a base to which a dynamic design is added

Usage
-----

DynamicReports is synchronized with a Maven central repository. For Maven projects you just add dependency to your maven configuration. In case you would like to use a development version, add a Sonatype Nexus snapshot repository to your maven configuration.

For non Maven projects you have to download a project with dependencies from the Download site.

To get started have a look at Getting started step-by-step tutorial which shows the basic usage of the tool. For more examples visit the Examples page where you will find a lot of useful examples.

In case you have questions regarding the usage, have a look at the Documentation and Forum. If you didn't get your answers there, feel free to post a question in the forum. To post in the forum you will need an account. If you don't have one, you can register at any time here.

If you think the library is missing a feature or has a bug, you can create a feature request or bug report in the Project tracker. Please provide a comprehensive description of your request when you are creating a new issue.
