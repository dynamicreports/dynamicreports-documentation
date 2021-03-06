==============
Report Builder
==============

JasperReportBuilder
-------------------

The most used report builder for creating reports. It allows constructing and 
customizing the whole report content. A report consists of bands, columns, 
subtotals, groups, and other parts. Each part is created and configured using 
a particular builder method and it's passed to the report builder instance.

In the table below, you will find a list of all available builders:

.. |br| raw:: html

    <br>
    
================== ======================================== ======================= ==================== ===========   
Builder name	   Using a static import for DynamicReports Without a static import Using a particular 	 Description
                   |br| methods                                                     builder
                   import static net.sf.dynamicreports |br|  
                   .DynamicReports.*		
================== ======================================== ======================= ==================== ===========   
ColumnBuilders	   col.*                                    DynamicReports.col.*	Columns.*	         A set of methods of creating report columns
GridBuilders	   grid.*                                   DynamicReports.grid.*	Grids.*	             A set of methods of customizing columns layout
GroupBuilders	   grp.*                                    DynamicReports.grp.*	Groups.*	         A set of methods of creating report groups
SubtotalBuilders   sbt.*                                    DynamicReports.sbt.*	Subtotals.*	         A set of methods of creating column subtotals
StyleBuilders	   stl.*                                    DynamicReports.stl.*	Styles.*	         A set of methods of creating and customizing styles
ComponentBuilders  cmp.*                                    DynamicReports.cmp.*	Components.*	     A set of methods of creating components
ExpressionBuilders exp.*                                    DynamicReports.exp.*	Expressions.*	     A set of build in expressions
ConditionBuilders  cnd.*                                    DynamicReports.cnd.*	Conditions.*	     A set of build in condition expressions
DataTypeBuilders   type.*                                   DynamicReports.type.*	DataTypes.*	         A set of build in data types
ChartBuilders	   cht.*                                    DynamicReports.cht.*	Charts.*	         A set of methods of creating and customizing charts
ExporterBuilders   export.*                                 DynamicReports.export.*	Exporters.*	         A set of methods of creating exporters
BarcodeBuilders	   bcode.*                                  DynamicReports.bcode.*	Barcodes.*	         A set of methods of creating barcodes
CrosstabBuilders   ctab.*                                   DynamicReports.ctab.*	Crosstabs.*	         A set of methods of creating and customizing crosstabs
================== ======================================== ======================= ==================== ===========   

**Examples**
|br| Quick usage:

.. code-block:: java
   :linenos:

    report()
    .columns(
        col.column("Item", "item", type.stringType()), 
        col.column("Quantity", "quantity", type.integerType())) 
    .title(cmp.text("Report title"))
    .setDataSource(...)
    .show();

Another example: SimpleReport_Step01

JasperConcatenatedBuilder
-------------------------

This report builder allows concatenating several separated reports into one single 
document. Each report starts on a new page with its own page dimension.

**Examples**
|br| Quick usage:

.. code-block:: java
   :linenos:

    JasperReportBuilder report1 = ...;
    JasperReportBuilder report2 = ...;
    concatenatedReport()
    .concatenate(report1, report2)
    .toPdf(...)

Another examples: ConcatenatedReport1, ConcatenatedReport2
