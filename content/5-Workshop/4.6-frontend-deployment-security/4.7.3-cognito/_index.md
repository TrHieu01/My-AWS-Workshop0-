---
title : "Cognito (User Authentication)"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 4.6.3 </b> "
---

#### Objectives

Integrate user authentication into the frontend to control access and issue valid tokens.

#### Overview

Cognito provides User Pools to manage users and App Clients to issue access tokens. This is the standard authentication layer for frontends in the AWS architecture.

#### Brief Explanation

- **User Pool**: A repository for user accounts, password policies, and permission groups.
- **App Client**: Configuration for the frontend application to receive tokens after login.

#### Required Frontend Environment Variables

1. COGNITO_USER_POOL_ID: User Pool identifier.
    ![Create User Pool](overview.png)
    
    *Go to User Pool and get user pool id*

2. COGNITO_CLIENT_ID: App Client identifier.
    ![Create App Client](app_client.png)
    
    *Go to App Client and get app client id.*

3. COGNITO_REGION: Deployment region for Cognito.

#### Verify Login/Logout, Token and group

1. Perform login and logout on the UI to check session status.
2. Verify the returned tokens (ID/Access token) and confirm that API calls have valid Authorization.

    ![check login/logout and token](check.png)
    
    *Check login/logout and token*

1. Check group

    ![check group](group.png)
    
    *Check group*
