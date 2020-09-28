# Testing-Tools-Info
This provides a document on basic information about testing tools

1. What is the Macro View of Hygieia?
Hygieia appears in two self-contained dashboards – one for engineers and another for executives - that visually depict CICD pipelines. In essence, Hygieia itself is an aggregator that pulls data from various DevOps tools that teams use in their CICD pipeline, making it easily digestible in dashboard view(s). Although it is an easily manipulated tool, Hygieia provides complex insights into the following areas:

DevOps Maturity: It offers fully automated CICD tracking quality and pipeline speed
Risk Management and Investing: It connects operational metrics to developmental metrics, offering a full understanding of where to invest in order to improve processes that reduce unnecessary risk taking in the future
On-going Enhancements for Agile Environments: It quantifies DevOps metrics to track and improve DevOps maturity
Establishes and Raises Standards: It sets and achieves a profile for maturity metrics and products. When products dip below the bar, it triggers an alert notification. In addition, this bar goes up incrementally to ensure that all products undergo simultaneous improvements

What Makes Hygieia Important?
Hygieia’s dashboards simplify the ability to view CICD pipelines in near real-time. The dashboards enable DevOps engineers and executives to monitor the health of code commit to deployment in final production. Between those two points – inception (commit) to completion (prod) – the dashboards also provide crucial information about the overall vitality and performance metrics of your software operations.

# Underlying Frameworks and Technologies
1. Bower
2. Java
3. Angular JS
4. Mongo DB
5. Maven
6. Docker
7. NodeJs
8. GULP

# Old UI Setup Instructions
Instructions to install all components of Hygieia
Prerequisites
Download or Clone Hygieia
Build Hygieia
Prerequisites
The following are the prerequisites to set up Hygieia:

Install Git - For installation steps, see the Installing Git section of Git’s documentation.
Install Java - Version 1.8 is recommended
Install Maven - Version 3.3.9 and above are recommended
Install Node - Version 8 is recommended.
If you’re using a Mac and don’t have node already installed, run:

brew install node@8 
Install npm - Version 5 or higher.
Download or Clone Hygieia
If you do not already have Hygieia installed, you can fork and clone Hygieia from the GitHub repo. Make sure that you also download the hygieia-core and api.

For information on forking a repository, see the Fork a repo section of GitHub’s Documentation. For information on cloning a repository, see the Cloning a Repository section of GitHub’s Documentation.

Build Hygieia
To package all components of Hygieia’s source code into executable JAR files, run the maven build. Before you build Hygieia using Maven, make sure to configure the settings.xml file. For more details, see Proxy Authentication.

Hygieia uses Spring Boot to package the components as an executable JAR file with dependencies.

** Note: The collectors are being migrated to their own repositories. Please see Module breakout section of Hygieia-2019-Roadmap-(draft,-work-in-progress) for the latest information on the repositories. Documentation will be updated after the migration is complete.

# To configure Hygieia, execute the following steps:

Step 1: Run Maven Build

First you must build the Hygieia core. In the command line/terminal, run the following command from the \hygieia-core directory:

mvn clean install 
Once you have built the Hygieia core, navigate to \Hygieia\UI and run:

npm install
Installing npm ensures that you have the necessary dependencies.

Next you must build the api. In the command line/terminal, run the following command from the \api directory:

mvn clean install 
After the core and api are successfully built, you will be able to build the Hygieia project. In the command line/terminal, run the following command from the \Hygieia directory of your source code installation:

mvn clean install 
These steps will build all the following components:

└── hygieia-core (https://github.com/Hygieia/hygieia-core)
└── api (https://github.com/Hygieia/api)
└── Hygieia (https://github.com/Hygieia/Hygieia)
    ├── UI
The output .jar file is generated in the \target folder for each component of Hygieia, including collectors.

In the future, you could also build collectors:

└── Jira (https://github.com/Hygieia/hygieia-feature-jira-collector)
└── Sonar (https://github.com/Hygieia/hygieia-codequality-sonar-collector)
└── NFRR (https://github.com/Hygieia/hygieia-audit-nfrr-collector)
└── Score (https://github.com/Hygieia/hygieia-misc-score-collector)
└── Github (https://github.com/Hygieia/hygieia-scm-github-collector)
	
and so on. 	
Step 2: Set Parameters in the Properties File

Set the configurable parameters in the .properties file to connect to each component of Hygieia. For more information about the server configuration, see the Spring Boot documentation.

Step 3: Run Each Component

To run the executable file for API module, change directory to ‘api\target’ and then execute the following command from the command prompt:

java -jar api.jar --spring.config.location=C:\[path to api.properties file] -Djasypt.encryptor.password=hygieiasecret
To run the UI module, in the command prompt, navigate to \Hygieia\UI. If you do not have gulp already installed, run the following command:

npm install gulp@3.9.1
Then execute the following command:

gulp serve
The dashboard will serve up on port 3000.

Tip: If there are difficulities loading your UI:

Clean up your cookies
Open up your local dashboard in incognito mode
In general, all the collectors can be run using the following command:

java -jar <Path to collector-name.jar> --spring.config.name=<prefix for properties> --spring.config.location=<path to properties file location>
For detailed instructions on installing each component of Hygieia, see the documentation corresponding to each component.


