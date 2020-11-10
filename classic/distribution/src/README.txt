WSO2 EI-Analytics @product.version@
======================================================================

Welcome to the WSO2 EI-Analytics @product.version@ release

WSO2 EI-Analytics is an instance of the [WSO2 Streaming Integrator](https://wso2.com/integration/streaming-integrator/) (WSO2 SI)
with Analytics Dashboard features. This by default is configured to monitor statistics related to the message mediation that is carried out by the
WSO2 Micro Integrator.

WSO2 EI-Analytics consists of two components: server and portal.
The server processes the data streams that are sent from the micro integrator and publishes the statistics to a database.
The portal reads the statistics published by the server and displays the statistics on the dashboard. The server and portal are connected through the database.

Installation & Running
==================================

Running the runtime and dashboard
==================================
Navigate to the <EI-Analytics_Home>/bin directory in the console and issue the appropriate command depending on your operating system.

For server:
- In Windows: server.bat
- In Linux/MacOS: ./server.sh

For portal:
- In Windows: portal.bat
- In Linux/MacOS: ./portal.sh

Known issues of WSO2 EI-Analytics @product.version@
==================================

     - https://github.com/wso2/observability-ei/issues

Support
==================================

WSO2 Inc. offers a variety of development and production support
programs, ranging from Web-based support up through normal business
hours, to premium 24x7 phone support.

For additional support information please refer to http://wso2.com/support/

For more information on WSO2 EI-Analytics, visit the GitHub page (https://github.com/wso2/observability-ei)

Crypto Notice
==================================

   This distribution includes cryptographic software.  The country in
   which you currently reside may have restrictions on the import,
   possession, use, and/or re-export to another country, of
   encryption software.  BEFORE using any encryption software, please
   check your country's laws, regulations and policies concerning the
   import, possession, or use, and re-export of encryption software, to
   see if this is permitted.  See <http://www.wassenaar.org/> for more
   information.

   The U.S. Government Department of Commerce, Bureau of Industry and
   Security (BIS), has classified this software as Export Commodity
   Control Number (ECCN) 5D002.C.1, which includes information security
   software using or performing cryptographic functions with asymmetric
   algorithms.  The form and manner of this Apache Software Foundation
   distribution makes it eligible for export under the License Exception
   ENC Technology Software Unrestricted (TSU) exception (see the BIS
   Export Administration Regulations, Section 740.13) for both object
   code and source code.

   The following provides more details on the included cryptographic
   software:

   Apache Rampart   : http://ws.apache.org/rampart/
   Apache WSS4J     : http://ws.apache.org/wss4j/
   Apache Santuario : http://santuario.apache.org/
   Bouncycastle     : http://www.bouncycastle.org/

--------------------------------------------------------------------------------
(c) Copyright 2020 WSO2 Inc.
