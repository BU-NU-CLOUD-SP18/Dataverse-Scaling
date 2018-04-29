** **

# Dataverse Scaling!

## Project Team: 

Students: Ashwin Pillai, James Michael Clifford, Ryan Morano, Patrick Dillon

Mentors: Dan McPherson (Red Hat), Phil Durbin (Harvard), Solly Ross (Red Hat)

## Our Dataverse Fork:
https://github.com/EC528-Dataverse-Scaling/dataverse

## Our Project Video
https://goo.gl/Fa8dvH

## Vision and Goals:

Dataverse is a popular open-source web application to share, preserve, cite, explore, and analyze research data. It facilitates making data available to others, and allows users to easily replicate work. However, the current Dataverse infrastructure has not been built for scale or high availability and the current development road map is focused on creating new features instead of making the product more resilient and easier to host. Dataverse was originally built as a single-deployment three-tier application. Our mentors collaborated to containerize the components of Dataverse and run Dataverse on OpenShift.

![The beginning state of the project](https://github.com/BU-NU-CLOUD-SP18/Dataverse-Scaling/blob/master/project_initial.png)

Our project is to advance this initial containerization work toward making Dataverse more scalable. As pictured above, after the initial containerization there is a single instance of each componenet. Our project will achieve scalability by allowing components to scale horizontally to multiple instances. We will incoprorate this scalability into the Dataverse project so that system administrators and developers can setup a scalable deployment of Dataverse out of the box.


## Users of the Project:

Users of the Dataverse project in general include researchers, journals, research and academic institutions, and companies. Our project work is directed toward the following users:

- Software Developers - Want to develop Dataverse on a local version of OpenShift and easily deploy changes to production
- System Adminstators - Want to easily deploy Dataverse to the cloud or local servers
- Database Adminstators - Want to manage the Postgres databases deployed in Dataverse


## Scope and Features:

 - Updated configuration of existing containerized instances of Dataverse to support reliable scaling.  Including, PostgreSQL, Glassfish and Solr
 - Installation script (extend existing) - easy developer setup

## Solution Concept:
![The final state of the project](https://github.com/BU-NU-CLOUD-SP18/Dataverse-Scaling/blob/master/project_final.png)

- PostgreSQL
  - Use StatefulSets to create single-master replicated DB
  - Update Dockerfile (if necessary)
  - OpenShift Deployment/Pod (DeploymentConfig in openshift.json)
  - Modify application code to access DB container service
  
- Glassfish
  - Use StatefulSets to create single-master replicated servers
  - Update Dockerfile (if necessary)
  - OpenShift Deployment/Pod (DeploymentConfig in openshift.json)
  - Modify application code to access server container service
- Solr
  - Update Dockerfile (if necessary)
  - OpenShift Deployment/Pod (DeploymentConfig in openshift.json)
  - Modify application code to access search indexing service
- Load-testing
  - Find and configure a tool and set of tests to replicate heavy load
  - Check Apache bench or JMeter

## Acceptance Criteria:
 - Scaling PostgreSQL pods creates replicas with a master
 - Scaling Glassfish is new territory, advance creating masters, hopefully finish
 - If time allows, scaling solr along the same lines
 - Deployable into the MOC’s OpenShift deployment.
 - Load tests verify scalable architecture
 - Creating containerized instance(s) of dataverse is simple (One-click install).
 - Developer setup documented
 - Production deployment documented

## Release Planning:

Detailed users stories and plans are available at https://tree.taiga.io/project/msdisme-2018-bucs528-template-6/ 

Release #1(Feb 8) - Initial
 - Stand up Dataverse on local OpenShift (using minishift)
 - Develop user stories
 - Prepare presentation

Release #2 (Feb 22) - Begin PostgreSQL & Glassfish StatefulSets
 - Modify OpenShift config in Dataverse to allow a scaled PostgreSQL & Glassfish

Release #3 (Mar 15) - Continue PostgreSQL & Glassfish SS
 - Choose PostgreSQL image
 - Modify Glassfish image to take into account master

Release #4 (Mar 29) - Finish PostgreSQL & Glassfish SS


Release #5 (Apr 12) - Begin deployment/load test on MOC & work on Solr


Release #6 (Apr 26) - Finish deployment/load test on MOC & Solr
 - Deploy Dataverse into the MOC’s OpenShift deployment
 - Run the load test against Dataverse in the MOC.

## Future Work:
![Future work](https://github.com/BU-NU-CLOUD-SP18/Dataverse-Scaling/blob/master/project_future.png)
