
## LAB 1 - Integrate API

Prerequisite:
- 3Scale installed with admin role (you can use trial version at https://www.3scale.net)
- Backend API: we will be using previously created nationalpark API, note nationalpark API route
  
  
1. Login into 3Scale admin portal
2. Integrate this API - nationalpark-<userx>
3. Integration > Methods & Metrics 
   ```
   Method - New method  
     Friendly name: GET_info  
     System name: GET_info  
     Create Method
  Method - New method  
     Friendly name: GET_all  
     System name: GET_all  
     Create Method
   ```
4. Integration > Configuration - add the base URL of your API and save the configuration.
   ```
   Private Base URL: http://<nationalpark-api>
   Mapping Rules:
     Delete Get /
     Add Mapping Rules:
       Verb: GET
       Pattern: /api/info
       + : 1
       Metric or Method: GET_info
     Add Mapping Rules:
       Verb: GET
       Pattern: /api/data/all
       + : 1
       Metric or Method: GET_all
   API test GET request: /api/info
   Update and Test in Staging Environment
   ```
   You might get auth error if there is no developer account set up. You can ignore that.
5. Delete Unlimited plan, we will create another one later
   ```
   Applications > Application Plan - Delete all Unlimited plan
   ```
6. Disable default plan, let developer choose their plan after registration
   ```
   Applications > Application Plans - Default Plan - [empty]
   ```
7. Applications > Application Plan
   Modify Basic plan.
   ```
   Click Basic - Metrics, Methods, Limits & Pricing Rules 
     GET_info - Limits - New usage limit
       Period: Minute
       Max. value: 60
       Create usage limit
     GET_all - disable
   Update Application Plan
   ```
   Create Premium plan.
   ```
   Create Application Plan
     Name: Premium
     System Name: premium
     Create Application Plan
   Publish
   Click Basic - Metrics, Methods, Limits & Pricing Rules 
     GET_info - Limits - New usage limit
       Period: Minute
       Max. value: 120
       Create usage limit
     GET_all - Limits - New usage limit
       Period: Month
       Max. value: 60
       Create usage limit
    Update Application Plan
    ```
10. Promote to Production
   ```
   Integration - Configuration
   Promote v.1 to Production
   ```
11. Note your API staging and production environment, we will use those later
