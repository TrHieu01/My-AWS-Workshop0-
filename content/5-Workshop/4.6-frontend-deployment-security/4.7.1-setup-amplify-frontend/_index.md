---
title : "Frontend Deployment with Amplify"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 4.6.1 </b> "
---

#### Objectives

Deploy the frontend from GitHub to AWS Amplify for automated build and deployment.

#### Overview

AWS Amplify provides mechanisms for building, hosting, and publishing frontends per branch, integrating the build pipeline and supporting domain/HTTPS configuration.

#### Connecting GitHub Repo and Selecting Branch

1. Create a new Amplify app.
2. Select GitHub and grant access permissions.
3. Choose the EduTrust repo and the deployment branch (main or release).
4. Enable auto-deploy if needed to synchronize releases per commit.

#### Custom Domain

The configuration for custom domains and HTTPS is presented in detail in section 4.6.3 using the Name.com, Route 53, and ACM stack.

#### Build Configuration (amplify.yml)

1. Describe the role of the `amplify.yml` file in defining install, build, and artifacts.
2. Ensure the correct output directory for a successful build.
3. Enable caching if needed to optimize build times.

#### Frontend Environment Variables

1. Set up environment variables for the frontend, such as API base URL, Cognito IDs, and region.
2. Synchronize variables across staging and production environments.

#### Verify Successful Build

1. Confirm the build was successful in the Amplify Console.
2. Access the default Amplify URL and check the user interface display.
