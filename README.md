﻿** **

# Dataverse Scaling!

## Project Team: 

Students: Ashwin Pillai, James Michael Clifford, Ryan Morano, Patrick Dillon

Mentors: Dan McPherson (Red Hat), Phil Durbin (Harvard), Solly Ross (Red Hat)

## Our Dataverse Fork:
https://github.com/EC528-Dataverse-Scaling/dataverse

## Vision and Goals:

Dataverse is an open source web application to share, preserve, cite, explore, and analyze research data. It facilitates making data available to others, and allows users to replicate others' work more easily. Researchers, data authors, publishers, data distributors, and affiliated institutions all receive academic credit and web visibility. However, the current Dataverse infrastructure has not been built for scale or high availability and the current development road map is focused on creating new features instead of making the product more resilient and easier to host.  

Therefore, the overarching goal of our current work is to aid in developing a more resilient and scalable deployment of Dataverse with OpenShift to deploy on the MOC. Specifically, we aim to make each of the existing components of Dataverse function at scale within OpenShift, including seamless integration with Glassfish, Postgresql and Solr. 

The final outcome of our work will include a one-click deployment of a fully scalable instance of Dataverse running on top of OpenShift on the MOC.   

![The beginning state of the project](https://github.com/BU-NU-CLOUD-SP18/Dataverse-Scaling/blob/master/project_initial.png)
![The final state of the project](https://github.com/BU-NU-CLOUD-SP18/Dataverse-Scaling/blob/master/project_final.png)
![Future work](https://github.com/BU-NU-CLOUD-SP18/Dataverse-Scaling/blob/master/project_future.png)

## Users of the Project:

Researchers - Want to publish data and analyse code on a reliable platform that can handle a high volume of traffic if research findings see a spike in popularity. Also open to be able to reexamine existing data in a new way, for example use machine learning. 

Journals - Want to verify and publish author’s research findings and data using dataverse repositories to increase the impact of journals and preserve data and make it citable.

Institutions - Need a place to host research data using customized dataverses for researchers, departments, and faculty to share their data. Deploying scalable Dataverse on OpenShift to production should be simple.

Developers - Develop Dataverse on a local version of OpenShift and easily deploy changes to production

Companies - Want to track the running instances of dataverse and collect results from tests.

## Scope and Features:
	
 - While the code uses OpenShift, all of the contributions will be in the Dataverse project
 - Updated configuration of existing containerized instances of Dataverse to support reliable scaling.  Including, PostgreSQL, Glassfish and Solr
 - Installation script (extend existing) - easy developer setup

## Solution Concept:
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

