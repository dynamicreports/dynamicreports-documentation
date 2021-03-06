======
Syntax
======

Before you start creating reports with DynamicReports, you should consider 
which java syntax you will use. Java 5 added static imports that allow 
static methods or constants to be referenced without qualifying them with 
a class name. DynamicReports provides a lot of static methods of creating 
every part of a report and therefore you can consider using a static import 
for these methods. And DynamicReports also provides the abillity to use 
`Method chaining <https://en.wikipedia.org/wiki/Method_chaining>`_ (also known 
as `Fluent interface <https://en.wikipedia.org/wiki/Fluent_interface>`_). Both are useful for code 
eadability, the ability to replace multiple calls to a class with a single one, 
and for invoking multiple method calls.
Let's see in detail the difference between using and not using a static 
import and method chaining:

Classic java Syntax
^^^^^^^^^^^^^^^^^^^
Classic java syntax (without using a static import and method chaining)

.. code-block:: java
   :linenos:

    JasperReportBuilder report = DynamicReports.report();
    report.addColumn(Columns.column("Item", "item", DataTypes.stringType()));
    report.addColumn(Columns.column("Quantity", "quantity", DataTypes.integerType()));
    report.addTitle(Componens.text("Report title"));
    report.setDataSource(dataSource)
    report.show();

Using a static import
^^^^^^^^^^^^^^^^^^^^^
Using a static import for DynamicReports methods and method chaining

.. code-block:: java
   :linenos:

    import static net.sf.dynamicreports.DynamicReports.*;
    report()
    .columns(
        col.column("Item", "item", type.stringType()), 
        col.column("Quantity", "quantity", type.integerType())) 
    .title(cmp.text("Report title"))
    .setDataSource(dataSource)
    .show();

As you can see, static imports and method chaining improve readability of the code but they are not mandatory. It's only up to you which code syntax you will prefer to use.
All examples and tutorials in the documentation use static imports and method chaining to provide more readability of the code.

Examples
^^^^^^^^
SimpleReport_ClassicSyntax, SimpleReport_Step01