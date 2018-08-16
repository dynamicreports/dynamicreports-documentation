Getting Started
===============

Overview
--------

Creating a report with DynamicReports is very easy, take a look at the example below

.. code-block::
  import static net.sf.dynamicreports.report.builder.DynamicReports.*;
    public class Report {
      private void build() {
        try {
          report()//create new report design
            .columns(...) //adds columns
            .groupBy(...) //adds groups
            .subtotalsAtSummary(...) //adds subtotals
            ...
            //set datasource
            .setDataSource(...)
            //export report
            .toPdf(...) //export report to pdf
            .toXls(...) //export report to excel
            ...
            //other outputs
            .toJasperPrint() //creates jasperprint object
            .show() //shows report
            .print() //prints report
            ...
        } catch (DRException e) {
          e.printStackTrace();
        }
      }
      ...
    }

See ReportBuilder class for all available features and JasperReportBuilder class for all available exports and outputs.

Simple report
-------------

Please note that this is a tutorial example and that this tutorial doesn't describe all features!

You will learn in this section how to create a simple report step by step.
First we need to create an empty report desing, configure it and set a datasource. Afterwards the report will be ready to export into any format.
It's important to remember the DynamicReports class, through which you will have available most of features. The class provides methods for building a particular piece of a report.
Let's start!


Step 1 : Start
--------------

First define columns through DynamicReports.col.column(title, field name, datatype) (the field name must match with the name of a field contained in the datasource) and pass them into the report as follows:

.. code-block::

  .columns(//add columns
    //             title,     field name     data type
    col.column("Item",       "item",      type.stringType()),
    col.column("Quantity",   "quantity",  type.integerType()),
    col.column("Unit price", "unitprice", type.bigDecimalType()))
