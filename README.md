# Natural Resources Metabase Showcase [![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE) [![img](https://img.shields.io/badge/Lifecycle-Retired-d45500)](https://github.com/bcgov/repomountie/blob/master/doc/lifecycle-badges.md)

This repository is no longer maintained. Please visit [https://github.com/bcgov/nr-showcase-devops-tools/tree/master/tools/metabase](https://github.com/bcgov/nr-showcase-devops-tools/tree/master/tools/metabase) for maintained documentation on deploying and managing a Metabase instance on Openshift.

---

This repository includes 2 pieces that were used to set up a prrof-of-concept application that would display Metabase dashboards to authorized IDIR users.
1. Instructions to manually set up and deploy a Metabase instance to an Openshift namespace and populate with data from a CSV or other source. This should be reconfigured to a proper pipeline if used an a live application.
2. A Java-based web application that secures pages behind Keycloak logins and displays embedded Metabase dashboards (linked from the deployed Metabase instance above) in the web app. This application is referred to as the Metabase Viewer. There is no OpenShift pipeline provided for this proof-of-concept, but it can easily be quickly deployed to an OCP namespace with the OC new-app command and a Java S2i.

# Instructions to Run

## Metabase
The Viewer is an application that is meant to display existing Metabase dashboard embeds in a secured web app. It will require an existing Metabase instance with dashboards set up and ready to be embedded.  
If you do not already have a Metabase instance set up, the quickstart guide here may be of use: https://github.com/bcgov/nr-metabase-showcase/blob/master/docs/metabase.md

## Metabase Viewer

### Prerequesites
The developent machine must have Java 8 and Maven installed. An IDE such as IntelliJ or Eclipse can be used, but the app can be started from the command line as well.

A Keycloak realm with an Client configured for this app to use must be available. 

### Configuration
See the https://github.com/bcgov/nr-metabase-showcase/blob/master/src/main/resources/application.properties file for a list of environment variables that will be pulled in as configuration.  

You can set up the environment variables as named in that file, or use the pattern of having a local configuration file (application-local.properties) and starting the app with a spring profile of local (-Dspring.profiles.active=local).

If you do not require sending emails via the Contact controller in this app, then the CHES properties are not required.

### Startup
Start the Spring Boot web app up with 
```
mvn spring-boot:run 
```