
## LAB 1 - Integrate API

Prerequisite:
- 3Scale admin portal: https://github.com/adithaha/workshop-3scale/blob/master/finto/url.md
- Backend API: https://api.finto.fi this is public API from finto, be mindful to not put some loads on this. Be grateful they are publish this for free.

This workshop is based on 3Scale on premises, if you use one from 3Scale SaaS there might be slight differences on procedures below.
  
  
1. Login into 3Scale admin portal
2. Integrate this API
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
     GET_vocabularies - Limits - New usage limit
       Period: Minute
       Max. value: 60
       Create usage limit
     GET_types - disable
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
     GET_vocabularies - Limits - New usage limit
       Period: Minute
       Max. value: 120
       Create usage limit
     GET_types - Limits - New usage limit
       Period: Month
       Max. value: 1000
       Create usage limit
    Update Application Plan
    ```
8. Delete default docs
   ```
   Active Docs - Echo - Delete - OK
   ```
9. Upload Finto docs
   ```
   Active Docs - Create your first spec
   Name: Finto
   System Name: finto
   Check Publish?
   Copy API JSON Spec from https://raw.githubusercontent.com/adithaha/workshop-3scale/master/finto-swagger.json
   Change line 11: "host": "finto-2445581864856.production.gw.apicast.io"
   To: "host": "api-<user>-apicast-production.anugraha-3scale.apps.rhpds3x.openshift.opentlc.com"
   Create Service
   ```
10. Promote to Production
   ```
   Integration - Configuration
   Promote v.1 to Production
   ```
   
