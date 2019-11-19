# nr-metabase-showcase
This repository includes 2 pieces that were used to set up a prrof-of-concept application that would display Metabase dashboards to authorized IDIR users.
1. Instructions to manually set up and deploy a Metabase instance to an Openshift namespace and populate with data from a CSV or other source. This should be reconfigured to a proper pipeline if used an a live application.
2. A Java-based web application that secures pages behind Keycloak logins and displays embedded Metabase dashboards (linked from the deployed Metabase instance above) in the web app. This application is referred to as the Metabase Viewer.
