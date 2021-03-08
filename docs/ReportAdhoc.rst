=============
Adhoc Reports
=============

Adhoc report applications allow users themselves to create specific reports and filter queries. A report is created on the fly, displaying values or charts that a user has specified via GUI.
This project simplifies creating adhoc report applications. It allows to configure reports and filter queries and this configuration can be stored to an xml file or loaded from an xml file. The main configuration object is AdhocConfiguration that consists of AdhocReport and AdhocFilter object.

| **AdhocReport** - a report configuration object that can be transformed to a dynamic report builder object.
| **AdhocFilter** - a filter configuration object. This project doesn't generate sql queries from this object, it only allows you to store and load a filter configuration.
| Another important class of this project is **AdhocManager**. It is a helper class that contains methods of loading/storing an AdhocConfiguration from/to a stream and methods of creating a report builder instance from a given AdhocReport object.

.. image:: ../images/adhoc.png

| **Examples**
| Quick usage:

.. code-block:: java
   :linenos:

    AdhocConfiguration configuration = new AdhocConfiguration();
    AdhocReport report = new AdhocReport();
    configuration.setReport(report);
    AdhocColumn column = new AdhocColumn();
    column.setName("item");
    report.addColumn(column);

The following code stores a configuration to an output stream

.. code-block:: java
   :linenos:

    AdhocManager.saveConfiguration(configuration, outputStream);

The following code loads a configuration from an input stream

.. code-block:: java
   :linenos:

    AdhocConfiguration configuration = AdhocManager.loadConfiguration(configuration, inputStream);

The following code converts a configuration to a report builder instance

.. code-block:: java
   :linenos:

    JasperReportBuilder reportBuilder = AdhocManager.createReport(configuration.getReport());
    reportBuilder.setDatasource(...);

Tags: adhoc