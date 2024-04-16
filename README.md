# aws-dynamic-model-switching-AWS

This project aims to seamlessly switch between two models, one considered "good" and the other "bad," based on real-world testing. The goal is to prevent errors from impacting production while still allowing for testing of new models in a shadow environment.

## Overview
In this project, we use two models:

(in code both named as model.tar.gz) in different endpoint,for the better understanding, uploaded in different name) :

Good Model: The current production model known to perform well. 
Bad Model: A new model under testing, which may produce errors or undesired outcomes.

The workflow involves deploying both models simultaneously, routing live traffic to the "good" model in production while the "bad" model operates in a shadow environment. If the "bad" model produces errors or unsatisfactory results during shadow testing, the system automatically rolls back to the "good" model in production to ensure uninterrupted service.

## Components

- **.**: Shadow Testing Endpoint: A separate endpoint dedicated to testing the "bad" model without affecting live traffic.
- **.**: Production Endpoint: The endpoint serving live traffic, routed to the "good" model.
- **.**: Error Monitoring: Monitoring system to detect errors or deviations in performance from the "bad" model during shadow testing.
- **.**: Automated Rollback: Automated mechanism to switch traffic back to the "good" model in production upon detecting errors from the "bad" model.
- **.**: Deployment Pipeline: Continuous integration/continuous deployment (CI/CD) pipeline to deploy new model versions and manage endpoints.

## Workflow

- **.**: Deployment:

  - **1.**: Both the "good" and "bad" models are deployed simultaneously.
  - **2.**: Live traffic is routed to the "good" model by default.
    
- **.**: Shadow Testing:

  - **1.**: A portion of live traffic is diverted to the "bad" model for shadow testing.
  - **2.**: Errors or deviations from expected behavior are monitored.
 
- **.**: Error Detection:

  - **1.**: An automated system monitors for errors or significant deviations from expected results from the "bad" model during shadow testing.
- **.**: Rollback Mechanism:

  - **1.**: Upon detecting errors or unsatisfactory performance from the "bad" model, the system automatically switches traffic back to the "good" model in production.
  - **2.**: The shadow testing endpoint is deactivated, and the "bad" model is removed from the shadow environment.
    
- **.**: Deployment of Corrected Model:

  - **1.**: After fixing issues identified during shadow testing, a new version of the "bad" model is deployed.
  - **2.**: The deployment pipeline ensures that the updated model undergoes shadow testing before being promoted to production.

## Usage
  
- **.**: Deployment:

  - **1.**: Set up AWS infrastructure, including endpoints, monitoring systems, and deployment pipelines.
  - **2.**: Deploy both the "good" and "bad" models using AWS SageMaker or similar services.

- **.**: Monitoring:

  - **1.**: Configure error monitoring systems to detect deviations in model performance during shadow testing.
- **.**: Testing:

  - **1.**: Monitor shadow testing results and ensure that errors are promptly detected and addressed.
- **.**: Rollback:

  - **1.**: Automate the rollback process to switch traffic back to the "good" model in production upon error detection.
- **.**: Continuous Improvement:

- **1.**: Continuously monitor and improve the shadow testing process and deployment pipeline to ensure efficient model switching and error detection.

## Acknowledgments

This project is inspired by the need for seamless model switching in real-world applications.
Thanks to AWS SageMaker and related services for providing robust infrastructure for model deployment and management.
