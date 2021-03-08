==========
Expression
==========

Expressions are used to define various calculations, conditions, text field content, specific report groups, etc. Every expression can access the declared report fields, variables and other expressions and get their values to calculate the expression value.
It must be an instance of DRIExpression.

Simple expression
-----------------

The basic and the simplest implementation of an expression.

A simple expression must be an instance of DRISimpleExpression and implement the inherited abstract method evaluate.

| *public Object evaluate(ReportParameters reportParameters)*;
| - reportParameters - access to report fields, variables, parameters, expressions, and other report values
| - the method returns the result of the expression evaluation

| **Examples**
| Quick usage:

.. code-block:: java
   :linenos:

    private class SimpleExpression extends AbstractSimpleExpression<BigDecimal> {
    public BigDecimal evaluate(ReportParameters reportParameters) {
        Integer quantity = reportParameters.getValue("quantity");
        BigDecimal unitPrice = reportParameters.getValue("unitprice");
        return new BigDecimal(quantity).multiply(unitPrice);
    }
    }

Another example: `SimpleExpressionReport <#>`_

Complex expression
------------------

The difference between a simple and complex expression is that a complex expression allows registering additional fields or variables that are not defined in the report and are needed for calculating the value.

A complex expression must be an instance of DRIComplexExpression and must implement the inherited abstract method evaluate.

| *public Object evaluate(List<?> values, ReportParameters reportParameters)*;
| - values - the values of the registered expressions
| - reportParameters - access to report fields, variables, parameters, expressions, and other report values
| - the method returns the result of the expression evaluation

| **Examples**
| Quick usage:

.. code-block:: java
   :linenos:

    private class ComplexExpression extends AbstractComplexExpression<BigDecimal> {
    public ComplexExpression() {
        addExpression(field("quantity", Integer.class));
        addExpression(field("unitprice", BigDecimal.class));
    }

    @Override
    public BigDecimal evaluate(List<?> values, ReportParameters reportParameters) {
        Integer quantity = (Integer) values.get(0);
        BigDecimal unitPrice = (BigDecimal) values.get(1);
        return new BigDecimal(quantity).multiply(unitPrice);
    }
    }

Another example: `ComplexExpressionReport <#>`_ 

Jasper expression
-----------------

This expression allows declaring an expression in a Jasper native syntax. Knowledge of the jasper syntax is also required for proper use.

**Configuration options**

= ============================================ =================================================
# method	                                   description
= ============================================ =================================================
1 | exp.jasperSyntax(String expression, Class  | Creates a new jasper expression
  |     class),                                | - expression - the jasper expression
  | exp.jasperSyntax(String expression)        | - class - the expression class
2 | exp.jasperSyntaxText(String text)          | Creates a new jasper string expression, useful 
  |                                            | only for showing a static text. This method 
  |                                            | escapes the characters in a String using Java 
  |                                            | String rules. - text - text to be shown
= ============================================ =================================================

| **Examples**
| Quick usage:

.. code-block:: java
   :linenos:

    JasperExpression<BigDecimal> columnExpression = exp.jasperSyntax("new BigDecimal($F{quantity}).multiply($F{unitprice})", BigDecimal.class);
    JasperExpression<String> columnTitle = exp.jasperSyntaxText("Price");
    TextColumnBuilder<BigDecimal> priceColumn = col.column(columnExpression).setTitle(columnTitle);

Another example: `JasperExpressionReport <#>`_

Value formatter
---------------

The purpose of this expression is to format a value only. For instance, when it is necessary to display a currency next to the value or just show a value in another format. It can be applied in any report column, group, subtotal, or text field component.

A value formatter expression must be an instance of DRIValueFormatter and must implement the inherited abstract method format.

| *public Object format(Object value, ReportParameters reportParameters)*;
| - value - the value to be formatted
| - reportParameters - access to report fields, variables, parameters, expressions, and other report values
| - the method returns the formatted value

| **Examples**
| Quick usage:

The code below converts a big decimal value to a string and adds a currency symbol next to the value.

.. code-block:: java
   :linenos:

    TextColumnBuilder<BigDecimal>  column = ...;
    column. setValueFormatter(new ValueFormatter())) 
    private class ValueFormatter extends AbstractValueFormatter<String, BigDecimal> {     
        public String format(BigDecimal value, ReportParameters reportParameters) { 
            return value + " EUR"; 
        } 
    }

| Another example: `ValueFormatterReport <#>`_
| Tags: expression