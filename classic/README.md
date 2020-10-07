# Classic Observability Deployment

WSO2 EI-Analytics provides capability to analyze statistics and tracing of WSO2 Enterprise Integrator.

WSO2 EI-Analytics is an instance of the [WSO2 Streaming Integrator](https://wso2.com/integration/streaming-integrator/) (WSO2 SI) 
with Analytics Dashboard features. This by default is configured to monitor statistics related to the message mediation that is carried out by the 
WSO2 Micro Integrator.

WSO2 EI-Analytics consists of two components: server and portal. 
The server processes the data streams that are sent from the micro integrator and publishes the statistics to a database. 
The portal reads the statistics published by the server and displays the statistics on the dashboard. The server and portal are connected through the database. 

## Building from the Source
To build WSO2 EI-Analytics from source, follow the steps below.

1. Clone or download the source code from this repository.
2. Run mvn clean install from the root directory of the repository.
3. The generated EI-Analytics distribution can be found at observability-ei/classic/distribution/target/wso2ei-analytics-<version>.zip

## Getting Started

Navigate to the <EI-Analytics_Home>/bin directory in the console and issue the appropriate command depending on your operating system.

For server: 
- In Windows: server.bat
- In Linux/MacOS: ./server.sh

For portal:
- In Windows: portal.bat
- In Linux/MacOS: ./portal.sh


## License
WSO2 EI-Analytics is licensed under the [Apache License](http://www.apache.org/licenses/LICENSE-2.0).

## How To Contribute
Please report issues at WSO2 EI Analytics Issues.
Send your pull requests https://github.com/wso2/observability-ei.
You can find more instructions on how to contribute on community site (http://wso2.com/community).

## Contact Us

WSO2 developers can be contacted via the mailing lists:

* WSO2 Developers List : dev@wso2.org
* WSO2 Architecture List : architecture@wso2.org
