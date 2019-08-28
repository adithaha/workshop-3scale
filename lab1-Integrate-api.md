
## LAB 1 - Integrate API

3Scale admin URL: https://3scale-admin.anugraha-3scale.apps.rhpds311.openshift.opentlc.com  
Backend API: https://api.finto.fi  
  
1. Login into 3Scale admin portal
2. Drop down - API
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
   API test GET request: /rest/v1/vocabularies
   Update and Test in Staging Environment
   ```
5. Applications > Application Plan
   ```
   Create Application Plan
     Name: Basic
     System Name: basic
     Create Application Plan
     Click Basic - Metrics, Methods, Limits & Pricing Rules 
       GET_vocabularies - Limits - New usage limit
         Period: Minute
         Max. value: 60
         Create usage limit
       GET_types - disable
   Create Application Plan
     Name: Basic
     System Name: basic
     Create Application Plan
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
       

```
xxxxx
```
