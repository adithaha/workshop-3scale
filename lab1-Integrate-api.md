
## LAB 1 - Integrate API

Prerequisite:
- 3Scale installed with admin role (you can use trial version at https://www.3scale.net)
- Backend API: https://api.finto.fi this is public API from finto, be mindful to not put some loads on this. Be grateful they are publish this for free.

This workshop is based on 3Scale on premises, if you use one from 3Scale SaaS there might be slight differences on procedures below.
  
1. Login into 3Scale admin portal
2. (+) New API
   ```
   Name: Finto
   System Name: finto
   Add API
   ```
3. Integration > Methods & Metrics 
   ```
   Method - New method  
     Friendly name: GET_vocabularies  
     System name: GET_vocabularies  
     Create Method  
   Method - New method  
     Friendly name: GET_types  
     System name: GET_types  
     Create Method  
   ```
4. Integration > Configuration - add the base URL of your API and save the configuration.
   ```
   Private Base URL: https://api.finto.fi
   Mapping Rules:
     Delete Get /
     Add Mapping Rules:
       Verb: GET
       Pattern: /rest/v1/vocabularies
       + : 1
       Metric or Method: GET_vocabularies
     Add Mapping Rules:
       Verb: GET
       Pattern: /rest/v1/types
       + : 1
       Metric or Method: GET_types
   API test GET request: /rest/v1/vocabularies?lang=en
   Update and Test in Staging Environment
   ```
   You might get auth error if there is no developer account set up. You can ignore that.
5. Applications > Application Plan
   Create Basic plan
   ```
   Create Application Plan
     Name: Basic
     System Name: basic
     Create Application Plan
   Publish
   Click Basic - Metrics, Methods, Limits & Pricing Rules 
     GET_vocabularies - Limits - New usage limit
       Period: Minute
       Max. value: 60
       Create usage limit
     GET_types - disable
   ```
   Create Premium plan
   ```
   Create Application Plan
     Name: Premium
     System Name: premium
     Create Application Plan
   Publish
   Click Basic - Metrics, Methods, Limits & Pricing Rules 
     GET_vocabularies - Limits - New usage limit
       Period: Minute
       Max. value: 6000
       Create usage limit
     GET_types - Limits - New usage limit
       Period: Minute
       Max. value: 6000
       Create usage limit
    ```
6. Register developer - Basic plan 
   There is existing account Developer, we will use that account to be registered with application plan.  
   Register with Basic plan
   ```
   Choose dropdown Audience
   Account - Listing
   Click Developer - Applications - (+) Create Application
     Application Plan: Choose - Finto - Basic 
     Name: finto-basic
     Description: finto-basic
     Create Application
   Note the User Key eg. 4567d96a9a0d34b590d1b93f92397a79
   ```
7. Call API through API Gateway with Basic application plan.
   Note API Gateway URL.
   ```
   Choose dropdown at top: finto
   Integration - Configuration
   Note API Gateway staging URL
   ```
   Call vocabularies API.  
   Open API Gateway staging URL via browser, add path below with user key from #6:
   ```
   https://<staging-apicast>/rest/v1/vocabularies?lang=en&user_key=<user_key>
   ```
   You should get a response since Basic plan is able to call vocabularies method
   
   Call Types API.  
   Open API Gateway staging URL via browser, add path below with user key from #6:
   ```
   https://<staging-apicast>/rest/v1/types?lang=en&user_key=<user_key>
   ```
   You should get a auth error since Basic plan is unable to call types method.
8. Register developer - Premium plan 
   Register developer with Premium plan, same procedure with step #6. Note the user key.
9. Call API through API Gateway with Basic application plan. 
   Call vocabularies and types methods with user key from Premium plan, you should be able to call both.
