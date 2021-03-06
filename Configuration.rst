=============
Configuration
=============

Default settings
----------------
DynamicReports automatically looks for a file named :ref:`dynamicreports-defaults` on startup.
In this file you can change the default settings (default font, pattern and horizontal alignment for all data types).

.. code-block:: xml
   :linenos:

    <?xml version="1.0" encoding="UTF-8"?>
    <DynamicReports>
    <!-- DEFAULT FONT -->
    <font fontName="SansSerif" fontSize="10" pdfFontName="Helvetica" pdfEncoding="Cp1252" pdfEmbedded="false"/>
        
    <!-- DEFAULT DATA TYPES -->
    <bigDecimalType pattern="#,##0.00#" horizontalAlignment="RIGHT"/>
    <dateType pattern="MM/dd/yyyy" horizontalAlignment="RIGHT"/>
    ... 
    </DynamicReports>

Copy this file in the root of the classpath.

Maven configuration
-------------------
DynamicReports is synchronized with Maven Central Repository.
Add the dependencies listed below to your pom.xml configuration file.

.. code-block:: xml
   :linenos:

    <dependency>
      <groupId>net.sourceforge.dynamicreports</groupId>
      <artifactId>dynamicreports-core</artifactId>
      <version>5.1.0</version>
    </dependency>
    <dependency>
      <groupId>net.sourceforge.dynamicreports</groupId>
      <artifactId>dynamicreports-adhoc</artifactId>
      <version>5.1.0</version>
    </dependency>  
    <dependency>
      <groupId>net.sourceforge.dynamicreports</groupId>
      <artifactId>dynamicreports-googlecharts</artifactId>
      <version>5.1.0</version>
    </dependency>

In some situations, maven may have a problem with downloading the itext-2.1.7.js6 
dependency to your local maven repository. The problem may happen because the 
library itext-2.1.7.js6 is not available in maven central repository, it is only 
available through `JasperReports maven repository <http://jasperreports.sourceforge.net/maven2>`_. 
If you are behind a firewall check if the firewall is not blocking that repository 
link or download the dependency and add it to your repository manually.


Maven snapshot repository configuration
To use the development snapshots of DynamicReports, change your pom.xml configuration:
just update the dynamicreports-core version

.. code-block:: xml
   :linenos:

    <dependency>
      <groupId>net.sourceforge.dynamicreports</groupId>
      <artifactId>dynamicreports-core</artifactId>
      <version>5.1.1-SNAPSHOT</version>
    </dependency>
    <dependency>
      <groupId>net.sourceforge.dynamicreports</groupId>
      <artifactId>dynamicreports-adhoc</artifactId>
      <version>5.1.1-SNAPSHOT</version>
    </dependency>
    <dependency>
      <groupId>net.sourceforge.dynamicreports</groupId>
      <artifactId>dynamicreports-googlecharts</artifactId>
      <version>5.1.1-SNAPSHOT</version>
    </dependency>

and add the Sonatype Nexus snapshot repository

.. code-block:: xml
   :linenos:

    <repositories>
      <repository>
        <id>sonatype-nexus-snapshots</id>
        <name>Sonatype Nexus Snapshots</name>
        <url>https://oss.sonatype.org/content/repositories/snapshots</url>
        <releases>
          <enabled>false</enabled>
        </releases>
        <snapshots>
          <enabled>true</enabled>
        </snapshots>
      </repository>
    </repositories>

.. _dynamicreports-defaults:

dynamicreports-defaults.xml
---------------------------

.. code-block:: xml
   :linenos:

   <?xml version="1.0" encoding="UTF-8"?>
   <DynamicReports>
      <!-- DEFAULT FONT -->
      <!--
      <font fontName="SansSerif" fontSize="10"/>
      -->
        
      <!-- DEFAULT DATA TYPES -->
      <!--
      <bigDecimalType pattern="#,##0.00#" horizontalAlignment="RIGHT"/>
      <bigIntegerType pattern="#,##0" horizontalAlignment="RIGHT"/>  
      <byteType pattern="#,##0" horizontalAlignment="RIGHT"/>
      <doubleType pattern="#,##0.#" horizontalAlignment="RIGHT"/>
      <floatType pattern="#,##0.#" horizontalAlignment="RIGHT"/>  
      <integerType pattern="#,##0" horizontalAlignment="RIGHT"/>
      <longType pattern="#,##0" horizontalAlignment="RIGHT"/>  
      <shortType pattern="#,##0" horizontalAlignment="RIGHT"/>
      <dateType pattern="MM/dd/yyyy" horizontalAlignment="RIGHT"/>
      <dateYearToMonthType pattern="MM/yyyy" horizontalAlignment="RIGHT"/>  
      <dateYearToHourType pattern="MM/dd/yyyy h a" horizontalAlignment="RIGHT"/>
      <dateYearToMinuteType pattern="MM/dd/yyyy h:mm a" horizontalAlignment="RIGHT"/>
      <dateYearToSecondType pattern="MM/dd/yyyy h:mm:ss a" horizontalAlignment="RIGHT"/>
      <dateYearToFractionType pattern="MM/dd/yyyy h:mm:ss,SSS a" horizontalAlignment="RIGHT"/> 
      <dateYearType pattern="yyyy" horizontalAlignment="RIGHT"/>
      <dateMonthType pattern="MMMM" horizontalAlignment="RIGHT"/>
      <dateDayType pattern="dd" horizontalAlignment="RIGHT"/>       
      <timeHourToMinuteType pattern="h:mm a" horizontalAlignment="RIGHT"/>
      <timeHourToSecondType pattern="h:mm:ss a" horizontalAlignment="RIGHT"/>
      <timeHourToFractionType pattern="h:mm:ss,SSS a" horizontalAlignment="RIGHT"/> 
      <percentageType pattern="#,##0.00%" horizontalAlignment="RIGHT"/>
      <booleanType horizontalAlignment="CENTER"/>
      <characterType horizontalAlignment="LEFT"/>
      <stringType horizontalAlignment="LEFT"/>
      -->
    
      <!-- LOAD SYSTEM FONTS -->
      <!--
      <loadSystemFonts>true</loadSystemFonts>
      -->
   </DynamicReports>
