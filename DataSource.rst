===========
Data source
===========

The important part of reporting is the data source which fills the report design with given data. Data can be retrieved from various sources such as a database, a xml file or using an interface JRDataSource. JasperReports itself has a lot of implementations of JRDataSource interface and basically implementation of this interface by you is quite often unneeded.
Data in reports can be additionally sorted or filtered and some components such as chart, subreport, and crosstab can have their own data source if it's needed. Please refer to the link below for examples.
Configuration options

method	description
setFilterExpression(DRIExpression<Boolean> filterExpression)	Sets a dataset filter expression. The expression must be a type of Boolean
sortBy(TextColumnBuilder<?> ...sortColumns),
sortBy(SortBuilder ...sorts),
addSort(SortBuilder ...sorts)	Adds a sort field to the dataset

Examples
^^^^^^^^
DataSource examples

Database
--------

In this type of data source, data are retrieved from a database. You only need a properly configured database connector and a SQL query.
Configuration options

method	description
setDataSource(String sql, Connection connection),
setDataSource(QueryBuilder query, Connection connection),
setDataSource(ResultSet resultSet)	Sets a database data source

Examples
^^^^^^^^
Quick usage:

.. code-block:: java
   :linenos:

   java.sql.Connection connection = ...;
   String query = "SELECT * FROM ...";
   report()
     .setDataSource(query, connection)

Another example: DatabaseDatasourceReport

Data source object
------------------

In this type, a JRDataSource object is expected as a data source. A good explanation of various implementations of data sources, as well as a few examples can be found using the following link: JasperReports data sources
Configuration options

method	description
setDataSource(JRDataSource dataSource),
setDataSource(Collection<?> collection)	Sets a data source object

Examples
^^^^^^^^
Quick usage:

.. code-block:: java
   :linenos:

   List<JavaBean> data = new ArrayList<JavaBean>();
   report()
     .setDataSource(new JRBeanCollectionDataSource(data))

Another example: CollectionDatasourceReport
Tags: datasource
